---
title: "Infinite loop just before log in prompt"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by trudy_cool on 2009-12-27
I just ran the Karmic Koala upgrade and am now locked out of my system.

At first it would boot up to a blank screen, but I fixed that with the ... ```
i915:modeset=0 acpi=off
``` ... tricks mentioned elsewhere in these forums.

Now I see the startup sequence get itself stuck in an infinte loop:
[LIST=1]
[*]I see the the bruise like splash screen
[*]the screen blanks 
[*]I see a white border box form around a list of the machine's users
[*]screen blanks again
[*]go back to #1 again
[/LIST]

Is there a thread already open on this?  I didn't see one.

I would be very appreciative if someone would advise of the appropriate log file to look at to get a better idea of why this could be happening.

Is there a setting I can use to increase the depth of logging detail one can get at that stage of the boot sequence?

---

### Post by trudy_cool on 2009-12-28
Some new data on this problem ...

On one attempt, I was able to log in and see my desktop ... but then it jumped back to the pre-login screen and fell into the previously mentioned loop.

I'd greatly appreciate some help.

---

### Post by trudy_cool on 2009-12-30
I have found that if I catch GRUB in time and fall out to a login prompt I can reconfigure X11, run startx and get back into my desktop.

Trouble is, it fails after a few minutes.

Can anyone, PLEASE, recommend which logs to look at to see what might have happened?

---

### Post by daklein on 2009-12-30
Hi Trudy,   I can at least commiserate with you.  I think I get the same behavior you describe.   here is what I have tried so far. [http://ubuntuforums.org/showthread.php?t=1368138](http://ubuntuforums.org/showthread.php?t=1368138)
 I can at least get in by selecting a recovery kernel, then command prompt as root,  and then startx works.  but really that's no help for wife & kids who want to use the computer......

So I would also very much like to figure this out.  I wonder if it's a problem with GDM?  

Dale

---

