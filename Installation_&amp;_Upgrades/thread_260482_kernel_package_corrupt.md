---
title: "kernel package corrupt?"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Illusionistx on 2006-09-18
i just ran the update manager and it said there was a new kernel update, so i downloaded it and installed it. then it gave me some errors and i ran apt-get install -f and i get this:
```

Unpacking linux-image-2.6.15-27-386 (from .../linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb) ...
The directory /lib/modules/2.6.15-27-386 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Cannot delete /boot/initrd.img-2.6.15-27-386, doesn't exist.
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
so... what's up with that?

---

### Post by Illusionistx on 2006-09-19
anyone?

---

### Post by Illusionistx on 2006-09-19
so no one has had this problem or knows how to fix it?

---

### Post by randell6564 on 2006-09-19
> **Illusionistx said:**
> i just ran the update manager and it said there was a new kernel update, so i downloaded it and installed it. then it gave me some errors and i ran apt-get install -f and i get this:
```

Unpacking linux-image-2.6.15-27-386 (from .../linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb) ...
The directory /lib/modules/2.6.15-27-386 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Cannot delete /boot/initrd.img-2.6.15-27-386, doesn't exist.
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
so... what's up with that?
I just installed those updates and had no problems!  Thats what is great AND Sad about linux!  Everyone's OS is different, unlike Windows, so it's a gamble!

---

### Post by AmboyGuy on 2006-09-19
I just finished updating my kernel and had no problems. 
I have a question, the update appears to have fixed a problem with my mouse and the system not recognizing mouse click's correctly. Where could I find a change log about this update ?

---

### Post by Jim McGinley on 2006-09-19
I ran the update manager with a similar problem and got the following attache d file.

---

### Post by acidbom on 2006-09-19
I just did the new kenel update, and everything seemed to go fine.
It promted me to reboot, and i did.
then i get:
Fatal: could not open /lib/modules/2.6.15-27-386: no such file...
so here i am stuck, no commands work nothing just text on the screen. 
any one help here?

---

### Post by randell6564 on 2006-09-19
> **acidbom said:**
> I just did the new kenel update, and everything seemed to go fine.
It promted me to reboot, and i did.
then i get:
Fatal: could not open /lib/modules/2.6.15-27-386: no such file...
so here i am stuck, no commands work nothing just text on the screen. 
any one help here?
Refer to post #4.

---

### Post by enopepsoo on 2006-09-19
When I updated my kernel tonight it broke my nvidia driver.

That was a pain.:sad:

---

### Post by acidbom on 2006-09-19
Yeah thanks for the insight there...

Any one have a suggestion on how i might recover from this without completely reinstalling.
Thanks in advance.

---

### Post by mcduck on 2006-09-20
I'm also having problems with the latest kernel update. Here's what the update manager says:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-686_2.6.15-27.48_i386.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.11-5_i386.deb
  Size mismatch
```

---

### Post by cneil on 2006-09-20
In your boot manager you can just select the previous kernel and run it.
The new update did horrible things to my x600 ATI graphics too.

I don't have a clue how to fix it.

---

### Post by AmboyGuy on 2006-09-20
I see that people are having problems with graphics cards, luckily for me the nvidia-glx-legacy driver was updated at the same time as the linux-image and I had no problems. Maybe a re-installation of your current graphics driver would help you recover ?

---

### Post by wkulecz on 2006-09-20
Here is my thread from last week. It has the links to how I was able to regress to working system with nvidia drivers.

[http://www.ubuntuforums.org/showthread.php?t=257347](http://www.ubuntuforums.org/showthread.php?t=257347)

After this experience, I skipped yesterday's "updates" while waiting to see if there would be another rash of posts like this one.  Good thing I waited, what I have now meets our needs (six systems) I'll leave well enough alone for now.

On the first system I set up I had a GDM self-destruction that I couldn't fix.  No updates were involved, just shutdwon, moved the box from my office to the lab and it wouldn't start X.  Ended up Ghosting it from the second system I'd repaired, which I'd updated so as to be cloning the most recent code to the other four.

--wally.

---

### Post by chris.olsen on 2006-09-20
I followed the instructions in one of the posts by the admin, on how to fix this problem, but it still crashes on reboot.

****
sudo apt-get update
sudo apt-get upgrade
****

I never had this problem at the start since I didn't immediately re-boot after the udpate (I had some programs running).

Is there anything else that has to be done?  Personally I don't think that I have the library setup properly. Could someone post the exact text to the library so I can add it to the .conf file.

Thanks

---

### Post by hearnden on 2006-09-20
A remote chance is that the file did not download correctly.  Easy to rule out though: just remove the cached copy of the .deb and try to update again (which will download a fresh copy).

```

$ cd /var/cache/apt/archives
$ sudo rm linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb

```

Then try to update again (with synaptic, update manager, aptitude, ...)

---

### Post by chris.olsen on 2006-09-20
ok, I did that and all it really seems to want to update is the flash-nonfree library and it crashes when trying to do this.

(Errors were encountered when processing)

---

### Post by arkan over ip on 2006-09-20
Hello all. I'm on an ATI X550 and the kernel + fglrx update put me back to mesa. Manually installing the latest ATI proprietary driver fixed things for me.

synaptic update history:
```

linux-image-386 (2.6.15.24) to 2.6.15.25
linux-restricted-modules-common (2.6.15.11-4) to 2.6.15.11-5
xorg-driver-fglrx (7.0.0-8.25.18+2.6.15.11-4) to 7.0.0-8.25.18+2.6.15.11-5

```

Xorg.0.log:
```

drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

```

---

### Post by al_sharpe on 2006-09-21
quick solution

at the grub screeen select the 2-6-15-26 kernel

I had no problem with the .27 kernel and 386 mode

I am using a nvidia card and it installed a nvidia update at same time

Al

---

### Post by al_sharpe on 2006-09-21
No the kernel is not corrupt?

you have the nvidia drivers installed and the kernel updates automatically
but you also need to install the
linux-restricted-modules-2.6.15-27-686 or 386
you should use a working kernel ex .26 and install the new restricted
module, shut down and start .27 386 or 686 kernel and your nvidia
drivers should work fine.

Enjoy
Al

---

### Post by al_sharpe on 2006-09-21
quick solution

at the grub screeen select the 2-6-15-26 kernel

I had no problem with the .27 kernel and 386 mode

I am using a nvidia card and it installed a nvidia update at same time

see fix in previous message

Al

---

### Post by mcduck on 2006-09-21
> **al_sharpe said:**
> No the kernel is not corrupt?

you have the nvidia drivers installed and the kernel updates automatically
but you also need to install the
linux-restricted-modules-2.6.15-27-686 or 386
you should use a working kernel ex .26 and install the new restricted
module, shut down and start .27 386 or 686 kernel and your nvidia
drivers should work fine.

Enjoy
Al

THe best way is to make sure that you have the linux-386, linux-686 or linux-k7 metapackage installed. That will make sure that you get automatic updates forr all kernel packages (including the restricted modules)..

---

### Post by wkulecz on 2006-09-21
What's the deal with these meta packages anyways?  Are they a kludge to fix problems with the dependency database?

INMHO they should go away and the "depends on" or "also requires" mechanism should be fixed.

People have always complained about *.rpms, but my experience with Debian based distros that use *.debs (Knoppix, Debian, Ubuntu) is frankly much worse so far.  I initially started with Slackware and RedHat 2 and *.rpms were such an improvement over *.gz that I never looked at Slackware again.  If *.debs are an "improvement" I just do see it.

I'm still on Fedora for my Linux develoment but am deploying Ubuntu because its more friendly to windows/mac users and seemed easier at first.  OTOH setting up six windows boxes starting from a pile of parts, would have taken me much longer.

--wally.

---

### Post by mcduck on 2006-09-22
> **wkulecz said:**
> What's the deal with these meta packages anyways?  Are they a kludge to fix problems with the dependency database?

INMHO they should go away and the "depends on" or "also requires" mechanism should be fixed.

They are packages that depend on the latest version of kernel image, kernel headers, restricted modules and other related packages. They are there to solve the problems people are having when they update kernel files. The problem is that many people don't know about them and install specific kernel packages from the repositories, so when the kernel updates they get updates for the kernel image but not for other packages needed..

So they are not there to help with problems in repositories, but only to help you to automaticly get all updates you need.

---

