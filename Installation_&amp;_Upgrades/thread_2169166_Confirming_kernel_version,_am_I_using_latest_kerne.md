---
title: "Confirming kernel version, am I using latest kernel avaliable?"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by jonnyboysmithy on 2013-08-20
hi guys, 

I received an update for linux-headers-generic-lts-quantal version 3.5.0.37.43 to version 3.5.0.39.45 
thats all good but I only get kernel 3.5.0-32-generic listed in grub. 

So my question is shouldn't grub be listing 3.5.0.39 instead of 3.5.0-32?




P.S.
output of uname -r
  3.5.0-32-generic.
Attached is screenshot of update history in software center

---

### Post by Quackers on 2013-08-20
Open a terminal window and run 
sudo update-grub
then see if the menu entries change to include the new kernel. (Though I would have thought that should already have run by default).

---

### Post by jonnyboysmithy on 2013-08-20
That was my first reaction too.
Heres output:```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


```

---

### Post by deadflowr on 2013-08-20
You do notice the difference between linux-headers and linux-image?
Do you have the linux-image-lts-quantal packages installed?

---

### Post by jonnyboysmithy on 2013-08-20
No I don't have the linux-image-lts-quantal package installed. I'm using 12.04 Precise Pangolin.
Ah, but I do have the linux-headers-generic-lts-quantal installed. 

Should I install the linux-image-lts-quantal package?
EDIT:I'll try it, lets see what happens... :)

---

### Post by deadflowr on 2013-08-20
> **jonnyboysmithy said:**
> No I don't have the linux-image-lts-quantal package installed. I'm using 12.04 Precise Pangolin.
Ah, but I do have the linux-headers-generic-lts-quantal installed. 

Should I install the linux-image-lts-quantal package?
EDIT:I'll try it, lets see what happens... :)

Yes.
If you have synaptic installed it'll make life easier.
When you it install the package, I think it'll also install another package.
I think it's something like linux-image-extra-lts-quantal.
But searching in synaptic will make it easier, especially for correct spellings.

---

### Post by jonnyboysmithy on 2013-08-20
Excellent!
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
``` It worked! 
SOLVED
It also installed another package I forgot the name, but it did the trick. 
Yes I'm using synaptic, its super handy.

Thanks for your help everyone!

---

