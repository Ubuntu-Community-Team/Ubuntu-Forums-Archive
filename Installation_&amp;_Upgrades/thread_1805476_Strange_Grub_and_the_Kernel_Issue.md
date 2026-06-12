---
title: "Strange Grub and the Kernel Issue"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by dancewithpratik on 2011-07-16
Hello Friends,
    I am using Ubuntu 11.04. Once I had to install Virtual Box on my Laptop but I had a strange error while installing it. I realised that even after updating the kernel the grub was showing the old one's, hence uname -r also showed the old kernels. However the Virtual Box libraries were expecting the latest one's. After much try in vain I deleted the kernel in use. After restart grub reported an error. Then I went in editing the command( by pressing 'e' during Grub menu ) for locating the recent kernel and edited the command and thankfully I could login in my Ubuntu.
   But now I cant do Update or install any packages.
   Please Help to recover my problem.

---

### Post by dino99 on 2011-07-16
try:

sudo dpkg-reconfigure grub-pc
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dancewithpratik on 2011-07-16
Thanks for your concern,

I am getting an error for 

pratik@pratik-laptop:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for pratik: 
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed


What should I do?

---

