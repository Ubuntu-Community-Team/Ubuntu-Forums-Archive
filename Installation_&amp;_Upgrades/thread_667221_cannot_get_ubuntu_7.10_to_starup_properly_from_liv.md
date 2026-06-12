---
title: "cannot get ubuntu 7.10 to starup properly from livecd"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by dreven on 2008-01-14
My system it a
Athlon 64 X2 5200
ASRock ALiveNF7G-HDready  with latest 2.10 bios update
NVIDIA GeForce 7050 PV / NVIDIA nForce 630a integrated
2x1gig G Skill F2-6400CL5-1GBNQ
WDC WD3200AAJS-00VWA0 320 gig sata 
LG LITE-ON DVDRW LH-20A1L sata burner

I am having problems getting ubuntu 7.10 64bit to startup properly.  It starts up fine initially
but when xwindows loads it comes up with an error saying my video card was not detected properly and it is running in safe graphics mode, when I hit continue it goes back to the black screen showing the initial hardware successes and hangs there no error messages no lockups it just hangs there and does nothing i've let it wait there for up to 10 minutes and nothing, when i hit ctrl alt delete it closes down fine with no apparent error messages.  I have tried the noapic nolapic string because i noticed some people were having problems with that not necessarily mine but I thought I would give it a try and still nothing.

I have also tried ubuntu 7.04 and when it tries to startup i get a weird xserver unknown graphics error with a bunch of weird ascii characters all around the error message which has the background of yellow.

I have seen that other people with this motherboard have not had the same problems any help would be highly appreciated.

---

### Post by PmDematagoda on 2008-01-14
I suggest you try the Alternate CD, the Alternate CD can be obtained from [here]("http://www.ubuntu.com/getubuntu/download"), just check the checkbox near the end of the page that will allow you to download the Alternate CD ISO.

In case you were wondering, the Alternate CD is the text-based installer for Ubuntu.

---

### Post by dreven on 2008-01-14
thanks for the advice but I got it to bootup finally.  I chose the acpi=off string for bootup as well as the start in safe graphics mode option.  I'm currently downloading the new driver or at least a driver for nvidia i got it through the appearance tab so we will see.  am I wasting my time doing this while still running off of the livecd? I would imagine I am.

---

### Post by PmDematagoda on 2008-01-14
Why are you trying to install the Nvidia driver while using the Live CD? You should first install Ubuntu and then install the applications and drivers you need.

---

### Post by Sef on 2008-01-14
> I'm currently downloading the new driver or at least a driver for nvidia i got it through the appearance tab so we will see. am I wasting my time doing this while still running off of the livecd?

Install the driver after Ubuntu is installed.  System > Administration > Restricted Drivers Management

---

### Post by dreven on 2008-01-14
I was not thinking, i'm now back in windows copying stuff to dvd so I can format and repartition my drive.   
While i'm here I have another question though, I am running the 64 bit version and when I was in I tried to play an mp3 and it wanted me to download ffmpeg I believe but then it told me it would not work under 64 bit, what am I to do to get mp3s and divx, xvid, wmv and such as well as dvd play back to work?

---

### Post by PmDematagoda on 2008-01-14
Post the results of:-
```
cat /etc/apt/sources.list
```

---

### Post by dreven on 2008-01-14
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
jesse@jesse-desktop:~$ 

I have to tell you this is absolutely wicked with the updated nvidia drivers and full effects
I pray to god I can get everything working like I want, because I hate windblows and never want to return to or from the darkside whichever you prefer.

---

### Post by PmDematagoda on 2008-01-14
Open Software Sources in System>Administration>Software Sources, enable all the repositories in the Ubuntu Software tab except for the CD-ROM. After that is done, close the window, you will be asked to reload the sources list, do that, after that is complete try installing the codecs again.

---

