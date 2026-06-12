---
title: "Upgrade to 12.04 disabled my wacom"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by orkaboy on 2012-04-29
Hi forum!

I have a Wacom Cintiq 21UX (combined 21" screen and a wacom tablet) that I use on my Ubuntu computer. Up until now it has been working flawlessly, but when upgrading from 11.10 to 12.04 I've run into a big problem.

The screen doesn't activate (I don't even get an image from the display). Restarting the wacom gives the following output on dmesg:

> [ 1371.616025] usb 5-2: new full-speed USB device number 3 using uhci_hcd
[ 1371.791217] input: Wacom Cintiq 21UX as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input13
[ 1381.264046] usb 5-2: USB disconnect, device number 3

Output of uname -a is:

> Linux **** 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I have confirmed that the device still works (that this is not a hardware defect) by booting up an older live CD.

Any ideas?

---

### Post by Favux on 2012-04-29
Hi orkaboy,

Welcome to Ubuntu forums!

Go to System Settings (cogwheel top right) and open the Wacom Graphics Tablet applet.  Click on 'Map to Monitor' and check the settings.  Are you able to use it to change them?

---

### Post by orkaboy on 2012-04-29
> **Favux said:**
> Hi orkaboy,

Welcome to Ubuntu forums!

Go to System Settings (cogwheel top right) and open the Wacom Graphics Tablet applet.  Click on 'Map to Monitor' and check the settings.  Are you able to use it to change them?

I get "No tablet detected" from the settings dialog. I tried to restart the tablet while this dialog was open, with some interesting results. The tablet pops up (correctly identified), I can see all the settings and so on. However, after a few seconds the tablet disappears again (the usb disconnects, as I figured from dmesg before).

---

### Post by Favux on 2012-04-29
> I get "No tablet detected" from the settings dialog. I tried to restart the tablet while this dialog was open, with some interesting results. The tablet pops up (correctly identified), I can see all the settings and so on. However, after a few seconds the tablet disappears again (the usb disconnects, as I figured from dmesg before). 
Clever.  OK, we want to look at your Xorg.0.log in /var/log and see what happened before and after the hot plug event.  Your Xorg.0.log.old might have something too.  It's big so you might want to compress it (right click it and Create Archive) and attach it to your post.  It is sounding like there is a crash in the gnome-settings-daemon or something.  That may be what's blocking your display.  They have added some bug fixes recently to libwacom.

Also what is your video chipset?
```
lspci | grep VGA
```

---

### Post by orkaboy on 2012-04-29
lspci | grep VGA returns the following:

> 01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX] (rev a2)

A bit oldish, but it works. In case you want further info on the driver, here is a cutout from glxinfo:

> OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GTX/9800 GTX+/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 295.40

I'm using nvidia-current as my graphics driver.

I'm attaching my /var/log/Xorg.0.log, there is some interesting stuff about the wacom at the end of it (starting around row 410). I couldn't figure out much from it though, other than that it sets everything up correctly, and then loses the connection.

Tomorrow I will try to connect another tablet (wacom intuos4) to my computer and see if that works or not. I find it rather interesting that the display capabilities of the Cintiq seems to have stopped working...

---

### Post by whiskers751 on 2012-04-29
Yet another ANNOYING kernel problem!!!

Hold Shift on boot
Choose an OLDER kernel
Ta-rah!

New kernels may break stuff.
If something seems strange after upgrading - try older kernels!

---

### Post by orkaboy on 2012-04-29
> **whiskers751 said:**
> Yet another ANNOYING kernel problem!!!

Hold Shift on boot
Choose an OLDER kernel
Ta-rah!

New kernels may break stuff.
If something seems strange after upgrading - try older kernels!


Sorry, already tried that one. I booted up 3.0.0-16 (the only older kernel available after the upgrade) but the behavior is the same.

---

### Post by Favux on 2012-04-29
Right.
> I'm attaching my /var/log/Xorg.0.log, there is some interesting stuff about the wacom at the end of it (starting around row 410). I couldn't figure out much from it though, other than that it sets everything up correctly, and then loses the connection.

This appears to be the problem:
```
[   102.116] (EE) Wacom Cintiq 21UX pad: Error reading wacom device : No such device
```
We know darn well that xf86-input-wacom-0.14.0 handles the pad (ExpressKeys).  So my guess is it is libwacom that is the culprit.  The default version in Precise is 0.4 I believe.  Right after the 0.4 tar was release the following commit was added to the libwacom git repository:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=commit;h=92765d8c233c04a6ac0c313a23b2963d676003cc](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=commit;h=92765d8c233c04a6ac0c313a23b2963d676003cc)  So that's why I'm guessing libwacom.

It is a little exasperating if that is indeed the problem.  To have a driver that works fine get "blocked" by a defective configuration gui is a wee bit irritating.

So the question is does the Wacom Graphics Tablet applet handle an updated libwacom if we correctly clone the libwacom git repository and compile it?

First steps would be to install git:
```
sudo apt-get install git
```
and then clone it:
```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/libwacom
```
But the README in the libwacom folder you end up with tells us nothing.

So up to you.  Do you want to try and figure it out?  Assuming this is the problem.

Also when you look in the NVidia configuration gui you get from the proprietary driver what do you see?  Anything about setting up the Cintiq's monitor?

---

### Post by Favux on 2012-04-29
Less inclined to think it is libwacom because when I look at the Ubuntu Source Package: libwacom (0.4-1ubuntu1) in Package Search the Changelog says:
> libwacom (0.4-1ubuntu1) precise-proposed; urgency=low

  * Merge from debian unstable, remaining changes: none.
  * Add libwacom-tablet-description-fix.patch which adds a new stylus id
    for the bamboo-pen-and-touch definition so that gnome-settings-daemon
    won't crash due to an unknown stylus, thanks Edward Donovan!
    (LP: #934445)

 -- Timo Aaltonen <tjaalton@ubuntu.com>  Fri, 30 Mar 2012 13:10:06 +0300

libwacom (0.4-1) unstable; urgency=low

  * New upstream release. (Closes: #667064)
    - Add Intuos 5, Bamboo One definitions
  * Drop git_touchpad_tablet.patch, included upstream.
  * Add git-add-missing-buttons.patch, missing button sections for Intuos
    and Cintiq series.
  * libwacom2.symbols: Add a new symbol.
  * control: Add DM-Upload-Allowed field.
  * copyright: Update the format url.

 -- Timo Aaltonen <tjaalton@ubuntu.com>  Fri, 30 Mar 2012 11:28:44 +0300

libwacom (0.3-1) unstable; urgency=low

  * Initial upload. Closes: #659700
  * git_touchpad_tablet.patch: "Don't fail to create WacomDevice for Touch"
    should fix gnome-settings-daemon segfault on some devices.

 -- Timo Aaltonen <tjaalton@ubuntu.com>  Tue, 20 Mar 2012 19:33:21 +0200
So the patch was backported and isn't the problem.

Are you happy with the Nvidia config setup?

---

### Post by orkaboy on 2012-04-30
Oookay...

The problem is solved, kind of. When I opened the nVidia control panel I saw the Cintiq as a disabled screen (usually enables itself by default, not anymore apparently). Turning it on (twinview) here turned on the monitor again, and magically activated all wacom functionality as well.

As to why it behaves this way, or what has changed since 11.10, I'm slumped... thanks a LOT for the debugging help though!

---

### Post by Favux on 2012-04-30
lol  Great!

The Wacom tablet applet doesn't show or let me configure my tablet buttons.  Better than the crashing it was doing in Precise a couple of weeks ago.  But anyway I finished figuring out how to compile libwacom and have done so.  Now I need to look at where the files are and if a reinstall of the libwacom package default will recover everything.  In other words up up to *sudo make install*.  Now you've lessened my motivation.  Heck I still use xsetwacom scripts to configure things.  :)

---

### Post by orkaboy on 2012-04-30
> **Favux said:**
> Heck I still use xsetwacom scripts to configure things.  :)

Well, so do I. Or I did before this release at least, since there was no other way to map to specific monitors or configure buttons.

---

### Post by Favux on 2012-04-30
Sure.

They killed wacomcpl when they forked xf86-input-wacom from linuxwacom.  So we haven't had a configuration gui since Lucid.  That's two years now.

It would be some kind of victory to finally have a gui back that lets me configure my buttons.  What kind of victory I'm not sure...  I'll probably still use my scripts anyway, especially since I rarely hotplug.

---

