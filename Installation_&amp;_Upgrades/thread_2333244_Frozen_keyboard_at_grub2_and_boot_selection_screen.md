---
title: "Frozen keyboard at grub2 and boot selection screens"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by Steven_T_Parker on 2016-08-08
I was previously using Kubuntu and tried to use the boot selection screen to install another distro from a USB memory stick, and the arrow keys did not work on either my laptop or a USB keyboard.

I think purged and reinstalled GRUB2, according to very precise instructions.  I was running a virus scan with Clam.TK (which I halted mid scan) not sure if this is an issue.  It discovered 2 trojans.

Soon after, when I did the whole F12 boot selection thing, a command line type screen would come up suggestion I input tab to see a list of BASH commands.  However, none of the keys apart from Enter worked.

This peculiar screen vanished for some reason when I made subsequent attempts, but still:  arrow keys frozen, and (not sure if this is related) attempts to boot Kubuntu 14.04 from DVD did not work.

This is "partially" solved, as I managed to select a USB boot device using this method:  holding the DOWN ARROW whilst pressing F12.  I am now using Lubuntu, but again it is impossible to change boot device: this "forcing the down arrow" thing no longer seems to work.  I am very happy with Lubuntu, but would at least like the choice of reformatting.

Is it worth purging Grub2 and installing again? [IMG]https://ubuntuforums.org/images/icons/icon8.png[/IMG]

---

### Post by oldfred on 2016-08-08
Probably not a grub issue.

What video card/chip?

Some UEFI/BIOS require you to turn on USB port for keyboard or mouse. Both Windows & Ubuntu add their own drivers, but grub requires the BIOS/UEFI driver to work.

---

