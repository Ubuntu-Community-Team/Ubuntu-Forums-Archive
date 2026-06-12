---
title: "Easy way to edit Grub boot order?"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by congdonb on 2010-04-24
Is there an easier way (gui based utility tool like Mandriva has) to edit the Grub boot order?  I read through the help files on Grub and the process is rather complex and even not recommended to reorder items on the boot loader and I want to readjust this rather often.  Each time the kernel is updated a new entry is added and I sometimes want to have other kernels or operating systems loaded as the default until later when I remove those older unused kernels and the Grub auto scan process removes the extra entries.

-Bill

---

### Post by tommcd on 2010-04-24
> **congdonb said:**
> Is there an easier way (gui based utility tool like Mandriva has) to edit the Grub boot order?  I read through the help files on Grub and the process is rather complex and even not recommended to reorder items on the boot loader and I want to readjust this rather often.
To update grub after a new kernel is added (or a new distro is added to your system), simply open a terminal (applications > accessories > terminal) and run:
```
sudo update-grub
```
To edit the boot order, simply edit /etc/default/grub file. Add the entry **GRUB_DEFAULT=saved**. This will set the default OS to be the one that was selected on the last boot. You can also add **GRUB_DEFAULT=OS_name** 
to /etc/default grub to accomplish the same thing.
For these and other options for editing how grub2 works, see this excellent tutorial:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
And specifically, for editing the boot order:
[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)
> **congdonb said:**
> 
  Each time the kernel is updated a new entry is added and I sometimes want to have other kernels or operating systems loaded as the default until later when I remove those older unused kernels and the Grub auto scan process removes the extra entries.

Using "sudo update-grub" and editing /etc/default/grub to include "GRUB_DEFAULT=saved" should accomplish this.

And welcome to the Ubuntu forums!

---

### Post by e-Gee on 2010-04-24
You can install startup-manager from synaptic that is gui for that

---

### Post by congdonb on 2010-04-24
Thanks Guys! I used the following:

In the terminal
 	Code:
 	gksudo gedit /etc/default/grub 
and changed this line to get my desired results
 	Code:
 	GRUB_DEFAULT=4 
Then ran
 	Code:
 	sudo update-grub 
I will look into the startup-manager.

-Bill Congdon

---

### Post by congdonb on 2010-04-24
Thanks again!

Installed the startupmanager from Synaptic Package Manager which is exactly what I was looking for.

-Bill Congdon

---

