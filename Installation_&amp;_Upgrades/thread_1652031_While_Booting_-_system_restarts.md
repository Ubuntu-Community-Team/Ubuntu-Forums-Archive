---
title: "While Booting - system restarts"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by r_samur on 2010-12-24
Hello I am using windows 7 in my laptop and I installed ubuntu on it. I was using ubuntu to discover it. however When I try to boot from Ubuntu, It re-starts the laptop. 
I can only see  "Booting from NTFS: " then immediately in a second it restarts. 

what would be the problem for it? should I re install ubuntu?

thanks a lot.

---

### Post by Quackers on 2010-12-24
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

