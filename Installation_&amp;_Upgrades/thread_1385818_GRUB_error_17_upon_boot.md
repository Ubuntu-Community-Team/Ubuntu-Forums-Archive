---
title: "GRUB error 17 upon boot"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by timothyQ on 2010-01-20
I recently formatted my partion of ubuntu from my HP G60 laptop. I am running vista. I had ubuntu and vista set up dual boot. so when i booted i had to select ubuntu or vistta, if i did not select vista it would boot ubuntu. this got annoying and i wanted to get rid of this. so i formatted the partion. i then restarted my computer and it gave me the GRUB error 17. Also i cannot access f11, is there anyway to fix this problem?

Thanks!

---

### Post by tachuela on 2010-01-20
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)
[http://www.youtube.com/watch?v=GjzFU6rXwLo](http://www.youtube.com/watch?v=GjzFU6rXwLo)

---

### Post by presence1960 on 2010-01-20
I need a little more info about your setup and boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. You did not have to get rid of Ubuntu to have Windows boot as default at the GRUB menu. But nevertheless it is too late for that now. What did you expect anyway? You are dual booting and have to select which OS to boot.

---

