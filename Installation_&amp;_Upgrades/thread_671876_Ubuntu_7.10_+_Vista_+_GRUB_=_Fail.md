---
title: "Ubuntu 7.10 + Vista + GRUB = Fail"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by ACLBandit on 2008-01-19
So my Vista partition had been broken for some time, and I hadn't bothered to fix it since I never used it anyway-- nothing it can do that linux can't.

But it finally got to me that it was broken, so I decided to fix it.

Reinstalled the Vista, then reinstalled grub. 

Got it all set up, I can boot in Ubuntu, no problem.

However, when I try to boot Vista, no matter how I change the menu.lst around, I get either a general fail, or, more specifically, a no "BOOTMGR.EXE" message. 

I've tried a number of solutions and howtos, but to no avail.

find /boot/grub/stage1 returns (hd 2,2). 

My menu.lst's useful bits appear as follows::
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a7256e8d-937f-4b64-bf0f-87403128132a ro quiet splash noapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a7256e8d-937f-4b64-bf0f-87403128132a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a7256e8d-937f-4b64-bf0f-87403128132a ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a7256e8d-937f-4b64-bf0f-87403128132a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Business
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Also, fdisk -l returns 
```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48a348a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6402    51422208    7  HPFS/NTFS
/dev/sdb2            6403        6651     2000092+  82  Linux swap / Solaris
/dev/sdb3            6652       19457   102864195   83  Linux

```

I think that's all the necessary information-- I just need someone to tell me how to turn all of that into a working option under my menu.lst to make Vista go. If any more info is necessary, just let me know.

BTW, Ubuntu boots with ease. Windows doesn't.

---

### Post by mikewhatever on 2008-01-19
It looks like you are chainloading from hd1 to hd0, rather then from hd2 to hd0. Have you tried the following:
> title		Windows Vista Business
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by ACLBandit on 2008-01-19
Nope, just tried your solution and got the missing "BOOTMGR.EXE" error.

Another thing that I may not have stated yet is that the computer *did* boot into Vista before I reinstalled grub. 

Thanks for the reply. Got anything else :(?

---

### Post by torgrot on 2008-01-19
Just a guess, but why are you mapping hd0 and hd2, I was under the impression that was for swapping physical hard drives around so windows would boot off another drive that was not the primary boot device.

root (hd0,0)
savedefault
makeactive
chainloader +1

That is all that you should need.

torgrot

---

### Post by mikewhatever on 2008-01-19
Try it without chain loading then:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Business
root		(hd2,0)
savedefault
makeactive
chainloader	+1

Any idea what's up with /dev/sda if there is any?

---

### Post by torgrot on 2008-01-19
Just change the windows entry to this
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Business
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

torgrot

---

### Post by ACLBandit on 2008-01-19
Torgrot, thanks! That did it. I honestly don't know why it was all odd and such-- this exact config worked perfectly before the Vista reinstall. Odd.

Also, thanks a lot Mike, for sticking with me and helping me try different solutions. 

I'm posting this from *shudder* windose... and although I probably will never boot in this OS again, the fact that it isn't broken is what makes me happy.

Thanks guys

---

