---
title: "Lynx upgrade incomplete due to 3 broken packages"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by yamel on 2010-05-14
I've done as much searching as I know how to do and haven't seen this exact problem.

I chose to upgrade to 10.4 by selecting the option in the Update Manager. Looks upgraded in flavor but missing some functionality. Most glaringly, a task bar.

I'm told I have three broken packages and synaptic will do nothing more until they're fixed:

libgnome-window-settings
libgnome-media0
libgnomecanvas

Here's the error message I get when trying through Synaptic Package Manager to fix the broken packages. Seems to fail each time in the unpacking.

E: /var/cache/apt/archives/libgnome-window-settings1_1%3a2.30.1-0ubuntu1_i386.deb: unable to stat `./usr/lib/libgnome-window-settings.so.1.0.0' (which I was about to install)
E: /var/cache/apt/archives/libgnome-media0_2.30.0-0ubuntu1_i386.deb: unable to stat `./usr/lib/libgnome-media-profiles.so.0.0.0' (which I was about to install)
E: /var/cache/apt/archives/libgnomecanvas2-0_2.30.1-0ubuntu1_i386.deb: unable to stat `./usr/lib/libgnomecanvas-2.so.0' (which I was about to install)

I don't know what other information is necessary or relevant. This is an Acer Aspire 4530 laptop dual-booted with Windows 7.

Thanks for any assistance you can provide!

[edit and update] - found a little more information in the details window of the synaptic activities that failed. After a lot of unintelligible bits (to me) it seems to be blaming broken dependencies in each of the three events - specifically that 'gnome-panel' is not yet configured. I don't know how to copy and paste from that error window - it warns of horrible failures if I continue with Ctrl-C!

Thanks again!

---

### Post by yamel on 2010-05-14
Not getting any nibbles, I see. Is it because I'm not giving enough information?

When I check for broken dependencies in Synaptic there are three listed:

gnome-control-center (1:2.30.1-0...installed and latest version)
libgnome-media0 (2.28.1-0ubuntu1 installed, 2.30.0-0ubuntu1 latest)
libgnomecanvas2-0 (2.26.0-1 installed, 2.30.1-0ubuntu1 latest)

In Synaptic I cannot change either of the libgnome packages to 'unmark' or 'mark for reinstallation'. I don't know what would happen if I marked them for removal.

The gnome-control-center won't reinstall because the process fails in the unpacking stage of the libgnome packages.

Seems to me that it's not actually downloading any files, just trying to unpack something that is somehow faulty. If that's right, can I make it do a fresh download and install of the libgnome packages outside Synaptic?

Thanks again for taking an interest in my plight!

---

### Post by cbecker78 on 2010-05-14
couldn't hurt to try "sudo dpkg --configure -a" in a terminal...

---

### Post by yamel on 2010-05-17
Thanks, cbecker! Is that command verbatim or shorthand for a string of commands? (Haven't tried it, yet. Just thought I should ask before typing that into the terminal and hitting enter.)

Appreciate your help!

---

### Post by yamel on 2010-05-19
Hi, again. Feel like cbecker78 got me part of the way there, but I just don't know what else belongs with the suggestion "sudo dpkg --configure -a".

Can't get rid of these packages to start over. Don't have the skills to diagnose what these errors even mean ("unable to stat"??)

If anyone has a suggestion for where I should post this or what more is needed to get a response, I really appreciate it. Barring that, is there an easy way to revert back to Karmic? I hate not having a functioning system.

Thanks again!

---

### Post by Catharsis on 2010-05-19
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade
```

---

### Post by yamel on 2010-05-29
Gave up and reinstalled. Thanks! I would say that was a failed upgrade, but thanks very much for your efforts, folks!

---

### Post by WinRiddance on 2010-05-29
I know that it's a little late now but just wanted to add that I never do an Ubuntu upgrade from within the Update Manager unless the system has been running virtually trouble-free from the first day that the previous system had been installed.

If not, I go ahead and back up my home/user folder and my personal data files if they're located on the same partition. Then I reformat and start from scratch with a new installation because Ubuntu makes it so gosh darn easy to use your backed up info. again. Usually it only takes a few minutes to get all of my backed up apps working the way that I want ... with a fresh installation.

---

