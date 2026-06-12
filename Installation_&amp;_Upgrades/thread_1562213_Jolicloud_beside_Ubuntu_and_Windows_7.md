---
title: "Jolicloud beside Ubuntu and Windows 7?"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by binarylife on 2010-08-27
So I have dual boot , windows 7 with ubuntu 10.04 amd64.
Can I install Jolicloud beside them?Also I have a HP550 laptop ,which isn't a notebook? So is there any way that I can have jolicloud ?  

p.s: I have jolicloud on virtualbox, but I need to try it better.
thanks

---

### Post by binarylife on 2010-08-27
help please?

---

### Post by Fableflame on 2010-08-27
I don't see your laptop model in the list of compatible hardware, so I don't know if it will work.

---

### Post by binarylife on 2010-08-27
> **Fableflame said:**
> I don't see your laptop model in the list of compatible hardware, so I don't know if it will work.

so you don't know,how can I be sure that it'll work?
I really need this 
if not ,is there linux os similar to Jolicloud that can i dual with ubuntu and windows ,and if necessary I can uninstall windows 7 .
thanks by the way :)

---

### Post by binarylife on 2010-08-29
Hi,
I've installed Jolicloud as triple-boot, beside Ubuntu 10.04 and Windows 7.(Ubuntu in drive C with Windows 7,Jolicloud in drive D).
I run Ubuntu using wubi inside Windows and everything was perfect until I have installed Jolicloud(I was using winboot then grub2 to boot to ubuntu easily).

So when I installed jolcloud also inside windows using jexpress ,windows 7 and jolicloud work fine.But the problem is with Ubuntu when I choose it from winboot it wouldn't open ,Jolicloud opens instead ,like it installed over it .So how can I fix Ubuntu please???
Thanks
:(
p.s: Jolicloud works perfect for my laptop model HP550.

---

### Post by binarylife on 2010-08-29
help

---

### Post by Iowan on 2010-08-29
Merged threads - deleted some duplication.

From the Code of Conduct: > Please do not cross post, or post the same thing in multiple locations.

---

### Post by varunendra on 2010-08-29
> **binarylife said:**
> So when I installed jolcloud also inside windows using jexpress ,windows 7 and jolicloud work fine.But the problem is with Ubuntu when I choose it from winboot it wouldn't open ,Jolicloud opens instead ,like it installed over it .So how can I fix Ubuntu please???

Simple! Don't install anything 'inside' Windows. Instead, install them in separate partitions. Just uninstall them from Win7 and using Gparted, create separate partitions for Jolicloud & Ubuntu. Then install Jolicloud first, afterwards- Ubuntu 10.04.

Jolicloud is based on Ubuntu 9.04, so I guess it might be using grub legacy. Whatever, if you install Lucid in the last, Grub2 installed with it should be able to take care of everything.

If you want to save something from your previously running Ubuntu, try locating root.disk file in \ubuntu\disks folder of your Windows partition. Copy it somewhere, reinstall Wubi then from within windows, replace the new root.disk file with the copied one and you should get your ubuntu back. Just reboot into ubuntu, copy the data to a different partition.

Then uninstall from win7, reinstall in its own partition.

---

### Post by binarylife on 2010-08-31
> **varunendra said:**
> Simple! Don't install anything 'inside' Windows. Instead, install them in separate partitions. Just uninstall them from Win7 and using Gparted, create separate partitions for Jolicloud & Ubuntu. Then install Jolicloud first, afterwards- Ubuntu 10.04.

Jolicloud is based on Ubuntu 9.04, so I guess it might be using grub legacy. Whatever, if you install Lucid in the last, Grub2 installed with it should be able to take care of everything.

If you want to save something from your previously running Ubuntu, try locating root.disk file in \ubuntu\disks folder of your Windows partition. Copy it somewhere, reinstall Wubi then from within windows, replace the new root.disk file with the copied one and you should get your ubuntu back. Just reboot into ubuntu, copy the data to a different partition.

Then uninstall from win7, reinstall in its own partition.

Works Great , Thanks a lot dudu: ) ..

---

### Post by varunendra on 2010-08-31
> **binarylife said:**
> Works Great , Thanks a lot dudu: ) ..
It's alright!

By the way, I suggested two different things. Not sure which one made you so happy :D. Would be nice if you confirm, & if it is all you needed, please consider marking thread as [solved] (click my sig. to see how).

-Thanks!

---

### Post by binarylife on 2010-08-31
> **varunendra said:**
> It's alright!

By the way, I suggested two different things. Not sure which one made you so happy :D. Would be nice if you confirm, & if it is all you needed, please consider marking thread as [solved] (click my sig. to see how).

-Thanks!

First It's Thanks a lot dude : ) {not dudu ,typing error:D}.Second, as u said it's simple I just need to install every OS in separated partitions.Windows 7 remained in the same drive (C), and I've installed jolicloud in another drive which is (D) for example ,And finally I've installed Ubuntu in another drive (F) .And as you said grub2 will take care of everything : ) , so I boot up simply for  whatever OS I want .Thanks

---

