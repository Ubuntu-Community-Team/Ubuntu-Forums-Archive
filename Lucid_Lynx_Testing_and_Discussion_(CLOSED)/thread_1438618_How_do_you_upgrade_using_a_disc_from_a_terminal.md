---
title: "How do you upgrade using a disc from a terminal?"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zosolm on 2010-03-25
I have installed Lucid and found that there is a problem with Nvidia/Xorg (i don't really understand), so that I get no desktop and just a terminal. ([http://ubuntuforums.org/showthread.php?t=1436966](http://ubuntuforums.org/showthread.php?t=1436966) here's the thread in case you know how to fix it)

I've read about people doing a fresh install from a CD having no problems with Nvidia. 

I want to know if there's a way you can upgrade Lucid from a terminal with a CD -- WITHOUT doing a fresh install and losing all your files?

Thanks.

---

### Post by dino99 on 2010-03-25
into console:

sudo gedit /etc/apt/sources.list

be sure that all repo are with lucid
remove or comment all extra repo (ie ppa or non ubuntu repo) if you have
remove xorg.conf  ( /etc/X11/xorg.conf)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f


sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings
sudo apt-get install nvidia-current

sudo apt-get upgrade

then reboot
then go to system -- admin -- hardware driver, you should see nvidia-current activated (dont worry if it says not in use, its a bug with no importance)

---

### Post by zosolm on 2010-03-29
It won't connect when I use sudo apt-get update.
I noticed this before, which was why I was wondering if there's a way to use the disc
I was connected fine when I had everything running before.
I use wireless and ndiswrapper shows hardware present and driver installed 
:S
thank you
please help :(

---

### Post by cariboo on 2010-03-29
If you are at a command prompt, type:

```
sudo dhclient <interface>
```

Where <interface> is your networking device eg: eth0, wlan0.

---

### Post by psyke83 on 2010-03-29
> **cariboo907 said:**
> If you are at a command prompt, type:

```
sudo dhclient <interface>
```Where <interface> is your networking device eg: eth0, wlan0.

That won't work, because the wireless password is not available until the NetworkManager applet is launched. The OP needed to configure NetworkManager to "allow all users" access to the wireless network (which is not the default behaviour).

---

### Post by QwUo173Hy on 2010-03-29
OP, I don't know how to update from the command-line, but I think what you want to do is download an ISO of a daily snapshot, which has a newer version of the package you're interested, and make it the only uncommented entry on your sources list.

Then perform the update command from the console (which hopefully someone will provide). This should make you up to date.

---

### Post by zosolm on 2010-03-30
This sounds good. how do I alter my sources list?
it says it can't display the file.
:(

---

### Post by ranch hand on 2010-03-30
If you are running from the live CD you will need to use nautilus as super user (sudo nautilus).  You have to be the super user to edit that file anyway.

If it will not display your files then you have some very strange and large problems, either with the CD or your installation.

I would try another Live CD.  9.10 would be a good choice.  If that doesn't display your files then I wouldn't have a clue as to the next step except a clean install.  Hopefully there is a way to avoid that.

As to updating I would check your /etc/resolv.conf tile.  Mine has;
> 
nameserver 10.0.0.2

in it.  You need something similar.

I got this script from phillinux during the last testing round.  It does use labeled partitions so you would need to label your / (root) partition.
```
 #!/bin/sh

sudo mkdir /mnt/Lounge-root
sudo mount /dev/sda7 /mnt/Lounge-root/
sudo mount -o bind /proc /mnt/Lounge-root/proc
sudo mount -o bind /dev /mnt/Lounge-root/dev
sudo mount -o bind /dev/pts /mnt/Lounge-root/dev/pts
sudo mount -o bind /sys /mnt/Lounge-root/sys
sudo cp /etc/resolv.conf /mnt/Lounge-root/etc/resolv.conf
sudo chroot /mnt/Lounge-root /bin/bash

fi

```
This will need the label edited (Lounge-root) for your box and the partition edited too (sda7).

If you want you can copy/paste the individual commands, in that order, to terminal and use it that way.  I would save it to the desktop or somewhere on your installation so that you can get it if needed in the future from a Live environment.

---

