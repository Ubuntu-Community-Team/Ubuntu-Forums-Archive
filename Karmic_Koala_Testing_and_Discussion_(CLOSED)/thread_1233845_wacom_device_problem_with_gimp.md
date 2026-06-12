---
title: "wacom device problem with gimp"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by super kim on 2009-08-07
hi, i have a bamboo tablet for drawing. I have tested it using gimp and inkscape. i have had problems with both programs which are unresolved i wanted to know if and how i should report a bug?

The basic problem with gimp is that the area that the active tool edits is about 35 pixel down and 58 pixels to the right of the cursor. not the greatest of problems i admit but it does of course mean that when you try to use a tool within the top and left borders of the screen the cursor is already outside the screen :(

With inkscape the problem seems similar but when using the calligraphy tool i got some strange results i took some screen shots whilest drawing so you can see the area the tool is drawing in relation to the position of the cursor

[http://img269.imageshack.us/img269/2...shotuxjyrx.png]("http://img269.imageshack.us/img269/2355/screenshotuxjyrx.png")
[http://img30.imageshack.us/img30/608/screenshot1zcm.png](http://img30.imageshack.us/img30/608/screenshot1zcm.png)
[http://img10.imageshack.us/img10/906...enshot2dwv.png]("http://img10.imageshack.us/img10/9065/screenshot2dwv.png")
[http://img10.imageshack.us/img10/390...enshot3fxq.png]("http://img10.imageshack.us/img10/3907/screenshot3fxq.png")

i don't think there is a bug in gimp and inkscape but favux who has helped me set up my .fdi previously thinks it could be a bug in Xserver and/or linuxwacom

---

### Post by MacUntu on 2009-08-07
I can confirm this "off-cursor" thing once I enable the "Wacom Bamboo" device in Gimp:

[IMG]http://img.xrmb2.net/images/599671.png[/IMG]

If I leave it disabled I can use the tablet but only as cursor (no pressure points).

Edit: Same in inkscape plus the strange calligraphic tool behaviour.

---

### Post by MacUntu on 2009-08-07
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

Please confirm (and add additional information if you can). Thanks!

---

### Post by super kim on 2009-08-09
> **MacUntu said:**
> [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

Please confirm (and add additional information if you can). Thanks!


how how how ???

i can confirm thats the same thing i have going on. i'm afraid i have no more information than you have given already unless you want technical information about my pc?

---

### Post by MacUntu on 2009-08-09
When logged into Launchpad, you should be able to click the status "New", change it to "Confirmed" and then click on "Save Changes". After that we just have to wait, wait, wait, and... wait.

If devs need more information from us they'll tell.

---

### Post by super kim on 2009-08-12
OK i forgot to mention i confirmed :)

---

### Post by MacUntu on 2009-08-12
Good! \\:D/

---

### Post by super kim on 2009-08-12
> **MacUntu said:**
> Good! \\:D/


well off the subject but i'm curious... if ubuntu is now using empathy instead of thunderbird... with epiphany supersede firefox one day? i like epiphany a lot there are a few things missing still but it is a nice browser.

---

### Post by taavikko on 2009-08-12
> **super kim said:**
> well off the subject but i'm curious... if ubuntu is now using empathy instead of thunderbird... 

empathy replaces ekiga and pidgin, not thunderbird which is mail-app.
Don't hink that thunderbird will ever replace evolution (but who knows?)

---

### Post by Favux on 2009-09-22
Hi everyone,

Loic2 reports they fixed the bug upstream and gives links to the patches in post #314 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=32](http://ubuntuforums.org/showthread.php?t=967147&page=32)

It would be good to get the fix into Karmic.

---

