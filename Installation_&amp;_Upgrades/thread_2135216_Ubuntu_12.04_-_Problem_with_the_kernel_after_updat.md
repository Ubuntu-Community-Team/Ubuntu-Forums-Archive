---
title: "Ubuntu 12.04 - Problem with the kernel after update"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by StarterX4 on 2013-04-13
After today's kernel update and the other shows the error:
> **The system is running in low-graphics mode**

Your screen, graphic card, and input device settings could not be detectedd correctly.
You need to configure these yourself.

and under it have the "OK" when I click ok shows up:
> 
[LIST]
[*]Run in low-graphics mode for just one session 
[*]Reconfigure graphics 
[*]Troubleshoot error 
[*]Exit to console login 
[/LIST]

and I might add that if I choose anything from the list shows me only "out of range", I use the monitor LG Flatron W1934S.
First, I updated the kernel, a package xserver, and some have the name "kernel ..." and ran after updating your computer and normally nothing bad will happen, and immediately took to be updated VirtualBox and Wine, and an hour after the update I had to go to his cousin, and the computer turned off, but when it came, turn on the computer, and suddenly this error I might add that during my absence, one of the computer is not used.
Kernel was updated version of "linux-generic-pae 3.2.0.40" to "linux-generic-pae 3.2.0.41"... and was retrieved from the server: [COLOR=#400080]"ftp.icm.edu.pl"[/COLOR].

Please Help Me !!

(I'm Sorry if I wrote some mistakes, I am Polish, and I took the google translate, at my school, I just learned the German language.:P)

---

### Post by kafkaian on 2013-04-14
HAve you got the Sandybridge problem? [https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/1140716)

I'm having a similar issue on a friend's PC and annoyed that a perfect system has been screwed by a regressive update. The reason you get told to stick to LTS versions is that you shouldn't get this problem.

---

### Post by andrewkay on 2013-04-15
me too. I'm running xubuntu 12.04.

with 3.2.0-30 Kernel the login dialog screen shows up ok, but after typing my password the dialog closes leaving only the background, and apparently does nothing else.

with 3.2.0-29 it seems to work as normal.

I can't see any error messages.

---

