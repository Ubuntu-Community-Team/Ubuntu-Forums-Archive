---
title: "Kubuntu Install grub to Boot Sector"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by darkhammer8108 on 2008-05-08
Hello everyone. i am a freebsd/opensuse user and im trying to migrate over to kubuntu. on my system i use the windows vista boot loader to select the operating system i wish to boot (EasyBCD). i have downloaded the kubuntu-alternate cd and want to make it install grub to the boot sector (the root partition). i went through the steps of installing kubunu on a VM a few times and cannot figure out how to change where grub installs to. does anyone know how to install it to the boot sector?

---

### Post by mikewhatever on 2008-05-08
> **darkhammer8108 said:**
> Hello everyone. i am a freebsd/opensuse user and im trying to migrate over to kubuntu. on my system i use the windows vista boot loader to select the operating system i wish to boot (EasyBCD). i have downloaded the kubuntu-alternate cd and want to make it install grub to the boot sector (the root partition). i went through the steps of installing kubunu on a VM a few times and cannot figure out how to change where grub installs to. does anyone know how to install it to the boot sector?

The boot sector, the MBR, should be the default choice, so just don't change anything if MBR is what you want. However, if you want grub installed on a partition, you have to specify that partition instead of hd0. 
[http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location](http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location)

---

### Post by darkhammer8108 on 2008-05-08
ahhh i see. i was testing in a vm without installing vista first so it was not detecting any other OS's and just installing to the MBR. what i need to do for the test is install vista then install kubuntu

---

