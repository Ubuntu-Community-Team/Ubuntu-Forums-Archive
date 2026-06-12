---
title: "Boot Loader...will not load"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by psyllex on 2012-12-22
Hello all...I'm actually shocked I've never came here to the forums before now.  

I was messing around with my Windoz machine delete sys files in an effort to install a partition with Ubuntu on it.  Unfortunately I wasn't paying attention and I highlighted the partition I wanted but didn't choose from the drop down list and wiped my entire disk...lol.  As many times as I've install Ubu you think I would've remembered that.  But, I disgress.  I installed from a usb stick and somehow the grub/boot loader is on my usb stick....but not my hard drive.  

Is there a way to change this?  I looked in /boot/grub and the grub.cfg file is in there but for whatever reason it isn't loading when I reboot.  I 'have' to have my usb stick in order for Ubu to boot correctly...then I can pull it out and it runs fine (a little slow honestly ).  

I tried to ```
sudo grub
```....It says it can't find grub.  I tried ```
sudo grub-install /dev/sda
``` and it didn't like that either.  Does anyone have any suggestions?

---

### Post by fantab on 2012-12-23
If you search the forums with terms, "reinstall Grub" or "fix grub" you will get answers to your question. It pays to do your own research first. 

For now, you will have to reinstall Grub using a Live Medium (in your case USB); [**Read Here**]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2").

---

### Post by darkod on 2012-12-23
The second command should have worked if your hdd is /dev/sda. And you have to have the stick plugged in.

If the /boot/grub folder you mentioned is on your hdd, then only the frist part of grub2 ended up on the MBR of the stick.

Plug in the stick, boot once, leave it connected and first check which is your hdd, /dev/sda or /dev/sdb. You can check that with:
sudo fdisk -l (small L)

Once you know for sure, use the command with the correct letter:
sudo grub-install /dev/sdX

---

### Post by oldfred on 2012-12-23
If still having problems, install Boot-Repair to your Ubuntu install flash drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

