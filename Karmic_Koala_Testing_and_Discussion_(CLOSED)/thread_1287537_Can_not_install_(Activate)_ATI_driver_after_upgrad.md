---
title: "Can not install (Activate) ATI driver after upgrading to Karmic Beta."
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-10
I upgraded to karmic beta and now I want to install the ATI driver for my graphic card.
I tried using System>Administration>Hardware Drivers and then I select the ATI/AMD proprietary FGLRX graphic driver and pressed the activate button. It asked for password and then nothing happened.

It didn't install the driver, I tried the same procedure more than once without any luck.

Is there any command line thingy for installing the restricted drivers from repositories?


Thanks.

---

### Post by Mark Phelps on 2009-10-10
Your post is confusing because your sig says you're using an Nvidia card -- which of course, will not use ATI drivers.

But, to install the ATI drivers from the command line, download the Linux drivers from the AMD site.  They have instructions for installing the drivers several different ways contained in the download.

---

### Post by legolas_w on 2009-10-10
Hi,
Thank you for mentioning my signature. I fixed it.

When I had 8.10 I tried installing the driver manually and that cause fair amount of headache for me. 
problem happened when I updated the kernel version which cause my computer to render un-usable as the driver were installed for older kernel and not the new one.

I am looking for a way to use proper channel to install the driver.

I searched in the web and I find some commands and tried them to install the driver.

```
sudo apt-get install xorg-driver-fglrx
```

I tried the code and it is telling that the driver is already installed.
I will update this thread as I continue looking for a solution.

Thanks.

---

### Post by pme 72 on 2009-10-10
You probably need to uninstall the old fglrx driver before installing a new one.

---

### Post by Mark Phelps on 2009-10-10
To see if the ATI driver is installed, open a terminal and enter "fglrxinfo".

---

### Post by legolas_w on 2009-10-10
It looks like that there is no driver for the current kernel version.

[http://grelbar.net/archives/271](http://grelbar.net/archives/271)

The above blogger explains that we may need to wait more before we could use ATI drivers in Karmic.

Thanks

---

### Post by bapoumba on 2009-10-10
Moved to Karmic.

---

### Post by cariboo on 2009-10-10
Is the driver actually getting downloaded, look in /var/cache/apt/archives to see if the driver has completely downloaded.

The deb you are looking for should start with fglrx-amdcccle.

---

### Post by alphacrucis2 on 2009-10-11
You can't use the Catalyst (9.9) driver from the ATI site as it doesn't work with the Karmic kernel. You need to use the 9.10 driver which is only available via the Ubuntu repos as it is a pre release that ATI made available to Ubuntu.

---

### Post by legolas_w on 2009-10-11
> **cariboo907 said:**
> Is the driver actually getting downloaded, look in /var/cache/apt/archives to see if the driver has completely downloaded.

The deb you are looking for should start with fglrx-amdcccle.

Thank you all for helping me out.

A file exactly named: fglrx-amdcccle_2%3a8.660-0ubuntu3_i386.deb is inside the directory you mentioned. the size is 7.4 MB.

what should I do from here? Is there some log file to study and find what is going wrong?

Thanks

---

### Post by legolas_w on 2009-10-11
Maybe I should purge everything related to ATI and start again?
I do not know exactly which packages are safe to be purged, can you please let me know?

I once purge all fglrx and AIT related packages using synaptic and that ended with Hardware Drivers window not showing any selectable driver item :D

Thanks

---

### Post by the_master on 2009-10-26
> **legolas_w said:**
> Hi,
Thank you for mentioning my signature. I fixed it.

When I had 8.10 I tried installing the driver manually and that cause fair amount of headache for me. 
problem happened when I updated the kernel version which cause my computer to render un-usable as the driver were installed for older kernel and not the new one.

I am looking for a way to use proper channel to install the driver.

I searched in the web and I find some commands and tried them to install the driver.

```
sudo apt-get install xorg-driver-fglrx
```

I tried the code and it is telling that the driver is already installed.
I will update this thread as I continue looking for a solution.

Thanks.
I am having the same problem as you except my download box shows up but stops loading half way through.  I inputed the code above in terminal and got this
```
The following extra packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source patch
Suggested packages:
  diff-doc libamdxvba1
The following NEW packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source patch xorg-driver-fglrx
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```

not sure what it means.  i also ran ```
fglrxinfo
``` and got ```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
fglrxinfo: command not found

```

so i guess mine never even installed.

---

### Post by humphreybc on 2009-10-26
Just chill out till Friday on the radeon opensource drivers. I'm sure once the final version comes out there will be no hiccups with installing the 9.10 driver from the repos using Hardware Drivers.

Reading through that blog post, it seems the blogger had the same problem as I did back on Jaunty with installing anything higher than 9.4. I think this was due to a bug in the fglrx-installer package, you're welcome to Google it and have a look for yourself. Bryce Harrington patched it a couple of days after I submitted a bug report, but unfortunately it was only due for Karmic. Perhaps this blogger hadn't received the updated package at Alpha stage.

---

### Post by legolas_w on 2009-10-27
> **humphreybc said:**
> Just chill out till Friday on the radeon opensource drivers. I'm sure once the final version comes out there will be no hiccups with installing the 9.10 driver from the repos using Hardware Drivers.


Hi
Do you mean that on Friday the open source radeon driver will become final?
I have a RADEON 3470 on my laptop and I wan to play 3d games on ubuntu.

Will that driver support my card?

Thanks

---

