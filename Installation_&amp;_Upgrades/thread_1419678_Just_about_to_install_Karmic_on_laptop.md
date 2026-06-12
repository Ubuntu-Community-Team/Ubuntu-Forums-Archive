---
title: "Just about to install Karmic on laptop"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by sqrooup on 2010-03-02
As it says above I am about to install Karmic on to my laptop, wish me luck!
I intend to have dual boot; my laptop has a 500GB hard drive, I intend to use 200GB for the Karmic, leaving 300GB for the original Windows 7.
When I first got the laptop Windows insisted I make a recovery disc or USB stick; this is available!

I am going to hold off for about an hour, so that any comments can be posted: some questions are; 

If it's a total failure, how to run recovery mode in windows 7?
If GRUB does not recognise windows , how to set it up?
What else can go wrong?

This is not the first time I have tried to partition an existing drive, my main PC was partitioned with Hardy / Karmic, but GRUB only recognises Hardy; hence my reluctance! So any help / comments would be useful.

---

### Post by khelben1979 on 2010-03-02
I would recommend that you take backups of your Windows system before you proceed. Other than this, booting Windows 7 and Linux from two different harddrives would be the most pain free solution, in my opinion.

From what I've read from [this thread]("http://ubuntuforums.org/showthread.php?t=1312894"), you can expect problems.

---

### Post by sqrooup on 2010-03-02
OK have followed the threads, have been to [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/"), and got the following;
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfa505bf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,458,047    19,456,000   7 HPFS/NTFS
/dev/sda2          19,458,048   976,771,119   957,313,072   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3CC49F13C49ECF10                       ntfs       System                        
/dev/sda2        982EA0A02EA07940                       ntfs       Windows                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

```

Any advice from this point?

For the record the laptop is an Advent Roma 3000, with an Intel Pentium T4300.

I will hold off for a bit longer.

---

### Post by darkod on 2010-03-02
Boot win7 and use Disk Management to shrink the system partition (/dev/sd2 in linux terms) for as much as you want. Leave the space as unallocated, don't create any parttion for ubuntu from windows. Boot win7 few times after that.

Then when you are sure win7 is fine after the shrink, boot with the ubuntu cd, select Install Ubuntu and in step 4 tell it to Use Largest Available Free space which will install it into the unallocated space you left for it.

That's it.

Did you run ubuntu in Try Ubuntu mode first to see if the hardware on the laptop will work as expected?

---

### Post by 2hot6ft2 on 2010-03-02
Well I'll add this. A lot of the problems people are having with win7 rebooting is that they are using bootleg copies of it, and there are problems with the bootlaoder hacks as shown in these threads.

[Program based Windows 7 loader]("http://forums.mydigitallife.info/threads/8632-Program-based-Windows-7-loader")
[RemoveWAT - A safer activation solution.]("http://forums.mydigitallife.info/threads/10895-RemoveWAT-A-safer-activation-solution.")

And since no one is going to admit they have a bootleg copy that they are using it makes it hard to tell who has a genuine copy of win7 with issues.

---

### Post by sqrooup on 2010-03-02
> **darkod said:**
> 
Did you run ubuntu in Try Ubuntu mode first to see if the hardware on the laptop will work as expected?

I did indeed, and pleased to see it works.

Will start proceeding with operation. Will let you know how how I get on.

---

### Post by sqrooup on 2010-03-03
Update;
[QUOTE= Doctor Frankenstein]IT'S ALIVE!! [/QUOTE]
[QUOTE=Bubbles D'Beere of Little Britain]CHAMPAGNE FOR EVERYONE!!![/QUOTE]
I now have a dual booting laptop (win 7/karmic)!
Thanks to all who helped (especially Darkod, your idea helped)!

sqrooup

---

