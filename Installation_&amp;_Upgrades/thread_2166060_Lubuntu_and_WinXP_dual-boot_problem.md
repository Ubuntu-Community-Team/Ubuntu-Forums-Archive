---
title: "Lubuntu and WinXP dual-boot problem"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by matias2 on 2013-08-07
[COLOR=#707070]Hello,

I'm having trouble with a laptop that had Windows XP installed and then I asked a friend to make a dual-boot with Lubuntu, but now it's only booting with Lubuntu.

I don't know what he did with the partitions, because:

```
sudo fdisk -l
```

Throws:

```

/dev/sdb1   *        2048      391167      194560   83  Linux
/dev/sdb3          393214   488396799   244001793    f  W95 Ext'd (LBA)
/dev/sdb5        16591743   163185119    73296688+   7  HPFS/NTFS/exFAT
/dev/sdb6          393216     4390911     1998848   82  Linux swap / Solaris
/dev/sdb7       163186688   363184127    99998720    b  W95 FAT32
/dev/sdb8       363186176   403183615    19998720   83  Linux
/dev/sdb9       403185664   488396799    42605568   83  Linux
```

**sdb5 **was the working partition of WinXP from which I'd like to boot.

I tried to run the tool **Fix Boot of Windows** of the program **Super Grub Disk** but didn't work.

Thanks in advance.
[/COLOR]

---

### Post by carl4926 on 2013-08-07
But do you have an option in the Grub menu for booting XP? What is on or where is sda in all this?

---

### Post by matias2 on 2013-08-07
Thanks for your reply carl4926. 

GRUB menu doesn't appear, Lubuntu is directly booted. I checked its options with **GRUB Customizer** and there is no WinXP entry.

**sda **is a pendrive.

---

### Post by carl4926 on 2013-08-07
Have you checked out: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)Again, what about sda, did you just leave it out. Can you take a screen of sdb in Gparted and paste here?  Are you able to access the XP partition in the lubuntu file manager?

---

### Post by sudodus on 2013-08-07
I think Windows XP wants a boot flag on its partition (now there is none). Also, it wants a primary partition (now it is in a logical partition). But I don't know if that would exclude it from grub. Why is the first partition a linux partition? What was there before? What is there now? Is it a linux /boot partition?

Do you remember or do you have a copy of ***the partition table before Lubuntu was added***?

---

### Post by Jonathan Precise on 2013-08-07
In the General settings tab of Grub Customizer, make sure that the check boxes below are checked:

```
Show menu
Look for other operating systems
```

Also make sure the timeout is around 10 seconds.

Then check to see of your problem is fixed.

---

### Post by oldfred on 2013-08-07
As sudodus mentions, Windows only boots from primary partitions with the boot flag. If you had another install of Windows in a primary partition your XP install in the logical actually had its boot files in that partition which now looks like it is gone. Or did you have another Windows install on sda, with boot files?

Only with XP is it somewhat possible to make it boot from a logical, but it is not standard. Since it is the first logical partition you may be able to move it out of the extended and make it another primary with fixparts.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You still need to do Windows repairs to restore the boot files ntldr and boot.ini.
More Vista, but how all BIOS based Windows systems boot.
      
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by matias2 on 2013-08-07
**carl4926:**
I checked out Boot-Repair-Disk. It made GRUB menu appear with the entries **Ubuntu**, **Ubuntu advanced options** and **Windows (in /dev/sdb5)**. However, when I choose "Windows" it doesn't boot, a cursor keeps blinking. Lubuntu continues booting OK. 

GParted screenshot:
[IMG]http://i.imgur.com/Sz1FWUB.png?1[/IMG]


Yes, I can access the WinXP partition in the Lubuntu file manager.


**sudodus**:
I don't know exactly what my friend did. I guess that before the first partition was a Windows recovery partition. Now there is a linux /boot.

No, I don't have a copy of the partition table before Lubuntu was added.


**Jonathan Precise**:
GRUB Customizer configuration was already set as you mentioned.


**oldfred**:
I will take a look at FixParts and Multibooters.


Thanks for your time.

---

### Post by carl4926 on 2013-08-08
In gparted right click sdb5 > manage flags
You need to add the flag 'boot'

You then must right click sdb1 and remove the flag from there

I'm not 100% sure this boot flag thingy is the issue, it's so long since I worked with XP...

---

### Post by carl4926 on 2013-08-08
> **carl4926 said:**
> In gparted right click sdb5 > manage flags
You need to add the flag 'boot'

You then must right click sdb1 and remove the flag from there

I'm not 100% sure this boot flag thingy is the issue, it's so long since I worked with XP...

You might have to do this from a live session rather than the installed system.

---

### Post by matias2 on 2013-08-08
**carl4926**: 
I changed the flag you mentioned from a live session: 

[IMG]http://i.imgur.com/cZsMzBz.png[/IMG]

But keep having the same problem.


**oldfred**:
Running:
```
sudo sfdisk -d /dev/sdb > parts.txt
```

Throws:
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

Regards.

---

### Post by carl4926 on 2013-08-08
I think the problem is that if XP is in a logical it still needs a primary fat32 or ntfs for it's boot code
You would need to make sdb1 fat or ntfs and install XP again and put the boot flag on sdb1. XP will then install it's boot code in sdb1

---

### Post by oldfred on 2013-08-08
The message on cylinder boundary is not important. Drives have converted from cylinders to LBA or large block allocation since hard drives became larger than 8GB.

Either convert sda5 to primary or reinstall to a new sda1 that is primary, formatted NTFS with the boot flag.

---

### Post by matias2 on 2013-08-08
**carl4926**:
But changing **sdb1 **file system won't make Lubuntu unbootable? In case I change it (with GParted from a live session), then, in which partition do you suggest me install WinXP? May I recover the system in **sdb5 **this way?

**oldfred**:
I don't understand yet how to convert **sdb5** to primary. 
I'm trying to avoid reinstalling WinXP system since I have a huge amount of software installed and configured in that partition :/

Sorry but my knowledge in this subject is quite limited. Thanks again for your time.

---

### Post by carl4926 on 2013-08-08
> **matias2 said:**
> **carl4926**:
But changing **sdb1 **file system won't make Lubuntu unbootable?.

It may well. But I'd say it's going to be easier for you to re-install lubuntu - at least your /home is separate, so it should be a doddle to keep /home unformatted. Usually takes me an hour or so to get back with all the updates and apps I use.

Mind you, your partitioning is pretty messy IMO

Once you re-install XP you'll probably find it easier to re-install lubuntu than for us to tell you how to repair it. And FYI, you just don't need a /boot partition for lubuntu

Make sdb1 to ntfs and set it to have a boot flag
Install XP to sdb5 and remove the boot flag
Then re-install lubuntu

---

### Post by oldfred on 2013-08-08
Did you load fixparts. Not in every case can you change partitions around but it will show you the options.

From fixparts page:
```

                                                                                                      Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             62      1171799   primary              Y      0x07
   2               1171800      1562399   primary              Y      0x83
   3               1562462      3124799   primary     Y        Y      0x0C
   5               3124862      3980213   logical     Y        Y      0xAF

```

---

### Post by matias2 on 2013-08-08
**carl4926**:
OK, I'm starting to consider to erase all the partitions and start from zero. Before that, isn't there a way to clone **sdb5 **somewhere and then clone it back to a new **sdb1** primary partition?


**oldfred**:
Unfortunately I can't change **sdb5**:
```
                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                  2048       391167   primary     Y        Y      0x83
   5      *       16591743    163185119   logical     Y               0x07
   6                393216      4390911   logical     Y        Y      0x82
   7             163186688    363184127   logical     Y               0x0B
   8             363186176    403183615   logical     Y               0x83
   9             403185664    488396799   logical     Y        Y      0x83
```

---

### Post by oldfred on 2013-08-08
I have never used these but several have suggested them. But if you move to a different partition I am sure you will have to use an XP disk to run repairs as partition info and boot.ini will be different and need correction.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by carl4926 on 2013-08-08
> **matias2 said:**
> **carl4926**:
OK, I'm starting to consider to erase all the partitions and start from zero. Before that, isn't there a way to clone **sdb5 **somewhere and then clone it back to a new **sdb1** primary partition?




dd can do that assuming you have a place to store it?
And I understand clonezilla too.
In either case I have not used these for this purpose.

Given that XP is terminally on the decline, I'd probably be considering if I should make a more practical investment of my time and energy

---

### Post by matias2 on 2013-08-09
**oldfred**: 
OK, I will consider them.

**carl4926**:
I have good experience using Clonezilla. I will remove the HDD from the laptop, clone sdb5 to another HDD, and then try to boot WinXP from this one. 
Yes, I know that WinXP is on the decline, but the laptop has an Atom Z530 processor, Win Vista/7 aren't options.

I'd like to work only with Lubuntu, but I have custom Windows software that doesn't run OK with Wine.

---

### Post by matias2 on 2013-08-12
Finally I could clone **sdb5**. These are the partitions now:

[IMG]http://i.imgur.com/ShbQKuU.png[/IMG]

There aren't */boot* or */home* partitions because I let the Lubuntu installer configure the partitions automatically and it didn't create them.

Regards.

---

### Post by carl4926 on 2013-08-12
And is there a problem?

---

### Post by matias2 on 2013-08-12
No **carl4926**, it's working fine, thanks for your help.

If I come up against a new problem I'll create a new thread, this one can be closed :)

Regards.

---

### Post by carl4926 on 2013-08-12
> **matias2 said:**
> No **carl4926**, it's working fine, thanks for your help.If I come up against a new problem I'll create a new thread, this one can be closed :)Regards.Excellent

---

