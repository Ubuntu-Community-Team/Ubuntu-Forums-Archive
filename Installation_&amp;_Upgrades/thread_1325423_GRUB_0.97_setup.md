---
title: "GRUB 0.97 setup"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by shoulder12 on 2009-11-13
Hi,
As a new linux user I installed the new Netbook Remix 9.10 on my netbook and try to setup GRUB.
Because the GRUB2 is too confusing to me, I removed it and installed the 0.97 version.

The partitioning of HD is next:

```
Device Boot Start End Blocks Id System
/dev/sda1 1 2550 20482843+ 17 Hidden HPFS/NTFS
/dev/sda2 * 2551 5100 20482875 17 Hidden HPFS/NTFS
/dev/sda3 5101 11990 55343925 7 HPFS/NTFS
/dev/sda4 11991 18813 54805747+ 5 Extended
/dev/sda5 * 11991 18529 52524486 83 Linux
/dev/sda6 18530 18813 2281198+ 82 Linux swap / Solaris
```And my first menu.lst file looks like this:
```
...
title Windows XP Primary
#root (hd0,0)
unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
makeactive
chainloader +1
#
title Windows XP Secondary
#root (hd0,0)
unhide (hd0,1)
hide (hd0,0)
rootnoverify (hd0,1)
makeactive
chainloader +1
#
title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,4)
hide (hd0,0)
hide (hd0,1)
kernel /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet
```Is there any other parameter which is necessary for regular booting and it's not included above, or from other side: is there any parameter which has no function in this situation.

Am I right when I think that
- at win menuitems **root** parameter isn't necessary, but should be used **rootnoverify**
- at win menuitems  should use a **chainloader +1** and **makeactive**
- at linux kernel line **ro quiet splash** parameteres are neseccery
- **quit** parameter in the separated line is not a duplicate of kernel parameter
- no problem if I use root and /dev/sda5 for linux identification instead of **uuid**

Bellow, in the AUTOMAGIC KERNELS LIST section linux automatically generated the next menuitem (+recovery, memtest):
```
title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid 9fdbd396-2318-4c8d-ac85-4fce3b65d337
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=9fdbd396-2318-4c8d-ac85-4fce3b65d337 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
```(sorry for my English, it is not my native language)

Thanks for the help

---

### Post by oldfred on 2009-11-13
Somehow you have two boot flags set (*). You can only have one and Ubuntu does not use the boot flag at all so you can remove that with the partition editior.

I have seen discussion on root vs rootnoverify and the last I saw was that old grub does not read NTFS so it should be a rootnoverify as you just want it to chainload into windows boot.

Makeactive is turning on the boot flag if it is not there, since you can only have one. It is not really doing anything for your second windows but would be required for your first as it is not flagged as bootable.

splash & quiet are to show the Ubuntu screen and not show all the scripts of the loading process. We sometimes ask to turn that off if their are boot issues to see all the messages. That is why the recovery boot stanza does not have splash & quiet. Not sure about ro and the extra quiet but that is how mine is set up.

Using root works just fine as long as you do not do any partition changes. Part of the reason for UUID's was that it is rare that they would change, so users would have less booting issues if if they changed partitions. I did see where someone did a dd full partition backup and then had two partitions with the same UUID and that of course caused issues.

---

### Post by shoulder12 on 2009-11-13
Thank you for your detailed answer...

---

