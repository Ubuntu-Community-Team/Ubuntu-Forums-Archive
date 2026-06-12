---
title: "Cannot remove grub2"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by asuastrophysics on 2010-05-03
Hi everyone,

I can't for the life of me figure out how to remove grub2.
I used the following official ubuntu documentation on uninstalling grub 2:
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)
I then proceeded to remove every last trace of grub2 from my filesystem by using the list of files here:
[http://packages.ubuntu.com/intrepid/i386/grub-pc/filelist](http://packages.ubuntu.com/intrepid/i386/grub-pc/filelist)
(It says i386. I'm running x64, but I dont think it matters)

I dont know what else to do. When I reboot after using CHROOT in a livecd to do the above following, I get, as always:
"GNU GRUB version 1.98-1ubuntu6"
Does anyone have any other suggestions on how to properly remove this monster? I just want to get grub-legacy back. GRUB2 cant boot anything. I get SATA errors and it tells me my EXT3 file system is EXT2....
Does anyone know of a way to remove it?

---

### Post by oldfred on 2010-05-03
The instructions you used should uninstall it.

The reference to ext2 in grub2 refers to any ext2, ext3 or ext4 type partition. They are essentially the same format but use journaling to store recovery info.

What SATA errrors are you getting. That does not sound like a grub error?

---

### Post by asuastrophysics on 2010-05-03
I found out the version of grub-common that is installed along with grub legacy is a new version, 1.98. I was confusing this with grub2.

I am (well, was) getting the following error on boot:
ata4: SATA link down 

But since I removed all of the grub2 files from the filesystem, I can't even get grub to boot anymore :confused:
I get error:file not found
grub rescue> 
I looked up this error message on google and found all sorts of links to GRUB2. This means that somewhere in my filesystem, grub2 still wants to start for some reason, and it won't allow grub-legacy to take over.

---

### Post by oldfred on 2010-05-03
You should be able to boot from a rescue mode. tab often completes a line or partially completes a line.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

** ls **
   
  Run **ls **  to see the devices recognized by GRUB 2. *Example: (hd0) (hd0,1) (hd1,5)*  In this example sda, sda1, sdb5 are recognized.

Express Boot to the Most Recent Kernel
 Command Summary *:
      set root=(hdX,Y)
      linux /boot/vmlinuz root=/dev/sdxY ro
      initrd /boot/initrd
      boot

---

### Post by asuastrophysics on 2010-05-03
Okay, that worked!

Now I can boot but...
more errors, more bugs. (Why so many from an LTS?)

I have two linux kernels installed, on is 2.6.32-22-generic, and the other is 2.6.31-21-generic. 
Both fail to boot my computer. With the first kernel mentioned booted into recovery mode, I dont even get an error message. The trail of text just stops with this:
```
[2.147581] usbhid: v2.6:USB HID core driver
```
The other kernel gives this message: 
```
udevadm: error sending message: connection refused
(screen blanks out, then displays):
init: plymouth main process (60) killed by SEGV signal
```

Ive been trying to fix this for the last 24 hours and I've gotten nowhere :(

---

