---
title: "I installed Ubuntu after windows 7, but it wont show up when I restart.  What do I do"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Mashuteichou on 2011-03-21
I have an ASUS 1005HA. 

Recently installed a new hard drive and made 3 partitions.  One for Windows 7, one for Ubuntu, one for storage.  I installed windows 7 first.  Then, I installed Ubuntu 10.10 Netbook remix. It loads all the way to the end, tells me to take the CD out when its done, but when I restart, its like nothing happened.  Windows 7 boots straight up to itself.

I tried redoing the GRUB loader while using the CD, but that didnt work either.  So, how do I make it so I can see both OS?  Because windows is running superior right now on my netbook, and I don't like that.  But I need it for work.  >_>   

Thanks for any help.

---

### Post by Quackers on 2011-03-21
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

