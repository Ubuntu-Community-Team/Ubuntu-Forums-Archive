---
title: "Need Help Recovering from Crash during Updgrade (14.04 --&gt; 15.10)"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by JackMohr on 2016-09-23
I recently decided to upgrade my system after not doing so for some time. I had been running Ubuntu 14.04 and attempted to upgrade to Ubuntu 15.10. I left my computer running the upgrade during the day and it appears to have powered off at some point during the upgrade. The system is now unable to properly boot. I tried the "Attempt to repair your current installation" option from this thread ([http://askubuntu.com/questions/249135/booting-issues-after-crash-during-update](http://askubuntu.com/questions/249135/booting-issues-after-crash-during-update)) but the command dpkg-reconfigure -a but it appears "-a" isn't an option and a series of other commands was offered. The computer only runs Ubuntu and doesn't have any separate partitions.

I'm usually good about backing up  my files but I've unfortunately uploaded a lot of photos recently without doing so. Any support to find a solution where I save the files that are on the computer would be greatly appreciated!

I've been using Ubuntu for some time but my knowledge level is pretty low, so the more detail and specific commands to enter into GRUB or terminal you can provide, the better.

---

### Post by Bucky Ball on 2016-09-23
? How did you manage to do that? 15.10 is no longer supported and the Updater shouldn't have offered you an upgrade to a dead release.

How did you try and upgrade???

---

### Post by JackMohr on 2016-09-23
I believe I did it through the Updater... any insight on how I might clean up this mess?

---

### Post by Bucky Ball on 2016-09-23
You believe you did it through the updater or you know? Still bemused that it would offer an end-of-life release. What happens when you switch the computer on? Can you still get to a desktop? If so, open a terminal and give us the results of these two commands, between code tags (green link in first line of my signature at the bottom of this post).

```
lsb_release -a
uname -a
```

---

### Post by JackMohr on 2016-09-23
I can't get to a regular desktop but I can get to the recovery mode. Can I run those commands there?

```
lsb_release a: lots of info in there but it does show the release as wily 15.10
uname -a: Linux jack 3.13.0-95-generic #142 Ubuntu SMP
```

Also noticed as the recovery mode was booting up the error message "Failed to start load kernel modules"

---

### Post by Bucky Ball on 2016-09-23
Well, that shows that you've managed to upgrade to an unsupported release but, like all these baulked installs, it's a mess. If I were you I'd boot to a live session from a 16.04 LTS install media, USB or DVD, 'Try Ubuntu', backup your valuable data and install 16.04 LTS.

You may be able to sort through this but you'll be running an unsupported release if you get to 15.10 anyway. Pointless. 

Just for future reference: LTS = long term support release. 14.04 is an LTS release and is supported until April next year whereas 15.10 died in July/August of this year. Sounds like sticking to the LTS releases would be advisable. Another tip, and could have saved you a lot of time and pain, is that LTS releases upgrade directly to the next LTS. In other words, you could have upgraded 14.04 LTS directly to 16.04 LTS via the Software Updater and avoided this. 

Anyway, for the future. I haven't got the expertise to fish you out of this one if you are intending to attempt a resurrection, but perhaps someone will come along that can. Good luck. :)

---

### Post by JackMohr on 2016-09-23
Thanks for the info! Sorry I wasn't more informative, not entirely sure how I got myself in this fat mess to begin with. 

Totally idiotic question but do I just need to download the Ubuntu 16.04 files onto a USB to be able to do the live session? I just don't want to mangle this anymore than I already have.

---

### Post by Bucky Ball on 2016-09-23
No. You need to [download the ISO from here]("http://www.ubuntu.com/download/desktop") and create a live install USB from it using a USB creator. I use [UNetbootin]("https://unetbootin.github.io/"). Universal USB Creator also works pretty well I've heard, and there are others, too. I only use the first so don't know much about the many other options. 

I presume you are creating the stick using Windows? If so, obviously you are going to want a Win friendly USB creator. Does Win have a USB creator already there by default? Think I'd go with UNetbootin as first choice. I can help you with that, but fairly 'follow your nose'. Give a hoy if you hit a brickwall. Make sure you have a blank USB, format it to FAT32 and off you go. :)

* Booting from a live USB to 'Try Ubuntu' will NOT alter anything on your hard drive. The only way you can do that is to manually install Ubuntu and you would need to hit the 'Install Ubuntu' icon on the desktop and even then you would need to get some way into the install before you actually alter anything on there partitioning-wise. 

Let us know how it pans out.

(PS: The only silly questions round here are the ones that go unasked. 

[QUOTE=Ubuntu Code of Conduct]Nobody is expected to be perfect in this community. Asking questions early avoids many problems later, so questions are encouraged ...[/QUOTE]

:))

---

### Post by howefield on 2016-09-23
> **JackMohr said:**
> 
```
lsb_release a: lots of info in there but it does show the release as wily 15.10
uname -a: Linux jack 3.13.0-95-generic #142 Ubuntu SMP
```

Might be showing as Wily 15.10 but it is still a Trusty kernel, just wondering if your /boot is full, hence it couldn't install the Wily kernel.

I'd use the Live CD/USB to save your files then it depends on how much you want to fix this upgrade or simply do a clean install with 16.04.1 (or 14.04.5 for that matter).

---

### Post by Bucky Ball on 2016-09-23
> **howefield said:**
> I'd use the Live CD/USB to save your files then it depends on how much you want to fix this upgrade or simply do a clean install with 16.04.1 (or 14.04.5 for that matter).

+1 and well picked re. kernel, howefield. So 'tis. The classic dog's breakfast which results from one of these messed up upgrades. Unfortunately. :| :)

---

