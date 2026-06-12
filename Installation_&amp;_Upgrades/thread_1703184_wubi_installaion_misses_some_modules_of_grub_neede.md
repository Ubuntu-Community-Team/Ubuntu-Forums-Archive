---
title: "wubi installaion misses some modules of grub needed to work with Xen"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2011-03-08
Here is a situation I installed Ubuntu on a friends laptop using Wubi in his Windows 7 drive.I have installed and things worked by now perfectly without any problem.We are trying to set up a Xen (virtualization)environment in this laptop.After setting up every thing cleanly.When I needed to boot with following grub entries
```

menuentry "Xen Linux 2.6.32.27" {
      insmod ntfs
      set root='(hd0,2)'
      loopback loop0 /ubuntu/disks/root.disk
      set root=(loop0)
      multiboot /boot/xen.gz
      module    /boot/vmlinuz-2.6.32.27 dummy=dummy root=/dev/sda2
loop=/ubuntu/disks/root.disk ro console=tty0
      module    /boot/initrd.img-2.6.32.27
}

```
I got
```
error:file not found.
```
when booting and 
```
error file not found
error unknown command 'multiboot'
error unknown command 'module'
error unknown command 'module'

```

Now to dig this issue further I reboot the machine and go to grub command prompt and manually pass on each of the above parameters which you see in the grub entry when I reached
```
grub> insmod multiboot
```
then I got following message on screen
```
error:file not found.
```

It looks like this  grub setup has just enough modules to use loopback file on ntfs and directory grub in > C:\ubuntu\install\boot\grub is completely empty.
Since the ACTUAL /boot directory is on the loopback NOT  ntfs (hd0,2). Therefore any attempt to read any files from (hd0,2)  simply wont work, cause there's no file there.

I necessarily need to use ```
insmod multiboot 
```and command multiboot and module which are available in grub on a normal install which is done without using Wubi.But since the laptop is not mine so I am not allowed to partition it and have to make it work in this situation only.
While a normal Kernel is still booting? How can I get module multiboot in this Wubi based install?

---

