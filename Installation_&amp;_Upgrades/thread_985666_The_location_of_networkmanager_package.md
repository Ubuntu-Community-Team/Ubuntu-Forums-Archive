---
title: "The location of networkmanager package"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Vincent_Lin on 2008-11-17
Hi,

My IBM T42 has Atheros wifi chip so I am experiencing no wireless after resume from sleep.  Fortunately I have found the "real" solution/workaround of this problem.

Unfortunately, before applying the workaround, I un-installed networkmanager.  Now I don't have Internet connection and Synaptic/apt-get can't find networkmanager to download and install, well, since there is no networking.  

I do have an 8.10 installation CD but after I instructed synaptic to read the source list from CD, it still can not find networkmanager package.

So, the question is, can someone tell me where I can find networkmanager package on the net so that I can download from another machine and install it?

Thanks.

Vincent Lin

---

### Post by iponeverything on 2008-11-17
You probably still have it in your cache.
```
 
cd /var/cache/apt/archives
find |grep network


```
You can reinstall with:

```
sudo dpkg -i <package> 

```

---

### Post by jgoguen on 2008-11-17
Are you sure it's not on the CD?  The package names you should look for are network-manager and network-manager-gnome.

If you can't find them on the CD, you can download the NetworkManager package by going to [http://packages.ubuntu.com/intrepid/i386/network-manager/download](http://packages.ubuntu.com/intrepid/i386/network-manager/download) and choosing a mirror in your country (or close to it).

You should also make sure you have the network-manager-gnome package installed as well, that's downloaded from here: [http://packages.ubuntu.com/intrepid/i386/network-manager-gnome/download](http://packages.ubuntu.com/intrepid/i386/network-manager-gnome/download)

---

### Post by Vincent_Lin on 2008-11-17
Thanks guys.

I can't find the file in /var/cache/....., nor I find the files in CD (networkmanager, network_manager, network_manager_gnome, etc...).

However, download from Internet did work for me.  I copied them to a flashdrive and installed them subsequently.

Thanks a bunch, and so promptly.

Now I would need to see that madwifi workaround

/etc/pm/config.d/madwifi file with a single line as

SUSPEND_MODULES=ath_pci

would work.

Thanks again.

Vincent

---

