---
title: "Upgrade LUbuntu 17.04 to 17.10 Large File Copy Fail"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by takahe2 on 2017-10-29
The machine - a Dell 530s - has worked pretty well for years as a LUbuntu/WinXP dual boot. The one problem I have never had is copying large files between partitions - until this latest upgrade. The upgrade worked fine on 2/3 machines - one server and one desktop. Not the 530s.

I have tried using command line copying and PCManFM the problem is the same - the CPU in task manager heads to 100% and -nan% within short order... the RAM of 4GB never above `400MegB'. Eventually the machine hangs and it has to be powered off before restarting.. the journal rebuilds and I can log in again as though nothing has happened...  

There is plenty of old discussion about the problem of  hanging while copying and usb copying but not this. 

Any ideas based on experience would be appreciated. Thanks

---

### Post by TheFu on 2017-10-30
Use   rsync.

---

### Post by sudodus on 2017-10-30
Are you running the 64-bit or 32-bit version of Lubuntu? I am asking because I had a similar(?) problem, when 16.04 LTS was new. I think it was only affecting the 32-bit version. (It was probably due to some low level bug, because it affected several tools, Disks (gnome-disks) as well as cp, cat and rsync. But tar worked. After some update & upgrade, that bug was squashed).

Please give an example of a big file, that cannot be copied (file size).

Please try to copy the same file, when running Lubuntu 17.10 live (booted from a DVD disk or USB pendrive), 'Try Lubuntu'. This way you can tell, if the problem is caused by something that is left from 17.04 after the upgrade.

---

### Post by takahe2 on 2017-11-02
Thanks for the feedback folks - the machine is a 32-bit Dell 520s running Lubuntu 17.10 (almost!). The file being copied is ~15GB - a virtualbox machine (virtual box seems to only access in this version machines on the linux partition (as this occurs on the working desktop, also 32-bit, I suspect this is more an issue of Lubuntu being ahead of vb than an issue with the Lubuntu).
I have tried rsync with the same results - hung machine.
Currently away from machine but will try the live version as suggested and report results. I do have a working live version on a USB.
Thanks again for the suggestions.

---

### Post by sudodus on 2017-11-02
If the VirtualBox is turned off (not running), the files belonging to virtual machines should work like any file, and should be possible to copy. I think there is a bug or incompatible library due to the upgrade from 17.04 to 17.10.

But it might be something else, for example some defect in the RAM. You can test the RAM with memtest from the boot menu.

Anyway, good luck with the live system :-)

---

### Post by ynota on 2017-11-02
takahe2 you will have problems with copying a 15GB file on to a 32 bit OS, have a read of [this]("https://en.wikipedia.org/wiki/Large_file_support") wiki, it explains maximum files sizes..

---

### Post by takahe2 on 2017-11-22
Just a quick response after re-engaging with this issue and as a  courtesy to those who have responded. I have two 32-bit, dual-boot  (WinXP/Lubuntu) machines - both work fine except for the 530s (the other  is a D620) when copying large files. On shared directories the format  is NTFS.

1. The copying of large files (~15GB) is not an issue  with the D620 - have tested both in parallel with NTFS formatted 32GB  USB sticks.
2. The files, the partitions and the hardware (memory,  and hard-drive: bad sectors none) on the 530s all pass testing with  various utilities.
3. I ran htop on both machines yesterday and  monitored both... despite the very high cpu usage nothing unusual. The  530s froze at 99% complete on several occasions. 

At this stage I  have a workaround (WinXP) to move to/from NTFS partitions which I've  found is generally faster even with modifying fstab mounts with ntfs-3g  and big_writes. 

Reinstall/repair lubuntu 17.10? No. Not until  I'm satisfied that the error is not due to hardware (unlikely though it is a Dell 530s  and has made the forum on a few occassions)  or some obscure user  input. Moreover, the machine has been updated from several versions of  lubuntu and a reinstall should really be a clean install to be sure to  be sure.

Will update in the event of new info. Thanks again for the feedback. 

Stop using lubuntu? No way. Despite hanging numerous times during file transfers and numerous changes to mounts, fstab etc by a novice user.. it still boots and runs 99.5% of what I want.

---

### Post by sudodus on 2017-11-22
Instead of or before re-installing you can try other versions live, Lubuntu 16.04.1 LTS and Lubuntu 17.10.

See this link, [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

It is a good idea to test copying your huge files when running live (booted from a DVD/USB drive with Lubuntu).

---

