---
title: "A faster software center?"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-04-17
Folks, have you noticed how slow it is to scroll? or are we gonna pretend it's ok.
Also clicking on items (the row with the corresponding app) is somewhat sluggish responding, I also noticed it's written in Python (now the Python fans should start demonizing me and saying that to them its fast enough) - which I'm wary of cause all GUI based apps in Python that I dealt with (and Mono, Java) are sluggish more or less and the devs hate a lot when someone mentions it.

I'm not trolling here, I'm asking if the sluggishness has to do with Python and if this is gonna be fixed.

On a different note, in some future release I hope Debian/Ubuntu will start using apt-fast or some other solution like a "real" database (and not a myriad of files miscalled "database") cause on a typical setup quite soon it gets _really_ slow reading the current "database" before trying to install an app, like 10 seconds with a lot of HDD trashing, a lot of room to improve here too, and no, suggesting buying an SSD is a half backed solution.

---

### Post by BackwardsDown on 2010-04-17
> **kahumba said:**
> On a different note, in some future release I hope Debian/Ubuntu will start using apt-fast or some other solution like a "real" database (and not a myriad of files miscalled "database") cause on a typical setup quite soon it gets _really_ slow reading the current "database" before trying to install an app, like 10 seconds with a lot of HDD trashing, a lot of room to improve here too, and no, suggesting buying an SSD is a half backed solution.

I'm still waiting for that too, as an amateur programmer, it seems that this should not me over-complicated to fix. But probably the difficulty lies in the fact that they don't want extra dependency's in apt-get.

---

### Post by zekopeko on 2010-04-17
> **kahumba said:**
> Folks, have you noticed how slow it is to scroll? or are we gonna pretend it's ok.
Also clicking on items (the row with the corresponding app) is somewhat sluggish responding, I also noticed it's written in Python (now the Python fans should start demonizing me and saying that to them its fast enough) - which I'm wary of cause all GUI based apps in Python that I dealt with (and Mono, Java) are sluggish more or less and the devs hate a lot when someone mentions it.

I'm not trolling here, I'm asking if the sluggishness has to do with Python and if this is gonna be fixed.

I think the sluggishness is a combination of bugs in GTK+ and general Python speed. If you sift through the bugs reports and read the comments you will see that this isn't so clear cut (it may seem to you or me as a simple scrolling list but there is more happening here).

---

### Post by cariboo on 2010-04-17
Check out bug #[lpbug]460366[/lpbug], your questions will be answered.

Seeing as we are late in the testing cycle, most of the bugs have been found and reported. Checking bugs.launchpad.net before posting a question is a good idea.

---

### Post by Lollerke on 2010-04-18
When I go into any category and scroll down I can see it's not fluid (scrolling down and up stutters). If I scroll down a lot with the mouse wheel and then I stop, the list is still scrolling. Anyone else with this problem? Is this a bug?

---

### Post by Uncle Spellbinder on 2010-04-18
Fine here. Scrolling just fine for me.

---

### Post by Lollerke on 2010-04-18
Thanks for the quick reply. Scrolling causes 100% CPU usage for me,so I filled a bug.

---

### Post by kahumba on 2010-04-18
I already started a thread about this:
[http://ubuntuforums.org/showthread.php?t=1456582](http://ubuntuforums.org/showthread.php?t=1456582)

---

### Post by Slorg on 2010-04-18
Honestly, I've got the some problem here...
I don't think it's a bug.

Canonical should be working towards a faster software center in Ubuntu 10.10.

---

### Post by BackwardsDown on 2010-04-18
> **Slorg said:**
> Honestly, I've got the some problem here...
I don't think it's a bug.

If it's bugging you it's a bug ;-)

---

### Post by 23meg on 2010-04-18
Threads merged.

---

### Post by dinamic1 on 2010-04-19
fixed in USC 2.0.2 (at least on my pc)

---

### Post by Slorg on 2010-04-19
> **dinamic1 said:**
> fixed in USC 2.0.2 (at least on my pc)

Honestly, I really did not expect that there would be any improvement for me...

But the latest updates really seems to do the trick, I can now scroll smoothly :) 
It really seems a lot faster now...

---

### Post by Mr. Picklesworth on 2010-04-19
> **kahumba said:**
> Folks, have you noticed how slow it is to scroll? or are we gonna pretend it's ok.
Also clicking on items (the row with the corresponding app) is somewhat sluggish responding, I also noticed it's written in Python (now the Python fans should start demonizing me and saying that to them its fast enough) - which I'm wary of cause all GUI based apps in Python that I dealt with (and Mono, Java) are sluggish more or less and the devs hate a lot when someone mentions it.

I'm not trolling here, I'm asking if the sluggishness has to do with Python and if this is gonna be fixed.

Keep in mind that Python deals with large lists and dictionaries amazingly well, which often compensates for the performance hit of being a scripting language. In this case, I bet that functionality helps ;)

And yep, I'm having the same experience as Slorg. Was sluggish scrolling through lists, but lately it's been far smoother. (Now, if only GTK did animations and a subtle motion blur when scrolling. Mmmm...)

---

