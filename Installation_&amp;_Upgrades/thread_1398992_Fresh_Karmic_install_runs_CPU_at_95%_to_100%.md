---
title: "Fresh Karmic install runs CPU at 95% to 100%"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by oygle on 2010-02-05
Am running karmic on a P2-350 Mhz with 256 Mb RAM. Yes, I know this is an old computer, but it has been very good, performance wise, since versions earlier than 8.x I think.

But now, after a fresh install of karmic, it is very slow at everything. Checked system monitor and CPU is constantly running at between 95% and 100%

Any ideas please ?

Oygle

---

### Post by Grenage on 2010-02-05
If you run 'top', can you identify the process using it?

---

### Post by oygle on 2010-02-05
top showed Xorg to be the highest, but it was only showing between 6% and 10%.  When I then ran gnome-system-monitor, Xorg skyrocketted (monitor was high also) to between 42% and 60%, so with Xorg and system monitor, it was well up in the high 90 perecent CPU.

It seems system monitor uses a lot, but I was using it to try and see why the system was so slow.

swap is 3.3 Gb and not being used, memory is about constant at 50%, it's just the cpu that is high. If I close system monitor, top shows Xorg running at around 6 to 7 perecent.

Just wondering what is slowing it down so much ?

Thanks,

Oygle

---

### Post by Grenage on 2010-02-05
My 'gut' suspicion would be that the machine is simply struggling with the system, considering the CPU specs.

---

### Post by oygle on 2010-02-05
Okay, thanks. It only has a short while to go, before I toss it out, but just noticed quite a difference to previous Ubuntu versions.

---

### Post by Grenage on 2010-02-05
Aye, the gradual advances do take their toll on older machines.  You could always use another distro or window manager on it?

---

### Post by oygle on 2010-02-05
Just noticed one thing. With only top running, Xorg is max at about 5 perecent. Then when I move the mouse foward and back a bit, Xorg jumps to between 20 and 25 percent. I guess that may be normal though ?

Oygle

---

### Post by Grenage on 2010-02-05
I'm surprised it uses that much, but it doesn't sound too high (I am assuming it's a USB mouse).

---

### Post by markbuntu on 2010-02-06
You should try something more lightweight. With 265m ram there is probably a lot of swap going on.

---

### Post by oygle on 2010-02-07
> **Grenage said:**
> I'm surprised it uses that much, but it doesn't sound too high (I am assuming it's a USB mouse).

I'm pretty sure it is a PS/2 mouse. Yes, USB just doesn't work on win95b on that computer (but it does for Ubuntu on same computer).

> **markbuntu said:**
> You should try something more lightweight. With 265m ram there is probably a lot of swap going on.

I was monitoring the swap for a while. It is 3Gb, and there was no acivity. The memory usage was high most of the time, but apparently not high enough to go out to swap. It was mostly CPU that caught my attention.

I'm only using the computer to convert some old Windooze files, then I'll ditch the computer.

Thanks,

Oygle

---

