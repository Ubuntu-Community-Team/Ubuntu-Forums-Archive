---
title: "MBR questions (and: Windows 7 not booting with Grub2)"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by Sylchat on 2010-06-15
Hi All,

I have some issues/questions with dual booting Ubuntu 10.04 and Windows 7.

I have 2 500GB disk, sda has windows 7, sdb has Ubuntu. Both disk are seperate physical disks (Grub 2 had issues with RAID at the time of installation, so no RAID).

Actually after selecting Windows 7 from Grub 2 (v. 1.98.), I got a black screen with a blinking underscore on top left corner. Ubuntu boots fines.

I gathered some information, and realized grub 2 was detecting only the first partition for SDA, i.e. sda1, containing the windows restore partition (labelled 'system reserved'). So I added Windows 7 from sda2 in grub, using the following entry in /etc/grub.d/40_custom (got UUID with blkid):
```
menuentry "Windows 7 (on /dev/sda2)" {
        insmod ntfs
        set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fa384d36384cf2e5
    drivemap -s (hd0) ${root}
        chainloader +1
}
```

But even after booting on the correct partition, it would stay on the blinking underscore screen forever...

I used the boot_info_script ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) to get more info, here is a summarized output:

```

sda1
    File system:       ntfs
    Boot sector type:  Grub 2
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2
    File system:       ntfs
    Boot sector type:  Grub 2
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1
    File system:       swap

sdb2
    File system:       Extended Partition

sdb5
    File system:       ext4
    Boot sector type:  -
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


=========================== Drive/Partition Info: =============================

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS
(...)
/dev/sdb1                  63       996,029       995,967  82 Linux swap / Solaris
/dev/sdb2             996,030   976,768,064   975,772,035   5 Extended
/dev/sdb5             996,093   196,314,299   195,318,207  83 Linux
/dev/sdb6         196,314,363   976,768,064   780,453,702  83 Linux

```


Looking at the MBR on sda1 and sda2, they both start with '.c.NTFS' and end with 55aa (MBR Magic Number - see [http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)), using 'sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C'

On the Linux disk, only /dev/sdb2 has the magic number (sdb2 is the start for the extended partition). BTW, sdb5 is /, and sdb6 is /home.


There are a few things that are unclear to me:

[LIST]
So having 2 disks, I have 1 MBR per disk, whose MBR is the main one?
[/LIST]

[LIST]
[*]Does the BIOS choose the first one (on SDA), as explained by the * sign on /dev/sda1? (from the hex number 80 in the MBR at address 1be (byte 446))
[/LIST]

[LIST]
[*]Is grub installed in the MBR of both disks? (I see the 'GRUB' string in the MBR hexdump from both sda and sdb) and do both copies are similar?
[/LIST]

[LIST]
[*]AFAIK, the MBR is at start of the disk, not the partition, right? (it seems the MBR/EBR would look after VBR - see [http://en.wikipedia.org/wiki/Volume_Boot_Record](http://en.wikipedia.org/wiki/Volume_Boot_Record)).
[/LIST]

[LIST]
[*]Should I backup both MBRs? (using sudo dd if=/dev/sda of=~/mbr512sda.img bs=512 count=1) and EBR+VBR as well?
[/LIST]

Finally, I will try fixing the problem using testdisk ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)) as explained in this thread: [http://ubuntuforums.org/showthread.php?p=9356346](http://ubuntuforums.org/showthread.php?p=9356346)


cheers!
Sylchat

---

### Post by darkod on 2010-06-15
sda1
    File system:       ntfs
    Boot sector type:  [COLOR=Red]Grub 2[/COLOR]
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

The testdisk procedure should be the first thing you try, not the last. You have grub2 installed on your win7 boot files partition.

And grub2 was correct at detecting the win7 loader on sda1 because that's where the boot files are. From win7 MS started creating small 100MB partition to hold just the loader boot files. In most cases it does exist, not always.
But if it does exist, that's where the loader is and hence the entry in grub2 would say (on /dev/sda1).

The grub2 on /dev/sda1 is the problem, remove it from there with the procedure:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by oldfred on 2010-06-15
You choose the boot disk in BIOS. Windows only uses the boot flag or active partition in windows to know where to jump to continue booting.

With 2 drives you should keep the windows boot loader on the windows drive. Install grub just to the Ubuntu drive and in BIOS make the Ubuntu drive the boot drive.

MBR is the very beginning of the drive and is not part of a partition. Their is space at the beginning of every partition referred to by several names, boot sector, PBR partition boot record, boot slice, but it is space also used by windows and grub can be installed into the PBR but has to be chainloaded from another boot loader in the MBR. If grub overwrites the windows code windows will not boot. Follow Darko's link on test disk to fix it.

---

### Post by Sylchat on 2010-06-18
Thanks for your replies, Darkod and Oldfred... I have not launched the testdisk tool yet.

But if I fix the faulty boot sector from the windows disk where Windows and Grub are installed, then I will have to reinstall the GRUB in the second (Linux) disk? (and tell the BIOS to boot from the linux disk)

Anyway, I will try that, I can still access the internet from another PC if something goes wrong... :P

---

### Post by wilee-nilee on 2010-06-18
> **Sylchat said:**
> Thanks for your replies, Darkod and Oldfred... I have not launched the testdisk tool yet.

But if I fix the faulty boot sector from the windows disk where Windows and Grub are installed, then I will have to reinstall the GRUB in the second (Linux) disk? (and tell the BIOS to boot from the linux disk)

Anyway, I will try that, I can still access the internet from another PC if something goes wrong... :P

Test disk if run as the link describes should leave you with grub installed and set. If darkod or oldfred had thought you needed any more then that they would have posted it. They know their stuff and are very thorough with instructions.

But just in case you do need grub reinstalled here is a link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Just remember grub goes to the mbr no partitions.

---

### Post by Sylchat on 2010-06-18
First, I must say, IT WORKED!!

I was almost happy to see Windows booting, but even happier to see my Ubuntu install still booting :)

So thanks all for the help (and the motivation I needed)...

Still there are still some things that are unclear to me, like:
Where is actually installed GRUB? Is it in the MBR or, the MBR will just indicate the start of a booting disk/partition where a bootloader (grub or ntldr/bootmgr) is?

cheers
Sylchat

---

### Post by wilee-nilee on 2010-06-18
> **Sylchat said:**
> First, I must say, IT WORKED!!

I was almost happy to see Windows booting, but even happier to see my Ubuntu install still booting :)

So thanks all for the help (and the motivation I needed)...

Still there are still some things that are unclear to me, like:
Where is actually installed GRUB? Is it in the MBR or, the MBR will just indicate the start of a booting disk/partition where a bootloader (grub or ntldr/bootmgr) is?

cheers
Sylchat

In Ubuntu like windows there are files that are associated with booting the computer. The mbr is where the booloader that reads these files are. So grub on a install loads the relevant scripts to Ubuntu and the grub bootloader to the mbr if the grub bootloader is pointed at the mbr. Actually darkod or oldfred can give a much better description of this, and many others on the forum as well.

The main thing to remember and doesn't even include understanding how grub works is that when you install there is a advanced button on the last install screen that will show where grub is pointed, it defaults to the main HD mbr.

So for example lets say you wanted to install Ubuntu to a thumb, a full install. You would boot the live cd run the install and at the partitioning screens make sure it was loaded to the thumb, lets say the thumb is sdb. The numbers after sdb like sdb1..etc would be the partitions. But on the screen with the advanced button you would want grub installed to the disc=mbr=sdb.

I have a 16 gig thumb that I have maverick on originally I had Lucid as well, both full installs 8 gigs each. Now I have just Maverick but with XP in a virtual running inside of Maverick. I can run this thumb on all my computers, although it is generally thought that a full install on a external may not always boot from every computer like one loaded with say unetbootin or the Ubuntu startup disc creator. These last two thumb loaders load the ISO not the whole OS, and boot with other then grub.

---

### Post by darkod on 2010-06-18
> **Sylchat said:**
> 

Still there are still some things that are unclear to me, like:
Where is actually installed GRUB? Is it in the MBR or, the MBR will just indicate the start of a booting disk/partition where a bootloader (grub or ntldr/bootmgr) is?

cheers
Sylchat

It is and it isn't. Grub/Grub2 has only part on the MBR, because it doesn't fit all. That first part tells it where to continue loading grub from.
For windows the boot process is little simpler. Windows MBR just continues the boot from the partition with the boot flag set on it.

You can force grub2 to install on the first sector of a partition, so called partition boot sector, but you really need it only for special setups. For ordinary setup, having it on the MBR is enough and most simple.

At this moment I wouldn't bother with installing windows MBR on the windows disk, no need. You can do it anytime you want anyway.

---

### Post by Sylchat on 2010-06-19
So just for information, here are the changes before and after running the testdisk on /dev/sda, using the boot_info_script:

BEFORE:
```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1283069 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

```

AFTER:
```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

```

@wilee-nilee: I will check the advanced button on a virtual machine.

So the boot process is 
1. BIOS loading and booting on the configured hard disk 
2. Going to the first sector (MBR) to find bootable code
3. If no bootable record, going on the next item in the booting device list from the BIOS

Problem is, I have 2 identical hard disks, so I can't know which one is the linux one or the windows one :P

Anyway, I didn't have to change the BIOS boot list, and just removed the useless /dev/sda2 entry from /etc/grub.d/40_custom.

---

### Post by wilee-nilee on 2010-06-19
In a virtual you don't have to worry about the grub placement it is its own partition.

---

