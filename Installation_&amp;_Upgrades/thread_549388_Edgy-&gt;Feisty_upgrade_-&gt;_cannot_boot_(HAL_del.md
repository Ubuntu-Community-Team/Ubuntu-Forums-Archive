---
title: "Edgy-&gt;Feisty upgrade -&gt; cannot boot (HAL delay); can boot with old kernel; no sound;"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by AstarothCY on 2007-09-12
**EDIT AFTER SOLVING: Ignore the sound issues, they are being dealt with in [this thread](http://ubuntuforums.org/showthread.php?t=550102).**

Here is the sequence of events, as far as I can recall them (important bits in bold):

1. I fully updated Edgy and rebooted.
2. After the reboot I was trying to install my Zyxel G-260 USB wireless adapter and was listening to music on Amarok and suddenly **the sound became corrupted, and everything I tried to play just came out as noise, in any app.**
3. I rebooted and had no sound at all, and **whenever I tried to play a sound the computer would slow down a lot.** The wireless adaptor never worked, I was trying to do it with ndiswrapper, the driver installed and ndisgtk recognised the device but **ubuntu networking manager did not give me a wireless option** and the adapter's LED never turned on.
4. I booted into WinXP and verified that my sound card was ok, it worked perfectly.
5. Booted back into Ubuntu, I opened up the update manager and began the Feisty upgrade procedure in hope that it would fix the sound & wireless problems. The manager downloaded all the packages with no errors and began installing them.
6. After the upgrade finished successfully, I rebooted.
7. The reboot was going fine until suddenly the Ubuntu logo screen changed to the terminal screen showing that **the bootup was stuck at the "Starting Hardware abstraction layer hald" part**.
8. Eventually, some more text appears and immediately the screen goes blank and stays that way forever, requiring hard reboot.


This is the state I am at right now. Here are the various things I have tried:

1. Booting with kernel version .11: Ubuntu boots successfully and works fine but there is no sound. There is no slowdown while attempting to play sound like before but the fact that sound is not working is a complete mystery. Yes I have checked volume controls etc. I tried testing all the various sound drivers in the sound preferences and none work.
2. Booting with any kernel newer than .11: same problem as described above, i.e. long delay at HAL and then blank screen freeze.
3. Pressing ctrl-c at the HAL delay part: moves on to freeze at the "Starting avahi-daemon" part, and never moves on.
4. Pressing alt-f3: I get the terminal login screen, and if i do "startx" I get a blank screen that stays that way forever.



THE ISSUES HERE IN ORDER OF IMPORTANCE:

1. I cannot boot into any kernel newer than .11.
2. There is no sound under any circumstances.
3. (ignore for now) Cannot get wireless to work.


I have a suspicion that the Zyxel G-260 might work with the zydas driver but I need to fix the first two issues before trying it again. I realise that I made several mistakes during this whole process, I should have not upgraded while I had two ongoing problems, one of them critical. Regardless, this is the situation, and I need all the help I can get.

---

### Post by AstarothCY on 2007-09-12
bump, this is kind of urgent

---

### Post by mysticmatrix on 2007-09-12
> **AstarothCY said:**
> bump, this is kind of urgent

Well this might not be the solution but perhaps a clean install of Ubuntu Feisty would be the method that would require least headaches. Perhaps other people might help you in your problems but that might takes just hours....

---

### Post by AstarothCY on 2007-09-12
im afraid a clean install is pretty much out of the question... the things i have set up and working on this install would take me weeks to reproduce... anyway i doubt it is a huge problem because nothing tragic like a power cut mid-upgrade happened or anything, its probably something stupid like a one-line edit in some config file, i just need some expert help to work out what it is.

---

### Post by AstarothCY on 2007-09-13
really sorry but i have to bump this again

---

### Post by AstarothCY on 2007-09-13
bump

---

### Post by AstarothCY on 2007-09-14
bump, i am on the verge of abandoning ubuntu, this is kind of unacceptable

---

### Post by Brendt2 on 2007-09-16
I wish I could help you, but I am unaware of a solution to this sort  of a problem.

---

### Post by AstarothCY on 2007-09-16
Gutsy kernel .22 doesn't work either, btw. Same exact problem.

---

### Post by AstarothCY on 2007-09-17
SOLVED by installing the gutsy HAL packages as described [here](https://launchpad.net/hal/+bug/92647). I also had to remove the gutsy kernel and reinstall the latest feisty kernel (20-16) and it boots fine. HOWEVER I still have other problems, I will make a new thread though since the problem has changed a lot.

---

