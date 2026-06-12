---
title: "How can I use a diff package?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by kg356 on 2010-08-29
Hi, this is my first post. I need to format my flashdrive to UFS file  system. I enabled UFS write and read support by modifying  the kernel.  The only thing that I've found is ufsutils package -  [http://packages.ubuntu.com/maverick/ufsutils](http://packages.ubuntu.com/maverick/ufsutils) , but I don't know how to  use it. I typed "patch" in terminal and it was unpacked. Just some files  with *patch extension. Pls help

---

### Post by oldos2er on 2010-08-29
Run ```
sudo apt-get update && sudo apt-get install ufsutils
``` then according to the package info, you should be able to run mkfs.ufs to format
your flash drive.

---

### Post by kg356 on 2010-08-29
Thanks for reply. 
I downloaded it, but I can't format.

```
root@******:~# mkfs.ufs /media/C444-0C7F
mkfs.ufs: /media/C444-0C7F: failed to open disk for writing
```I'm running Ubuntu on a virtual machine, does it matter? The USB stick is attached via virtual machine, but I can write data on it.

And one more thing. There is a parameter that allows to select fs: UFS or UFS2.

```
-O file system format: 1=> UFS1, 2 => UFS2
```And I dunno how to use that parameter, I typed [ -O 2], [ -O2], [ -O: 2] etc. But it didn't seem to be a valid use of the parameter.

---

### Post by kg356 on 2010-08-30
bump

---

### Post by oldos2er on 2010-08-30
> **kg356 said:**
> I'm running Ubuntu on a virtual machine, does it matter? 

I have no idea, sorry.

---

### Post by kg356 on 2010-08-31
Ok, so I'll try another way. I can't install any other os, because currently I have no enough free space on the HDD. I have a linux kernel with UFS r/w enabled. It's a deb package. Linux iso can be used as live cd, can't it? So I'll unpack squashfs and replace the kernel. But where is the kernel? What directory? Can I just replace the kernel using a file manager? Just unpack and replace the kernel? Then pack it to squashfs and burn as iso. Boot it and I have an Ubuntu install with the modified kernel? And I almost forgot one more thing, ufsutils are needed too. So if I run ubuntu from live cd, can I use sudo apt-get command and install any app I want?

---

