---
title: "Wont boot"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by tybasher on 2011-05-16
Okay so i just installed Ubuntu 11.04 32bit Desktop Edition, and dual booted it with my windows 7. After it was installed i restarted like the installation said, and right away it boots into windows 7, grub2 doesn't boot up or anything. 

So i booted from the live cd, and it says grub2 is installed, so i have no idea why its automatically booting windows 7 and not giving me a option to chose ubuntu. Any ideas?

---

### Post by Quackers on 2011-05-17
Where did you install grub to?
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tybasher on 2011-05-17
To be honest I'm not sure where i installed it, but after running that command here is the output

```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

```

I really appreciate all this help btw :)

---

### Post by PowerBarry43 on 2011-05-17
Hi

firstly i would recommend using supergrub ([http://www.bootproblems.com/](http://www.bootproblems.com/)) as a boot disk instead of using your live cd because it'll work with most distros and it will let you boot into your ubuntu installation on the hard drive. once you're in open up a terminal and run "sudo grub-install /dev/sda" then "sudo update-grub"

hope that helped :)

---

### Post by Rubi1200 on 2011-05-17
Hi,
you need to open the RESULTS.txt file and copy the contents. Then start a new post and paste all the copied content into it. After pasting, highlight all the text and click on the # icon on the toolbar to wrap the text with code tags.

---

