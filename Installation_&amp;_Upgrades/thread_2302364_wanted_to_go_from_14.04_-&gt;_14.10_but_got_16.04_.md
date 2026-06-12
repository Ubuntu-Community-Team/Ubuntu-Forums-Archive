---
title: "wanted to go from 14.04 -&gt; 14.10 but got 16.04 now stuff doesn't work"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by uh-huh on 2015-11-09
Hi, did  ```
$sudo do-release-upgrade -d

``` hoping to move up to 14.10 from 14.04. But now got 16.04. Now can't even reboot, or shutdown. irssi doesn't even work. No error, the cursor pops back up without a word. Tried to install Chatzilla in Firefox so I could ask at irc#ubuntu. Nothing happened. It kept asking me to download and install it, over and over.

This was at the end of ```
$grep error /var/log/dist-upgrade/main.log
```
 > 2015-11-09 16:04:56,045 ERROR got an error from dpkg for pkg: 'sysv-rc': 'subprocess installed post-installation script returned error exit status 1'
2015-11-09 16:04:56,046 DEBUG running apport_pkgfailure() sysv-rc: subprocess installed post-installation script returned error exit status 1
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)And this was at the end of the console read out after completion:> Errors were encountered while processing:
 lvm2
 libc-bin
 fontconfig

---

### Post by Bucky Ball on 2015-11-09
14.10 is no longer supported so that wouldn't have worked anyway. Not sure how you got to 16.04 LTS though. Please open a terminal and post the output of this:

```
lsb_release -a
```

Perhaps as it was impossible to go to 14.10 the system has somehow decided that it should go to 16.04 LTS, which is the next logical step for it as LTS can be upgraded to LTS directly via the net. But that option to 16.04 LTS shouldn't be available yet as far as I know. Development has only really just kicked off and its far from ready to roll.

You were trying to upgrade from a LTS release, supported until 2017, to an EOL interim release that has nine months support (which is now over). :)

---

### Post by QIII on 2015-11-09
The -d flag upgraded you to the development version, which is 16.04 LTS.

As a development version, breakage is frequent.

---

### Post by Bucky Ball on 2015-11-09
> **QIII said:**
> The -d flag upgraded you to the development version, which is 16.04 LTS.

As a development version, breakage is frequent.

Thanks QIII. In which case, there is no going back. 

Check the output of that command I gave and if it says you are now on 16.04 LTS, you can leave that there and test it/play with it and install 14.04 LTS or 15.10 on another partition or advise you create a 14.04 LTS or 15.10 boot media, USB or disk, boot from that, 'Try Ubuntu' and backup your valuable data to external media then install 14.04 LTS or 15.10. Both will upgrade directly to 16.04 LTS, just the way you have done it here, or via a GUI after its release.

---

### Post by sammiev on 2015-11-09
I guess they are a Ubuntu Development Tester now. :)

---

### Post by Bucky Ball on 2015-11-09
If you do decide to continue testing/reporting/attempting to fix 16.04 LTS, please note that support requests for this should be posted in the *[Ubuntu Development Version]("http://ubuntuforums.org/forumdisplay.php?f=427")* section of the forums. :)

---

### Post by QIII on 2015-11-09
Sorry my previous post was so short.  I'm on cell phone on a crowded train.

:)

---

### Post by uh-huh on 2015-11-09
~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Xenial Xerus (development branch)
Release:	16.04
Codename:	xenial

---

### Post by Bucky Ball on 2015-11-09
You're there. See post #4 for possible options.

---

### Post by uh-huh on 2015-11-09
> **Bucky Ball said:**
> 

advise you create a 14.04 LTS or 15.10 boot media, USB or disk, boot from that, 'Try Ubuntu' and backup your valuable data to external media then install 14.04 LTS or 15.10. Both will upgrade directly to 16.04 LTS, just the way you have done it here, or via a GUI after its release.

Don't have spare partitions. How does having a boot USB help? Can I use it to boot my current OS? Don't I have to do a change root, which IIRC, was nothing like having normal user access to my PC?

---

### Post by Bucky Ball on 2015-11-09
To reiterate. You now have an unreleased, buggy, wet-behind-the-ears release that is not fit for mainstream consumption at this point. You can persevere with it, test it, report bugs, and go on a steep learning curve, as that is now your operating system, or you can go back to an earlier release with a clean install. Forget what release you were running previously. You have successfully eradicated that and are now running 16.04 LTS. When it is released next April it will be supported for five years, until 2021.

Bottom line: if you want an earlier release, back up any valuable data you have on the machine and install whichever release you want. 

Boot USB can get you to a desktop by choosing 'Try Ubuntu' where you can save your files to an external disk before reinstalling.
No, you can't use it to boot your current install of 16.04 LTS, has nothing to do with that. Beyond there. 
Do a change root? No idea what that is about. 

If you are wanting to stick with 16.04, as I mentioned, best to post in the ***Ubuntu Development Version*** area of the forums as that is where support belongs and where you will get the best help. The average user will know little to nothing about 16.04 and its trials and tribulations on the other areas here.

---

### Post by grahammechanical on 2015-11-10
I would just like to say that when 16.04 is close to its release day the developers will add various scripts to handle upgrading from 14.04 and from 15.10 to 16.04. And that should make the upgrade path as smooth as possible.

The person who started this thread has had problems because inadvertently they upgraded to 16.04 without those developer scripts being present. I have been running xenial xerus (16.04 development) since the first day its development period started and I find it very stable. But I started from a fresh install of 15.10 and not 14.04 and at the moment 16.04 is not too different from 15.10. But there must be a massive code difference between 14.04 and the present state of 16.04 development.

Regards

---

### Post by uh-huh on 2015-11-11
Thanks for all your help! One last question: Have 80G on home dir. Looks like I'll have enough space to slip a tarball into another partition. How much can this be compressed? What is the tar <options> I should use? Two questions ;)

---

### Post by Bucky Ball on 2015-11-11
> **uh-huh said:**
> One last question: Have 80G on home dir. Looks like I'll have enough space to slip a tarball into another partition. How much can this be compressed? What is the tar <options> I should use? Two questions ;)

Two questions buried on a thread concerning something else and not related to the title. Best to post a new thread(s) about these issues to improve your chances of support. :)

---

