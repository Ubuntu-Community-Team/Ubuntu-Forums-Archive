---
title: "New HD but ubuntu 16.04 doesn't install, black screen with blinking cursor"
date: 2018-02-25
forum: Installation &amp; Upgrades
---

### Post by matrooswolf on 2018-02-25
In october my hard disk crashed and I finally got round to bying a new one, a WD bleu 1TB.

I installed Ubuntu 14.04 on it (by mistake), and it installed just fine. But when I tired to upgrade to 16.04, I got an error (I don't remember which one). So I thought, why not install 16.04 LTS instead.

But intstalling 16.04 gave me a blank screen on restart, with a blinking cursor, 7 or 8 lines down from the top of the screen. I tried reinstalling 5, 6 times, each time with no luck. I then tried to reinstall 14.04, but now it gives me the same black screen with blinking cursor...

I'm sure I had 16.04 installed before on the computer, before the old disk crashed. So I have no idea what is wrong or how to fix this.

Any help would be much appreciated...

---

### Post by Bashing-om on 2018-02-25
matrooswolf; Hey 

Graphic's driver issue ?
What is the graphic(s) set ?
Maybe Try and see what results with either the "nomodeset" kernel boot parameter or booting into grub's recovery console ?

Another good test is at the login screen key combo ctl+alt+F2 to gain a console interface, can you log into the system here ?

Once there is an active terminal interface, we can talk to the system and find out what is.

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by matrooswolf on 2018-02-25
Hi Bashing-om,

Thank you for your reply.

Yes, could be this, could be that. But after a day of head scratching I found it....

In the BIOS the new disk was not listed as boot device. (I have two disks and the other one was listed as boot device). I didn't think about that, because the new disk replaced the boot disk. Once I changed the order, Ubuntu booted just normal... Phew...

---

### Post by Bashing-om on 2018-02-26
matrooswolf; Great !

You do good work :)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

