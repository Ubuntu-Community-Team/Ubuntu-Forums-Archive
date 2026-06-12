---
title: "Failed 11.10 upgrade over network, Can I upgrade from the ISO?"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by winchendonsprings on 2011-11-09
[SIZE=2]I had a major failure upgrading from 11.04 to 11.10 via  update manager, leaving my system 90% unusable.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]I cannot get past  login(lightdm),and neither unity nor ubuntu-desktop is installed. I  cannot get to the desktop or grab a wireless signal without the live  image.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]I can get to the console (alt+ctrl+f1). If I could gain wireless access I  may be able to fix all broken packages in aptitude.[/SIZE]


  [SIZE=2]But I do have the 11.10 live image on a usb stick. Which is what I am writing this on now.[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]So can I try to upgrade again from the image? I'm pretty sure you could do this for 11.04.[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]I see[ this post]("http://askubuntu.com/questions/76591/how-do-i-upgrade-from-media-iso/")  is somewhat relevant but I am using the desktop image on a usb stick not a cd. If that post is relevant, I'd like to know where I can locate "cdromupgrade."[/SIZE][SIZE=2] I  could use the alternate cd image on another usb stick if that is  necessary.[/SIZE]


[SIZE=2]So is it possible to upgrade 11.04 to 11.10 via the desktop live cd without network access?

[/SIZE]  [SIZE=2]Any help would be GREATLY appreciated.[/SIZE]

---

### Post by zvacet on 2011-11-11
Until last year only alternate CD was able to do upgrade from CD.Now you can do it with livr CD,but I have to say that I never try that method.I don´t know if pst you mentioned is relevan to you if you already have 11.10.You can not upgrade that,because it is lates version.Run 

```
lsb_release -a
```

to be sure witch version do you have.

---

### Post by searchfgold6789 on 2011-11-11
Yeah, you can do that - just download the .iso file to an existing place on your hard disk (or even to the USB stick if it's got a large enough capacity) and use the commands in [the link you provided]("http://askubuntu.com/questions/76591/how-do-i-upgrade-from-media-iso/").
Good luck,
 - search
P.S. Try to fix your wifi first.

---

