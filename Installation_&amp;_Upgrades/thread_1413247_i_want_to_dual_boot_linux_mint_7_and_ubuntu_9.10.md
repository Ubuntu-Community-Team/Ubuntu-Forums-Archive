---
title: "i want to dual boot linux mint 7 and ubuntu 9.10"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by cpaige123 on 2010-02-22
i have been trying for day to dual boot Linux mint 7 and ubuntu 9.10. when i get remotely close Linux mint boot-loader says partition not found. even in ubuntus boot loader would do the same thing. but, there both grub. i don't know can any body help me?

---

### Post by harrisonk on 2010-02-22
[SIZE=2]Try mint 8 I think it has the grub2 boot loader which is the same as the one on 9.10.
[/SIZE]

---

### Post by oldfred on 2010-02-22
This script shows the files and setting for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by kansasnoob on 2010-02-22
> **oldfred said:**
> This script shows the files and setting for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

+1! That takes the "guess work" out of things :)

Edit: do you have a preference regarding which OS handles the boot? It can be done with either and while I prefer Ubuntu's grub2 I realize you might prefer Mint's grub because of the Minty menu.

Edit #2: also tell us what you can currently boot.

---

### Post by cpaige123 on 2010-02-22
i am booting windows 7 as my main operating system but i would like to have all 3 on there mint windows and ubuntu. i am installing mint and ubuntu on an external harddrive.

---

### Post by cpaige123 on 2010-02-22
i am able to boot windows 7 and ubuntu but when i pick mint 7 it says "no such partition'

---

### Post by wojox on 2010-02-22
You installed Mint last it seems? Did you let it overwrite the MBR or did you keep the original?

---

### Post by cpaige123 on 2010-02-22
i instlled mint last yes but i would like to dual boot them???????????????????????????

---

### Post by cpaige123 on 2010-02-22
and yes i lt it overright but i might remove it????????????????????

---

### Post by ubunterooster on 2010-02-22
have you tried:

sudo-apt update grub

---

### Post by cpaige123 on 2010-02-22
no ill try it

---

### Post by cpaige123 on 2010-02-22
it did not work thanks though

---

