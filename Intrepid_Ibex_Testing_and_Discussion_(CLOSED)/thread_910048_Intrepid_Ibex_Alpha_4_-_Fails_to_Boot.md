---
title: "Intrepid Ibex Alpha 4 - Fails to Boot"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lutin on 2008-09-04
Have been unable to get Alpha4 (amd64) to boot on my Acer Aspire 7003 laptop.

All I ever get is a blank background (no task bars, no icons) and with the mouse cursor in the centre which, by the way, is unmovable.

I've tried numerous times, but get the same result every time.

The machine is otherwise quite happily running Hardy, with all the whistles and bells working as they should.

---

### Post by ronacc on 2008-09-04
try removing quiet and splash from your bootline when you start , that should atleast let you see where it is dying . also search this forum for things to try , there are several "no boot " threads .

---

### Post by Lutin on 2008-09-04
Tried removing the quiet and no splash - no dice.

Not having any luck at all :-(


All I get is the background for the desktop, no taskbars, no icons and a mouse cursor that I cannot move. No keystrokes work either. It just sits there.

---

### Post by ronacc on 2008-09-04
is this something new or has it been this way from the time you installed intrepid ? also how did you install it ? upgrade , livecd or alternate install cd ?

---

### Post by plun on 2008-09-04
Alpha 5 will be out soon...  final tests...:)

---

### Post by Lutin on 2008-09-04
> **ronacc said:**
> is this something new or has it been this way from the time you installed intrepid ? also how did you install it ? upgrade , livecd or alternate install cd ?

This is just trying to get the LiveCD to boot! Never had a problem with any of the earlier LiveCDs, which is why I'm so flumuxed with Intrepid!

---

### Post by ronacc on 2008-09-04
intrepid has been having problems with the live cd from day one , especialy on laptops but even alot of desktops have been having to use the alternate install cd alpha 4 was the first live cd that would work on my fairly generic desktop .

---

### Post by Lutin on 2008-09-04
Doesn't seem like any kind of step forwards to me then.

---

### Post by Slug71 on 2008-09-04
Alpha 5 should be out within a few hours Lutin. Id say wait and give that a try.

---

### Post by ronacc on 2008-09-04
yeah this ride has been kind of ragged but thats what alphas are for , work out the bugs before dumping it on the public , if you are here you should expect problems .

---

### Post by Lutin on 2008-09-04
I understand what you are both saying. It's just that I'm a bit disappointed to have so much trouble with a late Alpha release. I'm fully prepared to expect problems, as you say that's what Alphas are for, but I did at least expect it to boot!

Anyway, Alpha 5 only a short time away. Will try that and see if I'm any more successful.

---

### Post by Gina on 2008-09-04
I now have Intrepid working on three machines (desktops) but won't boot on the laptop - Hardy is fine. Awaiting Alpha 5 and I'll re-install from that with the Alternate CD.

---

### Post by jerrylamos on 2008-09-05
> **Gina said:**
> I now have Intrepid working on three machines (desktops) but won't boot on the laptop - Hardy is fine. Awaiting Alpha 5 and I'll re-install from that with the Alternate CD.

I've got the reverse.  
Alpha 5 works on my laptop, but not Alpha 4.  
Alpha 4 works on my desktop, but not Alpha 5.

Alpha 4 has kernel 2.6.26-5 while Alpha 5 has kernel 2.6.27-2.  If I switch kernels, the failure follows the kernel.

The laptop is 1 gHz IBM Thinkpad R31, Intel graphics.  The desktop is Compaq Presario 3.3 gHz Cleron, ATI graphics.

And yes there are launchpad bug reports for each.

Jerry....

---

