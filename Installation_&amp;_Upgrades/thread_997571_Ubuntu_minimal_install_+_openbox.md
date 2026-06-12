---
title: "Ubuntu minimal install + openbox"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by COLiNx86 on 2008-11-29
I was wondering can I do a minamal install of Ubuntu with a kubuntu alternative install cd?
And also once I do have a minimal install (just command-line) what would I put to install X, openbox (and anything openbox needs to run), some ubuntu tools (such as Restricted Drivers, synaptic, etc.), and firefox?

---

### Post by m_duck on 2008-11-30
**INSTALLING**
I would have thought you can. You definitely can with the Ubuntu alternate disk, but I've not tried with the Kubuntu disk. When you first boot up, after you select language, press F4 (I believe) to change to "Cli Install" or "Install a command line system" or something like that. Then choose install Ubuntu etc and install as usual. After it reboots you will be greeted with an inviting text log in screen, and once logged in you will get:```
user@host:~$
```If you are using an ethernet connection to your router, you will probably be able to update your system now ```
sudo apt-get update && sudo apt-get upgrade
```If not, some extra fiddling with connecting will be required - more tricky but doable :D Then I think the only packages you **need** are xorg and openbox```
sudo apt-get install xorg openbox
```For synaptic, install the package "synaptic" as well, and for restricted drivers I think it is the "jockey-gtk" package, though I think there may be something else that is also required - I will check this.

**STARTING OPENBOX**
You will need to create a file in your home directory called .xinitrc```
nano ~/.xinitrc
```and add to it```
#!/bin/bash
exec openbox-session
```Save and exit (ctrl X, then y, then enter) and you can now log into openbox by entering```
startx
``` and press enter.

You could add a graphical log in manager such as gdm, kdm, xdm or slim instead of the startx approach.

**EXTRA PACKAGES AND CONFIGURATION**
To be able to customise openbox for your user, you will want to copy the default config files (there is a way to execute the 2 mkdir commands in one by I can't remember it):
```
mkdir ~/.config
mkdir ~/.config/openbox
cp /etc/xdg/openbox/autostart.sh ~/.config/openbox/
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/
cp /etc/xdg/openbox/rc.xml ~/.config/openbox/
```For openbox I would also suggest another few packages:```
sudo apt-get install obconf feh openbox-themes lxappearance
```**obconf** - This is a configuration program that lets you tweak various settings to do with openbox.
**feh** - image viewer and wallpaper program. A simpler option is "nitrogen" but once you get to grips with feh its very good.
**openbox-themes** - a selection of themes for openbox.
**lxappearance** - an easy way to set your gtk theme, gtk font size, icon theme etc. I think it is in the repo's in intrepid but not in hardy. In hardy, there is a package called "gtk-theme-switch2" or something of that nature. Or after some googling there is a deb package of lxappearance that works without issues.

Other useful packages:
**pypanel** - a lightweight panel (customisable via ~/.pypanelrc)
**tint2** - another nice looking panel, not sure if it is in the repos though ([website here]("http://code.google.com/p/tint2/"))
**gmrum** - a run box, similar to using alt F2 in gnome or kde, but needs to be bound to a key combination. I use alt F2 for consistency. This is set in the ~/.config/openbox/rc.xml file.
**gnome-terminal** - the terminal from the gnome desktop
**rxvt-unicode** - another nice terminal (more complicated to configure)
**conky** - system monitor application
**leafpad** - a lightweight graphical text editor
**thunar** - the file manager from XFCE
**pcmanfm** - another similar filemanager

You will probably also want to install some of the gtk engines and 

Some good resources for openbox stuff is [the openbox wiki]("http://icculus.org/openbox/index.php/Main_Page"), [the archlinux wiki]("http://wiki.archlinux.org/index.php/Openbox") and last, but by no means least [urukrama's openbox guide]("http://urukrama.wordpress.com/openbox-guide/").

Hopefully that helps... It is all from memory and I've not done it for a little while, so apologies in advance for inaccuracies, I will try to check it asap.

EDIT: I have just checked a Kubuntu Hardy Alternate iso, and if you press F4 when said above, you get the option "Install a command line system".

---

### Post by COLiNx86 on 2008-11-30
Wow! thank you so much!

---

### Post by scottmac112 on 2008-11-30
Good howto!

---

### Post by jis on 2008-12-14
lxde metapackage (the Lightweight X11 Desktop Environment) is based on openbox. I guess xfce4-terminal and lxterminal are lighter alternatives to gnome-terminal.

Unfortunately task list is not very good: you can not group items of same application like in Xfce4. 

LXDE and Xfce4 are rude in that they pop up windows when starting an application even if you start doing something with another application meanwhile. (Gnome and KDE handle this better.)

---

### Post by urukrama on 2008-12-14
> **jis said:**
> LXDE and Xfce4 are rude in that they pop up windows when starting an application even if you start doing something with another application meanwhile. (Gnome and KDE handle this better.)

You can change the Openbox's behaviour in ~/.config/openbox/rc.xml regarding. At the beginning of that file you have a section called <focus>:

```
<focus>
    <focusNew>yes</focusNew>
    <!-- always try to focus new windows when they appear. other rules do
       apply -->
    <focusLast>yes</focusLast>
    <!-- focus the last used window when changing desktops, instead of the one
       under the mouse pointer. when followMouse is enabled -->
    <followMouse>no</followMouse>
    <!-- move focus to a window when you move the mouse into it -->
    <focusDelay>200</focusDelay>
    <!-- when followMouse is enabled, the mouse must be inside the window for
       this many milliseconds (1000 = 1 sec) before moving focus to it -->
    <raiseOnFocus>no</raiseOnFocus>
    <!-- when followMouse is enabled, and a window is given focus by moving the
       mouse into it, also raise the window -->
    <underMouse>no</underMouse>
  </focus>
```

Change these settings and Openbox will behave differently. The comments in the default rc.xml should be clear enough to figure out what you need to change to have it behave like you want it to.

> **jis said:**
> lxde metapackage (the Lightweight X11 Desktop Environment) is based on openbox. I guess xfce4-terminal and lxterminal are lighter alternatives to gnome-terminal.

If you want an even lighter terminal, try urxvt.

---

### Post by jis on 2008-12-15
urukrama, no I can't figure out how to configure that e.g. a starting multi-window Firefox session would not pop up.

I don't see any menus in urxvt. How do you add tabs in it?

---

### Post by urukrama on 2008-12-16
To use tabs in urxvt, you need to add the following line to your ~/.Xdefaults (create it if you don't have one yet):

> URxvt.perl-ext-common:	default,tabbed

You can then open a new tab by clicking on the NEW button, or by pressing Shift+Down. You can move through the tabs by pressing Shift+Left or Shift+Right.

Urxvt does not have any menus. You configure it by editing configuration files. All of this happens in ~/.Xdefaults, where you can configure the colours and some behaviour of urxvt. Here is the relevant section of my ~/.Xdefaults:

> 
###############
###  urxvt  ###
###############
URxvt*font:		xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:hinting=true
URxvt*boldFont: 	xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:bold:hinting=true

URxvt*background:	#0e100f
URxvt*foreground:	#646f5b
URxvt*color0:		#0e100f
URxvt*color1:		#646f5b
URxvt*color2:		#9dad9c
URxvt*color3:		#8b99b5

#URxvt*background:	#08090A
#URxvt*foreground:	#4b555e
#URxvt*color0:		#08090A
#URxvt*color1:		#4b5261
#URxvt*color2:		#DFDFDF
#URxvt*color3:		#8b99b5

URxvt*fading:    	10
URxvt*tintColor: 	#FCFCFC
URxvt*shading:    	100
URxvt*inheritPixmap: 	False
URxvt*cursorBlink:      False
URxvt*cutchars:		`'",;@&*=|?()<>[]{}

URxvt*scrollstyle:	plain
URxvt*mouseWheelScrollPage:	False
URxvt*jumpScroll:       False
URxvt*skipScroll:       False
URxvt*scrollBar: 	False
URxvt*scrollTtyOutput:      False
URxvt*secondaryScroll:	  False

URxvt.perl-ext-common:	default,tabbed
URxvt.tabbed.tabbar-fg:         1
URxvt.tabbed.tabbar-bg:         0
URxvt.tabbed.tab-fg:            0
URxvt.tabbed.tab-bg:            1

URxvt*urlLauncher:	opera
URxvt*saveLines::       32767


If you don't want new window to receive focus, set the focusNew from the above mentioned section of your rc.xml to no:

```
<focusNew>no</focusNew>
```

---

### Post by jis on 2008-12-17
How do you delete a tab in urxvt?

---

### Post by urukrama on 2008-12-17
I generally just type "exit" to close a tab. I don't think there is a keybinding for it.

---

### Post by philthyfill on 2010-07-26
Any recommendations for a lightweight GUI power manager?

gnome-power-manager, xfce4-power-manager?

---

### Post by Frederich on 2010-11-01
Good evening everyone,

I followed step by step your excellent "how-to", and it did work great. 

However, I had an issue with Grub this morning, and had to reinstall everything. The installation of Ubuntu in command line is going ok. But, when it comes to starting X, all I get is a message saying "Waiting for X server to begin accepting connections" and then "No protocol specified" again and again and again, but no X starting...

Has anyone got a clue how to solve this problem ?

---

