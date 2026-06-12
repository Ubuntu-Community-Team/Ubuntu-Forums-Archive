---
title: "Lucid and Nvidia GeForce 210"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by brucehvn on 2010-05-05
I upgraded to Ubuntu 10.04 a few days ago and I cannot get Lucid to work properly with my video card which is a Nvidia GeForce 210.  It's a fairly new card that was installed just a few months ago.

The only way I can get the computer to boot at all is to remove all the restricted nvidia drivers and use nouveau, but they won't work for X.  I have to use the older "nv" X driver to get Xwindows to load.

If I install nvidia-current, the machine will lock up upon trying to start X. with nothing in the X logfiles.

The card worked fine under 9.10 with the restricted nvidia drivers installed.  I cannot figure out why lucid cannot work.  When using the nouveau drivers, the logs seem to indicate that the nouveau X driver just doesn't recognize the card.  It does seem to recognize it when the kernel is booting.

I need full support for my video card and this is driving me nuts.  When the restricted drivers are installed, nouveau is properly blacklisted and I see no evidence of it in the messages log.  I've tried the nouveau.modeset=0 kernel option as well, but it doesn't do anything.  Failsafe X mode from the recovery boot doesn't work either.

Anyone else have this card working under Lucid?  If so, how?

---

### Post by olivierjeulin on 2010-05-07
Hi,
Yes, the card works with nouveau and lucid.

With karmic, I was using nv and later the nvidia driver. When I upgraded to lucid, nouveau was installed and the nvidia driver wasn't properly uninstalled (the customed /etc/X11/xorg.conf was still there). Each time X started, there was a popup asking what to do: continue, log as root…. I deleted  /etc/X11/xorg.conf and X starts without any problem now.

I've just installed nvidia-current this evening, I'll tell you tomorow if it works (I can't log out right now).

---

### Post by brucehvn on 2010-05-08
> **olivierjeulin said:**
> Hi,
Yes, the card works with nouveau and lucid.

With karmic, I was using nv and later the nvidia driver. When I upgraded to lucid, nouveau was installed and the nvidia driver wasn't properly uninstalled (the customed /etc/X11/xorg.conf was still there). Each time X started, there was a popup asking what to do: continue, log as root…. I deleted  /etc/X11/xorg.conf and X starts without any problem now.

I've just installed nvidia-current this evening, I'll tell you tomorow if it works (I can't log out right now).

Thanks for the info.  The xorg.conf wasn't my problem however.  Specifying the proper nouveau driver would have it just show in the log that it could not recognize the card after several attempts.  Let us know how your nvidia drivers work.  I got an updated kernel through update manager last night, but I haven't tried the nvidia drivers again.

---

### Post by olivierjeulin on 2010-05-08
After a lot of reboot and try/fail, I found a stable configuration with the nvidia driver enabled an working.

To sum up:
- remove xserver-xorg-video-nouveau and xserver-xorg-video-nv
I had to remove xserver-xorg-video-all and all the other unused drivers xserver-xorg-video-*. (this may prevent gdm from starting automatically, which is fine to test if X works)

- install nvidia-current (and the dependencies)

- sudo nvidia-xconfig (to create /etc/X11/xorg.conf, if needed)

- reboot.
After some blank screen and a few kernel startup messages, I have the console login prompt (In my case, gdm didn't start --> sudo service  gdm start)
X login appears :p
nvidia-settings detects the card :p, and compiz works.

No special tweaking.
I do have low resolution and low colour  Plymouth boot, but I don't care ;)
(To re-enable gdm, use sysv-rc-conf, check gdm for runlevels 2-5)

My conf:
$ uname -a
Linux xxxxx 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

$ aptitude show nvidia-current
Package: nvidia-current
New: yes
State: installed
Automatically installed: no
Version: 195.36.15-0ubuntu2

$ lspci |grep -i nvid
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

Let me know if you want more details.

---

### Post by brucehvn on 2010-05-08
> **olivierjeulin said:**
> After a lot of reboot and try/fail, I found a stable configuration with the nvidia driver enabled an working.

...

Let me know if you want more details.

Hi Oliver,

Thanks for that into.  I removed xserver-xorg-video-nv and nouveau and re-installed nvidia-current, and ran nvidia-xconfig.  It still just locks up and hangs the entire system when starting X.  I will try removing all the other xorg video drivers as you suggest.

I do find that even with nvidia-current installed, I can now still log in by reinstalling the nv driver and using that in my xorg.conf, but of course, there's not OpenGL, etc.

Can you either send me or post here (attach) a copy of your xorg.conf and the /var/log/Xorg.0.log files?  I would like to see how yours boots up differently than mine as we are using the exact same kernel versions, driver versions, etc.

Thanks,
Bruce

---

### Post by wkulecz on 2010-05-08
Strange stuff here.

I did a virgin 64-bit install on an AMD Phenom II X4 with a GeForce 210 and things booted up OK but the nouveau driver messed up the display settings such that I couldn't reach any of the Gnome menu selections. I've a Samsung 1920x1200 LCD display runing through a 4-port KVM switch.

Nouveau was OK in my 10.04Beta2 tests on the same box, but had lots of screen redraw bugs when exposing windows, this was much worse.  As I sat there cussing, a "restricted drivers" icon poped up where I could click it and after installing the proprietary drivers, all is well so far.

---

### Post by olivierjeulin on 2010-05-09
Here they are. I also attached a log with errors.

---

### Post by brucehvn on 2010-05-30
Well, it's been over 3 weeks since Lucid came out and I tried to upgrade.  I still have not been able to overcome this problem with my nVidia card.  I have tried every solution that has come through here, and we've been through a kernel update as well as an nvidia-common update, but still no go.  Same issue.  If I use the nvidia hardware drivers, then the machine locks up at the purple screen and I have no output in my Xorg.log.0 file.  I have to use the "nv" driver to get it to work.

I decided to bite the bullet and backed up my home dir and was going to install 10.04 again from scratch only to find the install CD won't load X properly either.  Seems it wants to use the nouveau drivers which I've already seen will not work with my setup.  All I get from the CD is the splash screen while loading, then a garbled, unusable screen.  I can get to a prompt with Ctrl-Alt-F2, but cannot get into the graphical environment.  I tried the "nomdeset" option, tried "nouveau.modeset=0", but same behavior.   I could probably install with the alternate CD, but at this point, I have no confidence that I'm not going to just have the same problems after a fresh install.

It baffles me because I've seen at least two other people with the same video card that have been able to get it to work under Lucid.  I've installed various Linux distros for years and have had lots of weird issues, but I've always found a solution.  This one has me utterly stumped.  9.10 worked so flawlessly, but I just cannot get this upgrade to work.  It boggles my mind.  It's just an nVidia video card.  How can this be so difficult?  Windows works fine with this card, 9.10 worked fine with this card.  So why can't 10.04 do it?

So I guess at this point, I have no choice to to install 9.10 again  I have work I need to do with OpenGL stuff, and I need my nVidia drivers to work.  I've wasted way too much time on this

---

### Post by brucehvn on 2010-05-30
I tried a few more things today to no avail, including installing the Nvidia drivers from their website, but same issue, couldn't get into X.

Just for kicks, I removed my GeForce 210 and put back in my older GeForce 7300 video card.  I removed all the blacklists I had put in.  It did not lock up but couldn't start X and brought me be back to a console.  I reinstalled xserver-xorg-video-all and rebooted and the nouveau drivers loaded with no problem and my X came up.  I installed the Nvidia hardware drivers from the GUI and rebooted and all is well with this card.  No special blacklisting, no special kernel params, nothing.  Everything is as you would expect it to be.

All I did was remove the Geforce 210 and replace it wtih a 7300.  So obviously there is an issue between what I would guess is the Lucid kernel and my GeForce 210.  I guess I will file a bug report.

---

### Post by dennmans on 2010-06-05
Hi everyone,
I have [this issue]("https://bugs.launchpad.net/ubuntu/+bug/562565") with my GeForce 210.  The bug has a couple of workarounds that help the problem, but the solution seems to be 'wait for kernel 2.6.33', which will probably only come out with 10.10 in October.  
If this looks like the bug you're experiencing, please at least click on the 'this bug affects me' at the top of the page.  I'm hoping that more people reporting this will help to speed up a solution.

---

