---
title: "Adding Win7 to Ubuntu and XP"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by scoob8000 on 2010-06-14
Already have XP on my first partition and Ubuntu following it.

I want to add Windows 7 at the end of the drive and let grub boot to it.

I've done some testing on a spare system, and cannot seem to get grub to boot it directly.  Instead I need to select my XP partition, then use the windows boot manager to select 7 or XP.

I'm guessing 7 installs it's boot manager to the first partition, and not the one I installed it to...

---

### Post by ronnielsen1 on 2010-06-14
Probably the easiest way would be to install it and let UBCD configure it. It's always worked for me and easier to understand than grub2
>         [SIZE=2][SIZE=2][COLOR=#ee0000]***       Ultimate Boot CD is completely free for the download, or could be  obtained for a small fee. If you had somehow paid a ridiculous amount of  money for it, you have most likely been fleeced. The least you could do  is to make as many copies of the offical UBCD and pass it to your  friends, relatives, colleagues or even complete strangers to minimize  the per unit cost of your loss!***[/COLOR][/SIZE][/SIZE]

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by darkod on 2010-06-14
This has nothing to do with understanding grub2. It is how windows combines the boot files if two versions are installed.

Boot your ubuntu, open Gparted and create the ntfs partition for win7 on the disk where you want it. Make sure it's primary partition, not logical. If you already have 4 partition that might not be possible.

After you create the partition, use Gparted and remove the boot flag from the XP partition, put it on the win7 partition. Windows puts the boot files where the boot flag is and that is the way to keep two versions of windows with separate boot files.

Then boot with the win7 dvd and when asked where to install just select the prepared partition.

After that is done you will have to reinstall grub2 back to the MBR of the disk. The first time you boot in ubuntu win7 is still not in the boot menu, don't be surprised. Once you have booted ubuntu, just run:

sudo update-grub

to detect it. After that you should have a boot menu with all three OSs.

PS. If you already tried installing without the move flag procedure you might already have combined boot files on the XP partition, prompting you to select windows from windows bootloader. You might consider restoring the original XP boot files before restoring grub2, otherwise it's pointless to have the win7 boot files on its partition. Don't forget, windows depends on the boot flag, so before restoring XP boot files, use Gparted and return the flag to the XP partition.

---

### Post by scoob8000 on 2010-06-14
Darkod,

That worked a treat!  I went a step further and hid my XP partition before installing 7 just to play it safe, then added the hide and unhide commands to my menu.lst.

Thank you!

---

### Post by darkod on 2010-06-14
> **scoob8000 said:**
> Darkod,

That worked a treat!  I went a step further and hid my XP partition before installing 7 just to play it safe, then added the hide and unhide commands to my menu.lst.

Thank you!

You're welcome. Enjoy it now. :)

---

