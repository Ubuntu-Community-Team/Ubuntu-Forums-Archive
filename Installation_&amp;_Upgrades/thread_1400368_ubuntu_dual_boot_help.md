---
title: "ubuntu dual boot help"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by capt_nemo777 on 2010-02-06
Hi, I expanded my HD to 500gb, now I got a nice windows 7 running in it. but I want an ubuntu linux distro for dual boot, what should I do first ?, [ if you will recommend wubi,i think I read some bad rumors about it] ,, i want an ubuntu dual boot for using on LAMP development . TIA

---

### Post by ssulaco on 2010-02-06
> **capt_nemo777 said:**
>  [ if you will recommend wubi,i think I read some bad rumors about it]
Ive had real good luck with Wubi,I cant tell the difference in speed vs a Hardrive install,plus if you dont like it use Windows add/remove programs to get rid of it
or you can partition your drive and install Ubuntu:
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

---

### Post by wilee-nilee on 2010-02-06
With W7 being able to change the partition size of it's own setup, it is easy to install Ubuntu on any free space; granted your within maximum partition types on the hard drive.

Wubi is basically a way of trying it out. I would use a virtual like the Sun VM instead if you want to check out Ubuntu, you need at least a gig of ram for W7 and at least 512 for Ubuntu. The virtual is easily removed having never messed with the master boot record, which Wubi does and can leave at the least the choice of Ubuntu after removal in the MS MBR. This can be removed easily but the VM is better I think.

If you are familiar with Ubuntu and want a actual dualboot then shrink the W7 from the Disk management program leaving a open partition for Ubuntu and install.

---

### Post by brianfactors on 2010-02-07
I'd say VM over Wubi myself...

But that technically isn't dual boot. Really, you just need to install the Ubuntu ISO to a CD and install it normally. The only tricky part will be when you get to the partition manager.

If you want to make it easy on yourself, just have Windows 7 only use part of the hard drive. Then make the rest into a random partition and tell Ubuntu to use it and use the default formatting.

A little more detailed: You will create at least three partitions:
1) The windows partition -duh
2) Your SWAP partition - this is where Ubuntu puts extra stuff it can't fit into memory - also is used to save your data during suspend. The rule of thumb is to have your swap be twice your RAM size. But if you have about 4 GiB of RAM, you probably only need that much SWAP anyway.
3) The Ubuntu root partition (which the partition should take care of mostly without requiring you.) Just realize that you probably want to label it as "/" and format it something like ext4.

Hope that gives you the general idea... For more specifics: [https://help.ubuntu.com/9.10/installation-guide/index.html](https://help.ubuntu.com/9.10/installation-guide/index.html)

---

### Post by capt_nemo777 on 2010-02-07
> **brianfactors said:**
> I'd say VM over Wubi myself...

If you want to make it easy on yourself, just have Windows 7 only use part of the hard drive. Then make the rest into a random partition and tell Ubuntu to use it and use the default formatting.



I still got 218GB free in my C:\ drive where my windows 7 OS is installed, and I should just tell ubuntu to use the free space available, is that what you mean by the quoted statements ? , OR do I still need to do some shrinking volume stuffs ? :confused:

---

### Post by Jive Turkey on 2010-02-07
> **capt_nemo777 said:**
> I still got 218GB free in my C:\ drive where my windows 7 OS is installed, and I should just tell ubuntu to use the free space available, is that what you mean by the quoted statements ? , OR do I still need to do some shrinking volume stuffs ? :confused:
There are a couple of ways you could resize the partition.  I'm assuming the entire drive is windows ntfs?  Windows7 can resize its own partition though I'm not sure exactly how.  I've always used the live CD installer, when it asks you where you want to install ubuntu select the advanced mode and it opens up a disk partitioning tool that is easy to use.  Be careful to resize the windows partition, not delete it.

That said, if you're just wanting to mess around with LAMP, you would be well served installing ubuntu server edition in a VM.  Virtualbox is a nice option you can use on both windows and linux.  If you do it that way you can run the server on top of windows7, even a couple of them at the same time.  It makes it easy to roll back changes on the VM and start fresh as often as you like.  The desktop edition works well in a VM too.

If you're unclear on what I'm talking about:
1) Install virtualbox on Windows.
2) Download ubuntu iso image.
3) Create a virtual machine with virtualbox and install ubuntu on it.
Advantages: no need to burn a cd, cloneable, you can use windows at the same time.

---

### Post by capt_nemo777 on 2010-02-07
> **Jive Turkey said:**
> 
1) Install virtualbox on Windows.


is this the virtual box you're talking about ?
```

http://www.virtualbox.org/wiki/Downloads

```

---

