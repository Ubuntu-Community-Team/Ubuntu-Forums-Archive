---
title: "XP doesn't exist after few days using ubuntu"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by ramahi on 2008-09-06
Hell all , 
I have created a partition to test ubuntu ( beside windows XP)
every thing was working fine with dual boot screen .
for unknown reason suddenly I couldn't login to windows anymore . like the windows partition disaapeared.
 
 I tried some partition recovery tools but things got worst , and lost the ubuntu partition  , but I got it back but not bootable.

also I was desperate to get my files from windows , I have  tried to rebuild the MBR . 

my question is there any chance to get my files , I have some family pictures and some important documents .

or accept my loss and move on !

I bought new hard drive so I can use my laptop , the hard drive with the problem setting in front of me now .

Thank you guys

---

### Post by coffeecat on 2008-09-06
Where is the hard drive with Windows? Still in the laptop or sitting in front of you? It's not quite clear.

What you need to do is have the hard drive fitted inside a machine, or inside a USB enclosure so that it can be connected to a machine. Boot up with the live Ubuntu Hardy CD. If the hard drive with Windows is in a USB enclosure, connect that (once you've booted up) so that Ubuntu can automount it. Now go to System > Administration > Partition Editor. Don't try to do anything with this - just look. What does that tell you about the partitions of the internal drive? Is the Windows NTFS partition still there? If the affected drive is in a USB enclosure, click on the drop down menu at top right to select the USB drive and view its partition structure.

Now go to Applications > Accessories > Terminal. Post the output of:

```
sudo fdisk -l
```That will tell us what the partition structure of the disk is like - whether there are still Ubuntu and Windows partitions on there. If you can see the Windows partition, you could plug in another USB drive, let Ubuntu live mount that and copy the files you need from the Windows partition to the second USB drive. If the Windows partition is on the internal drive, it won't be automounted, so post back to clarify where the Windows HD is (it's getting very difficult to advise without knowing) if you need help mounting it.

**Edit**: re-reading your post, I see that the affected drive is probably outside the laptop. **If** you can get hold of a suitable USB enclosure and if you have another Windows machine available, you could simply plug the affected drive into Windows and see if it automounts the NTFS Windows partition. Then you could copy off the files you want, after which you could concentrate on rescuing both Windows and Ubuntu on that drive. Depending on what we find from fdisk, they may or may not be repairable.

---

### Post by ramahi on 2008-09-06
Hi coffeecat , 

I had to replace the hard drive so I can be able to use my computer .
I'll connect the old hard drive and follow your instruction and I'll come back here with the results .

Thanks for your help

---

### Post by ramahi on 2008-09-06
OK , things doesn't look good .
I'm using Ubuntu live to write this message .
here is what I found after 
fdisk -l 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13750   110446843+   7  HPFS/NTFS
/dev/sda2           13751       14593     6771397+   7  HPFS/NTFS


the smaller partition is the built in " hp recovery partition " and can't see Ubuntu partition now.

the NTFS partition  can't be located on places from Ubuntu .

is there any hope ?

thanks

---

### Post by coffeecat on 2008-09-06
> **ramahi said:**
> the NTFS partition  can't be located on places from Ubuntu .

is there any hope ?

Yes, there's still a Windows C: partition at /dev/sda1 - that's what I assume because it has the boot flag set.

In my experience, sometimes the live CD sees partitions in Places, and sometimes not. I've never worked out the rhyme or reason for this. Anyway, try the following. Fit the affected drive back into the machine and have a USB drive of some sort handy. Boot up from the Hardy live CD again, open a terminal and:

```
sudo mkdir /media/win
sudo mount -t ntfs-3g /dev/sda1 /media/win
```Hopefully, all being well, an icon will appear on the desktop for your Windows C: partition which you can double-click on to browse the filesystem. Now plug in the USB drive, let it be automounted and copy all the files you need onto the USB drive. But if you get an error at any point, post that and we can go from there.

If this is successful, do:

```
sudo umount /dev/sda1
```... before you log off from the live CD. Shutting down should do a clean unmount anyway, but it doesn't hurt to be careful.

Here's another thing to try. Do you have (or can you get hold of) a Windows install CD? Not a laptop manufacturer's restore disc - it has to be a Microsoft disc. It looks as though the Ubuntu partition has gone and, with it, stage 2 of grub has also gone which is why you can't boot into Windows. To get a bootable Windows on that drive, all you have to do is to reinstall the Windows mbr. Fit the drive, boot up from the Windows CD, go to the recovery console and run FIXMBR. You may have to run FIXBOOT as well.

If you haven't got a Windows CD, I've heard it said that you can repair the Windows mbr with [Super Grub Disk]("http://www.supergrubdisk.org/"), although I have no experience of this. Even if you can't repair the bootloader with SGD, you should at least be able to boot into Windows with it, and then you could rescue your important files.

---

### Post by ramahi on 2008-09-07
Hi , 
I have tried what you told me and i got the following message:

$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


and I have tried to use the Windows CD  but FMBR didn't fix the problem also I have used the SGD. no luck also 

Any suggestions 

thanks

---

### Post by coffeecat on 2008-09-07
> **ramahi said:**
> NTFS is either inconsistent

That's what I feared, which is partly why I suggested trying to get it to boot into Windows again. If there's a corrupted journal on an NTFS partition, you really need Windows to repair it with chkdsk as the error message states. A few thoughts therefore.

You have some important files on there but they may still be recoverable even if the OSs are lost. I've come across threads on this forum where people have inadvertently reformatted partition(s) that contained valuable data. Other posters have suggested a particular piece of software which is designed to recover image files when the filesystem is lost but which can also recover some other file types. It seems that this has often been successful. Your situation is not as dire as a reformatted partition, but at the moment I cannot remember the name of the software. A forum search may come up with something  - I'll do that myself later - and, if I remember more, I'll post again.

If the worst comes to the worst you could go to a data recovery company, but that would be expensive. And finally, are you able to try my earlier suggestion of putting the HD in a USB enclosure and trying to mount it with a Windows machine? I imagine that it's a 2.5" drive, but you can get hold of USB enclosures for them, both ide and SATA. You might not want to buy one just for a job that might not work, but when you have eventually got the data copied, you'll have a spare drive that you might want to use anyway - just a thought.

---

### Post by coffeecat on 2008-09-07
The name of the software I was trying to remember is photorec. According to Synaptic it seems to come as part of the testdisk package. The description of it sounds hopeful as it can cope with more than just image files. Since it will only occupy just under 3MB once installed, you could install it in the live environment to see if you can recover your data. It will be lost once you power the live environment down, but that won't matter if you can get your data copied.

Be aware that I have never used this software. I'm just going on what I have read.

---

