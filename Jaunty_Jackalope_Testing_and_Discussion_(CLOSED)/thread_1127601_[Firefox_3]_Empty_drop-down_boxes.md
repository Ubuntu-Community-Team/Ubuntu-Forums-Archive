---
title: "[Firefox 3] Empty drop-down boxes"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by w0ei on 2009-04-16
Hi,

I have the following problem in Jaunty: the drop down boxes in Firefox are empty. It's not the case that the font color is just the same as the background color, no, there is just no text :S there do seem to be entries cause when I click on one, I can see there is a long list, but just no letters (or something..). First I thought it was my theme (Elegance 2.0) but changing the theme doesn't help..

Screenshot:
[img]http://digimasters.nl/temp/emptyboxes.jpg[/img]

Any ideas?

[edit]
Someone already seems to have fired a bug, but nothing seems to happen really..
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/352424](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/352424)

---

### Post by w0ei on 2009-04-17
*bump*

---

### Post by frenkel on 2009-04-17
Did you try to completly restart firefox? (Not saving tabs you have open)
Did you try to start firefox with a different profile? (move ~/.mozilla to ~/.mozilla.bak and try again)

---

### Post by w0ei on 2009-04-17
Yep, tried that.. Doesn't help :S

---

### Post by Dauthi4 on 2009-04-17
Hi,

Did you try to rename yout .gtkrc-2.0 into .gtkrc-2.0_old (or maybe you've got a .gtkrc-mine, rename it too) ?

You should then restart X or your computer to be sure the theme has been reloaded.

Maybe your Gtk Theme is messed up...

---

### Post by crjackson on 2009-04-17
I had an issue like that a while back. It turned out to be a permissions issue. I had to fix the permissions on my fonts folder recursivly.

---

### Post by w0ei on 2009-04-17
> **Dauthi4 said:**
> Hi,

Did you try to rename yout .gtkrc-2.0 into .gtkrc-2.0_old (or maybe you've got a .gtkrc-mine, rename it too) ?

You should then restart X or your computer to be sure the theme has been reloaded.

Maybe your Gtk Theme is messed up...
Euhm, I don't seem to have a .gtkrc-2.0 anywhere? :)

> **crjackson said:**
> I had an issue like that a while back. It turned out to be a permissions issue. I had to fix the permissions on my fonts folder recursivly.
Hmm, I was kinda hoping this would be it since I had been playing around with fonts a bit, but no :( setting the permissions right for all the font-dirs didn't help.. :S

---

### Post by crjackson on 2009-04-17
> **w0ei said:**
> Euhm, I don't seem to have a .gtkrc-2.0 anywhere? :)


Hmm, I was kinda hoping this would be it since I had been playing around with fonts a bit, but no :( setting the permissions right for all the font-dirs didn't help.. :S

What font directory did you change the permissions on? Also - You must change the permissions from a root prompt or root nautilus.

---

### Post by w0ei on 2009-04-17
> **crjackson said:**
> What font directory did you change the permissions on? Also - You must change the permissions from a root prompt or root nautilus.
Of course.

I created a new font dir in /usr/share/fonts/truetype/custom where I placed new .ttf files. I chown'ed them to root (they were set to my username before) and chmodded them 644.

---

### Post by Dauthi4 on 2009-04-17
Did you try to regenerate the font cache by doing that ?

```
sudo fc-cache -fv
```

Maybe it could help...

---

### Post by w0ei on 2009-04-17
> **Dauthi4 said:**
> Did you try to regenerate the font cache by doing that ?

```
sudo fc-cache -fv
```

Maybe it could help...
Yep, also did that..

---

### Post by w0ei on 2009-04-18
It seems that Epiphany also suffers from the same prolem :S so it looks like it's not specifically related to Firefox...

---

