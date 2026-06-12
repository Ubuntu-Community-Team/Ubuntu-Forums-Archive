---
title: "Clean install, video card issues"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2006-08-18
ok  About to throw computer through window.

Am now doing a clean, fresh install using 6.06.1 and when it goes through the install process I get a error message saying:
"Fail to start the Xserver (your graphical interface) etc".

This is a clean install????  ](*,)   

Video card is nvidia 7600GS AGP.

Performing dpkg-reconfigure xserver-xorg goes through the process then hits a brick wall at choosing color depth in bits. the overwriting of a customised configuration file.


i never had this bullshit during other installs of ubuntu.

Anyone got ANY help this time please?

Cheers,
Ian

---

### Post by The Pinny Parlour on 2006-08-18
arghhhh  this is doing my head in. Why won't this <blanking> :-# thing work? ](*,)

---

### Post by meng on 2006-08-18
I can understand the frustration. It may help to take a few deep breaths. Although I probably can't help you, it wouldn't hurt to post your xorg.conf here.
P.S. How's the weather at the Coast? from an ex-Brisbanite

---

### Post by The Pinny Parlour on 2006-08-18
Thank mate.   command not found....trying: /etc/X11/xorg.conf

It's warm during the days and a little cold at night.  "They" say it's going to be 28 on the weekend.  :D 

Regards,
Ian

EDIT:  EVerytime I try something I have to go through the whole install process from scratch.   This is really frustrating.

---

### Post by meng on 2006-08-18
Try:
cat /etc/X11/xorg.conf

---

### Post by The Pinny Parlour on 2006-08-18
yep, that worked.   heaps of stuff came up.  the screen scrolled madly.  i have no idea what to do with it though.:mrgreen:

---

### Post by meng on 2006-08-18
Oh, that just shows you the contents of the xorg.conf file, just in case you wanted to copy/paste and post it here. I forgot you don't have X running, therefore you can't copy/paste easily! Can you copy the file to another machine perhaps?

---

### Post by The Pinny Parlour on 2006-08-18
I'm ready to throw this ******* thing.

---

### Post by The Pinny Parlour on 2006-08-18
I just want to clean/fresh install.  why is it soooo difficult?  

I  know i'm whinging, i'm losing patience with this thing.

---

### Post by The Pinny Parlour on 2006-08-18
It appears I'm making some progress.  Will keep posting as I go.  Choose the second option on the ubuntu boot screen when installing.

---

### Post by The Pinny Parlour on 2006-08-18
Got it.  Finally.

When installing, I choose the second option instead of the first on the live/install cd.  Thank goodness.  I was going nuts.

---

