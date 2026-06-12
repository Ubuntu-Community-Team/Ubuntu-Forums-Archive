---
title: "My broken install experience (and fixes)"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by bj0 on 2008-10-31
So I have been using hardy for a month or so, and I didn't want to format and reinstall from scratch so I decided to try the upgrade (over the inet).  It sounded simple enough so I started it.  The upgrade dialog seemed pretty strait forward, so I let it run while I went off to school.  When I got back It had gone through 'cleanup' and wanted to restart.  I acquiesced and the next thing I know I'm staring at tty1 log in prompt.

Apparently either the network device went down or something weird happened during the upgrade process and it removed a bunch of my old packages without installing any new packages, which left a very broken system (no X and no ethernet device).

Instead of giving up and installing from scratch, of course, I had to try and fix it.  After a few hours of browsing forums and punching in random commands I realized I actually still had an eth0 device, it just wasn't being activated, but I could still bring it up with:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```
That was the first step in the right direction.  With a now-working internet connection, I could use aptitude (aparently setting up the sources.list was one of the things the upgrade DID accomplish).  So I was able to 
```
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade
```
Now I tried the full before the safe, but a rebellious package was causing it to stop early, so I did the safe, which worked.  Then I got the full to work after removing said package (amarok)
```
sudo aptitude remove amarok
```
These upgrades took a few hours, and when they were done I rebooted and... nothing changed.  Apparently even though it installed many a package, It didn't install all the necessary packages that would normally come with a fresh install (or maybe it didn't install all their dependencies?).  So I threw a few more commands that seemed like they should get X working:
```
sudo aptitude install xorg xserver-xorg
```
After this, I was able to load up X with startx, but instead of seeing a login screen, I saw a brown background with single terminal window.  Anyone who's tried to set up vncserver has probably seen this (with gray instead of brown).  Anyway, I figured it had to do with gdm, so I tossed a 
```
sudo dpkg-reconfigure gdm
```
and restarted X (ctrl-alt-backspace).  And there it was, a login prompt!  So I punched in my credentials and it went and loaded.... a brown screen with a single terminal window.  I thought, 'ok, somethings messed up with the session manager too', so I tried
```
sudo dpkg-reconfigure gnome-session
``` which failed with some error about the package being corrupt or not installed, so I threw a 
```
sudo aptitude install gnome-session
``` at it, which installed quite a bit of missing dependencies.  This finally did it, I was able to get a login screen, and login to a normal gnome session (it even had my old theme), so I finally had a (mostly) working Ibex system.

I say mostly because I was still bringing up the network manually after every reboot, and there was some standard applications that were obviously missing, like a web browser.  Since I was in gnome, though, these easy enough to install through Add/Remove... (including network manager, so I didn't have to manually start the network adapter).


Once the system was functional, this led to the next major problem, which I've seen mentioned a few times on these boards:  nvidia drivers didn't seem to work at all.  I tried several suggestions: installing different combination of nvidia-*-177 (or 173), messing with the xorg.conf file, but whatever I tried, every time I had 'nvidia' in my xorg.conf file, I would get the message "nvidia kernel module failed to load" and would have to comment it out to get back into gdm.

I even tried envyng or whatever it was called, but it gave me an error about missing kernel headers.  This was the first clue I got.  

I then tried to start manually loading the module
```
sudo modprobe nvidia
```
which gave me some cryptic error about /sbin/lrm-video not being found.  A little searching showed me I could manually load the *.ko module with insmod, and you can find the modules with 
```
sudo find /lib/modules/ |grep nvidia
```
now this only turned up old nvidia modules (which I tried loaded and tested anyway, to no avail), and so it seemed the new module wasn't even being installed properly.

Well, long story short(er), I realized I was still running on kernel 2.6.24, where Ibex is supposed to be 2.6.27 (I should have known since the grub menu still listed 8.04.1).  I don't know why the upgrade didn't install it, and why every time I tried an aptitude update, it said I was up to date, but I wasn't.  So I figured the new kernel is probably needed (the headers that it said it couldn't find earlier only seem to exist in the repos for the new kernel).

Well, to install the newest kernel I found that, after some forum searching, that there is a handy little virtual package:
```
sudo aptitude install linux
```
which installs the kernel and all the necessities.  This of course didn't work the first time I tried it, complaining about some upgrade hook thing missing.  I don't remember exactly what it was, only that I found a launchpad bug related to it, and it was grub related.  So I checked and sure enough, my grub package was busted, so:
```
sudo aptitude install grub
```
which installed quite a bit of dependencies.  Repeating the linux line worked perfectly this time, and created a brand new grub menu for me.  Another nice thing is that it seemed to recognize that the nvidia 177 module wasn't complete, and as soon as the new kernel was installed, it automatically built and installed the nvidia driver.  This was great, I just had to re-add 'nvidia' to my xorg.conf file, reboot, and everything was golden again.

... I of course had to reinstall compiz-gnome, compizsettings-manager, the extra plug-ins, thunderbird, pidgin, etc, etc, but that's trivial.  All my profile/config files still existed, so that was no hassle at all.

Now, to be fair, it didn't exactly go as smoothly as I've typed it up.  There was quite a bit of trial and error, and a whole lot of pointless dpkg-reconfigure <insert random package here> going on. But even though I'm no leet linux hax0r, perseverance clearly paid off.

Well this is the longest post I have ever done, so I hope it is helpful to anyone who runs into similar problems.  now I'm going to sleep.  peace.

---

### Post by TikiKai on 2008-10-31
Great post! I'm sure it will be helpful to a lot of people. I was very lucky with my upgrade...but it was on an entirely clean system I had waiting for the release.
Mahalo!

---

### Post by bantai on 2008-10-31
Thanks for this. My upgrade left me with an unusable system. I am currently trying to restore it using your post. I will let you know how it goes.

---

### Post by pelmenept on 2008-10-31
I am not sure if I hace the same problem as you guys.
Firs of all I have dell notebook with Nvidia.

I upgraded ok (had to fix some stuff) but finally did it.
When ubuntu loads, I see loading screen, but as soon as GDM starts, I see black screen, but I can also see ONLY cursor no problem. I also see that screen tries to update or whatever, it keeps...hmm blinking. 

Funny thing, if I use KDM or XDM - no problem, but in that case, after login, gnome-desktop does not load. I just have wallpaper and cursos and that's it

I am hoping dpkg reconfigure will work for me, when I try it tonight.

I would also say my upgrade was terrrible, everytime up-manager would cauh with "package bla bla trying to replace /bla/bla/bla.so which is already in /bla_lots_of_letters_i386.deb

So I had to manually remove them and start upgrade from beginnning just to be sure it didn't miss packages... did it around 5 times.

Thanks for the post..... flawless upgrade experience.. damn.

---

### Post by glis on 2008-10-31
Thank you bj0. It worked until i need to do a startx. It says that it can't find the "nv" module which I suppose is the nvidia drivers or something like that.

I'm a beginner so i can't find the solution. Via Aptitude, i try to install some nvidia stuff. It still doesn't work.

An idea ?

---

### Post by bantai on 2008-10-31
> **bantai said:**
> Thanks for this. My upgrade left me with an unusable system. I am currently trying to restore it using your post. I will let you know how it goes.

No luck. I ended up upgrading my two systems using a newly downloaded 8.10 CD.

---

### Post by fugitive68 on 2008-10-31
This was super information and I'm now in the process of installing several hundred packages that we're deleted as part of the 'cleanup' task in the automated network-update process.

My xorg.conf had a device entry for nv, but the xorg and xserver-xorg install didn't install the driver (but tseng was).  So the only 'extra' step i needed was:

sudo aptitude install xserver-xorg-video-nv

Once again, THANKS!

---

### Post by bj0 on 2008-10-31
> **glis said:**
> Thank you bj0. It worked until i need to do a startx. It says that it can't find the "nv" module which I suppose is the nvidia drivers or something like that.

I'm a beginner so i can't find the solution. Via Aptitude, i try to install some nvidia stuff. It still doesn't work.

An idea ?

There is a "xserver-xorg-video-nv"  package in the repositories that I think contains this driver.  Note, however, that this is the free/open soruce driver for nvidia cards, and does not support 3D acceleration.  To get 3D acceleration (compiz) you will need "nvidia-glx-177" with it's dependencies.

Also, to make sure it is using the nvidia driver and not the nv driver, you will need:
    Driver         "nvidia"
somewhere in your "Device" section in your /etc/X11/xorg.conf   file

edit: you will need "nvidia-glx-177" or "nvidia-glx-173", but only if you have a newer nvidia card.  There are other packages in there for older nvidia cards: do an "aptitude search nvidia-glx".  And to get more info on the package (description usually says what cards it supports), try "aptitude show <package>" where <package> is for example nvidia-glx-177

---

### Post by michaelaly on 2008-11-04
Your fix didn't work for me, but it did set me in the right direction. I checked my menu.lst and discovered due to a Grub problem during the upgrade that required a Grub reinstall I was running the kernel from Hardy(2.26.24-21). I simply changed the menu.lst entry to 2.26.27-7 and bam, high res graphics and all 3d effects running.

---

