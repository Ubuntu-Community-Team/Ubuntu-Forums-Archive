---
title: "Swap Partition Question (No biggie)"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Don1500 on 2009-09-12
I have Ubuntu (Jaunty) running on the same HD (different partition) as Kubuntu (Karmic), would I need a separate Swap partition for each? I don't have two now and everything is working, I just want to know if this is right.

---

### Post by cariboo on 2009-09-12
You can share a swap file with as many distributions as will fit on your hard drive. You're only using one os at a time. so there won't be any conflicts.

---

### Post by FuturePilot on 2009-09-12
Yes, that's fine. As long as you don't try to hibernate one and then try to boot the other.

---

### Post by Seventh Reign on 2009-09-12
> **FuturePilot said:**
> Yes, that's fine. As long as you don't try to hibernate one and then try to boot the other.

Is that even possible on the same computer?  Wouldnt you have to shutdown/reboot to log into the other system?

---

### Post by MacUntu on 2009-09-12
Hibernate = suspend-to-disk(-and-shut-down) and not suspend-to-ram - so yes, that's possible. :)

---

### Post by Seventh Reign on 2009-09-12
Ahh thats right.  I dont use the suspend or hibernate features .. I forgot that when you hibernate, it essentially looks as if your PC is turned off, even tho its not really.

I can see that being a problem if you 'forget' that your PC is hibernating.  Or a friend comes over and hits the power switch and logs into the wrong system.

But what about logging into Windows?  Any good/bad issues with hibernating your Linux system and logging into Windows?  Since it doesnt use the Swap.

---

### Post by FuturePilot on 2009-09-12
> **Seventh Reign said:**
> 
But what about logging into Windows?  Any good/bad issues with hibernating your Linux system and logging into Windows?  Since it doesnt use the Swap.

I've hibernated my system and then booted into Windows a few times. Nothing bad ever happened.

---

### Post by inportb on 2009-09-13
> **Seventh Reign said:**
> when you hibernate, it essentially looks as if your PC is turned off, even tho its not really

O rly? It is pretty amazing then how computers are able to hibernate without power.

---

### Post by forumache on 2009-09-13
Hibernation: computer will save the state of RAM on the disk and power off.
When it will be powered on again, the OS will start booting and, at one point, will look for that memory dump on the disk. If it is found, it will load it => resume from hibernation. If not found, it will continue to boot normally.

Windows uses a file on the C: (hibernation.sys or something), Linux uses swap partition. As you can see, there is no conflict. You can hibernate (i.e. suspend-to-disk) Windows, boot in Linux, hibernate Linux, resume from hibernate Windows, etc.

On the other hand, you cannot use the same swap partition to switch between two hibernating Linux-es. Other than that, no problems.

---

