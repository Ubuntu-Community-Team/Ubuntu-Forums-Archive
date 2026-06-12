---
title: "Is it safe to remove files from /boot ?"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by skylarmt on 2013-02-18
Hello.  I hope this is the right place to post this.  So, I just looked in my /boot folder, hoping to find something to delete.  I found 6 old versions of initrd.img and vmlinuz with accompanying configs and stuff, and thought, "I can delete this."  But then I thought, "Anything with boot in the path might be best left alone," but *then* thought, "I'll ask these guys!"

So, is it safe to delete all the versions of the files except the latest one?  i.e. delete initrd.img-3.2.0-37-generic and keep initrd.img-3.2.0-38-generic?  Because there's 180MB of old stuff in there.  Thanks!

```
$ ls /boot
System.map-3.2.0-29-generic  abi-3.2.0-35-generic     config-3.2.0-38-generic      memtest86+_multiboot.bin
System.map-3.2.0-33-generic  abi-3.2.0-36-generic     **grub**                         vmlinuz-3.2.0-29-generic
System.map-3.2.0-34-generic  abi-3.2.0-37-generic     initrd.img-3.2.0-29-generic  vmlinuz-3.2.0-33-generic
System.map-3.2.0-35-generic  abi-3.2.0-38-generic     initrd.img-3.2.0-33-generic  vmlinuz-3.2.0-34-generic
System.map-3.2.0-36-generic  config-3.2.0-29-generic  initrd.img-3.2.0-34-generic  vmlinuz-3.2.0-35-generic
System.map-3.2.0-37-generic  config-3.2.0-33-generic  initrd.img-3.2.0-35-generic  vmlinuz-3.2.0-36-generic
System.map-3.2.0-38-generic  config-3.2.0-34-generic  initrd.img-3.2.0-36-generic  vmlinuz-3.2.0-37-generic
abi-3.2.0-29-generic         config-3.2.0-35-generic  initrd.img-3.2.0-37-generic  vmlinuz-3.2.0-38-generic
abi-3.2.0-33-generic         config-3.2.0-36-generic  initrd.img-3.2.0-38-generic
abi-3.2.0-34-generic         config-3.2.0-37-generic  memtest86+.bin

```

---

### Post by tgalati4 on 2013-02-18
Keep the last 2.  If you have a boot problem, you can boot into an older kernel as a backup.

---

### Post by ibjsb4 on 2013-02-18
To remove old kernels I prefer to use synaptic.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by oldos2er on 2013-02-19
> **ibjsb4 said:**
> To remove old kernels I prefer to use synaptic.

+1

Use Synaptic or whatever your favorite package manager front-end is to remove kernels. APT may become confused otherwise.

---

