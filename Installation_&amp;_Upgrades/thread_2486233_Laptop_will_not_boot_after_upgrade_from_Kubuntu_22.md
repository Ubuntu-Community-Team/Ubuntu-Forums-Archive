---
title: "Laptop will not boot after upgrade from Kubuntu 22.10 to 23.04"
date: 2023-04-23
forum: Installation &amp; Upgrades
---

### Post by jlynde on 2023-04-23
Yesterday the laptop (a Dell m6800) was running Kubuntu 22.10 just perfectly.  After applying all of the latest updates using the Discover application I got a popup suggesting that I should upgrade to 23.04.  It sounded like a good idea at the time so I went ahead and clicked.

Unfortunately, after the process was complete (which seemed like it took a few hours) the laptop will no longer boot.  I see the blue highlighted flashing "Ubuntu" on the splash screen for a few seconds, then I get some messages like this:

ERROR: Unable to locate IOAPIC for GSI 37
ERROR: Unable to locate IOAPIC for GSI 38
usb 1-1.6: device descriptor read/64, error -32

And that is where it stops.  It is stuck there.

At first I thought maybe the laptop could not support the kernel so I created a USB Thumb Drive from the Kubuntu 23.04 ISO but that boots and runs fine.  I also ran the complete BIOS Diagnostics on the laptop and everything worked.  So I know there is no hardware issue and I know that Kubuntu 23.04 CAN run on this laptop (at least from the Live-CD / thumb drive).

From the Live-CD I tried the "Install" option and was hoping that I would get a "Repair" option like I have seen mentioned on some web pages but I only get an option to do a clean install.  And if I click through to the "Disk" options there is only one drive listed there and it is NOT the one that I want to use (it is a drive that has a separate - still bootable - Kubuntu 22.10 install on it).  

Can anyone offer some suggestions for how I can try to get my system to boot again please?

Thanks,
John

---

### Post by oldfred on 2023-04-23
See these, full cold boot to get UEFI to recognize all hardware or boot parameter:
[https://ubuntuforums.org/showthread.php?t=2483019&p=14127231](https://ubuntuforums.org/showthread.php?t=2483019&p=14127231)
[https://askubuntu.com/questions/832152/how-to-solve-usb-error-at-start-up](https://askubuntu.com/questions/832152/how-to-solve-usb-error-at-start-up)

Something new & different plugged into USB port?
To see USB devices:
lsusb

---

