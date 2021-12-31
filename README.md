for (int i = 0; i < l; i++) {
seq[i] = Integer.bitCount((i*r));
}
Synthesizer synthesizer = MidiSystem.getSynthesizer();
synthesizer.open(); 
MidiChannel channel = synthesizer.getChannels()[0];
for (noteAndLength note : notes) {
	channel.noteOn(note.getNote(), 20);
	try { 
		Thread.sleep(note.getLength() * 20);
	} 
	catch (InterruptedException e) {
		break;
	} 
	finally {
		channel.noteOff(note.getNote());
	}
}
channel.noteOn(note.getNote(), 20);
channel.noteOn(note.getNote()+third, 20);
channel.noteOn(note.getNote()+fifth, 20);
channel.noteOn(note.getNote()+12, 20);
% javac fractalMusic.java
% java fractalMusic 1000 63 –min true
