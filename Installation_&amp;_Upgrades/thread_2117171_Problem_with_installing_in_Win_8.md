---
title: "Problem with installing in Win 8"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by Helldogify on 2013-02-17
After trying and not being able to install using a cd or through wubi i decided to use a usb and i got to the screen which asked if i wanted to install. But instead it was a lot like a bios theme with a box containing 4 options. I chose install ubuntu and then there was a black screen thats it. I tried it again but with try ubuntu instead but the same black screen came. Help.

---

### Post by oldfred on 2013-02-18
Is this a computer that came with Windows 8 or one you installed yourself?

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

