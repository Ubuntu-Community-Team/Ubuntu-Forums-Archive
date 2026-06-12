---
title: "linux boot problem! please help"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by zanzes on 2010-12-24
hey my problem is thet i cant boot linux iv tried to boot fedora 14, red hat 9, centos and ubuntu 32 and 64 bit and non of them boot i know they all work and i have installed them on other computers

the boot is set to boot from cd 
i dont get any error message or anything it just boots windows 7 and i wonna dual boot windows 7 64 bit and ubuntu 64 bit
i can use wubi but i wonna use the intire 70 gb partition iv made for it and wubi is max 30 gb
where have i gone wrong? it works on all my other computers
this is a packard bell computer originaly with vista but now running windows 7
any help would be much appreciated thx in advance

---

### Post by dino99 on 2010-12-24
welcome,

dont expect serious things with wubi, make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

booting from cd/dvd: if you have some issue, boot by adding noacpi

---

### Post by theasprint on 2010-12-24
Hi,

Have you at least tried booting from the LiveCD (That means Try Ubuntu without changes)

This is because trying Ubuntu (booting from LiveCD) actually gives confirmation if your PC is compatible with Ubuntu.

And you would need to specify further about "can't boot Linux"
I mean what do you have right now?
If you want to boot Linux then what do you see/what happens?

Thanks.

---

### Post by zanzes on 2010-12-24
> **dino99 said:**
> welcome,

dont expect serious things with wubi, make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

booting from cd/dvd: if you have some issue, boot by adding noacpi




i know wubi isnt serious the problem is that i can boot from a cd even though iv set the settings to boot from cd

---

### Post by zanzes on 2010-12-24
> **theasprint said:**
> Hi,

Have you at least tried booting from the LiveCD (That means Try Ubuntu without changes)

This is because trying Ubuntu (booting from LiveCD) actually gives confirmation if your PC is compatible with Ubuntu.

And you would need to specify further about "can't boot Linux"
I mean what do you have right now?
If you want to boot Linux then what do you see/what happens?

Thanks.

i know what a live cd is and yes i have tryed the fedora 14 is also a live cd
you really need to weed my post again *** i wrote i have windows 7 now
and as i also wrote i see nothing no warning message no nothing it just boots windows 7

---

### Post by zanzes on 2010-12-24
btw sorry about my bad spelling im danish :p

---

### Post by zanzes on 2010-12-24
if you need more details please specifi what you need to kwon and il try to provide the details

---

### Post by dino99 on 2010-12-24
so i've googled a little more and the problem seems to be the tatooed packard hardware:

[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=da&u=http%3A%2F%2Fwww.commentcamarche.net%2Fforum%2Faffich-2060692-packard-bell-installer-linux](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=da&u=http%3A%2F%2Fwww.commentcamarche.net%2Fforum%2Faffich-2060692-packard-bell-installer-linux)

---

### Post by theasprint on 2010-12-24
Hi,

So now I see that your problem is that when you put the Ubuntu (or any other Linux) Disc, you are unable to use it?

I can only think of one possible problem.

One is your CD-Drive. Your CD-Drive may not be able to read any bootable discs.
I've met problems like this before and there is no solution to that, just workarounds/replacements.
So if you want to boot Ubuntu, you can try booting from a USB drive instead.
In this link: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
At #2, there is a guide on how to put Ubuntu into the USB so that you can install from the USB just like a disc.

Another problem may be your graphics card.
But I ruled out that problem because you would rather see a blank screen instead of booting into Windows 7.

You might also want to burn the .iso file on another disc? (Perhaps the disc is spoilt)

Hope this helps, but I am sure that it is a PC/Hardware problem.

---

### Post by zanzes on 2010-12-24
> **theasprint said:**
> Hi,

So now I see that your problem is that when you put the Ubuntu (or any other Linux) Disc, you are unable to use it?

I can only think of one possible problem.

One is your CD-Drive. Your CD-Drive may not be able to read any bootable discs.
I've met problems like this before and there is no solution to that, just workarounds/replacements.
So if you want to boot Ubuntu, you can try booting from a USB drive instead.
In this link: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
At #2, there is a guide on how to put Ubuntu into the USB so that you can install from the USB just like a disc.

Another problem may be your graphics card.
But I ruled out that problem because you would rather see a blank screen instead of booting into Windows 7.

You might also want to burn the .iso file on another disc? (Perhaps the disc is spoilt)

Hope this helps, but I am sure that it is a PC/Hardware problem.



thx il try to boot from a usb drive as you suggest  but i know that i can boot from the cd drive as i just used it to install windows 7 :)

---

### Post by zanzes on 2010-12-25
when i boot from a usb drive i get an error message saying 
no default or ui configuration directive found
boot:_

---

