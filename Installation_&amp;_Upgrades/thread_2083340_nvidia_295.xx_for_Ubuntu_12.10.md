---
title: "nvidia 295.xx for Ubuntu 12.10"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by Majki-Fajki on 2012-11-12
Does anyone has working deb drivers for nvidia cards for 12.10 from 295.xx family? I literally searched whole internet by now. 


N00bslab has apparantly created debs
[http://www.noobslab.com/2012/06/nvidia-drivers-collection-for.html](http://www.noobslab.com/2012/06/nvidia-drivers-collection-for.html)
 but they need xorg-video-abi which is not in 12.10 repo.

Ideas?

---

### Post by whatthefunk on 2012-11-12
[http://www.geforce.com/drivers/beta-legacy](http://www.geforce.com/drivers/beta-legacy)

You dont need a .deb file.  Just download the drivers from Nvidia, kill your X server, and run the script from the command line.  Beware that you may break your system.

---

### Post by Majki-Fajki on 2012-11-12
But I will still have to reinstall nvidia each time kernel update, right?

---

### Post by Frogs Hair on 2012-11-12
The date of that post concerns me a bit. That site has listed items as being compatible with versions of which they are not. I have found this to be true with their theme ppas. Since it's a deb. package the most that can happen is that the dependencies won't be found and it won't install.

---

### Post by whatthefunk on 2012-11-12
> **Majki-Fajki said:**
> But I will still have to reinstall nvidia each time kernel update, right?

That I dont know about.  I know that Ive never had to reinstall a driver after a kernel update though.

---

### Post by dannyboy79 on 2012-11-12
> **whatthefunk said:**
> That I dont know about.  I know that Ive never had to reinstall a driver after a kernel update though.if a module (driver) is installed its compiled against the currently installed kernel at that time. the nvidia driver from the website in fact does this, it's a script that builds the driver against your current kernel. So, YES, if you're running an nvidia driver from their website that gets installed via their script, it will need to be reinstalled when a kernel upgrade occurs so that it can be compiled against the new kernel.

---

### Post by whatthefunk on 2012-11-12
> **dannyboy79 said:**
> if a module (driver) is installed its compiled against the currently installed kernel at that time. the nvidia driver from the website in fact does this, it's a script that builds the driver against your current kernel. So, YES, if you're running an nvidia driver from their website that gets installed via their script, it will need to be reinstalled when a kernel upgrade occurs so that it can be compiled against the new kernel.

Learn something new every day:)

---

### Post by bogan on 2012-11-12
Hi!, **dannyboy79**, et alia,

YOU Posted: > So, YES, if you're running an nvidia driver from their website that  gets installed via their script, it will need to be reinstalled when a  kernel upgrade occurs so that it can be compiled against the new kernel.That was true for the 295.xxx nvidia drivers and before, but not for 304.xx onwards.

The recent nvidia.com drivers are DKMS compatible, so the kernal module gets updated, just as it does with the Ubuntu ppa nvidia-current drivers.

Chao!, **bogan.**

---

### Post by Majki-Fajki on 2012-11-12
Well, I installed 12.04 again. I really wanted to have 3.4+ kernel :-(

Thanks guys.

---

### Post by dannyboy79 on 2012-11-12
> **Majki-Fajki said:**
> Well, I installed 12.04 again. I really wanted to have 3.4+ kernel :-(

Thanks guys.if you really wanted the 3.4+ kernel then why did you give up?

---

### Post by Majki-Fajki on 2012-11-12
Well, my GPU is old and has almost no performance on 300+ drivers. So I need to have 295.xx

I could not find working .deb of them for 12.10. Sure - some random packages hosted at some weird places, but no official PPA. Using .run drivers gave me problems, dunno why. 

I guess I will have to wait for 12.04.2 to get this bug fixed [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/610440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/610440)

---

### Post by dannyboy79 on 2012-11-12
tell us what the errors are when trying to compile the nvidia 295.xx driver? Also, what is your exact graphics chipset?

---

### Post by Majki-Fajki on 2012-11-12
Well, I had classy "fatal screen no found". Ofc xorg.conf configured properly. I used 295.71 driver from nvidia's webpage.

But like I said, I went for cheap solution and installed 12.04 again.

---

### Post by whatthefunk on 2012-11-12
What graphics card are you using though?  You probably have to try a few different 295.xx drivers to find a working one.  At least thats been my experience.

---

