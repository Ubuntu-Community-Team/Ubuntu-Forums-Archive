---
title: "Unreal, Intrepid is rocking, BBC streaming never looked this good."
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-15
Still got flash video sound coming through pc speaker and got sound set to Alsa. But this is the bees knees.

---

### Post by Kilz on 2008-07-15
> **philinux said:**
> Still got flash video sound coming through pc speaker and got sound set to Alsa. But this is the bees knees.

Its nice to hear that at this very early stage in the development of Intrepid it is looking good. But, there is a lot of work left to do. I personally would not run Intrepid as a every day os because I like stability.

---

### Post by bapoumba on 2008-07-15
Moved to Intrepid.

---

### Post by philinux on 2008-07-15
> **Kilz said:**
> Its nice to hear that at this very early stage in the development of Intrepid it is looking good. But, there is a lot of work left to do. I personally would not run Intrepid as a every day os because I like stability.

Yep it's on my spare hard drive as a full install.

Fonts look better in firefox too.

I accidentally posted in 64 bit. Must stop doing this.:lolflag:

Having to report you're own thread to be moved. Ha.

---

### Post by Nullack on 2008-07-15
I run it everyday as my primary os (have backups if needed)

To stop pc speaker blacklist the module, works well

---

### Post by philinux on 2008-07-15
It's only on flash which I'm not bothered about. I see pulse audio still not producing a test sound.

I'll leave mine as it is then I'll hear the fix.

---

### Post by jerrylamos on 2008-07-15
> **philinux said:**
> Still got flash video sound coming through pc speaker and got sound set to Alsa. But this is the bees knees.

Well, Ibex Alpha 2 Xubuntu here, YouTube video O.K.  BBC and Yahoo video hang loading video forever.  Ctrl-Alt-Backspace & Restart time.  This is a Celeron 1.2 gHz 640 MB.

Same results, Firefox 3.0 and Firefox 3.0.1

Had some problems with Alternate Install manual partitioning.  It set each partition to 8.2 mb.  Standalone Gparted fixed it.

Jerry

---

### Post by jerrylamos on 2008-07-15
> **philinux said:**
> Still got flash video sound coming through pc speaker and got sound set to Alsa. But this is the bees knees.

O.K., downloaded flashplayer 10 tar.gz from the Adobe site.  Tried running the installer and it says
"please enter a valid installation path" like /usr/lib/mozilla.

I've got a /usr/lib/mozilla.  Enter that, and it repeats "Please enter valid installation path".  I tried /usr/lib/firefox.  Same result.

Any ideas anyone?

Thanks, Jerry

---

### Post by psyke83 on 2008-07-15
> **jerrylamos said:**
> O.K., downloaded flashplayer 10 tar.gz from the Adobe site.  Tried running the installer and it says
"please enter a valid installation path" like /usr/lib/mozilla.

I've got a /usr/lib/mozilla.  Enter that, and it repeats "Please enter valid installation path".  I tried /usr/lib/firefox.  Same result.

Any ideas anyone?

Thanks, Jerry

Don't do that, please. Manually installing applications in this way can be a nightmare for you to keep track of *and* for others to support when you post on this forum. Just install the package "flashplugin-nonfree".

---

### Post by philinux on 2008-07-15
> **psyke83 said:**
> Don't do that, please. Manually installing applications in this way can be a nightmare for you to keep track of *and* for others to support when you post on this forum. Just install the package "flashplugin-nonfree".

+1 for that, stick to the repo's or else testing means nothing.

We should not be trying to make it work, just report the bugs against specific hardware.

---

### Post by jerrylamos on 2008-07-15
> **psyke83 said:**
> Don't do that, please. Manually installing applications in this way can be a nightmare for you to keep track of *and* for others to support when you post on this forum. Just install the package "flashplugin-nonfree".

O.K., used synaptic to remove/install flashplayer.  Works for YouTube videos anyway, not for BBC or Yahoo videos on this system.

Thanks, Jerry

---

### Post by L815 on 2008-07-15
> **jerrylamos said:**
> O.K., downloaded flashplayer 10 tar.gz from the Adobe site.  Tried running the installer and it says
"please enter a valid installation path" like /usr/lib/mozilla.

I've got a /usr/lib/mozilla.  Enter that, and it repeats "Please enter valid installation path".  I tried /usr/lib/firefox.  Same result.

Any ideas anyone?

Thanks, Jerry


Copy the libflashplayer (i think that's it) file to ~/.mozilla/plugins (if it doesn't exist create it)

---

### Post by jerrylamos on 2008-07-15
> **L815 said:**
> Copy the libflashplayer (i think that's it) file to ~/.mozilla/plugins (if it doesn't exist create it)

I wish.  Up thru Gutsy that worked fine.  With Firefox 3.0.1 the plugins directory looks like this:

jerry@linux:~$ ls /usr/lib/firefox/plugins
flashplugin-alternative.so  libjavaplugin.so

What's more, those aren't flashplayer files, they are links:

jerry@linux:~$ ls -l /usr/lib/firefox/plugins
total 0
lrwxrwxrwx 1 root root 37 2008-07-15 19:49 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 39 2008-07-14 22:15 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
jerry@linux:~$ 

Things get messy as more programmers write more code.

Thanks anyway, Jerry

---

### Post by philinux on 2008-07-15
Just keep things unmodified.

That way we see the real bugs. :lolflag:

---

### Post by psyke83 on 2008-07-15
> **jerrylamos said:**
> O.K., used synaptic to remove/install flashplayer.  Works for YouTube videos anyway, not for BBC or Yahoo videos on this system.

Thanks, Jerry

You're experiencing problems either because of the Firefox windowless mode bug (hopefully will get fixed in Firefox 3.0.1 or soon after), or incorrect Flash detection (sites believing that Flash 10 < Flash 9).

You can install Flash 9 by downloading the hardy version of "flashplugin-nonfree" from [http://packages.ubuntu.com](http://packages.ubuntu.com) - just don't do manual installs like you've been previously attempting, especially when there are packages available.

---

### Post by jerrylamos on 2008-07-16
> **psyke83 said:**
> You're experiencing problems either because of the Firefox windowless mode bug (hopefully will get fixed in Firefox 3.0.1 or soon after), or incorrect Flash detection (sites believing that Flash 10 < Flash 9).

You can install Flash 9 by downloading the hardy version of "flashplugin-nonfree" from [http://packages.ubuntu.com](http://packages.ubuntu.com) - just don't do manual installs like you've been previously attempting, especially when there are packages available.

Actually this is Firefox 3.0.1.  I get the same problems with Firefox 3.0.  Flash is installed with synaptic since manual install didn't work anyway.
Synaptic put on Shockwave Flash 10.0.0 d525.

What is the Firefox windowless mode bug?

Thanks, Jerry

---

### Post by psyke83 on 2008-07-16
> **jerrylamos said:**
> Actually this is Firefox 3.0.1.  I get the same problems with Firefox 3.0.  Flash is installed with synaptic since manual install didn't work anyway.
Synaptic put on Shockwave Flash 10.0.0 d525.

What is the Firefox windowless mode bug?

Thanks, Jerry

Here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

You are *not* running Firefox 3.0.1, you are probably running 3.0.1build1 which upstream released on 3/7 (and I assume got packaged by Fabio Tassin or Ubuntu's mozillateam). The fix for this windowless mode bug was committed to Firefox's trunk on 8/7, so it's not possible for you to have the fix.

---

