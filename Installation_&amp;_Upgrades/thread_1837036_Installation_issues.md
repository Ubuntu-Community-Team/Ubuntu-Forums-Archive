---
title: "Installation issues"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by dragngt on 2011-09-01
So I spent a few days playing with the AMD64-bit Ubuntu 11.04 install.  I was having no success with Flash working and staying in sync properly (video & audio), esp with 720p or 1080p.  Nothing at all showed up in Chrome either (flash based).  The idea is for this to be my HTPC.  YouTube, Netflix, MKV files etc... all in HD when available.

AMD Phenom x4 and 880G MSI mobo with ATI Radeon HD 4250

So my old roommate was attempting to help me.  He's a bit Ubuntu fan and swore my issues were related to my 64bit install and I needed to switch to 32bit.  I made a bootable thumb drive for the 32bit and erased and installed it.  After install I do my package updates and restart.... all's good.  I then get the ATI graphics FGLRX driver notification.  I had this installed on the 64bit and it worked fine and was the only way to fix the overscanning on the HDTV.  So I installed it...  When it asks to reboot to apply the update the computer will not boot.  I am stuck at the splash screen and my fans max out and just sit and spin until I reach over and turn them off myself after how ever long you wanna wait.  Reinstalled this all 3 more times, same results.  If I cut the computer back on after all that I get the Grub menu and it still won't boot.  I just get a dark purple screen of death.

What am I doing wrong?  Is it the 32bit install isn't supposed to be on what I'm using?

Also, if I go back to what worked (64 bit) how do I get the things that don't work... to well... work?

Thank you for your help!

---

### Post by 98cwitr on 2011-09-01
Old room-mate checking in...

To clarify, we did download the recommended flash install and ran these instructions:

[http://www.liberiangeek.net/2011/08/install-adobe-flash-player-11-64-bit-in-ubuntu-11-0411-10/](http://www.liberiangeek.net/2011/08/install-adobe-flash-player-11-64-bit-in-ubuntu-11-0411-10/)

Unfortunately, this works in Firefox and not Chrome, so the issue seemed to be isolated. Knowing that my flash works great (but I'm on 10.10 x86), it was worth a try to see if the 32-bit version of flash worked. 

That said, we made a USB bootable for the 32-bit distro and that's where I left him with it last night.

Dude, if you're having this much issue with the 32-bit version, let's put the 64 back on since we know it works (mostly) and just add the 64-bit source to the repository. I think with that initial, half-assed install we did might have not applied with chrome.

Let's get flash installed BEFORE Chrome gets installed, and go from there.

Any other thoughts from the board?

---

### Post by dragngt on 2011-09-01
Well now the fun will be getting a bootable 64bit USB.  The Ubuntu install page doesn't recommend making one on a Mac.  And my last attempt failed.

Before I ditch the 32bit install entirely what about installing the Open Source ATI driver I read about?  Do the guys in here think I should give that a shot before ditching a 32bit install?

32bit should work on my hardware correct?  Just checking considering what's happening...

Am I getting any weird left over script or funky things with my erase and reinstall of the OS this many times?  I ask that because Grub had the safe mode on there to boot to and "previous linux installs."  I thought that was interesting.

Also, does Ubuntu tend to behave this way when you install one little thing it doesn't like?  That's not building my trust in it's ease of use and stability...

---

### Post by 98cwitr on 2011-09-01
You still have the 64-bit CD don't you? Just use it, we'll do the Live USB later....

if you can't access the 32-bit OS and still want to, select recovery mode in grub, gain root access, and do the following:
[http://askubuntu.com/questions/33092/how-well-do-ati-drivers-work-with-unity](http://askubuntu.com/questions/33092/how-well-do-ati-drivers-work-with-unity)

---

### Post by dragngt on 2011-09-01
No dvd drive... because I'll never ever use it.

---

### Post by 98cwitr on 2011-09-01
> **dragngt said:**
> No dvd drive... because I'll never ever use it.

you used it to install it the first time....

---

### Post by dragngt on 2011-09-01
This looks more like a chit chat between the two of us.  I need some help or perspective from everyone else so let's get back to the whole drive screwing up my beautiful install.

Anyone with an idea, post up!  Thanks!

---

### Post by dragngt on 2011-09-01
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

heath@heath-MS-7576:~$ sudo apt-get install xserver-xorg-video-ati
[sudo] password for heath: 
Sorry, try again.
[sudo] password for heath: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
The following package was automatically installed and is no longer required:
  linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
heath@heath-MS-7576:~$ apt get autoremove
The program 'apt' is currently not installed.  You can install it by typing:
sudo apt-get install openjdk-6-jdk
heath@heath-MS-7576:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
heath@heath-MS-7576:~$ 

```

---

### Post by 98cwitr on 2011-09-01
you have to run sudo dude :/

```
sudo apt-get autoremove
```

you also can concatenate commands like so:

```
sudo apt-get install xserver-xorg-video-ati && sudo apt-get autoremove
```

---

### Post by dragngt on 2011-09-01
```
heath@heath-MS-7576:~$ sudo apt-get autoremove
[sudo] password for heath: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.38-8
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 85.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145842 files and directories currently installed.)
Removing linux-headers-2.6.38-8 ...
heath@heath-MS-7576:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
heath@heath-MS-7576:~$ 

```

---

### Post by dragngt on 2011-11-12
Follow up to things.  There doesn't seem to be any proper drivers for the ATI graphics cards.  Ubuntu still doesn't work properly where flash is concerned.  The 64bit install is the best one for the hardware I'm running.

In the mean time I got a $30 copy of Windows 7 Pro 64bit (direct from MS) and everything works perfect for my video playback.  I'm disappointed with Ubuntu but I understand it's a free service that will still suffer from this kind of support for many more years.  Personally I wouldn't work on anything I didn't get paid for either so I find no fault in that.

I'll continue to tinker with Ubuntu, but sadly it's still not a complete and supported system.  I'm fine with that... but it also means it's only useful as a secondary OS for me at least.

---

