---
title: "Ubuntu 11.10 won't install in my new system"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by oryctes on 2011-11-13
After receiving my new computer with Windows 7 pre-installed, and checked that everything was working fine. I reconfigured the partitions and prepared to install Ubuntu 11.10 (Oneiric).

But when running the Live CD, all the console messages were visible and after identifying all the hardware it just stopped wihtout any message.

I got the same situation using the Ubuntu 11.04 (Natty) Live CD. The Live CD's for Ubuntu 10.10 (Maverick) and Ubuntu 10.04 (Lucid) ran OK. I finally installed Maverick and it runs fairly Ok, but it does not load the NVIDA drivers so I can't use any hardware acceleration and I have no sound. (Even the hardware is identified correctly)

I tried to upgrade to Natty and the upgrade process finished correctly, but after rebooting I got nothing but a blank screen.

I tried to install from Windows using Wubi but it simply could not even start (the pyrun.exe told me that there wasn't any drive in \Device\Harddisk2\DR2).

I even tried installing Fedora 16 or Linux Mint 11. Same results:  after identifying the hardware they just stopped.

When I had Ubuntu Maverick installed, I tried the recovery mode and it showed the same messages that appeared while running the Live CD's, but after that it showed the recovery options and resumed without any issued.

When I tried the memtest86+ (4.10) included in Maverick,  it also froze.  I ran the lastest version of memtest86+ (4.20) and this time the program run normally and it didn't detect any issue.

I am completely lost. Any help will be greatly appretiated.


My computer specs are as follow

Dell Studio XPS 8300
Intel Core i5-2320 @ 3GHz
6 GB RAM DDR3 @ 1333 MHz
SATA HDD ST32000641AS 2000.3 GB
Video Card: GeForce GT 545
Sound Card: SoundBlaster X-Fi Xtreme Audio

---

### Post by bcbc on 2011-11-13
Boot the CD with the nomodeset option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
That's a common problem with nvidia cards.

If you still have issues booting the 11.10 CD, you may have a bad CD.

Then check this out: [http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html)

---

### Post by oryctes on 2011-11-13
.

---

### Post by oryctes on 2011-11-13
Setting the modeset option in the Live CD and then in grub did the trick.
The I could download the lastes nvidia drivers.

The system is up and running now. I'm still having some issues with the sound, but that's another matter.

Thank you very much.

---

### Post by bcbc on 2011-11-13
Great, you can mark the thread as solved from the Thread tools menu.

Good luck with the sound.

---

