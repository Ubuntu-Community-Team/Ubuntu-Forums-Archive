---
title: "Alpha 3 doesn't boot, intel atom"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by *g!t5^_)*(H on 2010-02-27
Hi,

I tested Alpha 3 into my Sony Vaio W netbook, using a live USB.

It only works if I start with 'acpi=off' from boot menu, and I've been looking for a reported bug but I've not found it.

I don't know how to report the bug, because I'm not even able to use the console, without using the 'acpi=off' option.

Is there a way to get the necessary logs (dmesg, ...) in order to report this bug ?

Is there a known bug with intel atom n280 with gma 950?

Thanks in advance for your help.

---

### Post by macstevejb on 2010-02-27
I too have the same problem with my Intel Atom Netbook...initially, I couldn't boot the Ubuntu Lucid live cd from my usb memory stick.

I found the workaround was to select boot option "nomodeset" at boot and then post-install to reconfigure grub2 to include the nomodeset option.

Must be some Lucid compatibility problem with the Intel graphics I think. It always booted fine in Karmic.

HTH

regards,

---

### Post by *g!t5^_)*(H on 2010-02-27
Thank you very much, yes it works with (no mode set) option, I'll test the rest of the features, hoping they will fix this issue with atom netbook in time to beta release.

---

