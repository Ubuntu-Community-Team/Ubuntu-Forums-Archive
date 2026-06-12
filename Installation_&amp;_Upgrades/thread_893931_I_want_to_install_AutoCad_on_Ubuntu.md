---
title: "I want to install AutoCad on Ubuntu"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-08-18
So, a friend of mine was amazed with my old laptop beating the ·$% out of his when we sat side by side and I was working and he waiting for his programs to respond. He has a Dell inspiron 1525 that came with virus - I mean Vista...
He said that I can make AutoCad work on Linux, he'll change it. Now, I have never used it, I need a guide of how to install it and to run well, he's an engineer and his whole work is around autocad. If not, what can be used instead? i saw a pretty good video on youtube about autocad on ubuntu, so I want that, if possible.

Any help is welcome.:)

---

### Post by Vivaldi Gloria on 2008-08-19
You use wine to run windows apps in ubuntu. Not all apps work with wine. You can check the wine apps database for a particular app:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=86](http://appdb.winehq.org/objectManager.php?sClass=application&iId=86)

Check the ratings column to see which versions work.

---

### Post by cdtech on 2008-08-19
I use VMware to run my Windows app's within Ubuntu.

---

### Post by Vivaldi Gloria on 2008-08-19
> **cdtech said:**
> I use VMware to run my Windows app's within Ubuntu.

The reason I hesitated to suggest virtualbox is that generally 3D things don't work in it. I have no idea if the virtualbox graphical drivers have enough juice to run autocad.

---

### Post by Loaded.len on 2008-08-19
There are also ACAD-esque apps specifically for *NIX systems. Although mostly commercial (some are free for non-commercial use), they are still a fraction of the cost of an AutoCad license.

---

### Post by cdtech on 2008-08-19
> **Vivaldi Gloria said:**
> The reason I hesitated to suggest virtualbox is that generally 3D things don't work in it. I have no idea if the virtualbox graphical drivers have enough juice to run autocad.

I understand.

I do run 3Dmax - gmax with no problems on mine though.

---

### Post by Vivaldi Gloria on 2008-08-19
> **cdtech said:**
> I understand.

I do run 3Dmax - gmax with no problems on mine though.

I did a bit of googling and it seems that autocad works in virtualbox:

[http://ubuntuforums.org/showthread.php?t=808245](http://ubuntuforums.org/showthread.php?t=808245)

But wine is preferable to virtualbox (close to native). So I suggest the OP to try first wine and then vbox. 

Actually, there are equivalent programs in linux:

[http://ubuntuforums.org/showthread.php?t=791132](http://ubuntuforums.org/showthread.php?t=791132)
[http://ubuntuforums.org/showthread.php?t=228890](http://ubuntuforums.org/showthread.php?t=228890)

---

### Post by cdtech on 2008-08-19
cool.......

---

### Post by arashiko28 on 2008-08-19
Thanks a lot. The bad part of all this is that sometimes people it's not willing to spent time on learning something new. That, most of the time pisses me off, because I do spent my time on teaching them at least the basics and then see my time go by the drain when they give up because of something isn't working the way they want. But, let's hope this one don't take it back.

---

### Post by Vivaldi Gloria on 2008-08-19
> **arashiko28 said:**
> Thanks a lot. The bad part of all this is that sometimes people it's not willing to spent time on learning something new. That, most of the time pisses me off, because I do spent my time on teaching them at least the basics and then see my time go by the drain when they give up because of something isn't working the way they want. But, let's hope this one don't take it back.

If your friend is not willing to learn a new os then he should stick with his windows. Don't force him. Better for both of you. It's a pain to admin someone's computer when they cannot be bothered to learn simple things.

---

### Post by noodlebike on 2008-10-08
Try running progecad 2008 smart (free after registering)

[http://www.progecad.com/eng_index.php?XMLFILE=http://news.progesoft.com/intellicad/index.rdf&TEMPLATE=../eng_index1.html&MAXITEMS=4](http://www.progecad.com/eng_index.php?XMLFILE=http://news.progesoft.com/intellicad/index.rdf&TEMPLATE=../eng_index1.html&MAXITEMS=4)

 under WINE. Works great on ubuntu 8.04 after initial dll warning on startup. 1 click gets rid of that. It is an almost clone of autocad Lt and uses all dwg formats. If you want a full autocad clone (3d) the full progecad costs a lot less than Autocad.

---

### Post by C.S.Cameron on 2008-10-09
I am also a mechanical engineer,
AutoCAD is the major reason I still have a Windows partition.
AutoCAD R14 is fairly stable in wine, I have had 2000 and 2005 working but did not find them stable enough to be much use.

---

### Post by colinpat on 2008-10-09
Try QCAD from Ribbon Soft. I just installed the professional version (to get manual & help etc cost 24 Euro) it will read and write to autocad. You can download and use free version to try.
A real neat cad package.

---

### Post by mb125 on 2008-11-05
I have been using acad 14 under wine with no problems, but had anyone had any luck with acad 2006 or newer?

---

