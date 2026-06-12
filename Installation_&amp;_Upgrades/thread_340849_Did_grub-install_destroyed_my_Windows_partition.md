---
title: "Did grub-install destroyed my Windows partition?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by rlgc79 on 2007-01-17
Hello, Here is the problem

I have a dual-boot system (Ubuntu 32 bits and Windows XP). I also have an additional partition to play with different distributions. Yesterday, I installed Ubuntu AMD64 in this partion, which, of course, replace my Ubuntu X32 grub.

Ubuntu 32 bits is  my primary desktop, so I went through the conventional procedure to recover my original grub in Ubuntu AMD64:

$ mkdir /mnt/tmp
$ mount /dev/sda4 /mnt/tmp   <=== My Ubuntu 32 partition

HOWEVER, in the last command, by accident, I wrote

$ grub-install /dev/sda1 --root-directory=/mnt/tmp  <== Do not try this

(the right command should be: grub-install /dev/sda --root-directory=/mnt/tmp)

/dev/sda1 is my Windows XP partition, which does not want to boot anymore. Additionally, even gparted cannot recognize this partition anymore. Mounting sda1 won't work, either. The question is: Is it possible to recover my Windows partition?? I have millions of pictures there...

Best,
rlgc79

---

### Post by lotacus on 2007-01-17
First of all, your topic is mis-leading. Ubuntu did not do anyting you didn't ask it to do. So you are the one that screwed it up. Your just blaming Ubuntu to save face. Unless of course, you meant the actual command destroying your partition, then that's a little different.

from what you wrote, all I can see is that you wrote the boot loader to your windows XP partition, which would have it's own bootloader. So you pretty much effectively over-wrote your windows XP boot sector.

Your Windows XP partition isn't screwed up. Only the bootsector. You can fix this by running your windows XP installation from the cdrom and choose recovery mode (or something similar) It should take you to a command prompt, from there you can enter the command fixmbr followed by what drive the boot sector is located on. and you *should* be all set to go.

example:

>: fixmbr c:  (it may look sometihng like this. You can always do fixmbr /?)

There *may* be a chance that this will replace your grub boot loader. If that is the case, then you can just repeat the Ubuntu steps correctly.

---

### Post by Sef on 2007-01-17
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by rlgc79 on 2007-01-17
Dear locatus and sef,

Thank you for you help, I managed to recover my Windows partition. The solution was not exactly the one you showed, but it was similar.
Here it is:
1) Use the Windows installation CD to enter in the recovery mode.
2) Type:
$ fixmbr
$ fixboot c:
3) Recover the MBR and grub following the right steps i posted earlier.

(If you only try to recover the MBR/Grub, it won't work. )

Some final thoughts:
1) Why doesn't grub-install give a warning telling that you are trying to mess up a NTFS partition (proprietary, doesn't play well with OSS) ?
2) luckily, it happened to my Desktop, which came with an OEM version of Windows. The Windows "installation" disk of one of my laptops is actually a Norton ghost image! Therefore, if the same problem happens, no recovery mode!

Best,
rlgc79

Ps.: When did I blame Ubuntu for destroying my Windows partition? My title of my topic doesn't even mention Ubuntu at all.

---

