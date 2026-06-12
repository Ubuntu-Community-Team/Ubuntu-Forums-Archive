---
title: "failing to install 24.04 (over pxeboot), it hangs on cloud-init"
date: 2024-07-22
forum: Installation &amp; Upgrades
---

### Post by sysnet-ucsd on 2024-07-22
Note that I AM NOT TRYING TO AUTOINSTALL.  I just have the iso handed up via pxeboot.  I seem to have a set of servers for which this installation gets all the
way to 

"Starting cloud-init.service - Init&#8230;t job (metadata service crawler)..."

and then it JUST HANGS.  I had a similar issue with 22.04 installation previously, which actually eventually went away and installed properly.  But this is getting old.  Is there some way to bypass
the cloud-init thing?  Note that this is during installation, I am using PXEboot, I am NOT trying to autoinstall (I'm just fine with manual/interactive installation).  I have the iso mounted on a local 
webserver, and my pxeboot menu looks like (i have a number of different distros/years/etc available in a menu)

```

    KERNEL ubuntu/24.04/vmlinuz
    INITRD ubuntu/24.04/initrd
    APPEND vga=normal console=ttyS0,115200n8 root=/dev/ram0 ramdisk_size=1500000 ip=dhcp url=https://www.localsource.com/ubuntu-24.04-live-server-amd64.iso

```

I mount the iso image and grab copies of its vmlinuz/initrd and make it available to the pxeboot loader.
If there is some way to dropkick/bypass/ANYTHING this stupid cloud-init, please let me know...???  
I mean I didn't even solve this for 22.04: it just went away on its own, which leads me to suspect there's some kind of hinky default values or setups but I don't want to wait for some random change later on (in .4 or whatever) that lets it work eventually.
I have done a LOT of googling to see if anyone else has they same issue, but it's all about getting the autoinstall to work, which is not my case.

I do note that the set of servers to which this happens are relatively old and have 4G memory (for example, Dell PE R200) but this should be enough. They all install 22.04 just fine from PXEboot.

Edited to add: I have plenty of servers for which the 24.04 installation is successful, so I don't think there's a fundamental issue with my setup, but it's possible that b/c they are older/slower/less memory, there's some settings
I could tweak into a new menu item for these particular servers? Or as I said, just bypass the cloud-init (after installation, I disable the cloud-init stuff entirely anyway for all of these servers).

I also noticed that 22.04 has a netboot option! After they said they weren't going to offer it anymore after 20.04??  But it doesn't seem available for 24.04 (yet?) so I can't try using that alternatively.  

Thanks for all your feedback and info!

---

### Post by jayrnz on 2024-07-22
Also having this same issue today when trying to install using [https://github.com/netbootxyz/netboot.xyz](https://github.com/netbootxyz/netboot.xyz) - Modern hardware, internet connected, pretty sure it has worked previously in the past couple of weeks.

---

