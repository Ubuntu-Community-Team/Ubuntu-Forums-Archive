---
title: "Upgrade to 11.04: Nothing on Startup (no splash, no grub, nothin!)"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by the pearly gates on 2011-05-05
Hi,

I recently installed Xubuntu 11.04 fresh on my machine.  There were some minor freezes that occurred that seem to be pretty common while reading these forums, but other than that it was working great.

A couple of times on restart the computer froze up.  And when I say froze up, *nothing* appeared.  Usually there's a splash screen with the "HP" logo, but in this case it didn't even get that far.  My monitor was black but the orange "idle" power light was on. I had to hold the power button down to shut it off and turn it back on again.  After that it was able to boot up as normal.

I should have taken this as a warning, and it has gotten worse and worse.  Now I'm at the point where I can't even turn the computer on even once to get it back to the desktop.  Like I said, on startup, there is no splash screen, no grub menu, no audible beeps, no blinking cursor, just a black screen.

I bought this off of woot a while back ago, so if you're looking for system specs here they are: [http://www.woot.com/Blog/ViewEntry.aspx?Id=16398](http://www.woot.com/Blog/ViewEntry.aspx?Id=16398)

Also, I read this forum here [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) about graphics errors, but I figured this didn't apply to my case because the users there were able to get to a terminal or the grub boot menu.

What I would like to do is do a fresh install of 10.04 LTS.  Does anyone know of a way that I would be able to do this if I can't even get the HP splash screen to appear in order to boot from a USB stick?

Any help would be greatly appreciated... right now I'm stuck with a brick :(

Thanks,
Tim

---

### Post by the pearly gates on 2011-05-06
Hi, no responses yet so I wanted to see if anyone had a similar problem.

---

### Post by Hedgehog1 on 2011-05-06
If you are not getting the 'beep' from post (Power On Self Test), then your PC on the Fritz.

If you hear nothing at all, and see nothing, there are a few things you can check if this system is a desktop:

Are the power leads properly seating into the mother board?

Are any fans working?

Is there power to eject the CD tray?

If more than the motherboard is not working, it may be the power supply need replacing.  If only the motherboard is not working, it may be the motherboard itself.

***The Hedge***

:KS

---

### Post by the pearly gates on 2011-05-06
> If you are not getting the 'beep' from post (Power On Self Test), then your PC on the Fritz.
Yikes!

> Are the power leads properly seating into the mother board?
Yes, all cables are connected to the motherboard and the light on the motherboard is on.

> 
Are any fans working?

Yup, sure are, all two fans are working.

> 
Is there power to eject the CD tray?

Yes, I can easily eject the CD tray


So it looks like this is a motherboard problem, eh?

---

### Post by MAFoElffen on 2011-05-06
> **the pearly gates said:**
> Yikes!


Yes, all cables are connected to the motherboard and the light on the motherboard is on.


Yup, sure are, all two fans are working.


Yes, I can easily eject the CD tray


So it looks like this is a motherboard problem, eh?
Or related to.  Yes, I agree that is sounds like you are not getting to a point where Grub would boot (as step 1 in my sticky on graphics problems) you're not getting through your BIOS post.

Unfortunately, if you can't even get to a BIOS post, and the Power Supply is good... it doesn't sound good.  The good news is that if the memory and processor are okay, a standard ATX motherboard, with an AM3 socket, integrated graphics  and DDR3 sockets... a replacement OEM motherboard is cheaper the a CPU and memory.  (Just checked- $44 to $180)

---

### Post by kurtburt1001 on 2011-05-07
I've had this happen from time to time with various distros.  Sometimes just unplugging the power source completely for a minute, then reconnecting is enough to get the bios to start.  Have you tried completely disconnecting the power?

---

### Post by MAFoElffen on 2011-05-07
> **kurtburt1001 said:**
> I've had this happen from time to time with various distros.  Sometimes just unplugging the power source completely for a minute, then reconnecting is enough to get the bios to start.  Have you tried completely disconnecting the power?
"Sort of"... meaning when what "kurtburt" is describing, that sometimes happened to me, but it only affected the video card initialising.  You can heard everything "happening" and see the disk activity of it's boot sequence... something with the video popping up at the GDM (sometimes not at all), but still having the sound and such... You "hear" the POST beep and GDM startup sounds.

This, differently, is described as the big "nothing."

---

