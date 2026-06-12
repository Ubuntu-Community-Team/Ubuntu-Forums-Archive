---
title: "Consider a new way to handle Window list"
date: 2009-11-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LKjell on 2009-11-21
The current Window list applet is kinda outdated. It does very bad when you have multiple windows up. Multiple tabs and workspaces are a solution. However, it does not solve all the problems.

Some of the problems when you have multiple windows open:

*It gets harder to read the text description.

*It gets harder to locate and close one or many related programs.

*It gets ugly.

A solution is to use [Dockbarx]("http://www.gnome-look.org/content/show.php/DockbarX?content=101604")

It keeps same windows in one box. There are no text description since it is useless to have when you have too many windows. And it looks like Windows 7, so easy transition.

---

### Post by Merk42 on 2009-11-21
See also:[list]
[*][AWN](http://ubuntuforums.org/showthread.php?t=1331413)
[*][GNOME Shell](http://ubuntuforums.org/showthread.php?t=1305154)[/list]

---

### Post by VMC on 2009-11-21
> **Merk42 said:**
> See also:[list]
[*][AWN](http://ubuntuforums.org/showthread.php?t=1331413)
[*][GNOME Shell](http://ubuntuforums.org/showthread.php?t=1305154)[/list]

I don't think I can use either one. I have an intregrated Intel 865 chip and after installing AWN it required compiz which failed:

```
vmc@vmc-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

---

### Post by LKjell on 2009-11-21
Dockbarx does not require compiz and it is very light.

---

### Post by BbICEP on 2009-11-22
> **LKjell said:**
> It keeps same windows in one box. There are no text description since it is useless to have when you have too many windows.
I found it pointless. At home I only have browser opened most of the time, so no crowd problem at all. At work I extensively use workspaces, so no crowd problem again. Docks are solution for people who try to use gnome as windows shell.
>  And it looks like Windows 7, so easy transition.
How many people use Windows 7? They are in minority now. So what "easy transition" you are talking about? Again, if you like docs and don't like workspaces: may be you better would stay with your windows? It's more stable, doesn't have so much problems with audio, graphic and network subsystems.

---

### Post by LKjell on 2009-11-24
> **BbICEP said:**
> I found it pointless. At home I only have browser opened most of the time, so no crowd problem at all. At work I extensively use workspaces, so no crowd problem again. Docks are solution for people who try to use gnome as windows shell.

How many people use Windows 7? They are in minority now. So what "easy transition" you are talking about? Again, if you like docs and don't like workspaces: may be you better would stay with your windows? It's more stable, doesn't have so much problems with audio, graphic and network subsystems.

The problem with workspace is that you need time to locate the windows in each workspace. Even if I use two workspaces I find it hard to locate where the windows are. Since you still need to remember in which workspace your windows are. A problem would be to juxtapose two windows from two different workspace. If we use Always on visible workspace then we stilled waste a space on the panel. 

If you use workspace to differentiate from different project then it is fine. But still even one project might have many windows open and that is where the problem lies. You might have a big screen and has no problem but I do not have a big screen. Even one with big screen will eventually run out of space on the panel. And then do what? Gnome is not smart enough to group similar application into one. Do you know how hard it is to locate 20 plots from different simulation when they are scattered on the panel?
And then how to close all those plots? If you argue to use killall command then the user friendliness just jumped out of the window.

Of course Dockbarx have limitation when we have 20 different applications. But it is a transition to something usable. This transition is what I am referring to. A transition to the future.

---

### Post by McDuff on 2009-11-24
> **VMC said:**
> I don't think I can use either one. I have an intregrated Intel 865 chip and after installing AWN it required compiz which failed 

awn 0.4 does not require compiz. it runs very fine with metacity compositing on my laptop with via integrated graphics – compiz and gnome-shell are a no-go on it.

---

### Post by baizon on 2009-11-24
> **Merk42 said:**
> See also:[list]
[*][AWN](http://ubuntuforums.org/showthread.php?t=1331413)
[*][GNOME Shell](http://ubuntuforums.org/showthread.php?t=1305154)[/list]

I've started using [Window Picker Applet]("https://launchpad.net/window-picker-applet") (A gnome-panel applet that displays open windows as icons on the panel, and has integrated window title-bar functionality. Optimised for use on netbook-size screens) and [Maximus]("https://launchpad.net/maximus") (A desktop daemon which will automatically maximise and, optionally, un-decorate windows. Has support for exclusion lists and will work with any EWMH-spec compliant window-manager). It's really nice and comfortable.

---

### Post by bobince on 2009-11-24
A new paradigm for window management is not a bad idea. But please, not another bleedin' &#8216;Dock&#8217;. It was a hopeless design when OS X introduced it and it has got little better since. I do not want an application launcher and a window list crudely jammed together into the same interface, and I do not want to have to click on an application first and then on the right window inside it to bring up the window I was after. My unit of attention is a document, not an application.

One of the things I like most about GNOME is that it gives me a straightforward window list and plain hierarchical main menu, instead of trying to be clever with big shiny icons and a swishy impractical mess of a menu like the Vista or KDE one (the latter being turnoffable, thankfully).

If I could have one window management change, I'd like tabbing to be done at the window manager level, so I could tab together a load of windows for related tasks regardless of what applications were in them.

---

### Post by Merk42 on 2009-11-24
> **bobince said:**
> One of the things I like most about GNOME is that it gives me a straightforward window list and plain hierarchical main menu, instead of trying to be clever with big shiny icons and a swishy impractical mess of a menu like the Vista or KDE one (the latter being turnoffable, thankfully).

How are Vista and KDE's window lists that different from GNOMEs?

---

### Post by inportb on 2009-11-25
Can you explain what is so swishy, impractical, or messy about KDE's window list? It seems to work just fine.

---

### Post by bobince on 2009-12-02
> Can you explain what is so swishy, impractical, or messy about KDE's window list?

I was talking about the menu (Kickoff) in that case, with its fixed size limiting it to ‘Favourite’ applications by default (like the ‘new-style’ Windows Start menu, but with even fewer applications).

Maybe for noddy users Favourites is a win, but with the amount of stuff I run it's a complete fail. The majority of the time the application I want isn't there (and on the Windows most-commonly-used version, even when it is, it moves, defeating muscle memory).

Switch the large-shiny-iconned tabs to ‘Applications’ instead and you're lost in a smoothly-animated, hierarchical maze, without the navigational cues you'd get in a real filer. And because it's still fixed-height, you invariably get a scrollbar as well, meaning you have to navigate on two axes, and when you've scrolled down a bit the only navigational cue you have at all (the heading at the top) disappears, leaving you to guess where you are from a load of shiny icons. And the shonky auto-scroll only fires when you don't want it, scrolling the header away when you move the pointer down near the tabs but then no further.

None of this is progress, but at least KDE lets me turn it off and just have a completely normal hierarchical menu, which is more than I can say for Vista(*). Classic Menu Style is fine: launch for a typical 1-deep application is click-move-move-click instead of click-move-click-move-click-scrollwheel-move-click.

(*: Then again, the old-school hierarchical menus from XP and earlier are also useless by default because of the terrible Manufacturer->AppName->App-plus-Uninstall-and-Help hierarchy. If you want a usable Category->App hierarchical menu on WinXP, you have to make it yourself. Linux distros at least have the advantage of being able to arrange the hierarchy how they like as they're in control of application deployment instead of a third-party that wants to spill its shortcuts all over the desktop. There is therefore no need to copy the Windows Start menu that is trying to work around these Windows-only problems.)

---

### Post by phenest on 2009-12-02
> **bobince said:**
> I was talking about the menu (Kickoff) in that case, with its fixed size limiting it to ‘Favourite’ applications by default (like the ‘new-style’ Windows Start menu, but with even fewer applications).

Maybe for noddy users Favourites is a win, but with the amount of stuff I run it's a complete fail. The majority of the time the application I want isn't there (and on the Windows most-commonly-used version, even when it is, it moves, defeating muscle memory).

Switch the large-shiny-iconned tabs to ‘Applications’ instead and you're lost in a smoothly-animated, hierarchical maze, without the navigational cues you'd get in a real filer. And because it's still fixed-height, you invariably get a scrollbar as well, meaning you have to navigate on two axes, and when you've scrolled down a bit the only navigational cue you have at all (the heading at the top) disappears, leaving you to guess where you are from a load of shiny icons. And the shonky auto-scroll only fires when you don't want it, scrolling the header away when you move the pointer down near the tabs but then no further.

None of this is progress, but at least KDE lets me turn it off and just have a completely normal hierarchical menu, which is more than I can say for Vista(*). Classic Menu Style is fine: launch for a typical 1-deep application is click-move-move-click instead of click-move-click-move-click-scrollwheel-move-click.

(*: Then again, the old-school hierarchical menus from XP and earlier are also useless by default because of the terrible Manufacturer->AppName->App-plus-Uninstall-and-Help hierarchy. If you want a usable Category->App hierarchical menu on WinXP, you have to make it yourself. Linux distros at least have the advantage of being able to arrange the hierarchy how they like as they're in control of application deployment instead of a third-party that wants to spill its shortcuts all over the desktop. There is therefore no need to copy the Windows Start menu that is trying to work around these Windows-only problems.)

You've drifted off-topic there.
AWN is a nice alternative to gnome-panel without being 'docky', handles workspaces just fine, and doesn't require a compositing manager.

> **baizon said:**
> I've started using [Window Picker Applet]("https://launchpad.net/window-picker-applet") (A gnome-panel applet that displays open windows as icons on the panel, and has integrated window title-bar functionality. Optimised for use on netbook-size screens) and [Maximus]("https://launchpad.net/maximus") (A desktop daemon which will automatically maximise and, optionally, un-decorate windows. Has support for exclusion lists and will work with any EWMH-spec compliant window-manager). It's really nice and comfortable.

The window-picker-applet is something xfce has always had and AWN has a good version too.

---

### Post by bobince on 2009-12-03
> **phenest said:**
> AWN is a nice alternative to gnome-panel without being 'docky'

Not ‘docky’? It's  an icon-based launcher and a window list smooshed together into the same interface. That's the definition of&#8201;—&#8201;and [problem](http://www.asktog.com/columns/044top10docksucks.html) with&#8201;—&#8201;a Dock.

> [Avant Window Navigator]("https://launchpad.net/awn/") (AWN/Awn) is a dock-like navigation bar

---

