---
title: "error 15: file not found"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by dylanologist on 2008-07-11
Hi all,

I recently upgraded from Gutsy to Hardy (64-bit) using the Update Manager, and whenever I would boot I would get the message:

Error 15: file not found
Press any key to continue...

If I pressed a key I would get the GRUB menu, in which case I could select a different kernel and it would boot up fine.  In other words, the new kernel (2.6.24-19) doesn't work, but the old kernel (2.6.22-15) does work.  The working kernel is the same one I was using in Gutsy, but it works for the Hardy upgrade as well.

I've adjusted the GRUB menu to boot into the working kernel by default, so I'm having no problem using the upgraded OS, but I assume there are probably advantages to using the newer kernel, so I would like to try to fix the problem.  I tested Hardy on a separate partition with a fresh install from a CD and didn't have any problem with the new kernel, so I assume something went wrong during the upgrade process.

Any help is appreciated.

EDIT:  I tried reinstalling GRUB at one point, which had no effect.  I've also tried <sudo apt-get update> and <sudo apt-get upgrade>, again to no effect.  I really don't know anything about kernels, so that's all I've tried so far.

---

### Post by Pumalite on 2008-07-11
Get Super Grub and correct your system:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Error 15:
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by CraigWatson on 2008-07-11
At what stage in GRUB is the file not found error appearing?

I have had very similar problems with a fresh install of 8.04.1 ([topic here](http://ubuntuforums.org/showthread.php?t=856079)), the vmlinuz file loads fine, but the 2.6.24-19 kernel's initrd.img file isn't present.

If GRUB is chucking the Error 15 when it tries to find that file, then it could possibly be the same problem and indicate a wider Ubuntu issue rather than just an isolated one.

---

### Post by dylanologist on 2008-07-11
Pumalite,

I tried the two possible suggestions posted on this link:

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

to no avail.  Also, I don't think I require SuperGRUB in this case because I am able to boot into Hardy using the old kernel.  If I'm not mistaken, I would only need to use SuperGRUB if I couldn't boot up at all.


CraigWatson,

I'm not sure how to determine at what stage in GRUB the error happens.  It seems to me to happen immediately.  I don't get the <GRUB loading stage 1.5> message that I get with a successful boot.  However, I'm not 100% sure about that because now I've got GRUB set up to boot the old kernel, so it works normally, and to try to boot the new kernel I have to press ESC and select it manually.

Is there a GRUB log file somewhere that will tell me at what point it is encountering the error?

---

### Post by meindian523 on 2008-07-11
Error 15 means it cannot find the file.Check your menu.lst to be sure that the path to the kernel and init which doesn't boot is indeed correct.

---

### Post by CraigWatson on 2008-07-11
Can you post the menu.lst file for your GRUB installation? It would be interesting if the kernel that's failing is 2.6.24-19.

If your install is failing at the same point mine is, you should see "kernel /vmlinuz ...... etc etc" then a line of information about the kernel file, then another line like "initrd /initrd.img" - and then the Error 15 line.

---

### Post by dylanologist on 2008-07-11
Here is, I believe, the relevant portion of /boot/grub/menu.lst:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2a9da4f8-9520-4b94-897b-b7cebe2672ed ro single
initrd		/boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST


I placed the old kernel (2.6.22-15) above the new one (2.6.24-19) because it still works, so it now loads by default. I checked the content of the vmlinuz and initrd.img lines, and everything appears to me to be fine.  Is it possible that the UUID's could be listed wrong, and if so, how can I check that?

The 7.10 install is on another partition, and it still seems to work fine.

As for the error, when I try to boot from the new kernel I simply get a black screen with the only writing being:

Error 15: file not found
Press any key to continue ...

No info whatsoever about the kernel or the stage at which it is failing.


EDIT:  Here is the content of <ls -1 /boot>:

abi-2.6.22-15-generic
abi-2.6.24-19-generic
config-2.6.22-15-generic
config-2.6.24-19-generic
grub
initrd.img-2.6.22-15-generic
initrd.img-2.6.22-15-generic.bak
initrd.img-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak
memtest86+.bin
System.map-2.6.22-15-generic
System.map-2.6.24-19-generic
vmlinuz-2.6.22-15-generic
vmlinuz-2.6.24-19-generic

---

### Post by Pumalite on 2008-07-11
Check:
sudo blkid
Against:
/etc/fstab
And:
/boot/grub/menu.lst

---

### Post by dylanologist on 2008-07-12
I took a quick look at the output of <blkid> and it seems to correspond to the UUIDs in the other two files.  I didn't have time to go through carefully, character by character, so I'll double check on Monday when I get a chance.  However, I don't think that that is the problem.

I can reinstall GRUB using <sudo grub>, but I assume that has nothing directly to do with the boot files.  Is there a way to, say, reinstall the /boot directory without doing a full system reinstall.  I have things tweaked nicely, and I really don't want to reinstall from scratch, especially since the old kernel is still working fine.

---

### Post by dylanologist on 2008-07-22
So I moved /home to a separate partition and installed Hardy from scratch on a different partition. I started using the new install of Hardy and found that other problems I was having were fixed (3D graphics, flash), so I continued to use it.

I just realized, however, that a fresh install of Hardy on a different partition seems to have repaired my previous upgrade on the old partition. I guess it must have had something to do with the MBR or grub menu, because I can't imagine why else this solution would've worked.

Anyway, I'm happy with the fresh install, so I'm going to continue with that and save the old partition for testing other Linux distros.

---

### Post by Pumalite on 2008-07-22
Congrats!

---

### Post by mosorensen on 2008-07-24
I am N00b, so take this with a grain of salt. But I also came across the Grub "Error 15", albeit I think for a slightly different reason, so I just want to post my experience here. 

I run Ubuntu 8.04 64 bit with two hard disks. For some obscure reason, I ended up booting from /dev/sdb (#1) and using /dev/sda (#0) for my /home directory, but everything worked fine. For other obscure reasons, I did a reset of my BIOS to its default settings, and this caused my Grub to fail with the dreaded "Error 15." 

I think what happened was that the boot order of the HDs was reset in the BIOS, so it was first trying to boot off the wrong HD and this caused the problem. I could probably have fixed it by changing the boot order in the BIOS, but instead I just flipped the two SATA cables on the motherboard, effectively changing the order of the harddisks. That solved it, and everything works wonderfully now. 

Note, for this two work, your /etc/fstab file should refer to your drives by "UUID = xxxxxxxx" instead of /dev/sda1 or /dev/sdb1, or you have to update this file as well.

I hope this helps,
MS

---

