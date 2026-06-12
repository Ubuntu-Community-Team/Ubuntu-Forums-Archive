---
title: "no free space on /boot after upgrade"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by unsichtbarkeit on 2013-08-21
hi,
i am running ubuntu 13.04 on thinkpad T61.
installation went very well, but apparently problems started with upgrades.
first i received crash reports saying that unattended-upgrades package crashed. and asking me to reboot.
then i received the message that there are no free space on my /boot partition. 
i found out that there are couple of new kernel on my /boot, but i am actually using an older one. so i am suspecting that the unattended-upgrades tried to silently upgrade my kernel, but something is wrong happened, and the new kernels was downloaded but never rightly installed, that is why i boot automaticly to the old kernel. 

here is the code:
~$ ls /boot:
abi-3.5.0-32-generic         initrd.img-3.8.0-27-generic
abi-3.8.0-23-generic         lost+found
abi-3.8.0-25-generic         memtest86+.bin
abi-3.8.0-26-generic         memtest86+_multiboot.bin
abi-3.8.0-27-generic         System.map-3.5.0-32-generic
abi-3.8.0-29-generic         System.map-3.8.0-23-generic
config-3.5.0-32-generic      System.map-3.8.0-25-generic
config-3.8.0-23-generic      System.map-3.8.0-26-generic
config-3.8.0-25-generic      System.map-3.8.0-27-generic
config-3.8.0-26-generic      System.map-3.8.0-29-generic
config-3.8.0-27-generic      vmlinuz-3.5.0-32-generic
config-3.8.0-29-generic      vmlinuz-3.8.0-23-generic
grub                         vmlinuz-3.8.0-25-generic
initrd.img-3.5.0-32-generic  vmlinuz-3.8.0-26-generic
initrd.img-3.8.0-23-generic  vmlinuz-3.8.0-27-generic
initrd.img-3.8.0-25-generic  vmlinuz-3.8.0-29-generic
initrd.img-3.8.0-26-generic

~$ uname -r
3.8.0-27-generic

any ideas what to do?
thanks

---

### Post by unsichtbarkeit on 2013-08-21
i forgot to say that i have a permanent crash message, and a message of no space on /boot whenever log in to the laptop :(

---

### Post by jonnyboysmithy on 2013-08-21
You can free up more space by removing kernels you don't need anymore. I'd keep always keep at least 2 or 3 kernels installed as backups.
Personally I like to use synaptic package manager to do this. Its not as pretty as ubuntu software center but I can find packages by name much more easily with it.
Let us know how it goes :)

EDIT: this guide could help you get started:[http://www.upubuntu.com/2012/10/how-to-easily-remove-unused-linux.html](http://www.upubuntu.com/2012/10/how-to-easily-remove-unused-linux.html)

---

### Post by grahammechanical on 2013-08-21
Do you have a separate /boot partition? If so you might want to make it larger or regularly remove older kernels. If you do not have a separate /boot partition but instead just a /boot folder then is the /partition filling up? The /boot folder can expand to whatever size it needs but once the partition starts to fill up there are problems.

You can create space by emptying the Rubbish bin. Also there is a Recovery Mode option called Clean = Try to make free space. I have never tried this. I do not know how successful it will be or what it will remove.

UPDATE

I have just checked the Recovery Mode scripts and the Clean option runs

```
apt-get clean
```

which removes all packages from the package cache. And

```
apt-get autoremove
```

which removes packages installed by other packages and are no longer needed.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by unsichtbarkeit on 2013-08-21
thanks all,
i used synaptic to remove old kernel, and it worked out.
while deleting the old kernel, synaptic installed the 'hanged' kernel, and after reboot the new kernel was automaticly used. 
and i don't receive the message of no memory on /boot
thanks again

---

