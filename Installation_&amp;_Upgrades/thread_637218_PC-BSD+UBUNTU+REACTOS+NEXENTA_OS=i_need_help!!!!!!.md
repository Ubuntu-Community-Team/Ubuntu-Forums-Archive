---
title: "PC-BSD+UBUNTU+REACTOS+NEXENTA OS=i need help!!!!!!!!!!!!!!!!"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by alex1996arm on 2007-12-10
OK HERES MY SETUP,
UBUNTU HD0,0
REACTOS HD 0.1
PC-BSD HD0.2
NEXENTA OS HD0.4

I INSTALL   UBUNTU  REACTOS PC-BSD
AND I GET TO NEXENTA OS ,IT OVERWRITE UBUNTU GRUB SO I INSTALL UBUNTU AGAIN
THIS TIME I ADD ALL MY OS TO GRUB AND I ADD NEXENTA 
 ```
title		NEXENTA
root		(hd0,3)
makeactive
chainloader	+1

``` 

HERE IS MY ENTRY

AND IT GIVES ME ERROR 13](*,)](*,)
 

THANKS TO ANYONE WHO HELPS

---

### Post by alex1996arm on 2007-12-12
anyone??:(

---

### Post by LaRoza on 2007-12-12
They entry you made is like the Windows ones, is that the way it is supposed to be?

-EDIT: I found [this]("http://www.gnusolaris.org/gswiki/FAQ#head-29d6b16cec20c3a417550e4f9743904ebd19898c") 

DON'T USE ALL CAPS IN THE FUTURE, IT REDUCES READABILITY AND MAKES IT DIFFICULT TO READ.

---

### Post by alex1996arm on 2007-12-16
thanks for the help!!:)\\:D/\\:D/
but ive only got half the problem solved.
Ill  notify you when ive fixed it:lolflag:

---

### Post by alex1996arm on 2007-12-18
and in the future i will not  ever ever ever in any planet,galaxies,universe,or any of the parallel dimensions will write with all caps:lolflag::)

---

