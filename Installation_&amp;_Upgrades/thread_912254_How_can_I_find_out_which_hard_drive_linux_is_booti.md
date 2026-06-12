---
title: "How can I find out which hard drive linux is booting form?"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by coden4fun on 2008-09-06
Hi, I have Ubuntu on my secondary slave drive, which is 160GB and there isn't anything on my Primary 250GB hard drive, for I have verified that using the Partition Editor.

However, I've realized that when my computer boots up it automatically boots Ubuntu, but that would mean my Grub boot loader is some how on my 250GB hard drive, right?

The reason why I ask is because I'm going to to install Windows XP for 2 weeks as I get some work done that I'm just comfortable doing in XP, and I want to make sure that when I install XP I'm not going to accidentally partition, or delete my Ubuntu that I've spent 2 weeks personalizing.

And I would like to make sure that my Ubuntu machine and even the Grub loader is only on the secondary slave drive, and I would like some way to verify this, and if not I would like to find away to fix this.

---

### Post by Pumalite on 2008-09-06
Post:
sudo fdisk -lu
You can take a look at your menu.lst too.

---

### Post by caljohnsmith on 2008-09-06
> **coden4fun said:**
> 
And I would like to make sure that my Ubuntu machine and even the Grub loader is only on the secondary slave drive, and I would like some way to verify this, and if not I would like to find away to fix this.
As you suspect, Grub is currently in the MBR of your master HDD. To install Grub to the MBR of your slave HDD, just do the following from a terminal in Ubuntu:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Now you can go ahead and install Windows XP on your master HDD, and of course Win XP will overwrite Grub in the MBR with its own MBR. But you'll need to modify your /boot/grub/menu.lst in Ubuntu since it will be booting off the same HDD now. All the Ubuntu entries in menu.lst will be using something like (hd1,X), and all you have to do is change them to (hd0,X). If you have any problems or questions, let me know, otherwise let us know how it goes.

---

### Post by coden4fun on 2008-09-06
so can't I just add XP to the menu.list in the Grub and throw grub on the Second drive, then after XP is finish messing up my system go back move it back to the masterdrive, add xp to the list and have Grub make me a nice list to see if I want to boot to either Ubuntu or XP?

---

### Post by Pumalite on 2008-09-06
Search and take a look at this thread in the Forum:
Dualboot Two Hard Drives

---

### Post by caljohnsmith on 2008-09-06
> **coden4fun said:**
> so can't I just add XP to the menu.list in the Grub and throw grub on the Second drive, then after XP is finish messing up my system go back move it back to the masterdrive, add xp to the list and have Grub make me a nice list to see if I want to boot to either Ubuntu or XP?
If you can set your BIOS to boot your slave HDD (Ubuntu), then I think it would be most ideal if you install Grub to the MBR of your slave drive (using the directions I gave in my last post), and let Windows install its own MBR to the master drive; then you can add Windows to your Grub's menu.lst and boot it just fine, just like you mention. But the advantage of this scenario is if your Ubuntu drive ever becomes unbootable for some reason (or you have other Grub problems), you can always set BIOS to boot your master HDD and Windows will still work. If you do it your way, you won't be able to boot Windows if anything goes wrong with Grub or your slave HDD.

---

### Post by coden4fun on 2008-09-06
> **caljohnsmith said:**
> If you can set your BIOS to boot your slave HDD (Ubuntu), then I think it would be most ideal if you install Grub to the MBR of your slave drive (using the directions I gave in my last post), and let Windows install its own MBR to the master drive; then you can add Windows to your Grub's menu.lst and boot it just fine, just like you mention. But the advantage of this scenario is if your Ubuntu drive ever becomes unbootable for some reason (or you have other Grub problems), you can always set BIOS to boot your master HDD and Windows will still work. If you do it your way, you won't be able to boot Windows if anything goes wrong with Grub or your slave HDD.

Thanks, I'll do that.

---

### Post by caljohnsmith on 2008-09-06
> **coden4fun said:**
> Thanks, I'll do that.
OK, let us know if you run into any problems; also, to save you a future hassle, here is the Windows entry to put into your Grub's menu.lst:
```
title   Windows
root    (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
That should work assuming Windows is installed into the first partition of your master HDD.

---

### Post by zipperback on 2008-09-06
> **coden4fun said:**
> 
The reason why I ask is because I'm going to to install Windows XP for 2 weeks as I get some work done that I'm just comfortable doing in XP, and I want to make sure that when I install XP I'm not going to accidentally partition, or delete my Ubuntu that I've spent 2 weeks personalizing.




Install virtualbox and you can install windows in a virtual machine and then you don't have to worry about messing up your Linux installation.

- zipperback
:popcorn:

---

### Post by coden4fun on 2008-09-06
> **caljohnsmith said:**
> OK, let us know if you run into any problems; also, to save you a future hassle, here is the Windows entry to put into your Grub's menu.lst:
```
title   Windows
root    (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
That should work assuming Windows is installed into the first partition of your master HDD.

Thanks your real helpful!

Also, I tried virtualbox, but didn't have the correct virtualbox kernal driver installed, so I was like hm... It's probably easier to just dual boot for now.

---

