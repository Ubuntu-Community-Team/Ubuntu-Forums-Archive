---
title: "Xubuntu installation issue"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by Rhino1 on 2006-09-11
I have been using Breezy for over a year now and really enjoy the setup, although it took me a long time to get it the way I wanted it.  

I recently burned ISO's of both Xubuntu and Edubuntu for work.  I teach and wanted something that would be good for classroom and faster on slow and older pc's.  I loaded both onto a HP pavilion without any issues and they work fine (dual-boot).  Xubuntu worked so nicely that I wanted to install it on my home computer,  oops!

I dual-boot with windows because I only have winmodems and can only use 14.4 kbps modem on Ubuntu.  I figured I would just perform a fresh install and set it up the way I wanted it.

Xubuntu hangs when I reach the xserver portion of the install, I repeated the process and it hangs everytime.  I tried the Edubuntu cd and got the same result.  I reloaded Breezy without issue and attempted to update from the Xubuntu cd through synaptic.  The update went fine, everything seemed all well and good until I rebooted... I got a failure on xserver, it was disabled and was only able to use a command line.

I've reloaded Breezy and will continue using that distro until I can determine what to do next, with someone's help?

What additional information do you need and where can I find it at?

---

### Post by jamesr on 2006-09-11
Hi,

I have the similar error (Failure to start X server). I know that my CD works because I used it to complete an install on a laptop. I used the live  CD and that crashed at the Xserver whereas the alternate install, did in fact, complete the installion but did not start the X Server. I had a similar error once before, so once I have found a solution I will post a more complete reply. 

If somebody knows the solution please post away.

---

### Post by jamesr on 2006-09-12
Hi,

The problem has been solved , by changing hardware. So the problem may not relate directly to your problem. The following are the steps that I followed

1) Check the version of xserver-xorg-core (problem mentioned on another thread re alternate CD Xubuntu)
```
sudo aptitude show xerser-xorg-core | grep Version
```

NB Version not version
Reply = version 1:1.0.2-0ubuntu10.4

2) Tried to get another version:-
```
sudo apt-get install xserver-xorg-code =1:1.0.2-0ubuntu10
```
Reply = already newest version.

3) Booted to recover mode ie no xserver

4) check config
```
dpkg --configure -a
```
5) Reconfigure xserver
```
dpkg -reconfigure xserver-xorg
```
messages about updating files

6) Reconfigure gdm
```
dpkg -reconfigure gdm
```

7) Reboot

same error 

8) looked at error log 
```
less /var/log/Xorg.0.log
```

At end of log
 no devices detected
Fatal server error
No screen form

9-12
Repeated 3 to 8 and configure manually. Reminded me of the bad old days of not automatically detecting the video.
Tried various combinations.

13-15
Repeated 3 to 8 and configure manually.The System is a Netserver LD Pro with built-in video Trident TVGA 9000i. Tried to force to use Trident driver no luck always seemed to give the same error.

16 Replace Video card with old matrox, disabled on board video (switch p8)
Repeated 3 to 8 and configure automatically. Identifed as mga and now works.

now to rest of the server working.

Thanks for the help in the forum in the form of previously posted replies, especially to TSelliot for his replies/postings.

Thanks a lot

---

