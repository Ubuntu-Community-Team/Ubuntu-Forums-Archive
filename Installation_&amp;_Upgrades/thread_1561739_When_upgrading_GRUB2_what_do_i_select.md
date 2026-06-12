---
title: "When upgrading GRUB2 what do i select?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by samn122 on 2010-08-26
Im currently upgrading from ubuntu 9.1 to 10.4. During upgrading a window comes out saying "Grub install devices" I have a dual boot of Ubuntu and vista on 2 seperate drives. Where do I install Grub2? It gives me 2 options of installing to the drive which has Ubuntu or to the drive which has Vista. Which one do i pick or do i select all? I really cant do anything as im am currently stuck on a stage of updating.

---

### Post by samn122 on 2010-08-26
*bump* kind of in a hurry to get things moving along so sorry if i'm being pushy.:D:D:D:D:D:D:D

---

### Post by samn122 on 2010-08-26
*bump* kind of in a hurry to get things moving along so sorry if i'm being pushy.:grin::grin::grin::grin::grin::grin::grin:
Im stuck on a stage of updating and I tried to search for a soulution myself with no avail.

---

### Post by samn122 on 2010-08-26
refreshing over 9000 times!!!!!!!!!!!!BLARRRGGG

---

### Post by Herman on 2010-08-26
Normally, it is best to write the GRUB code to MBR in whichever the BIOS thinks will be the first hard drive, but a few people like adding and removing drives from their computer frequently, so that is why it might be better to write GRUB to all drives.

If you're not sure you can safely select all (or both) drives to write GRUB to since this  only means writing a little code in the first 446 bytes of the MBR of  either/both of the drive(s).

The MBR is not part of any other operating system's partition, and GRUB will not cover up the drive's Unique ID number necessary for Windows Vista and 7 to boot.

If you remove the Ubuntu drive at some stage in the future to put in some other computer and you have GRUB in the MBR of the Windows drive you will need either install GRUB in Windows or somewhere else in the same drive or else write the Windows boot loader's MBR code to MBR in that drive. It's not difficult.

---

### Post by samn122 on 2010-08-26
THANKS A BUNCH!  Ill try installing it to bot of the drives now and tell you how it goes.

---

