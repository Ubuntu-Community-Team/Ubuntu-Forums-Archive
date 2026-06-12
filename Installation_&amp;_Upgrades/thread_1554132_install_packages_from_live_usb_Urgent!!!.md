---
title: "install packages from live usb Urgent!!!"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by duke.tim on 2010-08-16
okay so I was having trouble with pulse audio and completely obliterated pulse audio from my machine in order to prepare for a reinstall of pulse audio. this also uninstalled a few other packages that I needed to enter gnome....or kde..... so when I try to login via gdm(?) my password will not authenticate (when I enter via xterm or tty the password is accepted). to solve this I need to know

#1 how can install packages off a live usb drive from Terminal
or
#2 learn how to access a wifi network under terminal to use apt-get

any help would be great

i'm at school right now so It's kinda important :(

---

### Post by duke.tim on 2010-08-16
I guess that means adding the live usb as a repository to some program like synaptic on xterm
or telling where I could find packages and use dpkg

---

### Post by Lrpbpb on 2010-11-30
Bump. 
I have a similar problem, I had the infamous kernel problem in 10.10 (the one where everything installs fine but dpkg returns an error when configuring the kernel), so I erased the kernel I hopes I could reinstall it problem free. It gave me same problem so I rebooted....now it doesn't boot Ubuntu.
I know that doesn't help, but hopefully it will be noticed....
BTW.. maybe the above was unnecessary....have you already solved this problem??

---

### Post by Lrpbpb on 2010-11-30
I found what might be the answer here:[http://www.tecnoupdate.com.ar/2010/10/30/como-restaurar-grub-con-un-live-cd-de-linux/](http://www.tecnoupdate.com.ar/2010/10/30/como-restaurar-grub-con-un-live-cd-de-linux/) (for those who can read spanish)

Its actually a guide on how to reinstall grub from a live usb, but I'm pretty sure the commands they give can be the answer:
Mount your linux partition somewhere (for simplicity's sake, lets just say that your partition is /dev/sda1 and you mounted it on /tmp/part)
Mount it by:
```
sudo mount /dev/sda1 /tmp/part 
```The site then says to install grub by:
```
sudo grub-install —root-directory=/tmp/part /dev/sda.
```I assume we can just substitute grub-install with apt-get (or whatever command):
```
sudo apt-get install "x" —root-directory=/tmp/part /dev/sda.
```Where "x" is whatever you want to install.
Hope this works.

---

### Post by Lrpbpb on 2010-11-30
Also, can anybody who knows how to do the above (install packages from a live usb to a hd install) post if what is the way of doing it.

---

