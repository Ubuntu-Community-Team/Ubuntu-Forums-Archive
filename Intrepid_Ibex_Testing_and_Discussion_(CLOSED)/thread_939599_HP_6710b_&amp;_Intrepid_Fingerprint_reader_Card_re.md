---
title: "HP 6710b &amp; Intrepid: Fingerprint reader? Card reader?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stokedfish on 2008-10-06
Hello,

has anybody gotten to work the fingerprint and card reader on Kubuntu Intrepid with a HP 6710b notebook?

Yes? How? I'm lost...

---

### Post by sergiom99 on 2008-10-06
SD cards work out of the box.
MS cards are a Sony proprietary format and there is no kernel support for linux yet. Someone has to code the drivers or something like that.
There are tons of postings about this topic in the forums.

---

### Post by alphanaut on 2008-10-06
I also have an 6710b w/ intrepid. The only thing that I haven't fix yet is fingerprint logon. 
$ sudo apt-get install aes2501-wy 
$ aes2501
gets the fingerprintscanner to display what is scanned.

pls post if solved.

---

### Post by stokedfish on 2008-10-06
> **sergiom99 said:**
> SD cards work out of the box.

It doesn't. When I plug in my SD card, nothing happens...

It also doesn't show up in whatever filemanager I try.

(konqueror, dolphin, krusader, mc...)

> **sergiom99 said:**
> There are tons of postings about this topic in the forums.

Sorry, but I didn't find one single thread on here that helped me to get my card reader to run...

---

### Post by stokedfish on 2008-10-06
So I've just reformatted my SD card and did another dist-upgrade...

And yes, now it works. Wow! Thanks!!!  :)

Fingerprint reader left...   (not that important for me, actually)

---

### Post by stokedfish on 2008-10-09
> **alphanaut said:**
> I also have an 6710b w/ intrepid. The only thing that I haven't fix yet is fingerprint logon. 
$ sudo apt-get install aes2501-wy 
$ aes2501
gets the fingerprintscanner to display what is scanned.

pls post if solved.

Cool, this works. I still don't know how to enable fingerprint login though. Is it even possible? Anyone? Also, what about the special laptop keys? Fn + F9/F10 for brightness etc...none of them works for me.

---

### Post by jesuisbenjamin on 2008-10-09
hey there,

i have a Dell Vostro 1510 with fingerprint scanner, do you know if i can use the same program/driver as you used? 

What should i look at to find this out?

Thanks.

---

