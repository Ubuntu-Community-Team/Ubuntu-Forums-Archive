---
title: "Installed Win7 after Ubuntu 14.04; process to get to dual boot"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by G_M_Hardy on 2015-02-23
Installed Win7 after Ubuntu 14.04; here's the process used to get to dual boot


Did the following:
 -- Installed Ubuntu 14.04
 -- Partitioned drive
 -- Installed Windows 7
result:  can only boot into Windows 7


Next, downloaded and ran boot-repair (note: must boot from USB)
    sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair && boot-repair
 --  did "Recommended repair"
     (ref: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))
result:  can only boot into Ubuntu 14.04
 
Next, followed Mark Phelps instructions to regain dual-boot
     (ref: post #4 of [http://ubuntuforums.org/showthread.php?t=2215230](http://ubuntuforums.org/showthread.php?t=2215230))
 -- verified presence of Boot directory in Win7 partition (yes)
 -- verified no second boot directory in Win7 partition (yes)
 -- ran
sudo update-grub 
    (did not find Win7 loader files)
 -- ran "Startup Repair" 3x from Win7 install media
result:  can only boot into Ubuntu 14.04


Next, re-ran: sudo update grub
result:  found 4 kernels (vmlinuz-3.13.0-45,43, 40, 32), but NO Win7


--- I got to this point following existing forum recommendations.  Here's what I did that solved the problem (my apologies if someone else has already posted this):


Next, re-ran:  
    boot-repair
 -- advanced options: GRUB location: OS to boot by default:
    changed to:  Windows (via sda5 menu)   <-- note that this was an option
    apply
 -- then follow instructions in boot-repair to enter following:
    sudo dpkg --configure -a
    sudo apt-get install -fy
    sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
    sudo apt-get install -y --force-yes grub-pc linux-generic
result:  boot successfully repaired


reboot system
result:  success.  Grub offers Linux and Windows 7 dual boot.
 Hope this helps someone save some time figuring this out.

---

