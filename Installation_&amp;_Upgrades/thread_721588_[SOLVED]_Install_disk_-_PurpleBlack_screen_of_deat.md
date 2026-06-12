---
title: "[SOLVED] Install disk - Purple/Black screen of death (Nvidia?)"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Eoghan Murray on 2008-03-11
Hi All,

[B]
The Long Story:[/B]

I was a happy Gutsy user, and on Friday night absent mindedly agreed to an automatic update which warned that it could only do a  'Partial Update'.  This was a pretty bad idea.

I spent all weekend! Reinstalling the NVidia restricted drivers (even though I had done it before I still managed to clock up just over 60 reboots with incorrect attempts / Envy etc. ) from the NVidia site (NVIDIA-Linux-x86-160....run)

Then the wireless wouldn't work as it depended upon something from the 'Restricted Drivers Package' that I had removed in order to install the Nvidia drivers.

I finally got back to square one, and there was that 'Partial Upgrade' notice in the automatic updates again.  I decided to bite the bullet and, following a recommendation on these forums, try and use Synaptic to do the upgrade to get the system back to normal.

This was my second mistake, as during the upgrade, I agreed to set the locale to en-gb, changing it from the default en-us.  After upgrade, e.g. Postgresql wouldn't start because of locale problems, and after a reboot, I'm dumped into the console, only this time external keyboard & mouse, eth0, eth1 are all broken.  '-bash: /dev/null: permission denied' messages are popping up, so all in all a pretty thoroughly hosed system.

[B]
The Short Story[/B]

I'm trying to reinstall Ubuntu from the 7.10 install Disk, but as soon as it gets to the loaded part (I can hear the ubuntu Jingle)  all I see is a purple screen of death, sometimes black.

I would preferably like to recover the existing installation, but this is tough without internet

My video card is an nVidia GeForce Go 7600

Any help appreciated,

Thanks!

---

### Post by Kramxel on 2008-03-11
I find "envy" pretty usefull when it comes down to nvidia drivers....

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It is a software that will easily install the nvidia driver for you...


Hope this helps...

---

### Post by rillip on 2008-03-11
Quite an unusual situation. If you have another disk handy, I'd run the liveCD, move the stuff you want to save and just start from scratch.  Failing that, if you're careful with the paritioning/install, it's possible to install without loosing anything but the OS system settings, which at this point I think is a good thing for you.

Before you do anything though, boot into the LiveCD, mount the drive, and check the /var/log/dmesg and /var/log/boot (if you have one) to see if there's maybe something we can go on to fix the issue.

---

### Post by Eoghan Murray on 2008-03-12
Thanks for the help,

I've managed to make some progress with the old broken system.
I got ethernet back using 'ifup eth0' and managed to [reinstall locales ]("http://programminglinuxblog.blogspot.com/2007/07/locales-problem-ubuntu-606.html")

I've changed the video driver back to 'vesa' and can now get as far as the normal ubuntu login screen, however the system hangs when I enter my username and password. (I can still click on the options menu at lower left, e.g. click 'restart' but it still hangs).  I have to do a hard reboot.  

What log file should I be looking at to diagnose my current problem?

Many thanks..

---

### Post by Eoghan Murray on 2008-03-13
I've capitulated and done a reinstall with the alternative CD, and now I'm experiencing a black screen exactly like on [_this thread_]("http://ubuntuforums.org/showthread.php?p=4506647#post4506647").  This is similar to my original problem with a Purple/Black screen using the live CD.

---

### Post by Eoghan Murray on 2008-03-24
Closing this thread; 'workaround' was to upgrade to Hardy using alternate installation Disk.

---

