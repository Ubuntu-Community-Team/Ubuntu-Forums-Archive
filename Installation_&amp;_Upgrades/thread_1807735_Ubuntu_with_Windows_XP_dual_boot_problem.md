---
title: "Ubuntu with Windows XP dual boot problem"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by techlib on 2011-07-19
Hi all,

I have recently installed Ubuntu along with existing Windows XP.

After installation I was not getting dual boot option for Windows XP (in the start up menu)

After referring to this forum I issued the command: *sudo update-grub*

And now after reboot I am getting a blank screen! please help

---

### Post by Quackers on 2011-07-19
Welcome to UF :-)
Is this on every reboot or just when you choose XP from the grub menu?

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

