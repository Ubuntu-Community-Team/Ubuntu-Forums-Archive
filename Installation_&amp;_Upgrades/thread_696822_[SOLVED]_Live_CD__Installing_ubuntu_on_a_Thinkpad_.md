---
title: "[SOLVED] Live CD / Installing ubuntu on a Thinkpad T61p"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by StrangeBrew on 2008-02-14
I'm trying to install ubuntu 7.10 on a T61p, 64608VU, Intel Core 2 Duo T7700, WUXGA, nVIDIA Quadro FX 570M.  Sabayon live DVD is the only live CD that will run on it.   Every time I try the ubuntu live CD it acts like it will start, then the screen goes black, it's on just black.  The same thing after installing with the ubuntu alternate CD.  I can boot with the Sabayon CD and I can look at the hard drive, and ubuntu formatted it and the file system is there.  I've changed the SATA in the BIOS from ACPI to Compatability and that hasn't made a differnece, only it ran slower in Comapatability mode and I could read what was scrolling on the screen before it goes black.  I'm extremely frustraited right now.

---

### Post by Rocket2DMn on 2008-02-14
The reason it gives you a black screen is because it doesn't like your video card (yet).  What is your video card make/model.  You can reconfigure X by following this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If the open source drivers don't work, then you will need to install the proprietary drivers, but please post your card model and I will advise you on that.

---

### Post by StrangeBrew on 2008-02-14
thanks, it has a nVIDIA Quadro FX 570M

---

### Post by StrangeBrew on 2008-02-15
Is there another way of getting to a tty? Nothing happens when I press CTRL+ALT+F1.

---

### Post by Rocket2DMn on 2008-02-15
You can use F1 up through F6, but if those don't work, you can reboot into recovery mode kernel which gives you a root terminal, so you can run the reconfigure command from there (no sudo needed)
```
dpkg-reconfigure xserver-xorg
```
When it's finished, reboot into normal mode.

---

### Post by StrangeBrew on 2008-02-15
I booted from the alternate CD and used rescue mode.  This is the error...

unknown terminal: bterm
check the TERM environment table, Also make sure that the terminal is defined in the terminfo database.
Alternatively, set the TERMCAP environment variable to the desired termcap entry.
debconf: whiptail output the above errors, giving up!

---

### Post by Rocket2DMn on 2008-02-15
Sounds like the rescue mode on your alternate cd isn't functioning correctly, but that's not what I asked you to do (it's a separate issue).  Recovery mode is an option at the GRUB menu, right below your normal boot kernel.  It takes you to a root terminal, so you can run dpkg-reconfigure from there, no cd needed.

---

### Post by StrangeBrew on 2008-02-15
GRUB wouldn't install, so I had to install LILO. Is there a way to interupt or modify LILO so I can get to recovery mode?

---

### Post by Rocket2DMn on 2008-02-15
I don't know anything about the LILO bootloader, but you might be able to setup a recovery mode by modifying its options to include booting into the kernel is single user mode (runlevel 1).
Otherwise, here is a redhat little guide for getting to single user mode - [http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html)

---

### Post by StrangeBrew on 2008-02-15
I got to the single user mode with CTRL + "x" then entered 

linux single root=/dev/sda1 initrd=

Then I followed your directions to reconfifure. Went through all the steps manually. Started gdm and got this error 6 times.

The greeter application appears to be crashing. Attempting to use a different one.

After all that the following come up...

The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad is going on (no kidding!). Waiting for 2 minutes before trying again on display :0.

---

### Post by StrangeBrew on 2008-02-15
After trying many different settings in the reconfiguration. I got one that would work.  Now I can go about getting the notebook set correctly.

thanks for your help!!!

---

