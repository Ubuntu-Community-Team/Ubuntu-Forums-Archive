---
title: "GDM Update Conflicts"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by doctorzeus on 2010-11-19
Hello,

when I got Ubuntu 10.04 I downloaded all the latest updates and then went through this process:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1571304](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1571304)

(I also added comment to bottom)

I downgraded my GDM to 2.20 so I can have fully customisable login screens again, (I know some people are probably call me an idiot but I like my OS to be fully customisable).

However there is now no options for how I want to boot (e.g. recovery mode and etc) as it just boots directly into GDM.

1) Can you please give me advice on how to fix this?

2) Which System updates should I not install cause I suspect it may stuff up my System?

Any help would be great

Note: As stated at the URL I gave I:

> 
Only thing is I had to move "/etc/init/gdm.conf" to "/etc/init/gdm.bak" otherwise there would be a conflict on startup...


---

### Post by Zookalicious on 2010-11-19
Hi doctorzeus, as I'm sure you're well aware, downgrading to old versions of GDM is not necessarily the best idea :P, but I completely understand where you are coming from with desiring themes. Are the recovery and memtest+ options removed from GRUB2, or do you simply no longer see GRUB2? A little more detail on what's going on here will let us help you better ;)

---

### Post by doctorzeus on 2010-11-19
> **Zookalicious said:**
> Hi doctorzeus, as I'm sure you're well aware, downgrading to old versions of GDM is not necessarily the best idea :P, but I completely understand where you are coming from with desiring themes. Are the recovery and memtest+ options removed from GRUB2, or do you simply no longer see GRUB2? A little more detail on what's going on here will let us help you better ;)

Thanks for the reply,

No I can no longer see Grub2 at all,

it just idles for a sec and then boots straight into GDM..

It boots no problems (apart from no displaying Grub2 of course) but as you can imagine I like to be prepared in case something goes wrong :p cause I won't be able to access memtests or recovery modes..

---

### Post by Zookalicious on 2010-11-19
Of course. Have you tried running 
```

sudo update-grub

```

If that does not make a difference try installing startup-manager
```

sudo apt-get install startup-manager

```

And checking to make sure that there is a timer enabled, so it does not just immediately jump to gdm.

---

### Post by doctorzeus on 2010-11-20
> **Zookalicious said:**
> Of course. Have you tried running 
```

sudo update-grub

```

If that does not make a difference try installing startup-manager
```

sudo apt-get install startup-manager

```

And checking to make sure that there is a timer enabled, so it does not just immediately jump to gdm.

Um I know you were trying to help,

but all that did was make boot time longer and now I can't see any TTY's!!!!

Is there a way to reset it back to how it was before I installed Startup Manager??!

---

### Post by doctorzeus on 2010-11-20
Ok about 1 hour after my last post, system froze and crashed,

Backed up data and re-installed Ubuntu,

spose thats one way to solve the problem but not quite the one I had in mind :p

I may still downgrade GDM, and talk through after that

Is it possible the latest version of Grub isn't compatible with GDM 2.20?

---

### Post by Zookalicious on 2010-11-20
Yikes. None of that should have happened at all. Sorry that that didn't work out for you. In answer to your question it is entirely possible (and likely given this thread) that downgrading GDM causes compatibility issues. I would advise against it, but you're more than welcome to try again as long as you have good backups :P 

Good luck, sorry I couldn't help

---

### Post by doctorzeus on 2010-11-20
> **Zookalicious said:**
> Yikes. None of that should have happened at all. Sorry that that didn't work out for you. In answer to your question it is entirely possible (and likely given this thread) that downgrading GDM causes compatibility issues. I would advise against it, but you're more than welcome to try again as long as you have good backups :P 

Good luck, sorry I couldn't help

That's ok,

on further investigation it seems that GUI boot is disabled on Grub intentionally for compatibility reasons when downgrading...never know someone might develop a fix and I can always use the TTY's if something goes wrong..

---

