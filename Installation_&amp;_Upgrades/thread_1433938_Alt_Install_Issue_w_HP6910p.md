---
title: "Alt Install Issue w/ HP6910p"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by mathgeek2000 on 2010-03-19
I'd like to do a clean install of Ubuntu 9.10 or 10.04 (when it comes out) on my HP6910p Laptop so I can take advantage of the Encrypted LVM. But when I try to install from the CD, my laptop appears to freeze. -- The Screen goes blank, and disk activity stops.
  -- This happens w/ the current 9.10 Alt. CD, and the 10.04 Beta 1 Alt CD. 

By contrast, I've installed Alt 9.10 w/ Encrypted LVM in a VirtualBox VM, running on the Laptop.-- And that works Ok.

Am I just not waiting long enough? or are there specific boot options, I haven't found?
The normal Desktop CD works great.

---

### Post by Ozymandias_117 on 2010-03-19
When trying to boot from the CD, you can press a button... Pretty sure it's esc, if not try function keys. That will change it to verbose mode, meaning it will display text as to what it's up to. This may help you see if you're freezing or it's just taking longer than you expect.

---

### Post by mathgeek2000 on 2010-03-20
The Escape Key brings me to a Text Based Install -- or so it says.
  - with the Expert option I can still erase the 'quiet' option on the install command line, and add something like vga=normal --- But I get the same issue:

   -- I see the text, as the system loads off the CD, but at some point:
   -- Blank Screen, and no CD or HDD activity.

---

### Post by mathgeek2000 on 2010-03-20
To Clarify --- w/ vga=normal added to boot command, I see:
   -- Several lines as kernel loads, etc. ...
   -- Rather than step 1: choose language, I get the blank screen.
     -- same w/ graphical or text based alt cd install.

> **mathgeek2000 said:**
> The Escape Key brings me to a Text Based Install -- or so it says.
  - with the Expert option I can still erase the 'quiet' option on the install command line, and add something like vga=normal --- But I get the same issue:

   -- I see the text, as the system loads off the CD, but at some point:
   -- Blank Screen, and no CD or HDD activity.

---

### Post by mathgeek2000 on 2010-03-22
I've Solved it, I think ... --
 Press F6 to get the command line to Boot, manually edit it inserting 
    'VGA=788' ==>> that gives me the correct resolution, and the installation menu. 
   (Note: Currently there is a known bug in 10.04 Beta re: Encrypted LVMs, 
         but this worked w/ 9.10)

> **mathgeek2000 said:**
> To Clarify --- w/ vga=normal added to boot command, I see: ... Massive Issues ...

---

