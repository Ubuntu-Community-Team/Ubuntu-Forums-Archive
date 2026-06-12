---
title: "AMD64 SATA HDD installation problem"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2008-06-01
I have tried to install ubuntu 8.04 through the live CD (which I checked for defects) AND through Wubi. However either ubuntu fails to install, any ideas?

---

### Post by Pumalite on 2008-06-01
Did you do md5sum? Did you burn at 4x or less on good quality CD-R?

---

### Post by eekfonky on 2008-06-01
Burned on good quality cd rom at low speed, but what is md5sum?

---

### Post by Pumalite on 2008-06-01
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
[http://etree.org/md5com.html](http://etree.org/md5com.html)

---

### Post by eekfonky on 2008-06-01
sorry none the wiser - I don't know that much about computers, I know a fair bit that is over my head. What does it mean? Am I able to install ubuntu 8.04 or not?

---

### Post by Pumalite on 2008-06-01
You first have to make sure you have a good disk. Download my second link to your Windows. Install it. Run an md5sum on the iso and keep on going.

166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
a96aa69961f3ed80dd7a88fae1e28196 *wubi.exe

---

### Post by eekfonky on 2008-06-01
It was for a friend of mine, he's given up with ubuntu as it's too complicated, shame really as I've had nothing but good experiences eith it

Thanks anyway

---

### Post by Pumalite on 2008-06-01
Tell your friend that in life; everything worth having is worth fighting for.

---

### Post by eekfonky on 2008-06-01
An admiral approach! lol! I am going to see him on Friday, can you give me any tips as to why AMD64 SATA HDD don't work as they run Windows with (apparently) no problem (for now anyway). I was trying to convince him ubuntu is the way forward for safety, security and stability for online needs.

He HAS to use windows for all his Cubase music, but would rather be safer with ubuntu for web stuff...help me please, let's convert the masses and put pressure on Gates & co. lol!

---

### Post by logos34 on 2008-06-01
> **eekfonky said:**
> A
He HAS to use windows for all his Cubase music, but would rather be safer with ubuntu for web stuff...

You might mention this:
[Cubase runs on Linux (ubuntu 7.10)]("http://google-cyber.blogspot.com/")

There's even a YouTube tut, apparently.  But I'm not sure how much truth there is to the claim.  (Cubase isn't listed on the Wine appdb, and no one else seems to be able to run it).  But he should definitely check out Rosegarden--on Ubuntu Studio 8.04. That might make a linux convert out of him.

If you can be more specific as to exactly what is happening during installation someone may be able help. If the md5sum checks out then it could be a hardware detect issue, in which case all you may need to do is supply a boot option/kernel parameter

---

### Post by eekfonky on 2008-06-01
what is a "boot option/kernel parameter"? and I'll try to get one. It's a tough job to convert a person who relies on windows for their cubase. Without a guarantee, he'll not budge - he's a sceptic of ubuntu, more so now he can't even get it to install - my job is to fix that!

---

### Post by logos34 on 2008-06-01
here's one link:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On the hardy cd I think you press F1 for help, there are lists of options there too, one of which may apply to your machine. Or search/google you hardware for any clues to ubuntu compatibilty

---

### Post by Pumalite on 2008-06-01
Here are some boot parameters for your friend to try if that's the case:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791 vga=788
To be tried alone or in different combinations until you hit the right one.

---

### Post by logos34 on 2008-06-01
> **Pumalite said:**
> Here are some boot parameters for your friend to try if that's the case:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791 vga=788
To be tried alone or in different combinations until you hit the right one.

Don't hold back now, Pumalite! ;)

---

### Post by eekfonky on 2008-06-02
Sounds a bit daunting, but I'll see if he's up for it!

Cheers

---

### Post by eekfonky on 2008-06-06
At my friends house now, ubuntu works fine off of the live cd but when I install it on restart it says "Cannot mount partition, error 17"

Please help

---

### Post by Pumalite on 2008-06-06
Read this carefully:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

