---
title: "Grub rescue problem after installing ubuntu 10.04 amd64 after i386"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by morningsunshine on 2010-09-22
Hi all,
 
I have Windows XP dual boot with Ubuntu 8.10 on my system. I brought in a portable HDD on which I installed Ubuntu 10.04 32-bit. The grub boot loader was installed along with this and to boot windows, I've had to plug in the HDD (with lucid install) everytime. It had been working fine. Until few hours back when I decided to put Ubuntu 10.04 amd64 install on this portable HDD.
 
I chose the option - Erase complete drive and install Ubuntu10.04 - and install went alright. Now when the system restarted, it failed to boot up and I receive the grub rescue prompt.
 
I've tried to reinstall grub using references given in posts in this forum but it has not come up till now.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6aeea197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9548    76688608+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            9551       12161    20972795+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           12048       12161      915673+  82  Linux swap / Solaris
/dev/sda6            9551        9595      361399+  83  Linux
/dev/sda7            9596       11939    18828148+  83  Linux
/dev/sda8           11940       12047      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001241f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59345   476686336   83  Linux
/dev/sdc2           59345       60802    11698177    5  Extended
/dev/sdc5           59345       60802    11698176   82  Linux swap / Solaris


 
Could someone please help me on this?
 
Best Regards.

---

### Post by lejmer on 2010-09-22
> **morningsunshine said:**
> Hi all,
 
I have Windows XP dual boot with Ubuntu 8.10 on my system. I brought in a portable HDD on which I installed Ubuntu 10.04 32-bit. The grub boot loader was installed along with this and to boot windows, I've had to plug in the HDD (with lucid install) everytime. It had been working fine. Until few hours back when I decided to put Ubuntu 10.04 amd64 install on this portable HDD.
 
I chose the option - Erase complete drive and install Ubuntu10.04 - and install went alright. Now when the system restarted, it failed to boot up and I receive the grub rescue prompt.
 
I've tried to reinstall grub using references given in posts in this forum but it has not come up till now.



 
Could someone please help me on this?
 
Best Regards.

I have the same problem. I get the "file not found" error. Basically, all my screen says is:

error: file not found.
grub rescue>

I have Grub2 installed in the MGR of the same harddrive as Ubuntu (an external USB drive btw). I first installed Ubuntu through my girlfriends laptop (a Dell Inspiron 1525). It worked fine, without any problems. I could boot and do whatever I liked with the OS. (all I did was pretty much just install code blocks and programme for a while). I could reboot as much as I wanted as well. There were no problems at all (this was on the same USB hard drive that I mentioned above). Windows XP, which was already installed on the laptops internal drive also booted just fine.

My problem occured when I tried to boot from my own computer, a few days later (as I am sick of Windows, but need it to use Cubase, which is needed for work). This is where I got that Grub message. At first I thought "Wait, I have five drives when I include the externa USB hard drive, in my computer, and the USB hard drive is the fifth one. And when I installed it on the laptop, it was the second one, so maybe grub.cfg is just configured incorrectly, pointing to the wrong drive". So I booted from the live CD (I am using Ubuntu 10.4.1 LTS btw), and entered this in the terminal:

sudo mount /dev/sde1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sde

I double checked "grub.cfg" to see that it pointed to the correct drive - and it did - so I rebooted. But what did I see? The same freakin' message. It's still telling me that this mystery file is not found.

Then I though "Hmm, maybe it cannot find grub.cfg for some reason...". And this is still what I think is the actual problem, but I can not seem to find a solution for it. I don't actually understand why it doesn't find it. It points to the correct drive. I double checked with "set prefix". It outputs "(hd4,0)/boot/grub", which to me seems correct. I also checked with "set root", and it is set to "(hd4,0)", which is correct. At least it's the correct drive and partition (which is the fifth drive, and the first partition).

I have looked all over the internet and this forum for a solution. But nothing works. Any input on how to fix this?

Regards,
Anthony

---

