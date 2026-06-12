---
title: "Installing Ubuntu 18.04 on Inspiron 5575"
date: 2019-08-08
forum: Installation &amp; Upgrades
---

### Post by webbi87 on 2019-08-08
[COLOR=#000000][FONT=Roboto]Hi! I'm new to the community, so please sorry if I made a mistake on this post.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]I recently bought a Inspiron 5575 which cames with AMD Ryzen5 + Radeon Vega8. It has a 1TB HDD with windows 10 pre-installed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]I bought a WD BLUE SN500 NVME SSD 256GB, installed on it and wanted to install ubuntu there having dual boot.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Besides any EFI/BIOS config, I just wanted to launch the "Try ubuntu" option, so I made a USB boot with ubuntu (also tried kubuntu) iso using Rufus, turn on laptop, press F12 and select USB to boot with.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Grub screen appear and select "Try ubuntu", splash screen appear and after a few seconds it hangs.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Do it all over again but this time pressed 'e' on the grub screen and change boot params from "quiet splash ---" to "nosplash noacpi noapic". Boot start, and after a few seconds it hangs on "Begin: Preconfiguring networking" after a few more seconds, appear some errors that worried me: "TSC found unstable after boot [...] Broken BIOS"[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Attached an image where you can see the last boot output:
[ATTACH=CONFIG]283756[/ATTACH][/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]I have read many documents here about dell and ubuntu dual boot, but no one match my symptoms, also tried a lot of grub options and combinations:

noapic, noacpi, pci=nomsi, pci=noaer, nomodeset, irqpoll

But noone help. Using pci=nomsi the boot does not hang, but it shows initramfs prompt and "No bootable media found" as shown here:
[ATTACH=CONFIG]283755[/ATTACH][/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Hope someone could point me on this.[/FONT][/COLOR]

---

### Post by oldfred on 2019-08-09
Do not know AMD issues.

But Dell typically needs UEFI update & drives set to AHCI, not RAID nor Intel SRT.
And most SSD need firmware update, even if new.

General UEFI install info in link in my signature.

Some other Dell 5000 series. Often similar issues across multiple models, but Intel & AMD will have some differences.
       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[URL="https://ubuntuforums.org/showthread.php?t=2347889"]https://ubuntuforums.org/showthread.php?t=2347889
      [/URL]
 Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822) 
    [URL="https://ubuntuforums.org/showthread.php?t=2347889"]
[/URL]

---

### Post by webbi87 on 2019-08-09
Updated everything from windows Dell Update, included BIOS, BUT didn't try to update SSD firmware (don't know about that first time I got one), will try tonight and let you know if that changed something.

SSD firmware update should be done through some kind of WD software I guess?

Thanks!

---

### Post by Dennis N on 2019-08-09
> SSD firmware update should be done through some kind of WD software I guess?
I have the WD SN500 NVMe SSD but the 500 GB model. It worked out of the box. If you look at info on WD Dashboard management tool, which can handle updating firmware, all the "supported operating systems" are Windows. There is also some Mac software offered too. But Linux not mentioned anywhere. So, I never did a firmware update, and it doesn't seem to matter. This drive was only 3 dollars more than a Crucial MX500 500 GB  SATA m.2 drive, and 3X as fast. You probably know it's only PCIe 3 x 2,  but still a no brainer. Since my other drives are SATA SSDs, everything passing between them is throttled to SATA speed anyway.  

There is a Linux utility that can read the SMART data and temperature of NVMe drives that's useful. I'll add the name when I get a chance to look. It's not on this computer.

---

### Post by webbi87 on 2019-08-09
Yes, as far as I see, I choose the wrong brand to use SSD with linux, it looks like samsung is more supported.

Anyway I will try to make it work before doing anything else, hope that "dashboard" make some update that help me.
I will be posting news today.

Thanks for the reply!

---

### Post by Dennis N on 2019-08-09
Since you have Windows, you can update the firmware that way. I don't have Windows on my computers and I didn't see any alternate method (like some file to download). The Linux utility I mentioned is **nvme-cli** and in the Ubuntu repository.

Type nvme in the terminal to see the list of commands. There are lots of them. It has a command to download new firmware (if you have a URL, I suppose) and maybe can install it too. After the command list, it states that "Western Digital vendor specific extensions" are included which sounds promising. But I don't intend to mess with it at this time in my case since it appears to work as it should. If you learn anything about upgrading from Linux, please advise.

Sample commands:

```
dmn@Sydney:~$ sudo nvme list

Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     936635214204         WDC WDS500G1B0C-00S6U0                   1         500.11  GB / 500.11  GB    512   B +  0 B   201000WD

dmn@Sydney:~$ sudo nvme smart-log /dev/nvme0n1 | grep temp
temperature                         : 40 C



```
(The 12 digit SN here is not the real one.)

I would expect updating the computer firmware would be more important than the SSD firmware.

---

### Post by webbi87 on 2019-08-12
Well, good news here, I got it working, almost everything I try.

Solution? add to grub boot: nvme_core.default_ps_max_latency_us=5500

How to do it?
On grub screen, where you have to choose between 'Try Ubuntu' or 'Install Ubuntu' press 'e' and edit the line that ends with 'quiet splash ---' with 'quiet splash nvme_core.default_ps_max_latency_us=5500'

Explanation:
Appearantly (almost as far as I understood), nvme support is not for 100% of current devices, it's mostly done/test for Samsung devices.
In my case I have a Western Digital Blue SSD device, so after a big research I found that 5500us is the "correct value" to use. To be honest, I dont know what this param exactly does, I know its some sort of timeout that depends from each device manufacturer :S

I tried Ubuntu 18.10, Ubuntu 18.04 and Kubuntu 18.04 with success.
Everything else on the laptop appear to work properly, there is only one thing to check and it's the touchpad settings, I'll be working on that later.

So, hope this help anyone other with the same problem.

Thanks!

---

### Post by webbi87 on 2019-08-12
Dennis, thanks for the info! I tried to update the firmware from windows western digital dashboard but it says it was up-to-date.
Good to know that there is a way to update it in linux, thanks for that!

---

