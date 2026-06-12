---
title: "daul boot XP and ubuntu"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by nancy25dec on 2005-04-29
Hi,

I want to install Ubuntu with Win XP. XP is already there in my primary partion. And I want to install Ubuntu in my logical partion D:. 

Can someone please suggest me how should I go about it. I tried to do but after selecting my country and keyboard type.. (basic things) it gives me the option to erase IDE1 or to manually create partion. But I hv partion my computer already and want to install Ubantu on to second partion. When I select that partion it continues to give me File System error. I've tried to take all options available but it doesn't help and I'm too scared to loose my data in computer, that is why I want to make it daul boot. But it is not working. Can someone please suggest me on how to daul boot.

Any help will be greatly appreciate.

---

### Post by hashimoto on 2005-04-29
AFAIK, you can't install on a formatted NTFS partition (assuming this is what you have/tried) but you need to format it. If the standard installation doesn't do it, start the installation with option "expert". There you have the chace to manually select partitions and format them. Just a thought...

---

### Post by derrick1985 on 2005-04-29
You will have to first, resize your existing NTFS partition (the one you have XP on) and make some room for Ubuntu first.
Typically, take what space you want to reserve for Ubuntu, make a swap out of the unallocated space (i would say, 512 mb would be good) and then use the rest of the space to install ubuntu on.

If the Ubuntu (Debian) installer won't let you resize the NTFS partition (or, you want a GUI way of doing it) I recommend trying out a program called System Rescue CD. [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by momo66 on 2005-04-29
[QUOTE=nancy25dec]Hi,

I want to install Ubuntu with Win XP. XP is already there in my primary partion. And I want to install Ubuntu in my logical partion D:. 

Can someone please suggest me how should I go about it. I tried to do but after selecting my country and keyboard type.. (basic things) it gives me the option to erase IDE1 or to manually create partion. But I hv partion my computer already and want to install Ubantu on to second partion. When I select that partion it continues to give me File System error. I've tried to take all options available but it doesn't help and I'm too scared to loose my data in computer, that is why I want to make it daul boot. But it is not working. Can someone please suggest me on how to daul boot.

Any help will be greatly appreciate.[/QUOTE]
 I just did this yesterday and it worked fine.  I used Partition Magic to partition my drive and then started the install.  When it got to the partition section you need to edit the logical drive you partitioned.  There is a list of options to choose from.  

I chose ext3 file system, 
made it bootable,
made it mount at /, 
and format the partition.

You then will be ready to move onto the next step of the install.

Hope that helps.

momo.

---

