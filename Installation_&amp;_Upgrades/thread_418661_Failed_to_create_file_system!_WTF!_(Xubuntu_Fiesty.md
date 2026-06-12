---
title: "Failed to create file system!? WTF!? (Xubuntu Fiesty)"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Mochtroid-X on 2007-04-22
I'm trying to do a clean install of Xubuntu 7.04 on my 733Mhz Celeron computer and no matter how I partition my hard drive I get this problem about 15% into the installation:

```
The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.
```

How can I install Xubuntu 7.04 and why does my IDE hard drive come up as a SCSI drive!?

---

### Post by raul_ on 2007-04-22
Try using the Gparted Live CD to partition your disk, and then try again. It's a very handy tool

---

### Post by pedro.wicker.man on 2007-04-25
...or check the answer given at 2007-04-22 here: 

[https://answers.launchpad.net/ubuntu/+question/5296](https://answers.launchpad.net/ubuntu/+question/5296)

That's what i did, and it worked like a charm.

Pedro

(hey, my first post, and I'm helping instead of asking for help! Hurray!)

---

### Post by Mochtroid-X on 2007-04-25
Interesting. I had given up and reinstalled Xubuntu Edgy but I may reconsider after looking into this, thank you. :)

---

### Post by pedro.wicker.man on 2007-04-26
Well, glad i could be of help!

Soon i'll have my own set of questions, and i'm sure you all will help me as well :)

---

### Post by Mrs Harris on 2007-04-26
I'm seeing something similar with Ubuntu... I've posted here but had no response [http://ubuntuforums.org/showthread.php?p=2538261#post2538261](http://ubuntuforums.org/showthread.php?p=2538261#post2538261)

Do you think there's a similar thing I can do on Ubuntu as you did in Kubuntu (I'm at work now so cannot check from here)?

Ta,
Mrs H

---

### Post by mach777 on 2007-04-26
> **Mochtroid-X said:**
> I'm trying to do a clean install of Xubuntu 7.04 on my 733Mhz Celeron computer and no matter how I partition my hard drive I get this problem about 15% into the installation:

```
The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.
```

How can I install Xubuntu 7.04 and why does my IDE hard drive come up as a SCSI drive!?

I had this problem (or a similar one) in ubuntu 7.04.

I resolved it by unmounting all drives and removing all USB drives before running that step in the installer.

---

### Post by pedro.wicker.man on 2007-04-29
> **Mrs Harris said:**
> I'm seeing something similar with Ubuntu... I've posted here but had no response [http://ubuntuforums.org/showthread.php?p=2538261#post2538261](http://ubuntuforums.org/showthread.php?p=2538261#post2538261)

Do you think there's a similar thing I can do on Ubuntu as you did in Kubuntu (I'm at work now so cannot check from here)?

Ta,
Mrs H

Well, i did it on Xubuntu, not Kubuntu, but to get to the point, i haven't installed ubuntu - a geek friend of mine did it on my main pc a couple of months ago, because on this main pc i wanted to maintain the xp partitions and all that, and i was afraid to do it all by myself.

Good luck!

---

### Post by zero-bytez on 2007-05-08
Thanks Pedro, you are a legend...

Luis

---

### Post by pedro.wicker.man on 2007-05-08
You're kidding, right, Luis? :) 

I just found the answer on the forums, i didn't sort it out. 
Heck, I'm having a hard time getting some basic things goin on, as - for instance - writing "ã" (i've got that on a txt file, and i have to paste it every time i need to use it). And i've tried basically everything i've read on the forums. :( 

Oh well... :confused:

---

### Post by raul_ on 2007-05-08
> **pedro.wicker.man said:**
> You're kidding, right, Luis? :) 

I just found the answer on the forums, i didn't sort it out. 
Heck, I'm having a hard time getting some basic things goin on, as - for instance - writing "ã" (i've got that on a txt file, and i have to paste it every time i need to use it). And i've tried basically everything i've read on the forums. :( 

Oh well... :confused:

That's weird. We're kinda neighbours (portuguese here) and I have no problems with ã =\

---

### Post by pedro.wicker.man on 2007-05-10
We're more than neighbours, I'm a Portuguese living in Madrid :D

I've got a spanish keyboard, and after figuring out that x and gnome and whatnot are different things (and i can start a session with different graphic managers or whatever) i finally found one that had all the grpahic changes i asked for on the themes section, and i got my alt gr functioning for #~@€][}{.... but not for ã õ (i'm on xp right now).

And yes, i've tried all the solutions i've found on this forum :(

Oh well...

---

