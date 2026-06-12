---
title: "/ swap /home doesn't work with 18.04 installer"
date: 2018-05-31
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2018-05-31
I downloaded standard dekstop 18.04 install and did a fresh install. I did the 'something else' option to create 3 partitions (/ swap /home). I tried installing it 4 times each time recreating the 3 partitions. 3 of the 4 times it failed to install grub. The 4th time it install grub but not the intel wifi driver (the one time it install grub i did not earse the disk and had tried to install grub manually so maybe that is why it worked).
-
I then gave up and had it do the fresh install using the whole disk and it worked without an issue. Of course now i have to figure out how i can add a /home partition.

---

### Post by oldfred on 2018-06-01
UEFI or BIOS install? MBR or gpt partitioning?
Post this:
sudo parted -l

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by anewbie on 2018-06-01
I used the installer partitioning. Copying home was not a huge deal for some reason when I just did the default install it only used 20GB of the disk (it did repartition it but it only took 20GB so I was able to use the remainder of the disk for home by making a new partition).

The machine is kaby lake nuc so it has uefi bios; but secure boot is turned off.

---

### Post by oldfred on 2018-06-01
The NUC seems to want a different UEFI file to boot with.

       Intel NUC
intel nuc - nuc5i5MYHE w/M.2 SSD 
[https://ubuntuforums.org/showthread.php?t=2376245](https://ubuntuforums.org/showthread.php?t=2376245)
boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)

---

### Post by anewbie on 2018-06-01
I'm not sure this makes sense here; as everything worked fine when I just let ubuntu install using the defaults without making my own partitions. Also the install was done on a sata ssd not an m.2 (which is installed in the box but unused - i did check the m.2 after things were working and nothing was installed on it and it is unpartitioned. The thread you mention might be helpful when I reinstall on the m.2 but i don't think it is related to this specific issue. Btw the model I have is: 

BOXNUC7I5BNH
-
I also checked and the disk has a GPT partition so it is using EFI. sdb (which is the m.2 has no partitions at all as expected so the install process did not attempt to put grub on that disk)
-
Basically I stuck an old ssd I had previously used with zfs to test 18.04 with and test the hardware in this nuc which is new. When testing is done I will make the system look like windows 7 and put the ssd in another system i have for a friend (long story but they don't want to upgrade to windows 10 and window 7 is reaching eol).
-
Anyway I added a bit more detail above but the thread you pointed to might be relevant when i try to install on the m.2 but right now it doesn't explain at all why things work fine if i let the installer pick the partitions sizes as oppose to being able to make custom size partitions.

---

