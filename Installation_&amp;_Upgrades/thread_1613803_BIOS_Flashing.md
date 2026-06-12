---
title: "BIOS Flashing"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by deamon_knight on 2010-11-04
So, imaging I'm living in a world without access to a windows system. Any Advice on flashing a Motherboard BIOS? Some boards offer a bootable image or a Flashing utility integrated into the BIOS, but Many motherboards don't even offer a disk, they recommend finding a friend with a windows 98 system and making a general purpose DOS boot disk. So, I'm looking for advice on how to deal with this situation. I think I need to get a DOS disk image and I think that I can loopmount and boot a disk image directly with GRUB2.

If this is Correct, I need to locate a DOS boot disk, although I'm leery of downloading disks form the internet. Then I need to figure out how to boot a disk image from GRUB2.


 So how do you guys do it?

Thanks

---

### Post by Frogs Hair on 2010-11-04
My mother board came with a manual and an installation disk , but had to update the bios and used an external floppy drive. There is a bios utility for updates and  I had to navigate to the correct screen before flashing . I happen to pick a board that didn't have bios update software which only works with Windows.

---

### Post by Mark Phelps on 2010-11-05
My ASUS mobo has a builtin EZ-flash function that is invoked by pressing a combination of keys during boot -- at which point it reads the diskette drive looking for the BIOS .bin file.

You would need to Google on your make & model mobo to see if it has the same function.

As to flashing from Ubuntu LiveCD -- don't know how myself, and I certainly would not chance it with MY machine!  One error, and you end up with an electric brick.

---

