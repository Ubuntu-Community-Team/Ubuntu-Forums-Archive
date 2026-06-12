---
title: "No Video Output After Natty Clean Install with AMD-64 Alternate"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by linux4me on 2011-04-28
I have a Gigabyte 6A-M61P-S3 with an nVidia chipset, and I'm using the built-in graphics rather than a discrete graphics card. Ubuntu 10.10 and previous releases ran flawlessly on it using the nouveau drivers. 

I tried doing an upgrade to 11.04 using the Alternate AMD-64 CD, and it seemed to complete successfully, but when it came time to reboot, I had no video output at all after the BIOS screen. This is a test machine, so I went ahead and did a clean install using encrypted LVM with the Alternate AMD-64 CD after confirming that 64-bit 11.04 ran fine using the Live CD.

The installation went fine, but the first reboot flashed a brief "error: no video mode activated" and then I lost all video output. Subsequent reboots didn't give me any error message, but I had no video output.

I suspect there are some boot parameters that would have gotten the nouveau driver working, but I wanted to try Unity, so I rebooted to get the Grub menu, chose Recover Mode, selected failsafe graphics, and got to the Desktop, then installed the proprietary nVidia driver (current) and once I rebooted everything was golden.

Hope this helps someone else...

---

### Post by hojjat on 2011-05-06
Thank you for sharing this information.

I recently installed Natty with encrypted LVM and it worked fine until I installed the AMD driver for the ATI graphic card. Since then, it says "error: no video mode activated" on the boot time, and the splash screen where I have to input the passphrase for the LVM partitions looks awkward (large fonts, not full screen) but after I input the passphrase and OS is loaded completely, everything is fine.

I searched online but to no avail. Someone said he received a similar error because fonts were not available to GRUB at the boot time ([link](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)). This might be my problem too, because the fonts in /usr/share are not available to GRUB at the boot time, because /usr is located inside the encrypted partitions. However, I don't know how to make the fonts available to GRUB, and I'm not even sure if this is my problem.

Any advice would be appreciated.

---

### Post by linux4me on 2011-05-06
I believe the "error: no video mode activated" is a separate issue from your scrambled pass phrase screen in Plymouth. There is [a bug logged on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802") regarding the error that I found since posting here that you might want to take a look at.

As for the low-resolution Plymouth screen, [take a look at this tutorial]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/"), which includes a handy script that will help you put in place a workaround to fix the Plymouth resolution when you're using a proprietary ATI driver.

---

### Post by hojjat on 2011-05-06
Thank you for sharing that link. It worked for me smoothly! I have the graphics back in the passphrase screen at the boot time.

---

