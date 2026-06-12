---
title: "Lucid Fresh Install"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by beegary on 2010-04-03
Im eager to start using Lucid, but have a couple of concerns.....

1. If I install now will it auto-upgrade when the 'full' release comesout at the end of the month.

2. I want to start a fresh as I have bee tinkering and installing all sorts on my Karmic install is there anything I should be wary of as I have /home as a separate partition:
[SIZE=1]```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8601af91-ae66-4684-8488-2e2b9e24c514 /               ext4    errors=remount-ro 0       1
# /bee_media was on /dev/sda4 during installation
UUID=c90b50a8-e5d3-42b4-b82f-c1fb810da179 /bee_media      ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=6dcf7d6b-b045-457c-8a92-6242c6a06284 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=5961768d-b1d9-4d14-8fd1-e405c9e774da none            swap    sw              0       0
```[/SIZE]

3. Is there better mobile phone support in Lucid?

Cheers

---

### Post by howefield on 2010-04-03
> **beegary said:**
> If I install now will it auto-upgrade when the 'full' release comesout at the end of the month.

By updating with Update Manager, you will have the final release

> I want to start a fresh as I have bee tinkering and installing all sorts on my Karmic install is there anything I should be wary of as I have /home as a separate partition

If you want to keep your current /home,. select manual partioning during the install, and mount /home but do not mark it for formatting.

> Is there better mobile phone support in Lucid?

Don't know, although I don't think I have seen mobile phone support specifically mentioned anywhere in regard to Lucid.

---

### Post by beegary on 2010-04-03
Thank you, think I may do a fresh install this weekend as I have the time.

---

### Post by howefield on 2010-04-03
Remember that as a Beta release, you may encounter breakage, so ensure that your data is safely backed up before starting :)

---

### Post by _khAttAm_ on 2010-04-03
> **beegary said:**
> Thank you, think I may do a fresh install this weekend as I have the time.

It is better to wait for Final Release.

BTW, I have been using Lucid since 1st Alpha (upgrade from Karmic) and have been encountering small problems time and again. Hope Final Release has it all fixed.

---

### Post by sdowney717 on 2010-04-03
> I have /home as a separate partition 

well then upgrading should not be much of a worry about losing your home.

If you have a separate 'home partition', can you boot multiple linux OS's and each one use that 'home partition' while it is running.? 
Are there any restrictions on this?

---

### Post by beegary on 2010-04-03
> **_khAttAm_ said:**
> It is better to wait for Final Release.

BTW, I have been using Lucid since 1st Alpha (upgrade from Karmic) and have been encountering small problems time and again. Hope Final Release has it all fixed.

Im not that bothered about a bit of breakage, with the support of this forum I normally manage to get things moving again!!!
Ill let you know how I get on!!

---

### Post by ranch hand on 2010-04-03
When using a shared /home it is important to use a different user name with each OS.  There are a lot of config files on your /home partition and you do not want different OS' configurations conflicting with each other.  Separate user names prevents that problem.

They can all use the same files but they need there own conf files.

Have FUN.

---

### Post by beegary on 2010-04-03
> **ranch hand said:**
> When using a shared /home it is important to use a different user name with each OS.  There are a lot of config files on your /home partition and you do not want different OS' configurations conflicting with each other.  Separate user names prevents that problem.


Luckily I only have 1 user! But im glad i am aware of this for the future.

I have successfully installed Lucid! beta1 I think?

I have managed to maintain my /home and the /media partition I had. I deleted allot of the .conf folders I had in /home as I really just wanted to start again. The only thing i kept was my .mozilla folder and hence my Firefox is setup as before.

1st impressions is that I love it! Graphically on my NC10 everything looks sooooo much nicer

---

### Post by sprince09 on 2010-04-03
I also have /home mounted separately, but whenever I upgrade I delete all the old hidden files/folders in my home folder, just to make sure there's no conflicts with new versions of various programs and their previously configured configuration files.

---

