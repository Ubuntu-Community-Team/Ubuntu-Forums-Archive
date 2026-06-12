---
title: "Making bootable Installion on USB drive"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by coffeecat on 2006-09-04
I was wandering around the forum this morning and came across a link to a howto for installing to an external usb drive. Unfortunately and foolishly, I didn't make a bookmark and now I can't find the page in my browser history. Searches of this forum and the Ubuntu wiki using various combinations of < install, boot, usb, disk, external, hard, drive > come up with very large numbers of irrelevant results and I still can't find what I am looking for.

In essence the howto described making a bootable CD containing grub and the kernel and this is used to boot into the usb installation so that the internal drive is untouched. This CD trick gets around the problem of the system not being able to recognise the usb device until after the kernel is loaded. The disadvatage is that if there is a kernel upgrade one is stuck with an old kernel. The answer to this is to use a CDRW and change the kernel and menu.lst on the CD after a kernel upgrade.

I understand the principles - I just need the details. An earlier attempt to get a bootable CD with a grub menu using the instructions given in the Grub manual met with abject failure :(, so I am keen to give this howto a go.

Does anyone know where I can find this howto or a similar one? It doesn't have to be specifically for Ubuntu. I can adapt one written for another distro if needs must.

Thanks.

---

### Post by FakeOutdoorsman on 2006-09-04
Is it this?

[Ubuntu on a USB drive?]("http://ubuntuforums.org/showpost.php?p=1221276&postcount=153") (link to single post)

---

### Post by cotcot on 2006-09-04
See my signature

---

### Post by coffeecat on 2006-09-04
Sorry guys, I didn't make myself clear. I was looking for a howto to install to a USB *hard*-drive, not a flash drive. In a way it should be easier than for a flash drive because (if I understand things correctly) you just do a conventional install but in addition make a bootable CD which contains Grub and all its bits and bobs including menu.lst together with the kernel - all the contents of /boot I guess. But it's the making of a bootable CD which can read its own menu.lst that I came a cropper over before.

But thanks for the links and the replies - they're both much appreciated. Installing to a flash drive. Hmm - I feel another project coming on. :wink:

And if you're wondering why I want to make an install on an external hard drive? I've got Dapper running nicely on my laptop - so nicely that I don't want to risk breaking it. If I could work out how to do this I could make a parallel install for experimental stuff and also to try out other distros. On my desktops I've got multiboots and can use spare partitions, but I've got some specific laptop projects in mind.

Thanks again. But if anyone has come across what I'm looking for I'll be most grateful.

---

### Post by FakeOutdoorsman on 2006-09-04
I found a thread related to Breezy but has some info on Dapper:

[SUCCESS - Breezy loaded on external USB drive !]("http://ubuntuforums.org/showthread.php?t=80811")

---

### Post by coffeecat on 2006-09-05
That's one big thread! The howto I stumbled across (and then lost) was different - a wiki-type page I think, which was why I tried to search the Ubuntu Wiki, but thanks for the link. Looks as though there is some useful stuff in there.

---

### Post by coffeecat on 2006-09-05
Found it at last! It was on the Ubuntu wiki. Eventually found it by exploring down from the home page. In case anyone is interested, [this is it]("https://help.ubuntu.com/community/BootFromUSB"). What with that and the three links above I'll have plenty to keep me out of mischief for a while.

Many thanks to all of you. :)

---

