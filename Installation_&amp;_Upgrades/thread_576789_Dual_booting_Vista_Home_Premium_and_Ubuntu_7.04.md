---
title: "Dual booting Vista Home Premium and Ubuntu 7.04"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by f1racer on 2007-10-15
I am wondering how do I do this? I have them both installed on my hard disk already, but all I want to do is make Vista be the default for booting. Currently Ubuntu 7.04 is the default for booting but is there a way I can make Vista for default? I use Vista more for the time being and usually switch on the PC and walk away while it boots up. 

Thanks!

---

### Post by Martin Witte on 2007-10-15
in file /boot/grub/menu.lst you have an entry 'default 0' (0 is usually the value set). in a standard installation you have to change this to 3, as this is where vista lands wheen you have two os's on a disk, if you have more os' s count the entries in mentioned file, start counting with zero

---

### Post by maybeway36 on 2007-10-15
And don't forget to change the default again after a kernel upgrade, to make sure it's still right.

---

### Post by f1racer on 2007-10-15
Thanks guys! 

> in file /boot/grub/menu.lst

How do I get into this?

---

### Post by rsambuca on 2007-10-15
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by f1racer on 2007-10-15
Thanks! Got it sorted now.

---

### Post by rsambuca on 2007-10-15
You might consider moving your Vista entries to just above the line that says> ### BEGIN AUTOMAGIC KERNELS LISTThen set your default to '0', and you never have to change it when the kernel is updated.  Otherwise, if a new kernel is added, your default number will be wrong and you will have to manual change it every kernel change.

---

### Post by celticbhoy on 2007-10-15
rather than change after a kernel update just check the new kernel work sand delete the two old entries

---

### Post by rsambuca on 2007-10-15
With my method you never have to manually edit it except for the first time.

---

### Post by celticbhoy on 2007-10-16
but does it not make for a long grub list ?  .

---

### Post by rsambuca on 2007-10-16
No.  Once you are sure the new kernels work properly, you can just uninstall the oldest ones.  Also, you can set grub to only show the latest kernel.

---

### Post by celticbhoy on 2007-10-16
Bow to the greater wisdom. I would be interested to find out the steps involved in your method, especially the grub setup

---

### Post by rsambuca on 2007-10-16
> **celticbhoy said:**
> Bow to the greater wisdom. I would be interested to find out the steps involved in your method, especially the grub setup

Greater wisdom?  I think you give me far, far too much credit :)  Anyways, let me know what it is you want to do, and then post your /boot/grub/menu.lst.

---

### Post by celticbhoy on 2007-10-16
Really both bits of your last post how to set grub to only show newest kernel and how to delete old kernels - cant show menu.lst as on vista at moment.

---

### Post by rsambuca on 2007-10-16
If you want Vista to be the default and not have to worry about it with every kernel change, put the Vista info just above the line in your grub that says> ### BEGIN AUTOMAGIC KERNELS LIST
Then make sure the line that says "default #" is set to default  0.

To only show the latest kernel, change the line that says> howmany=allto howmany=1

To delete your old kernels after you are positive the new one works, just search using Synaptic for 'linux-image', and remove the old kernels you don't want.

And just as an aside, as you said you couldn't get your menu.lst from vista, you can install the [fs-driver for Windows]("http://www.fs-driver.org/") to get full read/write capability to your ubuntu partitions.  Just make sure you use the XP compatibility mode when installing it.

---

### Post by celticbhoy on 2007-10-16
back on Ubuntu will set it up now - thanx

---

