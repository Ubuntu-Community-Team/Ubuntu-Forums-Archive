---
title: "Stumped by Partitions"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by GregF on 2006-04-19
I am trying to install 5.10 as a dual boot with WinXP on a 200gb hard disk. When I originally installed XP, I was only given the option of creating a 137gb partition. I figured that this was a BIOS limitation (Asus A7S-VM motherboard). Windows installed fine and I thought I would have ~60gb left over to install Ubuntu. After 1st installation stage, I got a Grub error 17. Spent a lot of time working with Grub and I think it was installed correctly. I think the problem is that the original Windows partition was corrupted, possibly by trying to address more hard disk space than the BIOS could cope with. Couldn't fix it with FIXMBR.

So, I deleted all the partitions and started over, this time not going over 135gb of total disk space. Installed WinXP normally and upgraded it to SP2. Partitioning in Ubuntu looks like this:

NTFS - 80gb
Ext3 (bootable) - 40gb
FAT32 - 10gb
Swap - 1gb

...and *exactly* the same thing happened. I'm now stumped and I can't seem to find any postings of a similar experience. Any thoughts? Anyone?

Thanks.

-Greg

---

### Post by Sef on 2006-04-19
> NTFS - 80gb
Ext3 (bootable) - 40gb
FAT32 - 10gb
Swap - 1gb

Switch your boot to NTFS.  When I was dual booting, I always had the boot in the Windows partition.

---

### Post by GregF on 2006-04-19
Well, thats an improvement. I changed the active partition to NTFS and now XP boots, but only XP. I tried putting Grub back on using the "rescue" method but no luck. Ill try it using the live CD method next.

Update: reinstalled Grub and back to error 17. Pretty close to saying this just is not going to work.

---

### Post by twodogs on 2006-04-20
hi,

install xp first, then resize disc setting it up for the linux partition.
install linux and dont install bootloader in mbr, install on linux partion.
then download a small program called bootpart. i think i got it at
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

directions follow below the actuall download.
hope this helps.  i like it.

UPDATE:
after I install bootpart as per above instructions, this
is what I do...

1. open command console while in Windows
2. cd\bootpart
3. bootpart (notice number for the 83 linux location, should be 2, or maybe 3)
4. bootpart 1 bootsect.lnx Ubuntu
    -replace the 1 with the number from #3
    -replace the Ubuntu with whatever you want...Linux, Ubuntu Linux etc.
5. bootpart list
    -visually verify the boot.ini file is good with your new linux boot option
6. reboot your pc. you will be given a choice to boot into Windows or Ubuntu

ps: dont delete the bootpart folder on c:
if you do, this mod will NOT work.

enjoy!

---

### Post by Greg2 on 2006-04-20
[QUOTE=GregF]I am trying to install 5.10 as a dual boot with WinXP on a 200gb hard disk.
-snip-
[/QUOTE]
Here’s some links to info that should be of help to you:
[http://www.seagate.com/support/kb/disc/faq/137_winxp.html](http://www.seagate.com/support/kb/disc/faq/137_winxp.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by GregF on 2006-04-20
I think the problem has been identified and resolved. Using the SuperGrub disk ([http://adrian15.raulete.net/grub/tiki-index.php]("http://adrian15.raulete.net/grub/tiki-index.php")), I finally got a meaningful error message, stating (I'm paraphrasing here) that Linux was installed in an area of the hard disk that was not recognized by the BIOS. This was the 2nd partition, following a NTFS partition of 80gb. 

However, by adding a 2nd, smaller hard drive that I had lying around, I was able to install Ubuntu as a dual-boot system, with no special procedures required. I think that trying to install Ubuntu on a partition outside of the memory range reported by the BIOS (which in my case was just a little over 8gb, even when entering the HDD parameters manually) is not practical and in some cases may be impossible.

---

