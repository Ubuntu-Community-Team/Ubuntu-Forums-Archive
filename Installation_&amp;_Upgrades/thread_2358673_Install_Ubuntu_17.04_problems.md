---
title: "Install Ubuntu 17.04 problems"
date: 2017-04-16
forum: Installation &amp; Upgrades
---

### Post by azaravicius on 2017-04-16
Hi,
I can't clean install Ubuntu 17.04. Here are video about it [https://youtu.be/-Ts8kkAMNqw](https://youtu.be/-Ts8kkAMNqw)
Computer spec [https://paste.ubuntu.com/24392306/](https://paste.ubuntu.com/24392306/)
It is not first time, but before it happened prior to login screen and after login screen appeared it fixed automatically. But now I can't install ubuntu because of it.

---

### Post by ajgreeny on 2017-04-16
This looks like a video problem with your nvidia graphics.
Try again but when you get to the black and white menu where you choose to "Try Ubuntu without installing" or "Install Ubuntu" hit E key to edit the boot stanza.
Use cursor keys to move to the line that has "quiet splash" in it and replace those two words with "nomodeset" then use Ctrl+X to boot.  You may get a low resolution GUI screen from which you can install,

Once installed you may need to go through the same procedure from the grub menu at boot, to once again get a low resolution GUI, and then from there use Additional Drivers to install the recommended nvidia driver for that card.

---

### Post by azaravicius on 2017-04-16
Thanks,
it helped. Now I have Ubuntu 17.04 installed.

---

