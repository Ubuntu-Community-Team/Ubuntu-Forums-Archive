---
title: "upgrade to Ubuntu 13.04 taking too long"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by muzzyr on 2014-03-08
Hi
I wanted to upgrade to ubuntu 13.04 today, downloading packages went smooth but installing has taken too long (7 hours). Now the upgrading box+terminal are inactive and they have turned all grey. I have lost access to everything but what I have on desktop, I.e. I can't use bars to run programs , etc.
It seems I just can physically restart the laptop but that would damage the upgrade I reckon.
Any suggestions?
It's a Lenovo 450 by the way, and no other OS running on it.

---

### Post by buzzingrobot on 2014-03-08
13.04 is no longer supported, and the original repos are unavailable, as of Jan 30 of this year.  More here: [http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/).

Consider upgrading to 13.10, the current release.  The next LTS, 14.04, is due in mid-April.

---

### Post by muzzyr on 2014-03-08
Thank you for your reply. Probably it was 13.10, as I didn't upgrade manually and followed the upgrade center's option, so I assume it shouldn't have given an option for that version.
Anyhow do you suggest a restart? Isn't there risk of losing data?

---

### Post by buzzingrobot on 2014-03-08
Did you see any error messages? It's possible that the server you were pulling files from was offline.

If the upgrade stalled while the packages were being downloaded, then none of them should have been installed, and a reboot *should* be safe.  (Caveat: emphasis on 'should' because the reason the upgrade stalled is unknown. ) The messages displayed in the upgrader's terminal window indicate when it has switched over to installing packages.

If the package install process had started, what might happen on a reboot depends on what exactly was installed before things stalled, and if something critical -- like grub or the kernel or a video driver -- was left partially installed. If that's the case, a reboot might be unsuccessful.  

PPA's and software from them can cause upgrade problems because the upgrader is, necessarily, unaware of that software. That's especially the case if PPA's have been used to replace system components.  PPA's should be removed and their software backed out before upgrading from one release to the next.

You might try interrupting the reboot and going into recovery mode.  You should be able to enable networking from there, and then open a terminal to try a manual upgrade.

Or, you could reboot as usual and, if successful, open a terminal and do a manual upgrade. (I'd try this first because you can then go for the recovery mode boot. )

To upgrade manually, execute "sudo apt-get update", and then "sudo apt-get dist-upgrade" and reboot.

---

### Post by muzzyr on 2014-03-08
Actually it doesn't show anything right now and I didn't see an error message, just a frozen box, but it was going through installing, so as you said there might be problems.
Your suggestions are very helpful, I'm going to try them and will update the thread with result.

---

### Post by buzzingrobot on 2014-03-08
I'm assuming you are trying to go from 13.04 to 13.10.  If that's not the case, then a bit of Google research might be in order because the upgrades are intended not to skip releases. (Admiitedly, I never upgrade; just do a clean install.)

 Here's ([http://www.noobslab.com/2013/10/upgrade-to-ubuntu-1310-saucy-from-any.html](http://www.noobslab.com/2013/10/upgrade-to-ubuntu-1310-saucy-from-any.html)) a link from a usually reliable site that might be of help, in that case.

---

### Post by muzzyr on 2014-03-08
Ok, I carried out what you suggested.
With few other commands it seems that installation is complete.
But strangely I don't have bars in desktop so no option to run programs. I just can open the files on my desktop and then through some of them get to some other files and programs, I don't know how to open terminal or do anything else... Well, stuck.
But I guess I should open another thread for this problem.
Many thanks for your helpful suggestions.

---

### Post by buzzingrobot on 2014-03-08
What version did you upgrade from?

I'm not sure what you mean by "bars".  Older versions of Ubuntu used Gnome 2, which placed panels at top and bottom and used dropdown menus.  The Gnome 2 developers (it was not a Canonical project) abandoned it about 3 years ago.  In the aftermath,  Canonical developed the Unity interface for Ubuntu, which puts a panel on top of the screen and a dock fixed on the left edge. Clicking the top icon in that dock will expose a window with your system's applications, etc.  Unity also relies heavily on a search mechanism triggered by tapping the Windows aka Super key.  E.g., tap it., starting typing the name of something and its icon will be displayed.

---

### Post by muzzyr on 2014-03-08
I meant panels exactly as what you said on top and left. I had them on previous distribution (12.10 if I'm not wrong)  but now they have disappeared. 
The super key doesn't work either.

---

