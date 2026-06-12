---
title: "Grub2 grub only partition?"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by Odemia on 2010-03-10
I want to migrate my current setup to grub2 but am a little confused how best to do it.
My current setup is:[INDENT] Single - ext 2 grub partition (8MB) - no boot images in /boot, just /boot/grub
Many - ext3/ext4 root partitions - no /boot/grub, just the appropriate boot images in /boot
[/INDENT]Based on what I have found in forums/how to guides I am not sure how to replicate this type of setup in grub2.  As I understand I am not supposed to edit /boot/grub/grub.conf but let update-grub or grub-mkconfig manipulate it.  How do I get the right configuration onto my grub partition?  And how do I keep updating it? Anyone done anything like this with grub2?

---

### Post by dstew on 2010-03-10
That is an interesting setup. I assume your /boot/grub partition is correctly mounted to your Linux system filesystem(s) so that if you do```
ls -l /boot/grub
```you see your menu.lst file etc.

If so, I think you can just go ahead and install grub2 from your linux system the usual way. It will install in two steps. First, it installs the grub2 program files into the /boot/grub directory. The main program is core.img. That should be done automatically by the installation command:```
sudo apt-get install grub-pc
```The package might be **grub2** for some more recent Linux versions. The installer asks if you want to chainload grub2 on reboot, which you want to do, so answer yes. It asks if you want to reboot to a linux command line, and you also do want that (I think just press 'enter').

At this point, the grub2 program should be in your /boot/grub directory. The installer made an entry into the grub legacy menu.lst file that will allow you to chainload it from grub legacy.

When you reboot, you will have the new "Chainload into grub2" menu item. If you select grub2, it will now boot grub2, and you should get a grub2 menu. If the grub2 menu works OK, and you can boot your Linux systems with it, you are almost done.

At this point there is still the grub legacy stage 1 in the MBR of the boot disk. To replace it with the grub2 loader, in your Linux system enter this command:```
sudo upgrade-from-grub-legacy
```Here you have to make a choice as to where you are booting from. According to the Ubunut [Grub2 document]("https://wiki.ubuntu.com/Grub2"), you need to use the spacebar to mark your choice or else you get an unbootable system.

In [this How-To]("http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04") they edit the root line in the "Chainload into Grub 2" menu command seen at the first reboot, when you get the modifed grub legacy menu. Maybe this problem has been fixed, but I am not sure. It is not mentioned in the Ubuntu Grub2 document.

---

### Post by Odemia on 2010-03-12
@dstew:  No the grub partition is not normally mounted within any OS install.  But I have already sucessfully installed grub2 to my grub partition.  The question is not how to install grub2 but how to manage booting an ever changing array of distros?

Did some more research and I am thinking I should change things around to chain-load from my grub partition instead of booting the kernels directly from the grub partition.  That will allow each install to manage which which kernel to boot from locally.

But can grub2 be used for the boot partition that only contains /boot/grub (ie no /etc or /bin/bash)?  Despite all the warnings can I just statically enter the chain-loading statements into /boot/grub/grub.cfg?  Or would I have to go through the hastle of mounting and linking the grub directory into place and then configuring /etc/grub.d/* in order to configure grub on my boot partition?

Or is there a better way to manage booting into an ever changing array of distros?

---

### Post by TutAmongUs on 2010-03-12
> **Odemia said:**
> @dstew:  No the grub partition is not normally mounted within any OS install.  But I have already sucessfully installed grub2 to my grub partition.  The question is not how to install grub2 but how to manage booting an ever changing array of distros?

Did some more research and I am thinking I should change things around to chain-load from my grub partition instead of booting the kernels directly from the grub partition.  That will allow each install to manage which which kernel to boot from locally.

But can grub2 be used for the boot partition that only contains /boot/grub (ie no /etc or /bin/bash)?  Despite all the warnings can I just statically enter the chain-loading statements into /boot/grub/grub.cfg?  Or would I have to go through the hastle of mounting and linking the grub directory into place and then configuring /etc/grub.d/* in order to configure grub on my boot partition?

Or is there a better way to manage booting into an ever changing array of distros?
  You would run grub-install again (pretty sure the grub volume would have to be mounted), and that would re-iterate the bootable volume search again.:D

---

