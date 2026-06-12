---
title: "Re installing Boot manager"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by CCOS on 2006-12-09
After testing Unbuntu I'm  using it as my primery OS now, but..
I got my Windos on another disk and pluging and unpluging power cables acording to witch OS I going to use.

My quistion is. Can I install a boot manager so I don't have to mess around with cables with out having to reinstall my ubuntu? 


CCOS

---

### Post by bscbrit on 2006-12-09
Yes you can.  Make the Ubuntu drive the Master and the Windows drive the Slave.  Modify 'grub' on your Ubuntu disk to include and entry for the Windows drive and then, at boot time, you can select which one you want.

For example, I will assume that your ubuntu is on hd0 on the first partition, and Windows is on hd1, also on the first partition.  The entries in '/boot/grub/menu.lst' will look something like this:

```

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

title           Windows Wonderful OS
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```


You will have to modify the entries to match your chosen hard drives and partitions, and there will be additional entries in your /boot/grub/menu.lst to allow you to start in recovery mode, complete a memory check, decide which boot will be default and perhaps a few other options.  

Remember!

1. If you edit /boot/grub/menu.lst and corrupt the file you might lose the ability to boot your machine at all.  Do not be frightened of editing, but take care to type exactly what you need and then check, check and check it again.

2.  The contents of your /boot/grub/menu.lst will NOT be exactly the same as the entries above.  It will depend on how your computer is configured.


If you are still not sure, paste the contents of your /boot/grub/menu.lst here and I or someone else can show you exactly what to type.

---

### Post by bernied on 2006-12-09
You probably already have the 'grub' (GRand Unified Bootloader) boot manager installed on the Ubuntu disk. You can use this to manage dual booting. Look for the file /boot/grub/menu.lst - it is the configuration file for grub.

Windows generally likes to be on the first (bios) disk, so what people usually do when they have multiple disks is to install linux on the second (or third, or etc) disk. Since you already have ubuntu installed on, according to ubuntu, the first disk, this may not be best for you. There is a way you can multiboot without changing either of your installations very much - something like this:

- before you start, make sure you have a live cd that will give you internet access in case something doesn't go to plan
- check you have a /boot/grub/menu.lst file. If not, stop now, you have a different bootloader.
- backup your menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.working
```(if things go wrong, repeat that command with the two file names reversed)
- open your menu.lst file for editing:
```
sudo nano /boot/grub/menu.lst
```- then add the following text, just before the automagic section:
```
title Windows
map (hd1) (hd0)
map (hd0) (hd1)
rootnoverify (hd1,0)
chainloader +1
boot

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```
- shutdown
- configure cables/jumpers so that the ubuntu disk is master and windows disk is slave
- see if it works

---

### Post by bernied on 2006-12-09
Well, it's not really a waste to have two people give the same answer to a question. See that I suggest using the map command in grub - this fools windows into thinking that it is booting from the first disk. The makeactive command (as far as I know) changes the 'bootable' status on a partition - this should not be necessary as the bootable flag should already be set on that windows partition. I'd be curious to know whether the solution of bscbrit works.

---

### Post by bscbrit on 2006-12-09
bernied - it works on one of my machines.  The hd0 is all ext3 or swap and Windows does not even recognise its existence.  I agree the 'makeactive' needn't be there but I cut and pasted and did not edit it out.  Alternatively, you could edit boot.ini on the windows disk for a similar effect, I think - but I've never done this so I am not 100% sure that MS software will behave. :-D

Secondly, I agree that Windows always wants to _install_ to the first disk, but once on a partition I've never had any problems with it booting.

---

### Post by bernied on 2006-12-09
thanks for the education - there's always more than one way

---

### Post by CCOS on 2006-12-09
Thx. I'll try and see my win install I don't care have to reinstall it any way ( to much **** on that anyway)

CCOS

---

