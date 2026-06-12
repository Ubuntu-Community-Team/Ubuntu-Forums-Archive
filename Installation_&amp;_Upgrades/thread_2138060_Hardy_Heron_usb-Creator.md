---
title: "Hardy Heron usb-Creator"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by Seeker84 on 2013-04-22
I'm trying to create a Ubuntu Live USB.  From what I've gathered, usb-creator is a good way to do it.  But when I search Synaptic, and the Add/Remove for usb-creator both come up blank.

I tryed to use terminal:
```

sudo apt-get install usb-creator*

sudo apt-get install usb-creator.*

```
but terminal says it can't find the package.

I found a post here: [http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html](http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html), which took me to here: [https://launchpad.net/ubuntu/intrepid/i386/usb-creator](https://launchpad.net/ubuntu/intrepid/i386/usb-creator), which says obsolete all over it.  I also read from Scot's Newsletter, linked in the first site, that the last two releases had bugs in them.

So I'm stuck, I do not know how to get usb-creator on my system.  Please help.

---

### Post by kurt18947 on 2013-04-23
It appears that the earliest version of *buntu for which usb-creator support exists is 10.10.
[http://www.linuxliveusb.com/en/supported-linuxes](http://www.linuxliveusb.com/en/supported-linuxes)
> **These versions should work but I will provide no support whatsoever:**

 
[LIST]
[*]Any modified variants of the supported versions (like translated ISO) 
[*]Any Linux using syslinux or grub and USB boot capable (most of them are) 
[*]Any non "Live" version of the supported Linuxes (but only for booting and installing on disk since they are not "Live") 
[/LIST]


You want to install on 8.04.  The above sort of suggests that what you want to do might be possible but you're on your own.   Good luck.

---

### Post by Cheesemill on 2013-04-23
Are you really still using 8.04?

You do know that it hasn't been supported for 2 years now don't you?

---

### Post by Seeker84 on 2013-04-26
I really am using 8.04, I'm trying to upgrade, but I'm having trouble getting the right programs to make a USB live from Hardy.

---

### Post by mörgæs on 2013-04-27
You don't need applications in order to create a USB installation stick. 

First, please insert the USB stick and run (for example) ```
df -m
``` It will show you the name of the USB stick as well as the space available.

---

### Post by Seeker84 on 2013-04-27
> **mörgæs said:**
> You don't need applications in order to create a USB installation stick. 

First, please insert the USB stick and run (for example) ```
df -m
``` It will show you the name of the USB stick as well as the space available.

I don't really see how the df command will help if all it's doing it reporting what memory is available on the USB stick.  Since I'm attempting to put ubuntu 12.10 on the USB stick, I don't understand how the getting the name of the stick will help.

---

### Post by Dennis N on 2013-04-27
> **Seeker84 said:**
> I don't really see how the df command will help if all it's doing it reporting what memory is available on the USB stick.  Since I'm attempting to put ubuntu 12.10 on the USB stick, I don't understand how the getting the name of the stick will help.

It also gives you the device information needed make the bootable usb with dd (bit-by-bit copy). You can determine whether the usb stick is sdb, sdc, etc. 

No usb creator is necessary with bit-by-bit copy. For the process, see:

[http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device](http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device)

Then in the first answer given, read from where it says "Or you could try a bit-by-bit copy:"

---

### Post by Seeker84 on 2013-04-28
I did some real round about ways of doing things.  I needed my second computer to try this as I didn't seemto be getting anywhere with ubuntu's stuff.  The second computer is a windows XP machine.

I tried to find a usb-creator for Hardy, which failed miserably.  Couldn't find a way to install 1.8 because that was the version that didn't have a bug in it, both 1.9 and 10 did, but can't confirm.

I tried LinuxLive USB Creator, but I tried to use the USB key and it gave me missing operating system errors on boot.  I tried to use the BootICE.exe program to change the type of format of the USB key, that also didn't change the outcome.

I thought my isos weren't good, so I started making Live CDs, I knew if I got them to work, I could try to use the Usb-creator already installed on them.  This is where some light starts to come in...

12.10 gives me an error about PAE, apparanetly my computer doesn't support PAE.  A site directed me to a workaround whish was to install older version of ubuntu then update, fair enough.  I made CDs all the way down to 9.04.   This Live CD worked, then I tried the usb-creator on it.  I was getting the same result of missing operating system.

Here's the kicker, after doing some research this morning, I found out why the USB key was not booting.  I had updated the BIOS for my Dell Inspiron 700m, version A07, In the notes from dell about this update, it said that it fixed the issue with booting the USB key when the selection was not in the first slot of the BIOS boot priorities.  So I changed this, I set the USB key to be first in the list, and EUREKA!!!!!!

Dell's BIOS article here:[http://www.dell.com/support/drivers/us/en/04/DriverDetails/Product/inspiron-700m?driverId=R120447&osCode=WW1&fileId=2731111163&languageCode=en&categoryId=BI](http://www.dell.com/support/drivers/us/en/04/DriverDetails/Product/inspiron-700m?driverId=R120447&osCode=WW1&fileId=2731111163&languageCode=en&categoryId=BI)

I'm going to try linuxliveCD again, see if this new found discovery was my issue with booting from USB key.  I'll report back.

---

### Post by gordintoronto on 2013-04-28
There are several suggestions here:
[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present) 

Since the computer is obviously an older model, you might find Lubuntu or Xubuntu better options. If the computer has less than 1 GB of memory, you might find you are limited in how much you can do at once, even with Lubuntu or Xubuntu.

---

