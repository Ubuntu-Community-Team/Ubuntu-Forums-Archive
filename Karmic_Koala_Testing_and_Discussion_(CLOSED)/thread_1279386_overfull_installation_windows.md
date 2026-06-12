---
title: "overfull installation windows"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roger E Critchlow Jr on 2009-09-30
I've been testing from an upgraded jaunty for a while, but I just tried a clean install of alpha6 to see if it addresses some other problems.

When I got to the disk partitioning dialog, the window resized itself so that all of the response buttons were off the right hand side of the screen.   Because the install process runs in full screen mode, there was no way to move or scroll the window to see the off screen buttons.  gThe install process decided to keep that window size for the rest of the install, so I was blindly clicking and hitting return to get through the screens.  This would have been a disaster if I didn't know the installation process by heart.

This has been an issue in earlier releases, because I'm almost always installing to a laptop, and I've filed bugs about it before, and it's pretty annoying to see the install regressing to this completely useless state.

Who gets this bug?  I mean as in which package does this bug get filed against?  

An install dialog where the buttons to continue, backtrack, and cancel the install process are invisible is not user friendly.

-- rec --

---

### Post by Roger E Critchlow Jr on 2009-10-02
Bump, de bump.

This is still an issue with the Beta release.  From installation window 4 of 6 onward the [cancel][back][forward] buttons are positioned off screen with no way to move them on screen.  The only way to finish the install is to know what the buttons are and how to blindly focus and activate the buttons with the keyboard.

I have 8 partitlons on my hard drive, 6 with bootable operating systems.  When the partitioner goes to draw the pretty colored picture of what's on my drive, it ends up labelling the colors with long names like "ubuntu 9.10 development, kernel-2.6.31-11-generic".  It puts all the labels on one line with the result that the line is much wider than the screen.   I see this time that it actually puts a scroll bar in so I can scroll the disk cartoon with its labels, but it miscomputed the sizes:  the scrollable window is still wider than the screen, so it doesn't fit; the scrolled window is wider than the area set for scrolling, so I can scroll part of the cartoon on screen but not all of it.

In any case, the overall install window is resized larger than the screen and the buttons that control the installation process are invisible to the user.

Which package do I report this bug against?  Hint:  it isn't named "ubuntu-installer".

---

### Post by cariboo on 2009-10-02
If you boot to the desktop with the Live CD and then select install the windows are much smaller, you don't have to guess where the buttons are.

---

### Post by Roger E Critchlow Jr on 2009-10-02
Then maybe there should be no Install option on the live CD boot menu?

-- rec --

---

