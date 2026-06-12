---
title: "What's rewriting my /boot/grub/menu.lst"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by sholdowa on 2006-10-11
I'm running edgy eft with a customized 2.6.19-rc1 kernel on an acer aspire 2010 - and it's working fine. However, when I boot it up in the morning, the initrd line has disappeared from the following block.

title           Ubuntu, kernel 2.6.19-rc1 Default
root            (hd0,0)
kernel          /boot/vmlinuz root=UUID=2f24572d-6a54-47fe-97e8-9f0c3774cd0a ro quiet splash
initrd          /boot/initramfs-2.6.19-rc1.img
savedefault
boot

I have to reboot off an old kernel, add it back in, and reboot to get back up and running. Can anyone tell me which process is rewriting this file, and how to stop it??

---

### Post by ciscosurfer on 2006-10-11
Every time you update via command line or via Synaptic, lately anyhow, newer kernels get downloaded if you're using Edgy.  When this occurs, the kernel essentially gets written into your GRUB file via an 'update-grub' command.  If you want a static stanza within your 'menu.lst' file, then place this block either above or below the block that starts AUTOMAGIC ...blah, blah, blah....so, placing your desired title, root, kernel, initrd, savedefault, boot, etc. lines before the AUTOMAGICALLY ADDED...., it will get loaded properly and won't get overwritten.  Hope this helps.  As an aside, as I'm sure you're aware, Edgy Eft is in beta and is for testers and developers only and should not be used on production machines b/c, well, it's beta.  If you know this already and are comfortable with these points, then that's great.  If not, you should backup you data, and then reinstall Ubuntu but use the Dapper Drake install instead of Edgy Eft.

---

### Post by sholdowa on 2006-10-12
Thanks... forgot about that. Not too sure why my 2.6.19-rc1 definition didn't disappear completely, though!

---

