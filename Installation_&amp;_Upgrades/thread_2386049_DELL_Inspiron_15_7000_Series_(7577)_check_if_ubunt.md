---
title: "DELL Inspiron 15 7000 Series (7577) check if ubuntu can be installed"
date: 2018-02-28
forum: Installation &amp; Upgrades
---

### Post by nebojakomnenovic on 2018-02-28
Specs for the laptop which I want to buy:
DELL Inspiron 15 7000 Series (7577)
15.6" FHD
Intel Core i5-7300HQ 2.5GHz (3.5GHz)
16GB DDR4
1TB
GeForce GTX 1050 4GB
4-cell

Is there anyone who have had experience with this kind of configuration and how does it work with Ubuntu 16.04 or 17.10 ? 
What are performances ? 

Thanks,
Nebojsa

---

### Post by seymour93 on 2018-02-28
It is nice to read your question.

I just bought your exact same computer but with a dual drive configuration (SSD + HDD).

I would like to install ubuntu on the HDD but apparently it is not as straightforward as people said.

Especially because we have to mess with UEFI settings..

---

### Post by adriaan-e-van-niekerk on 2018-06-28
I bought the DELL Inspiron 15 7000 Series 7577 with the I7 Gtx 1050ti and it works fine on Ubuntu 18.04.

I had to add acpi_osi=! and acpi_osi='Windows 2009' to the Kernel parameters to get it to stop hanging and to be able to shut down and restart.

---

### Post by turpsicon on 2018-12-10
I have installed 18.04.1 as well ([FONT=Ubuntu]Inspiron 7000 Series - 7567[/FONT]), only issue i'm having is running games on steam discretely with gfx. 

Previously launch options you would run 
primusrun %command%

Anyone have any ideas?
Would like to avoid switching back and forth with primus-select if possible.

---

### Post by matthewjake on 2018-12-10
Hi,

I recently bought a Dell Inspiron 15inch 7580 series with Windows 10. I've been trying to dual boot Ubuntu 18.10, and when I'm using the Live installer everything is working fine, but after the install completes, even just clicking the button to restart hangs and I have to power down holding the power button for 10-20 seconds. And then when I boot up and login, everything is slow and unusable and it eventually just completely locks up. I have tried installing with Secure Boot and with third party software and also without those enabled. I'm posting here hoping to find some help as the topic is close to my laptop model, but if i should post elsewhere please direct me.

Thanks in advance for any help.

Matt

---

### Post by turpsicon on 2018-12-10
> **matthewjake said:**
> Hi,

I recently bought a Dell Inspiron 15inch 7580 series with Windows 10. I've been trying to dual boot Ubuntu 18.10, and when I'm using the Live installer everything is working fine, but after the install completes, even just clicking the button to restart hangs and I have to power down holding the power button for 10-20 seconds. And then when I boot up and login, everything is slow and unusable and it eventually just completely locks up. I have tried installing with Secure Boot and with third party software and also without those enabled. I'm posting here hoping to find some help as the topic is close to my laptop model, but if i should post elsewhere please direct me.

Thanks in advance for any help.

Matt

SEE: [https://www.youtube.com/watch?v=7jiaRJJ43kI](https://www.youtube.com/watch?v=7jiaRJJ43kI) [Round about the 1min40s marker]

You have to disable secure boot in the bios.
Also you need to change your grub. Go into it and add after the quiet splash 
acpi_osi=! acpi_osi='Windows 2009'
If that doesn't work try
acpi_osi=Linux
and if that doesnt work the last one you can try is...
acpi_osi='!Windows2015' [CONFIRMED]

Whichever one works, remember it as you need to add it permanently to your grub.
Once you are in and it works fine in ubuntu go to terminal and do the following
sudo nano /etc/default/grub

[BE VERY CAREFUL HERE ONWARDS]
then go to the line with the quiet splash and immediately afterwards add the line that works in. Eg. 'quiet splash acpi_osi=Linux'
those ' <- are important as well.

after that is done, hit ctrl-x, it will ask if you want to save, say Y for yes, then it will ask to overwrite, overwrite the file (hit enter), ctrl+x again to exit.

after you exit the grub menu, do...

update-grub

then reboot your system, your system should stop hanging permanently.

---

### Post by matthewjake on 2018-12-10
Turpsicon,

I tried each of the options with no success. Should I try reinstalling with Secure Boot disabled in the bios and not enabled in the install and then try these commands? Is secure boot relevant to the hanging?


Edit:

I just disabled secure boot in the bios, did a fresh install with thirdparty drivers enabled. Had the same trouble after booting. Tried each of your suggestions, only difference the Linux parameter was sleight improvement but still not usable.

Edit 2:

I was reading through this article [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) and I tried "acpi=off" and now it boots properly with no issue. I'm not really aware of exactly what I have disabled with this command, but it seems to be a workaround, I'll do some more reading and maybe someone who knows more can tell me if this is a decent solution?

Also, is this an issue that can be resolved and in time be fixed in a newer edition of ubuntu? and could there be an update developed?

Also now I have installed and enabled NVIDIA graphics through the Software and Updates app. They work but run everything slowly. Are the graphics drivers and ACPI configuration related?

---

### Post by matthewjake on 2018-12-13
I just booted up and now everything is working all of a sudden. There is no lag in the graphics and I didn't put any parameters into grub.

---

### Post by simone.romei on 2019-03-12
Hi All,
I've installed Ubuntu on dell inspiron 15 7000 on ubuntu 18.04

As already described in this thread (summary) the mandatory step to install are:
- BIOS Option - Disable secure boot on window 10 (take care...when you disable the secure boot if your HD is protected by "bitlocker" the system don't boot...so...disable bitlocker first)
- BIOS Option - Switch the HD controller from something (If I remember well...RAID) to AHCI -> take care this option make ubuntu installable but create noise in windows (windows didn't boot anymore because it miss the driver for AHCI)...so...is case of dual boot needed -> install the AHCI driver in window before switch it.
- Extra -> in my scenario the installation process was very very slow...accept it!!! :) in reality the installation can be improved by a boot option related to vesa driver (to avoid NVdia stuff only for installation)...but this is not needed.

After the installation (MANDATORY) - reinstall the nvidida driver (last version)...this will force your laptop to work with the right setup (the 2 driver card generate the slow down).

After this...all seems fine...except for a couple of "suspect message" in DMESG:

1) [    2.358468] PKCS#7 signature not signed with a trusted keyFrom a high level investigation; this is a problem related to a "wrong signature" of the NVidia driver...not important (secure boot is disabled)

2) [COLOR=#242729][FONT=Consolas][ 7.802354] CPU0: Package temperature above threshold, cpu clock throttled (total events = 1)[/FONT][/COLOR]
This message is more interesting...
This is an interesting link for extra check: [https://askubuntu.com/questions/941686/cpu-hardware-errors-in-ubuntu-17-04](https://askubuntu.com/questions/941686/cpu-hardware-errors-in-ubuntu-17-04) 

On this point I'm not able to "fix it" (thinking about rewriting the thermald configuration)
Any other advice here????

---

