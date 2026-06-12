---
title: "&quot;Installing the kernel&quot; -&gt; crash"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by W. Irving on 2008-04-02
Ubuntu just will not install on my laptop (HP Pavilion zd8185). I've tried both the desktop and the alternate CDs. The results are always the same: when the installer reaches "Installing the kernel - retrieving and installing linux-generic..." during the "Unpacking the base system" phase at 82% the computer powers off! Regardless if I do a normal install or just choose to install a command line system.

Additionally, the installers on the alternate CD will not work unless if I set the resolution to 1024x768/16bit. In other cases, this happens: [http://www.youtube.com/watch?v=WC0JcGIEcR0](http://www.youtube.com/watch?v=WC0JcGIEcR0)

Can I find out exactly what is going on at 82%, or is there any other way to install 7.10?

Will try 8.04 beta in the meanwhile.

---

### Post by manishsk on 2008-04-02
Are you installing from a CD?

Looks like your CD is not in good condition. Re-burn a new CD. I did face similar porblem but my PC was not restarting. It got hanged their. I reburnt the iso on a new clean CD and it worked. Try re-writable if you want to avoid wasting one more CD. OR look for option by which ou can install from the .iso on hard disk.

---

### Post by W. Irving on 2008-04-02
> **manishsk said:**
> Are you installing from a CD?

Looks like your CD is not in good condition. Re-burn a new CD. I did face similar porblem but my PC was not restarting. It got hanged their. I reburnt the iso on a new clean CD and it worked. Try re-writable if you want to avoid wasting one more CD. OR look for option by which ou can install from the .iso on hard disk.

It's a valid point - I've used the same CD-RW for both images.
However, I've always made sure Nero verified the CD after burning it, and it passed both times. I'm going to try another CD-RW now though.

---

### Post by dstew on 2008-04-02
Sometimes CD-RW's don't work well. Try a CD-R. Do the CD integrity test from the opening menu after you boot it.

---

### Post by yartow on 2008-04-02
I don't know if it helps any, but I've had the same problem and don't think it has anything to do with burning problems. 

I've tried three versions, Edubuntu, Xubuntu and Kubuntu and with the former two I got the same results as you; with the latter, the installation seemed to work, though once installed, there were different graphical problems, such as not being able to change the monitor size or wallpaper. I don't know whether those are bad installation problems or pre-release problems. 

Computer Specifications:

Fujitsu-Siemens Amilo 1705 Li
Intel Celeron M, 1.66 GHz
767 MB RAM
80 GB HD

Now the strange thing is that when booting my PC with a Windows Vista DVD it shows me after some clicks that I have approximately 60 GB, while when booting (installing) with the Kubuntu CD it says I have 80 GB. 
So apparently I have a hidden partition of 20 GB. 

Googling further for what this hidden partition is, it seems to be a Windows RunTime Environment, made to restore your system after crashes or something (though I don't see the words "Repair your system" when pressing F8 during boot, but I do see other boot options). 

The link between this hidden partition and the installing of (edu/x)ubuntu is that on another Dell computer, the helpdesk assistent told me that Dell had some stuff pre-installed on the computer, so partitioning was not always possible.
Perhaps it's the same with Fujitsu-Siemens and this hidden partition is preventing us to install Ubuntu versions. Somehow, Kubuntu gets through this, though. 

Hope someone knows some more about this.

---

### Post by W. Irving on 2008-04-02
Nothing was ever wrong with the CDs. I got tired of 7.10 and burned 8.04 to the very same CD the previous version failed with. I'm happy to announce that 8.04 installed perfectly.

The hard drive was also completely empty, so for me that was not the issue. Most manufacturers, perhaps also Vista does this by default, do add a restore partition. Anyway, such was not the case with my laptop.

---

