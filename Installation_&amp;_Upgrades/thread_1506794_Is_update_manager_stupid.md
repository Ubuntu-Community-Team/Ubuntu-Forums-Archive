---
title: "Is update manager stupid?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by odobo on 2010-06-10
I have had to install ubuntu several times so I decided to download the dvd so that I wouldn't have to keep downloading all the updates over and over again.  

But update manager doesn't look at the dvd, it goes to the internet.  All the updates in the list of updates are on the dvd, but update manager doesn't bother looking.

Do you really need a question to be asked in order to know what the question is?


How do I make udate manager use the packages that are already on the dvd instead of downloading every time?

---

### Post by SlidingHorn on 2010-06-10
Well, if you installed from the DVD, and it's asking to update the packages, it's likely that the packages on the DVD are outdated.

Either way, (@ least from how I've read your post), the DVD's are for installing, not updating.  if you want, you can probably make a local copy of the repositories.  There's a post [here]("http://ubuntuforums.org/showthread.php?t=20217") from a while back that seems to have figured out how to. [COLOR="Blue"]**Edit:** You might have to make some slight changes to reflect a newer version of Ubuntu, as the thread's from 2005[/COLOR]

You could always google "ubuntu local copy of repositories" (without quotes...or with, your choice i guess) and there should be plenty of results

---

### Post by wilee-nilee on 2010-06-10
> **odobo said:**
> I have had to install ubuntu several times so I decided to download the dvd so that I wouldn't have to keep downloading all the updates over and over again.  

But update manager doesn't look at the dvd, it goes to the internet.  All the updates in the list of updates are on the dvd, but update manager doesn't bother looking.

Do you really need a question to be asked in order to know what the question is?


How do I make udate manager use the packages that are already on the dvd instead of downloading every time?

Your going about running Ubuntu in a nonstandard manner. maybe a little explanation would be helpful.

---

### Post by odobo on 2010-06-10
No, the packages are not outdated, at least the ones I checked.  They're the same as the ones in the repository.  I looked at the thread you posed.  I have no idea what he's talking about.  I'm new to linux.

And anyway, what is the point of making a dvd available, if the installation doesn't even use the dvd?

---

### Post by odobo on 2010-06-10
I don't know enough to know what is standard and what is not standard.  And I also don't know what you want me to explain.

---

### Post by Zemblan on 2010-06-10
If the software installer wants to update some packages it stands to reason that there are differences between the versions on the dvd and in the repos. There are often new versions of something added almost daily, so any DVD copy will quickly become out of date and therefore some packages will need updating. You aren't necessarily forced to update though.

---

### Post by SlidingHorn on 2010-06-10
> **odobo said:**
> I don't know enough to know what is standard and what is not standard.  And I also don't know what you want me to explain.

Your original post doesn't really tell us much.  How did you install Ubuntu, what version, and what packages are trying to update.

As far as I know..the downloadable DVD images are solely for installations, not updates.

---

### Post by odobo on 2010-06-10
> **SlidingHorn said:**
> Your original post doesn't really tell us  much.  How did you install Ubuntu, what version, and what packages are  trying to update.

As far as I know..the downloadable DVD images are solely for  installations, not updates.


Ok, well I downloaded the dvd after having downloaded the CD of 10.04  and installing it.  After installing 10.04 using the cd, I noticed that  many many packages were listed in update manager as software updates,  and they took hours to download and install.  I also noticed after  searching, that there were also dvds available for download, so I  reasoned that the dvds must have some of the packages that were missing  from the cd.  I reasoned this because 700 megabytes is an arbitrary  amount of storage space, and maybe not enough to storing an entire  operating system, so a dvd might have at least more of the hundreds of  packages that took hours to download.  It does in fact have the  packages.  However, the dvd acted exactly the same way as the cd, that  is, it did not install any more or less than when I had used the cd to  install 10.04.  So I downloaded 4.4 gigs of data, only to use 700  megabytes of it when installing 10.04

---

### Post by SlidingHorn on 2010-06-10
> **odobo said:**
> Ok, well I downloaded the dvd after having downloaded the CD of 10.04  and installing it.  After installing 10.04 using the cd, I noticed that  many many packages were listed in update manager as software updates,  and they took hours to download and install.  I also noticed after  searching, that there were also dvds available for download, so I  reasoned that the dvds must have some of the packages that were missing  from the cd.  I reasoned this because 700 megabytes is an arbitrary  amount of storage space, and maybe not enough to storing an entire  operating system, so a dvd might have at least more of the hundreds of  packages that took hours to download.  It does in fact have the  packages.  However, the dvd acted exactly the same way as the cd, that  is, it did not install any more or less than when I had used the cd to  install 10.04.  So I downloaded 4.4 gigs of data, only to use 700  megabytes of it when installing 10.04

The DVD download page:

> Don't be confused, even though DVDs can hold far more data than the typical Ubuntu CD, the main benefit of the DVD downloads is to get access to all of the available language packs. Most people will be fine with the standard CD installer. There are fewer download locations for the DVD images and this list is updated less frequently than for the CD images.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd)

You'll have to install updates after installing *any* OS

---

### Post by kerry_s on 2010-06-10
software sources
or
synaptic-> edit-> add cdrom

---

