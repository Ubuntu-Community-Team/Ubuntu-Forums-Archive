---
title: "installing Nvidia drivers Problems - Ubuntustudio"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by jmd87 on 2008-08-05
Hi,

I recently reinstalled Ubuntu (Ubuntu studio this time though! =- Latest version) as im getting sick of windows!

I have run into a problem when installing the Nvidia graphics driver...It pop sup saying I need to install/enable etc so I download it and install it reboot but I can't get back into ubuntu. It just shows a black screen after the bootloader.

The only way I can get back in is by repairing in and then booting it but it stops the Nvidia driver.

Can anyone help me please ?

Many thanks
Joe

---

### Post by jmd87 on 2008-08-06
Hi again,

I forgot to tell you that my graphics card is a 7 series Geforce! 

Also I have tried other ways that people have listed on other question but none of them work :( And my graphics card worked with the previous version of ubuntu so I'm not sure why its not working :(

Many thanks again!
Joe

---

### Post by Thelasko on 2008-08-29
Follow the guide in my signature.  Make sure you get your video card working in Hardy before you try to upgrade to UbuntuStudio.

---

### Post by El Flauta on 2008-10-05
> **Thelasko said:**
> Follow the guide in my signature.  Make sure you get your video card working in Hardy before you try to upgrade to UbuntuStudio.
It's a different problem. I have the same issue with ubuntustudio 8.04, like a lot of people.

To install -from apt or dvd- are easy... video card may be working perfectly in "normal" Ubuntu; but when you boot with -RT kernel, the whole system go directly to the freeze hell. It's a problem between NVidia driver and -RT kernel, who existist only since Hardy.

I need to work with realtime kernel for my audio apps. "Normal" kernel don't matters to me... sadly, that bug is a continuos headache, who makes very hard to still working with Ubuntu.

For me, the only solution who works has been to reinstall UbuntuStudio 7.10, and don't do any actualization. :(

---

