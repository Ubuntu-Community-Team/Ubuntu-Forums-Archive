---
title: "Freeze during install"
date: 2017-05-17
forum: Installation &amp; Upgrades
---

### Post by thanekrios on 2017-05-17
Hi. I've been trying to install Ubuntu for a while now, and I ran into the problem that it froze once installed after a couple of minutes. I tried to re-install and now it freezes during installation, after I select everything and setup the disk partitions. I usually just leave the defaults because they suit my needs and I don't want to mess anything up. I'm not trying to make a dual boot. The disk is clear. I tried this on my main SSD and also on an HDD. Both have the same issues. My hardware:

AMD FX 8350, Gigabyte GA-970A-DS3P rev 2.x, GTX 1060 6g (MSI), Sandisk SSD Plus 240Gb.

I already tried enabling IOMMU and didn't work. Also disabled ACPI (I think, there is no specific ACPI option, just disabled some power saving features using it, like Cool&quiet). I'm currently using Mint 18.1 Cinnamon.

Thanks!

---

### Post by thanekrios on 2017-05-19
bump?

---

### Post by Bucky Ball on 2017-05-19
Are you online while you are trying to install? Either way, try disabling 'Update' and 'Third-party software' options during the installation if they are options during a Mint install. Once installed, try doing an update via the terminal first thing.

```
sudo apt update
sudo apt full-upgrade
```

Some suggestions. Let us know what happens.

---

### Post by ubfan1 on 2017-05-19
Looks like you have Nvidia hardware.  In grub, type "e" to edit and add the word "nomodeset" to the linux line at the "splash quiet" location.  Then boot with ctrl X or F10 and see if that helps.  After the install, and update, add the Nvidia drivers from the Software Updater/Settings button/Additional Drivers tab.  Might have to add the Canonical Partners software first, in one of the earlier tabs.

---

### Post by thanekrios on 2017-05-20
_Ok I will try that guys, thanks._

I forgot to mention,** I can install the 32bit version**, and works perfectly. **The 64bit is the problem**. Apparently, some people that owned** Gigabyte motherboards** had issues with it too (not the same, the issues where no USB ports and no Wifi card, solved by enabling IOMMU and disabling ACPI, the problem is, _**I don't know if I'm disabling ACPI correctly**_), so I believe that's could be the reason. I'll use the 32bit for now, but I would like to use all the RAM I have available (I have 8Gb). Thanks, I'll let you know if I figure something out!

---

### Post by Bucky Ball on 2017-05-20
Just noted the GPU. How far are you getting when you boot the 64bit version? If you're at least getting something, try this before the welcome screen. Boot the 64bit version and hit the shift key (I think for 64bit, or it might be any key or it might be escape, hopefully someone who's more familiar can confirm). That will take you to an options screen. Along the bottom you should see F1-F6. Hit the F6 key on the keyboard and choose the 'nomodeset' option.

That's the nutshell version, [here's a full explanation]("https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options"). That link may be a bit dated, but 'nomodset' is the option you might need for that card until you're installed and can install the correct driver. That's easy. They're in 'Additional Drivers' once you've installed and updated.

---

### Post by thanekrios on 2017-05-23
Hi guys. Sorry it took me a while to respond. I tried the nomodeset setting and got the same results. Also tried disabling ACPI and nothing. 

Interesting thing is, I installed Ubuntu 14.05 64bit and no problem. Seems the issue is with the last 2 releases (16,17). Does that give you any ideas?

---

### Post by thanekrios on 2017-05-23
More news guys! I just installed Lubuntu 16.04.5 64bit and there were no problems. I belive it uses a different installer, right? Could that be the reason?

---

### Post by Bucky Ball on 2017-05-23
Well, that is the latest point release of that, but no, not a different installer as far as I know. If you've successfully installed and problem solved, best to mark this thread as solved to help others (Thread Tools at the top right of page.)

This will not close the thread to further discussion. Good luck. :)

---

