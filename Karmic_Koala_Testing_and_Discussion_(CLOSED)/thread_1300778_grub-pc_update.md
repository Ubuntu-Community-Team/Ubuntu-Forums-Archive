---
title: "grub-pc update"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Goofee691 on 2009-10-25
hi everyone I just tried to upgrade to the latest grub-pc offered with update manager and while it try's to update the package it sits trying to configure it.

I used ctrl-c to stop it and then remove grub altogether and then reinstall grub with a fresh configuration with the same result

update-grub still works in a terminal however

is my bootloader actually functioning or should I not restart my computer

---

### Post by ranch hand on 2009-10-25
I would do three things.
One>run this;
```

sudo dpkg --configure -a

```
Hopefully this will do nothing and you will just go back to you prompt.  If something is stuck, though, this should clear it.
Two>go to synaptic and search for "grub".  Look to see if grub-common and grub-pc are marked as installed.
Three>run'
```

sudo update-grub

```
I know you said it works in terminal.  Another check will not hurt.

I do not use Update Mangler at all on any of my installs (lots).  I prefer using synaptic.

That said, UM should be work after the Final Release.  Read the sticky.  It is about partial upgrades but points up the problems that UM has in relation to "testing" phase releases.  I am surprised that it is having problems at this stage of the game.

---

### Post by Goofee691 on 2009-10-25
ok I tried to continue it but it just sat for at least 3 hours now trying to configure grub-pc

I thought that at this point that UM shouldn't have many problems and the update was not marked as a partial upgrade

---

### Post by ranch hand on 2009-10-26
I wouldn't expect it to be a problem either but, as I said, I don't use it.  You can't completely remove it easily, as that removes things I want but I removed most of it here on Jaunty.

The 9.10 installs still have it and I have had them going back to A1, but I have never even looked at it. 

Just don't like it.  Don't even really know why.

What happened when you ran "sudo dpkg --configure -a"?

I assume you did that before starting UM again.

---

### Post by Goofee691 on 2009-10-26
when I run

> sudo dpkg --configure -a

all I get is until I break it with ctrl-c.

> Setting up grub-pc (1.97~beta4-1ubuntu3) ...


this will happen if I try to install any other software or basically anything that involves installing or removing software.

I also did restart my computer today and it restarted without a problem but this problem still exists with the package

---

### Post by ranch hand on 2009-10-27
I would first;
```

ubuntu-bug dpkg

```
and follow the directions.

Then I would go to bed before giving bad advice from lock of sleep,  I can't hardly type.  h ave a guy picking me up to wean and sort and ship calves in the morning at 6.

Sorry, all I would do is something silly.

---

