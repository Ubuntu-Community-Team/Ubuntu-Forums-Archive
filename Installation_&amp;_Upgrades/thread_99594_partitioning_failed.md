---
title: "partitioning failed"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by figo2476 on 2005-12-05
hi:
Xp is installed in my computer currently. I try to install ubuntu in other driver. When I was up to partitioning, no matter how I tried, it kept failing.

I did:
*ext3 file system (I tried ext2; etc)
*boof flag on
*mount point / (I tried /home; /usr/local; etc)
*2.6 G

Is it the correct to do so? Is it my computer is too old(pentium 3, 512 ram, old motherboard....)

Any help is appreciated
Gary

---

### Post by Herman on 2005-12-05
figo2476, if you haven't done so already, look around on the website which my signature link below this post leads to, and compare the way you are doing it with the examples there and see if that helps you. (Herman).

---

### Post by figo2476 on 2005-12-05
I have 4 different drivers. when i was up to example [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm) 's 9th fat32 illustration
My installation only allows me to select the largrest amount driver. Actually, I choose arbitrarily

Gary

---

### Post by Herman on 2005-12-05
I am not sure I understand. Can you explain to me what  you mean when you use the word 'driver'?, and what do you mean by 'abitrarily'?

---

### Post by figo2476 on 2005-12-06
oh......
I partition my hard driver into 4 different small drivers(C: D: E: F:). The xp is installed in the C:, while I want to install ubuntu in F:. If I use the method I mentioned above, it won't allow me to install into the smallest driver (i.e. E:). The default installation is to the largest driver (i.e. F)

'arbitrarily' means I want to install ubuntu in E:

But anyway, I tried the method in your webpages. It still failed. Of couse, I had tried manually partition my drivers. Probably my pc is too old......

Can anyone give me ideas how to manage the partitioning.........

Regards
Gary 

[QUOTE=Herman]I am not sure I understand. Can you explain to me what  you mean when you use the word 'driver'?, and what do you mean by 'abitrarily'?[/QUOTE]

---

### Post by bwog on 2005-12-06
Try to install again, when you arrive at partitioning, you select the partitions one at a time. (Note that you only select the partitions where you want to install ubuntu). You have made these partitions before, and now you have to mount them.

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.

home partition; use as ext3, mount point /home, format, etc.

This mounts and formats the partitions and the installation will start.

**Or, in case you only want to you partition F for a swap and / (root) partition**: select partition F and use guided installation. I suppose F is formatted in ext3. With guided partitioning a / and a swap partion will be made.

---

### Post by figo2476 on 2005-12-07
* I tried the root partition. Then it failed.
* I think i did home partition. It failed again.

[QUOTE=bwog]**Or, in case you only want to you partition F for a swap and / (root) partition**: select partition F and use guided installation. I suppose F is formatted in ext3. With guided partitioning a / and a swap partion will be made.[/QUOTE]

* I did this as well. It failed.

* The reason may be unbuntu is not very compact with my old machine.

---

### Post by bwog on 2005-12-07
Edit: after reading your post again I have some questions. How did you make the partitions? How large are the partitions on your disk and how are they formatted? 

i ask this because it may be wise to use xubuntu: [https://wiki.ubuntu.com/InstallingXu...=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXu...=%28xubuntu%29)
basicly this is: install server and then install xubuntu-desktop.

However, when the installation failed at partitioning, you have to do that first. Ubuntu needs a / (root) partition **and** /swap.

What exactly failed? Was there a message on screen?

---

