---
title: "Upgrading from 7.10 to 8.10?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by RKBA on 2008-11-22
Hi Folks,

I'm running Ubuntu 7.10 and have downloaded the regular installation CD for 8.10, but there doesn't seem to be a way to upgrade without wiping out everything that's there (ie; a complete reinstall). I just started downloading the Ubuntu 8.10 Alternate installation CD in hopes that will work, but am not sure even that will allow me to skip directly from 7.10 to 8.10 and bypass 8.04 altogether if possible, because I understand it has many flaws (display problems, etc., and it won't run properly from CD on my system). 

Does anyone know if I can go directly from 7.10 to 8.10 without a complete reinstall (and if so,how?), or must I upgrade to 8.04 before I can upgrade to 7.10?

Thanks,

Ron

---

### Post by tommcd on 2008-11-22
> **RKBA said:**
> Hi Folks,
Does anyone know if I can go directly from 7.10 to 8.10 without a complete reinstall (and if so,how?), or must I upgrade to 8.04 before I can upgrade to 7.10?


Skipping versions when doing a dist-upgrade is not recommended. To upgrade from 7.10 --> 8.10 you should do it in sequence. That is, upgrade first to 8.04, then upgrade to 8.10. Or just do a clean install of 8.10, which will be faster, easier, better, and less likely to cause problems.

---

### Post by RKBA on 2008-11-23
Hmmm, I thought I'd already replied to tommcd before I started the upgrade and to say thanks, but maybe I forgot to hit the submit button. In any case, here is what transpired:

I upgraded from 7.10 to 8.04 uneventfully, except of course for a few minor things like having Ubuntu delete a few of my old applications and change my background wallpaper, but when I went to use the alternate installation cd to upgrade from 8.04 to 8.10 the installation got about halfway through and aborted with an error message that the CD was unreadable and provided a little advice about cleaning the read/write head, burning the CD at a lower speed, etc. Before I had started the install I'd run the "Media Check" on the installation CDROM so I "knew" (or thought I did) that it was Ok.

I then took the regular "Desktop" version of the Ubuntu 8.10 installation CD and began a fresh installation, but only reformatting the system partition and leaving my /home partition intact as is. The installation got about halfway through and aborted with an error message that the CD was unreadable and provided a little advice about cleaning the read/write head, burning the CD at a lower speed, etc. Keep in mind that this is a *different* CDROM than the alternate install CD I'd used earlier. 

At this point I wasn't sure what to think. I'd not only verified both CD's when I created them from the downloaded ISO's, but had run the boot-up "Media Check" feature which said the CD's were fine prior to using them for installation. 

What finally worked surprised me, and it takes a lot to surprise me. I dual booted into Windows2000 (which was fortunately still working even though the Ubuntu partition wasn't), and downloaded a fresh "Desktop" i386 install CD directly from the official Ubuntu download site instead of getting it via bittorrent as I normally do. Then I used the Windows "ImageBurn" freeware program to burn the new ISO at **1X Speed**. What happened next is what surprised me.

I popped the newly burned ISO into the CDROM tray, rebooted and installed Ubuntu 8.10 without incident.

What's astounding is that apparently having burned the installation CD's at maximum speed actually *did* affect their useability during the installation even though they passed the boot-up self-test "Media Check" that's selected from the menu shown after booting the CD. It's the first time I ever had that sort of problem from a CDROM (apparently).

After some fumbling around I was able to import my old Thunderbird email and settings into the newly installed 8.10 Thunderbird (same version number I think), as well as my old Firefox 2 bookmarks into Firefox 3, and restored some date and personal stuff. 

Basically I'm a happy camper now, and the only nuisance I've encountered is that everytime I reboot I get a pop-up message that precedes everything else and requires clicking Ok, which says something to the effect that a file called "$HOME/.dmrc" is not writeable (as I recall, but it was a long message), and that I should chown the file to me and chmod it to 644. No such file existed, so I created one with permissions as directed. It didn't do any good because the message keeps popping up and halting the boot process. I've already started looking around for a solution (unsuccessfully), but thought I would mention my experience with the CDROM during installation here before I forgot about it.

Best wishes to all and thanks for your help.

---

### Post by tommcd on 2008-11-23
> **RKBA said:**
> 
Basically I'm a happy camper now, and the only nuisance I've encountered is that everytime I reboot I get a pop-up message that precedes everything else and requires clicking Ok, which says something to the effect that a file called "$HOME/.dmrc" is not writeable (as I recall, but it was a long message), and that I should chown the file to me and chmod it to 644. No such file existed, so I created one with permissions as directed. It didn't do any good because the message keeps popping up and halting the boot process. I've already started looking around for a solution.

I have ~/.dmrc on my system. The contents of the file are:
```
[Desktop]
Session=default
```
The permissions are:
```
tom@ubuntu:~$ ls -l /home/tom/.dmrc
-rw------- 1 tom tom 2008-11-23 04:38 /hoem/tom.dmrc
```
Check that against your .dmrc. Also, see this thread:
[http://www.linuxquestions.org/questions/ubuntu-63/cant-log-in-users-home.dmrc-file-is-being-ignored....-478089/](http://www.linuxquestions.org/questions/ubuntu-63/cant-log-in-users-home.dmrc-file-is-being-ignored....-478089/)

---

### Post by RKBA on 2008-11-23
tommcd, if you are ever in the Los Angeles area I would be honored to buy you a free lunch (beverage of your choice included) anywhere you like,... except in Beverly Hills where I couldn't afford the cost of free valet parking, ha, ha! Seriously though I would like to make a small donation of $20 or so either to this forum or to a charity of your choice because of the trouble you have saved me from hunting around the Internet for a solution to not just one, but **two** different problems. Just adding the:

[Desktop]
Session=default

to my .drmc solved the problem and now I can reboot seamlessly. I should probably start hanging out here more often to try to be aware of these types of problems before they happen to me, and possibly even to help other relative newbies if I can. Best wishes and thank you.

Note: I do not have a Paypal account and cannot get one because I've exceeded the maximum $10,000 lifetime spending limit cap they impose unless you're willing to give them a banking account number, which I am not since they're crooks. Credit card is the easiest form of donation/payment for me.

---

