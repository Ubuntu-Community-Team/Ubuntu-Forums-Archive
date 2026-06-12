---
title: "Amarok 2 won't work."
date: 2009-01-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-09
```

amarok
amarok(9774) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) "HDA Intel (AD198xAnalog)"
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) ("x-phonon:CARD=0,DEV=0", "plughw:CARD=0,DEV=0")
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) setProperty(device, "x-phonon:CARD=0,DEV=0" ) failed
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) setProperty(device, "plughw:CARD=0,DEV=0" ) failed
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) "HDA Intel (AD198xAnalog)"
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) ("x-phonon:CARD=0,DEV=0", "plughw:CARD=0,DEV=0")
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) setProperty(device, "x-phonon:CARD=0,DEV=0" ) failed
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) setProperty(device, "plughw:CARD=0,DEV=0" ) failed
virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&) "default"
<unknown program name>(9773)/: Communication problem with  "amarok" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by messagebus)" "

lordveovis@ubuntu:~$ KCrash: Application 'amarok' crashing...
sock_file=/home/lordveovis/.kde/socket-ubuntu/kdeinit4__0

```
I think that speaks for itself

---

### Post by MaX on 2009-01-09
Yeah, it's a Phonon problem not a Amarok problem...

---

### Post by LordVeovis on 2009-01-09
> **MaX said:**
> Yeah, it's a Phonon problem not a Amarok problem...

Any workaround?  Currently my "solution" was uninstall amarok2 and go back to amarok.  Clearly this should not be the long term solution :P

---

