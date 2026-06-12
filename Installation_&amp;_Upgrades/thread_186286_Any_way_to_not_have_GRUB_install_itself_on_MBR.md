---
title: "Any way to not have GRUB install itself on MBR?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by jackson on 2006-06-01
Hi there-

I'd like to try out this new release, but I already have a bootloader on the MBR that I've tweaked out in various ways (I have several distros on this one particular box).  I have read that Drake installs GRUB on the MBR and that there is no option to install it on another parititon.  Is this true and is there any way around it?

Thanks.

---

### Post by reckless2k2 on 2006-06-01
I'm having same issue. I'm triple booting XP, Ubuntu, and Suse. The Ubuntu installer doesn't give you a choice of location to install boot loader as in previous versions. The Ubuntu installer overwrote my windows MBR and that's going to be an issue for me. 

I'm hoping there's a way to choose a bootloader location similar to older versions.

---

### Post by jackson on 2006-06-01
There's got to be a way.  I can't imagine installing GRUB to the MBR is the only choice.

---

### Post by reckless2k2 on 2006-06-02
I've been told that by using the alternate ISOs you can get the "old" text based installer where you can choose the location of the boot loader. I haven't confirmed this yet but I'm sure this would work. Thanks to Russ for the info.

---

### Post by jackson on 2006-06-02
Thanks, reckless2k2 -- I'll try that.  Is there a way to invoke the text-installer from the main live cd?  I'd hate to have to download another whole ISO (but I will, of course, but thought I'd check first).

---

### Post by reckless2k2 on 2006-06-03
Confirmed that text based installer exists in "alternative" ISOs and you have the bootloader location option. The install is MUCH slower than that of the LiveCD but it's worth it for the bootloader option for me. To my knowledge, there is no text based installer in the LiveCDs. 

Good luck. I choose a VERY fast mirror and got the alternative ISO in about 20 minutes.

---

