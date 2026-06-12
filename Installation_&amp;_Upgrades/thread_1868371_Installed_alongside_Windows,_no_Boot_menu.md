---
title: "Installed alongside Windows, no Boot menu"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by t_wright on 2011-10-24
Hi,
 
After trying Ubuntu 11.10 out on Wubi, I decided to set up a dedicated partition and install it stand alone. I downloaded and created a bootable USB stick, created an 80Gb partition on my drive using the Windows Disk Management tool, and started the installation. After the successful install using the 'Install Alongside Windows' option, it came to the reboot. However upon rebooting it just booted straight into Windows, with no Boot Menu screen or anything. Checking the disk utility in Windows shows it has installed, there is a 70Gb formatted partition and two 4Gb partitions that it created (after trying the install twice).
 
How do I get it to work?!
 
Cheers,
Tom

---

### Post by Quackers on 2011-10-24
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by mrw on 2011-10-24
I had the same problem. Just download and run "Boot-Repair"
It's bootable and will setup a grub automatically.

---

