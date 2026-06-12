---
title: "Vista won't boot even in safe mode, after 9.10 upgrade"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by ubg on 2009-11-23
Hello, I'm trying to help a friend. She did the automatic upgrade to 9.10, and everything seemed to go fine. But, after the upgrade, Vista won't boot.

She chooses Vista in GRUB, but then during the boot-up, Vista reports that something went wrong and that she should try to boot in safe mode. But when she tries that, the computer just restarts, and the process repeats.

She can boot fine into Ubuntu.

I'm not sure if this is related to upgrade, but Vista booted-up well before the upgrade, and she can't remember she did anything other worth mentioning.

I think I had some similar problem during the installation of Ubuntu and Vista on her computer in the first place, but I can't actually remember how I solved it.

Here are the GRUB entries:

```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        acaa8c0c-751f-487f-b052-1d7fc68e7dbb
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=acaa8c0c-751f-487f-b052-1d7fc68e7dbb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        acaa8c0c-751f-487f-b052-1d7fc68e7dbb
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=acaa8c0c-751f-487f-b052-1d7fc68e7dbb ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        acaa8c0c-751f-487f-b052-1d7fc68e7dbb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```/etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=acaa8c0c-751f-487f-b052-1d7fc68e7dbb / ext3 relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=e3b9737a-94ba-432a-8367-5b885cd2d6b2 /home ext3 relatime        0       2
# /windows was on /dev/sda1 during installation
UUID=EA6A7C286A7BF025 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
UUID=3ef51a03-9873-4fdb-bdcb-a7f999364bd0 none swap    sw           0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Output of `fdisk -l`:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22040   177036268+   7  HPFS/NTFS
/dev/sda2           22041       22171     1052257+  82  Linux swap / Solaris
/dev/sda3           28476       30402    15471800   12  Compaq diagnostics
/dev/sda4           22172       28475    50636880    5  Extended
/dev/sda5           22172       24721    20482843+  83  Linux
/dev/sda6           24722       28475    30153973+  83  Linux

Partition table entries are not in disk order
```If you need any more info, please ask. Thanks for your help.

---

### Post by phillw on 2009-11-23
Resetting GRUB and windows MBR's is covered here. if you're on 9.10, then you're on Grub2

If it was an upgrade, chances are you're on Grub1

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Rregards,

Phill.

---

### Post by ubg on 2009-11-23
phillw, thanks for the reply. I noticed that thread, but I wasn't sure what to do. I don't have physical access to her computer (she's not living in the same city at the moment), so I would like if you could give me a second opinion. Should I tell her to try and reset Vista bootloader, and then to reset GRUB?

---

### Post by phillw on 2009-11-23
> **ubg said:**
> phillw, thanks for the reply. I noticed that thread, but I wasn't sure what to do. I don't have physical access to her computer (she's not living in the same city at the moment), so I would like if you could give me a second opinion. Should I tell her to try and reset Vista bootloader, and then to reset GRUB?

Best I can do (and have done) is have the instructions on the screen in front of you and 'talk' them through it.

IM is a bit easier, but, doing it slowly & keeping the other person calm at the other end of the phone is do-able. (Removing viruses & malware from windows machines taught me well about using the phone)

Try to leave out negative comments whilst on the phone (e.g -- YOU DID WHAT?!!!!) Listen to what they say, track it thru' the instructions. If something occurs that is not in the 'script' - stay calm, take a note of it, tell the OP you're going to do a quick check. Have your panic attack, post the question, get an answer and go back to the OP in a calm manner. Humans are very unpredictable when scared / worried / stressed - keep them calm.  

The instructions DO work, just  talk her through them, quietly and calmly and all will be well.

Regards,

Phill.

---

### Post by ubg on 2009-11-23
Thanks again :). Social part of the problem should be fine. I would like to know if you think that "reset Vista bootloader, then reset GRUB" sounds like a good plan?

---

### Post by phillw on 2009-11-23
> **ubg said:**
> Thanks again :). Social part of the problem should be fine. I would like to know if you think that "reset Vista bootloader, then reset GRUB" sounds like a good plan?


That is something I cannot decide upon, it is not my call to make. I can only offer my opinion. As Vista is complaining, I'd hand control back over to Vista & let it get itself happy. Once Vista is happy I'd then tell Grub to take over. M$ seems happier with M$ stuff. The ubuntu area is 'out of bounds' to vista unless you do a full re-install of vista and will sit there patiently while you sort Vista out.

But, that is just the way I would do it. 

Hope that helps,

Phill

P.S. - So, it sounds like the same plan ....

---

### Post by ubg on 2009-11-23
> **phillw said:**
> P.S. - So, it sounds like the same plan ....

OK, I'll give that a try, hopefully everything will be OK :). Thanks again.

---

