---
title: "No Kubuntu Karmic for me"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stuart.reinke on 2009-10-24
I'm wondering if the Karmic and KDE combo is going to have issues with ATi video cards. 

I haven't been able to get a usable desktop from either Beta or RC. 

I've tried a thread in Testing and Development. ([http://ubuntuforums.org/showthread.php?t=1299846]("http://ubuntuforums.org/showthread.php?t=1299846")) No luck.:(

Anybody else have the same trouble?

I'm hoping it works by the time final release comes out.

---

### Post by TwiceOver on 2009-10-24
I've tried Kubuntu Karmic on both my laptop and desktop (both intel graphics) and everything is just slow (even after reverting to intel 2.4 drivers).  Looks really nice, and I have wanted to try to make the switch to KDE, but not with as slow as it is on my hardware.

---

### Post by hoppipolla on 2009-10-24
Surely as long as you've got the right drivers for your card, that's all that matters right?

Besides you can always turn off compositing, but I don't see why you would have to so long as you get the correct driver!

---

### Post by stuart.reinke on 2009-10-24
Kubuntu Jaunty works just fine on my laptop. That's what has me cofused, I wonder what is different in Karmic that makes KDE 4.3 not work. Karmic with Gnome works just fine.

---

### Post by Skripka on 2009-10-24
> **stuart.reinke said:**
> Kubuntu Jaunty works just fine on my laptop. That's what has me cofused, I wonder what is different in Karmic that makes KDE 4.3 not work. Karmic with Gnome works just fine.

Only thing of importance should be gfx different drivers....which can make all the difference.  What kinda GPU do you have?

---

### Post by hoppipolla on 2009-10-24
> **stuart.reinke said:**
> Kubuntu Jaunty works just fine on my laptop. That's what has me cofused, I wonder what is different in Karmic that makes KDE 4.3 not work. Karmic with Gnome works just fine.

very weird. Like I say check your drivers, other than that what else could be affecting it?

---

### Post by stuart.reinke on 2009-10-24
I also thought driver issue. 

Is the installer not detecting my card correctly?

Is there a way to tell the installer to install a specific driver? 
(desktop is totally unusable)

---

### Post by stuart.reinke on 2009-10-24
> **Skripka said:**
> Only thing of importance should be gfx different drivers....which can make all the difference.  What kinda GPU do you have?

sorry if this is a dumb question but what is a GPU?

This is what I have for a graphics card:

```
stuart@stuart-laptop:~$ lspci | grep "VGA"
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

---

### Post by -grubby on 2009-10-24
> **stuart.reinke said:**
> sorry if this is a dumb question but what is a GPU?

A video card

---

### Post by unknownPoster on 2009-10-24
> **-grubby said:**
> A video card

More specifically, a Graphics Processing Unit.

[http://en.wikipedia.org/wiki/Gpu](http://en.wikipedia.org/wiki/Gpu)

---

### Post by Skripka on 2009-10-24
> **stuart.reinke said:**
> sorry if this is a dumb question but what is a GPU?

This is what I have for a graphics card:

```
stuart@stuart-laptop:~$ lspci | grep "VGA"
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

Try the Radeon (Open source) drivers.  Fglrx/amdcccle (ATi proprietary driver) does not support cards as old as yours, IIRC.

---

### Post by stuart.reinke on 2009-10-24
> **Skripka said:**
> Try the Radeon (Open source) drivers.  Fglrx/amdcccle (ATi proprietary driver) does not support cards as old as yours, IIRC.

How do I switch drivers?  It will have to be done during install.

---

### Post by Chad5ter on 2009-10-24
> **stuart.reinke said:**
> How do I switch drivers?  It will have to be done during install.
I'm new here, but I think it's the same way I went to my Wireless Card driver;
System->Administration->Hardware Drivers

You have to remove your Proprietary driver, restart. Then, return back and choose open's one. Restart again and it should be good.

Unfortunately, I don't know the command lines.

All best,
Chad

---

### Post by hoppipolla on 2009-10-25
It's so weird that it works with Gnome (and Compiz right?) and not with KDE... I can't explain that at ALL!

There might be some deep dark hidden away setting pertaining to the way the desktop is displayed that is set to an option less preferable for your hardware/drivers o.O

Then again if you're just having it on Karmic then even that doesn't make too much sense. You could also try a different kernel? Like an older one? o.O


EDIT -- Sorry I just read to the end - yeah follow people's advice and try a different driver :)

---

