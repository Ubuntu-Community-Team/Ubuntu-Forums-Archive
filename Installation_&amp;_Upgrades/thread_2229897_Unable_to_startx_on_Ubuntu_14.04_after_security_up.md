---
title: "Unable to startx on Ubuntu 14.04 after security update - missing libXfont.so.1"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by ethomsen86 on 2014-06-15
I had Ubuntu 14.04 running perfectly on my system and then it underwent a recommended security update. I let it update while I was at work and when I returned I found a black screen stating, "No init found" and "mount: mounting /dev/mapper/ubuntu-root on /root failed: Invalid argument". I followed some guides and ran the following commands:

```
ls /dev/sd*
sudo apt-get install lvm2
sudo pvscan
sudo vgscan
sudo vgchange -a y ubuntu-vg
sudo fsck /dev/ubuntu-vg/root

```

After running those commands and rebooting, my Linux system was back up and running again; however, not quite like it was before. It starts up into command line mode (without GUI) and asks for my username and password. When I log in and try "startx" I get the following:


```
user@home-pc:~$ startx
xauth:  timeout in locking authority file /home/user/.Xauthority
xauth:  timeout in locking authority file /home/user/.Xauthority


/usr/bin/X: error while loading shared libraries: libXfont.so.1: cannot open shared object file: No such file or directory
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth:  timeout in locking authority file /home/user/.Xauthority
user@home-pc:~$ 

```

I get the same message when I try "sudo startx". I believe this error is due to the symbolic link that is used to identify the "libXfont.so.1" file, but I don't know how to fix this problem. I already tried running "sudo apt-get update && sudo-apt-get dist-upgrade" in hopes that this would fix or finish the upgrade and/or installing of the security update, but this didn't fix the problem. Does anyone have any idea on what is going on or how I can fix this?

---

### Post by Ben_Cunningham on 2014-06-15
Hope you had a backup. You may be able to type do-release-upgrade to upgrade to a later version of Ubuntu and in theory it will replace that file. I am definitely by NO means a Linux expert, in fact I was only introduced to Linux about a year ago so I am a total noob. I just figured that if you 'updated' to a newer version of Ubuntu it would replace that file in the process. The other thing you could do was a full reinstall of Ubuntu, thats why you NEED a backup! You might also be able to use a Live CD to 'repair' Ubuntu. Of course you would need to get your hands on a Live CD to do that though.

Anyways,
Hope I helped!

---

### Post by ethomsen86 on 2014-06-16
No I didn't have a backup. Is this sort of failure common when installing Linux/Ubuntu security updates? Anyway, my system is working fine except for the GUI. I have an active internet connection and everything. Isn't there a way to just completely uninstall the xorg/GUI and reinstall in order to eliminate this problem?

---

### Post by Ben_Cunningham on 2014-06-18
I just had a great idea. You can use tar in terminal to backup your data, then you can get a Live CD reinstall Linux and then restore from your backup. There are lots of tutorials about using tar in the Terminal so you should be able to figure it out.

Hope I helped,
Ben Cunningham

---

