---
title: "Boot-Repair Info"
date: 2022-10-16
forum: Installation &amp; Upgrades
---

### Post by pedpx2 on 2022-10-16
Hi, I have problem with booting Ubuntu 18.04 into normal mode. I got black screen, when I removed the NVIDIA graphic driver, it was able to show Desktop on the next boot, but when I reinstall NVIDIA graphic driver, it turn to black screen again after next reboot. I am also able to boot into recovery mode too. I knew that it was able to boot but was black screen because I enabled network inside recovery mode to see the IP address, then resume boot into normal mode (which I get black screen) then I was able to ssh into the account using another device. I'm not sure what was going on as my system works fine for few months prior and I did not update Ubuntu or bios relative closely prior to having this problem. There are also some weird behaviour with booting I found, I will describe it below in case it is of any interest.

Turning on PC at different stage of the problem:
1: Normally when turning on the computer, the motherboard should not have any debug LED flashes (the PC worked normally for few months), and with some keypress you will be able to enter the boot selector (Window or Ubuntu). 2: Closely before the boot problem shows up, the motherboard starts up with BOOT debug LED lit but at this point there were no boot problem and the boot selector still shows both Window and Ubuntu.
3: Then when the boot problem showed up, the motherboard flashes DRAM debug LED, then VGA and BOOT debug LED after few seconds, then BOOT debug LED lit and the boot selector shows empty, at this point the BIOS also can't find the SSD connected. After exiting the BIOS, the BOOT debug LED unlit then the boot selected showed up again with Window and Ubuntu. Then Window boots fine, but Ubuntu have boot problem described above.

(1: normal, 2: a bit before having problem, 3: having problem)

Boot Repair: [https://pastebin.ubuntu.com/p/SWDpr3w3hC/](https://pastebin.ubuntu.com/p/SWDpr3w3hC/)

---

### Post by oldfred on 2022-10-16
If you have nVidia card, you have to have nVidia driver or use nomodeset boot parameter to get a default low quality graphics.
Some motherboards have a UEFI setting for which video internal chip's or external cards video is default.
Check your UEFI settings.
Try recovery mode in grub menu, which has nomodeset.

If wrong nVidia driver installed, you must purge it first or you get conflicts.
And then install correct nVidia driver from command line or system settings.

sudo apt-get remove --purge nvidia-*

someone recently mentioned auto install may not work.
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by pedpx2 on 2022-10-24
Thank you for the advice. I am now able to use my system after uninstalling the Nvidia 515 driver and install the 470 driver. But I am confused as to why the driver version 515 worked before and does not work suddenly.

---

