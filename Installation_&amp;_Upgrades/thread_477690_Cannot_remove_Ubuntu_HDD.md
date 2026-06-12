---
title: "Cannot remove Ubuntu HDD"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by stzasnail on 2007-06-18
I am building a new computer. In my old computer I have my Ubuntu Fiesty HDD and a Windows XP Home HDD. When I try to remove my Ubuntu hard drive to put it into my new computer I get a GRUB error 21. When I go into the BIOS and set a boot order so I don't have to use GRUB, it says "Operating System not found". I can still acess Windows XP through GRUB. 

(P.S. Can somebody tell me if this is the right forum section? It seemed to be the best choice, but I didn't know.)

---

### Post by Pumalite on 2007-06-18
> **stzasnail said:**
> I am building a new computer. In my old computer I have my Ubuntu Fiesty HDD and a Windows XP Home HDD. When I try to remove my Ubuntu hard drive to put it into my new computer I get a GRUB error 21. When I go into the BIOS and set a boot order so I don't have to use GRUB, it says "Operating System not found". I can still acess Windows XP through GRUB. 

(P.S. Can somebody tell me if this is the right forum section? It seemed to be the best choice, but I didn't know.)

You could try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

And if it doesn't work, invert the order of your hard drives: make the master>slave and the slave>master. Then try again.

---

### Post by stzasnail on 2007-06-18
This is a problem with my old computer, not my new one. The old computer is a family computer and still needs to run Windows. Is there a GRUB for Windows? IF there is, how would I set it up to run instead of the Ubuntu one?

---

### Post by Pumalite on 2007-06-18
> **stzasnail said:**
> This is a problem with my old computer, not my new one. The old computer is a family computer and still needs to run Windows. Is there a GRUB for Windows? IF there is, how would I set it up to run instead of the Ubuntu one?

Plug in your Winblows CD>Recovery>FIXMBR

---

