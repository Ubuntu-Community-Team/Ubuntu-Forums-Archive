---
title: "Edgy / Feisty wrong UUID when installing new kernel images"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by giuliastro on 2007-04-06
I have had a problem with Edgy and now with Feisty. Every time I decide to install new upgrades to my kernel, Ubuntu modifies my grub/menu.list and replaces all my dev/drives with UUIDs. The problem is that those UUIDs are wrong and the system doesn't boot until I replace them with /dev/drives or correct UUIDs. Anyone knows what the problem is?

Thanks in advance.

---

### Post by Herman on 2007-04-06
Hello giuliastro,
You probably just need to edit your kopt command's UUID details in your Debian AutoMagic Kernels List in your menu.lst file.
[kopt= (kernel options)]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")
Your Automagic kernels list controls what will be written to your new menu.lst when it gets refreshed when we have a kernel update.

To find out what UUID number you need, use this command, ```
ls /dev/disk/by-uuid/ -alh
```Just make sure you pick the correct number that corresponds with your Ubuntu / partition. :)

Here is one more link about it,       [Fiesty Fawn's new menu.lst with filesystem UUID added in the OS boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst")

Regards, Herman :)

---

### Post by giuliastro on 2007-04-07
Herman, thanks a lot. I knew of a few ways on how to get my UUIDs but couldn't imagine the (wrong) kopt option in my menu.lst controlled my kernel options on each update..
Thanks again! :)

> **Herman said:**
> Hello giuliastro,
You probably just need to edit your kopt command's UUID details in your Debian AutoMagic Kernels List in your menu.lst file.
[kopt= (kernel options)]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")
Your Automagic kernels list controls what will be written to your new menu.lst when it gets refreshed when we have a kernel update.

To find out what UUID number you need, use this command, ```
ls /dev/disk/by-uuid/ -alh
```Just make sure you pick the correct number that corresponds with your Ubuntu / partition. :)

Here is one more link about it,       [Fiesty Fawn's new menu.lst with filesystem UUID added in the OS boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst")

Regards, Herman :)

---

### Post by iamajd on 2007-04-10
Wow, thanks so much for that tip!  I never even paid any attention to any of the other options in my menu.lst...  
Fixed not only the UUID problem, but the grub root problem as well.
And I turned off the memtest and single user (recovery) options.
Thanks again!

---

