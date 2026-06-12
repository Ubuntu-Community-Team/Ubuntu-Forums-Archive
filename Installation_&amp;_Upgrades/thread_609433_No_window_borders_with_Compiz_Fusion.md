---
title: "No window borders with Compiz Fusion"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2007-11-10
Ok.... I have been trough every single related thread, nothing solved the problem

I have a fresh install of gutsy on a dual boot (this does not matters). at first, compiz didn't run, now I fixed that, but emerald does not works, meaning, no window borders. Only while terminal is open. I have tried:
**emerald --replace, compiz --replace -c emerald &, -c emerald &...**

On the other hand, alt+f2 do not open the run window. i am going crazy without the borders!!! 

On compiz --replace -c emerald &; trows an error saying that emerald couldn't be loaded. Please help!!!!

---

### Post by berserker on 2007-11-11
This is what finally worked for me:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & emerald --replace &
```

---

### Post by arashiko28 on 2007-11-11
I fixed the problem on Ubuntu, now on Xubuntu, this is what I get:

$ sudo apt-get install compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gnome is already the newest version.
compiz-gnome set to manual installed.
compizconfig-settings-manager is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
compiz-fusion-plugins-extra set to manual installed.
libcompizconfig-backend-gconf is already the newest version.
libcompizconfig-backend-gconf set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stephanie@stephanie-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:01.0 0300: 8086:7121 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2e00020 (stephanie@)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2e00020 (stephanie@)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

I know my computer should be able to support it, despite being old, because I used to run beryl on it when had 7.04. I don't know what's wrong.

---

### Post by arashiko28 on 2007-11-11
> **berserker said:**
> This is what finally worked for me:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & emerald --replace &
```

I tried that, this is the result:

> $ LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & emerald --replace &
[1] 7268
[2] 7269
stephanie@stephanie-desktop:~$ Checking for Xgl: not present. 

(emerald:7269): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

Detected PCI ID for VGA: 00:01.0 0300: 8086:7121 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7339): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1a00020 (stephanie@)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by arashiko28 on 2007-11-14
My borders dissapeared again, but only on the folders, when I open a file, the have their borders. But the folders are with no borders, and occupies the full window, tried to minimize it manually, no luck so far. Please help!!!!!

On Ubuntu

This is what I get when i do compiz --replace :

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

and it stays like that forever

---

### Post by PoppelMoppel on 2007-12-24
I have exactly the same problem as you. Did you find a solution?

---

### Post by nandoc on 2008-04-13
Had the same problem, but got solved after activating "windows decoration" after installing and running CompizConfig-Settings-Manager (Synaptic), and using it under Terminal: ccsm . Make sure to activate other similar: window resize, windows move...
Good luck

---

### Post by mirko_3 on 2008-04-14
I got everything solved by using compiz --replace ccp. What is ccp anyway?

---

### Post by kutjara on 2008-04-14
One of the side effects of losing your menu bars and borders with Compiz is that Alt+F2 becomes inoperable (just when you need it most). The workaround I found was to right-click the Gnome Panel, choose "Add to Panel" from the dropdown menu, and select "Run Application..." from the list. This installed a little applet in my Gnome Panel that mimics the functionality of Alt+F2. I was then able to use it to type "compiz --replace" and everything worked fine. Even Alt+F2 was back, so I could remove the little applet from Gnome Panel.

---

