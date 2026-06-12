---
title: "How to install more than one linux distros on a single HDD?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by kipriaan on 2011-04-24
Hello!
I'd like to install more then one linux distros on my HDD (Ubuntu, OpenSuse and Linux Mint for instance). I've heard that it is possible. I tried to find out the best ay to do that, but what I found was referring to older versions and the explainations weren't very accurate. Which are the steps to do this multiple installation, in order to make sure all the distros will function properly. Is there something to edit in the bootloader? I'd apreciate some advice in this aspect. Thanks.

---

### Post by Iusedtowearatie on 2011-04-24
Unclear what the purpose of this would be... Other than exploring different distros - which is an admirable ambition. If that is the case, a good choice would be to run som hypervisor and install all OS:s as virtual machines. If your basis is Windows, WMWare Player would do the job, if your basis is some Linux distro, you'll need a Linux hypervisor (haven't tried this myself, probably someone else in the forum could guide you on this).

---

### Post by al111 on 2011-04-24
Create multiple partitions and a linux swap file-

Install the distro(s) you want (each distro on its' own partition)-

Update grub afterwards-

```

sudo update-grub

```

---

### Post by Hedgehog1 on 2011-04-24
Another option for running multiple OS's is running Virtual Box with as many OS's as you want:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]


***The Hedge***

:KS

---

### Post by coffeecat on 2011-04-24
@kipriaan, of those three, install opensuse first, unless you enjoy rummaging around in grub configuration files. :wink: Mint (which is based on Ubuntu) and Ubuntu will autodetect other operating systems when you install and set up a multibooting grub menu for you. Opensuse does not. Opensuse will detect the presence of Windows but not other Linux OSs. So, install opensuse and then either Mint or Ubuntu and then the third. Each will install grub to the mbr, but it will be the last one you will be using. If Mint or Ubuntu you will have a multibooting menu.

If you ever decide to try Fedora, the same caveat applies as with opensuse - it doesn't bother to look for other Linux OSs. In fact, it's so cavalier in this respect that it refers to Windows as "Other" in the grub menu. 

If you set up your partitions beforehand, you need to choose the manual/advanced option in the Ubuntu and Mint installers to point the installer to the partition of your choice. Opensuse has a similar option but I cannot remember what it is called.

---

### Post by al111 on 2011-04-24
> **Hedgehog1 said:**
> Another option for running multiple OS's is running Virtual Box with as many OS's as you want:

***The Hedge***

:KS

I just downloaded VM...nice program-

---

### Post by walt.smith1960 on 2011-04-24
Paid shareware solution works for me.  I see the product name has changed; I don't know what else beside the name has changed. I've been using BootitNG for a few years. 
[http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm)
The program creates an extended MBR and each partition can be separate or been seen by other partitions as you choose.  You can have over 100 partitions, each with its own operating system. There's one thing to be aware of when installing Linux & GRUB.  You have to use the advanced installation program to choose the partition and make sure that GRUB is placed in the partition, not in the MBR where the install process wants to put it. In fact if you refresh GRUB from a LiveCD, there are dire warnings about putting GRUB in the partition instead of the MBR.  Put it in the partition anyway:).

---

