---
title: "Help - updated but it hasn't taken effect"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by gargoyle60 on 2010-01-06
I have updated using the Update Manager but when prompted to modify menu.lst I answered "leave as is" (or the equivalent) and now when I boot I notice that the update hasn't taken effect, or at least grub isn't offering it to me. Unfortunately I didn't make a note of the update details. The update was quite large, circa 100MB+.

Currently running 9.04, Kernel Linux 2.6.28-16-generic.
Not sure what the latest update is, or how to find out?

Please advise?
Thanks

---

### Post by tachuela on 2010-01-06
Edit menu.lst and add the new kernel at the beginning of the list (you'll find it in /boot)

---

### Post by slakkie on 2010-01-06
Or run sudo update-grub or grub-update (it's one of the two, i always forget which one it is).

---

### Post by gargoyle60 on 2010-01-06
Okay, I ran sudo update-grub and got the following...
   Searching for GRUB installation directory ... found: /boot/grub
   Searching for default file ... found: /boot/grub/default
   Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
   Searching for splash image ... none found, skipping ...
   Found kernel: /boot/vmlinuz-2.6.28-17-generic
   Found kernel: /boot/vmlinuz-2.6.28-16-generic
   Found kernel: /boot/vmlinuz-2.6.28-15-generic
   Found kernel: /boot/vmlinuz-2.6.28-11-generic
   Found kernel: /boot/memtest86+.bin
   Updating /boot/grub/menu.lst ... done

but note the line that says "Searching for splash image ... none found, skipping ..."
Is that something I should be concerned about?
The procedure also did NOT update the menu.lst file with the latest details (although I have manually edited the file since then, and I hope I've got it right).

I had a look in /boot and found these...
-rw-r--r-- 1 root root 3491600 2009-12-01 21:04 /boot/vmlinuz-2.6.28-17-generic
-rw-r--r-- 1 root root 7547531 2010-01-06 16:59 /boot/initrd.img-2.6.28-17-generic

Note the timestamp for the file vmlinuz-2.6.28-17-generic, which is 2009. 
Is that correct?

---

### Post by oldos2er on 2010-01-06
If you use grub legacy, which I assume you do since you're running 9.04, update-grub won't actually update your menu.lst. You'll need to run ```
gksu gedit /boot/grub/menu.lst
``` and manually add an entry for the new kernel, as you said.

---

### Post by gargoyle60 on 2010-01-07
Yes, I've done that manually.

Now, when I boot I get the message
"Error 13: invalid or unsupported executable format"
or something along those lines.

All I did was copy the older entries and modify them with the new file names.

My new grub menu.lst entries are as follows:
--- start of code ---

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/initrd.img-2.6.28-17-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        43c5762f-33b6-4369-86c4-3f5a122c2992
kernel        /boot/memtest86+.bin
quiet

--- end of code ---

I have no idea about the other options, but the seem to be the same, I think?

---

### Post by oldos2er on 2010-01-07
Can you run **sudo fdisk -l** and post the output here? If you can't boot an older kernel, you can boot from a LiveCD if you have one, and run the command there.

---

### Post by gargoyle60 on 2010-01-08
Thanks Ann

I have renistated the previous menu.lst and I can boot from an older kernel.

Output from  **sudo fdisk -l**
--- output start ---
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x116a1169

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4632    37206508+   7  HPFS/NTFS
/dev/sda2            4633        9733    40973782+   f  W95 Ext'd (LBA)
/dev/sda5            4633        7182    20482843+  83  Linux
/dev/sda6            7183        9733    20490876   83  Linux

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a911a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         594     4771273+   7  HPFS/NTFS
/dev/sdb2             595        9733    73409017+   f  W95 Ext'd (LBA)
/dev/sdb5             595        1116     4192933+  82  Linux swap / Solaris
/dev/sdb6            1117        6338    41945683+   7  HPFS/NTFS
/dev/sdb7            6339        9733    27270306   83  Linux
--- output end ---

My other op sys is Win XP Home.

Gary

---

### Post by llawwehttam on 2010-01-08
Personally *( after a lot of experience) *I now go by the 'if it ain't broke don't fix it' approach.

---

### Post by oldos2er on 2010-01-09
I must have vision problems that I didn't see this sooner:

title Ubuntu 9.04, kernel 2.6.28-17-generic
uuid 43c5762f-33b6-4369-86c4-3f5a122c2992
kernel /boot/**initrd.img**-2.6.28-17-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro quiet splash
initrd /boot/initrd.img-2.6.28-17-generic
quiet

should be 

title Ubuntu 9.04, kernel 2.6.28-17-generic
uuid 43c5762f-33b6-4369-86c4-3f5a122c2992
kernel /boot/**vmlinuz**-2.6.28-17-generic root=UUID=43c5762f-33b6-4369-86c4-3f5a122c2992 ro quiet splash
initrd /boot/initrd.img-2.6.28-17-generic
quiet

Note the bolded part. Hope this helps.

---

### Post by gargoyle60 on 2010-01-10
I hadn't spotted it either. Thanks Ann.
Gary

---

