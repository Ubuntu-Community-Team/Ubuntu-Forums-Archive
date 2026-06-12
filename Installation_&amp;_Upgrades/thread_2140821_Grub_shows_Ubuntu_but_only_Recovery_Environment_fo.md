---
title: "Grub shows Ubuntu but only Recovery Environment for XP"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by spacetimecowboy on 2013-04-30
Hi there,

I recently carried out a dual boot install (Ubuntu 11.10 on an Acer Aspire One ZG8 netbook with XP). Whilst manually adjusting partitions I made a stupid error and changed sda 2 ntfs (the main windows data drive) directly into a linux swap. After the damage was done (it was formatted as part of the process), I reassigned the partitions into what I hope is a more sensible shape...

[sda1 ntfs 6gb PQSERVICE (original and unchanged)] [sda4 primary ext4 /home 130gb] [sda3 & sda5 (extended) logic linux swap 2gb] [sda2 ext4 / 10gb (boot)]

After successful install followed by successful upgrade to 12.04 I have a grub with Ubuntu options but for Windows, only 'Recovery Environment (loader)', which, when used, says it says runs succesfully. (This involves "restoring PC to factory default status", and formating C: drive (does this partition even exist anymore?) and produces ErrorCode=0 then reboots)

I have run boot-repair-disk from boot usb and used the 'recomended repair' function, but the situation is unchanged.

If there is an identical or useful thread, please show me.

I really appreciate any help in fixing my little bit of chaos. If you need more info, please tell me and I will post do my best to post it.

Many Thanks

---

### Post by spacetimecowboy on 2013-04-30
Boot-Repair-Disk info @ [http://paste2.org/LGO1pF3g](http://paste2.org/LGO1pF3g)

(Some things confuse me, like the date 20 Nov 2012 and the fact that it says sda1 is Windows 7, everything else looks right though)

Thanks

---

### Post by oldfred on 2013-05-01
The date is the version of Bootinfoscript.

Some systems that were downgraded may have recovery partitions that boot with Windows 7. But I had my XP partition converted to Windows 7 in the boot scripts after I ran a Windows 7 chkdsk (which did work better). But then I had to run more repairs to convert PBR - partition boot sector back to Windows XP.

You are not showing any other NTFS partition so your Windows is gone.
If you changed swap back right away you may have recovered Windows. Swap is just unformatted space and used when you run out of RAM. If not used (yet) then it still would have all the old data.

---

### Post by spacetimecowboy on 2013-05-01
Ok, thanks.

It looks like I might need a clean reinstall if I want windows back then.

---

### Post by oldfred on 2013-05-01
Windows only installs to a primary NTFS partition with the boot flag. You should be able to create a new partition as long as it is primary then the Windows install will use it.
But if all you have is a recovery version then that usually overwrites the entire system and makes it just as purchased. You may have to remove Ubuntu first for it to see drive,  and restore a Windows boot loader as it often does not restore MBR.

---

### Post by spacetimecowboy on 2013-05-01
Ok, that's useful to learn. Thank you. I think I'm going to clean install Windows 7 from usb boot (wonder if it does it's own partitioning and formatting?), followed by a dual boot Ubuntu install. However, if I can't find a flash drive big enough lying around I may give that a go.

Thanks again.

:)


"wonder if it does it's own partitioning and formatting?" - you might have just answered that question I think. Does this mean I need to create a /boot ntfs partition? G Parted cannot do this can it?

Thanks for your time.

---

### Post by spacetimecowboy on 2013-05-01
So some research shows me that the W7 install has its own partition manager. I am going to mark this thread SOLVED as we are digressing now.

Thanks

---

### Post by oldfred on 2013-05-01
Gparted can create NTFS partitions and you can add boot flag. I think it may be the XP type, but Windows 7 can install and convert to Vista/7/8 type. 

You can use Windows partition tools, just do not create more than 3 partitions as it may want to convert to dynamic which does not work with Linux and may not work with all Windows repair tools. Anytime you want more than 3 partitions you want the 4th to be an extended partition so you can add many logical partitions.

Some suggest third party Windows tools for Windows use.
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

But use gparted or Parted Magic or liveCD's gparted for any Linux partitions.
      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

