---
title: "ubuntu installtion failed"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by abhinay.pandey on 2011-04-24
i have installed ubuntu 10.10 on ACER ASPIRE with 2GB RAM and 500GB hard disk with windows7 installed on its primary partition.
after installing i got following problems :
1.unable to start ubuntu in normal mode
2.ubuntu starts only in recovery mode with no graphics
3.i am also unable to boot into windows 7
4.also in recovery mode it doesn't shows my partitions. only system reserved partition and a partition of 448GB are visible.
5. i am unable to fetch my folders which were there in windows

now please tell me what to do...

---

### Post by Quackers on 2011-04-24
Welcome to UF
If you installed 10.10 using the "install alongside" option, Windows may have been over-written.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

