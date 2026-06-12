---
title: "Great fixes today , 6/1"
date: 2009-01-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-01-06
- The nervous mouse is fixed....:D

> xorg-server (2:1.5.99.3-0ubuntu4) jaunty; urgency=low

  * 155_dix-don-t-set-the-child-window-for-non-virtual-Enter-Leave-events.patch
    + Fixes issue where mouse cursor in Firefox blinks when hovering over URLs.
      Workaround from X.org upstream bug 19086.  Problem was that
      LeaveNotify events with detail NotifyInferior and non-None child windows
      triggered something in firefox to switch cursor back to arrow instead of
      the link cursor.  A more complete fix has been pushed to upstream git, and
      sounds like it will be backported for 1.6, at which point we can drop this
      patch.  (LP: #312353)





- New kernel

> linux (2.6.28-4.8) jaunty; urgency=low

  * Fix i386/amd64 FTBS by ignoring all module and ABI changes,
    not something you would normally do, but I'm sure the ABI
    has not changed. This will probably also allow the ARM builds to complete.





-tty is fixed  :D   

Probably this fix....

> usplash (0.5.26) jaunty; urgency=low

  * Fix various compiler warnings.
  * debian/splash-functions: Kill usplash more gracefully in splash_stop;
    introduces new SPLASH_ORIG_CONSOLE environment variable which can be
    checked by other init scripts (LP: #304136).
  * Notify the main loop by means of a self-pipe when SIGALRM is triggered,
    rather than attempting to animate the display from a signal handler
    (thanks to Andrea Gasparini for testing and adjustment; LP: #259761).
  * Sleep for 0.1 second rather than 1 second in init script while waiting
    for usplash to die, and adjust the loop count both there and in
    splash-functions to match the previous behaviour of giving usplash up to
    10 seconds to go away (LP: #313574).




- Gnome volume control is in.....

> gnome-media (2.25.1-0ubuntu1) jaunty; urgency=low

  * New upstream version:
    **- Add new volume control applet and dialog**
    - Bug #552748 - General cleanups
    - Bug #552420 - Make speex voice encoder mono
    - Bug #543306 - Use .ogg extension
    - Bug #498617 - Use LC profile by default for AAC
    - Bug #557043 - Add MP2 profile
    - Bug #564060 - Use 32kHz for Speex
    - Bug #553383 - fix "can't delete profile with '#' in its name"
    - Bug #563573 - clean up GLib and GTK+ includes.
  * debian/control.in:
    - updated build requirements
  * debian/gnome-media-common.install:
    - updated the list of files to install (lp: #259945)
  * debian/patches/06_autoconf.patch:
    - new version update




Rock solid for me....   it can still be transients with the Gnome upgrade so watch out for brakes...!!! 

Thanks devs !!!:D


EDIT All changes

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/thread.html)

--------

---

### Post by ShirishAg75 on 2009-01-06
what do you mean by tty is fixed? Please elaborate what issue you were having?

---

### Post by plun on 2009-01-06
> **ShirishAg75 said:**
> what do you mean by tty is fixed? Please elaborate what issue you were having?

tty has been broken a long time and was just left "triaged"....

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301737](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301737)

I cannot be sure that it was the usplash fix which fixed it but probably... tty works again anyway.

---

### Post by zekopeko on 2009-01-06
"Add new volume control applet and dialog"

Pics?

---

### Post by plun on 2009-01-06
> **zekopeko said:**
> "Add new volume control applet and dialog"

Pics?

Yup...  I had it from source installed but reinstalled with Ubuntus packages.  Gnomeuser and I discussed it within another thread.

Here it is...

[[img]http://ubuntu-pics.de/thumb/8014/start2_nz8FVX.jpg[/img]](http://ubuntu-pics.de/bild/8014/start2_nz8FVX.jpg)


Note tabs for input/outputs also !!!

---

### Post by ShirishAg75 on 2009-01-06
Here you go. 

I do not know how to try the sounds though. libcanberra though is 0.10 so it should work. 

What I'm looking for are more sound-themes. There was a call given by Lennart in his blog for the same. 

[http://0pointer.de/blog](http://0pointer.de/blog)

---

### Post by plun on 2009-01-06
> **ShirishAg75 said:**
> 
What I'm looking for are more sound-themes. There was a call given by Lennart in his blog for the same. 



OK,  I am using FreeDesktops default theme...  no jungle..:D


I have also seen sound themes at Gnome-look


Also our friend from Denmark... name ??? writes sound themes  (bad memory)


EDIT   Mads is his name...

[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/New%20System%20Sounds](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/New%20System%20Sounds)

---

### Post by ShirishAg75 on 2009-01-06
How did you get the freedesktop default. What I have is ubuntu , I'm guessing the two packages are different.

```

$ aptitude show ubuntu-sounds
Package: ubuntu-sounds
State: installed
Automatically installed: no


Version: 0.10
Priority: optional
Section: gnome
Maintainer: Ubuntu Artwork Team <ubuntu-art@lists.ubuntu.com>
Uncompressed Size: 1094k
Conflicts: gnome-audio
Description: Ubuntu's GNOME audio theme
 Sounds to spruce up the GNOME desktop environment.

```This is the one which I have got.

Another screenshot of a sort of panel coming out when you click on the speaker icon.

---

### Post by plun on 2009-01-06
> **ShirishAg75 said:**
> How did you get the freedesktop default. What I have is ubuntu , I'm guessing the two packages are different.

This is the one which I have got.

Ok, this is Freedesktops default sound theme

[http://0pointer.de/public/sound-theme-freedesktop.tar.gz](http://0pointer.de/public/sound-theme-freedesktop.tar.gz)

Extract to  /usr/share/sounds   easiest with gksudo nautilus 


The package was stucked somewhere along the road...

[https://bugs.launchpad.net/debian/+bug/281044](https://bugs.launchpad.net/debian/+bug/281044)

---

### Post by ShirishAg75 on 2009-01-06
Right. Just put up a comment at [https://bugs.edge.launchpad.net/debian/+bug/281044/comments/6](https://bugs.edge.launchpad.net/debian/+bug/281044/comments/6)

Isn't it amazing that the freedesktop theme has 37 odd sound files while the ubuntu-theme has only 12.

---

### Post by bash on 2009-01-06
Indeed some nice fixes. I have to say I really like the new Sound Preferences menu. But I'm not a big fan of the new panel you get when you click on the sound icon. Looks really strange and ugly. Don't know why they just didn't keep the old slider for single click and on double click you get the new sound preferences menu.

---

### Post by ShirishAg75 on 2009-01-06
I would reserve judgement till jaunty is done. I haven't yet seen the overall vision as well as new upstream desktop-release of GNOME. Sometime improvements happen over couple of releases. 

I do like the idea/logic behind the gnome-preferences-menu though.

---

### Post by autocrosser on 2009-01-06
So, are the sounds working?  I miss my custom sounds--have the old Gnome login/out sounds + some Star Trek sounds........

---

### Post by plun on 2009-01-06
> **autocrosser said:**
> So, are the sounds working?  I miss my custom sounds--have the old Gnome login/out sounds + some Star Trek sounds........

Please read the bug....

[https://bugs.launchpad.net/debian/+bug/281044](https://bugs.launchpad.net/debian/+bug/281044)

I also followed it to Redhat and its packaged there...

---

### Post by caryb on 2009-01-06
The new Xorg fixed my flickering FF tabs & I now have my 3d effects going also my "kickoff" menu works also:D


Cary




Kickoff is a KDE thing you just wouldn't understand lol

---

### Post by plun on 2009-01-06
> **caryb said:**
> The new Xorg fixed my flickering FF tabs & I now have my 3d effects going also my "kickoff" menu works also:D

Kickoff is a KDE thing you just wouldn't understand lol


Well... I am a gnome-freak but KDE 4.2 is awesome great...:D

KDE knocks out Gnome.... better to knock out Windows 7 perhaps:confused:

---

### Post by | MM | on 2009-01-06
> **bash said:**
> I have to say I really like the new Sound Preferences menu. But I'm not a big fan of the new panel you get when you click on the sound icon. Looks really strange and ugly. Don't know why they just didn't keep the old slider for single click and on double click you get the new sound preferences menu.

I totally agree, its not the most attractive widget!  Fingers crossed the look get refined.

> **ShirishAg75 said:**
> I would reserve judgement till jaunty is done.

This is a development forum, so instead of reserving judgment users should feel free to express the direction they would like Ubuntu to take.  :D

---

### Post by exploder on 2009-01-06
I like the idea of a sound preferences menu and I think the timing is right. It is still early in Jaunty development and this could prove to be a welcome feature.I also like that work is being done to fix system sounds. I have wanted to see these working since the introduction of pulse audio. Although these sounds seem like a minor detail, they are important as far as the system being complete.

I see good ideas and actual development going on in Jaunty and I hope that everyone will be supportive of the developers in these efforts. Good things are happening!

Edit: I downloaded today's daily build and checked out the new volume control for myself. The new control is much more usable and fits in with the look of Gnome much better. So far I really like how this release is shaping up!

---

### Post by adult swim on 2009-01-06
ahh the  nervous mouse!  i didnt even realize he had left me until you pointed it out.

---

### Post by autocrosser on 2009-01-06
Thanks for the tip--I had forgot that that was the same thing I had to do to get sounds in Intrepid....I just wish that they would stabilize using libcanberra or whatever to keep sounds "alive"

> **plun said:**
> Please read the bug....

[https://bugs.launchpad.net/debian/+bug/281044](https://bugs.launchpad.net/debian/+bug/281044)

I also followed it to Redhat and its packaged there...

---

### Post by andrewsomething on 2009-01-06
The Freedesktop "Default" sound theme is availiable as a .deb in my PPA:

[https://edge.launchpad.net/~andrewsomething/+archive](https://edge.launchpad.net/~andrewsomething/+archive)

If any one can point to some good sound themes that are appropriately licensed*, there is still be time for me to package them for Jaunty (although the REVU queue is long). 

For some reason most sound themes on gnome-look seem to be KDE themes or just random sounds, not following the theme spec. I guess since GNOME sound are still fairly new... The most popular theme that follows the spec is specifically licensed to prevent derivative works, which sucks as it can be packaged by distros.

* GPL and the like... Unfortunately CC licenses are still not acceptable in Debian, and I would like to push anything I package back to them.

---

### Post by ShirishAg75 on 2009-01-06
andrewsomething, its good to hear from you. Any idea when we can have the free desktop theme in jaunty?

---

### Post by autocrosser on 2009-01-06
Thank you Andrew--worked very well..

---

### Post by ShirishAg75 on 2009-01-06
One big fix. The linux kernel. They had been making it quietly modular all over again. 

> 

linux (2.6.28-4.6) jaunty; urgency=low

  [ Tim Gardner ]

  * Enable CONFIG_X86_E_POWERSAVER=m for i386 generic
    - LP: #237405
  * Build i386 AGP drivers as modules
    - LP: #312721
  * Build i386 DRM as a module
    - LP: #312721

  [ Upstream Kernel Changes ]

  * drm/i915: Add missing userland definitions for gem init/execbuffer.
    - LP: #308387


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002373.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002373.html)

> 
linux (2.6.28-4.7) jaunty; urgency=low

  [ Tim Gardner ]

  * Enable CONFIG_ATH5K=m for i386/amd64
    - LP: #306719
  * Build all i386/amd64 AGP/DRM components as modules.
    - LP: #312721
  * git commands are now installed outside the default $PATH
    Use 'git  CMD' instead of 'git-CMD'.
  * Build in most PATA/SATA drivers. This should allow most i386/amd64 systems to boot
    without an initramfs, though some support work is still required in initramfs-tools
    and grub.
    - LP: #311730


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002505.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002505.html)

> 
linux (2.6.28-4.8) jaunty; urgency=low

  * Fix i386/amd64 FTBS by ignoring all module and ABI changes,
    not something you would normally do, but I'm sure the ABI
    has not changed. This will probably also allow the ARM builds to complete.


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002512.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002512.html)

and the latest

> 
linux (2.6.28-4.9) jaunty; urgency=low

  [ Tim Gardner ]

  * Restore DM_CRYPT, AES, ECB, and CBC as modules. This fixes
    some installer issues with encrypted /home and Private directories.
  * Take one more stab at building armel without module or ABI errors.


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002569.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002569.html)

 The only problem or issue I see is the kernel-helper issue. I hope that 
gets fixed soon and pulse-audio issues otherwise I'm happy with how jaunty
is shaping up.

---

### Post by andrewsomething on 2009-01-06
> **ShirishAg75 said:**
> andrewsomething, its good to hear from you. Any idea when we can have the free desktop theme in jaunty?


Unfortunately, you know as well as I do. (Just a lonely Universe Contributor, not even a MOTU =) ) The package in my PPA is simply a build of the package that existed before intrepid and was rejected from Debian for licensing issues (some CC stuff in there). 

Hopefully your comment on the bug report will wake up the assignee. If not the best place to take this up would probably be the desktop team mailing list.

---

### Post by zekopeko on 2009-01-07
> **bash said:**
> Indeed some nice fixes. I have to say I really like the new Sound Preferences menu. But I'm not a big fan of the new panel you get when you click on the sound icon. Looks really strange and ugly. Don't know why they just didn't keep the old slider for single click and on double click you get the new sound preferences menu.

i have to agree. the new sound icon window looks really ugly. it should be something like vista has.

---

### Post by MadsRH on 2009-01-07
> **plun said:**
> ....I have also seen sound themes at Gnome-look


Also our friend from Denmark... name ??? writes sound themes  (bad memory)


EDIT   Mads is his name...

[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/New%20System%20Sounds](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/New%20System%20Sounds)

Thanks for mentioning me (and my sounds) Plun :D

---

### Post by ShirishAg75 on 2009-01-08
MadsRH,

Thank you for your work but that wiki page is confusing. It needs to be cleaned up a bit. 

Btw love some of the sounds that you have created. Specifically the exit and start sounds are very good. Congratulations and keep up the good work :)


Btw I have posted the query on the ubuntu-desktop mailing list. 

[https://lists.ubuntu.com/archives/ubuntu-desktop/2009-January/001896.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2009-January/001896.html)

Update :- Just gave a whirl on the freedesktop sounds. 16 of the 37 have nothing (meaning no sound) . 
The files which I couldn't play were all less than 10 K in size. 

/usr/share/sounds/freedesktop/stereo/message-new-email.ogg
/usr/share/sounds/freedesktop/stereo/button-pressed.ogg
/usr/share/sounds/freedesktop/stereo/link-pressed.ogg
/usr/share/sounds/freedesktop/stereo/menu-click.ogg
/usr/share/sounds/freedesktop/stereo/dialog-question.ogg
/usr/share/sounds/freedesktop/stereo/window-slide.ogg
/usr/share/sounds/freedesktop/stereo/window-maximized.ogg
/usr/share/sounds/freedesktop/stereo/phone-outgoing-busy.ogg
/usr/share/sounds/freedesktop/stereo/dialog-information.ogg
/usr/share/sounds/freedesktop/stereo/window-close.ogg

although README does state it 

> 
RULES:
    Similar to those defined by gnome-audio, quoting Elliot Lee:

    <snip>
        The criteria for sound inclusion:
        . No licensing issues
        . Appropriate length
                . Shorter than 1 second for any sound that denotes a specific event
            . Shorter than 5 seconds for a background sound (basically, startup/shutdown)
So let's see how and if the devs. respond to the same (on the bug) or in the release archive.

What I don't understand is why the desktop-login and desktop-logout.ogg don't work. It plays ubuntu-sounds therein. Specifically logging in.

---

### Post by Fubarovic on 2009-01-08
The latest kernel doesn't seem to include LVM support (dm_mod module). As a result, I cannot boot my system anymore since my / is on a logical volume. 

I tried to rebuild the ramdisk with explicit LVM support, by adding "dm_mod" to /etc/initramfs-tools/modules. The rebuild went without errors, but I noticed the dm_mod-module wasn't included. 

When I looked in /lib/modules/2.6.28-4-generic/, a "find" command revealed there was no dm-mod.ko

```

[root@machine/lib/modules/2.6.28-4-generic] # find . -iname 'dm*'
./kernel/drivers/dma
./kernel/drivers/hwmon/dme1737.ko
./kernel/drivers/md/dm-zero.ko
./kernel/drivers/md/dm-crypt.ko
./kernel/drivers/media/dvb/dm1105
./kernel/drivers/media/dvb/dm1105/dm1105.ko
./kernel/drivers/net/tulip/dmfe.ko
./kernel/drivers/net/usb/dm9601.ko
./kernel/drivers/scsi/dmx3191d.ko
./kernel/ubuntu/dm-loop
./kernel/ubuntu/dm-loop/dm-loop.ko
./kernel/ubuntu/dm-raid4-5
./kernel/ubuntu/dm-raid4-5/dm-mem-cache.ko
./kernel/ubuntu/dm-raid4-5/dm-message.ko
./kernel/ubuntu/dm-raid4-5/dm-raid4-5.ko
./kernel/ubuntu/dm-raid4-5/dm-region_hash.ko
./kernel/ubuntu/misc/dm-bbr.ko

```

Has anyone else noticed? It seems like a very strange "bug".

[edit]
I think I've run into [bug 314879](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/314879).
[/edit]

---

### Post by ShirishAg75 on 2009-01-08
A poster gave this command, perhaps it can be of help . 

```

$ lvm vgchange -a y
exit

```

He gave in one of the forum posts today itself. That might work for you. 

Btw to get the other topic I was talking about. 

In /usr/share/sounds there are 118 sounds of KDE as well. They all seem to be part of the kdebase-runtime-data package 

While I was playing with them a though occured

that with sounds like 

 KDE-Sys-App-Error-Critical.ogg and 

KDE-Sys-App-Error-Serious-Very.ogg

the accessibility of KDE to differently-abled people would  become very good.

---

### Post by Fubarovic on 2009-01-08
> **ShirishAg75 said:**
> A poster gave this command, perhaps it can be of help . 

```

$ lvm vgchange -a y
exit

```

He gave in one of the forum posts today itself. That might work for you. 


Activating the volume groups and exiting the busybox shell works. The boot process continues right away. Thanks.

---

### Post by andrewsomething on 2009-01-08
@ MadsRH

You PMed me about packaging your theme, but you seem to have your profile set not to receive PMs.

I just brought up your theme on the desktop-devel listserve. There is no reason that it shouldn't be in the archive. In fact, as it was used for testing before, there should already be packaging done for it. I'll wait a bit to hear if there is any response there, as I don't want to duplicate the effort by repackaging if it already exists on some other devs hard drive.


I'll be in touch,

-Andrew

---

### Post by ShirishAg75 on 2009-01-12
Hi all, 
 An update, there is now a sound-theme- freedesktop 0.2 and can be found at REVU 

[http://revu.ubuntuwire.com/details.py?package=sound-theme-freedesktop](http://revu.ubuntuwire.com/details.py?package=sound-theme-freedesktop)

---

### Post by ShirishAg75 on 2009-01-12
> **andrewsomething said:**
> @ MadsRH

You PMed me about packaging your theme, but you seem to have your profile set not to receive PMs.

I just brought up your theme on the desktop-devel listserve. There is no reason that it shouldn't be in the archive. In fact, as it was used for testing before, there should already be packaging done for it. I'll wait a bit to hear if there is any response there, as I don't want to duplicate the effort by repackaging if it already exists on some other devs hard drive.


I'll be in touch,

-Andrew

Link to the discussion please.

---

### Post by Slug71 on 2009-01-12
Maybe someday we'll have a great fix for nspluginwrapper, like just get rid of that ****en piece of s**t!!
Had constant crashes throughout the Intrepid dev cycle and its happening again. Damn npviewer.bin!! Junk junk junk!!

---

