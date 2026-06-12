---
title: "Lubuntu 10.10 image not loading"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by epp on 2010-12-26
Is there a known problem with the Lubuntu 10.10 image [ here](http://people.ubuntu.com/~gilir/)?  I have downloaded it to two different computers, then burned the images to two different blank CD's (different brands) and neither loads.

Both only get as far as the Lubuntu menu, once ENTER is pressed at that point to load the LiveCD, a blank screen eventually appears with a flashing cursor at the upper left of the screen, that's it..  

They were both burned using the slowest burn speeds available.

---

### Post by karthick87 on 2010-12-26
Have you checked the hash code of that image??

---

### Post by dino99 on 2010-12-26
your url is from a dev, maverick is released now

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

choose the slowest speed to burn

---

### Post by epp on 2010-12-26
Yes, the MD5SUM matched on both.  Apparently, once the black screen with flashing cursor appears, the computer crashes at that point.  The Num Lock light remains on when that key is pressed.  The only way to reset is to power the system off.

Other images (non-Lubuntu or 10.10) will boot fine though.

---

### Post by dino99 on 2010-12-26
try either : noacpi, nomodeset when booting (remove "quiet splash" to be able to see errors)

---

### Post by epp on 2010-12-26
Same result with noacpi and nomodeset (with "quiet splash" removed).  I also tried "acpi=force" and "reboot=warm" which relates to the information below, with the same result (system crash).

This system has a 32-bit AMD Athlon CPU inside it.  I had some difficulty installing Ubuntu on this at first.  Apparently, something relating to SCSI drivers changed during 2008 and **all** LiveCD's I tried since then, would (like this) not load in on this system.  Rather than a total system crash (from the Lubuntu 10.10 LiveCD), the distros from 2008 onward would eventually display various I/O errors when loading in.

But distros from 2007 and earlier, would run (and install) perfectly.

In order to get Ubuntu successfully on this system, I had to install Ubuntu 7.10 first, then upgrade it to 8.04 LTS, then upgraded 8.04 to the current 10.04.1 LTS.  Because a reboot would not reboot the system, the boot parameters required "acpi=force" and "reboot=warm", in order for this system to reboot itself and power off correctly.  These two parameters must be added back into /boot/grub/menu.lst every time the kernel is updated with a new revision number, as it is using the original version of GRUB from the 7.10 installation.

I wanted to try 10.10 to see if it would at least run, but the image will not boot...

I also tried a different distro's LiveCD, only to get the same result (system crash).  So I don't know what's wrong.

---

### Post by epp on 2010-12-28
Any other ideas???  I'm stumped.  :(

---

### Post by Quackers on 2010-12-28
Have you checked the cd for errors? Press F6 during boot and you should get the option to check.

---

### Post by epp on 2010-12-28
I did not check either CD for errors, but I will do that.

I also ran one of the CD"s on a 64-bit computer and it flew right through, no problems whatsoever, so I would presume there are no errors on at least one of them.

---

### Post by Quackers on 2010-12-28
It's not a 64 bit image is it?

---

### Post by epp on 2010-12-28
I posted the link to the image in my original post.  As far as I know, it is a 32-bit image.  If it *were* 64-bit, I don't think I would have even seen the menu come up. :)

Not even the media check would work, it also caused the same crash.  I also tried to load it (with the failsafe selections on the F6 menu), which also caused the same crash.

---

### Post by epp on 2010-12-28
Quackers - In [http://www.ubuntuforums.org/showthread.php?t=1649029](http://www.ubuntuforums.org/showthread.php?t=1649029) you mentioned removing "quiet splash" and replacing it with "nomodeset" for someone having the same problem (cursor at upper left) with Ubuntu Studio, *although CTRL-X would not boot, I had to press ENTER at the end of the boot parameter line*.

I also tried the above, with the same end result.

Your message also mentions exploring other boot prompts for the graphics card, here is the system specs:

System:  Compaq Presario 5900Z
CPU:  AMD Athlon (32-bit) 600MHz
RAM:  256Mb (max'd out)
Video:  S3 Savage-based AGP card (16Mb video memory)
Audio:  Creative SoundBlaster Live 5.1 PCI card

I'm wondering if perhaps there might be a generic VGA-related boot parameter that could be used??  I do have another video card that I could install in this system, a 3dfx Voodoo3 2000 PCI (also with 16 Mb video RAM on-board), but I do not know whether switching the video card might cause problems with the already installed system...

---

### Post by OneMixDJ on 2010-12-30
I'm having a similar problem.

After downloading the Lubuntu iso 3 times and 5 burned CD's, I ended up with a LXDE GUI with an install icon in the top left corner that doesn't run when you click to begin. I even let the machine sit overnight to do its thing and still nothing.

So then I tried a different approach:

Installed Ubuntu Intrepid
Upgraded to Jaunty
Upgraded to Karmic

Then followed the steps in Lubuntu.net under:
_Install Lubuntu from Ubuntu or any Ubuntu flavors_

[i]sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-desktop[/i]

I ended up with Ubuntu Karmic with an LXDE desktop option, and not Lubuntu. :(

Now I'm confused.  :confused:

---

