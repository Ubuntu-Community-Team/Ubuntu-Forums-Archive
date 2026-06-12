---
title: "what and how to change MBR to point to the boot loader in Ubuntu"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by vasukoh on 2011-09-13
Hi, i have installed ubuntu 11.04 along side WINDOWS Vista on 2 of the partition out of 4 which was partitioned at the time on Vista installation, while Installation i mounted one of them as "/" and other as "SWAP", now when i restarted my PC it is still taking WINDOWS Vista by default. Now 2 query arise:

1- i am not able to see those 2 partitions which were mounted while UBUNTU installation in WINDOWS Vista.
2- What changes need to be made in the MBR to point to the boot loader in Ubuntu so that i can access both the OS as per the choice and how to make those changes.

It is really urgent, Please respond at the earliest...:(:(

---

### Post by Quackers on 2011-09-13
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

