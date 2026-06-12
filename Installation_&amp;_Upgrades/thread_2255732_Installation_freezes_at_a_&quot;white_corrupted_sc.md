---
title: "Installation freezes at a &quot;white corrupted screen&quot;"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by luca27 on 2014-12-07
Hi all, i'm having problem at installing ubuntu 14.10
The dvd works fine on another pc..

In this pc, after the loading pages:

[IMG]http://puu.sh/dkz8v/d4e0d03d03.jpg[/IMG]

and,

[IMG]http://puu.sh/dkz7R/445da64221.jpg[/IMG]

There is this:

[IMG]http://puu.sh/dkz97/1cbe7c0390.jpg[/IMG]

And there it blocks and doesn't go on..


I have no idea why that happens...


In the bios these are my options: (the bios with less options i ever seen)

[http://puu.sh/dkzi2/89f1775e20.jpg](http://puu.sh/dkzi2/89f1775e20.jpg)
[http://puu.sh/dkzhF/3177067c73.jpg](http://puu.sh/dkzhF/3177067c73.jpg)
[http://puu.sh/dkzgS/f767e55752.jpg](http://puu.sh/dkzgS/f767e55752.jpg)
[http://puu.sh/dkzfA/a143857cc2.jpg](http://puu.sh/dkzfA/a143857cc2.jpg)
[http://puu.sh/dkzfg/20370d899d.jpg](http://puu.sh/dkzfg/20370d899d.jpg)


I have no idea how to solve the problem.... 
Shall someone help me?

Ah, the installation of the ubuntu 9.4 worked, but i wanted the latest version...

Thanks everyone and sorry for my english :)


-


Tried again, now is like that:

[IMG]http://puu.sh/dkAnT/c8ade9d7dc.jpg[/IMG]

](*,)

--

Following these suggestions, i got to install it

> Have you tried holding down F6 during a cold boot, select language, then F6 again to get the options on the lower right to show up. Select nolapic, EDD=On, and nomodeset. Press ENTER. Next, down arrow to the second line which is the Install line. DO NOT PRESS ENTER OR A LEFT OR RIGHT ARROW!!Now back space and delete quiet and splash with nomodeset. Now press ENTER. The installation will begin and if it hangs up now, you will see what was the last process/script that completed.

However now, when it starts it blocks on a black screen. (after display for a short time a purple screen)

---

### Post by Mark Phelps on 2014-12-07
Some video drivers that worked fine with older Ubuntu versions won't work with the current one.  Since we don't know what video chip your PC is using, boot to the Live media, select the Try Ubuntu option, and when you finally get to a desktop, open a terminal, enter "lspci" (without the quotes), look for the line containint "VGA" and post that information back here.

---

### Post by grahammechanical on 2014-12-07
Read through this link and work your way down to the heading: Changing the CDs Default Boot Options and note the advice given in section 6 - F6, Try the nomodeset option.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by luca27 on 2014-12-09
Thanks all, 
I solved setting the nomodeset in the grub boot :popcorn:

---

