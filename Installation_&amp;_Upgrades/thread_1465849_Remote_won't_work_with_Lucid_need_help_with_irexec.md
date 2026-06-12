---
title: "Remote won't work with Lucid need help with irexec"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by linux.is.skynet on 2010-04-29
I tried using this post to get my soundcard to work: 

[http://art.ubuntuforums.org/showthread.php?p=2476075](http://art.ubuntuforums.org/showthread.php?p=2476075)

I get the following error when trying to run irexec :


justin@rEd:~$ sudo irexec 
irexec: could not open config files /home/justin/.lircrc and /etc/lirc//lirc/lircrc
irexec: No such file or directory

What I have is a Toshiba Multimedia Center sound card, which is really an Creative Labs Sound Blaster Live! External via usb. I know the sound card's IR port is showing up in Ubuntu by getting response when I run "irw" in a terminal. Here's what I get when I press button on the remote: 

justin@rEd:~$ irw
0000000000000084 00 up Creative_SBL
0000000000000078 00 left Creative_SBL
000000000000008a 00 right Creative_SBL
000000000000007e 00 ok Creative_SBL
000000000000007c 00 touche8 Creative_SBL
000000000000007b 00 touche5 Creative_SBL
0000000000000070 00 touche2 Creative_SBL
0000000000000074 00 touche1 Creative_SBL

Anybody know how to fix the error with "irexec"
? I've tried to make a .lircrc file in my home directory  but I don't know what to put in it. I tried putting the code from this site starting with "begin remote" and stopped with "end remote" in the code. I've also tried using all of the code... I dunno... ANY ideas?

---

### Post by linux.is.skynet on 2010-04-29
I've got it to work by modifying the file of .lircrc . Now I get this:


justin@rEd:~$ sudo irexec 
irexec: unknown token "touche1<0x74>touche1" in /home/justin/.lircrc:5 ignored
irexec: unknown token "touche2" in /home/justin/.lircrc:6 ignored
irexec: unknown token "touche3" in /home/justin/.lircrc:7 ignored
irexec: unknown token "touche4" in /home/justin/.lircrc:8 ignored
irexec: unknown token "touche5" in /home/justin/.lircrc:9 ignored
irexec: unknown token "touche6" in /home/justin/.lircrc:10 ignored
irexec: unknown token "touche7" in /home/justin/.lircrc:11 ignored
irexec: unknown token "touche8" in /home/justin/.lircrc:12 ignored
irexec: unknown token "touche9" in /home/justin/.lircrc:13 ignored
irexec: unknown token "touche0" in /home/justin/.lircrc:14 ignored
irexec: unknown token "CMSS" in /home/justin/.lircrc:15 ignored
irexec: unknown token "EAX" in /home/justin/.lircrc:16 ignored
irexec: unknown token "vol-" in /home/justin/.lircrc:17 ignored
irexec: unknown token "vol+" in /home/justin/.lircrc:18 ignored
irexec: unknown token "up" in /home/justin/.lircrc:19 ignored
irexec: unknown token "down" in /home/justin/.lircrc:20 ignored
irexec: unknown token "left" in /home/justin/.lircrc:21 ignored
irexec: unknown token "right" in /home/justin/.lircrc:22 ignored
irexec: unknown token "ok" in /home/justin/.lircrc:23 ignored
irexec: unknown token "return" in /home/justin/.lircrc:24 ignored
irexec: unknown token "start" in /home/justin/.lircrc:25 ignored
irexec: unknown token "cancel" in /home/justin/.lircrc:26 ignored
irexec: unknown token "record" in /home/justin/.lircrc:27 ignored
irexec: unknown token "options" in /home/justin/.lircrc:28 ignored
irexec: unknown token "display" in /home/justin/.lircrc:29 ignored
irexec: unknown token "previous" in /home/justin/.lircrc:30 ignored
irexec: unknown token "playpause" in /home/justin/.lircrc:31 ignored
irexec: unknown token "next" in /home/justin/.lircrc:32 ignored
irexec: unknown token "slow" in /home/justin/.lircrc:33 ignored
irexec: unknown token "stop" in /home/justin/.lircrc:34 ignored
irexec: unknown token "step" in /home/justin/.lircrc:35 ignored

which tells me that it's running, but the code format is off....

---

### Post by linux.is.skynet on 2010-04-29
Bump .. need help

---

