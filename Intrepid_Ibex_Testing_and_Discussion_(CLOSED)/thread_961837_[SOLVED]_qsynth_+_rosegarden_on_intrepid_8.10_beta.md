---
title: "[SOLVED] qsynth + rosegarden on intrepid 8.10 beta plays only the first note"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DARKAD on 2008-10-28
I have ubuntustudio 8.10 beta with a firewire soundcard.
I'm trying to play a rosegarden midi file with some soundfonts on qsynth.
Everything seems to work fine, except that I can hear only the first note, just when I push the play button.

I spent an hour googling but nothing was useful.

Probably the problem is my firewire soundcard not supported by alsa.

Any suggestion would be appreciated!


p.s. On ubuntustudio 8.04 I had the same problem, then I reinstalled qsynth and fluidsynth and everything worked.

---

### Post by DARKAD on 2008-10-28
When I look at the rosegarden configuration panel "midi settings" I can see only two choices on sequencer timing sources: "auto" and pcm capture 1.0.1.

I don't know if this helps, any of the two doesn't resolve the problem.

---

### Post by DARKAD on 2008-10-28
Thats what I see if I run rosegarden from terminal and then I push play:

darkad@depandance-ubuntu:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/darkad/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
LADSPAPluginFactory::discoverPlugins - done
Rosegarden 1.7.0 - AlsaDriver [ALSA library version 1.0.17a, module version 1.0.17, kernel version 2.6.27-3-rt]
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/darkad/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 256
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 4 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
JackDriver::initialiseAudio - found 6 JACK physical inputs
JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FreeBoB Jack MIDI, dev1c_Midi In)		(READ ONLY) [ctype 1, ptype 2, cap 33]
    129,1 - (FreeBoB Jack MIDI, dev1p_Midi Out)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    131,0 - (FLUID Synth (6529), Synth input port (6529:0))		(WRITE ONLY) [ctype 1, ptype 1048578, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 129:1 on initialisation
done
Creating device 0 in Play mode for connection 129:1 dev1p_Midi Out (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 131:0 on initialisation
done
Creating device 1 in Play mode for connection 131:0 Synth input port (6529:0) (write)
Default device name for this device is MIDI software device 2
Creating device 2 in Record mode for connection 129:0 dev1c_Midi In (read)
Default device name for this device is MIDI software input
CREATED OUTPUT PORT 5:out 3 - MIDI output system device for device 3
done
Creating device 3 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 4 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
Failed to open timer: hw:CLASS=1,SCLASS=0,CARD=0,DEV=0,SUBDEV=0
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 17, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.17 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 27, suffix = "rt"
AlsaDriver::versionIsAtLeast: is version 2.6.27-3-rt at least 2.6.20? yes
    Current timer set to "PCM capture 1-0-1" with timer checks
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 17, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.17 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 27, suffix = "rt"
AlsaDriver::versionIsAtLeast: is version 2.6.27-3-rt at least 2.6.20? yes
    Current timer set to "PCM capture 1-0-1" with timer checks
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.0/src/base/Composition.cpp:1539
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 130:3 to General MIDI Device
LADSPAPluginFactory::discoverPlugins - done
darkad@depandance-ubuntu:~$ CompositionModelImpl::slotInstrumentParametersChanged()

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FreeBoB Jack MIDI, dev1c_Midi In)		(READ ONLY) [ctype 1, ptype 2, cap 33]
    129,1 - (FreeBoB Jack MIDI, dev1p_Midi Out)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    131,0 - (FLUID Synth (6529), Synth input port (6529:0))		(WRITE ONLY) [ctype 1, ptype 1048578, cap 66]

TrackButtons::slotUpdateTracks
Comparing current version "1.7.0" with latest version "1.7.2"
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Renaming device 0 to General MIDI Device
Disconnecting my port 3 from 129:1 on reconnection
Connecting my port 3 to 129:1 on reconnection
AlsaDriver::setPlausibleConnection: connection like 129:1 dev1p_Midi Out (write) requested for device 0
AlsaDriver::setPlausibleConnection: exact match available
Renamed 130:3 to General MIDI Device
Renaming device 1 to MIDI software device 2
Disconnecting my port 4 from 131:0 on reconnection
Connecting my port 4 to 131:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 131:0 Synth input port (5367:0) (write) requested for device 1
AlsaDriver::setPlausibleConnection: fuzzy match 131:0 Synth input port (6529:0) (write) available with fitness 13
Renamed 130:4 to MIDI software device 2
Renaming device 3 to MIDI software device 3
Renamed 130:5 to MIDI software device 3
CREATED OUTPUT PORT 6:out 4 for device 7
Creating device 7 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 1
Renaming device 7 to MIDI software device 4
Connecting my port 6 to 131:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 131:0 Synth input port (5367:0) (write) requested for device 7
AlsaDriver::setPlausibleConnection: fuzzy match 131:0 Synth input port (6529:0) (write) available with fitness 13
Renamed 130:6 to MIDI software device 4
CREATED OUTPUT PORT 7:out 5 for device 8
Creating device 8 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 2
Renaming device 8 to MIDI software device 5
Renamed 130:7 to MIDI software device 5
CREATED OUTPUT PORT 8:out 6 for device 9
Creating device 9 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 3
Renaming device 9 to MIDI software device 6
Connecting my port 8 to 131:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 131:0 Synth input port (5367:0) (write) requested for device 9
AlsaDriver::setPlausibleConnection: fuzzy match 131:0 Synth input port (6529:0) (write) available with fitness 13
Renamed 130:8 to MIDI software device 6
CREATED OUTPUT PORT 9:out 7 for device 10
Creating device 10 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 4
Renaming device 10 to MIDI external device
Renamed 130:9 to MIDI external device
CREATED OUTPUT PORT 10:out 8 for device 11
Creating device 11 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 5
Renaming device 11 to MIDI output system device
Renamed 130:10 to MIDI output system device

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FreeBoB Jack MIDI, dev1c_Midi In)		(READ ONLY) [ctype 1, ptype 2, cap 33]
    129,1 - (FreeBoB Jack MIDI, dev1p_Midi Out)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    131,0 - (FLUID Synth (6529), Synth input port (6529:0))		(WRITE ONLY) [ctype 1, ptype 1048578, cap 66]

DataBlockRepository::clear()
Warning: Composition::~Composition() with 2 observers still extant
Observers are: 0xb529a3c4 [N10Rosegarden19SegmentParameterBoxE] 0xb4f31cd0 [N10Rosegarden20CompositionModelImplE]
TrackButtons::slotUpdateTracks
CompositionModelImpl::slotInstrumentParametersChanged()
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()
JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
SoundDriver::clearAudioQueue
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()

---

### Post by DARKAD on 2008-10-30
There was a little thing to do for my sys configuration:

I add these next lines from:

[https://help.ubuntu.com/community/Ub...dioPreparation](https://help.ubuntu.com/community/Ub...dioPreparation)

ALSA Sequencer

If you can not have midi sequencing enabled, or if you have midi error message, the Alsa midi sequencer module of the kernel may not be loaded. Try that:

sudo modprobe snd-seq

If it works, to have your system load it at bootup, you have to add it to the /etc/modules file, do:

sudo su -c 'echo snd-seq >> /etc/modules'

---

