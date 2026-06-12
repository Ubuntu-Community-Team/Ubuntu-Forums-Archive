---
title: "Can't boot to Windows anymore (Dual boot Windows 10 / Ubuntu 20.04.1)"
date: 2020-11-08
forum: Installation &amp; Upgrades
---

### Post by benidukadu on 2020-11-08
Hello all,

I hope this is the right place to post this.

So I installed Ubuntu 20.04.1 a few days ago on my PC. I had a dual boot with Windows 10 on my first SSD (which was installed first), and Ubuntu on my 2nd SSD (I followed these instructions: [https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives](https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives)), and it all worked fine initially.

However today after a Windows update, my PC booted straight to Windows. After entering ```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
``` in Windows command line I was able to get GRUB back and to boot into Ubuntu.

Unfortunately now I can't boot into Windows. Windows Boot Manager does still appear in GRUB but selecting it does nothing.

I unsuccessfully tried ```
sudo update-grub
```, as well as creating ```
/boot/grub/custom.cfg
``` as recommended here: [https://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix](https://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix). I did get a "Windows (UEFI)" entry in GRUB but it didn't have any effect either.

Finally I installed boot-repair,  launched Recommended repair, and got a "Boot successfully repaired" message with the following pastebin: [https://paste.ubuntu.com/p/FgwRKnvgD9/](https://paste.ubuntu.com/p/FgwRKnvgD9/)
However now I do not have access to GRUB anymore, it boots straight to Ubuntu instead.

I also noticed that now in UEFI, the fixed boot order priorities includes my  2nd drive (Ubuntu) instead of the first. Another option, UEFI Hard Disk Drive BBS Priorities, gives a list of 3 options: Ubuntu SATA1 (which I set first, as  apparently recommended by boot-repair), Windows Boot Manager SATA1,  & Ubuntu SATA2. Still boots straight to Ubuntu regardless.

So now I'm unsure what to do to get GRUB & Windows back. Any help would be much appreciated.

---

### Post by garvinrick4 on 2020-11-09
> sudo fdisk -l
See what partition table looks like copy and paste so as to look at it.

---

### Post by benidukadu on 2020-11-09
Actually I discovered that by pressing Escape on start-up I could access a GRUB screen with the message "Minimal BASH-like line editing is supported..." and a command prompt. (Typing "exit" in it boots to Ubuntu.) Does that mean the solution is to reinstall GRUB, as suggested here ([https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/]("https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)?") )?

Anyway, fdisk gives the following:

```
Disk /dev/loop0: 54,98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 255,58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 55,37 MiB, 58052608 bytes, 113384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 62,9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 217,92 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 50,69 MiB, 53133312 bytes, 103776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 29,9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 49,8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465,78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: CT500MX500SSD1  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6F31509E-898A-4E97-9CF4-02E5638BEDF5

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1085439   1083392   529M Windows recovery environment
/dev/sda2  1085440   1288191    202752    99M EFI System
/dev/sda3  1288192   1320959     32768    16M Microsoft reserved
/dev/sda4  1320960 976773119 975452160 465,1G Microsoft basic data


Disk /dev/sdb: 232,91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 860 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 36266318-4CF3-447E-8A5C-7A1083AA5D8E

Device        Start       End   Sectors   Size Type
/dev/sdb1      2048    999423    997376   487M EFI System
/dev/sdb2    999424  59592703  58593280    28G Linux filesystem
/dev/sdb3  59592704  98654207  39061504  18,6G Linux swap
/dev/sdb4  98654208 488396799 389742592 185,9G Linux filesystem


Disk /dev/loop8: 30,96 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by tea for one on 2020-11-09
Both your disks are GPT and both have EFI partitions.

I reckon that you can boot either Windows 10 or Ubuntu via your UEFI boot manager.

Do you know the dedicated key to access your boot manager?

---

### Post by oldfred on 2020-11-09
Windows updates normally reset it to first in boot order. Grub does same on major update.
But Windows typically turns fast start up back on which prevents grub from booting Windows. Check that setting also.

You can change boot order in your UEFI settings often f2 or del key and boot tab, (not the menu which is a separate key). 
Or you can use efibootmgr with -o option. Except it seems HP's UEFI does not recognize efibootmgr changes.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by benidukadu on 2020-11-09
> Both your disks are GPT and both have EFI partitions.

Just to be sure, this isn't an issue in itself, right?

> I reckon that you can boot either Windows 10 or Ubuntu via your UEFI boot manager.

Unfortunately I can't. I've tried placing Windows Boot Manager SATA1 as the top priority in my UEFI settings but it still boots straight to Ubuntu. Before it gets to Ubuntu I can just press Escape and get to the GRUB "Minimal BASH-like line editing is supported..." screen. I have no way to boot to Windows.

> But Windows typically turns fast start up back on which prevents grub from booting Windows. Check that setting also.

I'm not sure which fastboot you are referring to, since an option with this name is available in both Windows and most UEFI settings.
Anyway, my own motherboard (MSI B450 Tomahawk Max) does not have such an option, and I'm unable to boot to Windows to disable Windows' fastboot.

Here is what I get from running efibootmgr -v:

```
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0001,0002,0000
Boot0000* ubuntu    HD(1,GPT,f2264043-6189-4956-8c75-1bd00fe8c99d,0x800,0xf3800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager     HD(2,GPT,9d7a6fb7-fc91-4ac0-9c84-47f00507bec4,0x109000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0002* ubuntu    HD(2,GPT,9d7a6fb7-fc91-4ac0-9c84-47f00507bec4,0x109000,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
```

So Windows Boot Manager is set first, but it will still boot  to Ubuntu.

---

### Post by tea for one on 2020-11-09
Both disks with GPT and EFI partitions - that is perfect.

I was hoping that you could access the UEFI [COLOR="#0000FF"]boot[/COLOR] screen rather than the UEFI [COLOR="#0000FF"]set up[/COLOR] screens.

The boot screen simply allows you to select an OS rather than organise the priority of booting.

e.g. If I plug in a USB device containing an Ubuntu ISO, I press F10 to see the boot screen (I do not access the set up screens).

---

### Post by oldfred on 2020-11-09
If you select Windows UEFI boot entry, it still boots Ubuntu?
If so UEFI does not correct see the Windows boot entry.

UEFI has fast boot setting. Required by Microsoft to make it seem like Windows boots faster.
It assumes you have made no system changes, does not do the scan of system and record new settings on drive for operating system to use. Often a full cold boot, or full power down will  do a normal start, so settings can be updated & you have time to press keys to get into UEFI settings.

Windows has fast start up to speed settings. It really is hibernation and sets hibernation flag. 

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

MSI B450 Tomahawk Max & MSI Nvidia GTX 1080 TI UEFI update & defaults
[https://ubuntuforums.org/showthread.php?t=2450961](https://ubuntuforums.org/showthread.php?t=2450961)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)

---

### Post by benidukadu on 2020-11-09
> I was hoping that you could access the UEFI [COLOR=#0000FF]boot[/COLOR] screen rather than the UEFI [COLOR=#0000FF]set up[/COLOR] screens.

My bad, I wasn't aware of the difference. I can indeed access the boot menu but the issue remains: when I select Windows Boot Manager, the screen just blinks and stays on the boot menu.

> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary  report ( do not post report), do not run the auto fix till reviewed.

Unfortunately I had already tried running boot-repair's auto-fix before posting here... Anyway, here's the pastebin link:

[https://paste.ubuntu.com/p/gVwHPYct85/](https://paste.ubuntu.com/p/gVwHPYct85/)

---

### Post by CelticWarrior on 2020-11-09
> [COLOR=#000000]My bad, I wasn't aware of the difference. I can indeed access the boot menu but the issue remains: when I select Windows Boot Manager, the screen just blinks and stays on the boot menu.[/COLOR]


I think you're confusing Grub's menu with the UEFI boot menu - Please correct me if I'm wrong.
Users have been asking for you to open UEFI ("BIOS") settings > Boot menu and there change the boot order to "Windows", not to select it in the Grub menu. If this doesn't boot Windows directly and correctly you have a serious (Windows) problem and that likely preceded you attempt to install Ubuntu.

---

### Post by benidukadu on 2020-11-09
> I think you're confusing Grub's menu with the UEFI boot menu - Please correct me if I'm wrong.
Users have been asking for you to open UEFI ("BIOS") settings > Boot  menu and there change the boot order to "Windows", not to select it in  the Grub menu. If this doesn't boot Windows directly and correctly you have a serious  (Windows) problem and that likely preceded you attempt to install  Ubuntu.

I think I understood tea for one's last message correctly. I'll recap my situation for clarity:
[LIST]
[*]Dual boot Windows/Ubuntu worked perfectly until Windows update yesterday. So it seems unlikely the problem predates my installation of Ubuntu. 
[*]Now, when I power on my computer without pressing any key, it boots straight to Ubuntu. 
[*]If I press SHIFT during start-up, GRUB menu doesn't appear, boot just proceeds to Ubuntu. 
[*]If I press Escape during start-up, a GRUB screen apprears with the message "Minimal BASH-like line editing is  supported..." and a command prompt. Typing "exit" in it boots to  Ubuntu. 
[*]If I press Delete during start-up, I can access UEFI settings. There, I can change my boot order, but placing Windows Boot Manager n°1 still boots to Ubuntu. 
[*]If I press F11 during start-up, I can access UEFI boot menu, which is not the same as GRUB or UEFI boot order setting. Windows Boot Manager does show up there, but nothing happens when I try to select it. 
[/LIST]

---

### Post by CelticWarrior on 2020-11-09
Then this is indeed a serious Windows problem.

Have you rebooted into Windows several times to allow Windows to finish the major update installation? If not and you booted Ubuntu and in any way, shape or form, accessed the Windows partition(s) and changed something there then it's game over: You need to boot Windows installation media and repair Windows. Actually regardless of the root cause that's exactly what you have to do now anyway.

---

### Post by benidukadu on 2020-11-09
> Have you rebooted into Windows several times to allow Windows to finish the major update installation?

Windows rebooted several times during the update. I let the update finish and was able to use Windows without problem afterwards.
The only issue I had was that my computer now booted straight to Windows instead of showing the GRUB menu as before. In Windows command line, I entered:

```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

which brought GRUB menu back, but then I couldn't boot to Windows anymore: when I selected Windows Boot Manager in GRUB, the screen just blinked and stayed on GRUB.
I've tried several things to repair this, but the only result I got is that now I can't access GRUB menu.

So, no choice but to repair Windows? Does that mean I'll have to reinstall Ubuntu as well afterwards?

---

### Post by tea for one on 2020-11-09
> **benidukadu said:**
> So, no choice but to repair Windows? Does that mean I'll have to reinstall Ubuntu as well afterwards?

If you de-activate, isolate or physically remove your Ubuntu drive, there is no reason why a repair procedure to your Windows drive will affect Ubuntu.

---

### Post by oldfred on 2020-11-09
What brand/model system?

Grub only boots working Windows, but that also means it cannot be hibernated which is normally turned back on with updates.
So for grub to boot Windows fast start up must be off.
You should be able to directly boot Windows from UEFI boot menu if fast start up is on, so you can turn it off.

You have two ubuntu entries in UEFI menu.
One uses Windows ESP on sda2 and other uses ESP on sdb1
But both use this entry, which has correct UUID, but hdX cannot both be hd1.
> search.fs_uuid 3ade1dc9-eaf0-4d77-b0a5-cc1430a05b7f root [COLOR=#ff0000]hd1[/COLOR],gpt2 

Boot drive is always hd0.

So which "ubuntu" entry, 0000 or 0002 are you having issues with. Try both and see if different issue.

---

### Post by benidukadu on 2020-11-09
OK so the issue was with Windows: in the end I just did a clean Windows install and now dual boot works perfectly again. I didn't update GRUB (what's the point if Windows updates break it every time?), instead I boot to Windows by default and I use the UEFI boot menu if I want to boot to Ubuntu.

There's one thing I'm unsure about. When I reinstalled Windows, I was too stupidly lazy to unplug my Ubuntu drive, and it appears Windows installed its EFI to the Ubuntu drive, since now "efibootmgr -v" gives me this:

```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0002,0000
Boot0000* ubuntu    HD(1,GPT,f2264043-6189-4956-8c75-1bd00fe8c99d,0x800,0xf3800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* Windows Boot Manager    HD(1,GPT,f2264043-6189-4956-8c75-1bd00fe8c99d,0x800,0xf3800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
```

The Windows Boot Manager line looks all weird too.

Should I worry about this? Again, zero problem so far.

Thank you all for your time and advice!

---

