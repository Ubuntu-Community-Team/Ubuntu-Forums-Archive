---
title: "Installed manually and now need help tuning so it can run"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by bonixavier on 2011-06-19
Hello forums!

I see myself with an interesting problem and would like to get some help. I chose to install Lucid Lynx in a spare partition because I have a soft spot for Ubuntu, being the first distro I ever used. The thing is that my pendrive died and it's a netbook so I had to try to do things differently.

First, I mounted the .iso to a folder. Then I mounted the squashfs file and copied all of its contents to my spare partition. I copied my host's /etc/mtab to its /etc and created an fstab based on my host's (I know people have been using UUIDs, but it's just a blkid so it can wait). There it is:
```
/dev/sda6   swap   swap   defaults   0 0 
/dev/sda5   /   ext3   defaults   1 1
devpts   /dev/pts   devpts   gid=5,mode=620   0 0
proc   /proc   proc   defaults   0 0
tmpfs   /dev/shm   tmpfs   defaults   0 0
```Then I chrooted into it and installed grub to its root partition. I did a couple more things:

-I added a dummy user boni. I don't know what groups the first user should belong to, so I simply added me to users and sudo. Which ones should they be?
-I added Ubuntu's gpg key to the trusted keys and installed vim in order to check if apt-get was working. It works.

Then I rebooted. Ubuntu is booting, but there are a couple of things to be done. First, I get the following errors when gdm appears:
1. Could not update ICEauthority file /var/lib/gdm/.ICEauthority
2. There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check2 exited with status 256)
3. Loooong delay then the login screen appears. There's just the hostname (cardamom), but I can't pick a user to login.
4. At the same time, there's a notice on the top right corner of the screen: 
Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.

So I switched to TTY1 to try and kill gdm and try to reinstall it. The problem is that I can't use sudo. I get an error stating that it must be suid root. This one is easy to circumvent. All I have to do is chroot again and enable root logins.

I have a battery of problems so I'd like know what I can do to fix them or get some better reference to install Ubuntu manually. The IRC channel couldn't help me. I'm using Slackware 13.37 so suggestions to install additional software should take that in consideration.

Hope someone out there can help. Thanks for your time.

---

### Post by bonixavier on 2011-06-19
Nevermind. Found a [good reference]("https://help.ubuntu.com/community/Installation/FromLinux"). Don't know how I'd missed it before. Solved.

---

