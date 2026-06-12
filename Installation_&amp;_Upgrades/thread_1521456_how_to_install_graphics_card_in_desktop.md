---
title: "how to install graphics card in desktop"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by zacattack145 on 2010-06-30
how would I install an AGP ATI Radeon x700 pro graphics card in ubuntu? every time i put in the card it never boots up.
It has an AMD Athlon 750MHz CPU, and 768 MB 133MHz of Ram

---

### Post by gordintoronto on 2010-06-30
What is your video setup before you install the card? How far does it get in booting? What version? Ubuntu only, or dual boot?

Perhaps you need to remove the old video driver before you install the "new" video card.

---

### Post by zacattack145 on 2010-07-02
I barely installed Ubuntu 10.04 on the computer with an old Nvidia graphics card with 32MB on it. There is no graphics driver installed and there is no other operating system on it. It boots up the beginning part  (the part with the BIOS setup) and then ubuntu tries to boot up but has an error message where it counts up to 2 hundred and something and then stops and nothing happens.
(hope that wasn't too confusing)

---

### Post by davidmohammed on 2010-07-02
...

can you give any more detail of "counting" - what was counting.  any error messages before.  

When you say it stops - do you mean a black screen?

if you have a "black screen" problem then ...

press and hold down the shift key to display your grub. Then press e to edit. Find the line with quiet splash and add nomodeset immediately before this.

To fix it permanently

sudo nano /etc/default/grub

find the line

GRUB_CMDLINE_LINUX=""

change it to
GRUB_CMDLINE_LINUX="nomodeset"

save

then run

sudo update-grub

---

### Post by zacattack145 on 2010-07-02
I think it starts counting how many tries it takes to do something and on each try it has an error message. it starts at 20 and then goes up till 2 hundred something. after that it goes to black screen where you have to hit the restart button.
I will definitely try what you suggested.

---

