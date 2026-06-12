---
title: "Xubuntu Breezy on the XBox - sources.list question"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by mythx on 2008-11-04
Alright, I'm pretty new to this stuff, and I'm hoping this is a general enough question that it's in the right forum.

I installed Xubuntu Breezy on my XBox.  The installation went off w/out a hitch.  Once installed my first course of action was 'apt-get update'.  Which did absolutely nothing.  Took a look at /etc/apt/sources.list, and it was empty.  On a quest to figure out how best to populate this file, I turned to Google and started searching for examples.  Everything I found and tried gave me erros such as the site not being available, or the file not being available.  This problem was consistent until I tried the settings from my vanilla Intrepid installation.  After that, apt-get worked w/out errors.

Half expecting to break it by moving forward with the Intrepid settings, I continued with what I really wanted to do, which was 'apt-get install mythtvfrontend'.  This seemed to be working until it ended in error.  Could not install dependency libc.  Running 'apt-get install libc' gave me:  Segmentation faulty tree.  I'm assuming this is because I'm using Intrepid sources for a Breezy installation.....or does that matter?

I just can't seem to win here.  

Does anyone know how I should populate my sources.list file?  Keep in mind, I'm not a developer, and I'm rather new to linux.  What might be even more helpful would be a good document that describes how I can find what sources I need in the future for when I decide to install something else.

Thanks

---

### Post by snowpine on 2008-11-04
Sorry to break it to you, but...

[http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life](http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life)

Each version of Ubuntu is supported for 18 months, except the long term support versions (such as Hardy) which are supported 3 years.

---

### Post by mythx on 2008-11-04
> **snowpine said:**
> Sorry to break it to you, but...

[http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life](http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life)

Each version of Ubuntu is supported for 18 months, except the long term support versions (such as Hardy) which are supported 3 years.

Well, that's gonna put a kink in my plans.  Anyone with a recomendation on how to get MythTV frontend working on my modified xbox?

---

