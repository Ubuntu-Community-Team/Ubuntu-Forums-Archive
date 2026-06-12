---
title: "Installation Problem"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by NexyPlays on 2011-02-19
I want to switch from Windows 7 (32-bit) to Ubuntu 10.10 (32-bit), but I can't install it on my PC for some reason. I've tried burning the .iso onto 2 or 3 different DVD+ROM discs now, I keep getting the following message when I try to install it.

Message:
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Does anyone know what I should do?

Thanks.

Edit:  I got it to work, I'm not sure if this actually made any difference, but I formatted my hard drive using my Windows 7 installation DVD before trying to install Ubuntu 10.10.  But it worked fine after that and I'm now running it on my PC without any problems (at the moment).  Thanks for the help anyway guys!

---

### Post by Sean Moran on 2011-02-19
> **NexyPlays said:**
> I want to switch from Windows 7 (32-bit) to Ubuntu 10.10 (32-bit), but I can't install it on my PC for some reason. I've tried burning the .iso onto 2 or 3 different DVD+ROM discs now, I keep getting the following message when I try to install it.

Message:
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Does anyone know what I should do?

Thanks.
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

That means that the problem is with /casper/filesystem.squashfs which is the main filesystem that 'unsquashes' to start your Live-CD session.  It seems unlikely that three different burns would all be due to faulty media, although I wonder if it might be wortk burning the .iso to CD-ROM, rather than DVD.  It's beyond me to know for sure, but DVDs and CDs are somewhat different, so just a possible maybe on that one.  I've never tried to burn a CD .iso to DVD so maybe it works just as well.

Other than that, check the MD5SUM for the .iso because that might be flawed, and if not, try, try another blank CD.  I hope someone else might see this problem and know an easier fix.

---

### Post by Rubi1200 on 2011-02-19
As mentioned, try a CD not DVD.

You could also try from a USB stick.

I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

For the checksum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rickbeton on 2011-02-19
If you're stuck, there are free CDs available.

[http://www.ubuntu.com/desktop/get-ubuntu/cds](http://www.ubuntu.com/desktop/get-ubuntu/cds)

Rick

---

### Post by NexyPlays on 2011-02-19
I've tried a dvd, a cd like you said and alo a usb.  They all give me the same error message.

---

### Post by Rubi1200 on 2011-02-19
Did you check the md5sum? (link in my previous post)

Did you set BIOS to boot from the CD-ROM drive/USB drive?

---

