---
title: "ubuntu error: system error The boot files of [Ubuntu 12.10] are far from the start of"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by BenginM on 2012-10-26
i was trying to help a friend of mine installing Ubuntu after he tried  it and decided to dual boot with his Windows Xp , after the installation  was done , he rebooted then got an error message : "error: system error  grub rescue".

i suggested he should try and fix it using the tool "boot-repair" .. but then he posted th following link ..

[http://paste.ubuntu.com/1307036/](http://paste.ubuntu.com/1307036/)

after  noticing he downloaded and actually trying to install Ubuntu 12.10 and  not 12.04! i suggested he should download and try to install Ubuntu 12.04  instead , and so we went to start the whole process all over again ,  but this time i made sure to check and test with the ISO MD5sum , he  matched , then he went to burn the iso using Unetbootin , after that he  gone Off-line .. haven't seen him since !

 I spoke to a friend on IRC at #ubuntu , he noticed the extra partition /dev/sda5 .. which was a good catch of him! 

I checked the partition table with him during the installations process , he never mentioned that he added  an extra partition , which later on turned out to be /dev/sda5 !

So what to do next !,  is it save to remove this partition? .. adding a /boot partition sounds fruitless to me!

# any thoughts, hints!

---

### Post by dino99 on 2012-10-26
i've read some users comments having similar issue, but it was on system with many many partitions (> 25) some primary and others embebded.
Windows is known to require its bootloader installed on  the first primary partition, but linux usually does not care.
Anyway its better to set grub on /dev/sda in all cases, even if ubuntu is installed somewhere else.

---

### Post by BenginM on 2012-10-26
Hey dino99! thanks for dropping by , i forgot to mention that later on , he told me that his have a corrupted file in windows and he is unable to boot to his MS Windows Xp.

---

### Post by dino99 on 2012-10-26
what xp have to do with ubuntu installation ? Do you mean that he has made a wubi install ?
Anyway he still can fix xp using the cd and running chkdsk.

here is how i do an ubuntu install:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by YannBuntu on 2012-10-26
Hello

> **Sary.sa said:**
> [http://paste.ubuntu.com/1307036/](http://paste.ubuntu.com/1307036/)

First backup your documents if not done yet. Then:

1) please run Boot-Repair --> Advanced options --> tick "Restore MBR" --> Apply , indicate us the URL that will appear, then reboot the pc and tell us if the pc boots directly XP or not.
2) if not, please use a XP disk to fix it: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you have direct access to XP. Don't continue until you don't access XP.
3) via Gparted, reduce your sda5 partition in order to create 1GB free space just _before_ sda5. Then format this 1GB in EXT4. Write the name (eg sda6) of this 1GB partition on a paper.
4) run Boot-Repair --> Advanced options --> GRUB location tab --> tick the "Separate /boot partition: sdaX" (sdaX must be your 1GB partition) --> Apply , indicate us the new URL that will appear, then reboot the pc and tell us if you see the GRUB menu or not.

---

### Post by j0eb0b on 2012-10-26
You might want to download and try this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I've had good results with Super GRUB fixing both GRUB and MBR problems in both Linux and Windows systems.

---

### Post by BenginM on 2012-10-27
[YannBuntu]("http://ubuntuforums.org/member.php?u=485559") , j0eb0b, thanks guys!

Last night we catch up , only to tell me that he tried to install Ubuntu 12.04 from the USB Stick , but after he did , he gets a flashing course (_) then some errors follow (  out of disk, no suitable mode found, no video mode ... )  , he was able to reach the Desktop , but after a reboot h was unable to boot from the Live out of disk no suitable mode found no video mode-CD anymore , he said if he tries, that will take him to the OS !

could this be something to do with his GPU , or GRUB !

---

### Post by BenginM on 2012-10-28
Salutation !

I found out that he needed to add a separate /boot partition ,  although his partition table is a **non-GPT** , it worked so far !

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

