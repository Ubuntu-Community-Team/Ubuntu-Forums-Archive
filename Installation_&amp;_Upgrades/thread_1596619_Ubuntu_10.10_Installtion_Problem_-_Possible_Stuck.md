---
title: "Ubuntu 10.10 Installtion Problem - Possible Stuck?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by ruggerz on 2010-10-14
Just started installing Ubuntu 10.10 from disc onto a clean Toshiba Satellite.
 
All the first steps went ok, but now it seems to be stuck at
 
[INDENT]'Creating ext4 file system for / in partition #1 of SCSI1 (0,0,0) (sda)...'
 
[/INDENT]its been like his for over 30 minutes - often in expanded view it often says
 
[INDENT]'Oct 14 15:48:07 ubuntu NetworkManager[1906]: <info> (wlan0): supplicant connection state: gtoup handshake -> completed'
 
[/INDENT]its said this about 4 times but i havent noticed any progression on the status bar...
 
 
any ideas to fix or is this normal?
 
rugggerz

---

### Post by ronparent on 2010-10-14
Often this cryptic message appears because you went the manual partition route on step 4 of install and forgot to specify '/' as the mount point on your designated partition in step 5.

---

### Post by Aragant on 2010-10-14
Kindly help me..!!
I just updated my ubuntu 10.04 to 10.10 through update manager, there came an option to keep or remove of something i didn't read it
mentioned here [http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server)

on 12th screen-shot. And then after complete install when restarted i booted but it STUCK on ubuntu logon screen everytime...

i tried to skip the splash screen then loged-in successfully. As, i am new on ubuntu so i am unable to go into graphical desktop mode from there....

Can anyone HELP ME...??

---

### Post by vserbu on 2010-10-15
same thing here, stuck on ubuntu logo,  ATI X500. When I remove that ATI card and boot with motherboard built-in video adapter (VIA something) , ubuntu boots ok but can not get any better resolution than 800X600. I tried even with ATI X1650, but same thing happens. Even if I try to boot from CD. Help pls.

---

### Post by Hamishfox on 2010-10-15
[According to this thread]("http://ubuntuforums.org/showthread.php?t=1596901"), entering ```
startx
``` into the command prompt should give you a desktop.

[URL="http://ubuntuforums.org/showthread.php?t=1596901"]
[/URL]

---

### Post by vserbu on 2010-10-15
> **Hamishfox said:**
> [According to this thread]("http://ubuntuforums.org/showthread.php?t=1596901"), entering ```
startx
``` into the command prompt should give you a desktop.

[URL="http://ubuntuforums.org/showthread.php?t=1596901"]
[/URL]

I'm not getting command prompt, I just have Ubuntu logo and boot stucked there

---

### Post by Hamishfox on 2010-10-15
press escape when the logo first pops up and wait a bit - it should ask you for your username and password and then give you a command line. This booting from last good configuration or something, I think. I only found out about it yesterday ;p

edit: I was actually replying to aragant with that last post. I don't actually know what I'm doing, just what I've read in other threads.

---

