---
title: "Fresh install..and a couple of problems"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by Toddney on 2005-06-26
1)  In Firefox..I can't get into the Preferences or bookmark a page...it comes up with this box and some red letters...I can't remember now i'm back in windows...

2)  I tried to have my windows NTFS partition automatically mounted on login..under /media/windows through the ubuntu guide..and i go into that folder and there is nothing there...do i have to restart or something?

---

### Post by Toddney on 2005-06-26
BTW..thank you guys so much for all your help, i'm surprised i've made it this far!

---

### Post by mingus on 2005-06-27
*In Firefox..I can't get into the Preferences or bookmark a page...it comes up with this box and some red letters...I can't remember now i'm back in windows...*

Hard to say without the error msg.  Check that you have the most current version, it's 1.04 and you should get is from the backports repository, package name firefox plus firefox-gnome-support. 


*I tried to have my windows NTFS partition automatically mounted on login..under /media/windows through the ubuntu guide..and i go into that folder and there is nothing there...do i have to restart or something?*

Post back your /etc/fstab file.  Also, reboot and immediately open a terminal and do:
$dmesg | more
scroll thru the file looking for where your partitions are getting mounted, look for a NTFS reference, see if there are any error messages, post those back

---

### Post by Toddney on 2005-06-27
Ok, well the Firefox and the Windows problem are gone..I just needed to restart the computer.  My only other problem is, I haven't heard any sound yet...so I don't think my sound works...also, I checked the device manager..and my processor type is unknown..and a lot of other stuff is unknown..is this normal?

---

### Post by Toddney on 2005-06-27
I've been going through some sound related howtos..and in one of them i'm supposed to install the applicaiton "libesd-alsa0"..well i type in sudo apt-get install libesd-alsa0 and it comes back saying 

Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate

any ideas??

---

### Post by Toddney on 2005-06-27
Apparently (through further readings) there is no libesd-alsa0 in the AMD64 repositories.  Hmm..now what to do?

---

### Post by mingus on 2005-06-27
[QUOTE=Toddney]Apparently (through further readings) there is no libesd-alsa0 in the AMD64 repositories.  Hmm..now what to do?[/QUOTE]

Suggest you post this prob separately to the AM64 forum . . .

---

### Post by mingus on 2005-06-27
[QUOTE=Toddney]I checked the device manager..and my processor type is unknown..and a lot of other stuff is unknown..is this normal?[/QUOTE]

Look under the Advanced tab . . . you will see the details there.  I have no idea why the Device tab frequently reports "unknown".

---

### Post by crispingatiesa on 2005-06-27
[QUOTE=Toddney]I've been going through some sound related howtos..and in one of them i'm supposed to install the applicaiton "libesd-alsa0"..well i type in sudo apt-get install libesd-alsa0 and it comes back saying 

Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate

any ideas??[/QUOTE]


There is a typo should be: libesd0-alsa

---

