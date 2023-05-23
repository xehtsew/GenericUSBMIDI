GenericUSBMIDI - updated README
==============

This is a macOS driver for the Roland V-Synth G1 to work with MIDI over USB. It has been tested with a Roland V-Synth G1 Version 2 (not XT, not GT) on an Intel based MacBook Pro running Monterey. It was tested with Pro Tools 2021.

All credit to ysalathe for their implementation of the GenericUSBMIDI Driver. 

Slight changes I've implemented are: USB Device ID, Device Display Name, and locating the USB interface descriptor that the V-Synth uses. 

I didn't test the functionality extensively. Note on-off, MIDI cc's, that's all I needed. 

#### to use: 
Go to releases, download GenericMIDIDriver.plugin, place it into `/Library/Audio/MIDI Drivers/` and restart the computer. 

#### to compile yourself:
Download source, open XCode, compile source, locate plugin as outlined below, place into `/Library/Audio/MIDI Drivers/` and restart the computer. 

#### the future:
testing or re-writing if necessary on M1


Original ReadMe
===============

This is an OS X driver for MIDI devices connected via USB. It has been tested with a Roland (Ed) PC-300 MIDI Keyboard connected via USB to an Apple MacBook Pro running Mac OS X v10.8.2 (Mountain Lion) as well as v10.9.1 (Mavericks).

I started this project since at the time of writing Roland corp. does not provide drivers for the PC-300 that work with OS X versions greater than v10.5 (Leopard). 

At the present stage it consists of sample code from Apple Inc. which was obtained from the casiousbmididriver project (http://code.google.com/p/casiousbmididriver/).

The only change to the sample code that was necessary to get the driver to work with the Roland PC-300, was to set the USB interface number, vendor ID and product ID in the file GenericUSBMidi.cp:

    #define kTheInterfaceToUse	2	// The third one
    #define kMyVendorID		0x0582	// Roland Corporation
    #define kMyProductID	0x0008

The idea of the present project would be to provide a generic open source OS X driver for several other USB MIDI devices. Contributions are welcome! 


After compiling the source with Xcode simply copy the resulting bundle GenericUSBMidi.plugin to the Folder /Library/Audio/MIDI Drivers/. This is most simply done with the following bash (Terminal) commands:

    cd $HOME/Library/Developer/Xcode/DerivedData/GenericUSBMidi*/Build/Products/Debug
    sudo cp -r GenericUSBMidi.plugin /Library/Audio/MIDI\ Drivers/

Note: to find out where the "GenericUSBMidi.plugin" file has been created, right-click onto Products->GenericUSBMidi.plugin in Xcode and then click "Show in Finder". This is illustrated in the file ShowInFinder.png:

[screenshot to illustrate what to do in Xcode to find the compiled plugin in Finder](ShowInFinder.png)

After that it is necessary to reboot the MIDIServer process (or the entire OS). 

For debugging (e.g. using break points) attach your debugger to the MIDIServer process.
In Xcode this is done via the Menu Product -> Attach to Process -> MIDIServer.

Have fun!

December 30, 2012

Yves Salathe
