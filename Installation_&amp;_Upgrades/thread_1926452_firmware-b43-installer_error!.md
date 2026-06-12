---
title: "firmware-b43-installer error!"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by ethanzh on 2012-02-16
Ok so whenever i try to install anything (google chrome, skype) I get an error along the lines of "firmware-b43-installer error" What can I do to fix this?


Thanks!

---

### Post by insm0d on 2012-02-16
firmware-b43 is the proprietary firmware for use in some broadcom wireless cards.  Because of that I don't believe Ubuntu ships with those files, but there is a script that is run which downloads them.

If the computer you're working on is connected to the internet, try going to Hardware Drivers and install the Broadcom B43 wireless driver.

There's a way to manually download the needed files and install them if the above is not an option, but I'm sorry that I'm not familiar with that process.

---

