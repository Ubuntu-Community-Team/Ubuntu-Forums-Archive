---
title: "GRUB &amp; other boot systems (windows)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by bgabga on 2010-05-01
I have Win7 and ubuntu installed on the same PC. Win7 was installed first, after I installed GRUB from Ubuntu, Win7 is not listed as a second option to boot.

FYI, On the same PC I had Win7 and Debian (before changing from Debian to Ubuntu) and GRUB from Debian was showing Win7 as second option for boot. Ubuntu was installed on the same partitions as Debian. (For Win7 I have 2 partitions one 100M-system reserved and one 30G; both on NTFS).

I have:
Linux ubuntu 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux


Please help on setting  /boot/grub/menu.ls file to add Win7!
(I will do also a fresh install for Ubuntu 64Bit)

Thank you

---

### Post by Naitsirhc Hsem on 2010-05-01
you can try running sudo update-grub in the terminal

---

### Post by bgabga on 2010-05-01
I did:


$ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub

but grub list was not updated with windows.

---

### Post by Naitsirhc Hsem on 2010-05-01
What does gparted say about your windows drive? is it bootable?

---

### Post by bgabga on 2010-05-01
Yes, sdb1 is bootable.

sdb1                           Boot                        Primary                   NTFS  
sdb2                                                          Primary                   NTFS  
                                                                                                Unusable 
sdb4                                                          Primary                  Linux raid autodetect
sdb5                           NC                          Logical                   Linux raid autodetect
sdb6                                                          Logical                   Linux raid autodetect
sdb7                                                          Logical                   Linux ext3           


sda1                           Boot                        Primary                   Linux raid autodetect 
sda2                                                          Primary                   Linux raid autodetect 
sda3                                                          Primary                   Linux raid autodetect 


df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/md0                25G   3.3G    21G  14% /
/dev/sdb7              434G    83G   329G  21% /data
/dev/md2               464G   208M   440G   1% /data-raid

---

### Post by razy60 on 2010-05-01
Try in win 7 to reformat the partition that contained debian  to ntfs then extend that into your win 7 drive, then try a fresh install it should give you the option to Then resize and install, although i am not sure how that works with your raid set up, You may want to repair your mbr by using your win7 install disc first, 

Raz

Just found this if its any help [http://sourceforge.net/apps/mediawik...ms:Boot_Sector](http://sourceforge.net/apps/mediawik...ms:Boot_Sector)

---

### Post by bgabga on 2010-05-01
Is this a bug in GRUB Ubuntu (since with Debian GRUB was OK)?

---

### Post by malrost on 2010-05-01
Please post your /boot/grub/menu.ls

You might have to manually edit it and add a Windows boot entry. Like you, I have a Windows partition on sdb1 (though XP, not 7.) Here's why my GRUB boot entry for it looks like:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


It can get a bit confusing because of the different partitioning nomenclature. GRUB starts counting at 0, while gparted starts at 1. For example sda = (hd0), and sdb = (hd1). Similarly, sdb1 = (hd1,0) and sdb7 = (hd1,6). (See [this]("http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html") for further detail.)

So if you wanted to point the rootnoverify to sdb2 instead, the line would read rootnoverify (hd1,1). HTH.

And see [this]("http://www.gnu.org/software/grub/manual/grub.html#map") for a description of the map lines.

---

### Post by ctsbc on 2010-05-01
Take a look at this link: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by bgabga on 2010-05-01
Here is my menu.lst

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-18-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/md0 ro quiet splash quiet 
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/md0 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bgabga on 2010-05-01
> **ctsbc said:**
> Take a look at this link: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I did not find:


  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm
from testdisk

---

