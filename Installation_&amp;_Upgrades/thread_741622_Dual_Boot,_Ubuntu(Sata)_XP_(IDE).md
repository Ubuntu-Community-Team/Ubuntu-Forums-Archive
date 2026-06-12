---
title: "Dual Boot, Ubuntu(Sata) XP (IDE)"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by cribdeth on 2008-03-31
I've allready got both of them installed, I've seen some install procedure's for a XP Sata Ubuntu IDE install, but I want to do it the other way around.  I don't plan on using my XP install much and I don't want to put in on my better drive.  Both OS' are installed and functioning allready.  How do I set this up?  (Only been using Ubuntu for a week so forgive my n00b questions)

---

### Post by chewearn on 2008-03-31
Ok, I'm going to fire some questions, in order to understand your situation:

1. When you said you already have both of them set-up, did you mean you install both OS separately?
2. I.e. when you install ubuntu, did you have XP HD plug-in and let the ubuntu installer auto-detect it?
3. When you boot up, did you see the boot menu (grub menu), where you can select the OS to boot into?

---

### Post by cribdeth on 2008-04-02
1. When you said you already have both of them set-up, did you mean you install both OS separately?

A: Yes, I installed both of them separately (XP came after Ubuntu) and it was before I really thought about dual boot.  I've just been working with Ubuntu for about a week and wasn't even aware that this was possible.

2. I.e. when you install ubuntu, did you have XP HD plug-in and let the ubuntu installer auto-detect it?

A:  I did not, as above I installed XP after Ubuntu, and I did not set up a dual boot from Windows XP.

3. When you boot up, did you see the boot menu (grub menu), where you can select the OS to boot into?

A: I don't believe so, what exactly am I looking for?

---

### Post by chewearn on 2008-04-02
Ok, here is what you should do:

1. Plug in both harddisks
2. Boot into ubuntu
3. Post the output of the command below.  Take note of the XP partition designation (or post back the results)
```
sudo fdisk -l
```

4. Edit /boot/grubmenu.lst, add the entries for XP.
```
gksu gedit /boot/grub/menu.lst
```

At the bottom of the file, you need to append the lines to boot XP; I will exercise my google-fu and give you the answer in a while :lol:

---

### Post by chewearn on 2008-04-02
Ok, the addition to menu.lst should look something like this:
```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1
```

---

