---
title: "No GRUB, can't access Ubuntu on Dual Boot w/ Windows 10"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by BalsamAmaranth on 2018-10-08
I went through Software Updater and it went through and updated various drivers and software. I believe one of them was GRUB. It had a selection to choose whether or not I wanted to overwrite it. I chose no, since I didn't want to lose it. Well, I lost GRUB and I can't select Ubuntu to boot.

Laptop: MSI GP62MVRX Leopard Pro-1264

(256GB SSD, 1TB HDD)

Dual-booted with Ubuntu 18.10 and Windows 10.

I tried running through boot-repair via USB, but it gets stuck at "Unhide boot menu" for over 30 minutes, and will never pass it. I also tried to run boot-repair through Terminal on a Live CD, but my damn keyboard/mouse won't function as I click the "Try Ubuntu" button on the splash screen.

Here are my logs:

[http://paste.ubuntu.com/p/qKTBSM72HH/](http://paste.ubuntu.com/p/qKTBSM72HH/)

Any assistance would be greatly appreciated.

---

### Post by CLCressman on 2018-10-08
Have you tried Rescatux?

---

### Post by BalsamAmaranth on 2018-10-08
> **CLCressman said:**
> Have you tried Rescatux?

I hadn't previously, but I looked it up, loaded it onto a flash drive and booted from it. I forgot what the option was, something along the lines of "easy GRUB fix", then did upgrade GRUB. Rebooted, and now I can select Ubuntu as a boot option in UEFI, but no GRUB. Booted into Ubuntu, ran ```
sudo update-grub
``` and rebooted. I now have GRUB! Thank you so much for the help!

---

### Post by CLCressman on 2018-10-08
Don't forget to mark this thread "Solved".

---

