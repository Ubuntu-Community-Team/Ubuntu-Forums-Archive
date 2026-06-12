---
title: "can not run live cd monitor input out of range"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by h4xor66 on 2010-11-07
this has happened with a few different attempts of ubuntu based distros lately ... i try to boot a live cd it gets to where it starts loading and the monitor pops off and says input out of range  ... im aware that this is a known bug with xorg choosing either the wrong resolution or refresh rate ... but what the heck are we supposed to do , i can't get far enough into the boot process that i can open a terminal and try to bypass xorg ... so will all future distributions of ubuntu just be out of the question for me ?  if you ask me what needs to be done is make the installer ASK what resolution you want to attempt to boot at .... similar to what puppy does 

is there anything i can do ?

---

### Post by sikander3786 on 2010-11-07
You should be presented with a resolution option at boot, I agree.

For a workaround, you can try the **nomodese**t parameter.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by h4xor66 on 2010-11-08
excellent that did it ... thank you very much ... i had googled about ubuntu boot errors but never thought to look for live cd options haha  .... thank you again

---

