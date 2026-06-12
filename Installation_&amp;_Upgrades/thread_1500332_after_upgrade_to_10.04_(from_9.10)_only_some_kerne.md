---
title: "after upgrade to 10.04 (from 9.10) only some kernels boot"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by sathya288 on 2010-06-03
friends

I use ubuntu for almost 3 yrs. I had installed 8.04 on my Acer TravelMate 5720 laptop.
I have been upgrading to newer releases and eventually reached 10.04 last week.

In the grub, I see quite a few kernels listed. The first few are (I've omitted the recovery stuff)

 linux-image-2.6.32-22-generic-pae              2.6.32-22.33
  linux-image-2.6.32-22-generic                  2.6.32-22.33
  linux-image-2.6.31-21-generic-pae              2.6.31-21.59
  linux-image-2.6.31-21-generic                  2.6.31-21.59
  linux-image-2.6.31-20-generic-pae              2.6.31-20.58
  linux-image-2.6.31-20-generic                  2.6.31-20.58
  linux-image-2.6.28-18-server                   2.6.28-18.60
  linux-image-2.6.28-18-generic                  2.6.28-18.60
  linux-image-2.6.28-17-server                   2.6.28-17.58
  linux-image-2.6.28-17-generic                  2.6.28-17.58
  linux-image-2.6.28-16-server                   2.6.28-16.57

But not every one of them boot. Since I have 4GB of RAM I am interested in "pae" enabled kernels. But when I choose them, the grub reboots.

After some trial and error I found that ONLY **2.6.31-21-generic** works. But it does not make use of 4GB RAM.

I tried deleting files in /boot/grub that end with *1_5, as somewhere I read this would fix the grub reboot issue. But that dint help. Grub reboots only for certain kernels.

I desperately need to get pae work as I am running virtualbox with guests OSes (windows & Suse). Any pointers would be of great help.

-sathya

---

### Post by dino99 on 2010-06-03
pae kernels work fine

have you removed everything about grub-legacy and menu.lst ?

As grub2 (grub-pc and grub-common) cant work well if it find old settings from grub-legacy, you need to remove/purge (right click) ALL the grub packages installed and menu.lst, then install grub-pc and grub-common (when asked, install grub on your ubuntu partition)

into synaptic you can remove/purge all the kernels you dont want/need, then:

sudo grub-mkconfig
sudo update-grub

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by sathya288 on 2010-06-03
Thanks dino99

1. I found that I am running grub-legacy (version 0.97). So I installed grub2 (version 1.98)
2. Then I made grub 2 as my default. Removed all menu.lst stuff.
3. When I tried with a pae, it did not reboot. But did not book either. It stopped in with Kernel_thread_xxx kind of message.
4. Through synaptic, I removed unwanted old kernels. I re-installed 2.6.32.21-generic-pae.
5. In the grub menu I chose the pae that I re-installed. It worked !
    It utilizes the entire 4 GB (3.8GiB).

Thanks a lot.

---

