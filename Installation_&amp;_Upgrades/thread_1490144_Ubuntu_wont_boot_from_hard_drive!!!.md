---
title: "Ubuntu wont boot from hard drive!!!"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by topias.l on 2010-05-21
I have an Acer Aspire One ZG5 netbook. I have Windows XP home installed. I downloaded Ubuntu 10.04 netbook edition and put it on USB drive by Unetbootin. I booted from usb and it worked perfectly. I then installed Ubuntu to my hard drive from the live desktop and nothing went wrong. Perfect so far. Next, i shut down my netbook and took the usb drive out. I booted my netbook and it started loading Windows XP, didn't ask me if i want to use Ubuntu. I shut down the computer and pressed F5 while booting. It asked me what i want to do. I selected 'go back to OS selection' and i could only choose Windows XP from there. It was the only thing i could choose. Whats wrong? I really want to use Ubuntu!

Any help would be greatly appreciated. Thanks.

---

### Post by emanuel.b on 2010-05-21
> **topias.l said:**
> I have an Acer Aspire One ZG5 netbook. I have Windows XP home installed. I downloaded Ubuntu 10.04 netbook edition and put it on USB drive by Unetbootin. I booted from usb and it worked perfectly. I then installed Ubuntu to my hard drive from the live desktop and nothing went wrong. Perfect so far. Next, i shut down my netbook and took the usb drive out. I booted my netbook and it started loading Windows XP, didn't ask me if i want to use Ubuntu. I shut down the computer and pressed F5 while booting. It asked me what i want to do. I selected 'go back to OS selection' and i could only choose Windows XP from there. It was the only thing i could choose. Whats wrong? I really want to use Ubuntu!

Any help would be greatly appreciated. Thanks.
You may not have chosen to install the GRUB bootloader when you installed Ubuntu. Though I'm not sure if it was on purpose.

Anyway, check if Ubuntu is taking up space on your hard drive

---

### Post by topias.l on 2010-05-22
I checked my hard drive space in xp and it only showed 70gb. The drive is actually 140gb. it looks like it did install ubuntu. I will try to reinstall it now.

---

### Post by wilee-nilee on 2010-05-22
Post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The easiest way to post with the tags is to paste the script read out into the reply, highlight the text, and click on the # in the reply panel. This readout will tell us whats going on with the boot and pretty much everything that is needed.

I suspect grub was installed, but to the thumb, you have to click that advanced button in the last install gui to make sure grub goes to the correct place.

---

### Post by topias.l on 2010-05-22
Yes, i installed ubuntu again and i pressed the advanced button at the end and it worked.:smile:Thanks all you guys.:smile:

---

### Post by wilee-nilee on 2010-05-22
> **topias.l said:**
> Yes, i installed ubuntu again and i pressed the advanced button at the end and it worked.:smile:Thanks all you guys.:smile:

Cool, that is something you will never forget now.

---

