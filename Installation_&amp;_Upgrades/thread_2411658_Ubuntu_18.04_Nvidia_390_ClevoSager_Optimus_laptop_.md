---
title: "Ubuntu 18.04 Nvidia 390 Clevo/Sager Optimus laptop cannot get Nvidia properly going"
date: 2019-02-02
forum: Installation &amp; Upgrades
---

### Post by {CGL}ToWeR on 2019-02-02
Hi
Ive spent weeks, trawling and retrying and reinstalling so much, this has tested me.
I have a Clevo Metabox PA71ES-G 17.3" optimus laptop with i915 and Nvidia GTX 1070 (chipset 106M), UEFI secure boot off in bios

The best outcome I got was :
1. fresh install 18.04 live usb downloaded Nov 2018
2. Set nomodeset in grub as it was freezing on trying live / installing
3. install with internet connection, but not download/update anything, do not use proprietary drivers
4. finish install, boot ok
5. got to new tty console ctrl alt f2, $ sudo service stop gdm
6. $ sudo add-apt-repository ppa:graphics-drivers
7. $ sudo apt update
8. $ sudo apt install nvidia-390, installs ok, reboot

At this point I get nvidia settings on next boot into successful desktop. I see a full nvidia-settings, prime selected intel is set.

9. I switch to Nvidia on prime select in nvidia-settings, then log out and log back in and I get a login loop issue.
10. I try editing /etc/gdm3/custom.conf and enable waylandenable=false line, no change
11. I try $ sudo apt install lightdm, and switch to lightdm, no change but does show more login screen than gdm. But same effect, put in password, blank screen, back to put in password screen.
12. I keep lightdm configured. I update grub with "nogpumanagement" and update-grub, reboot. No change. Then I try in grub "nvidia-drm.modeset=1", no change. 
13. Only temp fix back to at least a screen is in grub "i915.modeset=1" but Nvidia will not be loaded in kernel.

14. I try purging Nvidia $ sudo apt purge nvidia-*, and reinstall $ sudo apt install nvidia-390, and I get even less nvidia-settings the second time around. All I see now in Nvidia is Prime settings, and nothing else - no screen, no GPU info, nothing.

I am pretty sure a newer Nvidia will not work. I started on 415 and worked backwards in another install on same machine and had the same effect - nvidia-settings only showing Prime options, nothing else, and even though it says I can switch to Nvidia, it gets the login loop issue, or login hang issue.

What is going on? Why can I not get to the same state as fresh install and first ppa install of Nvidia 390?

---

