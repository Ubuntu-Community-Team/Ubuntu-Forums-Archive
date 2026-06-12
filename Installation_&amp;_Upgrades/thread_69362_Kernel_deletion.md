---
title: "Kernel deletion"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by christooss on 2005-09-26
There were several kernel updates in Ubuntu. There were lots of kernels istalled but none of them uninstalled. How can I remove old kernels?

Thanks for the anwser

---

### Post by mlomker on 2005-09-26
They overwrite the same package, just like any other package does.  They can do that by using the same name and increasing the version number--that's how dpkg works its magic.

---

### Post by az on 2005-09-26
No, actually, they are each a different version of the kernel.  If they overwrote each other and you installed a kernel that didn't work for your machine, your box would be unbootable - which is why it works the way it does.

Pick your favorite kernel and uninstall all the other kernel packages in synaptic.  Yes, they are regular packages.

---

### Post by mlomker on 2005-09-26
[QUOTE=azz]No, actually, they are each a different version of the kernel. [/QUOTE]

The Hoary kernel is currently on version 35 and I haven't had to remove the previous 34.  I think, perhaps, that we are thinking about different things.

The original poster, I think, was talking about the regular kernel security updates and not additional kernels.

---

### Post by christooss on 2005-09-27
Nope I was talking about additional kernels. Im using breezy but I didn't know where to post my question.

Thanks azz I will try that

---

### Post by phex on 2005-09-27
go to:
/boot/grub and execute vi menu.lst -> at the end of the file you will see entry blocks with "title, root, kernel, initrd, ...,boot". each block represents another kernel or the same kernel in recovery mode. these kernels will be shown to you at boot up in the boot menu. 
choose the kernel block, which you want to have and delete all othere from the menu.lst file. if you delete the others you must remember their kernel image given under kernel and initrd for example it can look like this:

kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386

now  you can delete these kernel files for this example  /boot/vmlinuz-2.6.10-5-386 and /boot/initrd.img-2.6.10-5-386.

go to:
/usr/src/linux-"version of kernel" or /usr/src/linux-headers-"version of kernel"    -> delete old kernel header directories if installed (look on which directory the symlink linux points if the symbolic link is there -> the linux src kernel directory it points is used for installing new modules, eventually you have to link it to your new kernel src directory you want from now on)
in this example above the directory name looks like this: linux-2.6.10-5-386

/lib/modules/"version of kernel" ->delete old kernel modules
in this example above the directory name looks like this: 2.6.10-5-386

good luck.

---

### Post by mlomker on 2005-09-27
[QUOTE=christooss]Nope I was talking about additional kernels. Im using breezy but I didn't know where to post my question.
[/QUOTE]

Then you should be able to remove them using Synaptic.  The stock ones all start with names of **linux-image** and if you're making custom kernels then you should know the package names that you used (assuming you created .deb's...that's what I always do).

---

