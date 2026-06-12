---
title: "Installed 'ubuntu-desktop' on Feisty Server - but no GDM !!"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by kwilliam on 2007-04-26
I ran a straightforward Feisty 7.04 Server install, and selected both DNS and LAMP stacks to be installed.  Everything seemed to work fine - within 20 minutes I was at a good old login prompt.  The first two commands I entered after logging in were: 'sudo apt-get update'   and   'sudo apt-get install ubuntu-desktop'.   When it finally finished and I rebooted, all I get was a blank screen on tty7.  I switched to tty1, logged in and ran 'gdm', but it said that GDM was already running.  I killed gdm and started it again as root, but same problem: all I get is a blank black screen!  Ironically, USplash works fine.

I need to get the graphical interface working, because I'm setting this up for a Windows user who wants a simple way to administer his LAMP server. (Plus, I might try installing Myth TV on it at some point.)  But until I can actually start Gnome, I'm stuck.

Anyone else have this problem, or have any clue how to fix it?

---

### Post by zvacet on 2007-04-26
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by az on 2007-04-26
Perhaps it's the server kernel.  It is known to not use some desktop hardware properly.  Just install the desktop kernel.

Boot into recovery mode and run

apt-get install linux-generic
and then reboot.

---

### Post by kwilliam on 2007-04-27
> **az said:**
> Perhaps it's the server kernel.  It is known to not use some desktop hardware properly.  Just install the desktop kernel.

Boot into recovery mode and run

apt-get install linux-generic
and then reboot.

**Thanks!  That worked**.  (The psychocats stuff didn't.) Gnome starts now.  What's different about  the server kernel that made it do that?

---

### Post by az on 2007-04-27
The server kernel is optimized to different functions than the desktop one. The base timing of the kernel is slower (100 Hz instread of 1KHz) which is better suited to server tasks rather than desktop tasks.

I can no longer find the link which details the differences, but more than one person on these forums has had problems with simple things like mice when running the server kernel on a desktop system.

---

### Post by Green-e on 2007-04-28
I had the same problem, so I tried the same fix. But I still got the black screen. The funny thing is it seemed like it was running. It did the Ubuntu progress bar. I though I'd enter my username and password, and the funny thing is after a few seconds it made this funny sound, which I assumed was the start up (this is my first ubuntu experience, and i've never used the desktop before only the server). Unfortunately the screen is still black. So is there something I can do to fix the resolution, or something ?!?

I could re-install from the server CD, but I don't want to have to go through the process of doing another apt-get update. 

or....

I have another partition, is there a way to copy the apt-get cache/update data to the other partition, re-install the server and then copy the update data back to the boot partition.

any help would be much appreciated

---

### Post by kwilliam on 2007-04-29
> **Green-e said:**
>  I though I'd enter my username and password, and the funny thing is after a few seconds it made this funny sound, which I assumed was the start up.

Hehe, well if you got the the part where you log in and it plays sound, you are doing better than I was.  I still don't get a start-up sound.  I'll have to check and see if my sound works at all.  Maybe the server edition doesn't have a startup sound...

Sorry I can't help Green-e - (I'm still pretty new too) - but I'm sure somebody can.

---

