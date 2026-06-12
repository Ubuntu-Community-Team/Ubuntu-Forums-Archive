---
title: "grub"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by arunkmohan18 on 2009-12-13
when i installing ubuntu from dvd it shows grub install (hd0,0) failed fatal error 
after finishing in terminal i typed in terminal 
grub>root(hd0,0) 
device not found
root(sd0,0)
error while parsing number
i don't know now what to do please help me about this problem

---

### Post by 73ckn797 on 2009-12-13
What version of Ubuntu?

---

### Post by arunkmohan18 on 2009-12-14
it,s ubuntu 9.1

---

### Post by presence1960 on 2009-12-14
I need way more info than that to try to diagnose the problem. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

