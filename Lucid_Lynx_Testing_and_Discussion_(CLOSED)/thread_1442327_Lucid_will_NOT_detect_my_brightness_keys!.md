---
title: "Lucid will NOT detect my brightness keys!"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Hawk__0 on 2010-03-29
I've tried everything.  I know the keys work because at the boot loader and in windows 7 I can adjust the brightness.

Anyways, **xev**, **acpi_listen** and **xbindkeys -k** show nothing when they are pressed.

Computer: Asus UX50V Laptop
Key Combination: Fn/Function + F5/F6

I hope this is a bug and not something I'll always have problems with!  Really liking the beta otherwise :)

---

### Post by Hawk__0 on 2010-03-30
Bump,

I also noticed that if I add the brightness plugin to gnome-panel it glitches out and doesn't really do much of anything...

Could that be related?

---

### Post by Hawk__0 on 2010-03-30
Just a though, could this be a kernel bug? I was reading up on it and apparently it can be.  I notice that the kernel is already "frozen" in the [release schedule]("https://wiki.ubuntu.com/LucidReleaseSchedule"), so this worries me.

---

### Post by Arla on 2010-03-30
Did they used to work in any prior release? Reason I ask, my Lenovo laptop it's never worked on (in Ubuntu, works fine in Windows 7) I believe this was noted as basically hardware issues, there are some fixes out there that allow this to work, not sure if you've tried any of those.

---

### Post by Hawk__0 on 2010-03-30
Fixes? I haven't tried any, I don't know where they are.  I actually just got this laptop.  Ubuntu 9.10 wouldn't boot the live CD (got some text that kept repeating itself super fast so I couldn't read it.  It happened indefinitely) and I tried kubuntu 10.04 alpha (wireless half-worked) then I tried 10.04 beta and everything works except this, and my backlight keyboard (but that's a different thread/story)

---

### Post by bash on 2010-03-30
It's not completly uncommon that special laptops key are not recognized. Is this your first Linux distribution? Or have you tried others before and the keys worked there? Might tried to just generally do a Google search with your laptop name and "linux + function keys" or something along those lines. Maybe someone else with your model has had the same issues before.

---

### Post by Hawk__0 on 2010-03-31
On this laptop it is my first, since I got it only 2 weeks ago.  I know the keys work.  They work before and at the bootloader, and they work in windows.

Tried google to no avail.  Also, do you know what asus express gateway is? I just tried it a few days ago... it's asus' 5 second boot linux OS that gets you skype, firefox, and a couple other things.  everything works in it! How come not in ubuntu?

---

### Post by FlyingIsFun1217 on 2010-03-31
It seems all too common that ASUS brightness keys don't work in linux. The ExpressGate utility is really just a VERY small custom version of linux that your computer is supposed to be able to boot fast for quick work, and if your computer is the same as mine, you'll notice your brightness keys don't work in that version of linux either.

Often, the keys will work in Windows, but not in linux. It sucks, yes, but it seems to be the case. It seems that the way they work is different than normal keys (the actual route they take to make the monitor's brightness change).

The best thing you can do is file a bug report to try and bring more attention to this problem.

FlyingIsFun1217

---

### Post by Hawk__0 on 2010-04-01
My brightness keys work fine in express gateway.  There MUSt be a way to get this to work!!!

---

