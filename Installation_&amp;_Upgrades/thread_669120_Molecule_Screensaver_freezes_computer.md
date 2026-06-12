---
title: "Molecule Screensaver freezes computer"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by curiousnoob on 2008-01-16
I was previewing the different screensavers and when I tried Molecule the entire computer froze while it said it was "building" the molecule.  
The problem is now whenever I go to the screensaver options window it is still on Molecule and freezes my computer again.  
This is a fresh install with no other odd programs added.  Any help would be greatly appreciated.

---

### Post by kellemes on 2008-01-16
> **curiousnoob said:**
> I was previewing the different screensavers and when I tried Molecule the entire computer froze while it said it was "building" the molecule.  
The problem is now whenever I go to the screensaver options window it is still on Molecule and freezes my computer again.  
This is a fresh install with no other odd programs added.  Any help would be greatly appreciated.

Does /var/log/messages.log tell you something?

---

### Post by curiousnoob on 2008-01-17
> **kellemes said:**
> Does /var/log/messages.log tell you something?
I get this message:
bash: /var/log/messages.log: No such file or directory

---

### Post by Partyboi2 on 2008-01-18
If looking by terminal
```
cat /var/log/messages |more
```
or you can use
```
gksudo gedit /var/log/messages
```
if looking via nautilus opening up /var/logs and look for ```
messages
``` which is a text file

---

### Post by curiousnoob on 2008-01-18
> **Partyboi2 said:**
> If looking by terminal
```
cat /var/log/messages |more
```
or you can use
```
gksudo gedit /var/log/messages
```
if looking via nautilus opening up /var/logs and look for ```
messages
``` which is a text file

There is no entry recorded at all.  It's as if the computer freezes before anything can even be logged.

---

### Post by bpont on 2008-06-20
> **curiousnoob said:**
> I was previewing the different screensavers and when I tried Molecule the entire computer froze while it said it was "building" the molecule.  
The problem is now whenever I go to the screensaver options window it is still on Molecule and freezes my computer again.  
This is a fresh install with no other odd programs added.  Any help would be greatly appreciated.

I had the exact same problem...freezes everything...can't drop into a shell and am forced to reboot.

This molecule screensaver has been a bug for YEARS...it should simply be removed from the screensaver list by now.

---

