---
title: "how do I get Global Menu in Karmic?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AndyP79 on 2009-10-08
Hi All,
 I used to have Ubuntu Tweak installed on my last set up, and it had Global Menu in it, and I could get it in add to panel. 
Now I am using Karmic, but when I install Ubuntu Tweak, no there is no more Global Menu?
I searched Google, but did not come up with anything
Thanks

---

### Post by matthew.ball on 2009-10-08
I believe the following PPA is for Global Menu (at least it is what I used/use):
[FONT="Courier New"][SIZE="1"][SIZE="2"]#Global Menu Panel Applet
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main[/SIZE][/SIZE][/FONT]

Just add it to /etc/apt/sources.list and grab it then.

---

### Post by AndyP79 on 2009-10-09
Okay, I have no clue what you just said. I don't really know anything about building things from scratch. Can you break this down step by step and please don't assume I know anything....
Thanks

---

### Post by jdinosaurus on 2009-10-10
it seems that this repository  doesn't work

---

### Post by rburkartjo on 2009-10-11
same on this end i like the global menu

---

### Post by rburkartjo on 2009-10-11
and if anyone gets it to work in karmic please post on this thread. tks

---

### Post by ankspo71 on 2009-10-11
Hi,
I don't think they have a karmic repo yet. Jaunty might work.
[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

However you can download it and compile it from source.
[http://code.google.com/p/gnome2-globalmenu/downloads/list](http://code.google.com/p/gnome2-globalmenu/downloads/list)
James

---

### Post by jdinosaurus on 2009-10-16
the jaunty repo does work with karmic. just tried that - seems that everything is fine

---

### Post by fredunderhill on 2009-10-26
Agreed. Using Karmic via Virtual Box. The Jaunty repo works just fine and is working for me.

---

### Post by cariboo on 2009-10-26
From the ppa page:

> Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding **ppa:globalmenu-team/ppa **to your system's Software Sources. 

---

### Post by A.I. on 2009-10-26
I create bug repost to add Karmic packages to it PPA.

[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=524](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=524)

---

### Post by flipper9 on 2009-10-26
Why do you want to use Global Menu?  I originally wanted to use it to get more vertical real-estate on my height-restricted netbook screen.  The problem is that the two most used applications (IMHO) don't even support Global Menu, i.e. Firefox and OpenOffice.

To get more screen real-estate on my screen, I found a much better method (and is compatible with almost all programs) is to do the following...
1. Remove the bottom toolbar from the Ubuntu Desktop.
2. Remove the Applications/Places/System bar and replace with the standard Gnome menu (just the icon)
3. Remove the Firefox and Help shortcuts
4. Add the "window-picker-applet" (sudo apt-get install window-picker-applet) to the top Gnome toolbar and justify to the left.  This bar will show all windows as icons, and integrate the titlebar when windows are maximized and have focus.
5. Configure compiz to hide the window decoration for maximized windows (since the titlebar is integrated into the top toolbar (into the window picker applet) when maximized.  First install the CompizConfig Settings Manager (sudo apt-get install compizconfig-settings-manager), then goto the "Effects/Window Decoration" setting.  Under "Decoration Windows" you will need to change "any" to "!state=maxvert".  This prevents maximized windows from having their window decoration drawn.
6. To switch desktops, I just configure the "Desktop/Expo" compiz plugin to show all desktops when I place the mouse pointer into the bottom left-hand corner of the screen. 
7. To show all open windows, I configure the "Window Management/Scale" compiz plugin to show all windows on all desktops when I place the mouse pointer in the lower right-hand corner of the screen (I also disable showing the desktop when the desktop is clicked under this plugin).

This has allowed me to get what I intended Global Menu to accomplish (to get more vertical screen real-estate) without actually integrating the menu bar into the top toolbar.  Hope this helps.

---

### Post by A.I. on 2009-10-27
> **flipper9 said:**
> Why do you want to use Global Menu?  I originally wanted to use it to get more vertical real-estate on my height-restricted netbook screen.  The problem is that the two most used applications (IMHO) don't even support Global Menu, i.e. Firefox and OpenOffice.

To get more screen real-estate on my screen, I found a much better method (and is compatible with almost all programs) is to do the following...
1. Remove the bottom toolbar from the Ubuntu Desktop.
2. Remove the Applications/Places/System bar and replace with the standard Gnome menu (just the icon)
3. Remove the Firefox and Help shortcuts
4. Add the "window-picker-applet" (sudo apt-get install window-picker-applet) to the top Gnome toolbar and justify to the left.  This bar will show all windows as icons, and integrate the titlebar when windows are maximized and have focus.
5. Configure compiz to hide the window decoration for maximized windows (since the titlebar is integrated into the top toolbar (into the window picker applet) when maximized.  First install the CompizConfig Settings Manager (sudo apt-get install compizconfig-settings-manager), then goto the "Effects/Window Decoration" setting.  Under "Decoration Windows" you will need to change "any" to "!state=maxvert".  This prevents maximized windows from having their window decoration drawn.
6. To switch desktops, I just configure the "Desktop/Expo" compiz plugin to show all desktops when I place the mouse pointer into the bottom left-hand corner of the screen. 
7. To show all open windows, I configure the "Window Management/Scale" compiz plugin to show all windows on all desktops when I place the mouse pointer in the lower right-hand corner of the screen (I also disable showing the desktop when the desktop is clicked under this plugin).

This has allowed me to get what I intended Global Menu to accomplish (to get more vertical screen real-estate) without actually integrating the menu bar into the top toolbar.  Hope this helps.

I use globalmenu on desktop because menu on top is more usable for me.

---

### Post by cudjoe on 2009-10-27
I also like global-menu (and wish it could some day reach openoffice and firefox).

I miss it so much on Karmic !

---

### Post by A.I. on 2009-10-27
I found solution: just add to old repo
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main

---

### Post by eluminx on 2009-10-27
i found this one on the forums and it works on my karmic install 
ppa:matthaeus123/ppa

Been using it for the past 2 weeks and it works great.

---

### Post by A.I. on 2009-10-27
> **eluminx said:**
> i found this one on the forums and it works on my karmic install 
ppa:matthaeus123/ppa

Been using it for the past 2 weeks and it works great.

Also, ppa:sushkov/personal — developer PPA

---

### Post by renkinjutsu on 2009-10-27
if you're using the version in the jaunty repos, you'll probably have trouble opening gimp, inkscape, gparted, firefox, etc.

anyway, to avoid this problem, either download and compile the git or 0.7.8 beta they have up for download [http://code.google.com/p/gnome2-globalmenu/downloads/list]("http://code.google.com/p/gnome2-globalmenu/downloads/list")

but to compile this version, you'll need the latest version of Vala (the one in karmic is dated)
here's the Vala ppa 
[https://launchpad.net/~vala-team/+archive/ppa]("https://launchpad.net/~vala-team/+archive/ppa")

---

