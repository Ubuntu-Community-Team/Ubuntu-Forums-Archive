---
title: "Power off leads to restart after upgrade to Ubuntu 22.04 on Dell workstation"
date: 2022-05-11
forum: Installation &amp; Upgrades
---

### Post by trsr on 2022-05-11
Hi,

I upgraded a Dell Precision workstation 3450 that came pre-installed with Ubuntu 20.04 to 22.04. After the upgrade, I am unable to shut down the computer using either the power off option (clicking on the power off/log out button on the top right) or with sudo poweroff. In both cases, the machine simply reboots / restarts. the following lines flash briefly on the console during reboot:

[   25.433431] sd-umoun[2594]: Failed to unmount /oldroot: Device or resource busy
[   25.434705] sd-umoun[2595]: Failed to unmount /oldroot/sys: Device or resource busy
[   25.442580] shutdown[1]: Failed to finalise file systems, ignoring.

This seems to be similar to a problem reported long ago for 12.04 here: [https://askubuntu.com/questions/132882/why-do-i-get-a-reboot-instead-of-a-shutdown](https://askubuntu.com/questions/132882/why-do-i-get-a-reboot-instead-of-a-shutdown) 

I would appreciate any help/suggestions on how to fix this asap.

Thanks,

trsr

---

### Post by trsr on 2022-05-11
Just wanted to add that even this does not work and the computer still reboots ```
sudo shutdown -P
```
The only way to power off seems to be a hard shut down by long-pressing the main power button.
Would appreciate suggestions and help to fix this problem.
Thanks,
trsr

---

### Post by guiverc on 2022-05-13
Also asked at [https://askubuntu.com/questions/1408275/please-help-power-off-leads-to-restart-how-to-shutdown-without-reboot-in-22-04](https://askubuntu.com/questions/1408275/please-help-power-off-leads-to-restart-how-to-shutdown-without-reboot-in-22-04)

-- Duplicate comment given on askubu.

If your system is *detected* as benefiting from an OEM kernel at install; the default kernel is replaced.

 Were you using the OEM kernel before upgrade (*if fully upgraded, a 20.04 system was using 5.4 with the GA kernel stack & 5.13 if using the HWE stack; which were you using? or were you using an OEM kernel stack?*). 

 OEM kernels upgrade to later OEM kernels by default; so I'd not expect you to upgrade to 5.15 *general* kernel.  

If it was me; I'd *boot* live media & see if the issue occurs there, then if different contrast differences with your installed system (*esp. kernel stack related*)

---

### Post by trsr on 2022-05-13
Thanks @ 		guiverc. I am not sure what kernel was installed with 20.04 (how to find out now? from some log file?) It may have been an OEM kernel. As to what I have now, the results of the command ```
dpkg --list | grep linux-image
``` is as follows:
[FONT=courier new]rc  linux-image-5.10.0-1044-oem                5.10.0-1044.46                             amd64        Signed kernel image oem
ii  linux-image-5.14.0-1034-oem                5.14.0-1034.37                             amd64        Signed kernel image oem
rc  linux-image-5.15.0-27-generic              5.15.0-27.28                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-30-generic              5.15.0-30.31                               amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.30.33                               amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04              5.15.0.30.33                               amd64        Generic Linux kernel image
ii  linux-image-oem-20.04d                     5.14.0.1034.31                             amd64        OEM Linux kernel image[/FONT]

Is the shutdown leading to reboot problem due to the kernel or something else? 
~trsr

---

### Post by trsr on 2022-05-13
The problem solved itself after I discarded an old plugged in USB keyboard and pluuged in a new keyboard! Now the computer shuts down properly... no reboot!
Just putting this out here in case others run into a similar issue.
trsr

---

### Post by guiverc on 2022-05-13
I was typing here when I noticed your reply on askubu.  (*my original reply now deleted*)

Well done for solving it, and thanks for sharing it so it'll benefit others who may experience the issue.

*I've experienced like issue(s) before and assumed it was a USB device that was sending bad data.. as scanning input from USB showed lots of repeating rubbish that was mostly ignored.. maybe that slowed/delayed-forever the kernel's shutdown, I don't know as for me it was real cheap USB hubs that I just replaced with better ones.*

---

