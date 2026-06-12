---
title: "Newbie needs to get winXP boot back"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by lestrade on 2008-05-03
Sorry, this should be an easy one which I could google, but I need to do this rather quickly. (I have searched but the instructions deal with pre-ubuntu installation, not post.)
I installed 8.04 last night on an unused partition leaving my winXP on its own. Got Broadcom wireless working. Evolution working fine. Just to let you know that I am trying. The main problem is that GRUB does not give me access to my original windows boot. Is this something I can easily fix?  Thanks.
JL

---

### Post by bobnutfield on 2008-05-03
Open a terminal (in Ubuntu) and type:

fdisk -l

and post the output.  This will allow us to see where your windows installation is.  Then you will need to post /etc/boot/grub/menu.lst.  This contains the file that grub uses to boot the operating systems.

We can help from there.

Bob

---

### Post by lestrade on 2008-05-03
Thanks, BnF.
fdisk -l gives no output. nada.
The uncommented lines in menu.lst are:
__________________________
patrick@Featherlight:/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default         0

timeout         3

hiddenmenu

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=ab0d4556-aa37-409f-b8a8-223f31b947f8 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=ab0d4556-aa37-409f-b8a8-223f31b947f8 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2008-05-03
sudo fdisk -l

---

### Post by bobnutfield on 2008-05-03
> title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=ab0d4556-aa37-409f-b8a8-223f31b947f8 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=ab0d4556-aa37-409f-b8a8-223f31b947f8 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

OK, it appears from this that there is no entry in Grub to boot Windows.  When you have posted the output of fdisk -l, we can give an entry to add to boot Windows.  Sorry about forgetting to include "sudo" in my previous post.

Bob

---

### Post by lestrade on 2008-05-03
Thanks for the help:
__________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91769176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        7295    58597056    f  W95 Ext'd (LBA)
/dev/sda5            3649        7295    29294496    b  W95 FAT32
/dev/sda6               1        1216     9767425+  83  Linux
/dev/sda7            1217        3648    19535008+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by lestrade on 2008-05-03
ah, after searching I see what sudo does. As a former windows user I was used to fdisk at the command prompt -- with no formalities. :-)
JP

---

### Post by Pumalite on 2008-05-03
XP uses ntfs. I don't see it.

---

### Post by bobnutfield on 2008-05-03
OK you will need to add the following entry to your menu.lst file:

> # title		Windows XP
 root		(hd0,2)
 makeactive
 chainloader	+1

This is because the information from fdisk -l shows Windows on the second partition of your drive.

You can do this by:

> sudo gedit /boot/grub/menu.lst

This brings up the menu.lst file in a text editor so that you can add this entry.  Make sure you add it AFTER the ######END OF DEBIAN AUTOMATIC KERNELS#######

If you add it before, everytime the kernel is updated through Synaptic it will delete this entry.  Once you have Windows booting correctly, make a back-up of this file so that you can restore it if necessary.  

Hope this helps.

Bob

---

### Post by bobnutfield on 2008-05-03
Sorry, remove the "#" in front of "title" in my previous post.  If you leave it there the title Windows will not be seen in the boot list.

---

### Post by bobnutfield on 2008-05-03
Sorry, rereading (I was rushing around when I posted back earlier), the entry I gave for 

root (hd0,2)  SHOULD read:

root (hd0,1)

Sorry for the first incorrect post.

Bob

---

### Post by bobnutfield on 2008-05-03
Sorry, rereading what I have posted, I have made a typo.  The

root (hd0,2) SHOULD read

root (hd0,1)

Sorry, and I hope you read this before you made the eidt.

Bob

---

### Post by lestrade on 2008-05-03
> **bobnutfield said:**
> Sorry, remove the "#" in front of "title" in my previous post.  If you leave it there the title Windows will not be seen in the boot list.

it is with no small amount of pride that I say I actually figured that one out, by looking at the other "titles" in menu.lst.
However, now it says "No such Partition" when I choose Windows XP from the list..... any ideas?
thanks
JP
ps. I cut and pasted the instructions from your post...so no typo could creep in.

---

### Post by lestrade on 2008-05-03
Never Mind :)!!

---

### Post by bobnutfield on 2008-05-03
Please note my post where I have corrected to root (hd0,1)

Sorry for that.

Bob

---

### Post by bobnutfield on 2008-05-03
OK, hope you got it back OK.

Bob

---

### Post by lestrade on 2008-05-03
Sorry, it takes me a while to shutdown, reboot, etc.
and I apologize for being a pain in the rear, but now the error is:
"Error 12: Invalid device requested."

I take it that the error is somewhere in
hd(zero),1.
??
thanks,
JP

---

### Post by Pumalite on 2008-05-03
That means you are trying to boot Windows from a logical partition. Windows needs a primary partition.

---

### Post by lestrade on 2008-05-03
> **Pumalite said:**
> That means you are trying to boot Windows from a logical partition. Windows needs a primary partition.

That makes sense. So, perhaps, if I boot with windows cd, I can "repair" it?... (I cannot wait to switch away from the dark side -- "go to the light, Carrie Ann"... :)

---

### Post by bobnutfield on 2008-05-03
Sorry, again.  Pumalite is right.  /dev/sda5 is the bootable windows partition.  Change your entry to:

root (hd0,4)

My apologies for the wrong initial information.  I was trying to do too many things at once and I should pay more attention to what I am reading when trying to help.

That partition should boot.

Bob

---

### Post by Pumalite on 2008-05-03
No. You should start from scratch and install XP on sda1. Install Ubuntu last. Let Grub install to MBR and you'll have dual boot.

---

### Post by lestrade on 2008-05-03
thanks, guys, for all the help.
I will get'er done.
JP

---

