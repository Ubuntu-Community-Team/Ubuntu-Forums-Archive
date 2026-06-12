---
title: "When is Plymouth supposed to start?"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by godhika on 2010-03-17
Sorry, I am quite sure that the answer is either burried in one of the blueprints or some of the many Plymouth threads here, but I couldn't find a definitive answer. Most of the time of the boot (I guess about 20 seconds) I only see a black screen with a cursor blinking,after that I see for a split second fsck messages and then the Plymouth screen kicks in for about one or two seconds and then I am going straight to the desktop. I am not sure if this is expected behavior. According to bootchart Plymouth starts way earlier (from reading the bootchart I would even say it starts several times), but I only get a short glimpse of it. I am not complaining because most of the last weeks I had the double login and tty1 issues, so it already improved a lot with the last updates. Just want to check if this is the final behavior or if there is still a bug to file.

---

### Post by VMC on 2010-03-17
Here's some [information]("https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience") on its boot stream activity. 

Its being constantly worked on, as you can see by reading the package [change log]("https://launchpad.net/ubuntu/+source/plymouth/+changelog"). We've had two updates just today alone.

I'm confident they will resolve most , if not all of the issues.

---

### Post by kerry_s on 2010-03-17
i don't see it at all, just black screen all the way then the mouse cursor then the desktop. :x
i had it when i first installed & it was gone after getting up to date.

---

### Post by ndefontenay on 2010-03-17
Very interesting information in this thread.
I will see if anything changes tonight :)

A lot of people are having the cursor issue. I'm pretty sure they will come up with a complete booting experience.

Plymouth replaces usplash for a nicer transition and less screen flickers. 

Therefore, Plymouth being used to look nicer, the cursor will have to be out of the picture at one point. I believe it will be fixed.

---

### Post by VMC on 2010-03-18
> **kerry_s said:**
> i don't see it at all, just black screen all the way then the mouse cursor then the desktop. :x
i had it when i first installed & it was gone after getting up to date.

But you do see it when you shutdown, right? I see the splash on every shutdown, but its hit and miss on whether I see it on boot up.

---

### Post by kerry_s on 2010-03-18
> **VMC said:**
> But you do see it when you shutdown, right? I see the splash on every shutdown, but its hit and miss on whether I see it on boot up.

nope, i see the text terminal login.

---

### Post by PenguinInside on 2010-03-18
Same for me.

Total blank screen to the point that the power saver for the monitor kicks in.

Then the desktop login shows.

I'm sure a newbie would think that something has hung.

---

### Post by chek2fire on 2010-03-19
Same problem here with nvidia driver. No plymouth only text mode and some funky colors to the end until login screen show up.

---

### Post by Owen.C93 on 2010-03-19
There's a [bug her]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108")e with a workaround.

---

