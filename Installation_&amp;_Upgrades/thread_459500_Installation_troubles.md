---
title: "Installation troubles"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Lucideus on 2007-05-30
I'm dual-booting, btw.

Anyways, I have a 40GB partition set aside for Ubuntu, partitioning was all fine, but when I boot to the disc, it takes me to the first Ubuntu screen, ("Start or Install Ubu...etc..."), and whenever I try to start/install it, it starts loading green text in the top left with ellipses (...'s) extending all the way across the screen.

Once that all finishes, it takes me to a black screen with a blinking _ in the top left, and across the bottom of the screen it just gives a bunch of random numbers end such, like "err 0000000 E-something followed with numbers" and it stays on this screen till I manually turn the PC off.

This is with 7.04, I tried it with 6.06 too and after it did the green text dealy, it loaded up a screen filled with "Unknown Error 000000 E-some-odd ########" and so on all the way down the screen, then it reboots.

Can anyone offer advice?  I installed it fine on an older computer, doing the same stuff I did this time, yet I keep getting those errors.

(If you need exact info on the errors, I'll go try it again and write some of it down)

---

### Post by merlinus on 2007-05-30
Try Safe Mode.  If that does not work, you can download the alternate cd from ubuntu.com.

It is a text-based installer, so should not have what seems to be video problems.

Good luck!

-merlin

---

### Post by Lucideus on 2007-05-30
Thanks for the quick reply, I'll go and try that now.

---

### Post by Lucideus on 2007-05-30
Well, the safe mode didn't work, just gave me the same error screen as earlier.

And by alternate download, you mean X/Kubuntu?  I didn't see any text-based installers, so if you have a direct link that'd be nice.

---

### Post by merlinus on 2007-05-30
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

At the bottom of the page, below the green "Start Download" icon, there is a checkbox for downloading the alternate desktop cd.

Click in the checkbox, click on Start Download, choose save to disk, and away you go....

-merlin

---

### Post by Lucideus on 2007-05-30
Huh...I feel kinda stupid now that I see it there......thanks again, heh.

---

### Post by Lucideus on 2007-05-30
Alright, I tried that, did the same stuff as before.

Green text about loading the install, and then the almost blank error screen.  Some of the error text is "err 00000000 EIF c240c280 (can't remember exact numbers)" and then other numbers and such.

Any other possible advice? This is really buggin' me.

---

### Post by Lucideus on 2007-05-31
bump

---

### Post by need help on 2007-05-31
Just so you know I am having very similar issues... I ordered the free disk ubuntu 7.04. I first installed it on my brothers computer.. works great.

my computers turn. I replaced my hard drive. (wanting fresh start) and every time I attempt to install I have some sort of issed that makes me pull my hair out.

I too am getting similar error messages. I think the issue I am having is the fact that I am using a Intel p3
processor- My brothers was an athlon, not sure which one. 

I have tested my memory, wiped the hard drive. changed options in bios. so just so you know Im in the same boat... pulling out my hair because it works so good on my brothers computer

---

### Post by Lucideus on 2007-05-31
Yep, the disc I used works great on another computer (about 5 years old now), so it's definitely not any of the discs I'm using, but it seems to despise my compute for whatever reason.

And other people are having the same problem, so I think it's just a bug and we have to wait for a fix.

---

### Post by Lucideus on 2007-05-31
Got past that now by adding 'acpi=off noacpi' to the boot line, now I get this error:

[http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg](http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg)

Also, my computer's an HP a1230n, if you need specs just ask.

---

