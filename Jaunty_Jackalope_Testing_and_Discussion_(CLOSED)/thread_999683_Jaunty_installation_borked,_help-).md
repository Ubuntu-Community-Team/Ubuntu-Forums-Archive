---
title: "Jaunty installation borked, help:-)"
date: 2008-12-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter76 on 2008-12-02
Hello, I'm running Jaunty in VirtualBox. I updated Jaunty a couple of days ago and now when I want to run Jaunty it boots into memtestx86, which is the only option left in my grub menu. I booted with a livecd to try to setup Grub again, but found out I have no kernels in /boot ; only memtest. When trying to chroot into my Jaunty install and then updating the install, something is wrong with miy network setup ( in the chroot ); I have an IP, but dns resolving is not working... Is ther a solution to this or should I reinstall? Thanks in advance,

Peter Moll

---

### Post by Gina on 2008-12-02
Others may have a "quick fix" but I would reinstall.

---

### Post by Peter09 on 2008-12-02
Hi,
I've a similar problem and thread running. This happened to me today, thought I was the only one - guess I'm not glad to have company but at least it wasn't just me who got singled out for this.

[http://ubuntuforums.org/showthread.php?t=999625](http://ubuntuforums.org/showthread.php?t=999625)

Anyone have an easy fix yet?

Edit -- two Peters .... Spooky .. is there room for a conspiracy theory here

---

### Post by ronacc on 2008-12-02
well since you may be looking at a reinstall anyway you could try downloading the necessary kernel stuff with the install you are chrooting from and then extracting and copying it by hand to jaunty .

edit   use caution a mistake could take out your working install.

---

### Post by caljohnsmith on 2008-12-02
Here is how you could install a kernel by chrooting (assume the Jaunty partition is sdaX):
```
sudo mount /dev/sdaX /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
apt-get install <kernel packages>
exit
```
I think you get the idea, but the important part is to bind mount the important linux system directories onto the mounted Jaunty partition, and also to copy over the resolv.conf file which has your DNS servers; that way you should be able to download. How about giving that a shot and let me know how it goes.

---

### Post by Peter76 on 2008-12-02
Thanks Calljohnsmith, that did the trick, although there is something wrong with the kernel image as mentioned here: [http://ubuntuforums.org/showthread.php?t=996735](http://ubuntuforums.org/showthread.php?t=996735)

Still strange I ended up without a kernel... Must be like mentioned by Peter09, that if a user "Peter" updates his system, the kernel will be removed:-)

---

### Post by caljohnsmith on 2008-12-02
> **Peter76 said:**
> Thanks Calljohnsmith, that did the trick, although there is something wrong with the kernel image as mentioned here: [http://ubuntuforums.org/showthread.php?t=996735](http://ubuntuforums.org/showthread.php?t=996735)

Still strange I ended up without a kernel... Must be like mentioned by Peter09, that if a user "Peter" updates his system, the kernel will be removed:-)
That's great news, glad it worked OK for you. Cheers and hope everything else runs smoothly in Jaunty for you. :)

---

