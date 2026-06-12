---
title: "Boot Problem HELP"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by elliotlam09 on 2010-01-06
After I update Ubuntu 9.10, the booting of internal Hdd (windows 7) cannot be boot and it says that the boot manager of it is gone. I have to use ubuntu's bootup screen selection  to boot windows 7. How can i back to normal by restoring the boot manager reg????

---

### Post by presence1960 on 2010-01-06
are you using ubuntu from an external HDD? If yes then do the following with the external disk plugged in. If no just do the following:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by elliotlam09 on 2010-01-12
> **presence1960 said:**
> are you using ubuntu from an external HDD? If yes then do the following with the external disk plugged in. If no just do the following:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Yes, i use external to boot ubuntu, but when i just turn on the computer with no external connect it can't boot windows7 because it change my bootmgr and i must plug in external in order to use windows 7, Is there a way not to format the internal and restore the bootmgr in win7

---

### Post by darkod on 2010-01-12
Yes, there is. But not to give you wrong advice without knowing your setup, run the script like presence said, and with the external drive plugged in, and copy the results here.
We need to see the setup.

---

### Post by raymondh on 2010-01-12
.

---

### Post by presence1960 on 2010-01-12
> **darkod said:**
> Yes, there is. But not to give you wrong advice without knowing your setup, run the script like presence said, and with the external drive plugged in, and copy the results here.
We need to see the setup.

+1

Thanks Darko!:popcorn:

---

