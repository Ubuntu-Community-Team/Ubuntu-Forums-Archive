---
title: "Want a Clean Installation"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by infamous16 on 2008-05-29
I have Windows vista 64 bit right now and am looking forward to getting Ubuntu.

I had it before on my xp computer I just had some problems.

I was using the Grub bootloader, and I didn't really know how to work and change its settings...are there any other boot loaders that are easier to use? I would like windows vista to boot as default, and ubuntu to boot if I choose it...I couldn't get the grub loader to do that.

And I am not really sure how I should do this partition thing, should I just do it all off of the ubuntu installation cd, or on my own?

and do I need to burn a cd/dvd to install it, or can I just mount it or something?

thanks

---

### Post by lisati on 2008-05-29
> **infamous16 said:**
> I have Windows vista 64 bit right now and am looking forward to getting Ubuntu.

I had it before on my xp computer I just had some problems.

I was using the Grub bootloader, and I didn't really know how to work and change its settings...are there any other boot loaders that are easier to use? I would like windows vista to boot as default, and ubuntu to boot if I choose it...I couldn't get the grub loader to do that.

And I am not really sure how I should do this partition thing, should I just do it all off of the ubuntu installation cd, or on my own?

and do I need to burn a cd/dvd to install it, or can I just mount it or something?

thanks

The installers on some of the installers for Ubuntu that come on CD have an option to use the entire disk, which can take care of wiping out anything you migh have on your hard drive. If you choose that option make sure you have backups of all your important data first.

I've seen in the forums that there are options to boot a CD from other devices e.g. a USB devuce, but I've got no personal experience to draw on.

---

### Post by pastalavista on 2008-05-29
No need to wipe Windows. After you install Ubuntu it's fairly easy to edit grub. Just install, from the add/remove menu, Qgrubeditor. It's also pretty easy to do it in the terminal [sudo gedit /boot/grub/menu.lst] and change the default to 4 (or 5 if you have a hidden Windows recovery partition) and save and reboot.

---

### Post by pastalavista on 2008-05-30
If you don't want to install from the booted "Live CD" then you should download the "Alternate Installation" CD and install from it.

---

### Post by pastalavista on 2008-05-30
oh, I just remembered (I've read a lot about this recently) if you can't burn a CD, you can order one by mail for free (postage and everything) or, install a downloaded .iso file and install it to and/or run from an external usb drive... even a 2 GB or greater flash drive

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

---

### Post by LeoSolaris on 2008-05-30
Just a note, the Alternative CD is harder to use if you do not know what you're doing.

Here is a great site for info on Grub and what it all means. [HERE]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst")

Another great alternative to installing it and mucking around with partitions is to install it inside Windows with Wubi. Wubi is new, so it may have a few extra bugs, but it will let you get your feet wet, so to speak.

You will have to burn a disc to install it on it's own partition, however. It is a rather involved process to stick it on a USB thumbdrive.

Leo

---

### Post by infamous16 on 2008-05-30
and if I ever want to delete everything (ubuntu and grub) how do I go about doing that?

My last computer I could never figure out how to delete grub.

---

### Post by zvacet on 2008-05-30
You can delete Ubuntu with any(live or alternate) Ubuntu CD.After that you have to fix your Vista MBR.Instrctions for doing thar are [here.]("http://ubuntuforums.org/showthread.php?t=740221")

---

