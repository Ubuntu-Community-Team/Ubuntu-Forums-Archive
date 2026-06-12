---
title: "Boot options not working in 7.10 install"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by digbyt on 2007-10-22
I am trying to do a clean install using the latest Ubuntu 7.10 workstation install CD on an oldish Dell Precision 410 MT, but not getting very far so far..

The box has 2 PIII 450MHz cpus, 1024MB ram, 3DLabs Oxygen GVX1 video card, three HDDs on the on-board AIC-780 SCSI controller, and LF-D200 DVD-RAM on the integrated AIC-7880 SCSI controller.

As background, an old Ubuntu 5.04 CD I had lying around installed fine except for the need to tweak the xorg.conf file to get it using the correct driver.

With 7.10 however the system hangs when selecting "Start or Install Ubuntu" the system hangs after printing the message "Loading Kernel 100%". Attempting to select the option to check the CD hangs at the same place. 

I believe the problem is with the SCSI controller, and disabling the 7890 in the bios allows the CD check to run and declares it good. In this mode the Start or install gets further, but results in I/O errors reading from the (scsi) DVD..

The help screens mention a promising boot option under "SPECIAL BOOT PARAMETERS - VARIOUS DISK DRIVES" vis "Certain DELL machines aic7xxx.aic7xxx=no_probe", but the 'Boot:' prompt refered to in the instuctions is no longer there. Using <F6> (Other Options) produces a "Boot Options file=/cdrom/presseed/ubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --"

but it is not clear where in this line the option should go, and wherever I try I end up with the message:
[0.000000] Unknown boot option 'aic7xxx.aic7xxx=no_probe': ignoring
and unsurprisingly the same failure mode follows.. :(

Thus I conclude that the help screens on the install media release are incorrect  and the option that appears should be my salvation is not available. Any suggestions??

---

