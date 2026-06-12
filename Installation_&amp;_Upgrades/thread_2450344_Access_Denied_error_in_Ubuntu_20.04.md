---
title: "Access Denied error in Ubuntu 20.04"
date: 2020-09-11
forum: Installation &amp; Upgrades
---

### Post by drphd1 on 2020-09-11
I have recently had a very bad experience with Ubuntu 20.04. I installed Ubuntu on my HP Z620 workstation and the first problem that hit me was 640x480 resolution. I have a GTX 1070 in my system, so to install drivers I gave this command

sudo apt-get install nvidia-440

It started downloading all the dependencies but as soon as it reached 97%, it threw 403 forbidden IP error. In short no matter what I did, the same error. I opened the URL in browser but got error access denied. The library was libxxf86vm. I even changed the repositories but the same error with the same library. I also changed my network but still no success. Then I started noticing this error in many other installations also, e.g when I tried to install UNetbootin, Kubuntu desktop, etc. In the end, I  reinstalled Kubuntu on my computer. Interestingly, I easily installed the nvidia-440 drivers using the above command. I could also access the libxxf86vm library while on Kubuntu. Every other installation worked with any error. 

To check one last time, I again reinstalled Ubuntu and the same errors.

I don't know what's wrong and how to correct these problems.

---

### Post by TheFu on 2020-09-11
In general, drivers shouldn't be manually downloaded from a vendor.  The drivers should be loaded using the APT or Canonical package manager.  Since 18.04, LTS releases have made loading nvidia drivers for supported cards pretty easy.  There's an "**Additional Drivers**" button inside the Software Updater, whatever it is named on your system.  This will get what you need for that nvidia card, since it is relatively new.  I have a nvidia 1030 and it works fine.  My older 7200 GS isn't supported by nvidia anymore, so I'm stuck using the F/LOSS drivers.

There is also a CLI method ... run:
**sudo ubuntu-drivers autoinstall**
That should search the hardware, determine which proprietary drivers are available, then install those as needed. Works for nvidia, IME.

Before doing this, be certain to run:
**sudo apt update** so the current software locations for all packages are known to the system.
You may want to run sudo apt full-upgrade before doing the ubuntu-drivers command.

For other maintenance stuff all Linux desktops need, check this article:  
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) updated for 2020.

---

### Post by drphd1 on 2020-09-12
Tried all these steps several times. Under the **Additional Drivers** button in software update, its says no additional drivers. I can't choose any. Problem is not Nvidia or some other drivers. The main problem is the dependencies like libx files more specifically "libxxf86vm". It can't be accessed. Whenever I try to download these files, I get IP Forbidden error in CLI or Access Denied in browser. 




> **TheFu said:**
> In general, drivers shouldn't be manually downloaded from a vendor.  The drivers should be loaded using the APT or Canonical package manager.  Since 18.04, LTS releases have made loading nvidia drivers for supported cards pretty easy.  There's an "**Additional Drivers**" button inside the Software Updater, whatever it is named on your system.  This will get what you need for that nvidia card, since it is relatively new.  I have a nvidia 1030 and it works fine.  My older 7200 GS isn't supported by nvidia anymore, so I'm stuck using the F/LOSS drivers.

There is also a CLI method ... run:
**sudo ubuntu-drivers autoinstall**
That should search the hardware, determine which proprietary drivers are available, then install those as needed. Works for nvidia, IME.

Before doing this, be certain to run:
**sudo apt update** so the current software locations for all packages are known to the system.
You may want to run sudo apt full-upgrade before doing the ubuntu-drivers command.

For other maintenance stuff all Linux desktops need, check this article:  
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) updated for 2020.

---

### Post by TheFu on 2020-09-12
Are there any errors with:

```
sudo apt update
sudo apt full-upgrade
```

Please show the command and relevant issues. Use 'code tags' please. We don't need to see 200 lines of the same good or bad stuff, just the transitions between different types of good/bad output.

---

### Post by drphd1 on 2020-09-15
As suggested, ran the ```
sudo apt update
``` and ```
sudo apt full-upgrade
```. 

Got this

Fetched 945 MB in 14min 52s (1,059 kB/s)                                       
E: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.4-1build1_amd64.deb](http://pk.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.4-1build1_amd64.deb)  403  Forbidden [IP: 91.189.91.39 80]
E: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/main/v/vim/xxd_8.1.2269-1ubuntu5_amd64.deb](http://pk.archive.ubuntu.com/ubuntu/pool/main/v/vim/xxd_8.1.2269-1ubuntu5_amd64.deb)  403  Forbidden [IP: 91.189.91.39 80]
E: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.1.5-0ubuntu1_amd64.deb](http://pk.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.1.5-0ubuntu1_amd64.deb)  403  Forbidden [IP: 91.189.91.39 80]
E: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-11_amd64.deb](http://pk.archive.ubuntu.com/ubuntu/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-11_amd64.deb)  403  Forbidden [IP: 91.189.91.39 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I changed several mirrors but the same error.


> **TheFu said:**
> Are there any errors with:

```
sudo apt update
sudo apt full-upgrade
```

Please show the command and relevant issues. Use 'code tags' please. We don't need to see 200 lines of the same good or bad stuff, just the transitions between different types of good/bad output.

---

### Post by TheFu on 2020-09-15
403 errors mean that someone, between you and the other server, is blocking.  Any idea why that might be?  Didn't you write that other systems have these libraries and update fine?  What is it about this specific system which could be blocking the http GET from those locations?

---

### Post by drphd1 on 2020-09-16
Finally, solved the problem. Don't know why all mirrors were giving this problem. I hooked my computer to a 4G Mobile internet and the files downloaded without error. Thanks

---

### Post by ActionParsnip on 2020-09-16
Do you use a proxy for web access?

---

### Post by TheFu on 2020-09-16
In some of my travels, I've been places that filtered the internet, sometimes heavily, but didn't have issues with cellular data providing access. Te reason I ever remember was because some of my own websites were blocked, but only by name. Other sites running at the same IP on the same server worked fine. Found it shocking some of the places where this happened.  Places normally believed to have full access to all the internet, didn't, but otherwise seemed normal.

---

### Post by mastablasta on 2020-09-17
@TheFu it's probably nothing personal, but due to automation.

and yes there is more and more ad-hoc control over internet as well as organised attempt to control information flow to the masses.. it was free once, got a bit too free, now it's controlled, but many times by people who think Facebook & Twitter are internet. 

sometimes it is hard to understand what kind of setup is used. i had similar experience at a conference in my country. i could access company websites fine, my colleague from abroad could not access his office, even though we are the same company. but their server is in another country. he could access other stuff. in the end we used mobile network. it was something in hotel's network. maybe i could check or try a few more options, but without admin access to their windows PC it is impossible.

---

### Post by drphd1 on 2020-09-22
@ActionParsnip No. No proxy.

---

