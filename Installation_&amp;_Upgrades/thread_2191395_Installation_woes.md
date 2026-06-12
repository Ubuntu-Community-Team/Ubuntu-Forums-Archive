---
title: "Installation woes"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by tommy2k10 on 2013-12-02
I am trying to install Ubuntu 13.04 - I have tried countless times (32- and 64-bit versions) to install.  It loads initially and then I get 'unable to find a medium containing a live file system'.  I have followed the correct installation process, and still no luck.

I am trying to install it on an AMD 64-bit system with 2.5Gb memory.

There doesn't seem to be the required files on the DVD.  Here's a list:

[B][U]Folders


[/U][/B].disk
boot
casper
dists
EFI
install
isolinux
pics
pool
preseed

[B][U]Files

[/U][/B]autorun.inf
md5sum.txt
README.diskdefines
wubi.exe

Any ideas please?

---

### Post by rackit on 2013-12-02
There is an option on the cd when you boot to verify media - try to run that and see if you have good installation media.

---

### Post by tommy2k10 on 2013-12-03
For some odd reason, when I boot with the CD, I get the screen where that menu is supposed to be, but it's blank!

---

### Post by fantab on 2013-12-03
What graphics do you have on board?
Try the [NOMODSET ]("http://ubuntuforums.org/showthread.php?t=1613132")option at boot, and "Try Ubuntu without installing" first to check how are the other features behaving... once all is good, install from desktop.

Also 13.04 will reach end of support in January next year. So it will be a good idea to install 13.10.

---

### Post by tommy2k10 on 2013-12-03
I have NVidia NForce 430.
I tried the NOMODERESET option, and I get the same message, except it's slightly bigger!

---

### Post by tommy2k10 on 2013-12-03
That is rather interesting - my main machine has got VirtualBox installed - it installs fine on a VM!
The graphics on my main machine is an NVidia GeForce 7025!
I assigned it 640MB RAM with 16GB HDD.

---

### Post by fantab on 2013-12-03
Download 13.10, burn it to a usb and try again, without and with 'nomodeset'.
Try again....

---

### Post by tommy2k10 on 2013-12-04
It works fine now - I was using an external DVD drive, as my internal one stopped working on and off

---

### Post by tommy2k10 on 2013-12-10
Next problem - I am trying to copy my files back to Ubuntu from my external drive.  However, it copies about 2GB and then cannot copy a file with a long filename, if I click Skip, it skips it, but then it says, for all my other folders 'No such file or directory'.  I have checked by opening up a few of the files in Ubuntu, they open fine!  There is 250GB on the HDD, and it is a 500GB external drive (but it is not even half full).  Any ideas?

---

### Post by tommy2k10 on 2014-01-07
I have finally ironed out my problems!  Graphics were still distorted, sometimes wouldn't boot properly, but went to the Software Center, downloaded the NVidia graphics, and now it's fine!  
Does 13.10 use X.org as the default graphics driver?

---

