---
title: "debootstrap, problem with installing grub-pc"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by cbrands on 2010-07-05
I am in the process of creating an install script. The idea is that the script will be non-interactive. 

The instructions that I am following are from [https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD]("https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD")


The partitions sda1, sdb1, sdc1, sdd1 are going to be used in a raid 5 array.
sde is de boot disk with partitions
sde1 /boot
sde2 swap
sde3 /
sde4 /home

The problem starts with 
apt-get install grub-pc
Then I a get a bunch of screens with the title "configuring grub-pc". This is undesired as the script is non-interactive.

question. is it possible to install grub-pc without getting the configuration screens

---

### Post by leblancdw on 2010-12-16
I know it's been a while since this post, but I've just been searching for the same thing and found something that works for me,  so I figured I'd share with the forum:

Set the environment DEBIAN_FRONTEND to "noninteractive"; ie

**export DEBIAN_FRONTEND=noninteractive**

And voila - no more prompts!

---

