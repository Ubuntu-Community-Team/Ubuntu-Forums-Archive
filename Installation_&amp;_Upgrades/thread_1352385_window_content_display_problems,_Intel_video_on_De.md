---
title: "window content display problems, Intel video on DellD620"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by noSelf on 2009-12-11
i upgraded my Dell D620 laptop from Jaunty to Karmic (32-bit). 

Video hardware according to lspci is: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

kernel 2.6.31-16

i had the "white screen of death" problem after the upgrade, which was fixed after installing xserver-xorg-video-intel from the recovery console.

Now i have a really frustrating problem of window content not displaying properly in lists and tabs. Specifically:

- lists, such as in the "Processes" tab of System Monitor, or Nautilus windows in list view, or the list of apps in Startup Manager, don't display correctly. They generally apprear blank, and i need to drag the mouse over the content area to display the contents - and the display doesn't "stick" reliably. It seems like the content area isn't updating properly (System Monitor updates the Processes tab frequently, so the display blanks shortly after i move the mouse over it to force things to display).

- Some apps that support multiple tabbed documents (gedit, gnome terminal) display ok with only one doc/tab, but show the same behavior as lists as soon as a second tab/document is opened.

The problem persists even with Compiz disabled, and whether or not i add the "nomodeset" flag to the kernel line in Grub.

Another update: it seems to happen in Nautilus and gedit only when the content exceeds the size of the window, thus requiring scrolling.

Googling hasn't turned up anything. Suggestions most welcome.

---

