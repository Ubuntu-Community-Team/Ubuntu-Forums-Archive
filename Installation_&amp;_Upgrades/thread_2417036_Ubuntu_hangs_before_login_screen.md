---
title: "Ubuntu hangs before login screen"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by evandrorcc on 2019-04-19
Hi everyone.
I'm having some issues with Ubuntu boot, more precisely before login screen, it's seems that gdm stop working or something. It's weird because the Ubuntu plymouth is set to lower resolution and a few seconds during the animation the screen goes black and changes to the screen where all modules are starting. It's probably related with nvidia drivers or something, since I own a GTX 1060. Can someone help me fix this problem so I can enjoy Disco Dingo too?


**System Specs**
RAM: 8Gb
CPU: Intel i7 4770.
GPU: NVIDIA 1060.
Motherboard: Gigabyte B85M-D3PH

---

### Post by Bashing-om on 2019-04-19
evandrorcc; Hello - Welcome to the forum.

I accept that it is a graphic's driver issue. How about installing the proprietary driver for the NVIDIA 1060 card ?

At the login screen activate a terminal - key combo ctl+alt+F2 - log into the system with user name and password - there will be no response to the screen when password is entered, just enter the PW blindly and hit the enter key.

Once you are logged in execute terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
the use of "sudo" elevates your privileges to admin and the password will again have to be employed for the 1st instance of the commands. That access authority will time out by default in 5 minutes.

Reboot the system and tell now what results.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by evandrorcc on 2019-04-19
Hi, thanks for replying. I did this before and didn't worked. 
Something I forgot to mention was about the installation process, there, Ubuntu plymouth loads with my normal resolution, and everything works fine. The problem happens only after installation and reboot, when before login screen (during plymouth animation) the system hangs and the start checklist appears, and even there, you can do CTRL+ALT+F2 and it was the moment that I did what you said, still didn't worked.

---

### Post by evandrorcc on 2019-04-19
Another thing I've noticed was, before booting into **Installation Process. **I've saw this message, but as I said, this part wasn't the problem. But I don't know if this can be the reason for current problem, or why it happens during installation.

```

[COLOR=#242729][FONT=Consolas]Couldn't get size: 0x800000000000000e
[/FONT][/COLOR]MODSIGN: Couldn't get UEFI db list
Couldn't get size: 0x800000000000000e
```

---

