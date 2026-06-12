---
title: "Problem with booting up in Ubuntu after installing updates. No  vmlinuz 2.6"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by xairoy on 2010-01-09
I have shortly installed Ubuntu 9.10 in my Laptop ( I have Windows Vista). It was working properly untill I installed updates in Ubuntu. After the updates I needed to restart the Computer. When i restarted and after I chose Ubuntu from the windows boot Menu. But the Login Window from Ubuntu didn't come. I got Grub2 prompt.
sh:grub>
 
Then I went thorugh the Grub2 Document and tried to the the following steps at the grub prompt:´
 
1. sh:grub>ls
then comes the follwing files
(loop0)  (hd0) (hd1,0)...........
 
2.  sh:grub>linux boot/vml 
after vml I enter TAB. I dot not get vmlinuz-2.6.31-14-generic or any other version. I only got vmlinuz.old
 
I continued with old i.e 
 
sh:grub> linux boot/vmlinuz.old  root=/dev/s
then again i put TAB. I didn't get the **sda1** folder. **There was no folder started with sda. **

what should I do now?
please help. I am trying since yesterday.

---

