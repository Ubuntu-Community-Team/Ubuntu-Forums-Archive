---
title: "Chrome Flash Buttons Not Responding"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-09-25
I saw several threads about this for firefox, but since this is a Google Chrome thing I thought it should be a different thread.

Most people say that installing the 64-bit flash will fix the problem....and it did, but in FireFox not Chrome.

Anyone know why I can't use any flash buttons in Chrome even with the 64-bit Flash installed?

---

### Post by keenish27 on 2009-09-26
i'm guessing nobody else is having this problem?

---

### Post by joey-elijah on 2009-09-26
> **keenish27 said:**
> i'm guessing nobody else is having this problem?

I do! I thought it was just me...

---

### Post by hugmenot on 2009-09-26
I have this problem in Opera 10.00 on i386. The first click into a flash applet is registered; after that the cursor changes but nothing happens.

---

### Post by | MM | on 2009-09-26
I do as well, but in Opera 10.

---

### Post by meeples on 2009-09-26
i didnt think it has ever worked properly in chrome because flash was only "partially implemented"

so i never thought much of it.

---

### Post by alexmurray on 2009-09-26
I get the same thing - buttons dont work with mouse for flash in chromium - you can use the keyboard (on youtube atleast) to start and stop videos using space though.

---

### Post by keenish27 on 2009-09-27
> **meeples said:**
> i didnt think it has ever worked properly in chrome because flash was only "partially implemented"

so i never thought much of it.

I run it on my laptop and it works fine with the 32 bit version of flash on a 32 bit os install...

---

### Post by ElSlunko on 2009-09-28
I had the same issue in both FF & Chrome. Obviously a Flash related issue. Uninstalled flash from my system (non-free) and now it works! I didn't reinstall. I have no flash program installed and for some reason it still plays flash videos/games.

---

### Post by froggyswamp on 2009-09-28
I have same issue with Chrome x64 & flash x64 on Karmic x64.

---

### Post by dudude on 2009-09-28
I'm have the same problem with Youtube and Hulu videos with both Chromium and Firefox.

If I use Metacity instead of Compiz, I'm able to interact with everything again.

I would use 64 bit Flash, except it kills Firefox whenever it crashes.
I haven't tried the combination of Chromium and 64 bit Flash yet though.

---

### Post by OliW on 2009-09-28
This is true for some video players for me too. But I've found a workaround!

Hold down the right button. Keep holding it down. Then left click somewhere on the page to get rid of the context menu. Now, still holding the right button, left click on flash buttons, etc. It should work.

This isn't great but it's better than having no control over flash.

---

### Post by hugmenot on 2009-09-28
What what it seems like the applet gets the click event but not the release event.
Or something.

---

### Post by Leighman on 2009-09-28
I have this problem in every browser :/
I find that in Opera, if you click outside the flash item for each fresh click you want to make it works fine :P

---

### Post by duanedesign on 2009-10-14
Here is a bug report on the problem.
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

Switching from metacity to compiz makes the bug go away for a lot of people, including me. But this was not a workaround I could use while this gets fixed. But never fear, there is a better way around this bug.
[LIST]
[*]Go to the page with the Flash.
[*]Right-click outside  the Flash content and keep the button depressed
[*]Move your cursor just enough to where a Left-click will cause the menu to go away (still with the Right button held down)
[*]With the Right button held down you can use the Left-click to interact with the Flash buttons as normal. (ex. play and pause your Flash movies)
[/LIST]

---

### Post by OliW on 2009-10-14
> **duanedesign said:**
>  But never fear, there is a better way around this bug.
[LIST]
[*]Go to the page with the Flash.
[*]Right-click outside  the Flash content and keep the button depressed
[*]Move your cursor just enough to where a Left-click will cause the menu to go away (still with the Right button held down)
[*]With the Right button held down you can use the Left-click to interact with the Flash buttons as normal. (ex. play and pause your Flash movies)
[/LIST]

Didn't I just say that a few posts ago?

---

### Post by Prometheus7 on 2009-10-16
> **OliW said:**
> Didn't I just say that a few posts ago?

This is quite an odd workaround -- but it works. Thanks guys.

---

### Post by BrutishSaucer on 2009-10-27
Hey dudes, I found a great work-around!

As long as you have the right mouse button held down, the Flash object correctly detects the left mouse button.  Of course, right-clicking usually brings up some kind of context menu so you will need to left-click out of that menu first.
:popcorn:

---

### Post by VMC on 2009-10-27
> **BrutishSaucer said:**
> Hey dudes, I found a great work-around!

As long as you have the right mouse button held down, the Flash object correctly detects the left mouse button.  Of course, right-clicking usually brings up some kind of context menu so you will need to left-click out of that menu first.
:popcorn:

Déjà Vu

---

