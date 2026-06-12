---
title: "Acer TimelineX 3820TG - Ubuntu 10.04 problems"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by Nittalope on 2011-07-06
Hi everybody, after some search in the forums I've decided to start this thread because I cannot find an answer to my problem (the last, HDMI) so...

I've got a Acer TimelineX 3820TG and installed Ubuntu 10.04, after installation I had some problems that I fixed thanks to the forums. I'll write here all the procedures done, I'm writing this because there is no dedicated thread to the 3820TG and 10.04. For the dedicated Ubuntu community on Acer Timeline go [here]("https://help.ubuntu.com/community/AspireTimeline"). Most of the solutions I've found comes from there.

This are the problems I've encountered and the solutions are just below.


[LIST]
[*][B]Cannot adjust brightness -> [COLOR=SeaGreen]solved[/COLOR]
[/B]
[*][B]Internal mic doesn't work -> [COLOR=SeaGreen]solved[/COLOR]
[/B]
[*][B]Battery life -> [COLOR=SeaGreen]solved[/COLOR]
[/B]
[*][B]HDMI port doesn't work -> [COLOR=Red]pending[/COLOR]
[/B]
[/LIST]
I'll edit this post with all the modifications / new tricks to use this beautiful laptop with 10.04.[INDENT]**Cannot adjust BRIGHTNESS**
[/INDENT]Open Terminal and modify grub file. Just type this command:[INDENT]sudo gedit /etc/default/grub
[/INDENT]and change the line:[INDENT][FONT=Verdana][SIZE=2]GRUB_CMDLINE_LINUX=""[/SIZE][/FONT][SIZE=2][FONT=Verdana]
[/FONT][/SIZE][/INDENT]with[INDENT][FONT=Verdana][SIZE=2]GRUB_CMDLINE_LINUX"acpi_osi=Linux"[/SIZE][/FONT]
[/INDENT]then save and close and update grub with this command (always in Terminal):[INDENT]sudo update-grub
[/INDENT]I don't remember if you have to reboot, but now it will work.[INDENT]**Internal MIC doesn't work**
[/INDENT]I think the problem is with the ALSA version, here. I've installed Fedora 15 that has got alsa 1.0.24 and the mic works fine. I've got to try to update ALSA, in Ubuntu 10.04 is version 1.0.22. When I've tried I'll write the results here.
By now, you can make it work following the following steps.
It is needed to install alsa backports.
Open Synaptic (System/Administration/Synaptic, you should provide root password) and look for[INDENT]linux-backports-modules-alsa-lucid-generic
[/INDENT]and install it (check it and than push "Apply"). This package will install the latest backport modules and keep it to date when you install new kernels.
Now install Pulse Audio Volume Control (if you want you can install the whole Pulse Audio Device Chooser, but it is not needed) through Synaptic o Software Center (just look for "Pulse" and you'll find it).
Last thing, open Pulse Audio Volume Control (Applications/Sound & Video/...) and go to the Input Devices tab.
Now turn down the volume for one of the two channel, the mic is a mono device. Remember that you have to unlock the meter (press the "lock" icon).
Now the mic will come to life. If you are using Skype disable it's ability to automatically adjust the mic volume, as it will adjust it as a stereo device and mess it up again (just come back to Pulse Audio Volume Control and turn down one of the two channels).[INDENT]**Battery life**
[/INDENT]This was a though one, but at the and I managed it. The laptop in Windows stands up to 8 hours (they say, I've never tested it, just bought it and installed Ubuntu and deleted Windwos) and after Ubuntu installation it lasted 4 hours at the maximum. After a lot of searching in the forums I found out that the problem is due to the ATI graphic card and the solution is to turn it off. I found the solution [here]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html") and here it is.
We need to install GIT and then a acpi module and then load it.
Open Terminal and run[INDENT]sudo apt-get install git-core
[/INDENT][INDENT]git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
[/INDENT][INDENT]cd acpi_call
[/INDENT][INDENT]make
[/INDENT][INDENT]sudo insmod acpi_call.ko
[/INDENT]this will download the acpi_call source and create a acpi_call directory under Home/user_name.
now run[INDENT]./test_off.sh
[/INDENT]in the same Terminal session. There appear lines of acpi calls and "failed" or "works" at the end of the line. If one of the lines has the "works" at the end... great, you disabled the ATI card and this will save a lot of power.
I than created a script named "disable_ATI_card.sh" with this inside:[INDENT]cd ./acpi_call
sudo insmod acpi_call.ko
./test_off.sh
[/INDENT]made it executable and then added it in a launcher on my task bar.
So I can disable the card only if I want. It would be nice to have a similar think to turn it on, but still I haven't looked how to do it.[INDENT]**HDMI port doesn't work**
[/INDENT]I've connected my laptop to a LCD television with the HDMI port and nothing, the television doesn't receive any signal and the laptop doesn't detect any external monitor. Here I am stuck, I haven't found any help and so if somebody can help here, I really appreaciate!

BIOS update
My laptop comes with BIOS 1.08, I've downloaded version 1.13, 1.17, 1.19. Somebody already upgraded the BIOS? Something interesting happens?

---

### Post by Nittalope on 2011-10-01
Today I've upgraded to the 2.6.32-34 kernel and suddenly the acpi_call method was not working any more.
It is because the module cannot be loaded.

Open Terminal then go to the acpi_call directory (cd acpi_call) and run make again. Then everything will work again.

---

### Post by Kakitus on 2012-03-09
> **Nittalope said:**
> 
[/INDENT]I've connected my laptop to a LCD television with the HDMI port and nothing, the television doesn't receive any signal and the laptop doesn't detect any external monitor. Here I am stuck, I haven't found any help and so if somebody can help here, I really appreaciate!


You might have figured this out by now, but the lack of HDMI output is because the integrated graphics don't support it. HDMI mode 3820TG only works with the dedicated GPU.

---

