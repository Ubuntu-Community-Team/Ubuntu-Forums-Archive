---
title: "Failed to upgrade to Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Scooter7 on 2007-10-18
Hi,

I've been trying to upgrade to Gutsy since 7:30 this morning (9:04 right now), but I keep getting this error:

> Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Any idea why?

---

### Post by adonikam on 2007-10-18
i second that

---

### Post by Archmage on 2007-10-18
Too many people try to upgrade at once?

---

### Post by Lord Landis on 2007-10-18
Though I haven't tried to update yet, my guess would be that the servers are getting slashdotted.  This is, coincidentally, why I haven't done the upgrade yet.  I'm waiting a few days for the frenzy to die down (and for any particularly nasty issues to become known).

---

### Post by Antman on 2007-10-18
Give it a few hours and try again. Or better yet, try again in a day or two when the mirrors are less stressed. This kind of stuff always happens on the "day of" a release.

---

### Post by sdowney717 on 2007-10-18
I have major trouble with my ATI 9600 video card.
I am wondering if the upgrade for me was worth it.

This just makes me want to buy another video card, is Nvidia best?
I keep waiting for ATI to work properly and it never does, so I think it never will.

---

### Post by madsmeg on 2007-10-18
as its only a 9600 i would say just get your wallet out and fork out for a new NVidia, it doesnt have to be amazing, and there are some sites with some real good prices at the moment.

---

### Post by Lord Landis on 2007-10-18
The ATI cards work well if you don't mind recompiling your kernel every time an update to either the kernel or driver is released.  With the nVidia cards, however, there is no need to do this.

The nVidia cards have been, for me, much easier to get working.  They also tend to perform better (even under Windows).

---

### Post by leetcharmer on 2007-10-18
I'm having problems upgrading Edubuntu to Gutsy.  It won't get through the second item on the checklist.  Says it can't find any ubuntu found for upgrading, whether it's ubuntu-desktop, kubuntu-desktop, edubuntu-desktop.  I installed it originally with edubuntu-desktop (7.04).  Why can't I upgrade?

---

### Post by frenchcr on 2007-10-18
upgrade hangs for me...pressed cancel and got these....

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg 
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2
```

:(

...patience is a virtue...servers are jam packed.

I know as i have a gutsy laptop here that cant fetch updates for the first time....to many kids on the block...

---

### Post by z0phi3l on 2007-10-18
> **leetcharmer said:**
> I'm having problems upgrading Edubuntu to Gutsy.  It won't get through the second item on the checklist.  Says it can't find any ubuntu found for upgrading, whether it's ubuntu-desktop, kubuntu-desktop, edubuntu-desktop.  I installed it originally with edubuntu-desktop (7.04).  Why can't I upgrade?

try installing ubuntu-desktop and try again

---

### Post by nikef on 2007-10-18
> **frenchcr said:**
> upgrade hangs for me...pressed cancel and got these....

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg 
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg 
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2
```

:(

...patience is a virtue...servers are jam packed.

I know as i have a gutsy laptop here that cant fetch updates for the first time....to many kids on the block...

Did you get any errors before you pressed cancel ? l,because i am doing the upgrade at the moment as its stuck on the second 1,not sure wheather to cancel or not :confused:

---

### Post by Ber P on 2007-10-18
I also get the "Failed to fetch"-error. I don't think it has anything to do with the traffic. I tried to upgrade to one of the earlier RC a month ago, and got the same error. At that time, I thought it would be solved in the final release - but apparently not.
I tried to disable all third-party software, but that didn't help. 

Sugestions anyone?

---

### Post by Scooter7 on 2007-10-18
I tried some of the solutions found in this thread: [http://ubuntuforums.org/archive/index.php/t-189456.html](http://ubuntuforums.org/archive/index.php/t-189456.html) which didn't work.

So I have no idea what's wrong.   Could be the best way to upgrade is to do a clean install, but I'm hoping to avoid that.  Backups and all, y'know...

---

### Post by Ber P on 2007-10-18
I found a solution to my problem. I noticed that lot's of the fetch failures was in relation to language specific files. My prefered server in 'software sources' was set to 'main server'. I chagned to 'danish server', and now the upgrade didn't stop anymore.

Hope it helps someone.

---

### Post by mhousser on 2007-10-18
Yup, getting the same problem here. The annoying 'Perform a clean install' option, as if that weren't completely out of the question usually, does not apply to me, since I'm attempting this upgrade *after* a fresh 7.04 install.

You'd think traffic issues wouldn't give the bzip error, but maybe it's just an uninformative error message. i guess I'll wait.

Language related, you say? Perhaps I'll try setting my prefered server to somewhere else then..

---

### Post by andlinux on 2007-10-20
Got the same problem, I hope that we find a solution to this problem.

Oh forgot to mention but I changed it to my language (and country) but it didn't worked. it's "be" here (Belgium).

---

### Post by Scooter7 on 2007-10-20
I just sucessfully upgraded to Gutsy this morning with no problems, aside from waiting all day Friday (today's Saturday here in Canada).

So I think it's just a traffic thing, and after a while (maybe in a week or so) everyone should be able to perform the upgrade.

---

### Post by andlinux on 2007-10-23
Ok, I found a way to upgrade.
The only thing I did was this in a console:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

And then started the upgrade...

I found the solution on this website: [https://answers.launchpad.net/ubuntu/+question/15530](https://answers.launchpad.net/ubuntu/+question/15530)

---

