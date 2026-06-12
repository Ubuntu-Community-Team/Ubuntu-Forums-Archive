---
title: "Gruv won't boot from ubuntu drive."
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by chazzy on 2006-06-05
Hi all,

I'm now a fully fledged dapper user!

I have a problem though.

/dev/hda - Windows
/dev/sda - Ubuntu

If my BIOS boots from hda, grub kicks in says hello and lets it boot. However, should I boot from the ubuntu drive, i just get "GRUB" and freeze.

Not a problem if i boot from the windows drive, but I'm planning on ditching that, but without it I can't boot.

Best regards, and many thanks for your time in advance.

Chaz

---

### Post by llamakc on 2006-06-05
You're using the BIOS bootloader to chose which one to boot from? 

When you choose the Windows disk /dev/hda does Grub show up on the screen for a second or two? If so, hit the escape key. You should be able to arrow up to Ubuntu at the top and now boot into Ubuntu.

I hope.

---

### Post by chazzy on 2006-06-05
Hi!

Sorry I wasn't very clear.

I left my windows drive in the box (hdd1) when i installed ubuntu so it put grub on that drive. I /think/ the grub on the ubuntu drive is that of an old debian installation but it doesn't work at all.

I'm sure its something simple like using grub-install on the ubuntu drive and changing the bios to boot direct from the ubuntu drive rather than windows.

Thanks for your help thus far.

---

### Post by chazzy on 2006-06-06
Fixed. Thanks anyway. I needed to modify the hd identifier in menu.lst.

---

