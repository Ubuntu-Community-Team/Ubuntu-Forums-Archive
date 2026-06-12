---
title: "LiveCD with Repair Options"
date: 2008-11-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2008-11-06
Ever Lose GRUB or mess up your xorg and had to re-install Ubuntu because you didn't know how to fix it from the CLI?

How about including a bunch of scripts in the Jaunty LiveCD that will do just this automagically so newbies won't freak when one of these common problems arises.

Make them available before starting X on Casper's install menu under a 'Repair Previous Installation' option.

---

### Post by ronacc on 2008-11-06
they can't tell us its impossible because some other distro's have had that for a long time .

---

### Post by plun on 2008-11-07
Yup... really good idea.

Just remove Ekiga which nearly noone uses and add repair functions.

A backup tool for broken PCs would also be nice within a Live CD,  GUI based.

---

### Post by lisati on 2008-11-07
The alternate CDs have a "rescue a broken system" option that has been there for a while.

---

### Post by ronacc on 2008-11-07
the people most likely to need a repair function are the ones least likely to use the alternate install cd . I would guess that there is better than a 90% probability that what they will have onhand is the live cd .

---

### Post by Gina on 2008-11-07
> **ronacc said:**
> the people most likely to need a repair function are the ones least likely to use the alternate install cd . I would guess that there is better than a 90% probability that what they will have onhand is the live cd .+1

---

### Post by Gourgi on 2008-11-07
> **TheForkOfJustice said:**
> Ever Lose GRUB or mess up your xorg and had to re-install Ubuntu because you didn't know how to fix it from the CLI?

How about including a bunch of scripts in the Jaunty LiveCD that will do just this automagically so newbies won't freak when one of these common problems arises.

Make them available before starting X on Casper's install menu under a 'Repair Previous Installation' option.

i agree that would be nice :D

posting an idea in brainstorm and linking back here would be a nice idea ;)

p.s. search if your idea is already in brainstorm

---

### Post by ssam on 2008-11-08
a mode that reinstalled all installed packages might be useful.

---

### Post by pulpo69 on 2008-11-08
i agree ssam.

---

### Post by hellion0 on 2008-11-08
This is a good idea.

---

### Post by RATM_Owns on 2008-11-08
Great idea.
Because really, just about say 10 minutes ago, I broke my GRUB.
I did have to boot into 8.10 CD and reinstall GRUB from the command line, which I'm sure the average new user wouldn't know how to do.

---

### Post by bash on 2008-11-08
I would second an idea like this as well. I don't know how Blueprints submission exactly works, but is it possibly that we users submits blueprints, so the Devs get a hint what we users want? If so I would say we should submit this as a Blueprint.

---

### Post by TheForkOfJustice on 2008-11-08
> **Gourgi said:**
> i agree that would be nice :D

posting an idea in brainstorm and linking back here would be a nice idea ;)

p.s. search if your idea is already in brainstorm

Yeah, it kind of is: 

[http://brainstorm.ubuntu.com/idea/9463/](http://brainstorm.ubuntu.com/idea/9463/)
[http://brainstorm.ubuntu.com/idea/15402/](http://brainstorm.ubuntu.com/idea/15402/)

and there are likely others that suggest a way to fix common OS problems on the liveCD.

---

### Post by TheForkOfJustice on 2008-11-08
Bah.  I added the idea to Brainstorm anyway:

[http://brainstorm.ubuntu.com/idea/15422/](http://brainstorm.ubuntu.com/idea/15422/)

---

### Post by handydan918 on 2008-11-08
> **ssam said:**
> a mode that reinstalled all installed packages might be useful.

The package manager already does that. Search for dpkg set-selections

---

### Post by handydan918 on 2008-11-08
This really is an amazing feature not to have. A little distro called mepis has had it for years.


Maybe Shuttleworth could hire the mepis dev...


nah. mepis uses root.


:)

---

### Post by cariboo on 2008-11-09
Here's a link to the same topic in the Intrepid forum:

[http://ubuntuforums.org/showthread.php?t=851897&highlight=livecd+repair](http://ubuntuforums.org/showthread.php?t=851897&highlight=livecd+repair)

Jim

---

### Post by Lucretius on 2008-11-09
I 100% agree this is a great idea

---

### Post by ssam on 2008-11-09
> **handydan918 said:**
> The package manager already does that. Search for dpkg set-selections

yes. but the point of the rescue cd would that you just select 'fix packages' and it does all the fiddly stuff.
1) mount the disk
2) chroot into broken system
3) figure out whats installed (assume that the apt database might be corrupted)
4) reinstall all packages

---

### Post by TheForkOfJustice on 2008-11-09
I personally don't see how it could be any more than 400kb of extra space.  Just add the option in Casper and add a script that will fix GRUB via command line from mounting the partitions under root and extracting deb packages. There should definitely be no reason to have to load X to fix this problem.

The alternate cd has functions other than rescue functions so that's probably behind its larger size.  Besides, we only need to be able to fix GRUB to test its viability.  Fixing other problems (including xorg) can be done in 'recovery mode' available from GRUB once it has been fixed.

---

### Post by amano on 2008-11-09
And please cover the most likely case:

That you have to reinstall your dual-boot windows, which will remove grub and thus makes Ubuntu inaccessible.

I have a paper under my printer that describes the commands to restore grub (find /boot/grub/stage1, root (hd0,1), setup (hd0) etc.) but that should be done rather on the software side...

---

### Post by TheForkOfJustice on 2008-11-09
> **amano said:**
> And please cover the most likely case:

That you have to reinstall your dual-boot windows, which will remove grub and thus makes Ubuntu inaccessible.

I have a paper under my printer that describes the commands to restore grub (find /boot/grub/stage1, root (hd0,1), setup (hd0) etc.) but that should be done rather on the software side...

All you would have to do is reinstall GRUB after Windows is installed and that problem is fixed (and that is exactly what this thread is proposing: a simple way to restore GRUB from LiveCD).  GRUB automatically adds Windows partitions.

---

### Post by Gina on 2008-11-09
Yes, a simple way to reinstall GRUB - finding all the installed operating systems - would be good.

---

### Post by ronacc on 2008-11-09
> **Gina said:**
> Yes, a simple way to reinstall GRUB - finding all the installed operating systems - would be good.

I would  love just to get ubuntu's grub to find all my other installs , in many years of using Ubuntu this has never worked , I always backup my menu.list to a pendrive before I let ubuntu install grub so I can edit whatever it writes so I can access the rest of my installs .

---

### Post by Gourgi on 2008-11-09
> **TheForkOfJustice said:**
> Yeah, it kind of is: 

[http://brainstorm.ubuntu.com/idea/9463/](http://brainstorm.ubuntu.com/idea/9463/)
[http://brainstorm.ubuntu.com/idea/15402/](http://brainstorm.ubuntu.com/idea/15402/)

and there are likely others that suggest a way to fix common OS problems on the liveCD.

voted all of them :lolflag:

---

### Post by autocrosser on 2008-11-09
Move all the "junk" screensavers to an after install "extra_screensavers.deb" & there would be MORE than enough room ;)

BTW--voted all of them.....

---

### Post by Gina on 2008-11-10
> **ronacc said:**
> I would  love just to get ubuntu's grub to find all my other installs , in many years of using Ubuntu this has never worked , I always backup my menu.list to a pendrive before I let ubuntu install grub so I can edit whatever it writes so I can access the rest of my installs .+1  Yes, I often do it that way or just install another Ubuntu in a minimally sized partition then edit menu.lst using the Grub configfile to point to the other Uuntu menu.lst's.

I'm sure there must be a way to install GRUB without the rest of the distro but I haven't found one yet that works properly.  I thought I was missing something but perhaps not.

---

### Post by of_darkness on 2008-11-11
and a permissions restorer for system critical files..

i have borked upp my system by doing a sudo chmod 0 * in a dir not in the /usr or /bin tree that borked upp things in those trees:P

so in the light of how esay it is to bork upp a linux system by misstake..

so a good repeir cd to repair functions to the most common stuff would bo realy gold worth

---

### Post by ShirishAg75 on 2008-11-12
Makes for interesting read 

[https://fedorahosted.org/firstaidkit/attachment/wiki/WikiStart/firstaidkit-fudcon-en.pdf?format=raw](https://fedorahosted.org/firstaidkit/attachment/wiki/WikiStart/firstaidkit-fudcon-en.pdf?format=raw)

---

