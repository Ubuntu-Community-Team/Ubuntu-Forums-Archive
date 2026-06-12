---
title: "Cursor keys mismapped after upgrade."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by jema on 2008-11-01
For example the up cursor is mapped to "print".

---

### Post by 4leite on 2008-11-01
not sure i can be much use, but also has some funny mappings. My mouse buttons where set to move and resize windows respectively.

Went to System->Preferences->Compiz-Config-Settings Manager. 
Did an advanced search, selected value and deselected the other two options. Enter button1 (in your case maybe up) into the search field, scrolled through the options till I saw one that was just button1 (or up)  and disabled it.

Otherwise your keyboard might configured wrong and I can't help you...

---

### Post by Kinslayer on 2008-11-01
I am also having weird remapping issues.  Compiz-Fusion settings were the first thing I checked, but they are showing what they are supposed to.  Something seems to have gone off between the plastic keys and what happens on-screen. 

As soon as I find what the problem might be, I'll post here.

---

### Post by jema on 2008-11-01
I uninstalled the ATI driver and removed xorg.conf and now I have cursor keys again.

---

### Post by jema on 2008-11-01
Or not.

I reinstalled the proprietry driver via desktop effects, and the cursor keys were dead again... removed it again and the keys are still dead following a reboot :(

---

### Post by Kinslayer on 2008-11-01
It's not just the one computer.  Both my laptop and desktop have the same weird remapping issues:  Up is Print Screen, right Alt is Enter/Return, etc.

---

### Post by Kinslayer on 2008-11-02
I still have no idea what caused the problem.  With great difficulty, I managed to make a new xmodmap with xkeycaps.  It's not **THE** fix, but at least it's **A** fix.  It looks ugly, showing Print Screen remapped to Up arrow--just to get things back to where they are supposed to be--but I'm glad to at least have that functionality back.

---

### Post by jema on 2008-11-02
> **Kinslayer said:**
> It's not just the one computer.  Both my laptop and desktop have the same weird remapping issues:  Up is Print Screen, right Alt is Enter/Return, etc.

Weird isn't it. I can confirm my Right Alt is also Enter/Return.

How can something so basic go so wrong? Especially when they are right at the login screen.

---

### Post by kellner on 2008-11-03
I have the same issues with an IBM/lenovo thinkpad x60 tablet.

altgr = enter
page up = /
page down is not functional
cursor up works
cursor down is not functional
cursor left and right are not functional
home and end keys are not functional

I used to have a special Xmodmap file that I loaded on login. I disabled this, but the problems remain. The 8.10 release notes state that the new version of X.Org is not compatible with old Xmodmap files, but I don't think that this is the source of the problems people are describing here - in that case, one would not expect such consistent mismappings across what appears to be a broad (?) range of PC and notebook models. 

Any help would be greatly appreciated,

---

### Post by jema on 2008-11-04
The answer for me was to remove the MESA drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

solved other issues as well :guitar:

---

### Post by iputz on 2008-11-04
This is affecting me too. Up Arrow == Print Screen. What, seriously??

How the hell did this monster bug slip through? What does this have to do with the new version of xmodmap? The release notes mention some "conversion" of the ~/.Xmodmap file but do not say how this is accomplished. Anyone have a fix for this?

---

### Post by maddsch on 2008-11-04
I've the same problem here with my MSI Wind U100 (Advent 4211): The arrow keys are remapped. The solution above doesn't work:

$ sudo apt-get remove xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

---

### Post by iputz on 2008-11-06
Bump to the top. Yeah, it's that serious.

---

### Post by jema on 2008-11-07
> **jema said:**
> The answer for me was to remove the MESA drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

solved other issues as well :guitar:


Has no one else had luck with my solution then?

What do you get with:

>fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 2.1.8087 Release

That is where I was getting the wrong answers.

---

### Post by iputz on 2008-11-08
Well, I can't say that I've fixed /the/ problem, but I've managed to fix /my/ problem by replacing my own heavily customized ~/.fluxbox/ configuration files with the standard defaults. All it took was a complete backup of my home directory and a nuclear reinstall of the OS. I want two days of my life back.

---

