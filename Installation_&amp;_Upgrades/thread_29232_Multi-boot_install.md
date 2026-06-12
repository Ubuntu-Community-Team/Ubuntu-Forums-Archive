---
title: "Multi-boot install?"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by gratefulfrog on 2005-04-23
I have installed Hoary64bit on my AMD64 with the automatic partitioning scheme.

Unfortunately, many of the applications that I need just won't work on it.

Now I would like to add a 160GB SATA drive and try some other distros, such as:
Hoary32bit,
Fedora2
Suse32bit
Suse64bit.
...
Can anyone suggest a partitioning scheme for the new disk that would allow me install and to boot any of the OS's, while still being able to see the others?

Alternatively, any links to useful documentaton would be greatly appreciated.

---

### Post by alastair on 2005-04-23
If you are only testing, then :

1 swap partition (can be used by all of them)
1 partition per distribution

Perhaps a (larger) separate /home that they could share?

What applications did not work?

---

### Post by nad on 2005-04-23
I would create a /boot partition, with an ext2 filesystem, of about 100M at the begining of the first hard drive. This will give you room for ~15 compressed kernels and their associated map and init images. This will also make administration of your boot options easier as everything will be in one place. Install grub to the mbr and point it to the /boot partition. As you continue to install os's be certain that grub continues to point to and install in your /boot partition and that it recognizes _all_ of your previous os's. If you don't do this, grub will install to that os's file system and you will have to remember where grub is pointing to in order to correct any problems. It may become necessary to not install grub and then manually put the needed files in your /boot partition, edit menu.lst and run the grub shell to synchronize everything.

Four os's in 160G? That's 30G each primary partitions, the last logical partition could have 500M - 3G of swap partition depending on whether you need space to play with mounted iso's and the rest is unpartitioned space for ...

Other than that, it's simple. Let us know of any problems.

Dan M

---

### Post by moinahmd on 2005-04-24
I have a similar problem. I have windows me on drive c and and am installing Ubuntu Hoary Hedgehog 5.04 (from DVD) on it. I chose the option to erase everything on drive d during the Ubuntu install. all goes well except when the computer reboots all I get is a line that says :

Grub>

What does this mean? I am new to Linux and I do not know what to do now. I have reinstalled many times and samething happens. I even made sure I installed boot loader to MBR when it asked me that question.

Please help. ](*,) 

*[I]I have Compaq Pressario 800MHz with 128 MB memory and ATI video card.* [/I]

---

### Post by nad on 2005-04-24
You have entered the grub shell. At this moment nothing else is running and it is expecting you to control the os loading process from here.

Issue this command: find /boot/grub/stage1 and post the result.

D
an M

---

