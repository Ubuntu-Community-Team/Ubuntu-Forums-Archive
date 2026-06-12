---
title: "Nasty login loop in Ubuntu 19.04"
date: 2019-05-18
forum: Installation &amp; Upgrades
---

### Post by tevang2 on 2019-05-18
I had that nasty login loop after installing some updates on Ubuntu 19.04 and couldn't solve it by changing permissions of my .Xauthority or /tmp. So I reinstalled 19.04 using a flash disk, did apt uptgrade and installed the right nvidia drivers, but still encounter the same problem. Please some one troubleshoot me! I am writing from my mobile...

---

### Post by dino99 on 2019-05-19
Googling around 'ubuntu nvidia login loop' will list some threads, like that one:
[https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers](https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers)

---

### Post by tevang2 on 2019-05-19
> **dino99 said:**
> Googling around 'ubuntu nvidia login loop' will list some threads, like that one:
[https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers](https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers)

What makes you think I haven't googled?? Btw, the solution with lightdm is obsolete and very dangerous in Ubuntu 19.04! It has been replaced by gdm3. I tried it yesterday and broke down the system, I wasn't even able to switch to text mode with ctrl+alt+F2!!
Anyway, after the fresh install I selected at the login prompt to login to "Ubuntu on Wayland" instead of the default option "Ubuntu" and that worked!

---

### Post by hgkrug1 on 2019-05-23
There are many reports of this happening when you try to install nvidia drivers. Also when you just do "sudo ubuntu-drivers autoinstall"

I have not found a sloution yet, but I have found 2 solutions to restore the Ubuntu Desktop environment (see #17 at [https://ubuntuforums.org/showthread.php?t=2411777&page=2):](https://ubuntuforums.org/showthread.php?t=2411777&page=2):)

First by Fossfreedom at - [https://discourse.ubuntubudgie.org/t...k-screen/97/14]("https://discourse.ubuntubudgie.org/t/nvidia-390-black-screen/97/14")

You have to do a safe boot and go to root, then:
sudo apt-get remove nvidia-*
sudo apt install nvidia-prime
sudo prime-select intel

Then reboot.

Second form sgian entry #3 at [https://ubuntuforums.org/showthread.php?t=2399985](https://ubuntuforums.org/showthread.php?t=2399985)

Also do a safe boot and go to root. Then:

sudo apt purge nvidia*
sudo apt install --reinstall xorg xserver-xorg-core

Tnen reboot.

---

### Post by hgkrug1 on 2019-05-23
I finally found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

