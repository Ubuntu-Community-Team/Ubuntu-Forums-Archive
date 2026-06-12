---
title: "I really screwed up"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by fatesjoke03 on 2008-10-29
Okay, here is what has happened so far.

I am locked out of BIOS, so I cannot change the boot order but if I remove the hdd at boot it will go to CD and then I can re-seat the hdd.

I had Hardy installed and all was fine, I went to create a compressed backup and that worked fine (wasn't able to burn it though) but when I went to delete the back up it said I did not have permission to. So I went to the user menu and unlocked the option (big mistake) I then set my directory as "/" and tried to delete the file. Turns out that did not work but I managed to use nautilus eventually and do it.

Problem is, I did not change the permission back and rebooted.....to a GRUB error #15. I figured I could delete the partition using a LiveCD and reinstall. I can delete the partition but the MBR is still there it seems because if I take the LiveCD out and boot I get the same error.

There is nothing else on the hdd, it is a single boot system. It is 160 gigs but only shows a 143 gig partition. I tried to wipe the drive using UBCD but still there.

I have tried a lot of the suggestions on this forum but they all seem to assume that there is something on the hdd to pull from. That does not seem to be the case here.

Any ideas? Anything I can post that might help?

---

### Post by ujodarko on 2008-10-29
> I am locked out of BIOS...

Can removing and putting the battery on motherboard solve this problem? I heard that removing the battery makes date&time reset as well as BIOS password!

---

### Post by ivaarsen on 2008-10-29
Oh yes.  Remove the battery to set the mobo to default.

But I'm not sure that's the problem.  Something is definitely hanging out in the MBR.  (Curse me)Can fixmbr help?

Is there any way to mount the drive during a live boot and use a program to write zeros to the drive?  Forgive me I don't know the name of such a program, I've never had to REALLY format a hardrive.

---

### Post by caljohnsmith on 2008-10-29
If you want to delete the boot loader portion of the MBR (Master Boot Record) in order to get rid of Grub, you could run:
```
sudo dd if=/dev/zero of=/dev/<your HDD> bs=440 count=1
```
Then you shouldn't get any more Grub errors. :)

---

### Post by fatesjoke03 on 2008-10-30
> **caljohnsmith said:**
> If you want to delete the boot loader portion of the MBR (Master Boot Record) in order to get rid of Grub, you could run:
```
sudo dd if=/dev/zero of=/dev/<your HDD> bs=440 count=1
```
Then you shouldn't get any more Grub errors. :)

This is what I got from that:
1+0 records in
1+0 records out
440 bytes (440 B) copied, 0.00799554 s, 55.0 kB/s



Does not seem to have done anything though.

There is no CMOS battery that I can locate. Forgot to mention this is a laptop. I was running Hardy on it before with no problem though.

---

### Post by fatesjoke03 on 2008-10-30
Restarted just to check. Same error.

---

### Post by caljohnsmith on 2008-10-30
Based on the output you posted, the dd command did work, so which drive did you specify as <your HDD>? How many drives to you have? Please post the output of:
```
sudo fdisk -lu
```

---

### Post by fatesjoke03 on 2008-10-30
Here is the fdisk -lu output:

[COLOR="DarkGreen"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9ef35bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   312576704   156288321   83  Linux
[/COLOR]

I tried [COLOR="Green"]sudo dd if=/dev/zero of=/dev/<your HDD> bs=440 count=1[/COLOR] on sda and sda1, hell I tried it on sda2 and sda3 just to see what would happen and I got responses from all.

---

### Post by fatesjoke03 on 2008-10-30
caljohnsmith,

You rock, that did it. I am all good to go now. At reboot I got the blank cursor showing my hdd was blank. I am rebooting into a LiveCD now to confirm the volume of the drive is right and then going for another install.

Lesson learned: Do not unlock options in the menu, lol.

---

### Post by fatesjoke03 on 2008-10-30
Okay, the hdd is still showing the wrong size and shows that 1.4 gigs are used. I am going to try and reinstall anyway and see what happens.

---

### Post by caljohnsmith on 2008-10-30
Probably the HDD still shows 1.4 GB used because that dd command you ran only deletes the Grub boot loader code in the MBR (Master Boot Record); if you want to delete all your partitions on that disk and make the HDD look unformatted, you could run:
```
sudo dd if=/dev/zero of=/dev/<your HDD> count=1
```
That zeros out the entire MBR, which contains the HDD partition table, so your drive will look unformatted. Is that maybe what you are looking for? Or you could just use the Ubuntu partition editor "gparted" to delete any existing partitions:
```
gksudo gparted
```
Let me know how it goes. :)

---

### Post by fatesjoke03 on 2008-10-30
Gparted did not show any other partitions on the drive that I could delete.

I am doing the install right now and chose the Guided install so hopefully the whole drive gets used. We'll see.

If it does not work I will try the codes you supplied.

---

### Post by fatesjoke03 on 2008-10-30
Okay, not sure if it's related but my install errored out at 56% 2 times.

So, I tried the codes offered and checked that the partitions are gone. Still not showing the full volume but when I went to install AGAIN it did not offer the Partial Partition option this time and gave me only the Full and Manual. 

Instaling now, we'll see what happens.

---

### Post by KhanTG on 2008-10-30
this may or may not be related... If I read you correctly, you need to sanitize your HDD (meaning ERASE it)?  There are plenty third party applications that can do this (google: disk eraser or look at download.com). if you can find it as a stand alone, WebRoot has a good one but that is a disk that is created by their Disk cleanUp Utility (I'm not necessarily advocating the use of Windows based software... but it IS good). Also, you might give the manufacturer of your HDD a visit at their home page... they might have some disk utilities for that HDD that will do a Low Level format available for free and OS independent.

---

### Post by fatesjoke03 on 2008-10-30
Okay, I went and removed all partitions using the hardy LiveCD then downloaded an Intrepid LiveCD and using a different desktop at work I hooked the hdd up and installed.

Work perfectly. I have no idea why the hardy LiveCD would not install since I had originally used it but I am up and running now with the Intrepid installation.

---

### Post by caljohnsmith on 2008-10-31
That's great news you finally got it to work. Cheers and have fun with Intrepid. :)

---

