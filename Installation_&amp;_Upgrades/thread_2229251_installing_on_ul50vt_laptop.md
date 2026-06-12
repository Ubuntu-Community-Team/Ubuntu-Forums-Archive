---
title: "installing on ul50vt laptop"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by zenmatrix on 2014-06-12
Has anyone installed any version of ubuntu on the Asus ul50vt , or more the ul50vt-rbbbk05 model. I try every year or so but run into problems with the nvidia driver and performance issues and windows turns out to be just the better bet. Just looking for tips or anyhting as I think I'm going to try it again.

---

### Post by rahul4557 on 2014-06-12
Clean install Ubuntu 14.04 64bit
after install perform an update
> sudo apt-get update

goto to Settings > Softwares & Updates > Select "Additional Drivers" Tab 

Select only the NVIDIA Binary Driver (Proprietary, Tested)
Click on Apply Changes


I had faced issues when i tried installing Ubuntu 14.04 32bit and installing NVIDIA drivers..so later downloaded 64bit later and now everything is working fine.

---

### Post by oldfred on 2014-06-12
With nVidia you will need nomodeset to get into install after first boot.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

