---
title: "Win 7 Dual boot, ubuntu grub appears to not be installing"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by ryan461 on 2010-10-21
My dell machine has the following: A raid 0 SAS config with Windows 7 installed in one partition, and ubuntu in the other partition. Then two seperate sata hdd. The raid drive is set as first boot, and Windows views it as disk 0 and boots just fine. When I installed ubuntu 10.04 on the second partition, it viewed the disk as sdc. And when booting off the raid drive, im not given a grub menu to choose ubuntu or win 7, windows 7 boots all on its own. Not sure what im doing wrong here.

---

### Post by P4man on 2010-10-21
Ubuntu probably decided the boot drive is something and put grub .. well, somewhere else :). You could have verified and changed that in the last step of in the installer, but as it is, has its advantages too, now that windows can boot independently of grub, and you avoid any raid trouble. 

Probably all you need to do is change the hdd boot order in the bios, and boot from the drive where grub ended up first.

---

### Post by ronparent on 2010-10-22
When installing 10.04 to a raid, even if you applied the work around to see the raid drive to install to, grub won't often be installed to the right MBR. That would be the MBR for the raid 0 itself.

To fix, you have to reinstall raid to your boot drive (the raid 0). Use this reference as a guide: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

From a live cd list /dev/mapper. The boot drive is the first item listed after control. The remainder of the listing are the raid partitions. Type 'sudo blkid' in a terminal to identify the partition you installed Ubuntu to.

Then, also from the terminal, type:
> sudo mount /dev/mapper/<TheRaidPartitionInstalledTo> /mnt
This will mount your installation to the live session location /mnr. In a terminal 'ls /mnt' if you want to verify.

Now type:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/<RaidBootDrive>

- exactly as written above and with the raid boot drive exactly as you have written in the /dev/mapper listing. If done properly you should now be able to boot to both Ubuntu 10.04 and Win7 from the grub menu. Post how you make out. Good luck.

---

### Post by P4man on 2010-10-22
But why would you install grub on the raid if ubuntu is on another drive? Assuming you manage to have grub see and mount that fakeraid, you risk breaking the raid for windows and being unable to boot windows and you gain nothing. Booting ubuntu becomes dependant on a fragile fakeraid and booting windows depends on grub. Eeck.

Since each OS is on a different drive/arry, just boot from a different drive where grub and ubuntu is, and have grub chainload to windows if you want to boot windows. I always make sure each OS has its own bootloader and is capable of booting independently from its own drive (array), if thats what happened by accident here, I say, keep it like that :).

---

### Post by ryan461 on 2010-10-22
Well i unplugged the sata drives before installing ubuntu, and that got grub to come up. But when ubuntu loads it has a disk error and goes to initramfs or something. so was gonna install win 7 then ubuntu w/o the disks in. but i might need to repair grub as suggested.

---

### Post by ryan461 on 2010-10-22
> **ronparent said:**
> When installing 10.04 to a raid, even if you applied the work around to see the raid drive to install to, grub won't often be installed to the right MBR. That would be the MBR for the raid 0 itself.

To fix, you have to reinstall raid to your boot drive (the raid 0). Use this reference as a guide: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

From a live cd list /dev/mapper. The boot drive is the first item listed after control. The remainder of the listing are the raid partitions. Type 'sudo blkid' in a terminal to identify the partition you installed Ubuntu to.

Then, also from the terminal, type:

This will mount your installation to the live session location /mnr. In a terminal 'ls /mnt' if you want to verify.

Now type:


- exactly as written above and with the raid boot drive exactly as you have written in the /dev/mapper listing. If done properly you should now be able to boot to both Ubuntu 10.04 and Win7 from the grub menu. Post how you make out. Good luck.


Well /dev/mapper/sda1 didnt exist. so i did:

```

sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda

```

Im guessing this isnt what you meant, cause now the boot loader is scrubbed.

---

### Post by ronparent on 2010-10-22
P4man
> My dell machine has the following: A raid 0 SAS config with Windows 7 installed in one partition, and ubuntu in the other partition.

If I read the 1st paragraph in this thread correctly, both Win 7 and Ubuntu are installed on the raid 0 array which it boots to. If that were the case the MBR would be on the array which since 10.04 almost never installs the grub boot loader correctly would have remained untouched. Which would have created the situation that win 7 still booted but he couldn't boot the Ubuntu. That is why I suggested the grub reinstall to the Ubuntu partition with the boot loader on the raid.

ryan461: 
> Well /dev/mapper/sda1 didnt exist. so i did:

It should have been 'ls /dev/mapper' - /dev/mapper/sda1 does _not_ exist. Therefore:
> sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda
is complete nonsense and will not mount a raid drive.

Before things get completely out of control it would be helpful if you ran the Info Script file from: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
and posted the results here.

---

### Post by ryan461 on 2010-10-22
> **ronparent said:**
> P4man
.

If I read the 1st paragraph in this thread correctly, both Win 7 and Ubuntu are installed on the raid 0 array which it boots to. If that were the case the MBR would be on the array which since 10.04 almost never installs the grub boot loader correctly would have remained untouched. Which would have created the situation that win 7 still booted but he couldn't boot the Ubuntu. That is why I suggested the grub reinstall to the Ubuntu partition with the boot loader on the raid.

ryan461: 


It should have been 'ls /dev/mapper' - /dev/mapper/sda1 does _not_ exist. Therefore:

is complete nonsense and will not mount a raid drive.

Before things get completely out of control it would be helpful if you ran the Info Script file from: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
and posted the results here.

Well at this point i have to rebuild the raid as i botched the partition it was on. As for running that script, trying to think how i can get it on the machine and run it from live cd. Cant use USB on the box either, corporate policy.

---

### Post by ronparent on 2010-10-22
If you try another install I would suggest using 10.10. It works better with fakeraid and would probably install grub properly to the raid without intervention on your part! In that case the script would be immaterial.

Keep posting your results. Good luck.

---

### Post by P4man on 2010-10-22
> **ronparent said:**
> 
If I read the 1st paragraph in this thread correctly, both Win 7 and Ubuntu are installed on the raid 0 array which it boots to. 

You are correct, I misread. Probably because I would never even consider installing ubuntu on a windows fakeraid, especially when you have other disks available.

---

### Post by ronparent on 2010-10-22
Neither would I until 9.04. Functionally it has worked quite well. Until 10.10, however, the installations were exciting and different with each release!

---

