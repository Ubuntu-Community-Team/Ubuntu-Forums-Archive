---
title: "ubuntu install"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by pesach on 2006-09-11
So I built a computer and I want to install Ubuntu on it.
I made the "server cd" but when I put it into the cd-drive adn had it boot from cd, all I got was a boot from cd window that has yet to go away.  WHat do I do?!:confused:

---

### Post by pesach on 2006-09-11
I jst checked on the computer again and know it says that there was a system boot failure and I should insert cd and press enter. I did so, and know the whole proccess is starting again...

---

### Post by confused57 on 2006-09-11
See this guide for burning an iso:
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

Here's a thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=255734](http://www.ubuntuforums.org/showthread.php?t=255734)

---

### Post by pesach on 2006-09-12
I followed the instructions on that webpage and the disk was made succesfully.  I put thr disk in and it installed.  But when i restarted the computer, it would not boot from the hard drive.
(I did check and change the BIOS boot settings to hard drive)

---

### Post by pesach on 2006-09-12
Is there anyone out there who can help?

---

### Post by confused57 on 2006-09-12
Have you checked the jumper settings on the hard drive( master, slave, or cable select) and is the hard drive enabled(or set to auto) in your bios?

Knowing your system specs could possibly help someone come up with a solution for you.

You might want to try the desktop live cd, if you have enough memory(at least 256 mb, may or may not run on 128 mb)...the live cd can be useful to determine how well linux will run on your pc.

---

### Post by pesach on 2006-09-13
I was using the desktop live cd the entire time.. it worked I just could not use the computer after linux was installed and the cd was removed.  The BIOS setting are set to 1.Hard drive 2.cd 3.empty(I have no floppy). And the hard drive is set to master. 512mb RAM

---

### Post by pesach on 2006-09-13
so what do I do know?

---

### Post by d-train3054 on 2006-09-13
What is it doing after you installed from the new cds?

Check to make sure you don't have any USB storage devices plugged in to the computer (flash drive, ext hard drive, or other USB device). Sometimes during the boot process the computer waits for responses from those devices but never gets one.

---

### Post by confused57 on 2006-09-14
> **pesach said:**
> so what do I do know?

Open a terminal and post the output of:
```
sudo fdisk -l
```
The -l is a lowercase "L".

You could also try reinstalling grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

Also, did you check in your bios setup if the primary master IDE controller was set to "auto" or something like "lba"?  I'm not referring to the boot order,i.e. setting the hard drive to boot first...there should be a menu that points to hardware devices(specifically IDE, which I assume you are using since you have the hard drive set as master) and that your bios is correctly identifying your hard drive.

---

### Post by pesach on 2006-09-14
> **d-train3054 said:**
> What is it doing after you installed from the new cds?

Check to make sure you don't have any USB storage devices plugged in to the computer (flash drive, ext hard drive, or other USB device). Sometimes during the boot process the computer waits for responses from those devices but never gets one.
no usb conections, hard drive is recognised and after I installed form the new cd's it prompted me to restart(which I did)

---

### Post by pesach on 2006-09-14
and confused, I tried what it told me to do and it didnt work

---

