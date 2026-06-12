---
title: "Installing Edgy to existing partition"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by geovino on 2006-11-24
I have a Athlon 1400 pc w/768MB Ram with two hard drives:

hda1 with WinXP (35 GB) 
hda2 w/dead version of Dapper (45gb) tried to upgrade to Edgy and the installation hung up and I had to reboot which killed it. 

hdb1 with PCLinuxOS (40gb)

If I install Edgy (from CD) to the old Dapper partition, I assume it will see that partition, but will it install and add itself to my existing bootloader which is Lilo in PCLOS ver. .92?

I would like to use the bootloader that PCLOS is using and add Ubuntu Edgy to it. How is this done?

Thanks

---

### Post by geovino on 2006-11-25
Here's some info I got from the PCLOS forum:

Re: Installing Distro to existing Partition  	 Reply with quote
When given the option to install the bootloader choose not to install it to the MBR but install it to the partition that you are installing Ubuntu on. Then you just need to rdit the PCLOS Lilo and add in the Ubuntu partition. Hope this helps and if not we can get it done. 

Do I have the option to install the bootloader to the hda2 partition that Ubuntu would be installed?

---

