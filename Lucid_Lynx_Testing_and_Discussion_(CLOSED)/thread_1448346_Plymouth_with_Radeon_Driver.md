---
title: "Plymouth with Radeon Driver"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-04-06
Hey guys,
I've used Lucid since A2 and Plymouth used to look great, but now it doesn't load at all?  I just get the 'broken pipe' message and it jumps straight to GDM.  
Obviously it's not essential but makes the whole process look a little nicer!
I've tried:
```
sudo apt-get install --reinstall plymouth
```
..but had no luck.
Using the radeon driver on a HD3650.
Any advice?
Cheers,
JC

---

### Post by JCoster on 2010-04-11
sorry- bump!
JC

---

### Post by JCoster on 2010-04-14
Final try, I promise- bump!
JC

---

### Post by teh603 on 2010-04-14
I'm not sure its just radeon. I've got intel graphics and I get broken pipe messages too.

What the hell kind of pipe are they referring to, anyway?

---

### Post by JCoster on 2010-04-15
There's something somewhere in the forum about what it means...  But still, couldn't it do this silently without removing my boot splash? (if that is indeed the cause...)

---

### Post by JCoster on 2010-04-17
Ok well I have finally solved this problem by:
```
sudo apt-get install plymouth-theme*
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```
..after choosing a new alternative (I don't think any themes were installed originally as no alternatives were shown the first time..?  Must have been borked by an update..)

Just an FYI.
JC

---

