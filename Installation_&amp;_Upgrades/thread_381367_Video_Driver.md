---
title: "Video Driver?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by krenshau on 2007-03-10
Hello,

This is my first time using Ubuntu. I installed Ubunto on my machine, and when it first ran, the screen resolution was fine, 1024x768 is what it looked like. Then, it said it had to reboot, so it did, but then when it came back up the screen resolution was set to 640x480. So I found out how to get to the form to change the resolution, but when I try to change it, 640x480 is the only option available. I thought that maybe the driver for the integrated video was wrong, or generic, but I can't seem to locate any information that can help me resolve this issue. Can anyone show me where I can go to find this information, or tell me how to resolve this?

Thank you for your help.

Ben

---

### Post by chewearn on 2007-03-11
What is the integrated video type: nvidia, ati or other?  If you give the exact part number e.g. GeForce6100, then someone in the forum might know how to help.

---

### Post by krenshau on 2007-03-11
Thank you for your reply.

Sorry, it is a D845GLLY motherboard with Intel® 82845GL Graphics.

Thank you for your help.

Ben

---

### Post by krenshau on 2007-03-14
I found a download that is supposed to fix the problem by installing the driver, and I tried to follow the instructions as best I could, being new to Linux, but it didn't solve the problem.

Is there anything else I can try, or do I just need to use a Microsoft OS license?

Thank you for your help.

---

### Post by chewearn on 2007-03-14
Ok, I'm not familiar with your Intel graphics card; but after some research and googling, I could give you a few steps to try.  My main source of info comes from this thread:
[http://www.ubuntuforums.org/showthread.php?t=292336&highlight=82845G+driver](http://www.ubuntuforums.org/showthread.php?t=292336&highlight=82845G+driver)

1. Change your video shared memory to max via the BIOS

2. In ubuntu, open a terminal, type in this line:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
In the password prompt, use your user's password.
You will be asked two questions in the text-based menus:
  Q1. about video driver, select i810.
  Q2. about resolution, select the resolutions you want, by "spacebar" over them
After the menu exits, take note of the message about the xorg.conf backup file.  If you need to undo later on, just restore the backup.

3. In the terminal again:
```
sudo /etc/init.d/gdm restart
```This will restart your GUI, and hopefully, comes back with the resolution you have specified.

---

### Post by krenshau on 2007-03-19
Sorry, I didn't get back to you sooner. I booted up a coupld of days ago and the resolution was fine, but then I started up today, and it was low resolution again. Not sure what that was all about.

I followed your instructions, except for the bios thing, at first. When I first tried it the screen went blank, and didn't come back. Then, I changed the bios setting to 8MB, the max, and when I restarted I even got the boot up screen, which I didn't usually get. Everything seems to work fine, now.

Thank you very much for your help. 

This is all new to me; can you recommend any reading that could get me the basic of how all this works? Again, thank you for your help.

---

### Post by chewearn on 2007-03-20
Most of what I know came from this forum itself, the ubuntu documentations and websites of forum members.
I frequently come into the forum and read the various problems people are having, the solutions given by other members as well as try searching for the solution myself.  By working thru my own problems, and trying to help others find a solution, I found myself learning a lot along the way.

Occasionally, we got links to very useful websites from members.  I don't have a list of these websites on hand right now (some are bookmarks in my browser at home, I will post them later).

Oh, and glad to be of help.  Hope you enjoy using ubuntu.

---

### Post by chewearn on 2007-03-21
Here is one:
[http://ubuntuforums.org/showthread.php?t=302475](http://ubuntuforums.org/showthread.php?t=302475)

---

### Post by Palko on 2007-03-21
This is also my first time using Ubuntu, that I am most excited, and what I need is to change my resolution to 1440x900 for my wide screen but the Preferences Screen Resolution doesn't seem to give me that option, How do I, please, change it or is there a nvidia driver I could download, 

Thank you.

Pal'ko

---

### Post by chewearn on 2007-03-21
> **Palko said:**
> This is also my first time using Ubuntu, that I am most excited, and what I need is to change my resolution to 1440x900 for my wide screen but the Preferences Screen Resolution doesn't seem to give me that option, How do I, please, change it or is there a nvidia driver I could download, 


Hi, first welcome to the community.  Some things to get out of the way before we get down to your problem:
1. In the future, please create a new thread, so it is obvious to other forum members that it is a new request; you will get more viewings and faster/better help.
2. Please include the ubuntu version you are using and the video hardware your have, so the replies will be more specific to your need


Ok,there are two version nvidia graphics cards driver: regular(new), and legacy.  Here is a list of the legacy:
[http://ubuntuforums.org/showthread.php?t=233241](http://ubuntuforums.org/showthread.php?t=233241)

To install the stable nvidia driver in the repositories:
System > Administration > Software Sources
Make sure "multiverse" and "restricted" are checked, then close the window.

Open a terminal, copy/paste this line:
```
sudo aptitude update && sudo aptitude upgrade
```Next, if you have legacy card:
```
sudo aptitude install nvidia-glx-legacy
```If you have regular card:
```
sudo aptitude install nvidia-glx
```Next, to enable the driver:
```
sudo nvidia-glx-config enable
```Finally, you need to restart Gnome:
```
sudo /etc/init.d/gdm restart
```If all is well, you should get back to the Gnome GUI login.

---

