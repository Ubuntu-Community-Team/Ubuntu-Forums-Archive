---
title: "Windows doesnt show up on Grub - boot repair URL included"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by magnificat2 on 2015-02-12
I installed Ubuntu on one of my hard drives, but now I can't see Windows when Grub starts.  Windows is installed on the other hard drive.  Any suggestions?  My boot-repair URL is: [http://paste.ubuntu.com/10181160/](http://paste.ubuntu.com/10181160/)

Is there any other information I can include that would make this easier to answer?

Thanks!

---

### Post by yancek on 2015-02-12
You have windows installed in MBR mode on the first drive and Ubuntu using UEFI/GPT on the second drive and they conflict.  My understanding is that you need to make the selection in the BIOS to boot either drive in that situation.  I'm fairly certain there is a method to change it but I don't use UEFI so you'll need to wait for someone with more specific knowledge on the subject.

---

### Post by Gvarelov on 2015-02-13
GRUB should be able to auto- detect presence of other OSes on the disk. Can you make GRUB display its view of disks and partitions? Get to the GRUB prompt and issue the ls command. 
Do you remember at install time, where was GRUB installed? On a partition or to the MBR?
It is possible that you'd need to get the os-prober package or that the os-prober file in /etc/grub.d was for some reason marked as non- executable.
So possible course of action would be:
1. Check where is GRUB installed:
```
sudo grub-probe -t /dev/sda /boot/grub
```
2. Check if the os-prober file is executable:
```
sudo ls -l /etc/grub.d/30_os-prober
```
If it isn't executable, make it executable like so:
```
sudo chmod +x /etc/grub.d/30_os-prober
```
and then issue:
```
sudo update-grub
```
If for some reason you are missing os-prober utility, get it via:
```
sudo apt-get install os-prober
```
and then run update-grub.
Windows still not showing up in the GRUB menu? You may want to consider installing GRUB to the MBR:
```
sudo grub-install /dev/sda
```

---

### Post by Gvarelov on 2015-02-13
From the file you posted in the pastebin it seems that GRUB isn't in the driver seat when it comes to booting. Just out of curiosity, which OS are you booting into by default when you turn on your computer?
GRUB would be in charge of booting if it was installed in the MBR.

---

### Post by oldfred on 2015-02-13
UEFI and BIOS are not compatible. You can only boot from UEFI boot menu and may have to turn on/off UEFI or CAM/BIOS mode to boot system installed in that mode.
And grub can only offer to boot systems installed in the same boot mode as it does not do a full reboot to switch boot modes.

You can use Boot-Repair to uninstall grub-efi(UEFI) and install grub-pc(BIOS) without totally reinstalling. Then you should be able to dual boot from grub menu. 
Do not run Boot-Repairs auto fix as that will just install grub to all drives. You want to keep Windows boot loader on Windows drive sda.

---

