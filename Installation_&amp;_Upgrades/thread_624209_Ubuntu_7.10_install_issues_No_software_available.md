---
title: "Ubuntu 7.10 install issues No software available"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by melenor on 2007-11-26
I just installed ubuntu 7.10 for the third time, hopeing to get rid of this problem with no succuss, My problem is that when i click "add and remove programs" and i click the program i want to install it says this 

[B]The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection.[/B]

then it downloads 6 things then i click on the program again hoping that it would now install it, and the message comes up again. and when i looked around at the programs most of the programs listed say

**"..... cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."**

which worked on my last ubuntu this applies for things like Gnome partition edditor,  and many others and other programs just say 
**"This application is provided by the Ubuntu community."** inside the description area. Is there any way to fix this or should i just download 7.04 again and try installing it again?

PS when i go to restricted drivers to enable the ATI driver it comes up with this error message
 [B]The software source for the package

   xorg-driver-fglrx

 is not enabled.[/B]

thank you for your help.

---

### Post by danutzmilea on 2008-03-01
I´m having the same problem. With both the synaptic installer and my ati drivers. I don´t know why :(

---

### Post by deepclutch on 2008-03-01
a que:do u guys installed amd64 version of ubuntu on intel 32-bit systems?
or vice versa? :?

---

### Post by rabrandom on 2008-03-04
Yes!! I am having this exact same problem!! I thought it was just me having the 'anti'-midest touch - where everything turns to s@*# when i touch it.

Everything reported above is the same for me down to the last detail.

Additionally, I cannot install packages. The progam isn't working properly.

Thanks in advance for any assistance someone can give.

---

### Post by taurus on 2008-03-04
> **rabrandom said:**
> Yes!! I am having this exact same problem!! I thought it was just me having the 'anti'-midest touch - where everything turns to s@*# when i touch it.

Everything reported above is the same for me down to the last detail.

Additionally, I cannot install packages. The progam isn't working properly.

Thanks in advance for any assistance someone can give.

Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

