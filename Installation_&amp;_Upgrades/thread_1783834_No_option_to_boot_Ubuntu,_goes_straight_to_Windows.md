---
title: "No option to boot Ubuntu, goes straight to Windows 7"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by drtanz on 2011-06-16
Hi, I installed Windows 7 along with Ubuntu 11, my hard disk setup is similar to this page [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

(The 3rd one from the end).

While installing I chose to install the loader in the / partition. However when everything installed and I rebooted I could not choose to load Ubuntu, instead the system went straight to Windows 7 as usual. I am guessing I did something wrong when choosing the location for GRUB, any way I can fix this? Thanks

---

### Post by Quackers on 2011-06-16
The Loader (grub) is normally installed to the hard drive, not to a partition. Unless grub is in the mbr of the hard drive it doesn't get a chance to work.
You could re-install using the same partition(s) and this time install grub to the hard drive (/dev/sda or /dev/sdb for example (usually whichever boots first).
Or alternatively use the live cd to install grub to the mbr of the hard drive. But for this you would need to know which is your Ubuntu root partition.

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

### Post by drtanz on 2011-06-17
Thanks I solved this using EasyBCD for Windows to set the GRUB alongside windows' loader.

---

