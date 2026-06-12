---
title: "Runlevel 3 (without X) on livecd?"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by Rasputin_III on 2006-05-30
Is there a way to boot the new dapper live cd without starting a gnome/X session?
I've searched around, and the method for earlier releases ("live 3") didn't cut it.
I've also tried assorted switches passed via the "advanced" option, but to no avail.

Any thoughts on making it an official line item on the menu itself?

Ras

---

### Post by Ptero-4 on 2006-05-30
IIRC. There's no command line multiuser runlevel under debian, only singleuser (runlevel 1) and X11 (runlevels 2-5).

---

### Post by ssam on 2006-05-30
Ctrl+alt+f1
```
sudo /etc/init.d/gdm stop
```

---

### Post by mlind on 2006-05-30
[QUOTE=Ptero-4]IIRC. There's no command line multiuser runlevel under debian, only singleuser (runlevel 1) and X11 (runlevels 2-5).[/QUOTE]

yup, that's right.

Rasputin_III, you can configure any runlevel between 2-4 to suit your needs and
use runlevel 5 only for X.

---

### Post by Rasputin_III on 2006-05-30
Right, but those kinds of changes assume an installed OS or remastering the ISO.
I was just wondering if there was a quick 'n easy way of getting as close to a 
full environment as possible without loading X.  

The system I'm dealing with has abysmal specs, and can't really support X11 and
the ramdisk (especially with all the gnome overhead).  I know that knoppix has an
option like that--but didn't really want to download and burn an entire iso just for that
(when it should be possible to do it with ubuntu).

Thanks for the replies thus far,

Ras

---

### Post by ssam on 2006-05-30
what do you need to do on the system?

there are live resuce CD that have textmodes

or damn small linux (50mb download)

---

### Post by Rasputin_III on 2006-05-30
This is a temporary system that I threw together so I'd have a place to put
my "playstation" hard drive.  I have a rather beefy system that I use normally,
but have data I need to back up (off-load) while repartitioning and installing the
official dapper release on thursday.

It's a celeron with some pitiful amount of ram, but all I needed was the ability to
format the drive, and rsync the data from the workstation onto it.
Between the low ram, low horsepower, (and tiny black&white monitor), X and
gnome aren't cutting it.  In fact, just letting it boot into safe-graphics mode (and
X subsequently dying), the rsync I attempted failed and left the system unstable...
Maybe I should just tar the data up, and ftp the file, rendering the whole point moot?

Ras

---

### Post by ssam on 2006-05-30
give damn small linux a go, i think it has all those tools.

---

### Post by Rasputin_III on 2006-05-30
Will do.  Thanks for all the help!

Ras

---

### Post by Ptero-4 on 2006-05-30
A playstation HD. What playstation did you pulled it off (1 or 2)? And How did you do that?

---

### Post by Rasputin_III on 2006-05-30
A playstation 2 (not the slim model)--it came as a bundle with a network adapter when I bought FFXI, but is a standard ide hard drive.

---

### Post by Erujsoft on 2006-08-17
> **ssam said:**
> give damn small linux a go, i think it has all those tools.

Damn small linux, does it have also Resize2fs utility. I want to add additional disk to a logical volume (I use VLM and ext3 filesystem) on a machine with 98Mb of Ram.
Thanks, Jure

---

