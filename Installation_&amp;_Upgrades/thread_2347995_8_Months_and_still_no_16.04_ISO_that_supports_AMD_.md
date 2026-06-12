---
title: "8 Months and still no 16.04 ISO that supports AMD APU"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by cmoore580 on 2016-12-30
After 8 months and known problems why did they not release a iso ( for 16.04 LTS) that will give you any monitor output on an AMD APU machine. I find this hard to understand. Does anybody have any fix. How are you supposed to even make modifications when it boots to a black screen. I cant be the only one.

---

### Post by QIII on 2016-12-30
Hello!  The iso is frozen at release time.  16.04 has not changed.

16.04.1 has been released.  Have you tried that?

What model is your APU?

---

### Post by cmoore580 on 2016-12-30
I currently have an A10-7870K running on a Gigabyte F2A88XM-D3H. Thanks for any help. Just downloaded again today. I have to check what that was.

Update: download was ubuntu-16.04.1-desktop-amd64.iso

---

### Post by oldfred on 2016-12-30
Most must work as this site runs comparisons.
 AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)
How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)
Note Beta driver and limitations/issues
[http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx) 

      
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  

      
 AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016
Also needs  X.Org Server 1.19
[http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates)
Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

---

