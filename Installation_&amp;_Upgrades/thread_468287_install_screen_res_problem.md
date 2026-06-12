---
title: "install screen res problem"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by slotman on 2007-06-08
hi folks

i'm new to Ubuntu, and I am having a major problem.

I can't install the system due to my screen resolution being fixed at 800x600 max. I simply can't get past the choose time-zone screen as the bottom of the dialog box is out of view.

I've tried to adjust my settings but the options I get are 800x600 or 640x480...

Here's my hw spec (and yes it's an old system)

1.2GHz AMD Athlon
512mb RAM
17" Samsung Syncmaster display
and most importantly...a 3dfx Voodoo 3 video card

Help!!

Thanks!

---

### Post by slotman on 2007-06-08
......also, my keyboard (PS2) isn't recognised. It locks up.

---

### Post by slotman on 2007-06-08
OK done more research:

Seems this problem is very well known and documented. If Ubuntu wants to be taken seriously as a competitor to Windows then these silly problems have to be sorted out pre-release. How many millions of systems have PS2 keyboards and mice.....

Still not sorted the screen res problem..

---

### Post by slackerov on 2007-06-22
Hi all,

I am also new to Ubuntu and am having the same problem.  I have the ATI Radeon X1300 (256mb) video card.  Any help is greatly appreciated as I am very much looking forward to using Ubuntu.

Thank you,

Slackerov

---

### Post by NeoLithium on 2007-06-22
Install resolution problem - 1, try safe graphics mode, that may give you a better shot.  If that doesn't work, before you boot into the Install Ubuntu screen, alter the boot options and insert **vga=791** on that line, so that it tries to force the size for you.

2nd Person screen resolution problem, you need to give us your graphics card, or check out driver information from a page from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  It walks you through it step by step and makes it quite easy, for the most part.

As for the PS2, Ubuntu is taken seriously by a great deal of users, so there's no need to insult the forum or developers with that.  What version were you trying to install, when the keyboard wouldn't work?

---

### Post by marpstar on 2007-06-22
I just encountered this problem yesterday on an IBM T61.  You need to move both the top and bottom panels to the side.  Once you do this, you should be able to get to the buttons in order to advance to the next screen.

---

### Post by slackerov on 2007-06-26
Thanks guys!  Hopefully I don't have any more problems.  ;)

---

### Post by ColHerb on 2007-07-05
Trying Ubuntu on an older machine with the Samsung 17" CRT I found the same screen resolution problem. It was impossible to see the execution buttons at the bottom right of the screen. I could not figure out where to put in VGA=971 as suggested above. 

My solution: Drag the Menu bar to the left...Drag the Task bar to the right. Drag the Install window to the top of the screen. Under System-Preferences-Fonts change the fonts to 8 point. Click on Details. Play with the Pixels Resolution number in the upper right until you can see the execution buttons. Not very elegant but it worked for me.

The program creators would do us a favor to redesign the install screens to avoid this problem There is plenty of screen real estate that goes to waste.

If possible, be sure a few of the alpha and/or beta testers are NOT very adept and have older equipment. I volunteer.

---

### Post by slackerov on 2007-07-12
I am finally past that screen.  I had to use the way ColHerb did.  Thanks everyone for all the help!  [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)
:popcorn:

---

