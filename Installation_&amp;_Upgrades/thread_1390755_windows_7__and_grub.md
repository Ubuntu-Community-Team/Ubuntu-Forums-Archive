---
title: "windows 7  and grub"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by woodcarver_52 on 2010-01-26
I have tried several time to install ubuntu on my system. I go thru the entire install and right up to the restart...   the system restarts and goes straight to windows and does not show the grub screen at all.. I have tried to use 9.04 and 9.10  neither will load the grub so I can us ubuntu....   I am really getting stumped ..

Any help with this I have reformatted the system each time..

 I have 4 hard drives and a dvd burner on my system... would the other drives other then the boot drive cause any trouble?????

My computer is a 2.8 ghz  1 gmem 775 socket system  Compaq

---

### Post by garvinrick4 on 2010-01-26
> **woodcarver_52 said:**
> I have tried several time to install ubuntu on my system. I go thru the entire install and right up to the restart...   the system restarts and goes straight to windows and does not show the grub screen at all.. I have tried to use 9.04 and 9.10  neither will load the grub so I can us ubuntu....   I am really getting stumped ..

Any help with this I have reformatted the system each time..

 I have 4 hard drives and a dvd burner on my system... would the other drives other then the boot drive cause any trouble?????

My computer is a 2.8 ghz  1 gmem 775 socket system  Compaq
You have 4 hard drives on your system. That sounds like trouble right there. You are not
installing grub2 on the correct drive. By default it install on sda I believe. In last page of install you will see an advanced tab in lower right hand corner, click it, it will tell you default and give you choice of where you want it.  It is going somewhere!!!
Google the 4 hard drive set up, have no idea what your machines "fdisk -l" looks like.
But I would think it would take a read before you jump.

---

### Post by darkod on 2010-01-26
That's definitely your problem. Grub2 is on one drive but you are still booting your windows bootloader (and drive most likely) so it boots windows straight away (windows bootloaders know nothing about linux present).

Just play around with the HDD boot order until you find your ubuntu drive. Or if you can tell which one is it (by size for example), make that drive first in boot order and see if that helped.

---

