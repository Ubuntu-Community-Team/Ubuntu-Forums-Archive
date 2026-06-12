---
title: "[ubuntu 10.04.1 lts server] raid 1 fakeraid isw boot grub problem"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by cberni on 2010-09-29
Hi,
I have a Intel fakeraid and would like do install ubuntu 10.04.1 lts server using raid 1 (2x250gb sata).

First I was trying to install the version 10.04 (not 10.04.1) and the problem was when creating the partitions (the partitions could not be created and red screen).

Then, I saw the new release 10.04.1 and I tried to install again. The fakeraid partitions was created fine BUT when the installation is finish (all seems good) and the system is rebooted, nothing is started. After reboot nothing is initiate, no grub, nothing, just stay fixed in a black screen.

Someone could help me please?

---

### Post by ronparent on 2010-09-29
You probably had a grub install 'fatal error'. If that was it, it is fixable. See this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2s

Follow the instruction for installing except: be sure to reference the raid  drive you installed to as the root (ie /dev/mapper/<Your RaidTargetPartition#>) and the raid itself as the location to install the grub boot loader to (ie /dev/mapper/<Your RaidDrive>), not sda6 or sda. If you are still unsure, post the results of 'ls /dev/mapper'.

Although there are other possible cause, this seems most likely because most user are unaware of having to designate the boot loader position in step 8 of 8 of the install.

---

### Post by cberni on 2010-09-30
I think I got it.
I'll try it tomorrow and post news. Thanks.

ls /dev/mapper
./
../
control
isw_deihjjjhji_inovati
isw_deihjjjhji_inovati1 (system)
isw_deihjjjhji_inovati5 (swap)

---

### Post by cberni on 2010-10-01
I have spent a lot of hours with this problem and I'll post the solution I found.
The link that ronparent posted helped a lot.

- After the installation of Ubuntu 10.04.1 lts **server **was finished I booted with Ubuntu 10.04.1 **desktop **and chose to try it.
- I opened the terminal and I typed:

sudo mount /dev/mapper/isw_deihjjjhji_inovati1 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
**sudo upgrade-from-grub-legacy**

- Then I followed the steps and rebooted the system.
- Done! Works like a charm :)

---

### Post by ronparent on 2010-10-01
Glad to hear it is working for you. Have fun.

---

### Post by leoadias on 2010-12-30
> **cberni said:**
> I have spent a lot of hours with this problem and I'll post the solution I found.
The link that ronparent posted helped a lot.

- After the installation of Ubuntu 10.04.1 lts **server **was finished I booted with Ubuntu 10.04.1 **desktop **and chose to try it.
- I opened the terminal and I typed:

sudo mount /dev/mapper/isw_deihjjjhji_inovati1 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
**sudo upgrade-from-grub-legacy**

- Then I followed the steps and rebooted the system.
- Done! Works like a charm :)

Hi, I still have the same problem.

I have Ubuntu 10.10 Desktop installed on a Intel fake raid 1. The installation process worked fine. During the installation, I choosed /dev/sda to install boot (wrong choice!)

After read this post, I did this:

- booted again with Ubuntu 10.10 Desktop live cd
- opened a terminal and typed:

mount /dev/maper/isw_asdlfhjh_sistem1 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
chroot /mnt
grub-install /dev/maper/isw_asdlfhjh_sistem1
update-grub

- Then I reboot the system but nothing is initiate. Just a black screen.

Do I realy have to install grub on fake raid drive? There is another way?

tks

---

