---
title: "server installation trouble"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Jonny Axehandle on 2009-12-25
I'm trying to install ubuntu server edition 9.10 on a brand-new system. It all goes well until I reach the last step. I'm given a variety of options, with "Finish Installation" being one. I choose it and it tells me I need to install a boot loader. Choosing GRUB seems to do nothing (not even give me an error) after which I am still told I need a boot loader. LILO, on the other hand, errors no matter where I choose to install it to. My third option is skipping the boot loader. I chose this and it told me I needed /vmlinuz kernel on /dev/mapper/nvidia_eefiecec1 with root=/dev/mapper/nvidia_eefiecec1 as the boot option.

I am tech savvy but this is my first linux install. If anyone could give me some insight on fixing GRUB/LILO or explain how to boot without them it would make my day. If it helps there is a list of the hardware I am using here:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C122-05660](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C122-05660)

Thanks and merry christmas!

---

### Post by chrisinspace on 2010-01-06
I am having this exact same problem.  I'm installing on a RAID 1 array.  The installer can see the array and partition and format it just fine, but when I get to the step where grub should install I cannnot get past it.  I tried Lilo and ran into similar issues.  For the moment, I'm stuck.

---

