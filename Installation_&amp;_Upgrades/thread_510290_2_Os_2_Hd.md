---
title: "2 Os 2 Hd"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by yarayara on 2007-07-26
Hi,

I have Winsucks OS in my computer and I just bought a new hard drive. Can I install ubuntu in the second HD and boot from there to both OS??

How can I do that?

thanks!

---

### Post by beameup on 2007-07-26
About to do that myself. I'm pretty sure the bootloader has to be installed on the first hard drive. Still researching and I'l post my findings when done.

---

### Post by DJMatty on 2007-07-26
I think it depends on your bios, some will let you specify which HD to boot from first.

You can install ubuntu on your second HD and have the boot loader install itself to the MBR of the first HD, it will still let you boot into both o/s's.

---

### Post by Palypup on 2007-07-26
2 hd & 2 os can be tricky. The key to remember is to isolate the one you are working on.
I have 3 hd & 3 os. I have screwed this up many times and finally figured out that when
I do an install, disconnect the power or data or both to the hd's that you want to preserve.
Then do your install on the new hd,(it is isolated, alone and the only hd hooked up) test it, 
then re-connect your disconnected hd. When you boot, press Del (or whatever gets you into
your bios), select the hd with the os you want. This way, each hd thinks it is the C: or main
boot drive. Once you are up and running, you can decide if you want to modify Microsoft (XP?)
boot.ini to allow for boot to Ubuntu **or**, modify grub in Ubuntu to allow for booting to XP.
I haven't done either of the last two, but everyone else has. I am afraid of screwing this up, and
it works for me as is.

---

### Post by dabl on 2007-07-26
If your first hard drive is an IDE/PATA drive, you can think of that of that one as a "Grub-magnet".  So, the quickest way to dual boot with Win XP is to install Win XP first, on the first partition of the first hard drive.  Then you can make your "/" (root partition), "/home" partition, and swap partition anywhere on the two drives, but when you get to the Grub installation stage, just let it install to the MBR where Win XP.  Don't spend 3 days fighting it like it did!  :)

If you want to get fancy (and have plenty of patience), here's reasonable guidance: [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by yarayara on 2007-07-26
thanks everyone;

Im having a hardtime.

my hardrives (both) ar westerndigital 250G... sata

for some weeks, Ubuntu will just not recognize the HD. I tried with all, Ubuntu 4, 5, 6, 7 Desktop and Server. Finally, I got to install it (i stop trying for some days, dont know what happend) and everything was fine, but I used the automated install with only 2 partitions, so I tried to  install again with partitions for user, home, etc...
and now I get the following message:

/bin/sh: cant acces tty; the job control turned off
(initramfs) [ 206.788037] ata6.00: failed to set xfermode (err_mask=0x40)

and thats about it  =(

about which one will  be 1st and which one 2nd, I can reinstall windows and make it the second, at the moment I really need to make ubuntu work.

thanks!!

---

### Post by beameup on 2007-07-29
Mine went OK, Grub is on the first drive and all is Ok, except the nvidia drivers diddn't load. My Xorg.conf just shows Generic, so I'm searching the forum and I'll make another thread on that issue if i have to.

---

### Post by wombil on 2007-07-29
Hello yarayara,
Did the same thing lately.Just installed ubuntu 7.04 on the secondary ide with ubuntu as master and dvd-cd
rom as slave. Not sure if I disconnected the drives on the primary ide. Went like a dream,after the post you can select which os to boot.Ubuntu has put itself first on mine but you can change that.I haven't bothered.Good Luck with it.

---

### Post by manndani on 2007-07-29
A good link here. 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
good site for all tutorials on Ubuntu etc.

---

