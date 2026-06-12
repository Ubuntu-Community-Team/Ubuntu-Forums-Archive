---
title: "Please Help: Minimal Install Woes"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by kestal on 2008-11-16
So I wanted to experience what it was to install from the 8.10 minimal CD. I connected my laptop to my router and off I went. It was installing things as the packages were chosen and things went pretty smoothly. It said that the base installation was complete so I restarted my computer.

Upon entering back in, it asked for the basics, username/password, I did that. I am sitting at the text prompt. I try to do a sudo apt-get update, and I see countless error messages saying that I failed to fetch it from the server. I try to see if I could just sudo apt-get install xorg (and aptitude install xorg) but those failed.

Whats next? How can I check to see if my laptop is even connecting anymore? (I used a wired connection - as my wireless is broadcom 4306 and it doesn't work out of the box in a normal install). What should my next steps be?

---

### Post by Partyboi2 on 2008-11-17
Have you checked your /etc/apt/sources.list to make sure that the repo's are uncommented?
```
sudo nano /etc/apt/sources.list
```example:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20081001)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
```

---

### Post by kestal on 2008-11-20
hmm. mine is all there. How would I check to see if my eth1 is active? is ifconfig on a minimal install?

If its not active (it worked during the initial installation of the minimal cd, I was definitely connected and downloading), how would I activate it? (it my ethernet cable IS plugged in).

---

### Post by ddnev45 on 2008-12-03
> **kestal said:**
> 
Whats next? How can I check to see if my laptop is even connecting anymore? (I used a wired connection - as my wireless is broadcom 4306 and it doesn't work out of the box in a normal install). What should my next steps be?

See if you can ping a site.

```
ping www.<some site>.com
```

I usually check a news site or google. If the packets aren't lost, you're connecting to the internet; use Ctl-c to stop pinging.

---

### Post by coskierken on 2008-12-03
When you get to the point of wanting the Broadcom wireless to work, let me know.  I just got one to work on an older HP laptop.  They can be frustrating!

Does your network icon (on the panel) tell you are connected?

---

### Post by Swanbot on 2008-12-03
> **coskierken said:**
> When you get to the point of wanting the Broadcom wireless to work, let me know.  I just got one to work on an older HP laptop.  They can be frustrating!

Does your network icon (on the panel) tell you are connected?

I can't get Broadcom to work, or even activate let me know if you have any advice.

---

### Post by coskierken on 2008-12-04
Lets see your network hardware first.

lshw -C network

post the results back so we can see what broadcom it actually is and which driver it is loading.  Also, look in the system/admin/hardware drivers and see what, if any Linux is trying to load.

---

