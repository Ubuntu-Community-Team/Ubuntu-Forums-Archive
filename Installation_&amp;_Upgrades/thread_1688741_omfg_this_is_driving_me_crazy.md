---
title: "omfg this is driving me crazy"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by neybis on 2011-02-15
Okay so I have a netbook with 8GB SSD (/dev/sda) and I also have an 8GB SD card (/dev/mmcblk0). All I want to do is create an LVM and boot 10.04. I would prefer the boot partition to be on the root and thus inside the LVM since I know that grub2 supports that. Help!!!

I had to problems creating the LV, however when I get to the part where it installs the bootloader I get an error. It is unable to load grub2 onto /dev/sda. UNR will be my only OS. I skipped past it and tried to install manually and grub_probe kept giving me errors about a cross-disk install referencing the LV root partition. Duh! Of course Im trying a cross-disk install. Used insmod lvm and all that good stuff too. I am willing to start a clean install over and dont be afraid to get technical with me, I have background in Computer Science but for the life of me cannot figure this thing out!

I have performed countless searches, none of the came up with a solution, only others with the same problem. Most of them a while ago and bug should be fixed so not sure why im still having issues.

Please :) for the love of god, help me figure out how to get 10.04 UNR installed on an LVM (preferably with /boot inside the LV root partition since grub2 supports it). Thanks guys!!

---

### Post by neybis on 2011-02-15
how is everyone and their mother getting grub2 installed on an lvm but i cant?? i have been working constantly on this and making no progress despite my research online...

here is some output, maybe this will help you guys help me ;)

root@ubuntu:/# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.

root@ubuntu:/# less /boot/grub/devices.map
/boot/grub/devices.map: No such file or directory

root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

root@ubuntu:/# grub-install --modules=lvm /dev/sda
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
You attempted a cross-disk install, but the filesystem containing /boot/grub does not support UUIDs.

:( i hope someone can me my linux guru savior soon

EDIT:
root@ubuntu:/# blkid
/dev/mmcblk0p1: UUID="LoCZaW-r1cn-e4Bd-vVys-FT9d-Ow39-WHaSMM" TYPE="LVM2_member" 
/dev/sda1: UUID="CPn3Vo-yvkZ-RJ2H-1b0a-Xp6y-0nEc-Tf2OSP" TYPE="LVM2_member" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="2F8D-B53E" TYPE="vfat" 
/dev/mapper/lvm-rootp1: UUID="aa5f9db3-90b1-4b10-b579-9202dbd27c55" TYPE="ext4"

---

### Post by Bucky Ball on 2011-02-15
Welcome. 

I can't really help with this, sorry, but you will get a lot more help with a descriptive thread title rather than this one. Many will just ignore. Remember for next time.  ;)

---

### Post by neybis on 2011-02-15
thank you for the tip :) i hope it helps as this issue has been giving me headaches until about 4AM for the last 3 nights :P

EDIT:
can we close this thread? that way i can just open a new one?

NEW THREAD:
[http://ubuntuforums.org/showthread.php?p=10463011#post10463011](http://ubuntuforums.org/showthread.php?p=10463011#post10463011)

---

### Post by Hakunka-Matata on 2011-02-15
click on **Thread Tools** upper RH portion of screen

---

