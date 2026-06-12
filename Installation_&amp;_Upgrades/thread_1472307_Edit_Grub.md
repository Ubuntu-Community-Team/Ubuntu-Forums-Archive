---
title: "Edit Grub"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-05-04
I know how to edit menu.lst
I need the specific code (without a program) to change the text color. I want the text color to be a certain color, and NOT just when it's highlighted, but all the color.
 
I tried finding the code online, but when I editted, it wouldn't boot and I had to fix in recovery mode :(
 
The code I found that did NOT work was putting in "color green" right underneath the "title ubuntu" line.

---

### Post by gzarkadas on 2010-05-04
You have to specify foreground/background combinations for both text and selection, I assume. This config works in my menu.lst (note the / to separate fg/bg colors):

```
color light-cyan/black yellow/magenta

```

---

### Post by kakashi_12 on 2010-05-04
So what exactly do I type for green text? And where in the code?

---

### Post by gzarkadas on 2010-05-05
This will give you green color for text, yellow for selection in black and green background respectively:
```
color green/black yellow/green
```Anywhere before the list of kernels will be fine, as long is on a separate line.

Everything else you may need is here: [Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html"); The color information is in section 13.2.2.

---

### Post by kakashi_12 on 2010-05-05
before list of kernel? Meaning the list of the OS's?

---

### Post by tommcd on 2010-05-05
Which version of Ubuntu are you using?
Starting with Ubuntu 9.10, grub2 is now the bootloader. There is no menu.lst in grub2. 
The proceedure is different for grub2. See this tutorial from the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2#Theming](https://wiki.ubuntu.com/Grub2#Theming)
The section "Background Colors/Image" is what you want.
You should read that whole tutorial to get up to speed on grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
EDIT:
This tutorial has more detailed instructions on theming grub2:
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

---

### Post by gzarkadas on 2010-05-05
I have it before the password section. If in doubt put it at the beginning of the file, just after the first block of comments.
[INDENT]> **tommcd said:**
> Starting with Ubuntu 9.10, grub2 is now the bootloader

I have 9.10 karmic-koala and grub 0.97 which is what installed by the live cd; didn't make any changes. The change you describe must have been done at a later stage.
[/INDENT]

---

### Post by kakashi_12 on 2010-05-05
Intrepid 8.4

---

### Post by tommcd on 2010-05-06
> **gzarkadas said:**
> 
I have 9.10 karmic-koala and grub 0.97 which is what installed by the live cd; didn't make any changes. The change you describe must have been done at a later stage.

Ubuntu 9.10 used grub2.
Did you upgrade to 9.10 from 9.04, or did you do a *clean install* of 9.10?
An upgrade from 9.04 ==> 9.10 would still include grub 0.97. A clean install of 9.10 would use grub2.
[https://wiki.ubuntu.com/Grub2#Installing%20/%20Upgrading](https://wiki.ubuntu.com/Grub2#Installing%20/%20Upgrading)

---

### Post by kakashi_12 on 2010-05-06
> **gzarkadas said:**
> This will give you green color for text, yellow for selection in black and green background respectively:
```
color green/black yellow/green
```Anywhere before the list of kernels will be fine, as long is on a separate line.

Everything else you may need is here: [Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html"); The color information is in section 13.2.2.


Thanks man. It will only do the text of the OS's. Not the text outside the rectangle box. But that's ok I guess.

---

### Post by gzarkadas on 2010-05-07
> **tommcd said:**
> Ubuntu 9.10 used grub2.
Did you upgrade to 9.10 from 9.04, or did you do a *clean install* of 9.10?
An upgrade from 9.04 ==> 9.10 would still include grub 0.97. A clean install of 9.10 would use grub2.
[https://wiki.ubuntu.com/Grub2#Installing%20/%20Upgrading]("https://wiki.ubuntu.com/Grub2#Installing%20/%20Upgrading")

Well, I don't remember :-k, but the facts support the opinion that I did upgrade. It must have been so seamless that I didn't noticed! :-D

---

