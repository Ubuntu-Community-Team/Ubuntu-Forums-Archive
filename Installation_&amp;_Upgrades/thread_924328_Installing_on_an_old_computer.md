---
title: "Installing on an old computer"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by amphibious1 on 2008-09-19
I have tried to install on my old computer. I've made several cd's with different isos(alternative xubuntu 7/8, fluxbuntu 7) and everytime I'd try to install I'd get errors saying that modules couldn't load or whatnot. I tried one of the cd's on a newer computer and it worked fine. Is there anything I can do that might get it to work on this computer?

I have an old etower with 64mb ram and a 10gb hdd

---

### Post by oilchangeguy on 2008-09-19
> **amphibious1 said:**
> I have tried to install on my old computer. I've made several cd's with different isos(alternative xubuntu 7/8, fluxbuntu 7) and everytime I'd try to install I'd get errors saying that modules couldn't load or whatnot. I tried one of the cd's on a newer computer and it worked fine. Is there anything I can do that might get it to work on this computer?

I have an old etower with 64mb ram and a 10gb hdd

use puppy linux, or damn small linux. what is you are wanting to do with this antique?

---

### Post by shultzjr on 2008-09-19
Add ram, you probably do not meet the minimums for hardwware specs or your hardware is having problems.

later....

---

### Post by snowpine on 2008-09-19
64mb is too small for anything ending in -buntu. Puppy, DSL, or SliTaz (the loram flavor) are probably your best options.

---

### Post by Vivaldi Gloria on 2008-09-20
OS for old computers: [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575456") - [[COLOR="Sienna"]floppy[/COLOR]]("http://www.linuxlinks.com/Distributions/Floppy/")

---

### Post by Sef on 2008-09-20
There is also [Deli Linux]("http://delilinux.org").

---

### Post by Pumalite on 2008-09-20
And a Minimal Installation:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Vivaldi Gloria on 2008-09-20
> **Pumalite said:**
> And a Minimal Installation:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

See also CLI in my sig.

---

### Post by Sorivenul on 2008-09-20
> **Sef said:**
> There is also [Deli Linux]("http://delilinux.org").
+1.  SliTaz (loram edition) is also great on machines with specs similar to yours.

---

### Post by Atsuko on 2008-09-21
> **Pumalite said:**
> And a Minimal Installation:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Wish I would of known this Saturday, I ended up using the debian-40r4a-i386-xfce-CD-1.iso .
That work fine after burning four disk and getting one the cdrom would take. lol

---

### Post by Pumalite on 2008-09-21
You can still give Minimal a try.

---

### Post by snowpine on 2008-09-21
> **Pumalite said:**
> You can still give Minimal a try.

I've never had much luck installing Ubuntu 8.04 Minimal on my virtual machines with 64mb. I ran into the problem described in this bug report: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

Do you know a good workaround for that bug Pumalite?

---

### Post by Pumalite on 2008-09-21
Have you tried Fluxbuntu?

---

### Post by snowpine on 2008-09-21
> **Pumalite said:**
> Have you tried Fluxbuntu?

Of course I have tried Fluxbuntu! :)
Fluxbuntu is based on 7.10, not 8.04, and so does not suffer from the 64mb Hardy installer bug that I linked to in my previous post. 

However, I did have a problem getting the Fluxbuntu terminal to work correctly on 64mb (if anyone knows the solution, I'd appreciate if you'd reply to my thread here: [http://ubuntuforums.org/showthread.php?t=882096](http://ubuntuforums.org/showthread.php?t=882096)). It does install okay on 96mb (or more). 

Therefore, based on my experience, I would not recommend Fluxbuntu (or anything in the Ubuntu 8.04 family) on the OP's 64mb computer.

---

### Post by Pumalite on 2008-09-21
I agree that DSL or Puppy would be more appropriate.

---

