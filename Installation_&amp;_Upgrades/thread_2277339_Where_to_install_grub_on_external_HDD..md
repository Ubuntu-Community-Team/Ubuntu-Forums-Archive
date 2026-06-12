---
title: "Where to install grub on external HDD."
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by Furest on 2015-05-08
Hi!
I'm actually trying to install ubuntu on my external HDD which is partitionned like thisl:

900GB for DATA, sdb1  |  91GB for Ubuntu (ext4), sdb5  |  9GB for SWAP, sdb6

I already have things on the 900GB partition as I had to reinstall ubuntu (formatted the partitions with gparted and then went with a clean full install in custom mode).
At the end of the process, it showed me an error because it couldn't install grub on sda (which is the 8GB fake disk of the virtual machine I ran it with) so I choosed /dev/sdb5 which is the partition where the root (/) is.
But at my surprise it didn't boot and showed me an error: no such partition... and showed me the console...
What did I do wrong and how could I fix it?

Thank you ;)

---

### Post by plucky on 2015-05-08
> **Furest said:**
> Hi!
I'm actually trying to install ubuntu on my external HDD which is partitionned like thisl:

900GB for DATA, sdb1  |  91GB for Ubuntu (ext4), sdb5  |  9GB for SWAP, sdb6

I already have things on the 900GB partition as I had to reinstall ubuntu (formatted the partitions with gparted and then went with a clean full install in custom mode).
At the end of the process, it showed me an error because it couldn't install grub on sda (which is the 8GB fake disk of the virtual machine I ran it with) so I choosed /dev/sdb5 which is the partition where the root (/) is.
But at my surprise it didn't boot and showed me an error: no such partition... and showed me the console...
What did I do wrong and how could I fix it?

Thank you ;)

Normally you would specify /dev/sdb and not the partition /dev/sdb5.

If you can get into your system you could run ```
sudo grub-install /dev/sdb
``` which should write to the MBR of sdb.

Or if you re-install Ubuntu then specify /dev/sdb at the partitioning stage.

Good Luck

---

### Post by Furest on 2015-05-08
Hello! Thank you for the quick answer ;)
I just tried the command you gave me and I have an error : "failed to get canonical path of '/cow'...
Of course there are no cow in my HDD (I would hear it lol) but still he needs it :p
Any idea? :)
Oh and btw, he wants to install it in i386 which is 32-bit and my system, the installed ubuntu and the ISO are x64... is it normal?

---

### Post by plucky on 2015-05-08
> (which is the 8GB fake disk of the virtual machine I ran it with)

I don't understand this statement.

Did you run the install from an 8Gb usb drive?

I think you should run the install again and this time specify the boot device to be /dev/sdb instead of /dev/sdb5.

Then see if it will boot.

How is the external HDD connected?

---

### Post by oldfred on 2015-05-08
If you can boot into external from your grub in your virtual install's grub (is that possible?) then you just need the         sudo grub-install /dev/sdb

But if virtual install is just the ISO and you attempt to run that command you do get the /cow error as you are installing from the live installer to the live installer which you cannot do.

If from live installer you  can mount your install and then install to sdb. Or use Boot-Repair. Or use Supergrub to boot into it and then run the fix.

      Your need to change all of the examples to sdb & your sdbX partition instead of sda5.
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Furest on 2015-05-08
Sorry for answering late I had a bunch of things to do.
First over all I solved my problem via this tutorial: [http://openclassrooms.com/forum/sujet/pas-de-grub-au-demarrage-du-pc/84716723](http://openclassrooms.com/forum/sujet/pas-de-grub-au-demarrage-du-pc/84716723)

Explanation of the situation:
As I only have 1 pc for now, I like to be able to do my work while installing ubuntu on the external HDD so I created a virtual machine (with virtualbox) and created it with a 8GB VHD (I had no choice to create one).
I installed it correctly BUT installed GRUB on the partition which I shouldn't have done.

After searching longer I found the tutorial on openclassrooms.com and I worked perfectly.

Thank you for the help though!

Furest

Please note that I am not talking about any dual-boot (hi newcomers from google). As I worked under virtual machine only my USB HDD, the empty VHD and the virtualized ISO existed.

---

