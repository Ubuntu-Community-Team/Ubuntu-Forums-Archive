---
title: "Update went wrong. 9.04 server"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by fikkaud on 2010-04-05
I just did a package update through webmin and noticed that all packages failed to install due to lack of space in /boot (guess kernel upgrades) 
However webmin reported successfull install of all 20 updates and now my system won't boot anymore.
 
My next step would be to restore the system from backup.
Then to free up space in /boot. 
My question is how to approach this safely. removing older images and more.
 
regards
A

---

### Post by Tylerjd on 2010-04-05
Can you tell us what the failure is? Is it a **grub-rescue> **prompt, or does the BIOS report no operating system found? Or something else?

---

### Post by fikkaud on 2010-04-05
OK,
For now I have only had remote access, so I don't know yet if it's trying to boot fom a non exixting kernel number. I'll know more tomorrow when I bring a keyboard an monitor to the place the box is sitting.
 
However, I'm confident I'll get it up and running again. Can you still advice how to free up space in /boot removing older kernels?
 
A

---

### Post by Tylerjd on 2010-04-05
Use an Ubuntu live desktop CD, and this is what I would try, I'm pretty sure that it will work, but I don't know. I will install a ubuntu server vm and find out. But once your live cd is booted, open terminal and do the following to free up space in /boot.
```

sudo rm /boot/initrd.img.x.x.xx-xx-generic
sudo grub-update

```*x's being for old initrd.img numbers

Once i get a VM server up and running I'll try it so you don't have to kill a production machine.

---

### Post by fikkaud on 2010-04-05
Thanx, I won't give it a go until much later today anyway.
 
Edit: Got the system back by choosing previous img in GRUB :) Will later try the suggested option to remove older images from /boot. 
 
A

---

