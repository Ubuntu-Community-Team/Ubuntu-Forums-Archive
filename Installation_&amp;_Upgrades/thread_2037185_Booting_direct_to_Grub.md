---
title: "Booting direct to Grub"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by Davey H on 2012-08-03
Hello,
I have a Dell Inspiron 530 with two hard drive. From a fresh install throughout I first put Win XP Pro on one disk and then Ubuntu 12.4 on the other.

I followed an online guide to do this and both boot up and run OK.

The only difference is that in order to get to the Ubuntu drive I have to enter the boot menu and select the drive. This then goes to the grub before loading.

Its not a major hassle, just a bit of an annoyance doing it this way. Anyone now if there is a way to get the computer to boot into the Grub menu first off please?

David

---

### Post by oldfred on 2012-08-04
Is grub on the MBR of the Ubuntu drive? If so just reset BIOS to boot that drive first.

From Ubuntu this should add Windows to the grub menu if not already there:

sudo update-grub

You can reinstall grub to the Ubuntu drive from inside your working install with this:
sudo fdisk -lu
#Then choose correct drive sda or sdb, sdb shown as example:
sudo grub-install /dev/sdb

If you still have issues download and run the BootInfo report and post the link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Davey H on 2012-08-04
Thanks for the reply. 

I will have a go at resetting the boot order. I seem to remember getting an error when I done that but I can't recall now. Will try again. 

I guess that I am just concerned of messing it all up being as it all works, I've seen many threads about boot errors in these forums.

Will try again and report.

cheers

---

