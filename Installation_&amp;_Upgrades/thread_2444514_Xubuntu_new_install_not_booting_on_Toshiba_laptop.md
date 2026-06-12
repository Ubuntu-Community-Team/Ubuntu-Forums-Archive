---
title: "Xubuntu new install not booting on Toshiba laptop"
date: 2020-05-31
forum: Installation &amp; Upgrades
---

### Post by hannahldr on 2020-05-31
I created a bootable USB with 64-bit xubuntu 16.04 LTS a few years ago and used it to put xubuntu onto an ASUS laptop at the time with no problems.
I have now tried to put it onto a Toshiba Satellite C50 - no hard drive partitions.
It boots from the USB fine and seems to run through the install. However, when it restarts it just boots from the USB still even though I changed the boot order back to HDD.
When I remove the USB it gets stuck on the Toshiba start up image and doesn't boot at all.

---

### Post by GhX6GZMB on 2020-05-31
Did you format the partition(s) during install? You should normally format as ext4.
After the install is through, it normally prompts you to remove the installation media (USB stick)

That apart, 16.04 LTS is not really up to date, 20.04 LTS is there now.

---

### Post by hannahldr on 2020-05-31
> **ml9104 said:**
> Did you format the partition(s) during install? You should normally format as ext4.
After the install is through, it normally prompts you to remove the installation media (USB stick)

That apart, 16.04 LTS is not really up to date, 20.04 LTS is there now.

Thank you - I didn't't do anything with the partition before installing as there is only one partition present... how can I rectify this now as the laptop will only boot from the usb?

---

### Post by Autodave on 2020-05-31
If you are using the entire disk, then you do not need to specify the partitions or anything else.  I would start with d-ling 20.04 since there are many newer drivers in that than in the 4 year old OS you are trying to make work.

---

### Post by GhX6GZMB on 2020-05-31
> **hannahldr said:**
> Thank you - I didn't't do anything with the partition before installing as there is only one partition present... how can I rectify this now as the laptop will only boot from the usb?

You don't need to do anything before the install. After landing on the live desktop and starting the install, the installer will suggest that you format the HDD. In that case, select ext4.

Any error messages?

---

### Post by oldfred on 2020-06-01
Did you install in one boot mode, UEFI or BIOS, but system is set to boot in other mode?

Not sure if this model is similar or not:
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering,  found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again.

---

### Post by hannahldr on 2020-06-05
Thanks for the replies - I created a xubuntu 20.04 bootable usb and loaded this onto the laptop. All went well and the OS worked immediately after installation with usb removed. However, tried to turn laptop on the next day and back to square one - not booting at all. Stuck on the toshiba startup page...
I've seen some of the other threads mention NIC - how do I go about changing this when the furthest I can get on the computer is the BIOS menu?

---

### Post by oldfred on 2020-06-05
The link above was just to prevent it from trying to boot from network first, not USB. But then you turn network back on in UEFI/BIOS.

Do settings in UEFI match your install? UEFI or BIOS boot?
Have you updated UEFI to latest available from Toshiba?

---

