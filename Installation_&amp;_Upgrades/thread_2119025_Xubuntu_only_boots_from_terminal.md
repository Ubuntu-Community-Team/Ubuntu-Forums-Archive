---
title: "Xubuntu only boots from terminal"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by pegom on 2013-02-22
I have tried the Psychocats'  command,but after booting from bootloader with Ubuntu 12.04.2,the computer stops after checking the battery.I must launch a virtual terminal (Ctrl+Alt+F1,...,F6),login,and typing "startxfce4",I can start Xubuntu.I'd like boot whitout running the virtual terminal,but I don't know.

---

### Post by offgridguy on 2013-02-22
> **pegom said:**
> I have tried the Psychocats'  command,but after booting from bootloader with Ubuntu 12.04.2,the computer stops after checking the battery.I must launch a virtual terminal (Ctrl+Alt+F1,...,F6),login,and typing "startxfce4",I can start Xubuntu.I'd like boot whitout running the virtual terminal,but I don't know.
Hello and welcome to the forums.  I am not sure what you are wanting to do,
but I would suggest that you start your own new thread in this forum,  you
will probably get better results,  perhaps give some more detail about what
you want to do.):P

---

### Post by Bucky Ball on 2013-02-22
*Thread moved to **Installation & Upgrades**.*

Welcome to the forums. I have moved your post to its own thread with a title which I think describes your problem. Let me know if you want it changed or you can change it yourself within half an hour by editing the first post and then 'Go Advanced'.

Please refrain from hijacking other user's threads as it creates confusion, dilutes community effort, is unfair to the original poster and reduces your chances of getting help. Your issue wasn't the same as the original poster's and their problem and the thread title had nothing to do with your issue.

Good luck. ;)

---

### Post by MAFoElffen on 2013-02-22
> **pegom said:**
> I have tried the Psychocats'  command,but after booting from bootloader with Ubuntu 12.04.2,the computer stops after checking the battery.I must launch a virtual terminal (Ctrl+Alt+F1,...,F6),login,and typing "startxfce4",I can start Xubuntu.I'd like boot whitout running the virtual terminal,but I don't know.

Please post the results of 
```

lspci -vnn | grep VGA

```
Two indicators from what you said lean towards you needing to install a video driver for your hardware.

- Boots straight to a text session, without envoking Xinit.
- On the graphics layer load, it stops/hangs at the message "checking battery state."

It is not hanging there because of a battery issue, but rather with another process that occurs at the time.

At the time of that message, the XServer has already started and is running in background as another process. It is probing your video hardware and looking for appropriate video modes and/or drivers. Some video hardware drivers are not-opensource, so these proprietary drivers are not installed by default. If while trying modes, it cannot find something appropriate or tries a mode your hardware doesn't understand, it sometimes hangs... That would coincide with the timing of that message. 

So, yes, please post the results of that command and additionally attach your /var/log/Xorg.x.log file to the post, where "x" between the dots is 0 + 1 from current running (example: The Xorg.1.log file is one graphics session previous to the current Xorg.0.log session) so that the log you are sending is the one that had the hang error in it... Does that make sense to you?

---

### Post by pegom on 2013-02-23
Thanks for the answers.Maybe I didn't explain myself well the issue in my first post.The whole process has been:
1.Installation of Ubuntu 12.04.But my dual boot(with xp installed afterward) Dell netbook ran it slow,and the software updates were very,very slow.
2.Then I install the xubuntu-desktop package.Now,I can run uUbuntu and (if log out) Xubuntu,faster.
3.I decide remove Ubuntu  from a Ubuntu terminal using the Psychocats' command,reboot,and the Grub bootloader displays only Ubuntu and Windows xp,but not Xubuntu.
4.The result is my first post.The video drivers work when I start Xubuntu.

---

### Post by steeldriver on 2013-02-23
> **pegom said:**
> Thanks for the answers.Maybe I didn't explain myself well the issue in my first post.The whole process has been:
1.Installation of Ubuntu 12.04.But my dual boot(with xp installed afterward) Dell netbook ran it slow,and the software updates were very,very slow.
2.**[COLOR=Red]Then I install the ubuntu-desktop package.[/COLOR]**Now,I can run uUbuntu and (if log out) Xubuntu,faster.
3.I decide remove Ubuntu  from a Ubuntu terminal using the Psychocats' command,reboot,and the Grub bootloader displays only Ubuntu and Windows xp,but not Xubuntu.
4.The result is my first post.The video drivers work when I start Xubuntu.

Did you mean to say that you installed the **[COLOR=Red]x[/COLOR]**ubuntu-desktop package? if so it won't show as a separate grub menu entry, that would only happen if you made a separate install of a whole Xubuntu system (on a different partition).

If you then removed the regular ubuntu-desktop, you may have broken the lightdm display manager.

Let's see what these files say:

```
cat /etc/X11/default-display-manager

cat /etc/lightdm/lightdm.conf
```

---

### Post by pegom on 2013-02-23
> **steeldriver said:**
> Did you mean to say that you installed the **[COLOR=Red]x[/COLOR]**ubuntu-desktop package? if so it won't show as a separate grub menu entry, that would only happen if you made a separate install of a whole Xubuntu system (on a different partition).

If you then removed the regular ubuntu-desktop, you may have broken the lightdm display manager.

Let's see what these files say:

```
cat /etc/X11/default-display-manager

cat /etc/lightdm/lightdm.conf
```


These are the outputs:
# cat /mnt/sda2/etc/lightdm/lightdm.conf

[SeatDefaults]
autologin-guest=false
autologin-user=pl
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=xubuntu
greeter-session=unity-greeter
# cat /mnt/sda2/etc/X11/default-display-manager
/usr/sbin/lightdm

---

### Post by pegom on 2013-02-25
This is the output for MAFoElffen and the /var/log/Xorg.x.log file attached.

# lspci -vnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])

---

