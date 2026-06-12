---
title: "After Update, Sound does not work"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by suprman2020 on 2008-10-16
Everything was not working perfect yesterday, but it was working. After an update today my sound no longer works. When I go to sound at system preferences I get this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused


Any help would be appreciated.

---

### Post by milliman on 2008-10-16
I have the same problem.  It looks like the drivers are loaded in the kernel and the audio controller is located on the PCI bus.  Neither PulseAudio or ALSA work when they use to work perfectly.  I noticed that PulseAudio, Gstreamer, and the kernel headers were updated yesterday.

Mark

---

### Post by psyke83 on 2008-10-16
> **milliman said:**
> I have the same problem.  It looks like the drivers are loaded in the kernel and the audio controller is located on the PCI bus.  Neither PulseAudio or ALSA work when they use to work perfectly.  I noticed that PulseAudio, Gstreamer, and the kernel headers were updated yesterday.

Mark

PulseAudio was not updated yesterday (the last update was October 10th). It seems likely you're using PulseAudio 0.9.13 from TheMuso's PPA, and it doesn't work correctly for many users at the moment. You can find instructions to downgrade in my PulseAudio thread.

---

### Post by milliman on 2008-10-17
No I am using the official distro version of PulseAudio: 0.9.10.  The problem is with the Intel 82801 Audio driver that is now broken.

---

