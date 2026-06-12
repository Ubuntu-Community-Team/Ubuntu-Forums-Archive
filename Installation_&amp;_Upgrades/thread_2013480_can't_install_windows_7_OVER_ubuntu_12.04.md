---
title: "can't install windows 7 OVER ubuntu 12.04"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by tylerelk on 2012-06-30
I am at my wits end and ready to set fire to my whole house if it ends my computer problems. Here's the story:

My laptop was destroyed two weeks ago and I was left with no device. A friend said he had an old rig that I could have if I got it to work. Here's the hardware specs:

2x Intel Core 2 Duo CPU E8500 @ 3.16 ghz
4gb memory
geforce gtx 260 gpu

We pulled an old 320gb HDD from another system and installed it into this rig I'm trying to fix. After tons of failed attempts at getting windows 7 home premium 64bit I finally tried ubuntu 12.04. The install was flawless and I'm using the system right now. Unfortunately I'm not really feeling this whole linux thing and really want to replace it with windows.

I have all the legit, retail disks and the product key, but I can't get it to install no matter what I try. what happens right now is I'll get just past the windows logo to the install screen. I click "install now" and it just gives me an error message like this:

"Windows could not retrieve information about the disks on this computer."

Then it quits out. I've tried repair installs and all the system recovery tools available from the windows disk. What the hell am I supposed to do now?

---

### Post by leclerc65 on 2012-06-30
Your Ubuntu is probably installed on a EXT4 Partition , which Windows won't want to do anything with it. You need to reformat your HD as NTFS with a Gparted CD or some similar program. Blame MS, not Ubuntu.

---

