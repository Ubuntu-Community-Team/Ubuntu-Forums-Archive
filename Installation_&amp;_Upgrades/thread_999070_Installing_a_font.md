---
title: "Installing a font"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2008-12-01
I have a TrueType font that I created on a Windows Vista system. I would like to add it to my ubuntu installation in order for OpenOffice apps to use it. How do I do it?

---

### Post by pennacook on 2008-12-01
If there are other TrueType fonts that you want installed, it is as easy as copying the font files to the ~/.fonts/ directory.

After installing new fonts, you will have to log out and log in again to be able to see and use the new fonts. If you want to avoid this, you can regenerate the fonts cache by issuing the following command:
```
$sudo fc-cache -fv
```

---

### Post by josephmo on 2008-12-01
Thanks. Where is the ./fonts directory?

---

### Post by SuperSonic4 on 2008-12-01
It will be in your home directory.

It is not there by default though, you need to create it
This can/should be as user

1. ```
mkdir ~/.fonts
```

2a. (copy and paste them to the ~/.fonts folder you just created)

2b. ```
cp [COLOR="Red"]-r[/COLOR] /media/[COLOR="Red"]320GB\media[/COLOR]/Windows/Fonts ~/.fonts
```

Only do one step 2a or 2b of course, the bit in red will be the name of your drive as it appears in Places. I'm not 100% about the space being represented by \ but 2a will work. -r means recursive, try it if the fonts one won't copy without it.

you will then need to close and reopen your office

3.```
fc-cache
```

---

### Post by josephmo on 2008-12-01
> **SuperSonic4 said:**
> It will be in your home directory.

It is not there by default though, you need to create it
This can/should be as user

1. ```
mkdir ~/.fonts
```

2a. (copy and paste them to the ~/.fonts folder you just created)

2b. ```
cp [COLOR="Red"]-r[/COLOR] /media/[COLOR="Red"]320GB\media[/COLOR]/Windows/Fonts ~/.fonts
```

Only do one step 2a or 2b of course, the bit in red will be the name of your drive as it appears in Places. I'm not 100% about the space being represented by \ but 2a will work. -r means recursive, try it if the fonts one won't copy without it.

you will then need to close and reopen your office

3.```
fc-cache
```

I want to make sure I got this: let's say my home directory is /home/myusername, I would create a /home/muysername/.fonts directory (it does not exist now). This means though that these fonts are only available to me, and not to other users of the system.

---

### Post by forkandles on 2008-12-01
Your font may be a one-off, but if your required font is a Microsoft TrueType font then the simplest way is to download and install msttcorefonts via Synaptic Package Manager.
Open Synaptic, click on "Quick Search", type in the box    msttcorefonts

Mark for installation, Mark, Apply, Apply and wait for the fonts to be installed.

To make that particular font the default selection in Open Office.org Writer then:

Applications > Office > OOO Word Processor (OOO Writer) > Tools > Options >
Click on (+) next to OOO Writer > Basic Fonts (Western) > Choose font and size for new default.
Job done.

You may find this link useful if you want to make Ubuntu 8.10 more powerful.

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

---

