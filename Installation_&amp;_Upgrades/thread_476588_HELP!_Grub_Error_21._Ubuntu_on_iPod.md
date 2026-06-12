---
title: "HELP! Grub Error 21. Ubuntu on iPod"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by MattZani on 2007-06-17
I've booted of the Live CD for a while, and thought it was pretty good, so i decided to install it onto my iPod. It all went smoothly, then it asked me to reboot, i went into my BIOS to tell it to boot off removable first, and then exited. It started to boot, then gave me Grub error 21, i restarted, unplugged my iPod, and the PC booted off the Hard Drive, then the same error came up:( Im now stuck booting off the Live CD again, just to ask for some help, as nothing will get my PC to boot off the Hard Drive or my iPod!

I installed it on my iPod so that i could easily choose which to boot into, whether the iPod was plugged in or not, and it was in Disk mode aswell.

I've read pages telling me to boot off my XP disk, but my PC was pre-installed with XP MCE 2005, and i don't think an XP Pro disk i have would work.

Any help would be greatly appreciated, i hope i haven't lost all my XP Data, as thats a year of GCSE Coursework down the crapper, aswell as all my Edited images, holiday photo's etc.

Thanks

Linux new comer/Lover Matt

---

### Post by confused57 on 2007-06-17
I'm not familiar with installing Ubuntu to an iPod or if an iPod even has a mbr...it appears that Ubuntu's IPL was installed to your internal hard drive's mbr.
Here are several ways to reinstall Window's IPL to your internal hd's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you have a Window's install cd(not a recovery cd), you might be able to boot into recover console, by pressing "r", then entering the command FIXMBR.

I recommend that you find access to another computer and burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download and is capable of booting Windows or Linux and restore either's IPL to the mbr...this would probably be your best option.

---

### Post by MattZani on 2007-06-17
Ok, i'll burn SuperGrub to a disc, and restore Window's IPL, and hopefully boot into windows.

Thanks

---

### Post by MattZani on 2007-06-17
Fixed, now boots into XP, now i need to work out how to Dual Boot, must follow the link in Sig.

---

