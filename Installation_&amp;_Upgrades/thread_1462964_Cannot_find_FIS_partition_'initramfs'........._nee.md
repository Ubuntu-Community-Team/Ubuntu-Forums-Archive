---
title: "Cannot find FIS partition 'initramfs'......... need help!!!"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by vikramtheone on 2010-04-26
Hi Guys,
            I have a Ubuntu 9.04 Linux running on Freescale's i.MX515(ARM Cortex based) board with me.

There were about 250 updates pending and I did that today, well some of the updates failed because of the infamous errors:

[COLOR=DarkSlateBlue][B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/B][/COLOR]

So, when I do the ** '[COLOR=Red]sudo dpkg --configure -a[/COLOR]'** I get new errors related to FIS partition:
[B]
[COLOR=DarkSlateBlue]Cannot find FIS partition 'initramfs'[/COLOR][/B][COLOR=DarkSlateBlue]
User postinst hook script [/usr/sbin/flash-kernel] exited with value 1
dpkg: error processing linux-image-2.6.28-18-imx51 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-imx51:
 linux-image-imx51 depends on linux-image-2.6.28-18-imx51; however:
  Package linux-image-2.6.28-18-imx51 is not configured yet.
dpkg: error processing linux-image-imx51 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-imx51:
 linux-imx51 depends on linux-image-imx51 (= 2.6.28.18.23); however:
  Package linux-image-imx51 is not configured yet.
dpkg: error processing linux-imx51 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-18-imx51[B]
Cannot find FIS partition 'initramfs'
dpkg: subprocess post-installation script returned error exit status 1[/B][/COLOR]

Whats going wrong here, need help!!! I'm a newbie.

Regards
Vikram

---

