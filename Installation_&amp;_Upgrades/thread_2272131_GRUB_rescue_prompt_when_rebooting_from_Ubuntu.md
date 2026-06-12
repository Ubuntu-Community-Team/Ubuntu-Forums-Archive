---
title: "GRUB rescue prompt when rebooting from Ubuntu"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by leunam12 on 2015-04-04
Hi, I just got a new computer that has Windows 8.1 UEFI boot, so I took my Ubuntu hard drive (MBR) and installed it in this new computer alongside the Windows disk in order to have a dual boot (2 OS's on two separate disks). Of course the BIOS did not see the non-UEFI disk, so I went ahead and converted the disk to GPT and then ran boot-repair to be able to boot Ubuntu. It worked; so far everything is good, I get a GRUB menu that allows me to choose which operating system I want to boot. But here is the problem: When I boot Windows and restart I get the normal Grub menu, but when I boot Ubuntu and restart I get a GRUB rescue menu. From this point I can simply press Alt+Ctrl+Delete and press F11 to invoke a temporary boot menu from BIOS and choose to boot the Ubuntu disk and it boots fine, but whenever I restart from Ubuntu it goes back to the GRUB rescue. when I restart from Windows everything is normal. I ran grub-update, but nothing, same thing. 

Please help me solve this.

thanks in advance.

---

### Post by pfeiffep on 2015-04-04
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2272060")  "oldfed" posted some guidance about UEFI and grub

---

### Post by oldfred on 2015-04-04
Do you still have Ubuntu in BIOS/CSM mode. When systems are not in same mode you can only boot from UEFI menu.

Best to see lots of details, post link to Boot-Repair's Summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by leunam12 on 2015-04-04
> **oldfred said:**
> Do you still have Ubuntu in BIOS/CSM mode. When systems are not in same mode you can only boot from UEFI menu.

Best to see lots of details, post link to Boot-Repair's Summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I don't know how to change Ubuntu from BIOS mode to UEFI, I have not been able to find any information on how to do this. I am booting Ubuntu in UEFI because my BIOS is set to boot only UEFI mode. I changed the partition table and ran Boot-Repair, that is all that I have done. I can boot to Ubuntu from GRUB if coming from Windows or any other operating system such as live CD's and USB's of different flavors, but when I shut Ubuntu down and try to restart I get GRUB rescue. I will run boot-repair one more time.

---

### Post by leunam12 on 2015-04-04
I ran Boot-repair again. Now I get no such device: e4bb91cc-e35d-4805-89a8-57e89b76aa01
Entering rescue mode.

That UUID is my Ubuntu root partition on sdc1

[http://paste.ubuntu.com/10738678/](http://paste.ubuntu.com/10738678/)

---

### Post by oldfred on 2015-04-04
I suggest once you convert to UEFI, that all drives be gpt partitioned, but it is not absolutely required. Just next time you partition a new drive be sure to use gpt.

I also prefer to have each install boot without any other drive when you have installs on separate disks. Or you should have an efi partition on sdc so grub could be in that drive. Currently your /EFI/ubuntu folder is on sda, but install on sdc. That still should work and it is difficult to add an efi partition afterwards as it should be first or near beginning of drive. And grub installs to sda by default. 

Is sdb a removeable drive, and have you changed drive order by plugging in drives in different SATA ports or is sdc also a removeable drive?
Your fstab says Ubuntu was on sda, your grub.cfg now shows hd2, gpt1 or third drive as grub counts from 0. And UEFI from efibootmgr -v says both Windows and ubuntu on hd2 and UEFI counts starting at 1. And bootx64.efi says hd1. 
Not sure then how your UEFI is enumerating drives, and how removeable drives may change drive order, but order seems mixed.

Do you get grub menu from UEFI boot. I might edit hd2,gpt1 to either hd1 or hd0. Search by UUID should override and incorrect hdX setting, but does not always seem to work.
I have had to experiment with my external flash drive installs as they seem to always be wrong for full drive installs.

---

### Post by leunam12 on 2015-04-04
sdb is not removable, it is a fixed drive that I use for storage since the drives where the Operating Systems are installed are small.
Do you think I should format my ubuntu drive and create an efi partition on that drive and re-install ubuntu from zero? on gparted I can create a new partition at the beginning and move my root partition to the right, I don't know if this is a good idea or not. What do you think?

---

### Post by oldfred on 2015-04-04
I do not like moving partitions right, It takes a long time and has higher risk as everything is copied. Any interruption and you have total loss of data. Or good backups required. If a brand new install, it may be worth doing now, but still not required. 

You do not have to have the efi partition on your Ubuntu drive, and it will not be used by default unless you install by disconnecting all other drives. I installed a second Ubuntu to sdb and told it to install grub to sdb, but it overwrote my sda's efi Ubuntu boot. I then copied that to sdb's efi partition and reinstalled grub to sda. Or it can be a bit of work to get grub to install to same drive. Probably not work repartitioning once installed but next time you totally repartition a drive include the efi partition at beginning of drive.

---

### Post by leunam12 on 2015-04-04
So, I wonder why if I shut Windows down Grub works as expected when I turn the computer back on, but when I shutdown Ubuntu I get Grub rescue. There is something in the Ubuntu installation that triggers this.

---

### Post by oldfred on 2015-04-04
Is it then trying to boot the BIOS install of grub in the protective MBR, not the UEFI install?

You may get that error trying to boot this:

> Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img, but core.img can not be found at 
    this location.

---

### Post by leunam12 on 2015-04-04
how can I solve it?

Thanks

---

### Post by oldfred on 2015-04-04
Did I ask what brand/model system this is?
Many seem to work better if grub copied into /EFI/Boot and you rename bootx64.efi. And then in UEFI set hard drive as default boot entry.
Details on that in link in my signature.

---

### Post by leunam12 on 2015-04-04
MSI motherboard Z87-G45-Gaming. Intel Core i7 4770k Haswell. 8GB ram.

---

### Post by leunam12 on 2015-04-04
I went and copied and renamed the file but it didn't make any difference; but when you mentioned _system_ it gave me an idea: maybe this is system related not OS; so I went and played with the Motherboard's System Setup a little bit and it seems that disabling "MSI FastBoot" did the trick. Having this setting disabled doesn't make any difference in the time it takes to boot; Both Operating Systems still boot in less than 10 seconds. ;)

Thanks for your help

---

