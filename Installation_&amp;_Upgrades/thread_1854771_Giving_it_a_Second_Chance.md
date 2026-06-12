---
title: "Giving it a Second Chance"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2011-10-05
So I decided to give 11.04 a second chance today.  I ditched Ubuntu after the release of 11.04 because it just seemed insanely slow, even when using the "Classic" gnome desktop.

I dd'd the 11.10 beta 2 iso to a thumb drive and let my wife play around with the "Try Ubuntu" option and she really really likes Unity, so I'm going to give it another shot.  I'm going to install 11.04 and just do a dist-upgrade when 11.10 comes out this month.

I haven't used Ubuntu since a week or so after 11.04, is there anything in particular I should be aware of, any major changes since release, improvements, regressions?

Just dipping my toe back in the water after a bad migration to 11.04 that lead me to investigate other options for a while.

---

### Post by Hedgehog1 on 2011-10-05
In practical terms, you might want to wait until 3-4 weeks after 11.10 is 'shipping' before you install it.

Although many folks are testing 11.10 (myself included), and it is moving along nicely, there will be bugs found that the smaller testing community just didn't hit.

If you wait a month after the release, most things will have fixes and your experience should go better.

My 2 cents...

***The Hedge***

:KS

---

### Post by Rubi1200 on 2011-10-05
I concur with Hedgehog1's assessment; in most cases waiting a month (or even longer) until the first bug fixes are released will save you a lot of headaches.

---

### Post by gerowen on 2011-10-05
Well I will have to say the performance is much better than it was the first time I installed.  Additionally, the open source drivers for my ATI Radeon 3100 provide 3-D support, so installing the proprietary ones is unnecessary.  The games I play run just fine.  On Debian, I couldn't even play World of Goo with the open source drivers.

The font rendering is really nice too.  I do have one question.  Is there an applet for Parcellite, or some program like it that works in Unity?  I installed Parcellite, but its icon doesn't appear in the system tray, so I'm guessing it doesn't work with Unity.

For those that don't know, Parcellite was a clipboard manager that kept a history of the contents of your clipboard, so you could regress to previously copied items without having to actually go redo the right click action on the original source.

Edit: Glipper serves this purpose, and works in Unity.

---

### Post by gerowen on 2011-10-06
So I've learned something, at least about Unity, and why I may have had a bad experience my first go-around.  I just tried installing the proprietary drivers for my video card.  I ran glxgears at a specific resolution and redirected the output to a text file.  I thin removed the proprietary driver and did the same thing.  Although the open source driver had a lower reported frame-rate, the motion appeared much smoother.  Also, the interface in most programs is noticeably much more responsive using the open source driver for my card.  Has anybody else noticed that installing the proprietary ATI drivers makes interface response time suck in Unity?

This isn't a big deal, I don't play many games at all, and using the proprietary driver makes my computer (this happens across all the distros I've used) emit a high pitched squeal, like what you hear when a TV is on even though it's muted.  So I'm more than happy to use the open source driver, but it's weird that for general use it actually works "better" than the ATI driver.

---

### Post by mastablasta on 2011-10-06
perhaps it is not the driver that is at fault. does this also happens on other DE (e.g. KDE) where Compiz is not present?
 
also there will probably be a new ATI drivers version release soon for the 11.10.

---

### Post by coffeecat on 2011-10-06
> **gerowen said:**
>  So I'm more than happy to use the open source driver, but it's weird that for general use it actually works "better" than the ATI driver.

From what I've read it seems that the open source driver seems to give a better user experience than the proprietary one with certain chipsets. I have three different ATI GPUs in different machines, and my few tries with the proprietary driver were - how shall I put this diplomatically? :wink: - unrewarding. 

By the way, the "ATI" driver is actually the open-source one. The proprietary is the so-called fglrx or catalyst. Or, more precisely, the ati driver is simply a wrapper which "loads  one of the 'mach64', 'r128' or 'radeon' sub-drivers depending on the hardware" (from the xserver-xorg-video-ati package description).

Good luck with using Unity.

---

### Post by gerowen on 2011-10-06
So I've come to the conclusion that Unity, at least for me, is best left to the netbooks.  It's pretty, but menu navigation is just too much of a pain compared to classic Gnome, so I'm going to stick with that.  I think I'll stick with Ubuntu for my regular desktop OS as well, just because I can use the default drivers for my card for mild 3-D acceleration without the overheating, and the font rendering and general appearance is much better out of the box than with Debian.

---

### Post by mörgæs on 2011-10-07
Classic Gnome is on its way out in Ubuntu. You could try Xubuntu, if you want something (more or less) in that style.

---

### Post by gerowen on 2011-10-07
> **mörgæs said:**
> Classic Gnome is on its way out in Ubuntu. You could try Xubuntu, if you want something (more or less) in that style.

I'll toss it on a Virtual Machine and see what I think.  I just like having a menu where, with one click, I can move around and see everything.  It just feels cumbersome to only be shown 3 or 4 items with the first click, then to have to click a little sub-menu to get a list, where I click on a category where I'm still only shown the top couple of entries.  Then if I want to see the rest of that category I have to click again on a link to "See all items".  Unity is pretty enough, but the number of clicks I have to use to find stuff any more is a little annoying sometimes, maybe I'll give it a chance again.

---

### Post by gerowen on 2011-10-09
Just one more update, and I'll leave this topic alone.

I've come to the decision to go back to Debian.  Below are some notes that I've taken for the developing community behind Ubuntu so you guys can continue to improve on your product.  This is by no means an Ubuntu bashing session, I just want to convey some honest notes I took while giving Ubuntu a shake on a few of my computers over the past couple of days.

I've received comments from some people telling me to try Gnome classic or Xubuntu, but Gnome classic feels incredibly slow in Ubuntu now, and I want to stick with Gnome so Xubuntu isn't really an option.

_**The Good**_
**1)** The Ubuntu font is a lovely replacement for the anti-aliased default found in most other Linux distros.
**2)** Unity would probably be really effective for tablets and netbooks.
**3)** The integration of the window title bar into the system title bar is a nice space-saving touch.
**4)** The "Additional Drivers" program is one of the best things to ever hit a Linux distribution.  Not having to manually hunt down the appropriate drivers for your hardware is awesome.
**5)** The Unity bar is nice, especially having applications dock on their launch icon.
**6)** OpenOffice replaced with LibreOffice, :-)

_**The Bad**_
**1)** Across 3 different computers I experienced various differing graphical glitches, using both open source and proprietary video drivers.  Sometimes I'd have white squares or static over top of an element of the interface.
**2)** The interface just "feels" really slow, even if you choose "Ubuntu Classic" at the login screen.  It just doesn't feel "snappy", and on one of my computers, even though 3-D application performance improved, Unity interface performance got terribly worse after installing the proprietary ATI drivers.  There was a really noticeable amount of lag in just navigating the right click menus, mousing over icons in apps like LibreOffice, etc.
**3)** 3-D applications, that normally would have functioned just fine in Windowed mode, are seriously bogged down when running in Windowed mode now, probably due to the presence of Compiz.
**4)** Non-standardized implementation.  Applications that have system tray icons under normal conditions in all the other desktop environments, don't get system tray icons in Unity.  Just out of the ones I've used in the past 2 days I've had multiple applications that should have system tray icons that don't get them under Unity.  The problem with this is, let's say I opened Truecrypt and mounted my encrypted file container, then habitually hit the "X" to send it to the system tray.  5 minutes later I'm done working with my encrypted files, but there's no graphical way to access the currently running instance of truecrypt so I can unmount the volume.  The only way to fix the issue is to forcibly kill the Truecrypt instance.
**5)** The universal menu bar gets confusing when running multiple applications, on top of the fact that you lose access to your nautilus bookmarks if you don't happen to have a nautilus window focused.  It's no longer as easy as moving to the top of the screen and clicking "Places".  I know this is more of a preference to Gnome, but I just found it a bit awkward trying to get to the menu of an application that wasn't focused.
**6)** Where did all my panel applets go?
**7)** The menu in Unity is absolutely horrible.  In regular Gnome 2 I could find any application anywhere in the menu with one click and minimal movement of my mouse to different subfolders of the menu.  As it is now, I have to **click** the "Applications" button on the Unity bar, then **click** the arrow next to "All Applications", then I have to **click** on a subcategory.  If the program isn't listed there, I have to **click** on a link to show all of the programs in that submenu.  Depending on the program I'm looking for, what used to be accessible with one click is now buried under up to 4 clicks.
**8 )** When applications are running and you want to open a new instance of that program, you have to manually hunt it down in the menu (see step 7) because its shortcut does not have a right click option to launch a new instance, it only restores the minimized copy of that program.  I first noticed this because I had gnome-terminal pinned to the taskbar.  I had a process running in one terminal which took up the side bar.  Single or double clicking that side bar icon would not launch a new terminal.  Right clicking it and clicking its title also did not launch a new instance of the program.  I had to go hunt it down in the menu.

---

### Post by coffeecat on 2011-10-09
> **gerowen said:**
> I've come to the decision to go back to Debian.  Below are some notes that I've taken for the developing community behind Ubuntu so you guys can continue to improve on your product.

*Our* product? A point of information: most of the members of this forum are ordinary users, some (many?) of whom are IT professionals. Few of the developers frequent the forum.

---

### Post by mörgæs on 2011-10-09
I always recommend that people try as many distros as possible. Linux is about choice, and one distro should not be seen as more correct than the other. Good luck with Debian.

I like your signature, by the way.

---

