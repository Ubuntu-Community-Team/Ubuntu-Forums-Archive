---
title: "grub with flashing cursor"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by ac8038 on 2007-03-17
Hi i'm new to linux I have two hard drives one of which has windows and the other has linux. using some of the guides i have set up the grub boot loader which boots fine into windows but if i select ubuntu i get a black screen with grub at the top and a flashing cursor. I would be grateful for any help.

---

### Post by Herman on 2007-03-18
Hello ac8038,
If you think it looks like the illustration in this link, [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), then you can try to follow the link's instructions and boot Ubuntu from the command line. 
Be sure to take good notes while you are doing it. Most likely you have a small error you will need to correct in  your menu.lst file in Ubuntu. The same commands you need to boot Ubuntu from the command line will also be needed again to edit your menu.lst file to make Ubuntu will boot up automatically from now on.

 If you don't want to do that, or if you have trouble, you should be able to use your Ubuntu Desktop live CD for getting some information so someone ca help you. 
Here is how to                               [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") That link also tells you at the end, how to access your menu.lst file that you will probably need to edit.

You can also open a 'terminal' ('Applications'-->'Accessories'-->'Terminal' and enter the following command, sudo fdisk -lu ```
sudo fdisk -lu
``` If you can post the output from that command here along with a copy of the bottom part of your menu.lst file from /boot/grub someone will be bale to help you.

Regards, Herman :)

---

