---
title: "[SOLVED] PCLOS reinstall messed up Ubuntu instillation"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2008-08-30
I have Ubuntu 8.04 on my boot drive ( the first drive in my computer) and PCLOS 2007 on my second drive. I had to reinstall PCLOS and now I'm having a problem booting up Ubuntu. Ubuntu starts with the splash screen, then goes to white text ending with the text below. 

fsck 1.40.8 (13-Mar-2008)

/dev/sda5: clean,
/dev/sda1: clean,
fsck.,ext3: Unable to resolve 'UUID=C9e56b85-9719-4340-a8fa-e3cb5e0950cs'
fsck, ext2: Unable to resolve 'UUID=dd500520-Cbb9-4481-9670-81cd69c692b3'
fsck died with exit status 8

*File system check failed.
A log is being saved in
Please repair the file system manually.
*A maintenance shell will now be started. 
CONTROL-D will terminate this shell and resume system boot.
Bash: no job control in this shell

And then there were 7 more lines of bash stuff. I pressed CONTROL-D and it booted into login. After login it booted into the desktop. The desktop acted normally until I tried to load a program (any program) and the program would start to boot and then it wouldn't boot, it would just stop.

When I first installed Ubuntu and PCLOS I made a root partition a home partition and a swap partition on both drives with PCLOS and formatted the partitions with PCLOS. Then I installed Ubuntu on the first drive so Ubuntu formatted the partitions on the first drive again. Then I installed PCLOS on the second drive and until I had to reinstall PCLOS everything has worked fine.

Is there any way to fix this? Do I have to reinstall Ubuntu? If I have to reinstall Ubuntu I know that will blow out PCLOS and I'll have to reinstall PCLOS again. Thankx for any help.

---

### Post by prshah on 2008-08-30
> **Spaceman9 said:**
> 

fsck 1.40.8 (13-Mar-2008)
/dev/sda5: clean,
/dev/sda1: clean,
fsck.,ext3: Unable to resolve 'UUID=C9e56b85-9719-4340-a8fa-e3cb5e0950cs'
fsck, ext2: Unable to resolve 'UUID=dd500520-Cbb9-4481-9670-81cd69c692b3'
fsck died with exit status 8


Looks like some leftover/ghost entries; can you post the following outputs? To get to a working prompt, either boot into recovery mode or, boot normally, and press Ctrl+Alt+F1 to get to a prompt```
cat /etc/fstab
sudo blkid
``` (No need for sudo if in recovery console.)

---

### Post by Spaceman9 on 2008-08-30
prshah thank you for the help. Here is the stuff you asked for.

bruce@bruce-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cb772597-a441-4caf-a123-8c8fe300956c /home           ext3    relatime        0       2
# /dev/sda6
UUID=4db8a804-f90a-4ac6-a93d-51ed119ee827 none            swap    sw              0       0
# /media/sdb1
UUID=cae56b85-9719-4340-a8f8-e3cb5e0950c5 /media/sdb1 ext3 relatime               0       2
# /dev/sdb5
UUID=8070c047-730f-4378-ae5a-869eb51318f6 none            swap    sw              0       0
# /media/sdb6
UUID=dd500520-cbb9-4481-9670-81cd69c692b3 /media/sdb6 ext2 relatime               0       2
# /media/sdc1
UUID=4a4062e0-e07d-4012-b7b2-80eb19f8125b /media/sdc1 ext3 relatime               0       2
# /dev/sdc5
UUID=4766e575-f47c-454d-8d8e-7bae96ff910b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,users,noauto,fmask=111,dmask=000,exec,utf8 0       0
/dev/sdd        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
bruce@bruce-desktop:~$ sudo blkid
[sudo] password for bruce: 
/dev/sda1: UUID="00186574-55f8-44d1-ac03-04b9ebb7cc9a" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: UUID="cb772597-a441-4caf-a123-8c8fe300956c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="98b5dee2-e122-440f-b9ed-7e561957be04" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="19068d35-b753-4de0-b149-62d51cdc9b22" 
/dev/sdc1: UUID="4a4062e0-e07d-4012-b7b2-80eb19f8125b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="f3149431-9496-4c3b-866b-21d1bbbac7bb" 
/dev/sda6: TYPE="swap" UUID="777d3bf1-e7f2-4fe8-809f-8f892a5f96ab" 
/dev/sdb6: UUID="61c45f6f-46a6-4e6d-a5dc-392eff5bba87" TYPE="ext2" 
bruce@bruce-desktop:~$ 

It looks like the UUID on sdb1, sdb5 and sdb6 changed after I reinstalled PCLOS. So, if I edit the menu.lst and put in the new UUID's for the partitions on my b drive would that solve the problem?

Or, what if I comment out any entries in ubuntu's fstab for any hd partitions* other than the ubuntu /* home and swap and then try booting it. Would that work?

---

### Post by Spaceman9 on 2008-08-30
I tried typing in the new UUID's by hand but it made things worse. I don't know what else to do.

---

### Post by confused57 on 2008-08-30
> Or, what if I comment out any entries in ubuntu's fstab for any hd partitions* other than the ubuntu /* home and swap and then try booting it. Would that work?

That should work...

---

### Post by Spaceman9 on 2008-08-30
> **confused57 said:**
> That should work...

Thankx for your help. I'll try it again.

---

### Post by confused57 on 2008-08-30
> **Spaceman9 said:**
> Thankx for your help. I'll try it again.
Commenting out your PCLinuxOS partitions should enable you to boot Ubuntu, then you can change the fstab in Ubuntu to reflect the partition designations, e.g.:

```
# /dev/sda1
UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=cb772597-a441-4caf-a123-8c8fe300956c /home ext3 relatime 0 2
# /dev/sda6
UUID=4db8a804-f90a-4ac6-a93d-51ed119ee827 none swap sw 0 0
# /media/sdb1
/dev/sdb1 /media/sdb1 ext3 relatime 0 2
# /dev/sdb5
UUID=8070c047-730f-4378-ae5a-869eb51318f6 none swap sw 0 0
# /media/sdb6
/dev/sdb6 /media/sdb6 ext2 relatime 0 2
# /media/sdc1
UUID=4a4062e0-e07d-4012-b7b2-80eb19f8125b /media/sdc1 ext3 relatime 0 2
# /dev/sdc5
UUID=4766e575-f47c-454d-8d8e-7bae96ff910b none swap sw 0 0
```
You don't need but the one swap for Ubuntu, so you can comment out any of the other swap partitions.

---

### Post by prshah on 2008-08-31
> **Spaceman9 said:**
> 
Or, what if I comment out any entries in ubuntu's fstab for any hd partitions* other than the ubuntu /* home and swap and then try booting it. 

As others have said, this sounds like a good plan. You can start with this, and if everything is OK, add back your other partitions one at a time.

---

### Post by Spaceman9 on 2008-08-31
I did try what you talked about so far but Ubuntu was still running very slowly when I booted any software. I decided to redo my 3 hard drives and see if may be I can set up the 2 distros better this time.

I'm putting the swap partition on the backup drive instead of the drives the distros are on. I'm just reinstaling Ubuntu and PCLOS. Should I make a swap partition for each distro or should I just make one swap partition for both distros to use? Thankx for your help guys.

---

### Post by prshah on 2008-08-31
> **Spaceman9 said:**
> 
Should I make a swap partition for each distro or should I just make one swap partition for both distros to use? 

Single swap partition is fine. Note that if you hibernate any one OS, the hibernation image will be saved to the swap; this may cause problems if you hibernate one OS and switch to the other (which I imagine will try to load an incompatible hibernation image..)

In short, if you hibernate, don't switch.

btw, if your "backup drive" is an external, putting swap on it is a bad idea.

---

### Post by Spaceman9 on 2008-08-31
prshah, I didn't know that about hibernation. I learn a lot at this forum. I've never used hibernate so I'll just make one swap. Thankx for your help.

---

### Post by Spaceman9 on 2008-09-01
Ok, I had to reinstall Ubuntu. I just couldn't get it working normally again. Thankx very much for all your help guys.

---

