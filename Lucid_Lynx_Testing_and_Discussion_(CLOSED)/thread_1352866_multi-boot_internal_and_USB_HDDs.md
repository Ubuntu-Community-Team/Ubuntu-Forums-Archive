---
title: "multi-boot internal and USB HDDs"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-12-12
Hi

I have for a long time successfully had a set-up with Windows (7 and Vista) and stable ubuntu on my internal HDD and a dev Ubuntu (currently Lucid) on my USB HDD.

I enabled the BIOS boot from USB. If the USB drive was plugged in then it would boot from that, if not it would boot from the internal HDD. (i.e. grub was installed on both drives)
Both grubs were aware of the other drives so I could boot into either (if you see what I mean &#8211; although I would have to plug in the USB drive after getting to the grub menu from the HDD but before selecting the USB drive Ubuntu option!)

Recent updates to grub on my USB (Lucid) mean that this setup no longer works. When I boot from the USB I get the message 'error: the symbol 'grub_gettext' not found' and then go to a prompt
grub rescue>

Googling the error message gets some results which says 
[http://osdir.com/ml/debian-bugs-rc/2.../msg02604.html](http://osdir.com/ml/debian-bugs-rc/2.../msg02604.html)
'Hi,

There's no bug here. You installed different versions of GRUB to different
drives using the same /boot/grub/. One of them stopped booting because of
ABI incompatibility.'

Just tell the debconf template to install GRUB to each drive and you'll be ok.'

I don't know what debconf is our how to do this (may be Debian specific?)

(There is a similar problem raised in [http://ubuntuforums.org/showthread.php?t=1349438](http://ubuntuforums.org/showthread.php?t=1349438) but the OP seems to have solved this, and I'm not sure if the circumstances are similar enough to continue that thread)

I can work around this by disabling USB boot in the BIOS and then selecting the USB from the HDD grub, but I liked it the old way (I could automatically boot from a USB stick as well if needs be &#8211; now I would have to go into BIOS and re-enable the USB boot).

It seems to be a case of grub now not playing nice with two drives both having grub installed.

Can anyone help me to get back to my original position of being able to use grub from both the HDD and the USB HDD?

(BTW This is funny:
grub rescue> help
unknown command 'help'
try 'help' for usage)

---

### Post by ranch hand on 2009-12-12
Well, I am confused.  I have my bios set the same way and use an external enclosure for my test platform.

I have 2 internal drives and I keep them separated for booting too.

What drive did you update that screwed things? 

I think the best thing for you to do is run this script and post the results here;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I am sure that this can be straightened out without a lot of pain.  We just need ot know what we are working with.  This script is a wonderful tool.

---

### Post by ubername on 2009-12-12
> **ranch hand said:**
> Well, I am confused.  I have my bios set the same way and use an external enclosure for my test platform.

I have 2 internal drives and I keep them separated for booting too.

What drive did you update that screwed things? 

I think the best thing for you to do is run this script and post the results here;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I am sure that this can be straightened out without a lot of pain.  We just need ot know what we are working with.  This script is a wonderful tool.

Thanks

It was the USB drive I updated. My RESULTS.txt is too big (20K) to upload so I have split it.

edit - got to go out for a couple of hours - be back later - thanks for the help

---

### Post by ranch hand on 2009-12-12
I have to go to bed I will study this when my brain functions in a few hours.

---

### Post by VMC on 2009-12-12
> **ubername said:**
> Thanks

It was the USB drive I updated. My RESULTS.txt is too big (20K) to upload so I have split it.

edit - got to go out for a couple of hours - be back later - thanks for the help

Looking through your outputs, everything matches up - UUID's, fstab, grub.cfg's. 

Wat are these "other" devices that are plugged in:

```
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by ranch hand on 2009-12-12
OK, you really do have two versions of grub.  Your 9.10 should be running grub1.97beta4 and your 10.04-testing should be running grub1.97.  There are some differences.

I have only booted from an internal to boot it and my external usb HDD so I am not sure about how it works the other way.

What I would like to have you try is to go into your bios and turn off your internal HDD.  See if you can boot to the usb drive then.

If not boot to a LiveCD (9.10 or 10.04-testing) and follow these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the file editing instructions as this should not be needed.

This will, of coarse, get rid of all menu entries for your internal on your usb drive.  That is ok as we can get them back later.  Let us see if we can get it to boot by it self with no distractions.

As a side note, I can see where this would be handy, I have my internal shut off (in bios) right now.  I am running on 10.04 as my production OS during the day but I do not want any problems to be able to effect my internal drives.  I like them separated for safety.   At night I use a 9.04 install as my production OS and if I want to access the external I turn it on (it has a switch) and that gets me safe access for transferring data.

My idea here is to get the usb booting on its own and then seeing if we can boot to it from the internal (this may currently work you didn't say but it looks good).  then if that works you can, if you want, boot from the usb and run "update-grub" and see if it works again.

One thing at a time.  See if you can get the usb to boot by itself.

---

### Post by ubername on 2009-12-12
thanks vmc and ranch

the 'other' drives are various sd card readers etc (the pc came with one of those '7 in 1' readers.

I will see if I can get the USB to boot with the internal drive disabled.

FWIW I can boot into the USB from the HDD grub (currently positing from there)

---

### Post by ubername on 2009-12-12
No joy trying to boot from USB

First I tried disabling the internal HDD as a boot device
Next I completely disabled it

In both cases I get the same 'grub_gettext' error.

---

### Post by ranch hand on 2009-12-12
This seems like the only bug I can turn up;

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg719668.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg719668.html)

If you follow the links at the bottome of the page you can read about his ordeal.  I assume that the problem must be related to memtest86 as we do not have "grub-invaders" (a game that you can start from grub) installed by default (if you have it - loose it).

He seems to have removed and reinstalled grub several times, I thinks you may need to do that but I would try deleting the memtest86 stuff first (actually I would just change the name so that it ended in .OLD  so that I can find it easily to put it back if needed).

If you are going to have to reinstall grub anyway it can't hurt to try it.

---

### Post by VMC on 2009-12-12
I'm still curious about those "other" devices.

I had this issue with booting a usb device and my usb camera plugged in at the same time. It started to boot then made some off the wall comment that the kernel was corrupt. I then realized that the camera was plugged in. I unplugged the usb camera and all was well?!?!

Just a thought.

Also, I was thinking as Ranch Hand was thinking. I was going to suggest to unplug the ide or sata internel hard drives, but RH's advice is a simpler and a better solution.

---

### Post by ubername on 2009-12-12
Result!

I reinstalled grub-pc and removed the execute permission from 20_memtest86+ in /etc/grub.d.

Sorted!

Thanks for finding the link, Ranch
Now to get my Desktop back, and a working Nautilus.....

---

