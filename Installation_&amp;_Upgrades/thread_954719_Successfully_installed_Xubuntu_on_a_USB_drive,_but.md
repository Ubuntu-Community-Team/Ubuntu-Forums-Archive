---
title: "Successfully installed Xubuntu on a USB drive, but..."
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2008-10-21
now, I find myself wanting to use the bootable USB drive on computers that do NOT boot from USB. I used the method described at [http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/).

Anyone tell me how to make a Grub or Lilo boot CD that will allow me to boot into my USB installation from a computer that doesn't support USB booting?  Thanks...

---

### Post by snowpine on 2008-10-21
Hi Squashpup,

I am not sure if this advice will apply to Xubuntu or not. I have a distro called SliTaz installed on a Live USB stick. When I want to use it on an old computer that can't boot from USB, I insert both the SliTaz Live CD and the USB stick. The computer boots from the CD, then at the boot options prompt, I type 'slitaz home=usb' and it boots from the CD but uses the USB as my /home partition (so all of my documents and settings are identical to when I boot from the USB on a more modern computer). I would assume that Xubuntu has this feature as well, but I've never tried it. :)

(edit) I haven't used a Xubuntu live CD in a while but I think you can press F6 to edit your boot options. Hope that helps.

---

