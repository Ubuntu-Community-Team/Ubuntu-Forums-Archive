---
title: "External Hard Drive Install (with Vista)"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by SAChopper on 2007-10-04
Hi,

I have just installed Ubuntu (feisty) onto an external hard drive.  I just booted into the live CD, plugged the USB hard drive in, then ran the installation on the desktop.  I selected the external hard drive, and the install happily went away.

When I rebooted, I just went straight to a Grub 21 Error.  So I spammed F8 when my laptop posted and I had 4 options:

Ubuntu
Ubuntu
Windows Vista Longhorn (Recovery)
Windows Vista Longhorn

So I booted into standard Vista again and googled around and found this page in the ubuntu documentation: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I installed EasyBCD and the reinstall vista bootloader option was too tempting! I need Vista for work, Ubuntu is just for a play at this stage!  Anyway I clicked it and vista now boots, but of course there is now no sign of Ubuntu.

Now in EasyBCD there is also Add/Remove Entries with a handy Linux option.  So I selected type: grub, but the only Drive showing up in the dropdown is my windows partition.  So I checked the GRUB isn't installed to the bootsector box.

My problem now is that I have no idea how to configure NeoGrub.  I can't find much on it on google, and even then none of that is helping me regarding it is installed on an external drive!  I tried just rebooting, but I just get a GRUB command line thinger when I select the Ubuntu boot, Windows Vista still boots fine.

So, does anyone know what I should be putting in my NeoGrub config file?  Or should I just delete the ubuntu partition on my external hard drive and start again and do something different?

Thank you,

Matt.

---

