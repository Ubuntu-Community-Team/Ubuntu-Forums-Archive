---
title: "error"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by bob29th on 2011-08-16
I installed ubuntu 11.04 on a usb hard drive which I created a 100 gig partition however when i try to boot from the usb drive I get the message error:no such partition grub rescue> when I boot from live dvd I can see the partition I created with all the files on it how do I solve this

---

### Post by Quackers on 2011-08-16
Welcome to UF :-)
With all hard drives plugged in please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

