---
title: "how do I install Jaunty without a cdrom or updating Intrepid?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xzero1 on 2009-04-09
I have a tablet pc ,with no internal cdrom, that already has Intrepid installed. I cannot boot from usb and I do not yet want to overwrite my current Intrepid install. There is not enough space for a direct partition copy. Would it be possible to install Jaunty from an iso file? What would be the best approach?

---

### Post by Marlonsm on 2009-04-09
I think the best for you would be pressing Alt+F2 and typing "update-manager -d" (without quotation marks) it will start the update manager and tell you about the 9.04 release, after it, it's pretty much straight forward.
it will download ~700mb of files, tho, so be prepared to wait some time during the update.

---

### Post by super.rad on 2009-04-09
The only thing that I can think of is if you somehow cloned your intrepid installation onto another partition then upgraded that, but I have no idea if that is possible or if it would work.

EDIT: Sorry only just saw you had already said there isn't enough room for a direct partition copy.
How much space do you have then? If there isn't enough for a partition copy then will there be enough for jaunty?

---

### Post by xzero1 on 2009-04-09
> I think the best for you would be pressing Alt+F2 and typing "update-manager -d" (without quotation marks) it will start the update manager and tell you about the 9.04 release, after it, it's pretty much straight forward.
it will download ~700mb of files, tho, so be prepared to wait some time during the update.   A wait would be acceptable. Will this allow me to install without overwriting Intrepid?


> How much space do you have then? If there isn't enough for a partition copy then will there be enough for jaunty?     
I do have enough space for Jaunty, but my Intrepid partition used is about twice what I need.

---

### Post by super.rad on 2009-04-09
What Marlonsm said will overwrite Intrepid.
Could you not remove programs you don't use, empty /var/apt/cache (or wherever it's stored) to try and cut the size of your intrepid install until it's small enough to copy?

---

### Post by robert.rankin.jr on 2009-04-09
I would recommend deleting your swap partition (you can re-create it later), format it with gparted, and use UNetbootin (or something similar) to install Parted Magic. Then boot into that, resize your existing partition. Chroot into that environment and run grub-install /dev/sda so that when you reboot your in your original installation. In that installation, delete your swap partition. Then follow the instructions for installing ubuntu from an existing installation at [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)


Robert

Edit: apparently you can do an online resize in the more recent linux kernels. I guess I'm out of date ;) That means, if your FS is ext3, you should be able to just run gparted and resize it. Though I can't seem to do it here... Will research. Here's this: [http://www.vtek.nl/resize-mounted-partition-under-ubuntu_software_181.html](http://www.vtek.nl/resize-mounted-partition-under-ubuntu_software_181.html)
When I try it, the e2fsck warns me about severe file system damage. Would rather not risk it ;)

---

### Post by xzero1 on 2009-04-09
> What Marlonsm said will overwrite Intrepid.
Could you not remove programs you don't use, empty /var/apt/cache (or wherever it's stored) to try and cut the size of your intrepid install until it's small enough to copy?Possibly, but I'm not yet convinced there is no better way. I know its possible to mount the Jaunty iso. So it should be possible to install from that mounted iso.

---

### Post by xzero1 on 2009-04-09
:popcorn:Thanks guys, I think I have found it and I *know* you are interested. Why waste burning a cd-rom! I will attempt this method and post on the results. 

**Update:** [dougfractal]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html#comment-3547725998443369362") adds that this is possible from Linux too. The method as he describes is:

From the terminal enter these commands

sudo mkdir /distro
sudo chmod `whoami`:`whoami`
cp MYLINUX.iso /distro/distro.iso

Now  extract Linux_kernel & Ram_disk  to /distro#

Open  /boot/grub/menu.lst

#ADD NEW ENTRY#
title Install Linux
root (hdX,X)
kernel /distro/Linux_kernel
initrd /distro/Ram_disk

Reboot and select "Install Linux" from grub.

For the full article see [http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)

---

### Post by CLomax on 2009-04-09
Is it possible to use this?

[http://lubi.sourceforge.net/unetbootin.html#](http://lubi.sourceforge.net/unetbootin.html#)

:KS

---

### Post by xzero1 on 2009-04-09
> Is it possible to use this?

[http://lubi.sourceforge.net/unetbootin.html#](http://lubi.sourceforge.net/unetbootin.html#)Cool, it seems it was designed for this type of thing. It even downloads and installs the distrubution you select! From what I've read it should work perfectly. Still, its good to know what the code does as explained in the article linked in my post above.

---

