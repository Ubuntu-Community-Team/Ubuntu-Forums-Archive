---
title: "New Wave Theme &amp; Firefox Menu Bar"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by WiFi Ed on 2009-04-10
Jaunty is working well for me, and I like the new themes, especially the New Wave theme but....

All the apps have white text in the menu bar except Firefox. The white text shows up well and I prefer it, but Firefox's is black and hard to see.

Is there an easy fix for this?

Thanks!

---

### Post by Nullack on 2009-04-10
Yeah Ive bugged it in launchpad but its not fixed - poor quality decision by Ubuntu to implement community themes without sorting the packaging out properly.

---

### Post by WiFi Ed on 2009-04-10
Thanks for the info, I'll just have to live with it then...

---

### Post by olskar on 2009-04-11
Yes, there is a, fairly simple, way.

Download [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=new-wave0801.zip](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=new-wave0801.zip) and unzip. 

Check the README

---

### Post by phenest on 2009-04-11
I'm using New Wave but don't have this problem, because I selected New Wave Dark Menus for Controls.

---

### Post by phenest on 2009-04-11
Although, check Evolution Preferences > Mail Preferences. I'm getting white text and it's very hard to read until you mouse over something.

---

### Post by Lem on 2009-04-11
Just unpack this and add into 
~/.mozilla/firefox/[something random].default/chrome/

Sorted.

---

### Post by WiFi Ed on 2009-04-11
Thanks everybody, for the responses and suggestions!

I'm sure one (or more) of these will sort me out...:p

---

### Post by dilomo on 2009-04-11
> **WiFi Ed said:**
> Thanks everybody, for the responses and suggestions!

I'm sure one (or more) of these will sort me out...:p

You should use the firefox theme provided with the package here:
[http://gnome-look.org/content/show.php/New+Wave?content=87134](http://gnome-look.org/content/show.php/New+Wave?content=87134)

The userchrome.css is integrated in the FF theme so it's not needed anymore.

---

### Post by Nullack on 2009-04-11
dilomo if users click on the new wave theme they naturally expect that the theme will be changed to new wave. Why should they have to fiddle with adding a firefox theme manually?

---

### Post by BwackNinja on 2009-04-11
The thing is that _technically_ it is a problem in firefox that hasn't been fixed, because remember, firefox doesn't use 'real' GTK, the same goes for OpenOffice.org, which has the same troubles. The good about firefox is that its easily worked around with a UserChrome.css, too bad you can't do that with OpenOffice.org.

---

### Post by dilomo on 2009-04-12
> **BwackNinja said:**
> The thing is that _technically_ it is a problem in firefox that hasn't been fixed, because remember, firefox doesn't use 'real' GTK, the same goes for OpenOffice.org, which has the same troubles. The good about firefox is that its easily worked around with a UserChrome.css, too bad you can't do that with OpenOffice.org.

Exactly what I would say. You see the New Wave Dark menus does not have this prob because firefox fakes it ok but taht is not the case with the default New Wave. So you should probably ask this question to the FF bugzilla?

---

### Post by phenest on 2009-04-12
Perhaps we need to put this to the Mozilla team. Ask for better compatibility in Gnome for both Firefox & Thunderbird.

---

