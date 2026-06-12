---
title: "Ubuntu GNU GRUB installation NEED HELP"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by stephenstop on 2011-02-26
HELP! I am trying to install ubuntu 10.04. i had ubuntu 10.10 but i want to install 10.04 (32 bit) because 10.10 is slow. Problems with cd drive/cd caused installation to be incomplete so system cannot reboot at all.

I just tried the "Try Ubuntu without installing" option and got

Gnu Grub Version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-25-generic
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
Ubuntu, with Linux 2.6.35-24-generic
Ubuntu, with Linux 2.6.35-24-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtes86+, serial console 115200)

Which should I select? and what do I do to go on to install/reinstall 10.04?

PLEASE HELP

---

### Post by oldfred on 2011-02-26
That is your grub boot menu for 10.10, not the liveCD.

Did you check download that it was correct and burn at slowest speed. I seems like liveCD is not booting correctly.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Can you use USB install. I find that quicker and you do not use up CD's if a problem.

What was slow in 10.10? perhaps a minor fix will solve the issue. Or do not not have enough RAM to run Ubuntu?
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

---

### Post by stephenstop on 2011-02-26
Thanks for your suggestions.

I have Dell D610 Latitude that someone gave me with Ubuntu 10.10.  It has Intel Pentium M with 1.86Ghz.

The system would be slow and jerky when recording and making music on Audacity LMMS.  Also slow when using firefox .  I've been having problems with the sound (while using webcam and microphone...can't have both of them working at the same time).

Which reboot should I select from the list above?

---

### Post by oldfred on 2011-02-26
The first on the list is the newest and the default. You run recovery to try to get to a command line if you have problems. Sometimes an older kernel works where the newer does not, so we usually suggest keeping two kernels, but updates will keep adding over time.

How much memory do you have. Processor while not new should be ok.

You can use this in the command line to see what is running and if some process is using all the resources.
top

control c or q (or something to exit. I forgot.)

---

