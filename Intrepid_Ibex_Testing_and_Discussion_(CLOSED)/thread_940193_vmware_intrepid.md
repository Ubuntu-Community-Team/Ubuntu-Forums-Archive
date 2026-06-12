---
title: "vmware intrepid"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Dan The Man on 2008-10-06
Does anyone have vmware working in intrepid? I've tried to install server and player but it just bombs. I have an XP vm which took me weeks to make (it has msSQLserver #-o ) I really would like to get this running, because Notepad++ is the best code editor (don't laugh 'till you've tried it!). was made with msvpc2007 (virtualbox wont do it). Looks like tomorrow could be a hardy re-install, ouch!

---

### Post by sp200606 on 2008-10-16
Hi,
Notepad++ works fine with Wine...
As for vmware, I'm still struggling with it.

regards

---

### Post by dabl on 2008-10-16
Yep.

VMWare Player 2.5 works well, except in my Win XP VM there is a problem with the arrow keys on the keyboard, as in they don't work at all.  All other keys and the mouse work fine.  I believe the "cursor keys" issue is a bug that VMWare is working on.

---

### Post by conundrumx on 2008-10-16
I'm in the same boat as dabl.  Workstation 6.5 runs fine, arrows keys cause oddness.

---

### Post by abarilla on 2008-10-17
I have the same problem with arrow keys in vmware server 2.

---

### Post by conundrumx on 2008-10-20
Any news on this?  Really making life difficult...

---

### Post by billyShears on 2008-10-20
I'm having the same problem with arrow keys...as a workaround I use the arrow keys on numeric keypad

---

### Post by conundrumx on 2008-10-20
It looks like the culprit for this is Intrepid's X configuration (or maybe the new X included therein?).  Some insight from a MOTU or something would be hugely helpful.

---

### Post by jmacak on 2008-10-20
Hi 

I had the same arrow problem and found this:

[http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html)

hth

joe

---

### Post by dabl on 2008-10-24
Just found this -- but the link appears broken.

???

Can you post the fix, if it exists?  :)

EDIT:  NEVER MIND -- link works from my alternate location in the Eagle's Nest.  ;-)

---

### Post by mikio on 2008-10-26
hi everybody,
i had the same problem with arrow keys and found the solution here:
[http://www.ultimalinux.com/wiki/VMware](http://www.ultimalinux.com/wiki/VMware)

following their instructions i created the following file:

~/.vmware/config

with the following line:

xkeymap.nokeycodeMap = true

problem solved!

---

### Post by dabl on 2008-10-26
> **mikio said:**
> hi everybody,
i had the same problem with arrow keys and found the solution here:
[http://www.ultimalinux.com/wiki/VMware](http://www.ultimalinux.com/wiki/VMware)

following their instructions i created the following file:

~/.vmware/config

with the following line:

xkeymap.nokeycodeMap = true

problem solved!


Yep, I confirm it.  Very nice find -- thanks!

:guitar:

---

