---
title: "Upgrade from 16.04 to 17 - no input from keyboard or mouse"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2017-11-01
Today I ran the upgrade to the stable new version of xubuntu, after checking at each question, I allowed the package system to do it's stuff as changes found did not affect me.

The upgrade completed apparently correcctly and when asked if I wanted to remove the obselete packages, I selected 'yes' and the system rebooted.

The login screen was identical to the screen before the upgrade and I entered my password. At this point I noticed that no entry was being made. I also found that the mouse was unresponsive. None of the keyboard keys worked and the only way to proceed was to shut down the machine and restart it into the dual booted windows I am using to write this post.

After a reboot, the normal grub selections are offered so grub appears to be working. I tried recovery mode and made some checks but the results were beyond my knowledge.

My /home is on a separate partition so I suppose I could reinstall the previous version but I would like to fix this latest version if possible as I will probably face the same difficulties later.

I have a live USB instance of the previous xubuntu and have used chroot in the past with guidance but have never had a keyboard/mouse problem so not sure where to start.

Is there any assistance available?

---

### Post by #&amp;thj^% on 2017-11-01
See if this is installed?
```
apt policy xserver-xorg-input-all
```

---

### Post by makem2 on 2017-11-01
> **1fallen said:**
> See if this is installed?
```
apt policy xserver-xorg-input-all
```

Thank you,

As no keyboard I assume via the live USB. In that case, if I find it is not, install it?

---

### Post by #&amp;thj^% on 2017-11-01
Yes I would... this has been plaguing some users upgrading since 16.10 through 17.10.
maybe this is a bit more helpful: [https://askubuntu.com/questions/908918/updated-from-16-04-to-16-10-the-keyboard-and-mouse-no-longer-works-after-gettin](https://askubuntu.com/questions/908918/updated-from-16-04-to-16-10-the-keyboard-and-mouse-no-longer-works-after-gettin)

---

### Post by makem2 on 2017-11-01
From memory I believe thes are the commands to enter to installed version:

```

sudo mount /dev/sda2 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc

sudo chroot /mnt


```

sda2 is where my / is placed.

I just realised after that I am not sure where to look for the file xserver-xorg-input-all

If it is not where it should be am I right I can use apt-get to install it?

> **1fallen said:**
> Yes I would... this has been plaguing some users upgrading since 16.10 through 17.10.
maybe this is a bit more helpful: [https://askubuntu.com/questions/908918/updated-from-16-04-to-16-10-the-keyboard-and-mouse-no-longer-works-after-gettin](https://askubuntu.com/questions/908918/updated-from-16-04-to-16-10-the-keyboard-and-mouse-no-longer-works-after-gettin)

Thank you for that edit. However, I went along this route before I posted and it failed at the "Network". I forget what the error was but the script just hung and I had to reboot.

If I were to chroot into the existing system, would there be any problem in re-installing the packages 'xserver-xorg-input-all' even if they already exist?

I went ahead after research and re-installed xserver-xorg-input-all. Now I am able to log in and the mouse works too.

However all is not well, yet!

Network is constantly trying to connect and being disconnected, so no Internet

I get an error message on log-in, "A program error has been detected, do you want to report it" No details of the cause.

I think I could mark this thread as 'Solved' because I am now able to log in and use my mouse which was the reason for the post.

I thank you for your assistance and will make another request for assistance under 'Networking' if I cannot see an answer already. Hopefully that may resolve the program error message.

---

### Post by #&amp;thj^% on 2017-11-01
Great! Glad that solved the keyboard and mouse issue.
We have some of the best Networking Folks there are. Good Luck. :D

---

