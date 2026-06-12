---
title: "Lubuntu installation on NC10 Netbook not working"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by cibeles on 2016-07-30
Hi, 
I'm trying to install Lubuntu 16.04 on a Samsung NC10 netbook and it's not working. I go through the whole installation process without an issue and as soon as I try to reboot I get to this screen and it never moves from it.[ATTACH=CONFIG]270465[/ATTACH]

If I try to do the trying option before installing nothing works either I don't get anything working, but I go through all the screens and partition options, naming the computer, creating password etc if I chose the option of directly installing. I have verified that the iso downloaded is okay and usb used for installation has nos issues. I used Rufus to create the installation usb

I would like to add that I have an issue at bios level that may or may not be relevant. I have a BIOS password and when I start the netbook when it reaches the BIOS password screen it starts typing something without my input. If I delete the characters it stops typing and I can actually enter the right password without a problem.

Can anyone help me?

Thanks a million in advance

---

### Post by cibeles on 2016-07-31
Bumping it to see if anyone out there can help me.

---

### Post by sudodus on 2016-08-01
1. Did you try from a Lubuntu 16.04.1 iso file (the first point release with several bug-fixes)?

2. It seems like a problem with the graphics. Which graphics chip is there in the computer?

- It **Intel** graphics, it should work better in Lubuntu **16.04.1** (I guess this is the case because you mention, that it is a netbook.)

- If **nvidia** graphics, it might help to use the boot option **nomodeset**, and after that install a proprietary driver.

---

### Post by cibeles on 2016-08-01
Thanks for your reply sudodus.

The iso I downloaded is a lubuntu-16.04-desktop-i386. The netbook has integrated Intel graphics.

By Lubuntu 16.04.1 do you mean using the non-graphical installer and forcing graphic drivers? I had a problem with another computer years back and I had to do that. Totally forgot about that issue

---

### Post by sudodus on 2016-08-01
An important bug affecting Intel graphics is fixed in the version 16.04.1 LTS, so that you should be able to use the desktop installer.

There are desktop and alternate iso files of both 16.04 and 16.04.1, and there are many reasons to select 16.04.1 (many bugs are fixed and many packages are updated, so it will be much more convenient to make the installed system up to date with all security updates and bug-fixes).

Maybe it is better to download the 'alternate' iso file with the text mode installer.

- advantage: it needs no working graphical mode, as you already know. We are not sure if your bug is not fixed (yet), and you might be able to work around it via the alternate installer.

- disadvantage: you cannot test it live, 'Try Lubuntu', and the dialogue is more difficult (but it works, I have tested it).

---

### Post by cibeles on 2016-08-01
I'll try your suggestion with 16.04.1 and if that doesn't work the text installer and let you know if it works. 

Thanks a million for the help :D :D

---

