---
title: "Screensavers? in 2009?"
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-12-02
What is happening? I accepted a slew of updates, and suddenly my laptop is showing crazy Windows3.1-style screensavers at every opportunity. I have set Blank Screen for the screensaver, unset Use screensaver when idle, even removed gnome-screensaver, and still this blasted doodling is infecting my screen.

Removed everything with "screensaver"in its name - let's see if that defeats the hideous menace.

Seriously, who thinks it's OK to over-ride my preference not to have screensavers when my screen is idle. It's not as if I had a pre-historic CRT on my laptop......

---

### Post by ranch hand on 2009-12-02
I hope that you filed a bug.

---

### Post by PaulInBHC on 2009-12-02
system>preferences>screensaver click power management click never

---

### Post by davidshere on 2009-12-02
"Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in Launchpad."

---

### Post by lisati on 2009-12-02
> **scradock said:**
>  It's not as if I had a pre-historic CRT on my laptop......

:) 

Screensavers do seem a bit redundant on recently manufactured machines. It's not as if leaving the displayed image static is going to etch an image into the phosphorous....... (Mind you, my old desktop still has a CRT-based display. Now to get any sort of *nix working on it!)

---

### Post by scradock on 2009-12-02
> **PaulInBHC said:**
> system>preferences>screensaver click power management click never
That's what I had - been like that since I started using ubuntu. Now someone has changed it without asking me. Hence the grump.

Besides, the system | preferences | screensaver dialog should be where I set my preferences for screensavers - not another layer deeper in a section called "power management". That should deal with preferences for power management, shouldn't it?

Anyway, removing all programs with "screensaver" in the name seems to have fixed it, for now.

---

### Post by scradock on 2009-12-02
> **davidshere said:**
> "Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in Launchpad."
Not only that, they have explicitly said that persons who post to forums do not represent "normal users", so they have no intention of taking any notice of what we think..........

[Goldarn it I'm grumpy today, aren't I?]

---

### Post by ranch hand on 2009-12-02
I still hope you filed a bug.

---

### Post by scradock on 2009-12-02
> **ranch hand said:**
> I still hope you filed a bug.
OK, I tried - re-installed gnome-screensaver + xscreensaver + xscreensaver-gl, checked that it still ran despite the settings. Found an essentially identical bug filed over a month ago (#467285) and still listed as New, Undecided, Unassigned. No responses or requests for additional information; no sign it had sparked any interest or activity.

Now what?

---

### Post by ranch hand on 2009-12-03
You need to click on the "effects me too" link at the top of the bug page and then leave a comment out lining your problem.

What would be better is, if your apport is working, to run;
```

ubuntu-bug <xxxxxxx>

```for the xxx use what ever the other bug is filed on (hopefully "screensaver" and then follow the dirrections as they come up in launchpad.  You should get the potion for the previous bug and report yours as the same.  This will dump all the information on your box, that relates to the bug, on launchpad.

Along with your comments to clarify the issue this will help.  This, with only one bug filing, must be rare (at least we need to hope so), but the more reports they get the better.  It is not possible for one bug report to be worked on.  They need to know that this really does effect people.

EDIT;
I think that the package would be gnome-screensaver.  Check the other bug.

---

### Post by hikaricore on 2009-12-03
There are still a massive number of CRT displays in use all over the world.
I fail to see how this is relevent to your inability to disable a screensaver.

---

### Post by Merk42 on 2009-12-03
> **hikaricore said:**
> There are still a massive number of CRT displays in use all over the world.
I fail to see how this is relevent to your inability to disable a screensaver.

I thought that the point was that preferences were rewritten, not that screensavers existed.

---

### Post by phenest on 2009-12-03
> **scradock said:**
> What is happening? I accepted a slew of updates, and suddenly my laptop is showing crazy Windows3.1-style screensavers at every opportunity. I have set Blank Screen for the screensaver, unset Use screensaver when idle, even removed gnome-screensaver, and still this blasted doodling is infecting my screen.

Removed everything with "screensaver"in its name - let's see if that defeats the hideous menace.

Seriously, who thinks it's OK to over-ride my preference not to have screensavers when my screen is idle. It's not as if I had a pre-historic CRT on my laptop......

Apart from the fact that LCD's have the same problem as CRT's (albeit to a much lesser degree), I thought that this was something that happens during a development release of Ubuntu, that is, preferences could change to represent the default setting.

---

### Post by scradock on 2009-12-03
> **phenest said:**
> Apart from the fact that LCD's have the same problem as CRT's (albeit to a much lesser degree), I thought that this was something that happens during a development release of Ubuntu, that is, preferences could change to represent the default setting.
Ah, that would explain it.

Actually I had a quick response from Chris Coulson, who led me to discover that gnome-screensaver wasn't actually running; thus NOT disabling the default X screensaver, which was what I was seeing.

The problem may be simply that the gnome-screensaver update a couple of days ago DIDN'T correctly set g-ss to autostart.

That leaves me feeling a bit bewildered at the fact that, if I don't want screensavers, I HAVE to have gnome-screensaver running to prevent the X screensaver from taking over.......

---

### Post by castrojo on 2009-12-03
Why not remove xscreensaver?

---

### Post by scradock on 2009-12-03
> **whiprush said:**
> Why not remove xscreensaver?
Yes, that should also fix it - the temptation to also remove xscreensaver-gl and -data was my undoing, as gnome-screensaver depends on them too. But xscreensaver can indeed be removed by itself, leaving gnome-screensaver safely in control.

---

### Post by avb on 2009-12-04
> **scradock said:**
> Yes, that should also fix it - the temptation to also remove xscreensaver-gl and -data was my undoing, as gnome-screensaver depends on them too. But xscreensaver can indeed be removed by itself, leaving gnome-screensaver safely in control.

fyi, screensavers are used not onlly to save life of your crt monitor. Its main function is to lock and hide the contents of your desktop from other peoples.

---

### Post by lisati on 2009-12-04
> **avb said:**
> fyi, screensavers are used not onlly to save life of your crt monitor. Its main function is to lock and hide the contents of your desktop from other peoples.

I've seen this use of screensavers. Perhaps in time someone will push for a name change. There's also a "TBIC" ("The boss is coming") key in some games.

---

### Post by Kevbert on 2009-12-04
The gnome-screensaver Package has just been updated (to 2.28.0-1ubuntu1) and now gives only two choices (random and blank). Just confirm the bug (#467285) previously reported, then you may get some action.

---

### Post by scradock on 2009-12-04
> **Kevbert said:**
> The gnome-screensaver Package has just been updated (to 2.28.0-1ubuntu1) and now gives only two choices (random and blank). Just confirm the bug (#467285) previously reported, then you may get some action.
That was the update I thought had caused the problem. After some "conversation" Chris C has now marked the bug "Invalid", as it appears that what I was complaining about was the intended behavior. The fix is apparently to remove xcreensaver, which is the fall-back if gnome-screensaver isn't running.

My menu still contains the original choices, as far as I know - though of course without gnome-menus it's hard to get to these days. It certainly did before the breakage.....

---

