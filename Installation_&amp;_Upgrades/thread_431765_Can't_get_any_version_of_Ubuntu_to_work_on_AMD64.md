---
title: "Can't get any version of Ubuntu to work on AMD64"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by WhizCas on 2007-05-03
At home I've got two PC's one intel 1,5 ghz where I got Ubuntu installed for over 3 years, the other I've been struggling from time to time to get a version of ubuntu working. The PC is a AMD 64 with an ati radeon 9800 pro. I can install any version of ubuntu but after logging in to Ubuntu it always hangs, it still shows the screen but the mouse can't move and it's impossible to go to any tty. The numlock and scroll lock button of my keyboard also start to flash. After long time struggling over the forum I still can't find a solution. For the info I tried Vesa and it is possible for me to go into recovery mode. Hopefully there are some usefull tips!

Thanks in advance!

---

### Post by dannyboy79 on 2007-05-03
have you tried to boot into the new system without starting x? then try to install envy and run it? this will install either the ati driver or the radeon driver. here is my personal experience I had trying to get a live cd to work with  my ATI AIW 9800 Pro.

[http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688)
read thread #5

---

### Post by WhizCas on 2007-05-03
Thanks for your help Dannyboy, I already read your thread yesterday, too bad it didnt help me. I just tried envy, but it didnt made any changes. The error is still there. The strange thing is that the live cd also didnt function until i used the alternative cd text mode and I also couldnt use ubuntu till i went to recovery mode. So Im really wondering why X bugs me :(

---

### Post by psusi on 2007-05-03
I have an amd64 and used to have a Radeon 9800 pro, but it blew out and so now I have an X850.  To get the amd64 livecd to get past the boot loader, I have to edit the command line and change the splash option to nosplash.  I used to have to disable acceleration and dri but the feisty livecd boots up and works properly with full 3d acceleration, as long as I disable the splash screen.  I used the xorg.conf on the livecd as a guide to getting my main install to work that well after upgrading.

---

### Post by dannyboy79 on 2007-05-03
ok, what drivers have you tried in your xorg.conf?? you're saying you tried vesa, ati, and radeon? also, what is the "error"?

 there are ton's of threads which help people get their ati cards to work. well the recovery mode boots you into single user mode, meaning root access so I am not entirely sure why that works? I am sure some1 with more experience can help IF you followed my guide to the "T" that is and that still didn't get you into your ubuntu install. and you tried all the boot options like irqpoll, noapic, nolapic then I am fresh out of ideas.

Check /var/log/Xorg.0.log

---

### Post by WhizCas on 2007-05-03
Yep already tried al those drivers in xorg. The error is that X freezes, I can't even acces tty so more I can't tell you. By the way I got ubuntu installed, so installing doesnt worries me. I dont even know if my ATI card is the reason... Shall I report my log here? And is that the log after the crash and rebooting in recovery mode?

---

### Post by dannyboy79 on 2007-05-03
no, don't post your log here, you're suppose to review it and see if something sticks out like the word ERROR and similar. Also, if you don't think it's your graphics card, check out the dmesg file as well, it's also  located within /var/log/

---

