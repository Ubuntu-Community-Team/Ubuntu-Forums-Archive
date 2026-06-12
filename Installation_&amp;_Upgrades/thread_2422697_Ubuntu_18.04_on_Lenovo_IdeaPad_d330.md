---
title: "Ubuntu 18.04 on Lenovo IdeaPad d330"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by naib864 on 2019-07-11
Im currently trying to install Ubuntu on my Convertible as dual boot, but I have some graphics card related problem.
The device has a Intel UHD Graphics 600 and the screen stays blank when booting the live usb. Otherwise it boots just fine, as I can hear the sound feedback from the login screen when i press the arrow keys.

Any idea for a solution? I already tried nomodeset, but I can't even get to that option. The only menu I see is the one where I can select between trying ubuntu, installing ubuntu (Both options get the blank screen) and oem install.

Thanks in advance :)

---

### Post by oldfred on 2019-07-11
Have you updated UEFI from Lenovo? And if SSD, updated SSD firmware?

Intel graphics are supposed to just work.
You may need other boot parameter? And should get grub menu if booting in UEFI boot mode.
Or at least remove quiet splash to see boot process and where it stops. Usually not last line posted, but errors or warnings several lines above.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Often issues are common across many 
models of same brand. Different issues if AMD or Intel.

       

 Lenovo boot screen can be accessed by Fn + F2 keys, boot device selection by Fn + F12.
Ubuntu on Lenovo ThinkPad E470  Pre-installed Ubuntu
[https://certification.ubuntu.com/hardware/201609-25122/](https://certification.ubuntu.com/hardware/201609-25122/)
Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)
Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by naib864 on 2019-07-12
No, I didn't update the UEFI, do I have to do that?
I have no SSD, just eMMC-storage.

I don't get any purple screen, the screen stays black after the grub, so I can't give any screenshots.

Booting without quiet splash also doesn't work, screen stays black and doesn't give any feedback.
It doesn't stop the boot process at any point as far as I can hear, it sounds like I got to the login screen. 

Rotating the screen also doesn't work, like stated in this article: [https://www.rojtberg.net/1652/ubuntu-on-the-lenovo-d330/](https://www.rojtberg.net/1652/ubuntu-on-the-lenovo-d330/)

Edit: I tried nomodeset again, now it "worked":
[http://www.dropbox.com/s/qdaobd87yk73sj1/IMG_20190712_120133071.jpg?dl=0](http://www.dropbox.com/s/qdaobd87yk73sj1/IMG_20190712_120133071.jpg?dl=0)
I opened the terminal in this picture.
How do I fix this?

---

### Post by oldfred on 2019-07-12
I had a similar screen on a reboot.

But I have both nVidia & Intel & use nVidia with the open source driver in most of my installs.
I have multiple Ubuntu installs and use 18.04 as main working install, but rebooted into 19.04 & 19.10 to test something & on reboot via a Debian version of grub into 18.04 got that screen. But on reboot it worked normally, so was not sure of issue. Perhaps a firmware version issue as Ubuntu also loads firmware.

You need to update UEFI.
Both Windows & Ubuntu have updated kernels. But UEFI also needs updates for this, but vendors also fixing other issues with updates.
       [https://www.intel.com/content/www/us/en/architecture-and-technology/facts-about-side-channel-analysis-and-intel-products.html#2](https://www.intel.com/content/www/us/en/architecture-and-technology/facts-about-side-channel-analysis-and-intel-products.html#2)
[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)
[https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1)

---

### Post by naib864 on 2019-07-13
Okay, I'll try that tomorrow. There's a brand new update released yesterday on the lenovo website, I hope it works.

---

### Post by naib864 on 2019-07-22
The Bios update installer didn't work at first (It just extracted some files and then restarted itself). Now, after a week it randomly popped up and I was able to install it, but unfortunately it had no effect on the linux problem.

---

### Post by oldfred on 2019-07-22
Are you getting the grub menu shown here for UEFI boot?
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by YaronSh on 2019-10-03
> **naib864 said:**
> 
How do I fix this?

Add the following to your grub config (/boot/grub/grub.cfg):
```
set gfxmode=1280x800
set gfxpayload=800x1280
```

I'm guessing these are reversed due to the rotation issue (it won't fix the rotation of the touch).

---

### Post by oldfred on 2019-10-04
Do not edit grub.cfg, but edit settings in /etc/default/grub.
Every update to grub or kernel creates new grub.cfg from several scripts & the settings file.

---

### Post by YaronSh on 2019-10-04
Is there a way to add these lines using the default? I've tried several options and none of them worked.

EDIT:
I found a way but it's pretty ugly, I can add these manually to `/etc/grub.d/10_linux.cfg` (not sure about the suffix) and it will add these to all the linux entries whatsoever.

---

### Post by oldfred on 2019-10-04
You edit grub's files & then update it which creates a new grub.cfg.

       sudo nano -B /etc/default/grub 
    
sudo update-grub

---

