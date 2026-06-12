---
title: "Can no longer boot"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by moogyd on 2010-11-15
Hi,
I have dual boot (10.04/Windows XP) system, and until today, everything was working OK (SIngle Hard Disk with multiple partitions)

Today, I select Ubuntu from Grub, and it fails to boot. There are lots of log messages on the screen, and then it seems to jump into memfs (?) and busybox.

Windows boot is fine, so the disk is OK.

I then tried booting from Live USB stick (same one I used for installation). This shows the menu - I select run from USB, and it gets as far as the splash screen with 5 pips and the Ubuntu logo and then seems to lock up.
If I hit ESC, it shows

can't open /dev/sr0
can't open /dev/sr0
unable to open /dev/sda

I guess that /dev/sda is my hard disk (? although my disk is not SCSI, so this may be a little strange).

Any ideas how to recover from this, or at least investigate further - I get a feeling that without livecd, it will be difficult.
Thanks,

Steven

---

### Post by ccrs8 on 2010-12-08
> **moogyd said:**
> Hi,
I have dual boot (10.04/Windows XP) system, and until today, everything was working OK (SIngle Hard Disk with multiple partitions)

Today, I select Ubuntu from Grub, and it fails to boot. There are lots of log messages on the screen, and then it seems to jump into memfs (?) and busybox.

Windows boot is fine, so the disk is OK.

I then tried booting from Live USB stick (same one I used for installation). This shows the menu - I select run from USB, and it gets as far as the splash screen with 5 pips and the Ubuntu logo and then seems to lock up.
If I hit ESC, it shows

can't open /dev/sr0
can't open /dev/sr0
unable to open /dev/sda

I guess that /dev/sda is my hard disk (? although my disk is not SCSI, so this may be a little strange).

Any ideas how to recover from this, or at least investigate further - I get a feeling that without livecd, it will be difficult.
Thanks,

Steven

Did you ever get this resolved?  I am experiencing the exact same thing now.  Can't boot to Ubuntu and now can't boot using live usb drive. Unable to open 'dev/sda'  Only difference is that I don't have dual boot with Windows - only Ubuntu.

---

### Post by moogyd on 2010-12-09
> **ccrs8 said:**
> Did you ever get this resolved?  I am experiencing the exact same thing now.  Can't boot to Ubuntu and now can't boot using live usb drive. Unable to open 'dev/sda'  Only difference is that I don't have dual boot with Windows - only Ubuntu.

No real solution, I ended up doing a fresh install.

Even this was not straight forward (since live CD doesn't work). I think a eventually used gparted livecd to boot and then reformat (loosing all the data).

I did search at the time, but could not find any other solution.

Good luck,

Steven

---

### Post by wilee-nilee on 2010-12-09
n

---

### Post by karthick87 on 2010-12-09
Can you post your results of [[COLOR=DarkRed]bootscript[/COLOR]]("http://bootinfoscript.sourceforge.net/")

---

### Post by sikander3786 on 2010-12-09
> **ccrs8 said:**
> Did you ever get this resolved?  I am experiencing the exact same thing now.  Can't boot to Ubuntu and now can't boot using live usb drive. Unable to open 'dev/sda'  Only difference is that I don't have dual boot with Windows - only Ubuntu.
I would recommend to check the MD5SUM of downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you are booting from disc, check the disc for defects or burn a new disc at lowest possible speed. (4X)

If booting from USB drive, it would be worth trying to use another USB creation program.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If the image is ok and the disc is ok and still you can't put, try putting in some boot parameters by pressing F6. There are 6 of them and you need to try each of them one-by-one.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

And at last, just make sure your Bios is set to boot from the disc or the USB drive, whichever appropriate.

---

### Post by ccrs8 on 2010-12-09
I tried unetbootin to create another usb boot drive, but other than the fancier initial menu, any choice I made ended with the screen hung on "Ubuntu" with the five dots below.  Pressing ESC came up with the same messages.  I then used my wife's Windows computer (ugh...the shame) to burn a CD, and that allowed me to boot all the way in to the live disk environment.  In that environment I was able to see my hard drive without problem, so it wasn't anything physical with the disk.  I backed up my data to a USB hard drive (I had already done that a few weeks ago so there wasn't much more to grab) and then I went about the instructions found here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Unfortunately, it gave me errors that the author had not seen before, and at that point I just decided to do a clean install.  /home was on a separate partition so it wasn't a huge loss or anything like that.  Once I used the live CD instead of the live USB and was able to at least get in to a live environment, thankfully that was an option.  Not sure what I would have done had I not been able to do that.  Very strange - all this because I wanted to watch a Hulu video (that's what I did right when the computer started acting funny and wouldn't load anything...I rebooted and this whole cycle started)

EDIT: I just found out that the GRUB purge and reinstall I attempted didn't work because I don't know how to read.  If anyone comes across this and has the same problems I or the original poster of this thread had and got as far as me, give the instructions in that thread a try.

---

