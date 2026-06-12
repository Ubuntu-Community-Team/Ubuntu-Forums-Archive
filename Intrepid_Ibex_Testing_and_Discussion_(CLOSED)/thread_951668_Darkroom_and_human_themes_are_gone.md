---
title: "Darkroom and human themes are gone?"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ba0bab on 2008-10-18
Hi,

Just updated to 8.10, and tried out the new darkroom theme. It looks sooo cool!

However, I tried installing the blubuntu theme. It tells me it can't, because it needs the "gtk2-engines-ubuntulooks".

I then install that package, and all of a sudden darkroom, murine and human are gone! I tried to uninstall "gtk2-engines-ubuntulooks" but that doesn't bring any of the themes back.
 
Can't really figure it out. I tried looking after darkroom but can't find it, and would like to figure out what happened.

Thx in advance for any clues!

---

### Post by mc4100 on 2008-10-18
The ubuntulooks engine conflicts with the human-theme package ... to get it back:
```
sudo aptitude install human-theme human-icon-theme
```

---

### Post by shane19174 on 2008-10-18
If I try to update blubuntu, gtk2-engines-ubuntulooks blocks my way because of a conflict not only with human-theme but also ubuntu-artwork and ubuntu-desktop. Especially the last one is important, so you should probably check and see if those packages are still there.

Shane

---

### Post by ba0bab on 2008-10-18
@mc4100
Thank you, I got the human themes back, at the expense of blubuntu. It allso removes some other packages though: 
```

The following packages are BROKEN:
  blubuntu-theme 
The following NEW packages will be installed:
  human-theme 
The following packages will be REMOVED:
  exiv2{u} gtk2-engines-ubuntulooks{a} libexiv2-4{u} libkdcraw5{u} 
  libkexiv2-6{u} 
0 packages upgraded, 1 newly installed, 5 to remove and 0 not upgraded.
Need to get 54,7kB of archives. After unpacking 2482kB will be freed.
The following packages have unmet dependencies:
  blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme

Score is 188

```

@shane19174:

thanks for the warning - ubuntu-dekstop isn't installed, I think. this is what I get with sudo apt-get install ubuntu-desktop:

```

The following extra packages will be installed:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-style-human openoffice.org-writer python-uno transmission-gtk
  ubuntu-artwork
Suggested packages:
  openoffice.org-base openoffice.org-style-industrial
  openoffice.org-style-hicontrast openoffice.org-evolution openoffice.org-gcj
  openoffice.org-filter-binfilter openoffice.org-java-common
  openoffice.org-writer2latex
The following packages will be REMOVED:
  openoffice.org-debian-menus
The following NEW packages will be installed:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-style-human openoffice.org-writer python-uno transmission-gtk
  ubuntu-artwork ubuntu-desktop
0 upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
Need to get 6612B/52,5MB of archives.
After this operation, 200MB of additional disk space will be used.

```

I uninstalled Openoffice 2.4 and installed 3.0, with menus for 3.0. Seems like it wants to install 2.4 again, so what could I do if it is only ubuntu-desktop I want? Also, if I use the synaptic tool under "administration" in search of ubuntu-desktop, it doesn't show up at all?

I'm sorry if it isn't clear what I need of you, but I don't know myself. It seems quite a bit bigger than a question of mere themes?

/Emil

---

### Post by shane19174 on 2008-10-18
> **ba0bab said:**
> 
I uninstalled Openoffice 2.4 and installed 3.0, with menus for 3.0. Seems like it wants to install 2.4 again, so what could I do if it is only ubuntu-desktop I want? Also, if I use the synaptic tool under "administration" in search of ubuntu-desktop, it doesn't show up at all?

I'm sorry if it isn't clear what I need of you, but I don't know myself. It seems quite a bit bigger than a question of mere themes?

/Emil

ba0bab, I don't want to give you any wrong info, so I would suggest asking someone more knowledgeable about this. Perhaps in the thread about "OpenOffice 3.0 debs". The main issue seems to be this: removing OOo 2.4 removed ubuntu-desktop. Reinstalling the latter would apparently reinstall the former. The question is: would this screw up OOo 3.0? 

Wait a minute, synaptic doesn't show ubuntu-desktop at all? I don't know what's up with that.

Sorry I can't help more concretely, but like I said the OOo experts are probably your best bet here.

Shane

---

