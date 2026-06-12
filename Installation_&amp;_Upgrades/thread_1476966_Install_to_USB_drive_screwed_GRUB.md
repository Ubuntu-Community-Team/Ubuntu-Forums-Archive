---
title: "Install to USB drive screwed GRUB"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by gibbylinks on 2010-05-08
Help,

I used the live CD to install 10.04 to a USB hard drive. It installed successfully but has left me with a problem.

It's absorbed the USB hard drive into my GRUB menu when I was hoping to have two separate GRUB menus. When I boot from the USB drive it fails and gives me a GRUB Rescue prompt.

But if I boot normally I get a GRUB menu with my internal hard drive and the USB drive on it, which if I select boots from the drive OK.

My question is how do I separate them, so I end up with two separate independent GRUB menus.

Thanks

Sorry it's worse than I thought. Can't boot without the USB drive connected........

---

### Post by Penguin Guy on 2010-05-08
You'll need to use chainloading, but that requires two copies of grub and I'm not sure how you'd go about doing that.

---

### Post by gibbylinks on 2010-05-08
OK reinstalled GRUB onto internal hard drive and it's working as normal now. But if I select USB drive from BIOS boot menu, it no longer boots.

What I'm trying to achieve is a set-up on the USB drive I can use for testing.

Thanks

---

### Post by oldfred on 2010-05-08
Just like you installed grub to the internal, install grub to the external. Just use the install that is on the external as the mount fo t the reinstall.

You then should have two different grubs.

If you want to see what is where I use this before and after installs to make sure I did what I wanted and to document the system. It shows the boot loaders and runs a lot of commands to a file. You do not need to post unless you want help understanding it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by dakra137 on 2010-05-09
To boot from the stick independently of what is on the machine's disks:

The easiest thing is to reinstall onto the USB drive from the distribution CD. After picking the partitions on the USB drive (my case: 6GB root and 2GB SWAP on the stick)  click the ADVANCED button, which will let you add the boot loader onto the stick.

---

