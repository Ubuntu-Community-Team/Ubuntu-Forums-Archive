---
title: "Ubuntu 14.04 Booting Problems"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by PattersonR on 2014-05-06
Hello,

I recently installed 14.04 on my laptop and am having issues booting. I just tried to boot this morning and it starts repeating "19~^" and then goes to the Ubuntu screen and just starts flashing with repeating, indecipherable codes. I am able to go to recovery and boot that way, but when it goes back to the flashing screen whenever I reboot. Any help is greatly appreciated, thanks!

---

### Post by oldfred on 2014-05-06
What computer & model?
What video card/chip does it have?
It may need video driver or boot parameters to boot correctly.
Recovery mode automatically uses nomodeset, but that usually is a temporary fix until correct video driver is installed.

See if adding nomodeset to boot works like it does with recovery.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by PattersonR on 2014-05-06
I have a Toshiba e205 with Nvidia GeForce 310M + Intel GMA HD. Everything was working fine until last night and the last program I installed was Packet Tracer.

---

### Post by oldfred on 2014-05-06
No idea what Packet Tracer is, but that should not have changed anything.

But did you install video drivers or updates to video drivers or change UEFI/BIOS to boot using a different video mode.
With dual video are you using the latest nVidia driver or Bumblebee?

 Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

---

### Post by PattersonR on 2014-05-06
I just issued the command: sudo apt-get remove --purge nvidia-*    and am now able to log on to the machine. However, it still hangs on the ubuntu screen and flashes while displaying scrolling codes for about ten seconds and then allows me to log on. Which should I install, Bumblebee or Optimus, to see if it fixes the problem?

---

### Post by oldfred on 2014-05-06
If you are using nomodeset in place of splash quiet the scrolling codes is normal boot.

Do not know about your system if one or the other is better video.

---

### Post by ubfan1 on 2014-05-06
Are you using a USB keyboard?  Sometimes a sticky key can cause such a problem.

---

### Post by PattersonR on 2014-05-06
I am not using a USB keyboard. However,I just installed Bumblebee and am now able to bypass the flashing screen by pressing enter. I'm still confused as to why it's still doing this out of nowhere though. Thank for you help oldfred.

---

