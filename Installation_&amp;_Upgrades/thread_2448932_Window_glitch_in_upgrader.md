---
title: "Window glitch in upgrader"
date: 2020-08-16
forum: Installation &amp; Upgrades
---

### Post by dustyt on 2020-08-16
Hi, I wanted to report a window glitch in the distribution upgrade.

On two of my machines there have been things no longer needed, supported, etc.

If you click on these to see the details, which I did both times, the window expands down when the list is expanded. But it does not retract when collapsed. The end result is the bottom of the window is out of view because it is so large when you move it all the way up you still can't see it. If you right click the title bar there are no options to resize it or anything. So I was stuck on what should have been a simple graphical upgrade and had to shut down to get rid of the window that I could not move forward from.

Now a partial upgrade is running...

---

### Post by Impavidus on 2020-08-16
If you hold alt, you can drag the window by clicking anywhere in it, not just on the title bar.

---

### Post by dustyt on 2020-08-16
Yeah, but when the window expands larger than your screen is tall, you  can't push the title bar up out of sight so you can see what is on the  bottom, and there was no way that I could find to resize the window. So I  was stuck.

---

### Post by CelticWarrior on 2020-08-18
Maximizing the window actually makes it fit the screen in those cases.

---

### Post by dustyt on 2020-08-18
There are no options to maximize or minimize in the distribution  upgrader. This occurred on a window in the process of upgrading from  19.10 to 20.04

I did remember to right click the title bar of the window, but that didn't work either because the options were grayed out.

---

### Post by CelticWarrior on 2020-08-19
If so that could only happened if you're using the wrong resolution or your monitor has some weird resolution.

---

### Post by Impavidus on 2020-08-19
Sometimes the devs forget that there are still people who use screens that are only 768 pixels high (like my laptop).

---

### Post by dustyt on 2020-08-19
The resolution isn't wrong or weird. This was on a new 15.6" laptop which is a very standard 16:9 ratio. 

The coding for said window is broke. It don't work. Just don't work. It expands out of the viewable screen when you use the list details dropdown that shows you what is on the list of obsolete. And then it will not retract back once you collapse the dropdown. It is very badly coded, end of story. Needs fixing so it is not an issue that causes a new or base user to get confused and give up on linux.

It was not just a one time glitch senario. I was able to reproduce it while upgrading another machine which is a totally different brand and all that. The coding for that window needs debugging. Someone needs to have a look at it. If needed, send it to me and I will have a look.

---

### Post by QIII on 2020-08-20
If this is genuinely a bug, this is not the place to report it.  We are all, Admins and Staff included, end users such as yourself.  We volunteer our time here as we have it to help peers.  We are not Ubuntu developers and we are not employed by Canonical.

Given the nature of this bug (if that is what it is), it may be difficult for you to use the normal bug reporting application.  I might suggest using the mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss) to ask the developers about the issue and how to properly report it if you are not able to use apport/ubuntu-bug.

---

### Post by Impavidus on 2020-08-20
I would call it a bug. But I've never had any difficulty pushing the title bar out of sight when alt-dragging. Maybe that depends on the window manager in use. Anyway, it shouldn't be necessary to drag the window; the window should fit on the screen.

---

