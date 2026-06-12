---
title: "multi-selectable-troubleshooting boot usb stick"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by Flaggmann on 2014-09-04
I would like to make a troubleshooting/installing boot stick that would boot and allow me to select which local ISO file from the stick I want to boot into.
For example 1. ubuntu live install  2. mint live install  3. debian live install  4. peppermint live install 5. clonezilla live  6. gparted live 7. boot repair  and possibly one or two 32 bit versions of one or two of these.

I am not always in a position to have an immediate internet connection so unetbootin, although it allows selection, requires a download; my need is to select the choice from a number of ISO files on the bootable stiick.

I have seen a program in mint, called mintstick that creates a bootable install live disk but does not allow one to use multiple ISO files and select which one you want to use each boot. It would be added bonus to be able to replace individual ISO files as newer ones were released.

Is anyone aware of such a program in any distro for that matter but would prefer debian/ubuntu?

Thanks

---

### Post by varunendra on 2014-09-06
Try 'MultiSystem' or 'YUMI' - both from [pendrivelinux.com]("http://www.pendrivelinux.com/").

YUMI (originally made for Windows, but now also exists for Linux) is more capable than MultiSystem (made only for Linux) in some ways, but I'm not sure how well its Linux version works. The windows version works perfectly.

For best compatibility, YUMI 'extracts' the contents of the supplied ISOs and also makes some changes to its boot files to make sure they work properly. But it also allows you to 'Directly Load ISOs (originally intended for unlisted distros)' if you wish to preserve the original ISO. Although the functionality/compatibility of the booted ISO is not guaranteed that way.

---

