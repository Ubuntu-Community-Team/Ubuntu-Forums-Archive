---
title: "Dual boot with Windows 10 not working"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by glazu on 2020-10-22
Hello,

I am having some difficulties setting up a dual boot with Ubuntu 20 LTS and Windows 10 Oct 2020 update. 
My computer is a Thinkpad X1 Extreme Gen 2, and I have installed Windows first and Ubuntu afterwards. Both these OS' are UEFI and Secure boot is disabled.

The issue is that the PC boots to Windows right away. If pressing F12 during the startup, there is no Ubuntu listing in the boot menu.
Using EasyUEFI, I can see that there are the following folders in \EFI: Boot, MICROSOFT, ubuntu.

I have tried using this command ```
[COLOR=#DAD7D2][FONT=Consolas]bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi[/FONT][/COLOR]
```, but with no luck. This entry changes back to the Windows Bootloader after reboot.
I have also tried boot-repair, however it behaves the same way. I have disabled Fast boot in windows, as well as hibernation.

Any suggestions?
Thanks in advance

---

### Post by oldfred on 2020-10-22
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)


Some HP, do not seem to work with efibootmgr which grub uses to set boot order. 
Not sure if UEFI or Windows then resets Windows to first in boot order.
But users have said changing order in UEFI settings then does work. You could try that.

---

### Post by cimh on 2020-10-22
Hi Glazu: I dont have an answer for you but looks like you got to the same point I did yesterday. See my last post at the end of:-
[https://ubuntuforums.org/showthread.php?t=2452250](https://ubuntuforums.org/showthread.php?t=2452250) 

Fortunately I CAN see the option to boot ubunu in my BIOS setup when I hit F11 on start up. This is not the perfect solution but it does enable me to get to ubuntu quite easily. I searched the forums for an answer to my problem (and of course yours) but all the solutions looked too complex and risky or not permanent like the bcdedit command you tried. However there are some v clever and helpful experts like oldfred and CelticWarrior here so I shall keep a close eye on any replies.

---

### Post by dagyrox on 2020-11-12
I am having the same exact issue with the same exact machine, except I've installed 20.10  I don't know if I should start a new post or not.  I'll post here what I got and you tell me if I should start a new one.  Thanks.

[https://paste.ubuntu.com/p/GgP4Zq64mM/](https://paste.ubuntu.com/p/GgP4Zq64mM/)

^^^  I've done boot repair multiple times.  This is the pastebin of the latest one.

Hibernation is off
fast boot is off
secure boot is disabled

current boot order is:
usb hdd
other hdd
nvm1
nvm0
windows
...others

I used rufus to create the live disk.  Set GPT, UEFI only (cms no)

---

### Post by oldfred on 2020-11-12
Make sure you have newest UEFI and have updated firmware on SSDs. 

There is a setting somewhere in UEFI that restricts changes to boot entries.
Lenovo ThinkPad X1 Extreme 2019 UEFI settings required.
[https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub](https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub)

---

### Post by dagyrox on 2020-11-12
Upgrading bios worked, but I don't think it was necessarily the upgrade version itself that did the trick. Upgrading changed my settings so that it was uefi hybrid with cms enabled. Before, it was uefi only with cms disabled.

Thank you!  2 weeks trying to figure this thing out &#129318;*&#9794;&#65039;

---

