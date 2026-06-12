---
title: "Fresh install of Feisty isn't so feisty"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by davidcoffield on 2007-05-02
Hi,

I just downloaded Ubuntu 7.04, burned my ISO image, popped in the CD and booted the PC (it's an old PC, the hard disk is blank). Start or Install Ubuntu, off it goes and does stuff - looking promising - and then something like 

Nautilus can't be used now, due to an unexpected error from Bonobo 

and the PC just sort of sits there. I (not it) timed out after 15 mins of it just sitting there.

What to do to resolve the error?

Is the PC still loading something - how can I tell?

Thanks,
David

PS I used to have Dapper Drake and it all worked fine. Same PC.

---

### Post by garlik42 on 2007-05-02
On the boot menu pick the safe graphics boot. You may have a video card related issue.

---

### Post by davidcoffield on 2007-05-02
Hi,

Nope, that just pops up a weird red box with Out of Range H46Khz V86Hz, Max 1280 x 1024.

The monitor is running at 1024 x 768 which I'd have thought was pretty standard and not Out of Range.

Any other thoughts?

Many thanks,
David.

---

### Post by garlik42 on 2007-05-03
It sounds to me like there is a video issue, you might need to use the alternate install cd, which I believe (I have not used it) works in text mode.

I'm curious, what kind of video hardware are you running ? Card/monitor ?

---

### Post by nevernamed on 2007-05-09
I get the same error message, but I've been running ubuntu in the past.
I have  a dell latitude c840 and previously it has had problems getting linux on it but these forums always help me when I'm stumped!

So I booted using the "driver update" option on the boot menu, because using the standard install was giving some sort of error when I started ubuquity (even sudo ubiquity) and it would keep crashing. So when I tried it with driver update everything seemed to be working fine.

Then I went to login and I got the error. What the heck is bonobo anyway?

Does anybody have any ideas on how to fix this?

---

### Post by stchman on 2007-05-09
> **davidcoffield said:**
> Hi,

I just downloaded Ubuntu 7.04, burned my ISO image, popped in the CD and booted the PC (it's an old PC, the hard disk is blank). Start or Install Ubuntu, off it goes and does stuff - looking promising - and then something like 

Nautilus can't be used now, due to an unexpected error from Bonobo 

and the PC just sort of sits there. I (not it) timed out after 15 mins of it just sitting there.

What to do to resolve the error?

Is the PC still loading something - how can I tell?

Thanks,
David

PS I used to have Dapper Drake and it all worked fine. Same PC.

What kind of PC.  The LiveCD for Ubuntu requires at least 256MB of RAM.  I have an older PC that would not install Ubuntu at all until I put more memory in it.

---

### Post by PRAEst76 on 2007-06-18
I'm having the same problem and my girlfriend isn't. We both use gnome on the same machine. I'm suspecting some kind of conf issue. I've already done ```
rm -Rf .gnome*
``` and ```
rm -Rf .gconf*
``` so I'm thinking it's not with either of those.

Is there anything that may be bothering bonobo?

---

### Post by Pumalite on 2007-06-18
> **PRAEst76 said:**
> I'm having the same problem and my girlfriend isn't. We both use gnome on the same machine. I'm suspecting some kind of conf issue. I've already done ```
rm -Rf .gnome*
``` and ```
rm -Rf .gconf*
``` so I'm thinking it's not with either of those.

Is there anything that may be bothering bonobo?

You said disk is 'blank'. Good idea would be to use Gparted. Make one LARGE partitioned of the entire disk formatted ext3. Pop in your live cd. During installation, use: 'Guided>Use Entire Disk'

---

