---
title: "Uninstalled Ubuntu, problems with Grub"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by Bios___ on 2006-06-17
As the name suggests.

Basically, I have 2 physical Hard Drives, one of which has Xp Pro on it, I was reffered to Ubuntu, so i installed that on the second drive. 

Tested ubuntu, thought well of it, and am deciding to put it on a seperate machine as having to choose which OS to load each time can be a pain.

I have removed Ubuntu from my second drive via a format, and now I get a Grub error at startup and it doesnt load Xp at all.

I dont have an Xp Recovery Disc, I have attempted to use the FDISK/MBR commands and they haven't gone too well for me. I caught glimpse of a post explaining that there is a way to remove the Grub loader using the Ubuntu Live CD's, but I lost it and feel like a plank.

Any and all help would be greatly appreciated. ;) 

Thank you.

Also I apologise if this post is in the wrong section. Sorry.

---

### Post by zxee on 2006-06-17
in dos the command is fdisk /mbr (all lower case and a space after the fdisk.
From the ubuntu live cd enter a shell and do sudo install-mbr /dev/hda
If hda isn't the drive that contained your master boot record type in the drive that did. The install-mbr command should remove all of grub or lilo. Hope that helps.

---

### Post by Herman on 2006-06-17
Hello, Bios_
If you still have any problems, this page goes into more details in case that might help, [*click here*]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

