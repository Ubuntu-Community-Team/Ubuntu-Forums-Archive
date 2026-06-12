---
title: "[SOLVED] Firefox Update Broke My Firefox"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by mikeashelby on 2008-02-08
Hi,

I just installed the updates to firefox (including a gnome thingy), and it's broken firefox. When it starts it says it didn't shut down properly last time, do I want to restore or start fresh; and which ever on I select the browser pops up, and the closes immediately. I've tried an uninstall and a reinstall, but with no joy. I even tried firefox 3, and that works, but without displaying text on any web pages...

I'm a complete noob, so am sending this from my windows boot as I can't get my browser to work!

Any advice would be massively appreciated.

Cheers,

Mike

---

### Post by Partyboi2 on 2008-02-08
what happens if you try and start firefox from the terminal. Open a terminal (Applications>Accessories>Terminal) and type firefox

---

### Post by mikeashelby on 2008-02-08
Cheers for the help. Firefox says:

(gecko:6328): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'
Segmentation fault (core dumped)

When I try to run it from the terminal... Any thoughts?

m

---

### Post by Cybergod on 2008-02-08
Are you using Gutsy?  Try changing the permissions of your '/usr/share/fonts' folder to 755.  Have you installed any new fonts?

---

### Post by navneeth on 2008-02-08
I'm having the problem too. It doesn't open at all. In fact, I had opened Firefox while doing the apt-get dist-upgrade, but after I noticed there was an update for Firefox, I closed it, let the updates install, and then clicked on Firefox menu item, via the terminal, Alt+F2/F3...nothing works!

---

### Post by Cybergod on 2008-02-08
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/133124]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/133124")

---

### Post by navneeth on 2008-02-08
> **Cybergod said:**
> [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/133124]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/133124")

Forgive my ignoarance, but that seems to a bug report from last year. :confused:

Anyway, here's what pops-up in my terminal

> navneeth@ubuntu:~$ firefox
navneeth@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux
navneeth@ubuntu:~$ firefox --version
Mozilla Firefox 2.0.0.12, Copyright (c) 1998 - 2008 mozilla.org


---

### Post by kostkon on 2008-02-08
Try to start *Firefox* with a fresh profile, by opening a terminal and giving
```
firefox -ProfileManager
```
Create a new profile and run Firefox. If it will load fine, then that means that your profile is corrupted. Follow [this help on how to manage profiles]("http://www.mozilla.org/support/firefox/profile") to create a new profile and transfer any data from your old one to it.

If the above does not work then you could try to remove *Firefox* completely and then install it again. Better backup your profile before doing this.

---

### Post by navneeth on 2008-02-08
Thank you, kostkon. I'm now able to use Firefox, of course not with my usual profile. And I use FEBE to back-up the profile every week. :)

---

### Post by billstei on 2008-02-08
Had nasty font and image rendering problems after 2.0.0.12 update.  Also noticeable delays when clicking/navigating/scrolling.  Deleted my firefox profile (backed up bookmarks.html file first) and made a new one.  All OK now.

Bill

---

### Post by Chappy7777 on 2008-02-08
Just out of NooB curiosity and because I looked in Synaptic and it's there...

Has anyone tried doing the upgrade/install thru Synaptic rather than the System Updates? I have always updated FFox thru Synaptic and never had any trouble. 

Or do they both use the same loader/installer/whatever?

After all the fun of playing in the flashpugin-nonfree that the System Updater messed up and repairing it by marking for uninstall, applying the uninstall, the reinstalling Flashplugin from Synaptic and having that solve the problem, thank God, I was leary today when I saw the FFox Update pop up in System Updates. I haven't installed the latest version of FFox, since 2.0.0.11 is working fine, and I see folks having similar probs today with the update and yesterday's.

I'll wait till all the real geeks (heavy bean users) decide on the best and safest install of 2.0.0.12
before I install it. If there are bugs in the new version, maybe they'll be worked out.

Old family motto: he who rushes gets there and waits.

---

### Post by mikeashelby on 2008-02-11
It was the fonts. I'd tried to install an arial font, and it had failed for some reason. Anyway, I got rid of it, and things are all good again.

Thanks for all your help.

There may be other unsolved issues here, but as for me, this is solved.

m

---

