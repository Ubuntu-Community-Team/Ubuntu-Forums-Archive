---
title: "Google Chrome with Smartcard DOD CAC Card???"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by perro68 on 2010-12-01
I Have been using firefox to access AKO and DTS and it works fine

my question how do i get google Chrome to access AKO and DTS using my  CAC card

when i boot my machine in windows i can use chrome and  but on ubuntu i  have no idea how to set up Chrome to add a security device like in  firefox


How do i configure Chrome to access my cac card while i am on my ubuntu machine



Can anyone help with this?

---

### Post by perro68 on 2010-12-01
no help out there at all for this?

---

### Post by default013 on 2010-12-01
I think it depends on the CAC reader you have. Most of the drivers are proprietary and sometimes they charge to download them. Look at your reader and find out what type it is and see what kind of drivers you need, if there's a plugin for Chrome it'll come from the manufacturer - but I'd doubt that most readers have a plugin for Chrome. Some only work with IE and maybe support Firefox or Safari. I wouldn't support Chrome if I was them; Chrome isn't the best on security.

Maybe this site can help you out:
[https://militarycac.com](https://militarycac.com)

This guy says he can't even get FireFox to work on his though.

---

### Post by perro68 on 2010-12-02
> **default013 said:**
> I think it depends on the CAC reader you have. Most of the drivers are proprietary and sometimes they charge to download them. Look at your reader and find out what type it is and see what kind of drivers you need, if there's a plugin for Chrome it'll come from the manufacturer - but I'd doubt that most readers have a plugin for Chrome. Some only work with IE and maybe support Firefox or Safari. I wouldn't support Chrome if I was them; Chrome isn't the best on security.

Maybe this site can help you out:
[https://militarycac.com](https://militarycac.com)

This guy says he can't even get FireFox to work on his though.

firefox is easy ..it a thread on this forum about it

---

### Post by martinpaljak on 2010-12-29
> **perro68 said:**
> I Have been using firefox to access AKO and DTS and it works fine

my question how do i get google Chrome to access AKO and DTS using my  CAC card

when i boot my machine in windows i can use chrome and  but on ubuntu i  have no idea how to set up Chrome to add a security device like in  firefox


How do i configure Chrome to access my cac card while i am on my ubuntu machine



Can anyone help with this?

Chrome/Chromium does not support smart cards (yet). You need to use Firefox. Even if you can configure Chromium to show your CAC certificates when connecting to some HTTPS site, the functionality to enter the PIN code is not yet implemented.

---

