---
title: "No Xauthority file after upgrade 19.04 to 20.04"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by xiguus2 on 2020-05-10
My system is an ACER Aspire 3.

I have upgraded my 19.04 installation to 20.04. Boot stops with a system prompt. I can Ctrl-Alt-F3 to a terminal and log in.
* The installation initially seems to have stalled before completion and left me with a login screen which looped when I entered the password. I googled for explanation and found out that this can be caused by a missing Xauthority file. I opened tty and logged in, and found that there was, indeed, no Xauthority file in /home/user. I ran **uname -r** and found that OS was 5.0.0.38
* I booted to tty and ran update/upgrade again. Various errors came through which prevented the upgrade from completing. I addressed these from the terminal and eventually got a successful upgrade, ie uname -r now reports 5.4.0.29.
* Behaviour is now as above, with a system prompt at boot, no login screen, and access to the system through tty.
Can someone advise how I can generate an Xauthority file for 20.04?

Additionally, I am getting a  lot of messages "PCIe Bus Error...". These seem to be affecting/interrupting command execution, imposes a 12-sec timeout. Offending device (**lspci -nn**) is Raven2 GPP Bridge. I understand that these messages can be suppressed by supplying a kernel boot parameter, which I will do when I have my OS back again.

Many Thanks & Best Regards,
xiguus

---

### Post by Impavidus on 2020-05-10
Fixing a release upgrade gone wrong is rarely worth the effort. You tried to upgrade from 19.04 (which reached end of life 4 months ago) to 20.04, skipping 19.10. This release upgrade was never tested or supported, so don't be surprised if things don't work as intended. Numbers like 5.0.0-38 and 5.4.0-29 are kernel versions, not OS versions. The kernel is part of the OS, but there's more. 5.0 was the kernel belonging to 19.04, 5.4 belongs to 20.04, so that's right, but you can't tell from that that the upgrade was complete.

Don't worry about the .Xauthority file. The problem is when the file is there, but has the wrong ownership or permissions, as frequently happens after sudo abuse. If not present at all, it's created automatically on login – if needed. The Linux community is trying to move away from X.

The quick and clean solution is a fresh install. I'm not saying this can't be fixed otherwise, but it will take longer.

---

### Post by rbmorse on 2020-05-10
Also make sure you do not enable the login automatically option when you set up your user.

---

### Post by xiguus2 on 2020-05-11
Hi guys, thx for this.
Would still like to know why I can't get a login screen and why system is not generating an Xauthority as it should.
Background to the situation (mbe boring -- sorry) is I am travelling and could not do upgrade in a timely manner because my downloads were limited. When I ran the upgrade I was taken directly to 20.04. No alternative option was provided. I then got messages that the upgrade could not be completed because there was no focal security file/repository. I found a 'solution' which said to **sed **sources.list disco -> focal, which I did, and after various whatsits got to here.
I am looking through my log files and have errors in Xorg.0.log and Xorg.1.log:
       open /dev/dri/card0: no such file or directory
       Screen 0 deleted because of no matching config section
I'm assuming my problem is not a display issue *per se* but if there is a problem with X.. it must start somewhere. Also, I don't know why I have two display configs.
Waiting for your advice,
BR,
xiguus

---

### Post by rbmorse on 2020-05-11
Your system isn't generating an .Xauthority file in /home/*username *for 20.04 because the default display manager, gdm3, doesn't use it.  

If you really need one you can switch to lightdm.  Use the console to:

sudo systemctl stop gdm3 
sudo dpkg-reconfigure gdm3 (select lightdm then <tab> to "OK")
configure lightdm as prompted
sudo systemctl start lightdm.  

Log out of the console.  If that doesn't take you to a graphical login screen <ctrl><alt><F2> (or some other function key...they seem to change from time to time) should start the GUI.

---

### Post by xiguus2 on 2020-05-12
Returning to the substantive issue, which is that boot takes me to a login loop, I did some searching and checking and decided that verifying the completeness of the upgrade was a useful prelude to digging (a lot) deeper:
```

sudo apt update
sudo apt-get -y dist-upgrade
sudo apt-get -y autoremove
sudo apt-get -y clean
reboot

```

Result is a working login screen and a fully functional system...

All is not entirely well, however -- 'update-grub' has blitzed my Manjaro partitions because they have two arguments for their initrd line and the grub scripts in Ubuntu will only write one. I think I've run into this problem before so there's a solution somewhere. In the meantime I will just edit the line at boot time.

Accordingly, I'm marking this as "Solved" (if I can figure out how to do it)

BR,
xiguus

---

