---
title: "Upgraded from 16.04 to 18.04 &amp; now boot fails"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by john-t-erskine on 2018-08-22
My upgrade seemed to go fine until the reboot portion. Then I encountered an error that prevented me from getting to the splash screen. A live version of 16.04 worked, but 18.04 live would not. I discovered that the issue was the result of an outdated version of my HP bios. I have updated my bios and the boot now gets to the splash screen and hangs. Booting into recovery works now and live booting 18.04 works. When I boot verbose I see that the error now is ```
modulenotfounderror no module named 'distupgrade'
```. I have my /home and /usr setup on individual partitions and am trying to back them up in a live version of 18.04, but I can not get it to recognize my usb drive. 

I don't particularly want to re-install and certainly not if I can't back up my /home and /usr before the attempt. Any help is greatly appreciated.

---

### Post by dwilde1 on 2018-08-22
I had a scary warning message, so I haven't rebooted.

Could not install 'systemd'

The upgrade will continue but the 'systemd' package may not be in a working state. Please consider submitting a bug report about it.

triggers looping, abandoned

Did you see this, John? systemd is your startup command sequencer. If that doesn't work nothing else will.

---

