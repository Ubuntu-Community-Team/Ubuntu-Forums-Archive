---
title: "Problems installing"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by webmeister87 on 2008-02-09
Hey all,

First time user here, and having some problems.

I downloaded the "normal" CD, for my AMD 64. When i boot from CD i get the simple menu, with install, check CD, etc. I have checked the CD and it says its fine, but when i go to install it does this:

[LIST]
[*]Goes to the screen with the orange bar scrolling back and forth
[*]Turns into an install/progress bar
[*]The screen flickers, and looks all messed up for a second or two, with like a small circle in the middle
[*]It goes to a command promt looking screen, and sits there doing nothing
[*]Once it told me to take the CD out, close the tray and reboot machine... but it booted right into XP
[/LIST]

What can i do to try and get around this? I really want to give it a try as my PC is due for a format anyways.

Hardware:
AMD Athlon 64 3800+
ASUS A8N-SLi Premium
512mb Corsair RAM (my other sticks died, but 512mb should be fine right?)
Radeon X1800 512mb

Thanks for any help,

Gareth

---

### Post by webmeister87 on 2008-02-09
Shameless bump :(

Ive had quite a look around and cant find anything about whats happening.

Please help!

Thanks,

Gareth

---

### Post by oldos2er on 2008-02-09
Have you tried safe graphics mode?

---

### Post by Pumalite on 2008-02-09
You need to install with the Alternate CD:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'
Do md5sum on the iso and burn as image at 4x or less in good quality CD-R media.

---

### Post by webmeister87 on 2008-02-10
Thanks for your replies!

I did what each of you said, but unfortunatly neither worked.

I made 2 new partitions for linux, 1 main one and a swap one, and it installed without a problem. When it comes to starting up though, its almost the same as my last post described.

I get an orange bar under the Ubuntu logo, where is shows its loading progress.

When the progress bar hits 100%, it looks like it tries to load the GUI/desktop/whatever. I see two "Ubuntu" symbols on my screen, but the quality is aweful (wrong colors, distorted, i hope u know what im talking about here...)

It then flashes off (after about 1 second), and goes to a command prompt style screen. On the screen it has 4 lines, one of which i can remember is:

Checking battery state               [OK]

The last one is something about running scripts            [OK]
Then it just sits there.

When i hit ctrl-alt-del it scrolls a page of things its stopping and then it just dies/reboots (cant remember).

Please give any more info/ideas

Many thanks

Gareth

---

### Post by Pumalite on 2008-02-10
Are you wired to the Internet during installation?

---

### Post by webmeister87 on 2008-02-10
Yeah.

Ethernet ADSL modem > router > PC

---

### Post by Pumalite on 2008-02-10
Make sure you set the router to provide you with DHCP.

---

### Post by webmeister87 on 2008-02-10
In windows i assign my own IP, but DHCP is deffo working as my dads laptop uses it.

Any other idea's?

---

### Post by Pumalite on 2008-02-10
Here you have a guide and a collection of boot parameters to try one at the time or in combination:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

Sometimes removing 'quiet' and/or 'splash' works.

---

### Post by Partyboi2 on 2008-02-10
If that does not work, try changing to a terminal (Ctrl+Alt+F2) then reconfigure xserver
```
 sudo dpkg-reconfigure xserver-xorg
``` choose vesa as the driver and answer all the questions, if unsure choose the default answers. then type
```
startx
``` If this works it will allow you to get to the desktop where you can sort out your driver problem, (if its a graphics card problem)

---

