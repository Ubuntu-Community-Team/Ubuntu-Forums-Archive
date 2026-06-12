---
title: "Newbie Install  issues"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by xman1128 on 2006-12-09
I have downloaded 6.10 about 4 times now and every time i try to just boot it up to run live (i need to do a demonstartion at work without actually installing ubuntu) its in DOS mode on drive A. It has WWBMU in there and when i switch over to my D drive where the disk is it wont work. I thought i downloaded the live disk but at this point im confussed. Im not giving up I just need some guidence from those who know ubuntu.

Xander

---

### Post by meng on 2006-12-09
If it's booting in "DOS mode", the problem is that you're burning the CD wrongly. Most likely you're burning it as a bootable image rather than re-creating the filesystem from the ISO, which is inherently bootable. So your burning program is adding a primitive OS (probably DR-DOS) to the CD, which defeats the whole purpose of burning in the first place. See here for some hints on burning:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by bscbrit on 2006-12-09
Have you burnt it to CD as an image (.iso), or have you simply burnt it to CD as a Window's file?  If you are running the download and burn under Windows, you will have use Roxio or some other software that allows you to burn file as an image (.iso) otherwise it will not boot.  

This is a limitation of Windows, not a problem with the .iso image.  Most other OS can cope with .iso but Microsoft have elected not to support it directly.

---

### Post by kackler on 2006-12-09
You're probably have the "server" version. Go back to the downloads page and download the "Desktop" version. The desktop gives you a GUI, the server is in text mode.

---

### Post by meng on 2006-12-09
> **kackler said:**
> You're probably have the "server" version. Go back to the downloads page and download the "Desktop" version. The desktop gives you a GUI, the server is in text mode.
I doubt this is the problem. When the user reports s/he is in DOS on A:, that's not the server/alternate install at all. Not to mention that the text/GUI dichotomy is really Live Desktop vs. Alternate Desktop.

---

