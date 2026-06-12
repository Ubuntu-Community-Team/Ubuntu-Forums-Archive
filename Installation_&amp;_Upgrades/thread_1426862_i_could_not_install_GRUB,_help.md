---
title: "i could not install GRUB, help"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by colifato13 on 2010-03-10
Is there other way to boot into ubuntu? some kind of command?

---

### Post by presence1960 on 2010-03-10
we need a little more info from you. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by nitstorm on 2010-03-10
I am under the assumption that you are using GRUB2, this link might be useful. Cheers :D

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by presence1960 on 2010-03-10
> **nitstorm said:**
> I am under the assumption that you are using GRUB2, this link might be useful. Cheers :D

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

How do you assume that- the OP gave no info whatsoever about his setup, boot process or installed version? Let's see what the results from the boot info script say before giving any suggestions...that is unless you have a crystal ball!

---

