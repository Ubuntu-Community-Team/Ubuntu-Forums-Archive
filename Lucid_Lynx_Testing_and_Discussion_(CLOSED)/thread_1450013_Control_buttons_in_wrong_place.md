---
title: "Control buttons in wrong place"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Shadow12313 on 2010-04-08
I've installed ubuntu on my friends laptop and the minimize maximize and exit buttons on are the wrong side of the screen and it's driving him crazy.

It should be a simple fix but, I have yet to find an answer.

---

### Post by Megaptera on 2010-04-08
From this website: [http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28](http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28)

Along with the new theme, the shift in Min/Max/Close buttons from the right corner to the left has caused quite a bit of grumbling from users. While Ubuntu does not currently (as of Beta 1) provide a simple way to reverse this, it can be done from the command line with:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:maximize,minimize,close"

---

### Post by clhsharky on 2010-04-08
HI

Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Sharky

---

### Post by Shadow12313 on 2010-04-08
Thank-you all so much it solved the problem.

---

### Post by lidex on 2010-04-08
> **Shadow12313 said:**
> I've installed ubuntu on my friends laptop and the minimize maximize and exit buttons on are the wrong side of the screen and it's driving him crazy.

It should be a simple fix but, I have yet to find an answer.

You put beta software on his laptop? Better make sure he backs up his data.

---

### Post by AlanR8 on 2010-04-08
Never understood this as a problem as I also use a Mac at home and have got used to the left of screen position where the main menus are as well in Ubuntu.

Just makes sense, you don't have to travel the mouse so far!

---

### Post by lidex on 2010-04-08
> **alanr8 said:**
> never understood this as a problem as i also use a mac at home and have got used to the left of screen position where the main menus are as well in ubuntu.

Just makes sense, you don't have to travel the mouse so far!

+1
I even edited my emerald theme to place buttons on the left.

---

### Post by pipsqueak on 2010-04-08
it took a little getting used to but i actually like it in the upper left...

i read from left to right (of the page)...hence, my eyes tend to first go the top left of a page...going to the right to control the window was awkward for me...

but being a creature of habit, i still needed to break the habit going to the right...

---

### Post by lisati on 2010-04-08
Moved to  Lucid Lynx Testing and Discussion

---

### Post by emarkay on 2010-04-08
Mods, please lock....   :)

---

### Post by lisati on 2010-04-08
Thread closed. There are a number of threads already on the change of the button position, several of which detail what to do if you want to change them back.

---

