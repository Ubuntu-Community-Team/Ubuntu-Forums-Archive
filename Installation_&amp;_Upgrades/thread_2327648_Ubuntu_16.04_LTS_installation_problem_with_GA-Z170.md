---
title: "Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by paul263 on 2016-06-13
Hello everyone,

I had the following problem when I tried to install Ubuntu 16.04 LTS on my computer: from the moment I boot from the DVD, the message 'error: unknown chipset' shows up with followed with an other one containing 'snd_hda_intel  failed to add i915 component master  (-19)'. Those two error messages I get at the beginning let me do the installation anyway. But at the end, the system wasn't able to reboot itself. 
And when I try to boot in Linux for the first time, I cannot log in successfully. I immediatly get an empty desktop with the sparkling warning message: 'Ubuntu 16.04 has experienced an internal  error'. At that point, I cannot make any action on the desktop. As it was suggested on some forums, I tried to use Ctrl+Alt+F3 but it produced nothing else than a black screen. 
I tried to install Ubuntu 14.04 LTS and it ended up the same way.

My specifications are the following:
Motherboard: GA-Z170X-UD5 TH
CPU: i7 6700K
Graphics card: GTX 1080 Founders Edition

Would you have an idea of how to tackle this issue?

Thank you a lot in advance!

---

### Post by oldfred on 2016-06-13
I have a  Z170N-Gaming 5 v and have no issues.
       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

Are you booting with Intel video or nVidia. It used to be you needed nomodeset, but with that nVidia card, not sure it that works.
Are you able to boot recovery mode to a terminal?

But you have the very newest nVidia card. I doubt the default drivers in repository are new enough. Normally it takes a while before drivers are updated, and then a further while before they are in a distribution. Best to not use drivers directly from nVidia but find ppa with those same newest drivers.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

      Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
This ppa shows your needed driver: 367.18-0ubuntu0~gpu16.04.3
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 

    It must work
       NVIDIA GeForce GTX 1080 On Linux: OpenGL, OpenCL, Vulkan Performance
[URL="http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1080&num=1"]http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1080&num=1
[/URL][http://www.phoronix.com/scan.php?page=article&item=gtx-1080-cuda&num=1](http://www.phoronix.com/scan.php?page=article&item=gtx-1080-cuda&num=1)

---

### Post by paul263 on 2016-06-14
Dear oldfred, thank you so much for your concise, clear and detailed message. 
Thanks to your suggestions, my problem has been solved. For those who may encounter the same problem, here's what I did:

1. Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
2. Restart and plug the HDMI cable on the motherboard instead of your graphic card
3. Boot on your Ubuntu installer DVD and install Ubuntu
4. Install latest the Nvidia drivers using PPA
5. Restart and go to your BIOS, Peripherals > "Initial Display Output": set it back to "PCIe 1 Slot" (uses your graphic card again)
6. Boot into Linux and enjoy!

Thank you once again oldfred!

---

