---
title: "Totally Remove Ubuntu 8.04,Keep Win XP"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by jbocean on 2010-04-27
I have an old Compaq w/ 40g HD & 1g RAM.

**When I boot up I see on the Boot Screen**:

Ubuntu 8.04.3 LTS Kernel 2.6.24.25 rt
Ubuntu 8.04.3 LTS Kernel 2.6.24.25 recovery mode
Ubuntu 8.04.3 LTS Kernel 2.6.24.16 rt
Ubuntu 8.04.3 LTS Kernel 2.6.24.16 rt recovery mode
Ubuntu 8.04.3 LTS Kernel memtest86+
Windows XP Home

I believe I read somewhere it is possible to remove Ubuntu from a Live-CD.


**So I Booted from Ubuntu 8.04 Live-CD,went to G-Parted**:
(where the '±' symbol represents a Key icon and '|' separates column)


_Partition |Filesys |Size |used |unsused |flag_
/dev/sda1 !  |ntfs | 22.26 |    |     |boot
&#9660; /dev/sda2 ±|extended |16.03 g
    /dev/sda5|ext3 |15.4 g |2.78 |12.63     
    /dev/sda6 ± |linux swap |635.35 m

G-Parted would not allow me to select partitions w/ the Key '±' symbol to edit them. 

So I stopped there and I am asking for help.
What steps do I take next to 
A) Totally Remove Ubuntu
B) Maintain Windows XP

---

### Post by dabl on 2010-04-27
Short answer:  boot your Win XP installation CD, choose "Repair", and run "fixmbr".

Longer answer:  you probably want to re-format the hard drive partition(s) used by Linux to NTFS filesystem, so they will be recognizable and usable by Win XP.  I think your Ubuntu 8.04 Live CD has GParted on it it -- you can used that.  Be sure you reformat the correct partition(s)!

---

### Post by jbocean on 2010-04-27
Thanks for the Reply.

1. My Father-In-Law got the computer at a yard sale, so we don't have the Windows XP install disk. 

2. We might have another Windows XP disk around the house; Would Any Windows XP install disk work, or does it have to be the specific disk w/ the specific Microsoft License # to be able to run 'fixmbr'* 

3. Not sure how to for-sure recognize which partitions are Linux vs Win, but once I learn that - I may be able to go and change Linux partitions to ntfs. How will that move me towards overall goals of:
     A. Totally Remove Ubuntu 8.04
     B. Still keep working Win XP

* does mbr stand for Master Boot Record?

---

### Post by dabl on 2010-04-27
Yes, any Win XP installation CD should work to fix the Win bootloader.

Yes, their "fixmbr" command installs the Win bootloader into the Master Boot Record.

As far as re-formatting the partition(s) where Ubuntu is presently installed, Windows will not "see" the extra disk partition, which is presently formatted ext3 I assume, unless you either install an ext3 driver for Windows, or else reformat it NTFS.  Regarding "removing" Ubuntu, once you're not able to boot it (after reinstalling the Windows bootloader), it is just a bunch of files on an ext3 partition.  So, reformatting that partition to NTFS kind of finishes the job and makes the partition available for Windows.

If you also made a Linux swap partition, there's an additional bit of space that you could potentially reclaim.  To combine it with the main Ubuntu partition, you would need to use GParted (from a Live CD).

---

### Post by jbocean on 2010-04-27
And is there a way to totally remove Ubuntu 8.04 and still keep working Win XP - if I *don't* have a Win XP copy handy?

btw all my important data IS backed up already.

---

### Post by dabl on 2010-04-29
You might be able to do what you want with Super Grub Disk: [http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)

---

