---
title: "no keyboard layouts to choose from"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by armware on 2006-11-29
running kde on 6.10

my keyboard works (minus the multimedia keys, but i can fix those again) however i cannot select a keyboard layout as there are zero to choose from. i'm assuming this broke when i upgraded from 6.06 because that's when my volume control buttons stopped working and i finally got around to looking at the keyboard configs. that's when i discovered i had zero layouts. this should be simple, but i'm at a loss.
attached is a screenshot of what i mean.
ideas?

---

### Post by tomane on 2007-01-16
Bump.
Well, I have the same issue here, on an instalation from scratch. I began installing ubuntu from the CD and later installed kubuntu-desktop from aptitude.
using [System Settings]->[Regional Settings]->[Keyboard Layout] gives nill to choose from.

[COLOR=Red] So far the only fix I found was to manually edit xorg.conf. (EDIT: Nope, it didn't help either)[/COLOR]
also, if I run xmodmap /usr/share/xmodmap/xmodmap.pt under my KDE session, I get the ALTGR key back. Is there at least one way to run this command automatically at every kde session startup?

I'm on edgy, by the way :)

Cheers,
--to

---

### Post by armware on 2007-01-16
yes there is.
create a script to run the command and place it in  ~/.kde/Autostart/ folder.

the script should like like:

```
#!/bin/bash
xmodmap /usr/share/xmodmap/xmodmap.pt
```

don't forget to make it executable. 
```
chmod +x name_of_script
```

i should also point out that a complete repartitioning/reinstall of my installation fixed the issue.

---

### Post by tomane on 2007-01-17
Thanks, armware.
After my post I put that command in my ~/.profile and it did the trick. However, it is ran at every login I make, be it on kde, shell or gnome. I'll follow your suggestion.
As of now, the problem is gone with the .profile fix. 

Cheers,
--to.

---

### Post by mihao2am on 2007-01-27
I also had the problem with no keyboard layouts after installing kubuntu-desktop.  There seems to be an error in the kubuntu-desktop packages for ubuntu in where they get the layout configuration from - **I solved the problem by copying all the files from /etc/X11/xkb to /usr/share/X11/xkb**

---

### Post by tedrogers on 2007-02-08
I have a similar issue but I can't choose anything other than US English....and this is rubbish as I am British and need £ signs (for example).

I was looking into your solution but I don't have **/usr/share/X11/xkb**?

Is this a problem and do you know why when I ran **sudo apt-get install kubuntu-desktop** I have no options other than US-English in my regional settings?

It won't even allow me to *ADD* new ones...nothing appears...nor can I delete the US-English from the list.

Thanks all.

---

### Post by armware on 2007-02-09
create the missing directory

---

### Post by tedrogers on 2007-02-10
It's okay...installing kubuntu-dekstop on my ubuntu machine seriously borked up a lot of things...especially when I did recent update in ubuntu and it all went nuts.

I got rid of it.

---

### Post by svetlin on 2007-02-13
Did someone find a solution to this problem?

---

### Post by tritesnikov on 2007-02-19
> **svetlin said:**
> Did someone find a solution to this problem?

I followed a variation of one of the previous comments. I don't know how dangerous it is, but in /usr/share/X11, i linked /etc/X11/xkb in that directory after first renaming the existing /usr/share/X11/xkb:

cd /usr/share/X11
sudo mv xkb xkb.orig
sudo ln -s /etc/X11/xkb


The keyboard layouts now show up in System Settings, but it is retarded that you even have to do this in the first place.

---

### Post by svetlin on 2007-02-22
Thank you very much! That fixed the problem.

---

