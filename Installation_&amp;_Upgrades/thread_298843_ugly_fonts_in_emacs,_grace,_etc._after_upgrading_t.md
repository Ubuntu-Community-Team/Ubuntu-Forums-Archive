---
title: "ugly fonts in emacs, grace, etc. after upgrading to edgy"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by rayanez on 2006-11-13
The menu / application fonts in several applications look very ugly after upgrading from dapper to edgy. I mean really ugly.

It seems most non-gnome-supported applications have the same problem. Here I list the ones I commonly use,

- emacs21
- amsn
- grace
- gacc

The System/Preferences/Font settings won't configure these fonts. I'm not an fort expert, but is this a problem related to GTK, QT?

Help please, I'm so unhappy as to consider going back to Debian.

---

### Post by Rui Pais on 2006-11-14
hi,
see if [this thread here]("http://www.ubuntuforums.org/showthread.php?t=285304") helps.

---

### Post by mohammedosman1986 on 2006-11-19
> **rayanez said:**
> The menu / application fonts in several applications look very ugly after upgrading from dapper to edgy. I mean really ugly.

It seems most non-gnome-supported applications have the same problem. Here I list the ones I commonly use,

- emacs21
- amsn
- grace
- gacc

The System/Preferences/Font settings won't configure these fonts. I'm not an fort expert, but is this a problem related to GTK, QT?

Help please, I'm so unhappy as to consider going back to Debian.

hi,

I have the same problem in emacs as yours but I got it fixed.

First, changing the font paths in xorg.conf from /usr/share/X11/fonts/ to /usr/share/fonts/X11.  Then restart X.

If there is still a problem after restarting, first open the emacs application then go to the option menu and select Mule (Multilingual Environment) => set fonts/fontset.  The menu will appear, select fontset => default.  The fonts will display clearly.  But it is not configured permanently.

So follow the recipe below:

1. Select the "Option" menu.
2. Select "Customize Emacs" => "Top-Level Customization Group".
3. Then on the window, scroll down until you see "Faces group", select the button "Go to group".
4. Again scroll down until you see "Basic Faces", select the button.
5. Now you can see the text "Default", select the Show button then the sub menu will appear.
6. Change the text field of "Family:" as "fontset".
7. Then enter the height of font (you decide what type of font height, I chose "164") in the text field of "Height in 1/10 pt".
8. Then, at the top you will find the "Finish" button, select it.  
9. Close this application and open the application again, and the fonts should look better now.

Hope it helps.

Cheers

Mohammed.

---

