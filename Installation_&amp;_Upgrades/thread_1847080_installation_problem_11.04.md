---
title: "installation problem 11.04"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by richard_the_second on 2011-09-20
hi lads.
i have a laptop toshiba x500 102.
the processor is a i7 2630.
i have downloaded ubuntu 11.04,put it on a cd with nero.
i changed the boot sequence in the bios but  the computer doesn't boot on the cd.
it keeps on booting on windows 7.
a few years ago,when i was engraving a cd ,nero was asking me if it was a bootable cd or not.and here i can't find any "bootable cd" option.

:mad:
thank you if you can help.

---

### Post by Elfy on 2011-09-20
Assuming that the bios is set to boot the cd I'd say it's not burnt as an iso, not used nero for a long time.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If you didn't use a torrent to get the iso then make sure you check the md5sum before you do burn it

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Mark Phelps on 2011-09-20
If you used the Nero option to create a bootable CD -- that won't work because it will add MS Windows boot files and then copy the ISO file to the CD.  This is not what you want.

To do this in Nero, you want to use the option to burn an Image file.  Then, find the .ISO file and select that.  Nero will then burn a bootable CD, but this time, it will boot into Ubuntu.

---

### Post by Elfy on 2011-09-20
> **Mark Phelps said:**
> If you used the Nero option to create a bootable CD -- that won't work because it will add MS Windows boot files and then copy the ISO file to the CD.  This is not what you want.

Thanks for that - I'll remember that next time.

---

### Post by richard_the_second on 2011-09-23
thank you for that.
my computer is not available at the moment so i will try it very soon.

---

