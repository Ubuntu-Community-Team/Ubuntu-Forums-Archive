---
title: "remove linux mint 8 dual booted with ubuntu 9.10"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by sidkapoor on 2010-03-06
hi,
this is my first post. i am a beginner to linux. i searched around and found ubuntu and linux mint were the most popular distros for linux. i decided i will dual boot them and give them both a try. i have decided to stick with ubuntu and want to remove linux mint and reclaim the empty space left to ubuntu. can someone help me on how to go about doing this. i have no idea so layman's terms would be much appreciated. thanks a lot

---

### Post by hatalar205 on 2010-03-06
First learn how to "**re**install Grub2" again. And later you can do it by using gparted it on Live Cd. But your Ubuntu partition must be before the Mint partition on the disk order. Otherwise it can cause you lots of problems.

---

### Post by oldfred on 2010-03-06
You also need to know which system is in the MBR. That is usually the last install so it is the one in control. I would boot into Ubuntu and reinstall grub or grub2 depending on your version and make sure your can then boot from Ubuntu's grub. Then you can look into repartitioning.
You may want to make the existing linux mint a data partition by just reformating it rather than deleting and recombining it.

If you have a new install of Karmic and can boot into it then do this:
reinstall from working system - first find Ubuntu drive, you may see two ext3 or ext4 drives but you have to know which is which: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

Using gparted on partitions, they must be umounted so you usually have to do it from a liveCD.
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

