---
title: "Green screen after upgrade from Jaunty to Karmic"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TPirog on 2009-06-26
Video died on upgrade to Karmic Koala (from Jaunty). Ideas anyone, please? I do not want to reinstall!
 
I just get a green screen. :confused:
 
Thanks.

Tony

---

### Post by Therion on 2009-06-26
> **TPirog said:**
> I just get a green screen.
nVidia user, huh?  Okay, sorry, couldn't help myself.

You did an **online upgrade** to an **alpha-release**???  Wow... you were BEGGING for trouble from the get-go.

Try booting using the Recovery kernel.  That's what helped me track down the fact that my printer (believe it or not) was the source of the same problem for me just a few days ago.  Although my screen was more of a burnt umber sort of color.

---

### Post by cmwslw on 2009-06-26
> **TPirog said:**
> Video died on upgrade to Karmic Koala (from Jaunty). Ideas anyone, please? I do not want to reinstall!
 
I just get a green screen. :confused:
 
Thanks.

Tony

THis is a prime example of why one should NOT upgrade their main desktop to a development version of an OS. Especially in only Alpha 2. There is not really a way to revert, so all i can suggest is to backup your home and reinstall to jaunty. This problem is a bug the recent 2.6.30.10 kernel that karmic just incorperated.

[http://nuclear-imaging.info/site_content/tag/green-screen-of-death/](http://nuclear-imaging.info/site_content/tag/green-screen-of-death/)

EDIT: see if GRUB allows you to boot from an earlier kernel - that should allow you to boot

---

### Post by TPirog on 2009-06-26
I agree. I was stupid, and i am appropriately ashamed. LOL. Especially since I do have a test desktoip i coudl have done it on. (Cringe.) ](*,)

Can I find instructions anywhere for backing up my system (home) when in this state please? :confused:

Thank you.

Tony

---

### Post by TPirog on 2009-06-26
If I get no replies, I can reinstall. I'll just boot off the 9.04 cd and copy off my files first. Such a life! 
 
I'm just concerned about multi OS's. I have two drives: one with XP on it and the other with Linux. Hope the partitioner can figure out to replace the old Ubuntu with the new one gracefully. 
 
I just was so enamored of Ubuntu that I believed it could never be killed a la Windows. Live and learn.

---

### Post by TPirog on 2009-06-26
> **cmwslw said:**
> 
[http://nuclear-imaging.info/site_content/tag/green-screen-of-death/](http://nuclear-imaging.info/site_content/tag/green-screen-of-death/)
 
EDIT: see if GRUB allows you to boot from an earlier kernel - that should allow you to boot
 
I'll try and and (per: [COLOR=#339966]The newer kernel 2.6.30-10 has been fixed. It boots and functions normally now.[/COLOR]) see if I can get update manager to fix me.

---

### Post by TPirog on 2009-06-26
Oooh! I'm gong to install Ubuntu Server!!! Yes!

---

### Post by khelben1979 on 2009-06-26
From my experience with Debian I never ever have all the troubles which I constantly see on this Ubuntu forum. More users should learn the virtue of true [patience]("http://en.wikipedia.org/wiki/Patience"). Look for my signature and you'll see what I mean.

---

