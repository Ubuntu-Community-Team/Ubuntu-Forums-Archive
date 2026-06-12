---
title: "Minimal Lubuntu install on old Hercules-Ecafe"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by linuxkvh on 2013-01-08
Hi,

I am trying to do a minimum Lubuntu install on an old  old Hercules-Ecafe running on an early Mandriva version. My guess is the machine is older than 2005.

installing the latest Puppy Linux failed, for it has a non PAE kernel (at least that's the message I read when attempting to install it)

Finally the Minimum Lubuntu 11.1 install seemed to work, but I was unable to connect to the Internet (tried Wlan) and proceed to the final install. It seems that the DHCP protocol cannot connect to my router?

Anyway, is there a way to do a Lubuntu (or other distro) install or is this machine somehow protected from new installs? Trying to update the original Mandriva didn't get me anywhere.

---

### Post by forkandles on 2013-01-08
These links may be of help to you:

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

Booting from a USB drive:
I had no joy with StartUp Disk Creator, so I used Unetbootin (second answer down): 

[http://askubuntu.com/questions/15429...rking-in-12-04](http://askubuntu.com/questions/15429...rking-in-12-04)

Before this, I formatted the USB drive:
[http://freshtutorial.com/format-pen-...-drives-linux/](http://freshtutorial.com/format-pen-...-drives-linux/)

The USB stick must also be mounted. 
In my case:


```
sudo mkdir /media/Corsair

sudo mount /dev/sdc1 /media/Corsair
```

In the BIOS set USB drive to boot first and you should be okay.

---

### Post by sudodus on 2013-01-08
Try to install

1. Lubuntu 12.04 with the alternate-i386.iso
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/")

2. Knoppix


3. DSL (Damn Small Linux)

---

### Post by mlentink on 2013-01-08
Just googled it, and it appears to have an AMD Geode LX800 CPU, which I know nothing about, but also 512MB RAM. That should be enough to run Lubuntu. I installed it last week on a Dell Inspiron 5100 (P4, 512 MB) and Lubuntu runs smoothly. 
But this one has an optical drive so installataion was easy.

---

### Post by linuxkvh on 2013-01-09
Thanks a lot for your help, guys. I will attempt to do the install following your steps. Once I can connect the machine to the internet, it should work smoothly.

---

### Post by sudodus on 2013-01-10
> **linuxkvh said:**
> Thanks a lot for your help, guys. I will attempt to do the install following your steps. Once I can connect the machine to the internet, it should work smoothly.
Good luck and welcome back to describe how you succeeded or to ask for more help :-)

---

