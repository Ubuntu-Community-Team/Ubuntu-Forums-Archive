---
title: "How to install Grub on mbr without ubuntu itself runin.."
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by 3abdo3asal on 2011-06-21
[SIZE=2]The title say's it all.... 
Ma Story : I had ubuntu 11.04 up and runing well but i had a netbook so i want to install ubuntu 10.10 netbook edition so i did i formatted it and then installed 10.10 but the installition didn't work  half way through it freezes ,so i turned it off and try again format then install same thing saw no im writing this through a live cd and this is my only computer i have win 7 on another partition and the ubuntu 11.04 iso with it .
So to install ubuntu 11 to my computer i need to log in to win 7 somehow....
Thankx...
SO how to install grub to mbr through live cd ???????
[/SIZE]

---

### Post by Quackers on 2011-06-21
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

