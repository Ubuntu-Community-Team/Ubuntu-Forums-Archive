---
title: "error: no such partition"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by acsweitzer on 2011-07-29
I have a Toshiba Satellite laptop that used to have Windows 7 installed. It was having problems, so I wanted to try installing Ubuntu 11.04 to see if that would work.
 I had no problems with the installation until it got to the point where you restart and take out the CD. It gave me an error message saying, "error: no such partition" and below that, "grub rescue>".
 Does anyone have any ideas on what I can do? (:

---

### Post by Quackers on 2011-07-29
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

