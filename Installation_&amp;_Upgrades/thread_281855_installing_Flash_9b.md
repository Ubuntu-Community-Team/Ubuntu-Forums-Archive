---
title: "installing Flash 9b"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by ZERO_SHIFT on 2006-10-21
I downloaded the falsh 9 beta plugin, but as I dragged it into the firefox plugin folder I got an error about not having the permission of writing it.

I then did go to the file properties and cahnged the permissions, but Is still get the same message.

Please advice.

Thanks in advance.

---

### Post by Dylan103 on 2006-10-21
You need root, so, in terminal type
sudo nautilus
then goto the plugin folder, drag and drop.

---

### Post by madmetal on 2006-10-21
open terminal type 
sudo chmod 777 libflashplayer.so (change file permisions just in case)
and then 
sudo mv libflashplayer.so /usr/lib/<browser_directory>/plugins

---

