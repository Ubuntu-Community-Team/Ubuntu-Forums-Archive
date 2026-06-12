---
title: "Black flashing screen after upgrade to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by mwedemeier on 2011-04-29
Thank you for reading and any help is greatly appreciated. I am also new to Ubuntu, so please forgive dumb questions.

I currently get a mostly black flashing screen after I select the OS in the grub screen. It appears to boot, I just can't see anything. I do hear startup sounds. 

I can however boot if I add 'nomodeset' by pressing 'e' at the grub screen. 

This is what I get with the following commands.

**lpsci | grep VGA **

[COLOR=#000000][FONT=Tahoma]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GTX 460M] (rev a1)[/FONT][/COLOR]

** glxinfo | grep Vendor**

[COLOR=#000000][FONT=Tahoma]The program 'glxinfo' is currently not installed.  You can install it by typing:
 sudo apt-get install mesa-utils[/FONT][/COLOR]

---

### Post by mwedemeier on 2011-04-29
I'm guessing no one else is having this problem.

---

### Post by mathdater on 2011-04-30
I am having same problem. I upgraded both laptop and desktop both are useless now .

---

