---
title: "Installer disk will not load the kernel from installer disk grub menu. 20.04.4"
date: 2022-02-26
forum: Installation &amp; Upgrades
---

### Post by gds1960 on 2022-02-26
I have downloaded this new installer 12 times and all twelve times the iso file checked good. I burned 12 dvd's and they all tested good and I burned the iso to 3 different jump drives and all checked good. When trying to install the grub menu appeared and I tried all entries and got no display or sound and there was no activity on my dvd-drive or jump drive.:(

Is there anything that I can type on the grub command line that might save the day?????:confused:

There will be no code windows here since it will not boot my computer.:frown:

Motherboard: asus prime z590-p wifi
cpu: core i9-11900k
SSD: SP Silicon Power nvme 1tb

---

### Post by MAFoElffen on 2022-02-26
Let's back up and get a clearer picture. Not just that I see what you have done,  but that we are talking the same terms and language. Communications is the mutual understanding of what is said.

You believe that you have good ISO image files. You have checked them. Then you said you burned the files to DVD's... 

Where you lost me was when said that you burned them from the DVD's to 3 different Jump Drives... ???

Let's stop at that to see what you really meant. Because in my mind and experience, when I say "jump drive", I mean a USB connected external storage drive, portable. HDD, or SSD. Now when some one mentions a pen drive, or thumb drives, then I know that is a USB Flash Drive.

So... What was the boot media that you created from what? And How did you create it?

Next, what is it that you are trying to boot on? The hardware in your signature line? Or other?

---

### Post by oldfred on 2022-02-26
Have you updated UEFI from Asus and firmware for NVMe?
Asus may need settings. My Asus is an older z97 but since UEFI, settings are often similar. I have maybe 7 UEFI settings I change, some required, some optional to make it a bit better booting.
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

What video card?

I stopped using DVDs years ago as I often burned coasters. I even used one as a coaster for years. :)
Flash drives are reusable, but now an external SSD is a lot faster and if larger can be both a functional system and used for installs, bit more advanced to configure, so best to learn with a flash drive.

---

### Post by michael-vrobles on 2022-03-03
> **gds1960 said:**
> I have downloaded this new installer 12 times and all twelve times the iso file checked good. I burned 12 dvd's and they all tested good and I burned the iso to 3 different jump drives and all checked good. When trying to install the grub menu appeared and I tried all entries and got no display or sound and there was no activity on my dvd-drive or jump drive.:(

Is there anything that I can type on the grub command line that might save the day?????:confused:

There will be no code windows here since it will not boot my computer.:frown:

Motherboard: asus prime z590-p wifi
cpu: core i9-11900k
SSD: SP Silicon Power nvme 1tb

I have the same chipset and same processor, I think I am narrowing it down to a secure boot issue. I believe there is an issue with the intel graphics integrated to the motherboard as well so try to disable that if you have an external GPU.

[https://ubuntuforums.org/showthread.php?t=2459739&highlight=Z590](https://ubuntuforums.org/showthread.php?t=2459739&highlight=Z590)

---

