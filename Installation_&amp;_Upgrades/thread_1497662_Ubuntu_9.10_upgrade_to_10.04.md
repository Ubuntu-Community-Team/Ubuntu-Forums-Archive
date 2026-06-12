---
title: "Ubuntu 9.10 upgrade to 10.04"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by carl_pr on 2010-05-30
So i decided once and for all to clean the HDD and install only ubuntu on it and remove windows 7 completely. I don't have any blank CDs, so months ago i ordered a ubuntu 9.10 CD. My goal was to install 9.10 and then upgrade to 10.04 via upgrade manager. I did everything the upgrade downloaded and installed everything then the computer restarted and i just got a black screen with a error that i couldn't write down because it disappeared to fast. So the OS couldn't boot, i had to install again 9.10, im on 9.10 right now. Is there any way to solve this? should i try and upgrade again? or i am stuck with 9.10 ( i like having the latest stuff :P)

The program is i dont have any blank CDs and i don't think this desktop can boot via USB.

---

### Post by robvas on 2010-05-30
What kind of hardware does your system have?

10.04 is known for issues with certain video cards.

---

### Post by carl_pr on 2010-05-30
the video card is an Nvidia 61** something, i know is 6000 series. As soon 9.10 booted for the first time, i upgraded to 10.04 without updating 9.10 or activating and downloading any video cards drivers. I don't know if that have anything to do...

---

### Post by garvinrick4 on 2010-05-30
Install 9.10 then run.
```
sudo apt-get update && sudo apt-get upgrade

```After 9.10 is up to date copy and paste this into terminal.
                                 ```
sudo sed -i 's/karmic/lucid/g' [/etc/apt/sources.list]("file:///media/etc/apt/sources.list") && sudo aptitude update && sudo aptitude dist-upgrade

``` This will get you current in 10.04 lucid lynx. Have a nice day.

Here is the instruction manual for Lucid, it is a nice piece to have around.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking](http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking)

---

### Post by carl_pr on 2010-05-30
all right, im gonna try that. I have 10.04 netbook release on my netbook and didn't had any problems but i did install it from scratch, wiped all, didn't did via upgrade.

---

### Post by wilee-nilee on 2010-05-30
> **garvinrick4 said:**
> Install 9.10 then run.
```
sudo apt-get update && sudo apt-get upgrade

```After 9.10 is up to date copy and paste this into terminal.
                                 ```
sudo sed -i 's/karmic/lucid/g' [/etc/apt/sources.list]("file:///media/etc/apt/sources.list") && sudo aptitude update && sudo aptitude dist-upgrade

``` This will get you current in 10.04 lucid lynx. Have a nice day.

Here is the instruction manual for Lucid, it is a nice piece to have around.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking](http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking)

I wouldn't do this, but that is me personally. The reason being is it will probably leave you in the same position your already in. 

A look at the full computer specs including the graphics card would be a good place to start with. Post the output from the terminal ```
lspci
``` from the live cd.

---

### Post by carl_pr on 2010-05-31
this is the output, im on 9.10 currently but i dont know if upgrade to 10.04 because i fear is happen the same. The output is this:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
03:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
carlos@carlos-desktop:~$

---

### Post by oldfred on 2010-05-31
I have a newer nvidia and Karmic worked without any issues and I updated to use the nvidia driver.

With Lucid neither the CD install nor the first boot would work.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

More info if nomodeset does not work:
Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by wilee-nilee on 2010-05-31
> **oldfred said:**
> I have a newer nvidia and Karmic worked without any issues and I updated to use the nvidia driver.

With Lucid neither the CD install nor the first boot would work.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

More info if nomodeset does not work:
Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

Excellent advice, It is important to look ahead at what your going to be dealing with and being prepared for it.

The OP mentioned earlier that they were not sure or didn't think the computer would boot with a thumb here is a download that will allow you to boot a thumb with the cd.
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by carl_pr on 2010-05-31
Hey i did the update via the terminal like the guy said previously and at first i got the black screen and the error. It say something like


error probbing (something like that) SMB1 but now ubuntu 10.04 booted normally. I hope i dont encounter any more issues. 

I dont know what SMB1 is...

---

### Post by garvinrick4 on 2010-05-31
> **carl_pr said:**
> Hey i did the update via the terminal like the guy said previously and at first i got the black screen and the error. It say something like


error probbing (something like that) SMB1 but now ubuntu 10.04 booted normally. I hope i dont encounter any more issues. 

I dont know what SMB1 is...
I am glad it boots normally for you now.

---

