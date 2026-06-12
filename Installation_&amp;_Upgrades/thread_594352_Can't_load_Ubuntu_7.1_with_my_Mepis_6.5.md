---
title: "Can't load Ubuntu 7.1 with my Mepis 6.5"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by cary123 on 2007-10-27
I'm standing on the very edge of the pit of despair!!!  I have an Element computer, Ion.  It was made by a linux co.  I have always had Mepis on it.  Just installed Mepis 6.5.  A friend told me Ubuntu would clear up a lot of problems I was having.  That was 1 week ago!  I've tried everything, I know the installation manual by heart.  Yes, I'm a newbie toddler but I will try anything if directions are clear and simple.
  I found the directions for installing from linux.  Typed in everything and had to improvise 1 line (most thrilling for a newbie!) you copy to a partition on the harddrive and pick "installer" from boot screen.
    mkdir /tmp/install_cd...umount /tmp/install_cd
  It all worked until I tried to boot and then I got this message:
      root (hd0,3)
   Filesystem type is ext2fs, partition type 0x83
   Kernel /casper/vmlinuz boot=casper
   root=/dev/ram ramdisk_size=1048576 rw
   Error 15: file not found
I checked w/ kwikdisk and the partition is there and formatted ext3 like the directions say.  I have tried for 1 solid week.  It would not boot from the cd because it couldn't read graphics card and monitor and the screen was garbled.  (Already tried all those fixes - NOT).  Is this a Mepis thing?
Please help.

---

### Post by logos34 on 2007-10-28
> **cary123 said:**
> 
      root (hd0,3)
   Filesystem type is ext2fs, partition type 0x83
   **[COLOR="Red"]K[/COLOR]**ernel /casper/vmlinuz boot=casper
   root=/dev/ram ramdisk_size=1048576 rw
   Error 15: file not found

I assume you're referring to [this guide]("https://help.ubuntu.com/community/Installation/FromLinux").

It may be case-sensitive, which would explain why it's throwing an error. ..Try '**k**ernel...'

Otherwise you might try the text-based **alternate desktop CD**.

---

### Post by cary123 on 2007-10-28
I didn't type in "Kernel", that was message computer gave me.  After searching MANY forum pages, I have found that many people who  are trying to upgrade from 7.04 to 7.10 are having the same problems I am of trying to go from Mepis 6.5 to Ubuntu 7.10.  Garbled graphics, black screen, kernel panic, etc...  This must be a linux thing and not an ubuntu thing.  Will keep trying fixes.  Will they put the 7.04 back up or try to fix the linux conflict with 7.10???  I would really like to try ubuntu but this is taking up 90% of my life :sad:

---

### Post by logos34 on 2007-10-28
> **cary123 said:**
> I didn't type in "Kernel", that was message computer gave me. 

yes, but I think the error message is printing back the entry as it appears n the menu.lst, and you edited it.  So reboot and select that entry, hit 'e' to edit, hit 'e' again on the 'kernel' line and correct it if necessary.  I don't know if that will solve the problem but it's worth a try

---

### Post by cary123 on 2007-10-28
Sorry, typing error.  It was a small "k" in the message and on my menu.lst.  I did go back and look in the partition I made for ubuntu and I can't find anything about the kernel.  When I used the CD and used the console, I typed in (hd0,3) at the boot prompt and it said it could not find kernel image at (hd0,3). I was going to try what zveroboy did and add corresponding initrd entry to the 2.6.22-14-386 and 2.6.22-14-generic kernels but I can't find anything that matches it.  What is it under?  When I look in my ubuntu partition, the disk is there and there is folder "installer" but there doesn't appear to be anything in there.  Also tried what Stemp suggested for the black screen when using the CD.  I typed: sudo dpkg-reconfigure -phigh xserver-xorg, which took me to a screen where I could change the resolution but I could not get out of the screen and it wouldn't let me configure the resolution.  Is anything working?,

---

### Post by logos34 on 2007-10-28
> **cary123 said:**
> Sorry, typing error.  It was a small "k" in the message and on my menu.lst.  I did go back and look in the partition I made for ubuntu and I can't find anything about the kernel.
When I used the CD and used the console, I typed in (hd0,3) at the boot prompt and it said it could not find kernel image at (hd0,3). I was going to try what zveroboy did and add corresponding initrd entry to the 2.6.22-14-386 and 2.6.22-14-generic kernels but I can't find anything that matches it.  What is it under?  When I look in my ubuntu partition, the disk is there and there is folder "installer" but there doesn't appear to be anything in there.

EDIT: Check the Gutsy CD contents--the folders may have changed since Feisty.  If vmlinuz and initrd.gz are inside 'installer' folder instead of 'casper' folder, you need to alter the menu.lst entry (the 2.6.22-14-generic is not relevant here; it's what you see later in /boot after installation is complete). If the partition your created and copied the cd to is /dev/hda4 (or sda4), then the menu.lst entry should be:

> title installer
root (hd0,3)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw  
initrd /casper/initrd.gz

* or 'kernel /installer/vmlinuz...'

> Also tried what Stemp suggested for the black screen when using the CD.  I typed: sudo dpkg-reconfigure -phigh xserver-xorg, which took me to a screen where I could change the resolution but I could not get out of the screen and it wouldn't let me configure the resolution.  Is anything working?,

alternatively try

**sudo dpkg-reconfigure xserver-xorg**

Or as I suggested above do a text-mode installation using the [alternate desktop CD]("http://www.ubuntu.com/getubuntu/download")
(tick box below green 'Start Download' icon)

---

### Post by cary123 on 2007-10-28
vmlinuz and initrd.gz ARE in the 'casper' folder.  I will try the other suggestion "sudo dpkg-reconfigure xserver-xorg" when I can figure out what I did to get into the terminal.  Might try it on kubuntu because all I get there is a console.  I only have dial-up so will have to see if my friend will download the alternate CD for me.  Will all these problems happen with the 7.04?  I will try that one if it's better.  Thank you so much for your time and help, logos34.  The bright side to all this is I have never "messed" with commands before and it was so exciting to see that
"installer" come up on the boot screen and to know that I did that!  Even if it didn't work, I sure have learned a lot this past week.  Thanks again, and I will keep trying. :)

---

