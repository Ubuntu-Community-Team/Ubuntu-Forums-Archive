---
title: "Install Ubuntu on integrated SSD currently used for Intel RST?"
date: 2017-06-04
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2017-06-04
Currently, I have Windows 8.x , Ubuntu 16.04LTS, and Mint 18 installed on 500GB HD. All is ok.
My laptop also has an 32GB integrated mSATA SSD (that I think is on the motherboard) that appears to have Intel Rapid Storage Technology on one partition, and about 23GB of free space.

Can I install Ubuntu onto SSD without fear of causing Windows or Ubuntu boot issues? I'm ok if Windows no longer uses the Rapid Storage Technology, if the only penalty is using Windows is slower.  If I can, should I install on the 23GB partition next to Intel RST, or just blow away the Intel RST partition and use all of the SSD?

---

### Post by oldfred on 2017-06-04
Some have just converted entire SSD to Ubuntu as it only is for booting Windows and does not otherwise speed it up.
Some also noted that the amount used was the RAM size and rest unused. Then they installed Ubuntu into that remaining space.

These threads are now all older. Some of issues should have gone away with newer Ubuntu.
 [http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
SRT Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[URL="http://ubuntuforums.org/showthread.php?t=2090605"]http://ubuntuforums.org/showthread.php?t=2090605
[/URL]
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491) 

Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by aeronutt on 2017-06-04
Most excellent, thanks!  Thanks for the input and supporting threads.  I also found this thread elsewhere.
[https://superuser.com/questions/459578/ubuntu-on-an-xps-14-ultrabook-with-msata-cache-and-500gb-hd-how-to-partition-f#460051](https://superuser.com/questions/459578/ubuntu-on-an-xps-14-ultrabook-with-msata-cache-and-500gb-hd-how-to-partition-f#460051)

I'll probably give this a go, then if successful, report back.

---

### Post by aeronutt on 2017-06-04
Update:
I've disabled SRT on Windows 8, and disabled SRT in the BIOS. After this, the install iso sees the mSATA SSD! Cool.
However, if in BIOS I change 'SATA operation' from 'Intel Smart Response Technology' to ACHI, Windows will not boot. So it appears that SATA operation must stay as iSRT.
If I reformat the mSATA and install Ubuntu, will having SATA set as iSRT in BIOS be a problem?

---

### Post by oldfred on 2017-06-04
Some Dells have RAID and have to change to AHCI also.
In those cases you have to install the AHCI drives in Windows before converting drive to different mode.

This discusses it, but I do not think it has generic details on installing AHCI driver in Windows.
 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 



Some info here.
[URL="https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html"]https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html
[/URL] [https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 

[URL="https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html"]
[/URL]

---

### Post by aeronutt on 2017-06-06
Update, all is good and (mostly) working!
- tried a few of the posted methods to get Windows8 to use AHCI for SATA, but all failed.
- in the end, in BIOS I left SATA as intel Rapid Storage Technology 
- deleted all partitions (which contained the iRST software) on mSATA SSD, and loaded Ubuntu onto mSATA SSD
- had some difficulty getting Grub to recognize both disks and all OSs properly, but it's now working!
- I ran boot-repair from mSATA SSD Ubuntu load; Grub is loaded at sda1 (/boot/EFI), recognizes all OSs across 2 disks, including W8 on sda and my Ubuntu on SSD mSATA at sdb
- Windows boots fine.
Marked solved.

Thanks for your help oldfred !

---

### Post by oldfred on 2017-06-06
Glad you got it working.

Windows on major updates will probably turn on fast start up and also make itself first in boot order. Then you will not be able to boot Windows from grub until you turn off fast start up.
You should be able to directly boot Ubuntu from UEFI, and if fast start up on & you cannot boot Windows from grub you should still be able to directly boot from UEFI boot menu. 
But best to always have both a Windows repair flash drive and Ubuntu live installer to use for repairs.

---

