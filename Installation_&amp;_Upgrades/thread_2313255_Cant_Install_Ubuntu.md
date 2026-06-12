---
title: "Cant Install Ubuntu"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by sofia10 on 2016-02-10
everytime i install ubuntu or any other linux except debian...i have tried many. anyways it installs fine and runs great but when i restart it and try to turn the computer on again it freaks out  it just says kernel bugsoft lockup #0cpu stuck for 22s 

now i have no idea how to make it work i have amd drivers and i guess linux hates it 

im on windows atm so i cant get lspci but heres what i can say

processor  AMD-A8-7600 Radeon R7, 10 compute cores 4c+6g 3.10 GHz

and i guess i have 2 graphic cards 

AND Radeon R9 255 

AMD Radeon r7

idk if any of that will help but its something i also have no clue where to post this

---

### Post by Vladlenin5000 on 2016-02-11
Hi and welcome.

What AMD drivers and how have you installed them?

---

### Post by sofia10 on 2016-02-11
well all i know is what i said in the post and no i havent installed the drivers i get wifi but on debian i install firmware-linux-nonfree and firmware-realtek but on ubuntu i dont install anything related to drivers

---

### Post by Vladlenin5000 on 2016-02-11
So perhaps you should... AMD APUs such as yours usually require it not only for graphics.
System settings > Software Properties > Additional drivers
Select and apply the recommended one (fglrx).

---

### Post by sofia10 on 2016-02-11
ok i tried that once but il try it again see what happens i think last time i did fglrc-updated so i guess il the regular fglrx

---

### Post by Vladlenin5000 on 2016-02-11
Most of the times it makes no difference, fglrx or fglrx-updates...
Now... What Ubuntu release are you using?

---

