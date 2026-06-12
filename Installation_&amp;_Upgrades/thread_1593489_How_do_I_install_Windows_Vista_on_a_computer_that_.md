---
title: "How do I install Windows Vista on a computer that only has Ubuntu Maverick Meerkat?"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by ProcuratorIncendia on 2010-10-11
Like the title says...
PS. It's Urgent.

---

### Post by bardu on 2010-10-11
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by dino99 on 2010-10-11
i dont use that crap but if i remember it need the first partition on hdd, so with ubuntu you have to make room with gparted, or better to boot with partedmagic, next use the vista cd for installation (grub will be removed so you need the cd of ubuntu to reinstall grub-pc.

---

### Post by sgwebb on 2010-10-11
I would recommend using virtual box, I have an XP install that I use for times when I have to do something in Windows.. this works very well for me
here is how to do it 
[http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

---

### Post by oldfred on 2010-10-11
If you create a partition, it does not have to be first, but does have to be a primary partition. So depending on what partitions you have used may change how you install.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by ProcuratorIncendia on 2010-10-12
I do not want virtual box because it would take too long to install it inside a virtual box. Many features don't work, my Ubuntu ends up lagging and the vista virtual box doesn't have all the necessary RAM.

[How do I use test disk?]
[How do I install vista with Ubuntu meerkat installed first]
[I would prefer to use grub2 as it is easier]
[I only want to run the Vista disk and will not run any others unless I have to.]

---

### Post by ProcuratorIncendia on 2010-10-12
BUMP
THIS IS URGENT...I need this done today!

---

### Post by oldfred on 2010-10-12
Older but goes over some of the issues, but use grub2 not any of the other alternatives shown:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")


Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

After you install windows you will have to reinstall grub2 to the MBR and then once booted into Ubuntu run sudo update-grub for the osprober to find the windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ProcuratorIncendia on 2010-10-12
None of those help very much.

Please check my understanding [say yes or no...]

So I should:
1. Make free space.
2. Install Windows to the free space.
3. Shutdown computer.
4. Load my  lucid disk [,to minimise problems, lucid didn't break when I installed it.]
5. Install lucid to some small space.
6. Fin.

---

### Post by ProcuratorIncendia on 2010-10-12
BUMP...THIS IS URGENT...I NEED windows.

---

### Post by oldfred on 2010-10-12
You should be able to use free space or a NTFS partition that you create. You have to have another primary partition available or it will not be able to use the free space.

If you have Ubuntu installed you just use the liveCD to reinstall grub2 per links above. Otherwise you will just be booting windows.

---

### Post by ProcuratorIncendia on 2010-10-12
Can you please just tell me if 
> 1. Make free space.
2. Install Windows to the free space.
3. Shutdown computer.
4. Load my lucid disk [,to minimise problems, lucid didn't break when I installed it.]
5. Install lucid to some small space.
6. Fin.
Is correct?

---

### Post by pricetech on 2010-10-12
> **ProcuratorIncendia said:**
> Can you please just tell me if 

Is correct?

Step 5 should be reinstall GRUB.

---

### Post by ProcuratorIncendia on 2010-10-13
Installing grub is too complicated. I would rather just install lucid and let it install grub.
...Okay...unless anyone has anything else to say, I'm installing vista according to those steps I listed.

---

