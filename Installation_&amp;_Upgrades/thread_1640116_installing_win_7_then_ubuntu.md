---
title: "installing win 7 then ubuntu"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by mrgoodmccann on 2010-12-07
ok so im not the sharpest tool in the shed but i can not figer this one out. i did a new fresh install of win 7 on 10gb partition it starts and runs. then i booted down and installed ubuntu 10.10 i went to manual complete to make a new partition i made one 4gb for swap and one 10gb for root "\" then installed with internet updates whan all finished it asked for a reboot and did not give option for ubuntu just started windows. so i did some looking and the partitions are still there how do i get the option for ubuntu? did i do something wrong? 
 
computer dell inspiron 1521
150gb drive 2gb ram

---

### Post by Quackers on 2010-12-07
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mrgoodmccann on 2010-12-07
i can not get this to work i have tried several ways with the * with out with 055 with out i even went in to the properties and changed them to an exe.file to run in a term. dont know what im doing wrong but this did not work. i even checked the path twice and put the file in two different places and followed all the steps again

---

### Post by Quackers on 2010-12-07
Did you download the script to your DESKTOP? Or somewhere else - like Downloads?
Go to wherever you downloaded it, copy/paste it onto the desktop then copy/paste the above command into the terminal.

---

