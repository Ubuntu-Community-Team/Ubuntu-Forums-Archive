---
title: "New install to 12.04 with MATE but desktop folders remain"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by suomalainen on 2013-08-16
Hi,

I installed 12.04 with MATE.

The home folder and computer folder which remain after the install won't disappear.

You can't delete them
Google tweak didnt work
Gconf or something or other didn't work.


Anyone know of a solution?

Thanks!

---

### Post by tgalati4 on 2013-08-16
You are correct!  It must be a setting within Mate.  Perhaps buried in one of these:

mateconf-editor (1)  - an editor for the MateConf configuration system
mateconftool-2 (1)   - MATE configuration tool

Let us know what you find.

---

### Post by suomalainen on 2013-08-16
**I tried these two approaces to no avail......**

1. from software centre download

"Advanced Settings"

2. Open terminal

3. Enter "gnome-tweak-tool"

4. Under desktop you can make the changes you need. BUT STILL home, computer and trash remain after settings changed...

ANOTHER APPROACH 

From Terminal

1. gconf-editor

2. "Configuration editor" opens but desktop icons are no where to be found.???????

Help...

---

### Post by mikewhatever on 2013-08-16
Why do you want the home folder to disappear? It should have all your files and settings, so, at least, back them up before it's too late.
Same goes about the computer folder, whatever that is.

---

### Post by suomalainen on 2013-08-16
Found these commands here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)


To show the Computer icon run:

Code:

gsettings set org.gnome.nautilus.desktop computer-icon-visible true

To hide the Computer icon run:

Code:

gsettings set org.gnome.nautilus.desktop computer-icon-visible false

To show the Home icon run:

Code:

gsettings set org.gnome.nautilus.desktop home-icon-visible true

To hide the Home icon run:

Code:

gsettings set org.gnome.nautilus.desktop home-icon-visible false

These also did not work for me. I wonder if a new install is in order?

---

### Post by suomalainen on 2013-08-17
I found this file:

org.mate.caja.gschema.xml

in:

/usr/share/glib-2.0/schemas

and so logged into Nautilus as su and edited it because it held the true/false values of trash, computer and home folders. Changed all three from True to False and still they apper on desktop. Even after reboot.


This isn't funny anymore. Quite a few solutions were attempted to no avail.

Does anyone know if these folders are hardcoded into the source code and cannot be deleted or what's the deal?

Thanks!

---

### Post by suomalainen on 2013-08-17
Sorry. Uploaded wrong screenshot and the edit option would not allow me to delete it.

---

### Post by tgalati4 on 2013-08-17
I bet if you search through the source code you will find it!  You have tried numerous methods.  Perhaps send an email to the [Mate]("http://mate-desktop.org/") developers.

---

### Post by suomalainen on 2013-08-17
I'm gonna do a new install.

Is their a right and wrong way about installing MATE?

---

### Post by suomalainen on 2013-08-18
Before the install. Anyone know the answer to this?

---

### Post by tgalati4 on 2013-08-18
Linux Mint Mate 14 has done all of the heavy lifting and it works out of the box--no tweaking involved.  It's based on 12.10, so it is not an LTS release, but it works.  I believe 15 is out now so you could try that as well.  I don't know if the newer versions of Mate allow you to delete those two folders off of the desktop.

---

### Post by mikodo on 2013-08-18
[Is this helpful, from ArchLinux Forums?]("https://bbs.archlinux.org/viewtopic.php?pid=980156")

---

### Post by tgalati4 on 2013-08-19
I will give it a try to test Mate 1.4

```
mateconftool-2 --type boolean --set /apps/caja/desktop/computer_icon_visible false

mateconftool-2 --type boolean --set /apps/caja/desktop/home_icon_visible false    

mateconftool-2 --type boolean --set /apps/caja/desktop/trash_icon_visible false
```

Thanks for the link.

---

### Post by suomalainen on 2013-08-20
Did the codes Mikodo offer work?

---

### Post by tgalati4 on 2013-09-26
I tried just the first command and it worked!  I like to have the home folder icon on my desktop and my trash icon is missing.  So I know for sure the first command works with Mate 1.4.

---

### Post by suomalainen on 2013-09-29
Finally found the answer

The dconf editor replaced mate-conf in the 1.6 release. Install "dconf-tools" if it isn't already there. You should find "Dconf editor" in the System Tools menu.

Once launched, click on "org" in the left panel, then "mate", then "caja", and, finally, "desktop" (org->mate->caja->desktop). On the right you will see checkboxes to toggle the visibility of the icons.

---

### Post by hg-knight on 2013-11-06
thanks for the help

---

