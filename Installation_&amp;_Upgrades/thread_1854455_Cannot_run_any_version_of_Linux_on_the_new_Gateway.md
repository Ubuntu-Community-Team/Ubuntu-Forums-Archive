---
title: "Cannot run any version of Linux on the new Gateway computer"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by dnguyen1963 on 2011-10-04
Hi,

I just bought a new computer: 

Gateway DX4860-UR21P
Intel Core i7 processor 2600
Windows 7 Premium 64 bit
8 GB RAM, 1.5 TB HD
NVIDIA GeForce GT520 1GB
LAN - both integrated and wireless

Problems:

1.  None of the Linux Distros recognizes the graphic card - All I get is a low resolution when running live CD.

2.  Installed Ubuntu 10.04 LTS anyway hoping that after the installation Ubuntu will be able to find the appropriate driver for the graphic card - No luck!

3.  Attempts to change the resolution resulted in a message that the monitor is unknown to the system.  I have used this monitor with my old computer without any problem.

4.  Internet is painfully slow - It takes more than three minutes to open a web page.

The system is running fine under W7.  I am at a lost.  I have been trying to figure out the problem, but with little luck so far.  I would appreciate any help troubleshoot these problems.

Thank you!

---

### Post by collisionystm on 2011-10-04
Run a live cd of 11.10 daily build. The new kernel may provide the drivers you need to function.

---

### Post by collisionystm on 2011-10-04
Oh and try fedora 15. It works great for me at times when ubuntu fails.

---

### Post by dnguyen1963 on 2011-10-04
> **collisionystm said:**
> Run a live cd of 11.10 daily build. The new kernel may provide the drivers you need to function.

Yes, I did try this version already...same problems.

---

### Post by dnguyen1963 on 2011-10-04
> **collisionystm said:**
> Oh and try fedora 15. It works great for me at times when ubuntu fails.

I have not tried Fedora in a long time, but did try Fuduntu without any luck.

---

### Post by PhilGil on 2011-10-04
You could download the newest drivers from the NVIDIA site [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us). Don't they'd work with a live CD, though, you'd probably have to do a HDD install of Ubuntu to test.

---

### Post by dnguyen1963 on 2011-10-05
> **PhilGil said:**
> You could download the newest drivers from the NVIDIA site [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us). Don't they'd work with a live CD, though, you'd probably have to do a HDD install of Ubuntu to test.

Thank you...will do that tonight.  I tried Fedora 16 live CD last night and, interestingly, internet speed was back to normal.  I still do not understand why other distros had speed problem with my computer.  I wonder if it is because both wired and wire-less were on at the same time.  Although all of them selected wired Ethernet as default.

---

### Post by dino99 on 2011-10-05
you will be only able to run with the latest kernel (oneiric) + 285.05 nvidia driver (xorg-edgers ppa)

---

### Post by dnguyen1963 on 2011-10-05
> **dino99 said:**
> you will be only able to run with the latest kernel (oneiric) + 285.05 nvidia driver (xorg-edgers ppa)

I did try the latest kernel, but could not get the internet to work.  Firefox could get to a main website, e.g. CNN.com, but then it would just sat there when I tried to open anything.  Everything else on the computer, except for the low resolution graphic, was working ok.

I had the same problem for the following distros:  All version of Ubuntu, Opensuse, PCLinuxOS, MacPuppy, all version of LinuxMint, Fuduntu, ArtistX, Scientific Linux, and a few other ones.

---

### Post by fuduntu on 2011-10-05
> **dnguyen1963 said:**
> I have not tried Fedora in a long time, but did try Fuduntu without any luck.

If you try Fuduntu again, try enabling our testing repository and then doing a yum update.  We are testing a lot of new packages including the most recent Xorg backported from Fedora 16.

---

### Post by jawilljr on 2011-10-05
> **dino99 said:**
> you will be only able to run with the latest kernel (oneiric) + 285.05 nvidia driver (xorg-edgers ppa)

X-Swat and 280.13 will work...[Source](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html).

Me wouldn't touch xorg-edgers unless I absolutely had to.  It is bleeding-edge on steroids. Me I prefer stable.

Jerry

---

### Post by dnguyen1963 on 2011-10-06
Ok, boot the computer up with live CD Fedora 15 and the internet connection became a snail again.  Boot Fedora 16 beta and internet became normal.  I have not install this version of Fedora yet.  I'll try to work on this problem again when I get back in town in about 2 wks.

---

### Post by MAFoElffen on 2011-10-06
> **dnguyen1963 said:**
> I did try the latest kernel, but could not get the internet to work.  Firefox could get to a main website, e.g. CNN.com, but then it would just sat there when I tried to open anything.  Everything else on the computer, except for the low resolution graphic, was working ok.

I had the same problem for the following distros:  All version of Ubuntu, Opensuse, PCLinuxOS, MacPuppy, all version of LinuxMint, Fuduntu, ArtistX, Scientific Linux, and a few other ones.
IMHO - The graphics problem seems to me a separate issue from your networking/internet problem.  Is your GPU now recognized with the "newest" driver?  

Separately- can you ping other sites and notice the timings of that? Compare those same timings to same under your Windows install... Could it be that your Win install is going through wired and Your Ubuntu install is going wireless?  (becuase of a driver issue or such) Just curious on that...

---

### Post by dnguyen1963 on 2011-10-10
> **MAFoElffen said:**
> IMHO - The graphics problem seems to me a separate issue from your networking/internet problem.  Is your GPU now recognized with the "newest" driver?  

Separately- can you ping other sites and notice the timings of that? Compare those same timings to same under your Windows install... Could it be that your Win install is going through wired and Your Ubuntu install is going wireless?  (becuase of a driver issue or such) Just curious on that...

Ubuntu is telling me that it uses the wired Ethernet, but both wired and wireless are active at the same time.  I suspect that this might be the problem.  I have not had the time to open up the computer to see if I just can remove the wireless card.  The graphic and internet problems are probably related.  I have had problems in the past with Linux when incorrect graphic driver was used resulting in snail-pace for everything.

---

