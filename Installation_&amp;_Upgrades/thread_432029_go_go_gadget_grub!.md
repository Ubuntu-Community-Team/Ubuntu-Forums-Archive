---
title: "go go gadget grub!"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Ben325e on 2007-05-03
Hey folks,

I was running xp and got a free hard drive from a buddy, so I popped it in my machine and decided to learn linux.  I had edgy eft on the new drive, and xp on the original, with the free drive being booted to (with grub on the free drive).  Since the fonts looked less than adequate on my open office stuff and online, I thought that the upgrade to feisty would be a good idea.  I did the upgrade as per ubuntu's website, but it redid my grub menu.lst.  My current grub is posted at the bottom.  It changed my root to (hd1,1), and my windows is gone, and I also can't boot into any OS from grub.  
P.S.  I have an HP pavillion computer, and HP puts the "restore" stuff on a small D: partition on my windows drive, and I remember that had something to do with how I set up my grub, but  I don't remember what.  I was reassured that the upgrade wouldn't mess with my grub, so I didn't write it down.  
Any idea's of how to fix would be greatly appreciated!

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=380f38df-81fe-420d-af16-db6581771f16 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Ben325e on 2007-05-03
I forgot to mention that I can only see this from the live cd, which isn't too good because I only know how to view the file in read only.  I don't know how to actually edit and save it.

---

### Post by Jazztux on 2007-05-03
Hi, 
ok let's start from the beginning. Open a terminal (gnome-terminal in GNOME, konsole in KDE) and type:

```
fdisk -l
```

And post here your output.

---

### Post by bulldog on 2007-05-03
> **Ben325e said:**
> I forgot to mention that I can only see this from the live cd, which isn't too good because I only know how to view the file in read only.  I don't know how to actually edit and save it.

If I understand you correct,your ubuntu is on the master boot device with the GRUB installed to the same hdd.
Your windows is on the 'slave' device with no GRUB in the MBR.
If this is correct,your menu.lst points to the wrong hdd .
You have to edit the menu.lst to correct this,and add an entry for your windows.

When you see the GRUB menu,hit the 'e' key,this aloud you to change the boot line.
Make (hd1,1) (hd0,1) hit the 'b' key and see if it will boot.

---

### Post by Ben325e on 2007-05-04
Hey Bulldog, you're exactly right with what you said.  I tried to switch back to hd0,1 , but that didn't work, and I also tried it for other versions.  
Using fdisk or any of it's variants to list all the partitions was futile because i was running from the live cd.  I think I'll just reformat and start again from the beginning.  Thanks for your help, though!

---

