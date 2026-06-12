---
title: "No sound in Lynx"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by TruthDose on 2010-04-30
I just upgraded from Karmic to Lucid and I have no sound. When I go to Admin >Sound It tells me to wait for the system to respond, nothing happens after this. HELP!

---

### Post by TruthDose on 2010-05-02
bump

---

### Post by utnubuuser on 2010-05-02
right-click the speaker icon in top panel, open volume control and make sure sound isn't muted.

or try > sudo alsamixer in a terminal and check if anything is marked MM (MM means mute)

**Note: I'm using Hardy Heron, and I've discovered a bug in alsamixer that causes runaway  CPU usage (100%) which could damage your hardware,  so be careful.  You can kill any running processes by running > sudo killall name-of-application-or-process-to-kill**

---

### Post by TruthDose on 2010-05-02
this may sound stupid but the master does have the mm. How do you unmute?

---

### Post by TruthDose on 2010-05-02
I pressed m and unmuted it. Still no sound...

---

### Post by utnubuuser on 2010-05-02
Not sure how else to help you, -- there are several current threads about sound probs in Lucid - do a search. 
**PS - Check the update/edit in my earlier response about a bug in alsamixer**

---

### Post by CDennis on 2010-05-29
System - Preferences - Sound - Hardware Tab - Settings for the selected device - 
For my setup switching from the default bottom choice of Analog Stereo Duplex to Digital Stereo Duplex ( iec958 ) made everything work. This is on a full install of 10.04 with no changes to any other sound/driver settings. 
Perhaps try to find a setting that works for your system?

Best 

-DJ

---

