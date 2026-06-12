---
title: "ubuntu 10.04 boot from usb in safe graphics mode"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by ethnvine on 2010-05-30
Dear All,
  Wanted to know how to enable boot in safe graphics mode in the bootable USB that I created for 10.04 by following the instructions in the download page.

Currently when I boot from USB and select installation, the monitor goes off. So I guess safe graphics mode is the way to go.

Thanks.

---

### Post by ethnvine on 2010-07-23
The problem is solved, after following these instructions :
The Nvidia 7050PV video IGP on my Biostar TF7050-M2 motherboard has normally been cranky on install of previous versions of Ubuntu so it was not unexpected when it gave me trouble with Ubuntu 10.04 “Lucid Lynx”. On starting my flash drive I was able get to the initial install menu but the normal “Try Ubuntu without installing” option yielded a blank screen when the graphical display manager (gdm) started up. To avoid this I pressed F6 Other Options and selected nomodeset. Then I selected the “Try Ubuntu without installing” option to get to a point where I could install Lucid.
Once I installed Lucid and attempted to restart I found again that there was no video on boot. To avoid this I held the shift key down during startup to enter the grub boot menu. The first option was highlighted (in my case Ubuntu, with Linux 2.6.32-21-generic). I pressed “e” to edit the commands before booting and used the cursor keys to move the cursor down to the end of the “linux /boot/vmlinuz-2.6.32-21-generic root=UUID=xxxxxxxxxxx-xxx-xxx-xxxx-xxxxxxxxxxxxx ro quiet splash” line. At the end of the line I added a space and “nomodeset” (without the quotes) and then pressed Ctrl-x to boot the system.
When the machine started into the gdm and after login, I selected System->Administration->Update Manager and made sure all the updates had been installed. Then I selected System->Administration->Hardware Drivers to install the latest drivers for the nvidia IGP on my motherboard (in my case NVIDIA accelerated graphics driver (version current) [Recommended]). When it finished installing I restarted and the correct driver at the correct resolution was what appeared. As always your mileage may vary.

see : [http://www.seephar.com/2010/04/lucid-video-quirk-on-biostar-tf7050-m2/](http://www.seephar.com/2010/04/lucid-video-quirk-on-biostar-tf7050-m2/)

Thanks.

---

### Post by chenguo4 on 2010-09-20
Oh man your post helped me out majorly. Thank you so much!

---

