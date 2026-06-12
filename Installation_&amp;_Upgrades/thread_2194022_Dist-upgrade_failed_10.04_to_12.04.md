---
title: "Dist-upgrade failed 10.04 to 12.04"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by exepcis on 2013-12-16
I tried to upgrade from Ubuntu 10.04 to 12.04 but run into errors.

The message is *Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'*

I attach the dist upgrade log which is confusing me.

---

### Post by fantab on 2013-12-16
Have you followed [this Wiki page]("https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Desktops_10.04_LTS_to_12.04_LTS_.28Recommended.29") on how to upgrade?

---

### Post by exepcis on 2013-12-16
Yes I did after updating

---

### Post by deadflowr on 2013-12-16
You need to disable/remove the medibuntu repos.

i forget if they're in the sources.list file or if they have a folder in the sources.list.d folder.

But you should be able to disable them in the program "software sources"
They would be listed in the "other software" section.

The reason for the removal is because those repos don't exist anymore, anywhere.

The lucid desktop packages reached end of life, so I assume that the various packages that required the mediubuntu repos were not updated to reflect the changes. Where as the currently supported versions like 12.04 and newer were.

I actually did not look at your dist-upgrade log any further and more action might be needed, but that one action was one the glared at me.

---

### Post by fantab on 2013-12-16
If you allow me, then I want to suggest that you should consider a clean and fresh install of 12.04, or 13.10. It much simpler and saves lots of time. I hope your data is all backed up.

---

### Post by exepcis on 2013-12-16
Thanks Fantab, but at this stage i prefer to upgrade and that must not be very difficult in Ubuntu I thought.

I removed Medibuntu from the sources. Updated but still the same error msg if try to upgrade.

Latest dist upgrade log attached[ATTACH]248645[/ATTACH]

---

### Post by deadflowr on 2013-12-16
Like I said, did not read the log beyond what I saw.
But what is the output for
```
sudo apt-get upgrade
```
copy that and paste what it says.
Answer n(no) for now, if anything like that comes up.

and use the code tags function so people don't have to download that little bit of text everytime.

Here's a quick look at how to use code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by exepcis on 2013-12-16
result 

```

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by deadflowr on 2013-12-16
So I was reading this old thread
[http://ubuntuforums.org/showthread.php?t=1592083](http://ubuntuforums.org/showthread.php?t=1592083)
and noticed you have a couple ppa added.
Maybe post the output for the /var/log/dist-upgrade/apt.log as well.
Hopefully that will gives us a better clue as to what is being held back.

Once that is known, then we can proceed from there.

---

### Post by exepcis on 2013-12-16
Ok. Attached is the apt log

---

### Post by deadflowr on 2013-12-16
The held package is the libcv-dev package.
The two commenters  in this blog had the same problem, or at least the same broken package being held back.
 [http://bramp.net/blog/2012/04/29/failed-ubuntu-update/](http://bramp.net/blog/2012/04/29/failed-ubuntu-update/)

You might want to investigate further, though.
Maybe more info could be gleaned from this
[http://askubuntu.com/questions/266419/how-to-solve-the-pkgproblemresolver-error-when-upgrading-to-12-04](http://askubuntu.com/questions/266419/how-to-solve-the-pkgproblemresolver-error-when-upgrading-to-12-04)

Having no idea what the outcome of removing that package would be, I stress that I can only point you to it, and that whether you choose to remove it and see what happens is entirely up to you.
I personally agree with fantab, in that a complete reinstall, fresh and clean, is the simplest solution, if viable.
I hope something in here helps you.
Good Luck.

---

### Post by oldos2er on 2013-12-16
> **exepcis said:**
> Ok. Attached is the apt log

It's best not to make people jump through hoops to try to help you. If you're attaching a *really* long log file, use paste.ubuntu.com or pastebin.com. Otherwise use code tags as deadflowr advised. Thanks.

---

### Post by craig10x on 2013-12-16
I have a suggestion...this would only apply if you run just 1 ubuntu on your set-up because the installer will not offer this option otherwise...Burn a dvd iso of 12.04 and run the live session...after the live session loads in, then select "install ubuntu" to bring up the iso installer...it should offer (as one of the automatic options) to Upgrade you to 12.04...select that and see if it will install that way...

But before you boot off the live iso, make sure you uncheck any ppas you have on your 10.04 hard install...

If it works, then it should carry over most of your programs, all your data and the majority of your settings just like any other upgrade would...if it doesn't work, then your best bet would probably be to clean install, using that very same iso (except then you would select to have it wipe 10.04 and replace with 12.04)...

Back up you important data of course (say, on an external drive or usb flash drive or dvd depending on how much data you have) before you start...

---

### Post by exepcis on 2013-12-16
Thank you so much Deadflowr . The held package is indeed the libcv-dev package. After removing this i can ipgrade now without problem. Strange that the Ubuntu upgrade cant handle this of at least give a notification.

---

