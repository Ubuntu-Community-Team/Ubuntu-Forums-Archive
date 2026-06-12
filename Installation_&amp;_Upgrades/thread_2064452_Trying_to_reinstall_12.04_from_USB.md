---
title: "Trying to reinstall 12.04 from USB"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2012-09-29
. . . but I cannot get my Asus G74 laptop to boot from the memory stick.
I can explore the stick from win7, and the files are there.

Tried going into my setup prior to boot, tried to add the usb as a boot device, but I don't see where that is working.  I can select the usb, and the file system that shows is staple and some numbers - that is the only choice (staples is where I purchased the memory stick).

I'm guessing that I should be seeing some file, but perhaps not.  I don't see any files for the HD (boot option #1) or the CD/DVD drive, so perhaps this is correct.

Unfortunately, nothing I know how to try seems to have any affect.

I will probably have to burn a CD/DVD as usual.

Any suggestions welcome.

Thanks.

Caruso

---

### Post by 2F4U on 2012-09-29
How did you create the usb stick? On Windows, you can use a usb installer:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by carusoswi on 2012-09-30
> **2F4U said:**
> How did you create the usb stick? On Windows, you can use a usb installer:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

I had used another process, but decided to try your recommendation.

It did not recognize my USB stick, but I had a disc in my CD/DVD drive, so directed the install/burn routine to that location.

Disc burned fine, but attempts to boot to that disc stalled at some Ubuntu specific screen that displayed some Ubuntu Icons, but no other information.

What really could be wrong with my system?  I have never had problems with Ubuntu before.  I am getting very frustrated.

Thanks for your reply.  Your link seems to have worked well, but, unfortunately, my issue remains unsolved.

Caruso

---

### Post by akoskm on 2012-09-30
You should check the integrity of the downloaded ISO file. 
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
Corrupted ISO files can lead to unexpected behavior.

---

### Post by 2F4U on 2012-09-30
> **akoskm said:**
> You should check the integrity of the downloaded ISO file. 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Corrupted ISO files can lead to unexpected behavior.

Yes, either that or a bad burn. Anyways, sounds more of a problem with the way the liveCD was created than actually a hardware problem.

---

### Post by carusoswi on 2012-09-30
> **2F4U said:**
> Yes, either that or a bad burn. Anyways, sounds more of a problem with the way the liveCD was created than actually a hardware problem.

I ran the install from the CD.  My Grub did not come up after the process finished.  I got this message:

Error: No such Device: cc596efs-2ad9-46f4-93e6-0f1546d9fce6

Now, of course, my blood pressure is starting to rise.  A second install try did not help.

Fortunately, I had a cd with ubuntu 10.10 on it, so I installed that, and my grub (or a new version of it) was restored.

I'm typing from my Win7 OS, now.  Will try to download 12.04, and, if I can work up enough courage, I may retry an install.

Would have been a major problem if I could not have regained access to my Win7 partition.

I don't believe I made rescue discs, but couldn't locate them when I needed them.

Thanks for your replies.

Caruso

---

### Post by oldfred on 2012-09-30
Is this a new system with UEFI? If so have you downloaded the 64bit version of Ubuntu? Only the 64bit version is UEFI aware. 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are using the nVidia card you probably also need nomodeset. If you get the accessibility icons at the bottom of the screen right at the beginning hit any key. If not try tab. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by carusoswi on 2012-09-30
Ok, I downloaded the iso again, burned to a new disc, ran the installation, this time, everything worked well.

Thank you all for your replies/suggestions.

Caruso

---

