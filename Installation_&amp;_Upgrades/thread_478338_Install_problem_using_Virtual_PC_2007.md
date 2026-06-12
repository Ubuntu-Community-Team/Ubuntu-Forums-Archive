---
title: "Install problem using Virtual PC 2007"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by ArcticLemon on 2007-06-19
Hello,

Having a frustrating problem when trying to instal ubuntu on a virtual machine in Microsoft Virtual PC 2007.  I get the inistial install menu but when I select install, the installation starts but then crashes with a coloured liney, unreadable screen.

Any help would be appreciated.

Ta....

---

### Post by thelinuxguy on 2007-06-19
The video depth needs to be changed to 16. Take a look here: [https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)

---

### Post by nathanaa on 2007-07-24
I installed Ubuntu 7 on VPC 2007 and when I boot I get a blank screen. I tried the instructions on that link ([https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)) but it didn't work.

When I type: dpkg-reconfigure xserver-xorg. I get a message that says:
Package 'xserver-xorg' is not installed and no info is available. ... /usr/sbin/dpkg-reconfigure: xserver-xorg is not installed.

So I tried: "cd /ect/X11" and then "pico xorg.xonf", which just brings me to a blank editor. I exit and type "ls" to see if the file is there and all it says is "xkb" in blue.

What do I do?

Thanks,
Nathan

---

### Post by thelinuxguy on 2007-07-25
I can't say for sure but it looks like X is not installed properly (or not installed at all) because when I do an ls in /etc/X11, I get a lot of entries which includes xorg.conf.
So 
1) You may try installing X on what you already have (I can't be of much help here since I haven't done it myself). 
But this could help
```

sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal

```
(Look at topcop's response at this thread: [http://ubuntuforums.org/archive/index.php/t-86076.html](http://ubuntuforums.org/archive/index.php/t-86076.html))

2) Reinstall, making sure that X is installed this time. And check that you are installing the desktop version and not the server version instead.

Hope this helps.

---

### Post by nathanaa on 2007-07-27
Oh, ok. I installed the server version, I didn't realize that it doesn't come with a desktop. I will try installing it manually. I want to install a LAMP server (for the first time) so I assume installing the server and then installing the desktop manually is the right move.

Thanks,
Nathan

---

### Post by thelinuxguy on 2007-07-27
> **nathanaa said:**
> I want to install a LAMP server

Let me know how your LAMP server comes about. I mean any issues and how u solved them. I had trouble lately getting php and MySQL to work on my Edgy desktop and am thinking of doing the same. 
Off topic for this thread. So maybe you could make that post in a thread that deals with LAMP. But do let me know.

Thanks.

---

