---
title: "so close to victory w/ triple boot (Vista, XP, linux)"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by ericnord on 2007-09-11
I've spent three days trying to get Vista, XP and Suse all running. I can get each to run individually and now have Vista and Suse running via GRUB, but I lost XP. Sorry for the long message, but I've read everything I could first and still no luck. It is just some small item I'm sure. Using Suse becaue my abit ip35 pro has the jmicron issue that Ubuntu has issues w/.

Setup:
sda
hd0,0 - Vista primary partition NTFS
hd0,1 - XP primary partition NTFS
hd0,2 - Suse primary partition EXT2
hd0,3 - NTFS space for data

sdb
hd1,0 - primary partition Suse swap
hd1,1 - primary partition XP swap
hd1,2 - primary partition Vista swap
hd1,3 - NTFS for data

sdc
hd2,0 - NTFS primary for data

Steps I followed:
1. Start w/ three fresh drives and empty MBR, GRUB, etc.
2. Install XP to second partition on first HD (hd0,1). I did this because I read that Suse cannot move a Vista partition so it would be best to leave Vista on 1st partition. I also heard that XP should be installed first so Vista bootloader auto dual boots XP. All of this = me installin XP first, but on second partition
3. remove all media and boot to XP and do this a couple times to make sure MBR is good and XP loads as it should
4. Boot to Vista CD and install it to first partition of first HD (hd0,0). Remove all media and make sure it boots fine on its own
5. Here I noticed that I was not getting the dual boot from Vista boot loader. Vista would boot straight off w/ out recognizing any other OS.
6. Install Suse to first HD third partition hd0,2. Also install Grub to this partition and add XP as hd0,1 w/ rootnoverify and chainloader +1. Same w/ Vista except hd0,0
7. Reboot Suse and except Suse at Grub loader....Suse works fine.
8. Vista loads fine from Grub loader, but once I select it I get a bunch of text for a second that I don't have time to read, but I can catch GDLR outputted to the screen.
9. Select XP from Grub loader and it stops on screen w/ only text saying, rootnoverify (hd0,1) chainloader +1

So, I can boot into Suse and Vista just fine. I've gone into my menu.lst file and it is all correct, identical to Vista except w/ the proper partition. I've tried using Super Grub boot CD to boot the hd0,1 partition, but it just sits there w/ the boot command. I've verified everything w/ fdisk -l, I've tried to make the XP partition active first in both menu.lst and Super Grub, etc. XP will no longer boot...

One weird behavior that might offer some clue is when I now (system in state described above) insert the XP boot CD it says it cannot continue because no HD are connected. This is weird because if I take the CD out and boot to grub Vista and Suse boot fine.

The only thing I can think is that XP wrote the MBR to the second partition hd0,1. When I installed Vista it wrote MBR to first partition so that could explain the reason Vista didn't know XP was there. But I thought Grub on the booting partition hd0,2 could be told to boot any partition regardless of what the partitions MBR says.

Any ideas?

---

### Post by Steve1961 on 2007-09-11
Might be worth exploring EasyBCD:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I'm quad booting Vista, XP, Debian and Ubuntu with this, and I have to say it works really well.

---

### Post by _samba_ on 2007-09-11
Also you can try this: XOSL - Boot Manager

[http://www.ranish.com/part/xosl.htm](http://www.ranish.com/part/xosl.htm) 
and you can use also Ranish Partition Manager (great tool)

---

### Post by kenji-san on 2007-09-11
[GAG]("http://gag.sourceforge.net/") is also a great boot manager.  I can't confirm 100% that it works with vista but it should.  Have a look.

---

### Post by dabl on 2007-09-11
> **ericnord said:**
> 

The only thing I can think is that XP wrote the MBR to the second partition hd0,1. 

Any ideas?

Or, maybe XP wrote to the MBR for that hard drive, and then Vista just clean overwrote it, essentially nuking the XP boot info.  I don't think it is supposed to do that, but ....  that would be consistent with your Item 5, in which Vista doesn't see XP or anything else but itself.  :)

---

