---
title: "No sound on Gutsy upgrade? Check you kernel packages."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by ArtInvent on 2007-12-19
I like many other people ran into sound problems after a Gutsy upgrade. Sound card absolutely not recognized, unable to even start alsa-mixer at all. I have an Asus M2NPV-VM mobo with onboard sound from a SoundMax AD1986a audio chip. When I ran alsamixer it returned the error** alsamixer: function snd_ctl_open failed for default: No such device**.

After pulling my hair out, going through all the forums, messing with alsa drivers packages, reinstalling, messing with config files etc. etc. I had no luck. It seemed that all was as it should be yet the kernel was simply somehow not recognizing the hardware at boot. Plus I knew that my sound card works fine in Ubuntus past. Yet I was starting to think that a wipe and fresh install was the only solution. Ye gads, anything but that.

I rebooted and in Grub booted to one of the earlier Gutsy kernels. This made sound work fine again but the graphics display would not use the correct nVidia driver. I guess you have to install and enable the proprietary driver for each kernel which is about as much fun as a frozen mudbath. This seemed like a worse problem than no sound so I went back to the latest kernel. 

In Synaptics I checked all the installed kernels and their packages. These are all grouped under** linux-  linux-image  linux-headers** etc. The kernel that boots up after the upgrade defaulted to 2.6.22-14-386 but in checking the packages there was no linux-headers package installed for that kernel. I installed the package** linux-headers-2.6.22-14-386** and rebooted, but still no luck. In perusing the installed packages I saw that there was a meta-package called linux-386 that installed some other related kernel packages for the latest 386 kernel. So I thought, what the hell, worth a try. Installed, rebooted, presto, sound is back in full, graphics are perfect.

So the lesson is, check your kernel version with command ** uname -r** and make sure you have all the right kernel headers and packages installed. Find the kernel you are using and then make sure the package billing itself as the 'complete Linux kernel' for that is installed. Hope this helps someone, and that my hair grows back soon.

---

### Post by legalizemeth on 2008-03-20
Thank you most kindly.  I had the same problem, with the same motherboard, and this took care of it.

---

