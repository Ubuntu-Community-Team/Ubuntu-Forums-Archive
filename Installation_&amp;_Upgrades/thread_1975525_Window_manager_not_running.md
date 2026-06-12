---
title: "Window manager not running?"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by rivera151 on 2012-05-07
Hi.  I decided to try Unity and 12.04, and so far much more pleasant than my expectations.  However, I have run into this minor problem. Unity is not running when I log in.  I get my desktop background and context menu, but there is no bar at the top, and no dash/icons.  Opening any windows (say, by clicking a text document on the desktop) opens an unmovable window without decorations.  When I run the command 
```
ps -A | grep unity
```
I get no output.  However, if I run unity --replace unity starts up without problems, and the above command then gives the following output:
```
 
 2026 ?        00:00:00 unity
 2052 ?        00:00:04 unity-panel-ser
 2811 ?        00:00:00 unity-applicati
 2813 ?        00:00:00 unity-files-dae
 2815 ?        00:00:00 unity-music-dae
 2817 ?        00:00:00 unity-lens-vide
 2853 ?        00:00:00 unity-musicstor
 2874 ?        00:00:00 unity-scope-vid

```

So it seems that my problem is that unity is not being launched on login.  Some details:
[LIST=1]
[*]Already tried ```
unity --reset
```
[*]Fresh 12.04 install with a clean / partition and a used /home partition
[*]Tried deleting .config, .config/compiz*, .gnome, (also metacity dirs, gconf dirs)
[/LIST]

I can work around it by adding a ```
unity --replace
``` entry in the startup applications (shutdown menu), but this seems hackish, and I would like to resolve it properly.

Thank you very much.

Ricardo

---

### Post by rivera151 on 2012-05-20
Nobody?

bumpity bump?

---

### Post by bogan on 2012-05-20
Hi!, [B]rivera151,
[/B]
When you log-in are you selecting the Ubuntu option in the drop-down menu?, activated by Clicking in the Icon to the right and just above the Password string box.

If that icon is the Gnome Footprint you are booting to Gnome, Shell or Classic.

Selecting Ubuntu or Ubuntu-2d will change the Icon to a Ubuntu logo.

Edit: Try the 'ps' option of 'ax' instead of '-A' , [no hyphen]
Chao!, **bogan**.

---

### Post by rivera151 on 2012-05-22
I checked, and it is ubuntu I'm logging in to, not gnome. Still getting by with my hack...

---

### Post by jadtech on 2012-05-22
if you have no top bar menus and no gui on the launcher  then you should attempt to login ubuntu2d rather then ubuntu 3d usally things missing is a sign your video card is up to unity or  there is video driver issues .. 

just up over the login box  click on the menu before you type  your login password choose ubuntu 2d  if this does not get you a desk top test logging in as guest ..

if you haven't been to system setting additional drivers once you get there choose to activate  the waiting video driver if you havent already , also all the update  through software updater ..

---

### Post by rivera151 on 2012-05-22
I logged into unity 2d.  I got a top panel.  No window decorations when opening programs and no dock.

Running "metacity --replace" fixes everything.  So, in both unity and unity 2d, the display manager launches either, but in both it fails to run a window manager, as evidenced by running "unity --replace" (unity 3d) or "metacity --replace" (unity 2d) with resolution of the problems.

ANY ideas are greatly appreciated.

EDIT: Yet the Guest account loads perfectly. AAAAARGH!

---

### Post by rivera151 on 2012-05-26
Can one of you guys paste here the output of
```
update-alternatives --get-selections | grep x-window-manager
```

I'm getting this
```
x-window-manager               auto     /usr/bin/metacity
```

but I get a feeling it shoulod be unity. 

Also run this command if you can, please.  My output is included on the second line.
```

update-alternatives --get-selections | grep x-session-manager
x-session-manager              auto     /usr/bin/gnome-session
```

Confirm, please?

---

### Post by bogan on 2012-05-27
Hi!, **rivera151**,

Logged in to ubuntu with 12.04-24-39-generic-pae 32bit LTS, running the commands you suggested gives exactly the same results:```
~# update-alternatives --get-selections | grep x-window-manager
x-window-manager               auto     /usr/bin/metacity
~# update-alternatives --get-selections | grep x-session-manager
x-session-manager              auto     /usr/bin/gnome-session
~# 
```I have made no special ccsm settings changes, and all the log-in options work as I would expect, except that Unity-2d-Launcher does not appear in Dash or menus and does nothing when run from terminal.
Edit: That is, the 2d launcher appears when logged in to ubuntu-2d, but is not available when logged to Gnome classic or Classiic -no-effects, as it was in previous versions.

My display and session manager all work OK, though I get a lot of error messages; mostly Seg crashes of 'nautilus' & ' Sorry, Ubuntu 12.04 has encountered an internal error'.

Chao!,** bogan.**

---

