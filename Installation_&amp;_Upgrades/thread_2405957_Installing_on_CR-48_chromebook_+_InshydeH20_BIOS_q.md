---
title: "Installing on CR-48 chromebook + InshydeH20 BIOS question"
date: 2018-11-13
forum: Installation &amp; Upgrades
---

### Post by igotsanevo4g on 2018-11-13
Trying to revive my CR-48 chromebook, and wondering if anyone has experience with installing linux on a chromebook.

Ive found a few outdated guides, the most promising one being this [http://sabiancrash.blogspot.com/2011/10/installing-lubuntu-natively-on-cr48.html](http://sabiancrash.blogspot.com/2011/10/installing-lubuntu-natively-on-cr48.html) but the download link is dead for the InshydeH20 BIOS that's needed to be able to install lubuntu from USB.

Does anyone know of a workaround, or can help me install/find the InshydeH20 BIOS? My goal is simply to install lubuntu.

---

### Post by igotsanevo4g on 2018-11-15
I've figured a solution, so i'll post it here in case anyone is digging for this info in the future. [THIS IS ONLY FOR CR-48 CHROMEBOOK, newer chromebooks have much easier options for OS swapping]

First- You'll need to flip the developer switch under the battery, and pop the back of the cr-48 off to remove a metal tab connected to the back panel that prevents writing a new bios by making contact with some prongs (Y U lock this down google, seeesh). Once removed you'll be free to flash a new bios, we need that.

Second- Follow this [https://sudoroom.org/wiki/Installing_Ubuntu_on_a_Chromebook_CR-48](https://sudoroom.org/wiki/Installing_Ubuntu_on_a_Chromebook_CR-48), and instead of using the wikispaces link in the code, use this instead [https://bayton.org/download/cr48.bin.tar.gz](https://bayton.org/download/cr48.bin.tar.gz)  <- This is the only working link ive found for a working BIOS, thankfully. (I couldnt get the backup/install to work from USB, so i simply ran downloaded/install the bios to the system using the shell in chrome from login screen, just connect network before hitting ctrl+alt+->. This method produces no backup, but also requires no USB stick)

Third- After installing the custom bios, reboot and mash F10 (brightness up). You'll get a typical bios, allowing you to install any OS of your choosing from USB.

This solution is infinitely better than running linux ontop of the chromeOS kernel, or running linux from USB. Unless you need to dual boot ChromeOS for some unknown reason.

Cheers.

---

### Post by eg-bnb on 2019-11-12
> **igotsanevo4g said:**
>  I simply ran downloaded/install the bios to the system using the shell in chrome from login screen, just connect network before hitting ctrl+alt+->. 

Any chance, a year later, you can provide more detail on how to install the alternative bios?

---

