---
title: "[Sony Vaio Pro 13] UEFI dual boot, with Windows 8.1 and Ubuntu 14.04.1 LTS"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by Scott_Moore on 2015-01-09
Hello, (wow this message got big)

I have tried several times to setup Ubuntu on my laptop however without luck. I have refered to the following guides:
[LIST]
[*][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[*][http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
[*]Several more.
[/LIST]

For those who want to quickly browse through my boot-repair log:
[LIST]
[*][http://paste.ubuntu.com/9692083](http://paste.ubuntu.com/9692083)
[/LIST]

I currently have a Sony Vaio Pro 13 laptop and installing Ubuntu on it has quickly become much more difficult than previous installations I have done on my desktop and also developed a growing hate for UEFI :eek:. The laptop comes installed with several partitions which I will describe below, which as far as I know prevent me from completely reinstalling all operating systems on the device (something I would rather not do anyway, as I have been using windows on the laptop for about 6 months now, and it may prevent me from restoring it to factory settings).

Its partitions are setup like so in a GUID Partiton Table (if you read through the boot-repair log it may also give you this information):

[LIST]
[*]1 MB of free space I assume could be used for MBR
[*]sda1: "SONYSYS" -> As far as I am aware it stores data for the Sony ASSIST button with is on the laptop. When pressed it turns on the laptop and brings up a screen shown below. It is the only way I know how to access the bios currently.
[*]sda2: "Windows Recovery Environment (Windows)" -> Also a useful tool, which can be launched from the ASSIST menu, which shows many options to fix windows, including a Windows console.
[*]sda3: "EFI partition" -> Stores EFI data (know the least about this one, but it appears sda1 also has EFI data? Perhaps for the ASSIST button)
[*]sda4: "Microsoft Reserved Partition" -> Something to do with Windows installation
[*]sda5: "Data partition" -> Windows OS is installed here
[*]sda6: "Data partition" -> Ubuntu OS is installed here
[*]sda7: "Swap partition" -> Swap for linux OS
[/LIST]

For those that are wondering sdb is the installation USB.

Also I have disabled SecureBoot even though Ubuntu 14 I assume should deal with it fine using shimx64.efi. I have turned off Windows Fast Startup which is also known to cause issues.

When installing Ubuntu it appears it does not detect Windows and does not offer an "Install alongside Windows" option. Instead I chose "Something else" and shrunk the Windows partition, and created a Linux partition and swap partition at the end of the drive. The installation completed successfully, however when I restarted the computer boots straight to Windows again. After reading for a while I found boot-repair and decided to try this. Running the "Try Ubuntu" off the USB I install boot-repair and run it. Which produces the log seen above. The computer still boots to windows however, but the boot-repair says to enter the following command.

```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```

After running the command however with no luck, the computer boots to Windows again. I found a website mentioning that some motherboard are non-compliant with the standard, and will always choose the file ```
\EFI\Microsoft\Boot\bootmgfw.efi
``` so after mounting sda3 in the "Try Ubuntu" mode I then renamed ```
bootmgfw.efi
``` to ```
bootmgfw.efi.old
``` which worked. The computer booted into grub and allowed me to select from various options. Those options were something like:
[LIST]
[*]Ubuntu
[*]Advanced Ubuntu -> takes us to a selection of other ubuntu modes
[*]Windows UEFI recovery bootmgfw.efi -> "same as below, recovery tools"
[*]Windows Boot UEFI Recovery -> "Recovery tools, windows recovery console, etc"
[*]Windows Boot Manager (on dev/sda3) -> "Cannot find due to renamed file"
[*]System Setup -> "Sony ASSIST button screen"
[/LIST]

[IMG]http://i.imgur.com/TVOI43f.jpg[/IMG]

[IMG]http://i.imgur.com/KrMpaRc.jpg[/IMG]

I thought if at least I could launch Ubuntu I may be able to add Windows to the grub list and then slowly work through the other issues, such as these other entries in the list and changing grub settings, such as wait time. However Ubuntu used to boot up to a recovery thing, now it just stays on a purple/pink screen after I ran boot-repair for a second time. Running with Linux 3.13.0.43-generic just stays on the purple screen. Running however with Linux 3.13.0.32-generic does what the first one does before I ran boot-repair for a second time (I think this is what caused it). It takes me to a screen like so.

[IMG]http://i.imgur.com/vC5qUPY.jpg[/IMG]

I ran some of the suggested commands.

[IMG]http://i.imgur.com/rNdIxAh.jpg[/IMG]

Luckily by using the "Try Ubuntu" I can rename the efi file back to its original state and launch safely back into windows. Also using bcdedit and setting that back as well (just in case). So now I am do not know what to do.

Also as a note: this is my second time installing Ubuntu as the first time I tried the above method, but with less confidence (as I did not know what was going on) and somehow after using the boot-repair, bcdedit worked! Which makes me think it may not be a motherboard issue if it worked at one stage. Also in that first run Ubuntu did not work either, which was the primary reason I thought I should reinstall. The boot-repair log for my first run through is [here]("http://paste.ubuntu.com/9692083"), but it may not be relevent anymore (just in case). Also there is an error at the end, because that was before I had turned Windows Fast Startup off.

So currently I can operate in Windows, and I feel safe as I can remove the Ubuntu and swap partition from the drive and extend my Windows partition to fill the space if necessary, but I enjoy using Ubuntu and have it installed in a dual boot on my desktop, which works perfectly (close enough). Happy to supply more information.

Side Note: I really wish I could remove all this Sony crap. I have already had to reinstall Windows 8 onto the laptop to remove the bloatware preinstalled on that Windows image, and I am reluctant to remove the functionality of the ASSIST button in fear that I will not be able to access the BIOS. While the windows recovery tools are useful I could probably just install something similar on a USB.

---

