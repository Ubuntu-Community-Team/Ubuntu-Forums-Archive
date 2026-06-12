---
title: "Catalyst Control Center displays incorrect version information"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by russofris on 2010-10-20
Good afternoon

I have installed Catalyst 10.10 to Ubuntu 10.10 using the following methodology:

```

wget http://someplace/ati-driver-installer-8.783_RC1-x86.x86_64.run
chmod +x ati-driver-installer-8.783_RC1-x86.x86_64.run
sudo ./ati-driver-installer-8.783_RC1-x86.x86_64.run --buildpkg
sudo dpkg -i *deb

```

All is well and good.  I have a system that boots into X and has acceleration.  

```

user@Ubuntu:~/NewCatalyst$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series 
OpenGL version string: 4.0.10243 Compatibility Profile Context
user@Ubuntu:~/NewCatalyst$ 

```

The issue that I face 'may' be a cosmetic one.  When I open the Catalyst Control Center (system->preferences), I am confronted with the following information:

```

Catalyst Version        10.5
Driver Packaging Version     8.723-100406a-099494C-ATI
2D Driver Version     8.78.6
Catalyst Control Center Version     2.13

```

Obviously, the Catalyst version should report 10.10, and the packaging version should report 8.783.  This issue has persisted with each Catalyst installation, beginning with 10.5, all the way up to the current 10.10 RC1. 

Is there something wrong with my installation methodology?  Do other users that update their catalyst drivers experience a similar issue?

Thanx Much,
Frank

---

### Post by Jakub Milkiewicz on 2010-10-22
Hi

Since i am not able to get a nice picture on Samsung FX2490HD (external screen) on my Sony VAIO(radeon 4570)  with Ubuntu 10.10 and fglrx 8.780 (the one coming from maverick repositories)  i have decided to download and install new catalyst driver.
I downloaded the driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx). The driver file full name is ati-driver-installer-10-10-x86.x86_64.run.

I followed instructions as shown in your post, and after successful installation of debs i enabled the driver by  System > Administration > Additional Drivers. 

After reboot i got 

```

milus@milus-SONY:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.10243 Compatibility Profile Context

```

In my ccc console i can see
```

Catalyst Version        10.10
Driver Packaging Version     8.783-101005a-106925C-ATI
Driver Version     8.78.6
Catalyst Control Center Version     2.13

```

I hope this driver installed will give me a good picture with Fx2490hd plugged.

---

