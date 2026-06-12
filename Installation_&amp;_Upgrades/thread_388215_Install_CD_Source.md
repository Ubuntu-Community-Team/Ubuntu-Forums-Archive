---
title: "Install CD Source"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by tankarama on 2007-03-19
Hi,

To avoid the questions why, heres a little background:

I have a Asus m2n4-sli, which has nforce chipset with Fake Raid. I have a single large Raid5 array that I wish to install Ubuntu on to, in a dual boot situation with Raid.

My chipset isn't supported fully until 2.6.19, so I'm stuck with the feisty install if I want the live CD to boot. To get dmraid to support raid5 I need the kernel patch dm-raid45, which of course isn't available (produced by redhat) for anything larger then 2.6.18. So I have re-written the patch myself and successfully applied it to the 2.6.20 kernel source from the feisty archive. I have then followed the instructions for customizing an install CD, extracting the squashfs, installing my kernel as well as the dmraid packages. 

I then went to boot my customized install CD and it isolinux of course booted the /casper/vmlinuz not the one in the squashfs. I then replaced the /casper/vmlinuz and the /casper/initrd.gz with those from my patched kernel and re-burnt the CD.

But now the CD gets stuck finding VFS and kernel panics. The original initrd.gz from the CD is much bigger then mine and I would like to know where the sources are for the live CD that create this file in particular. So that I can see how its built and build my own that works.

If i get this all working I'll write an article to help others. Maybe even put the install CD somewhere people can just download it since the patch is not going to make it into feisty now.

---

