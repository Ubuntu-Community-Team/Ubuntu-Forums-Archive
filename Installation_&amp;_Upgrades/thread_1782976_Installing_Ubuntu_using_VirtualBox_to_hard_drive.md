---
title: "Installing Ubuntu using VirtualBox to hard drive"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by roses100 on 2011-06-15
Hi,

I need to install a fresh copy to Ubuntu to hard disk, but would like to do it through VirtualBox so that I can still be working while it's running in the background. This is the first time I've done it this way, as conventional methods always leave me with the 'errno 5' error. Can anyone give me some advice/tips on how to go about doing this?

I generally keep two copies of Ubuntu anyway, current and previous versions, I already have spare root and home partitions to use.

Thanks!

---

### Post by l_o_s_b on 2011-06-15
Are you trying to install Ubuntu in Virtual Box? Or are you planning to install Ubuntu on your physical machine while working in Virtual Box? 

If you want to install it on the physical machine there is no way to use Virtual Box from the same computer as Virtual Box is a program that is installed in your operating system. And you will need to install the OS before installing a program.

---

### Post by roses100 on 2011-06-15
I was hoping to install Ubuntu to real partitions using a fresh machine in Virtualbox and then sorting out the grub menu later.

I have 4 partitions, 2 of which are used as my current OS, I have 2 other partitions dedicated to a previous version of Ubuntu which I have kept as a back up, but was hoping to use these spare partitions for the fresh install using VirtualBox.

It's because previously almost every time I install Ubuntu I get the 'errno 5' error and have to start the process again, and this could take several attempts before I can successfully install. This can potentially take up to whole day where I need a working PC.

---

### Post by mortuk on 2011-06-15
I think roses is trying to say she wants to install a guest of ubuntu, but instead of onto a virtual disk she wants to use a physical disk.

I wouldnt mind knowing how to do this as well.

In the virtual box manual it explains how to use [raw host hard disks]("http://www.virtualbox.org/manual/ch09.html#rawdisk") however when I try this, I get to create the VMDK file ok, but when I try and add it to a virtualbox machine it tells me:

```
Failed to open the hard disk /home/chris/.VirtualBox/HardDisks/sda5.vmdk.
Could not open the medium '/home/chris/.VirtualBox/HardDisks/sda5.vmdk'.
VD: error VERR_ACCESS_DENIED opening image file '/home/chris/.VirtualBox/HardDisks/sda5.vmdk' (VERR_ACCESS_DENIED).
```

I have chown and chmod'd the files but it still gives me issues

Any ideas?

---

### Post by roses100 on 2011-06-15
I've managed to create a .vmdk file which points to my two partitions, run VirtualBox as root and attached the vmdk to the virtual disk manager and boot it off that. 

But now when it boots up the old partitions it gives this error:

```

error: unknown filesystem.
grub rescue>

```Is there a way to bypass the grub so I can get to the OS/Ubuntu thats installed on the partitions?

---

### Post by roses100 on 2011-06-17
I have managed to do a fresh install to raw partitions using VirtualBox, and have got it to boot up fine within the Virtual machine. But now I would also like to boot the new install natively from the grub menu on the host machine too.

When I boot up my machine, it can't seem to find the new install or recognise that there is a new copy Ubuntu on the other partition. Is there a way in which I can update or reconfigure the grub menu / boot loader on my current / host to see the new install on the other partitions?

---

### Post by roses100 on 2011-06-17
Had to do

```
sudo update-grub
```

---

