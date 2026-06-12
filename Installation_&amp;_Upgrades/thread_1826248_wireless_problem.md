---
title: "wireless problem"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by gayden on 2011-08-16
Hi there,
i'm a new wubi user and i am facing a problem with wireless the problem is that when i click on the network sign this is what happens:-
[[IMG]http://dc13.arabsh.com/i/03293/xlgorryhw9lv.png[/IMG]]("http://v1.arabsh.com/xlgorryhw9lv.html")

so i tried using help as the following :-

[[IMG]http://dc13.arabsh.com/i/03293/5ljmhw13obz9.png[/IMG]]("http://v1.arabsh.com/5ljmhw13obz9.html")

[[IMG]http://dc13.arabsh.com/i/03293/x3l166hkssbi.png[/IMG]]("http://v1.arabsh.com/x3l166hkssbi.html")

[[IMG]http://dc13.arabsh.com/i/03293/1xhnj9sjmfga.png[/IMG]]("http://v1.arabsh.com/1xhnj9sjmfga.html")

[[IMG]http://dc13.arabsh.com/i/03293/r04lxjxh46l1.png[/IMG]]("http://v1.arabsh.com/r04lxjxh46l1.html")
so please give me a full instruction because i'm new and i know nothing about using ubuntu
and here's my laptop info :-
acer aspire 5710z
broadcom BCM 4311
and i have the newest version of ubuntu ( i'm using wubi )

thanks in advance.

---

### Post by Vakman on 2011-08-16
You could try using Ndiswrapper. I thought this was fixed in an update way back.
If you want to use Ndiswrapper, try this link: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
Original older bug?: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/206277](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/206277)

Whenever my Wireless doesn't work out of the box, I usually use Ndiswrapper.

---

### Post by gayden on 2011-08-16
ok i'll try this out and i'll tell you the result thanks :)

---

### Post by Vakman on 2011-08-16
> **gayden said:**
> ok i'll try this out and i'll tell you the result thanks :)

No problem, but the first link should actually be this: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by gayden on 2011-08-22
hi ,
i setup all the requirements and i get an error message when "make distclean"
i tried to search for the solution but nothing helped me
sorry i cant upload the image now because the internet isn't working on windows so im using chromium os flow
but i'll try to make the program using chromium then installing it on ubuntu maybe it'll work

cheers

---

### Post by gayden on 2011-08-22
hi again,
i can't compile it using chromium os flow because there's no header files for it.
so il try 2 things
1- using online compiler
2- is a question , can i compile using g++? if yes tell me how.

thanks in advance.

---

### Post by Vakman on 2011-08-24
Sorry, what exactly are you compiling?

---

### Post by gayden on 2011-08-24
hi ,
i dont know exactly im just using this command : make distclean and it  doesn't work so i tried make and it did the same and here's the error  message:-
[[IMG]http://www10.0zz0.com/2011/08/24/14/203873930.png[/IMG]]("http://www.0zz0.com")
( what the hell should i use google translate with arabic websites to upload a .png photo? )
anyway i recently installed backtrack5 and it works perfectly

anyway thanks for trying help

---

### Post by Vakman on 2011-08-25
Yes, that was another option, some distros have better support for wireless.
In regards to photo uploads, I would just put the images directly here when uploading or use [imgur]("http://imgur.com/").
Also, there should have been a deb package made for Ndiswrapper and you just grab the inf file from the windows driver to install it with Ndiswrapper. I never had to compile anything.
Glad it all worked out anyways.

---

### Post by gayden on 2011-08-26
ok thanks for the website + the problem was that the windows driver was .sys file and i didn't find the package bcuz there r another packages not installed

---

