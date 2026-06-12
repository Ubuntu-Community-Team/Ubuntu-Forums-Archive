---
title: "ATI Drivers: SystemError: installArchives() failed"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Shadow12313 on 2010-04-08
I am trying to get compiz to work on my friends computer but I need the correct ati drivers and when I try to install them it returns the error:  SystemError: installArchives() failed

Any ideas?
Thank-you in advance.

---

### Post by Shadow12313 on 2010-04-08
Bump*

---

### Post by Ahadiel on 2010-04-08
> **Shadow12313 said:**
> I am trying to get compiz to work on my friends computer but I need the correct ati drivers and when I try to install them it returns the error:  SystemError: installArchives() failed

Any ideas?
Thank-you in advance.

How are you trying to install them?

If you haven't already, try System -> Admin -> Hardware Drivers.

---

### Post by Shadow12313 on 2010-04-08
Tha's where I got the error in the first place.

---

### Post by Shadow12313 on 2010-04-08
Bump

---

### Post by clhsharky on 2010-04-08
HI


Whats the video chip you have?

```
lspci | grep VGA
```

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Sharky

---

### Post by Shadow12313 on 2010-04-08
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]

---

### Post by clhsharky on 2010-04-08
HI 

Is this on 9.10 or 10.04?

Sharky

---

### Post by Shadow12313 on 2010-04-08
10.04

---

### Post by clhsharky on 2010-04-08
HI again

10.04 should be posted in

Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

But anyways 10.04 should be giving you 3D out of the box. I do know 3100 didn't have HW acceleration like 3200 chip, was intended for low cost office computers.


look here post 162 on installing fglrx if the other way didn't work.
[http://ubuntuforums.org/showthread.php?t=1434064&page=17](http://ubuntuforums.org/showthread.php?t=1434064&page=17)


Sharky

---

### Post by Shadow12313 on 2010-04-08
Neither worked when I tried to install fglrx it failed.

---

### Post by Shadow12313 on 2010-04-08
Bump

---

### Post by cariboo on 2010-04-08
Please don't bump more than once every 24 hours.

---

### Post by emarkay on 2010-04-08
cariboo- OK, but he (and many others - including me) have ATI issues - literally in this case showstoppers - cut a bit o'slack - you can see this is a big problem for 40% of the Lucid users... Can't ya?  :) 

OP - sorry can't offer any ideas, and yea, maybe instead of "bump", add more info, what you have done between posts, ideas thunk of, Google searches, magic words that worked and maybe a legit "help meeeee!"  (OK I just saw  "The Fly"...)

---

### Post by splicerr on 2010-04-08
> **emarkay said:**
> cariboo- OK, but he (and many others - including me) have ATI issues - literally in this case showstoppers - cut a bit o'slack

I disagree, I find his bumping behavior unacceptable, it's really in the same category as  spamming. I think the moderator is very nice here. I would have closed the thread for sure.

---

### Post by Shadow12313 on 2010-04-12
This is getting off-topic, I just need some help with ATI drivers not an explanation of bumping rules.

And for the record it was my friend (the owner of the computer with this problem) who became impatient and decided to bump repeatedly.  Sorry if his "bumping behavior" somehow offended you splicerr.

---

### Post by BrokeMahPC on 2010-04-12
After going to System - Admin- Hardware drivers and enabling and installing the driver you need to do this:
```
sudo aticonfig --initial -f
```then
```
sudo reboot 
```
BTW all those with ugly low colour Plymouth please read this thread:
[http://ubuntuforums.org/showpost.php?p=8995529&postcount=7](http://ubuntuforums.org/showpost.php?p=8995529&postcount=7)
They are testing it in stages by the looks of things and it's not where it should be yet.

---

### Post by Shadow12313 on 2010-04-12
Thank-you I will try it as soon as I meet with him again.

---

### Post by Achiraaz on 2010-04-24
I have the same problem.

Message SystemError:installArchives() failed is displayed when I go to System -> Administration -> Hardware Drivers and attempt to activate ATI/AMD Proprietary FGLRX graphics driver.

I have tried to install fglrx through the synaptic package manager and the terminal but I get the error message: 
```
apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34,4MB of archives.
After this operation, 110MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 138166 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.723.1-0ubuntu3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am using Ubuntu 10.04 like Shadow12313 and:
```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
```

---

### Post by raz3r_ on 2010-04-24
Same problem here, Ubuntu 10.04 with a Mobility Radeon 5650 on a laptop Sony Vaio :( Same identical error and I don't know what to do...

---

### Post by lhaeh on 2010-04-24
I had the error "SystemError: installArchives() failed" come up as well, but in 9.10. Turns out I had forgot that Synaptic was running. Hope that points you in the right direction.

---

### Post by Shadow12313 on 2010-04-27
I would like to report that this problem has been corrected with a fresh installation of Ubuntu 10.04 Lucid Lynx.

---

### Post by Achiraaz on 2010-04-28
> **Shadow12313 said:**
> I would like to report that this problem has been corrected with a fresh installation of Ubuntu 10.04 Lucid Lynx.

I tried Updating through the Update Manager which I assume gets my system into the same state as yours. This however did not solve my problem.

There may be a difference - can anyone confirm/reject this?

---

### Post by williamdabastrd on 2010-04-28
I got that error the first several tries and just assumed that the server was busy. Tried again 20 mins later and it worked. I have a 5850. 
 
Hope I helped :D

---

### Post by Shadow12313 on 2010-04-28
> **Achiraaz said:**
> I tried Updating through the Update Manager which I assume gets my system into the same state as yours. This however did not solve my problem.

There may be a difference - can anyone confirm/reject this?

I don think updating to a new version is the same as a fresh install.

---

### Post by arloth on 2010-04-28
For now, just don't use the driver off of ATI's website - it's likely to break things, and afaik the one that 10.04 installs is fully functional.

As to your solution, I suggest searching the forums a bit more, inst_path_default and inst_path_override are dead giveaways. :) [http://ubuntuforums.org/showthread.php?t=1456282](http://ubuntuforums.org/showthread.php?t=1456282)

My card is happily functioning now.

---

### Post by Achiraaz on 2010-04-29
Performed a combination of Shadow and Arloth's advices:

I reinstalled 10.04 and followed the guide which there was a link to in Arloth's post:
> **clhsharky said:**
> HI


Lucid requires special fglrx driver

[http://ubuntuforums.org/showpost.php?p=9062521&postcount=158](http://ubuntuforums.org/showpost.php?p=9062521&postcount=158)



This section is for Lucid
Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Ubuntu Gets Another ATI Catalyst Driver Handout
[http://ubuntuforums.org/showthread.php?t=1434064](http://ubuntuforums.org/showthread.php?t=1434064)


Sharky

This got me to succesfully install fglrx.
I took a screenshot of the packages that FGLRX needs based on a fresh lucid lynx installation:
- dkms
- fakeroot
- fglrx-amdcccle
- lib32gcc1
- libaudio2
- libc6-i386
- libmng1
- libqtcore4
- libqtgui4
- patch

Whoever is stuck with the same problem I had and are not quite ready to reinstall yet should try to uninstall these packages (possibly with that apt-get purge command but I'm too much of a newbie to know the difference.)

Moving on to the reboot.

Edit: I think this solved my problem.

---

