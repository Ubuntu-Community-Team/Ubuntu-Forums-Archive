---
title: "GRUB not booting on SATA hdd"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by nalbion on 2008-05-19
I'm trying to set up a Mythbuntu system with a single SATA hdd, but after installing and rebooting it gets stuck at "GRUB Loading stage1.5."

It works when I install Mythbuntu and GRUB onto a parallel ATA hdd, but as soon as I enable SATA in the BIOS with the SATA drive connected it hangs at 1.5. I've installed Mythbunto onto the SATA using just about every possible combination of install/setup options.  I know it's not (100%) a hardware problem (although I suspect buying a new mobo may solve the problem) because the system boots fine with LILO.  I'm not sure if it's:

a) Mythbuntu making some incorrect assumptions about my configuration and telling GRUB to do the wrong things ("/boot" or "/" being described incorrectly to GRUB).
b) The BIOS not supporting SATA correctly - There's an option in the BIOS "enable onboard SATA", but IRCers and some web pages have suggested there should be other settings to indicate the boot priority (not to be confused with boot order). 
or
c) GRUB not doing something correctly.

My motherboard is described here:
[http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US](http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US)

---

### Post by Scunizi on 2008-06-01
I have a similar issue.. brand new HD, fresh install of Hardy from the live cd. On initial reboot it also gets stuck at "Grub loading stage1.5" .. I've tried reinstalling grub via the live cd and terminal and was presented with no errors.. this is frustrating.. I have several machines with hardy on them.. This is the only one giving me headaches.

---

### Post by nalbion on 2008-06-16
How old is your mother board?  I've just upgraded my whole system as I suspected a dodgy motherboard - it had SATA connectors, but I think only for RAID - the bios couldn't autodetect...

Works on the new motherboard, but while I was connecting everything I noticed that my DVD drive was set up as an IDE master - perhaps that was actually the problem? 

Good dog - fetch

---

### Post by pmlxuser on 2008-06-16
in the bios seetings try to cheat your system to see your SATA hard disk as IDE (there is an option that syas somthing like disk type) set that one to IDE and then do install again , mine worked Though it was an ubuntu and i also tried fedora (both worked with the tweak.
Good luck

---

### Post by pmlxuser on 2008-06-16
in the bios seetings try to cheat your system to see your SATA hard disk as IDE (there is an option that syas somthing like disk type) set that one to IDE and then do install again , mine worked Though it was an ubuntu and i also tried fedora (both worked with the tweak.
Good luck

---

### Post by MattVogt on 2008-06-21
I have a fairly similar situation to you, except that my system does occasionally boot; it seems to be random as to whether it succeeds or fails, but it boots approximately every 6-8 attempts.

I have an IDE CDROM drive and a single SATA HDD - everything works fine when booting from CD, or when loading grub from HDD actually works.  Otherwise, I get a range of different errors from GRUB - sometimes I get complete failure to load, other times I get "Loading stage 1.5Read error", other times it loads grub and gives me the option to enter the menu, then seems to hang after that...

My motherboard is new, it's a Gigabyte GA-MA78GM-S2H, so I think it's unlikely to be the issue.  Any other ideas?

Thanks

---

