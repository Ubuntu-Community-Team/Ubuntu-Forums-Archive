---
title: "gparted failed to create linux partition from edgy desktop cd for dual-boot"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by VCSkier on 2006-11-03
A friend of mine is trying to install Edgy only his Dell laptop.  XP is currently installed, and he wants to dual-boot.

Dell apparently has 2 "hidden" partitions on his hdd, in addition to his XP partition, and gparted wouldn't let us have more than 4 partitions.  So, I had to shrink his Windows partition, then make an "extended partition," and then make an ext3 and a swap (logical) partition inside of it.

He later told me that shortly after he tried to apply the partition changes, he got an error message that, among other things,told him to "try another distro"?!  What could have possibly happened that would cause Ubuntu to tell him to try another distro?

I then looked at his partition setup, and apparently, gparted had successfully shrunk the Windows partition, but had failed to create the new partitions.  Basically, I'm wondering what could have gone wrong, and where I should go from here.  Would I have more luck w/ the "Alternate" install disk?  Or should I set up his partitions using some other utility (other than an Ubuntu install disk)?  I'd like to avoid trial and error, because he's pretty protective of his computer.

Sorry I don't have more details on the error code, but I don't think my friend would want to try the install again just to see it mess up again (unless of course, you guys think it was just a random error, and trying the installation a second time would be successful).  Thanks!

---

### Post by H.E. Pennypacker on 2006-11-03
First, let's begin by ensuring the integrity of his Windows partition.  Is everything still there?

Second, let's try downloading and burning (use a CD-RW if you can) G-Parted by itself, and run the Live CD.   Try doing what you were doing before.

I've never heard of GParted telling people to try another distro, and I am sure it was confusion on part of your friend.  GParted is a Gnome application, and that message doesn't settle well with a Gnome distro like Ubuntu.

Anyhow, try the partitioning using GParted's Live CD, but as always, backup before doing anything.  This applies to anything computer related, regardless of which operating system is at question.

---

### Post by VCSkier on 2006-11-03
I'm download the gparted cd now.  I downloaded the alternative ubuntu install cd last night, in cause someone thinks I should go that route.  Is the gparted live cd more likely to be successful than the gparted that is on ubuntu's desktop cd?  Thanks.

---

### Post by H.E. Pennypacker on 2006-11-05
> Is the gparted live cd more likely to be successful than the gparted that is on ubuntu's desktop cd? Thanks.

There should be no difference.  They're both GParted, and neither are using the harddrive while partitioning is going on.  The Live CD runs using RAM, and therefore, working on the harddrive should be the same.

---

### Post by VCSkier on 2006-11-06
I don't mean to be dumb, but I don't really understand.  If there is no difference, why am I trying the GParted Live CD?  I already know that GParted didn't work from Ubuntu's Desktop CD.  Don't get me wrong, I'm still planning on trying it, I'd just like to understand the logic.  :-D

---

### Post by confused57 on 2006-11-06
> **VCSkier said:**
> I don't mean to be dumb, but I don't really understand.  If there is no difference, why am I trying the GParted Live CD?  I already know that GParted didn't work from Ubuntu's Desktop CD.  Don't get me wrong, I'm still planning on trying it, I'd just like to understand the logic.  :-D
The Gparted live cd has a later version of gparted than the desktop live cd, therefore it has more features...this may explain some of the updated features:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by VCSkier on 2006-11-07
You guys were right.  Thank you so much!  The GParted Live CD worked flawlessly, and rather quickly, as well.  So, I guess it was just a Gparted problem that has been fixed in recent versions.  My friend is now a happy, and very excited new linux user.

By the way, why dosen't Ubuntu's Desktop CD have the latest GParted, because obviously there are significant differences?  :)

---

