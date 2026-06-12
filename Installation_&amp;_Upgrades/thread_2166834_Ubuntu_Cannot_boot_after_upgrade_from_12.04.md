---
title: "Ubuntu Cannot boot after upgrade from 12.04"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by kyral210 on 2013-08-11
Ok, so I went through the standard Ubuntu update from the update settings, it installed, it asked me to reboot. No problem. After reboot I got my basic 'select OS' but there was not 12.10 option, just 12.04. 

[IMG]http://farm8.staticflickr.com/7314/9486917850_e3098f5da0_z.jpg[/IMG]

I clicked on that and got this screen. 

[IMG]http://farm4.staticflickr.com/3695/9484126215_5eb71c4b9c_z.jpg[/IMG]

How do I fix this?

---

### Post by grahammechanical on 2013-08-11
Writing in ignorance, I say that you are using a Windows 8 bootloader that knows about Ubuntu 12.04 but has not been updated to load Ubuntu 13.04.

The reference to 12.04 will look for Linux kernels that no longer exist because the kernels have been updated to those that are used in 13.04. So, the boot loading process is broken.

You need to update Grub4Dos and the Windows bootloader so that they know about Ubuntu 13.10. You should also give us information about your system. Especially, the disks and partitions. Are Windows and Ubuntu on the same disks? Or are they on their own disks? It makes a difference.

Regards.

---

### Post by kyral210 on 2013-08-11
same disk but different paritions...

as for the rest, im a real no hoper, so do I do that?

---

### Post by nachinew on 2013-08-11
> **kyral210 said:**
> same disk but different paritions...  as for the rest, im a real no hoper, so do I do that?  Hi,  I also got a same issue but with the help of Boot repair tool I recovered ubuntu OS Have a Ubuntu CD and put into the DVD Drive and boot from CD  After that Click Try Ubuntu, then Open the terminal and paste this line one by one.  

```
sudo add-apt-repository -y ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

Once the successful install of boot-repair it will launch, it gives two options one is recommended repair, click that one.  It takes some time to repair your boot loader problem by installing Grub.  After that restart your system, then new GRUB menu will appears but its not look GUI, its like GRUB Boot Menus,  It contains the collection of OS list you installed previously.  But I like this Easy BCD Menu and GUI of Windows Boot Loader but its not work for me, share you view if you got any alternate solution for your problem.

---

