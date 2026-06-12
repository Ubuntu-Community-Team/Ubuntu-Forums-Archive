---
title: "About to dual boot Ubuntu on 2nd hdd"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by lazulilasher on 2010-01-15
Hello all,

I'd like to install Ubuntu on a second internal hard disk which I'm going to pop in today. 

I've installed Ubuntu on other computers, but it has always been a clean install (I've overwritten Windows).

I've never had a problem before.

I was wondering if there are any specific problems to look out for while installing onto a second hard drive? I've searched the forum, and it seems that some have problems with Grub. Are there any ways to avoid that?

Oh, I should add that I have Windows 7 64 bit on my main hard drive, and would like to install Ubuntu on the second, blank drive.

Thanks in advance!

---

### Post by darkod on 2010-01-15
There are no problems with grub2, except sometimes but any tech equipment can have problems right? Most problems with multiple drives come by not being careful where the bootloader will go.

I guess you would like to leave your win7 disk with win7 bootloader on it and have grub2 on the ubuntu dusk. In this case, do not forget to go into BIOS and set the ubuntu drive as first in boot order BEFORE beginning to install ubuntu on it.
Then start the install process and in step 4 make a note what is your ubuntu drive named. Most probably it will be /dev/sdb and the win7 drive /dev/sda. In the last screen of the install, before clicking the Install button, click on Advanced and make sure grub2 goes to /dev/sdb (or what ever it was called in step 4), and not on partition like /dev/sdb1! Just /dev/sdb, the MBR of the disk.

If you do all this and it doesn't work, then you can curse grub2 and ubuntu. And me probably. :)
Let us know how it went so others can know too what to do.

---

### Post by audiomick on 2010-01-15
Occasionally the installer has problems with machines with 2 HDs in them, like in mine... For some reason, it doesn't always see both HDs.
If that should be the case, try using the alternate CD.

---

### Post by rahulkumarc on 2010-01-15
In my opinion its usually the hardware at fault most of the time not GRUB, also sometimes its been observed that over-enthustatic users like me who like to tweak the system, sometimes mess it up. Make sure read a lot before you go ahead with it.


Also make sure to install GRUB on the MBR on the first disk ;)

All-in-all I'd say goahead and install ubuntu, with out a second thought about problems. And if you do run into problems, we are all here to help you with.

---

### Post by darkod on 2010-01-15
> **audiomick said:**
> Occasionally the installer has problems with machines with 2 HDs in them, like in mine... For some reason, it doesn't always see both HDs.
If that should be the case, try using the alternate CD.

Out of curiosity, did you figure out the reason for that?

Don't say it like that, you will spook new users. :) It sounds like there is a bug, but usually that problem would be from something else, either the dmraid issue, etc.

---

### Post by lazulilasher on 2010-01-15
> **rahulkumarc said:**
> 

Also make sure to install GRUB on the MBR on the first disk ;)



Just to verify...DarkOD suggests installing GRUB on the Ubuntu disk; I'm not sure, but it would seem you suggest installing Grub on the first (Win7) disk.

Anyone have any clarification?

Thanks for the help, I would not have thought to instruct the BIOS to point to the correct disk.

I'm looking forward to doing this this evening, pending your replies.

Thanks again.

---

### Post by Leppie on 2010-01-15
> **lazulilasher said:**
> Just to verify...DarkOD suggests installing GRUB on the Ubuntu disk; I'm not sure, but it would seem you suggest installing Grub on the first (Win7) disk.

Anyone have any clarification?

Thanks for the help, I would not have thought to instruct the BIOS to point to the correct disk.

I'm looking forward to doing this this evening, pending your replies.

Thanks again.
since you have to open your machine, i would suggest to install the blank drive as the first master and the windows drive as the 2nd master. 
like this you can install ubuntu onto the blank drive, install grub2 to the mbr of the ubuntu drive and leave the windows drive as is (you will find this can be useful when you need to take the first drive out of your system as you do not have to go and restore the mbr to factory defaults).
another advantage of installing like this is you don't have to setup the boot order in the bios.

---

### Post by darkod on 2010-01-15
> **lazulilasher said:**
> Just to verify...DarkOD suggests installing GRUB on the Ubuntu disk; I'm not sure, but it would seem you suggest installing Grub on the first (Win7) disk.

Anyone have any clarification?

Thanks for the help, I would not have thought to instruct the BIOS to point to the correct disk.

I'm looking forward to doing this this evening, pending your replies.

Thanks again.

It's not polite to speak for myself, but go ahead with my suggestion. It's much better option to leave the win7 bootloader alone on disk1 since you have disk2 for ubuntu and grub2. No sense putting grub2 on disk1 and have disk2 MBR empty right?

Not that it wouldn't work if you put it on disk1 too. It will work either way.

As I said, the boot order in BIOS is the most common mistake with multiple drives (and the grub2 location that you have to look out for). I've seen cases where ubuntu was installed and windows kept booting directly as if ubuntu doesn't even exist, because the windows disk is still first in boot order.

---

### Post by oldfred on 2010-01-15
There is also a minor bug in grub2 where if it is on one drive and Ubuntu on another it takes 20 seconds or so extra to search drives. I concur with the recommendations to make each drive have the boot loader for the operating system on that drive. That way each drive does not depend on the other to be functional.

If you are familiar with partitions I like to set those up in advance and use the manual install. But I ran with the standard install with only a separate partition for files to share with windows for over 3 years now.

---

### Post by Leppie on 2010-01-15
> **darkod said:**
> It's much better option to leave the win7 bootloader alone on disk1 since you have disk2 for ubuntu and grub2. No sense putting grub2 on disk1 and have disk2 MBR empty right?
+1, leave the mbr of the windows disk alone
however, change the disk to be the 2nd and not the 1st (sata port) so you don't have to go into the bios either.

---

### Post by darkod on 2010-01-15
> **Leppie said:**
> +1, leave the mbr of the windows disk alone
however, change the disk to be the 2nd and not the 1st (sata port) so you don't have to go into the bios either.

I'm not 100% sure and it depends from BIOS to BIOS, but whether it's slave or master on a certain channel doesn't always dictate the boot order. The times of IDE drives and strict master/slave settings are long gone.
It is always wise to check the hdd boot order in BIOS because slave CAN BOOT before master if that's their order in the hdd boot list. Why assume when you can check in BIOS and set it the way you want.

---

### Post by lazulilasher on 2010-01-15
Sounds great. Thanks for the input. 

That's exactly what I will do: leave Windows disk alone, throw Grub and Ubuntu onto second hdd (the faster one which I am buying this afternoon, lol).

This will be my first time using Linux on a "newer" machine (I've always installed on my older laptops). So, I am greatly looking forward to trying things out.

Thanks again, and I will post after everything is running (hopefully running, that is....).

---

### Post by Leppie on 2010-01-15
> **darkod said:**
> It is always wise to check the hdd boot order in BIOS because slave CAN BOOT before master if that's their order in the hdd boot list. Why assume when you can check in BIOS and set it the way you want.
because if you do not change the boot order in bios, it's unlikely to change on its own...
furthermore, AFAIK changing the bios settings also involves modifying device.map as drive mappings will not be correct anymore.

---

### Post by darkod on 2010-01-15
> **Leppie said:**
> because if you do not change the boot order in bios, it's unlikely to change on its own...
furthermore, AFAIK changing the bios settings also involves modifying device.map as drive mappings will not be correct anymore.

You're making valid points and correct me if I'm wrong, but:

1. The OP doesn't have ubuntu right now, and the device.map issue is exactly why I recommended to put ubuntu disk first in boot order before installing it. That way a correct device.map is generated from start. And this change in BIOS will not create any issues with device.map because of the simple reason that it doesn't even exist right now.

If by any chance grub2 is messed up and you need win7 urgently, you can change win7 disk to be first in boot order and win7 bootloader couldn't care less about the device.map file. In order to boot grub2 later you still need to put ubuntu disk first again, hence device.map will be correct.

2. It's true that boot order will not change by itself, but I have no idea how it looks right now and how it will look after installing the second disk. So, to say "keep the setting same" I would have to assume or depend how the board lists the disks. Maybe it goes by channel and then master/slave order, maybe not. I'm not sure and I don't even need to go that far because I can simply see and set the boot order.

---

### Post by Leppie on 2010-01-15
> **darkod said:**
> 1. The OP doesn't have ubuntu right now, and the device.map issue is exactly why I recommended to put ubuntu disk first in boot order before installing it. That way a correct device.map is generated from start. And this change in BIOS will not create any issues with device.map because of the simple reason that it doesn't even exist right now.
from what i've understood from other posts (i don't have a 2nd drive to put in my laptop, so i cannot test this personally ;() is that even after re-installing grub2 to the mbr (AFAIK this should also recreate device.map) the mappings remain the same even after changing the boot order in the bios.

> **darkod said:**
> If by any chance grub2 is messed up and you need win7 urgently, you can change win7 disk to be first in boot order and win7 bootloader couldn't care less about the device.map file. In order to boot grub2 later you still need to put ubuntu disk first again, hence device.map will be correct.
this would still be valid if the windows drive is on the 2nd channel...

> **darkod said:**
> 2. It's true that boot order will not change by itself, but I have no idea how it looks right now and how it will look after installing the second disk. So, to say "keep the setting same" I would have to assume or depend how the board lists the disks. Maybe it goes by channel and then master/slave order, maybe not. I'm not sure and I don't even need to go that far because I can simply see and set the boot order.
normally the first channel is listed first (and the default boot selection), if there's only master devices then there's no reason to think about slave devices ;)

---

### Post by darkod on 2010-01-15
> **Leppie said:**
> from what i've understood from other posts (i don't have a 2nd drive to put in my laptop, so i cannot test this personally ;() is that even after re-installing grub2 to the mbr (AFAIK this should also recreate device.map) the mappings remain the same even after changing the boot order in the bios.


From my limited experience with ubuntu, the device.map stays the same during grub2 reinstall unless the argument --recheck is used. That argument creates new device.map.

For example if you use:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

you don't care about any BIOS changes you made. Grub2 will get it right with new device.map.

If we continue this discussion we'll just confuse the OP even more. :)

He doesn't have any ubuntu and device.map right now, so as long as he decides on the hdd boot order BEFORE installing ubuntu, correct device.map will be created from the start and no need to worry about it.

---

### Post by lazulilasher on 2010-01-15
Ok, here's the update....

Everything works flawlessly.

Here are the steps I took:

1. Purchased new Hard Drive from Best Buy.
2. Installed new hard drive.
3. Booted into Windows to make sure new hard drive was there (it was).
4. Rebooted computer and entered the BIOS. Set my new harddrive as first in boot list.
5. Rebooted computer to make sure Windows would boot if it were second in boot list (it booted fine.)
6. Downloaded iso via Bit-Torrent. Since I had my machine open, I took the opportunity to blow all of the dust off the interior. This took about 10 minutes to download.
7. Burnt an image to a CD.
8. Boot up the computer with the Live CD in the drive.
9. Tried out Ubuntu Live CD. It worked, but the Wireless did not work *at all*, so I spent about 40 minutes trying to get it to work. I was not successful. Decided to install Ubuntu anyway (why not?).
10. Installed Ubuntu which was *amazingly* quick (10-15 minutes).
11. Held Breath.
12. Rebooted Computer.
13. Grub loaded fine. Chose "Windows" to make sure I hadn't lost anything.
14. Booted into Windows. No problems.
15. Rebooted computer and chose Ubuntu.
16. Ubuntu loaded fine. The wireless worked fine. No tinkering required.

Total time: about 2 hours (includes time spent installing HD and time spent trying to get wireless to work on LiveCD).

Note: I didn't swap the SATA cables because they are inconveniently placed on my motherboard (right next to my graphics card.)

Anyway, I'm on to installing packages, now ;)

---

### Post by Leppie on 2010-01-15
glad that everything went well apart from the wireless issue on the livecd. enjoy ubuntu ;)

---

### Post by Honayo on 2010-01-15
Can the same result be found if Ubuntu is already installed on the second drive?
I've been switching the SATA power cable from my Ubuntu disc when I wanted to boot into Windows but a new power supply today gave me the additional SATA connectors I needed.
Please forgive me if this is the wrong place to post this.

---

### Post by oldfred on 2010-01-16
A new thread might be better.

With SATA drives they are controlled by the BIOS. You should be able to go into BIOS and see two different settings one is to choose boot order - HD, floppy , cd etc. And another to choose which hard drive will be the first when hard drive is the choice. It is like the old master/slave setting on the hard drive with IDE but all with software in the BIOS. Some early BIOS with SATA may not have that feature. Latest BIOS also have a key while BIOS is loading to choose boot drive often f12.

But grub is very good at letting you choose what to boot. If you have both drives installed grub should let you choose from a menu which system to boot. IF you have a new install of Karmic with grub2 all you have to do is:
sudo update-grub

---

### Post by Leppie on 2010-01-16
> **darkod said:**
> For example if you use:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
i hardly ever suggest people to use grub-install without the --recheck option.

---

