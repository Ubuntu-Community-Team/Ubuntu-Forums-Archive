---
title: "URGENT: GRUB Error 17 after deletion of Ubuntu Sector"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by amosharper on 2007-06-04
Hi all,

I desperately need to be able to print tomorrow morning (GMT), so I'd be eternally grateful for a quick answer.

Since I was so happy with Ubuntu on my own desktop, I installed it on the family computer. Since then I've had challenge after challenge, problem after problem so I decided to remove it from the family PC.

I run the Live CD and opened GPartition. I 'deleted' the ext3 sector as well as 'unswapping' and removing the Linux Swap partition and resizing the FAT32 partition to fill the disk.

It threw an error near the end (telling me to look at the details, which told me nothing of a problem) and seemed to work fine anyway. The FAT32 partition remained mounted and I could access it from the Live CD. It may be worth mentioning that I also made a 2.5GB FAT32 partition as well, and copied all important documents to it from the main sector just in case.

I rebooted, and got the following error message:
```
GRUB Loading stage1.5:

GRUB loading, please wait...
Error 17
_
```

What can I do? How can I make Windows work again?

Greatest thanks,

- Amos

---

### Post by aaabbb on 2007-06-04
.

---

### Post by amosharper on 2007-06-04
[COLOR="LemonChiffon"]Was that a bump, or to make me think someone had replied, or...? *[Reference to deleted post]*[/color]

Anyway, at the advice of a friend, I loaded the Windows CD and eneered FIXMBR into the recovery console. It appears to have worked, but it's going through every single file on the disk in chkdsk, saying something about them being 'crosslinked', and 'resolving by copying'.

Will edit with final result.

EDIT: Just for reference, the above worked. For instructions, head to [http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/](http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/).

---

