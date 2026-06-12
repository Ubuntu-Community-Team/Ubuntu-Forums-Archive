---
title: "Ubuntu Software won't show installed programs/extensions after upgrade to 20.04"
date: 2021-02-26
forum: Installation &amp; Upgrades
---

### Post by galacticstone on 2021-02-26
Hi Folks,

I just upgraded from 18.04.5 to 20.04.2 - the upgrade went smoothly for the most part.

However, when I open Ubuntu Software, it no longers shows what I have installed. Everything else seems to work, but when I click on the tab to show my installed programs, nothing happens. (see screenshot).  Any ideas how to fix this?

Thanks in advance!

MikeG

---

### Post by galacticstone on 2021-02-26
My system stats (basic)

---

### Post by grahammechanical on 2021-02-26
I can confirm this problem. I do not open Software app very often. But I just now tested the app on my install of 20.04 and it has the same problem as the one you have found. I do not have the answer.

Regards

---

### Post by Dennis N on 2021-02-26
Ubuntu Software is OK on my system with respect to installed applications. But gnome-shell extensions are not shown in Ubuntu Software - instead, they are in the separate Extensions app.
Extensions also handles updates. See screenshot 2.

---

### Post by galacticstone on 2021-02-27
> **Dennis N said:**
> Ubuntu Software is OK on my system with respect to installed applications. But gnome-shell extensions are not shown in Ubuntu Software - instead, they are in the separate Extensions app.
Extensions also handles updates. See screenshot 2.
Just curious, what extensions app is that?

I can't get mine to show either - apps or extensions.

---

### Post by galacticstone on 2021-02-27
> **grahammechanical said:**
> I can confirm this problem. I do not open Software app very often. But I just now tested the app on my install of 20.04 and it has the same problem as the one you have found. I do not have the answer.

Regards
Me too. I don't use Software that much either, but I wanted to check it out after a fresh upgrade, just to see if anything interesting had changed. It works fine for browsing apps to install, but it won't show your installed apps or extensions.

---

### Post by Dennis N on 2021-02-27
> **galacticstone said:**
> Just curious, what extensions app is that?

I can't get mine to show either - apps or extensions.

It's gnome-shell-extensions. It's in the Ubuntu repository.

```
dmn@Sydney-vm:~$ apt show gnome-shell-extensions
Package: gnome-shell-extensions
Version: 3.36.1-1
Priority: optional
Section: universe/gnome
Origin: Ubuntu

```

---

### Post by grahammechanical on 2021-02-27
This issue might get fixed with an update/upgrade. I think my system was updated yesterday after my post. And Software is now showing icons for installed applications. 

Regards

---

### Post by galacticstone on 2021-02-28
I can confirm this. I just checked again and now my installed apps are showing. Must have been fixed by the latest update.  :)

---

### Post by galacticstone on 2021-03-01
I'm trying to find the button to mark this thread as "solved", but I don't see it now.

---

### Post by galacticstone on 2021-03-01
Nevermind. It's still an issue. I just checked again and now the screen is blank. It's no longer showing my installed software. Weird.

---

### Post by Dennis N on 2021-03-01
> **galacticstone said:**
> Nevermind. It's still an issue. I just checked again and now the screen is blank. It's no longer showing my installed software. Weird.
I suggest you remove 'Ubuntu Software' (snap-store) and install 'Software' (gnome-software) which is not a snap. They look the same with the added feature of Flatpak support in Software (it handles Snaps too).

---

### Post by galacticstone on 2021-03-01
> **Dennis N said:**
> I suggest you remove 'Ubuntu Software' (snap-store) and install 'Software' (gnome-software) which is not a snap. They look the same with the added feature of Flatpak support in Software (it handles Snaps too).
Where do I find that version of Software? I tried apt-get and nothing came back. I looked in the default Software/Snap store and it didn't show up as a search result. Can I find it with Synaptic?

---

### Post by Dennis N on 2021-03-01
> **galacticstone said:**
> Where do I find that version of Software? I tried apt-get and nothing came back. I looked in the default Software/Snap store and it didn't show up as a search result. Can I find it with Synaptic?
Use your terminal:
```
sudo apt install gnome-software
```
It's in the Ubuntu Repositories. 
Some info:
```
dmn@Sydney-vm:~$ apt show gnome-software
Package: gnome-software
Version: 3.36.1-0ubuntu0.20.04.0
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Recommends: gnome-software-plugin-snap, fwupd
Suggests: apt-config-icons-hidpi, gnome-software-plugin-flatpak

```
'Software' is the program name you will see with it's icon.

---

### Post by galacticstone on 2021-03-01
> **Dennis N said:**
> Use your terminal:
```
sudo apt install gnome-software
```
It's in the Ubuntu Repositories. 
Some info:
```
dmn@Sydney-vm:~$ apt show gnome-software
Package: gnome-software
Version: 3.36.1-0ubuntu0.20.04.0
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Recommends: gnome-software-plugin-snap, fwupd
Suggests: apt-config-icons-hidpi, gnome-software-plugin-flatpak

```
'Software' is the program name you will see with it's icon.

When I tried that, it said it was already installed. So I tried running it from the command line and the same thing happened - software opened as normal, but wouldn't show what's installed.

Here's what I got when I tried to install it from the CL :

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-software is already the newest version (3.36.1-0ubuntu0.20.04.0).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.




---

