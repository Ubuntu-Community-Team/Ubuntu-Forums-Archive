---
title: "Upgraded to 14.04 from 12.04, where are my drivers?"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by Extreedoc on 2014-09-26
As above, upgraded to 14.04 LTS, resolved a crashing issue but now I have no sound, no printer and my photo card reader doesn't work. How do I fix this?

---

### Post by QIII on 2014-09-26
Hello!

Were you using any proprietary drivers for these items that you had installed from sources other than the Ubuntu repos?

Could you give us some hardware specs?

---

### Post by Extreedoc on 2014-09-26
Whoa!! That was quick... In answer to your question: no, all the drivers were those that came with the OS.

---

### Post by QIII on 2014-09-26
You are likely going to have to just go through the normal printer setup again.  Have you tried that?

Is your sound on-board? Make/Model?

Is your card reader a USB unit?  Connected to an internal header?  Connected to an external USB port?  Make/model?

(Not trying to nag.  ;)  Rather than taking stabs in the dark, this is easier to do with some information.)

---

### Post by Extreedoc on 2014-09-26
Thanks for trying to help. Sound: on-board but I have no idea as to make etc, card reader is a USB unit connected to socket on the computer, Advent RDR-ALL if that helps... The Printer: is recognized by the computer in System Settings>Printers it just doesn't work. This is odd because when 12.04 was installed, everything just worked without any trouble.

---

### Post by Extreedoc on 2014-09-26
Well, I got the printer working by deleting it and setting up fresh. The sound card is not recognized, it is an AMD Trinity HDMI audio controller. Also the media card reader is not recognized. I can't see it in the Dash in files and can't get the sidebar to show at all.

---

### Post by Rob Sayer on 2014-09-26
You can't assume that after a release upgrade everything will work the same.  This is a big reason I prefer a clean reinstall, with a separate /home partition.

More importantly IMO, you can't assume that the way to fix a problem in the previous release will work in the new one.

You need to get hardware details.  Read this for a start:

[http://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details](http://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details)

I don't use Google to search so I'm not led to the many crappy blogs that google prefers in search results because they use google ads.  In any case, you should usually go for this site or askubuntu.  Just search ubuntu + whatever hardware details you get.

---

### Post by Extreedoc on 2014-09-26
Thanks Rob, this is very useful, I'll get back when I know more.

---

