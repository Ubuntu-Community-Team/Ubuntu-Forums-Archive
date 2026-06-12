---
title: "Screensaver does not activate"
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-08-09
Screensaver begins to activate (fades to black) and then immediately returns to normal display.  Anyone else?

---

### Post by ronacc on 2008-08-10
screensaver does seem to be having a problem . what I have found so far , some selections don't start at all not even gray out. some do start but take a huge amount of cpu for instance plasma does start and run but takes 100% of both cores of my amd64X2 4600 , skyrocket starts but takes 100% of 1 core .bubble3d starts and takes very little cpu . also the selector seems to forget where you were and is back at blankscreen when you go there to change your selection .

---

### Post by DCMarkie on 2008-08-16
Having the same problem here. Screen fades to black then goes right back to normal. DPMS doesn't seem to activate either.

Running the latest Ibex Alpha.

---

### Post by Goth Mneph on 2008-08-17
same here.  hopefully someone more apt than us can let us in on the secret to a happy screensaver.

good luck all.

edit:
I'm not at home right now so I'll edit this again when I get home.
I got my screensaver to work, yeah!
1. I found on the forum that someone went into the compiz manager and went to the general icon and on the first tab 3/4th the way down there is a box that says something to do with drawing the pixels off the screen. uncheck it.
2. in the screensaver controls there are two times to set at the bottom, again I'll add the specifics later.  the first one says something like blank screen, that is supposed to be for when you want the screen saver to start.  I thought it was for when you wanted the screen to go blank, go figure.

well I hope that helps.

edit number B:

1. compiz config settings manager
   general options
   general (tab)
   untick  Force independent output painting.

2. screensaver preferences
   Blank After (I put 5 minutes)

again, good luck all :)

---

### Post by Nullack on 2008-08-18
We need to include the bug numbers in these discussions - saves everyone time.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/)

Ive confirmed it

---

### Post by Dr.Fritz on 2008-09-20
> **Goth Mneph said:**
> 

1. compiz config settings manager
   general options
   general (tab)
   untick  Force independent output painting.



The correct option that should be unticked is "unredirect Fullscreen windows" that was the workaround i found in the bug forums :) and that worked for me, as i had "Force independent output painting" unticked allready

---

### Post by Lorenz on 2008-09-20
same here, got a grey screen and couldn't get back to desktop. Computer didn't freeze, but I couldn't enter any commands either. I had chosen "random" as screensaver theme, but now I just chose something else and it works now.

---

### Post by kyleabaker on 2008-09-22
I'm also having this problem still. I've unchecked "Unredirect Fullscreen Windows", but it still doesn't seem to be working. I'll leave it unchecked for a while and see if it decideds to start working for some reason.

Intrepid Alpha 6 x64
nVidia - Dual Screen

EDIT:
This does fix the problem. Thanks!
System -> Preferences -> ConpizConfig Settings Manager -> General Options -> General -> Unredirect Fullscreen Windows : Unchecked

---

### Post by mariner09 on 2008-09-28
Thanks much for this one...

My Lenovo T61 would just freeze up with no recourse but to forcefully power off.  This was a problem for me back in Hardy and I could not find the fix.

Looks like Intrepid will be a new frontier for me...

---

### Post by eznet on 2008-10-06
Unchecking "Undirect Fullscreen Windows" under Compiz general settings got me back up and running - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263)

---

### Post by Victormd on 2008-10-11
> **eznet said:**
> Unchecking "Undirect Fullscreen Windows" under Compiz general settings got me back up and running - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263)

Same here!

---

### Post by quazi on 2008-10-13
I had the same problem and just unchecked that option.  Where does one configure the standard screensaver to test if it's fixed?  The compiz screensaver kills compiz for me.  If I click it, compiz crashes back to metacity, and I can't bring compiz back until it's unselected.

---

### Post by wizard10000 on 2008-10-19
> **Dr.Fritz said:**
> The correct option that should be unticked is "unredirect Fullscreen windows" that was the workaround i found in the bug forums :) and that worked for me, as i had "Force independent output painting" unticked allready

This worked for me as well - on two machines.

---

### Post by Hollowman on 2008-10-19
Thanks that worked for me as well.  Now my wife will get off my case for the missing screensaver.   


Hollowman:)

---

