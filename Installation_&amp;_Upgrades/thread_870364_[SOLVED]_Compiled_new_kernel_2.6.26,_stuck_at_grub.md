---
title: "[SOLVED] Compiled new kernel 2.6.26, stuck at grub menu config"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by fung on 2008-07-25
I want 2.6.26 so the alsa 1.0.17 would compile. Got to the end and now I don't really know how to configure grub to point to the new kernel. 

Here is the first two kernel entries, maybe it will help?

```
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=1869f2b8-039f-4989-9ea2-d27a19cefb94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=1869f2b8-039f-4989-9ea2-d27a19cefb94 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869f2b8-039f-4989-9ea2-d27a19cefb94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869f2b8-039f-4989-9ea2-d27a19cefb94 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
```

Any help would be appreciated!

---

### Post by ibutho on 2008-07-25
You can try the entry below
```
title		Ubuntu 8.04.1, kernel 2.6.26-custom
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26-custom root=UUID=1869f2b8-039f-4989-9ea2-d27a19cefb94 ro quiet splash
initrd		/boot/initrd.img-2.6.26-custom
quiet

```
The entry above assumes that you named your kernel vmlinuz-2.6.26-custom and your initrd image initrd.img-2.6.26-custom.

---

### Post by fung on 2008-07-25
Well, the object of my confusion is that I don't what it is named. I got the kernal straight off the official kernel site but they didn' have the subdivision (the -20 or -19 from my example above).

---

### Post by ibutho on 2008-07-25
If you got the kernel from kernel.org, then you need to compile/build the kernel yourself. The final image file (bzImage) needs to be moved to /boot and you can name it anything you want but most people use "vmlinuz" with the version number.

---

### Post by fung on 2008-07-25
OH so the bzImage is the vmlinuz? Alright I'll try that.

edit
umm would you know in which directory it would be?

edit
nevermind found it

---

### Post by ibutho on 2008-07-25
> **fung said:**
> OH so the bzImage is the vmlinuz? Alright I'll try that.
Remeber that you may need to build an initial ramdisk image (initrd img) for your kernel using mkinitramfs if you have build some things as modules.

---

### Post by gjoellee on 2008-07-25
MANY computer cannot boot kernel 2.6.26-20 so just go to synaptec and uninstall it, and boot with 2.6.26-19

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344)

---

### Post by fung on 2008-07-25
Damn, upon startup, there was some kind of problem accessing /lib/modules/2.6.26. I'll be back with the exact error message in a sec.

> **gjoellee said:**
> MANY computer cannot boot kernel 2.6.26-20 so just go to synaptec and uninstall it, and boot with 2.6.26-19

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344)

I don't even have 2.6.26 installed, is it in the repos? that'd save me a whole lot of hassle.

edit
you were talking about 2.6.24 which I have. I also have -20 and it boots up fine on my laptop.

---

### Post by ibutho on 2008-07-25
Did you do "make modules_install" when you compiled the kernel?

---

### Post by fung on 2008-07-25
Errors:

```
Couldn't open directory /lib/modules/2.6.26: No such file or directory
Fatal: Couldn't open /lib/modules/2.6.26/modules.dep.temp for writing: No such file or directory
Fatal: Couldn't open /lib/modules/2.6.26/modules.dep: No such file or directory
Fatal: Couldn't open /lib/modules/2.6.26/modules.dep: No such file or directory
```

I verified the 2.6.26 directory was there but neither modules.dep.temp nor modules.dep were in there. 

:(

edit:
yeah I did. It took a while too

edit:
Checked to see what was in the 2.6.26 dir and there were two folder links, 'build' and 'source'; a folder called 'kernel'; and a file named 'modules.order'

---

### Post by ibutho on 2008-07-25
Something went wrong somewhere, so try rebuilding the modules by doing "make modules && make modules_install".

---

### Post by fung on 2008-07-25
alright I'll try again.

edit:
oh damn you're right, neglected to do one of those.

---

### Post by fung on 2008-07-25
Weird, I went back into the modules/2.6.26 folder and saw there was new stuff there now. I rebooted and received the exact same errors. Do I need to "make install" the kernel again?

---

### Post by PmDematagoda on 2008-07-25
> **fung said:**
> Weird, I went back into the modules/2.6.26 folder and saw there was new stuff there now. I rebooted and received the exact same errors. Do I need to "make install" the kernel again?

That might work, just remove the old kernel images and files before installing the kernel again though. After installing the kernel image, run:-
```
sudo update-initramfs -k *kernel-version* -c
```
creating the initial RAM disk image is necessary if you want to boot Ubuntu up with the new kernel at all. After that is all done, run:-
```
sudo update-grub
```
and then check your menu.lst file and see if the proper entries have now been added.

---

### Post by fung on 2008-07-25
Can you specify what kinds of files I should get rid of before 'make install'ing again? I removed everything that I did in /boot but don't really know what else is safe to remove.

---

### Post by ibutho on 2008-07-26
That should be enough. You need to copy System.map (name it something like System.map-2.6.26) to /boot as well as the bzImage to /boot (name it something like vmlinuz-2.6.26) and create and initrd image. After that create a grub entry.

---

### Post by fung on 2008-07-26
Awesome, thanks guys, it seems to have worked. Would've been nice to have known about 'update-grub' and 'update-initramfs'. Too bad they don't seem to show up in any documentation :confused:

The 'update-grub' seemed to have added a bunch of other kernels related to I guess my previous failed attempts at installing and those did not work but it's easy to remove those.

Thanks

---

