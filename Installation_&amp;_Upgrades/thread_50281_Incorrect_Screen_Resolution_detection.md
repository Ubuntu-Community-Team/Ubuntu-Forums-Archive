---
title: "Incorrect Screen Resolution detection"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by diffuser78 on 2005-07-19
Ubuntu shows my Screen Resolution as 1024x768 while my monitor supports 1280x1024. While installation it asked me and I had specified to use 1280x1024. By the way I hava a nVidia Graphics  card in my DELL Dimension 4600.

How can I manually change my screen resolution.

Please help

---

### Post by super on 2005-07-19
you can maunally change your screen res by editing /etc/X11/xorg.conf

be sure to make a back-up copy first tho  :)

---

### Post by diffuser78 on 2005-07-19
[QUOTE=super]you can maunally change your screen res by editing /etc/X11/xorg.conf

be sure to make a back-up copy first tho  :)[/QUOTE]


It didnt work...I changed my file to 1280x1024 ....but still it doesnt change.

I am attaching my xorg.conf file for your reference.

Any other option I can try,

Please help

Dan

---

### Post by damonw5 on 2005-07-19
[QUOTE=diffuser78]It didnt work...I changed my file to 1280x1024 ....but still it doesnt change.

I am attaching my xorg.conf file for your reference.

Any other option I can try,

Please help

Dan[/QUOTE]
 Hi Dan,

You xorg.conf didn't seem to attach. Try again?

Damon

---

### Post by diffuser78 on 2005-07-19
[QUOTE=damonw5]Hi Dan,

You xorg.conf didn't seem to attach. Try again?

Damon[/QUOTE]

Ok here it is.... i have names it xorg.conf.txt coz it wont attach with .conf externsion

---

### Post by mingus on 2005-07-19
You can regenerate your xorg.conf file with the new settings by:

$sudo dpkg-reconfigure xserver-xorg

Try dropping the default color depth to 16 or even 15.  Also choose the lowest resolution offerred for your desired resolution.  Resolutions are inter-dependent with refresh rates and number of colors.  The card, monitor, and driver are not always in sync.

---

### Post by diffuser78 on 2005-07-19
[QUOTE=mingus]You can regenerate your xorg.conf file with the new settings by:

$sudo dpkg-reconfigure xserver-xorg

Try dropping the default color depth to 16 or even 15.  Also choose the lowest resolution offerred for your desired resolution.  Resolutions are inter-dependent with refresh rates and number of colors.  The card, monitor, and driver are not always in sync.[/QUOTE]

Thanks man!!!

It worked for me...I got my 1280x1024 resolution.

I have started to love Ubuntu because of the support one gets from the community members.

Dan

---

### Post by mingus on 2005-07-19
[QUOTE=diffuser78]Thanks man!!!

I have started to love Ubuntu because of the support one gets from the community members.

Dan[/QUOTE]

And thank you for the kind words.

---

