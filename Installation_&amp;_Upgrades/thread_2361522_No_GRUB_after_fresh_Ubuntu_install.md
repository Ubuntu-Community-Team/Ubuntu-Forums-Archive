---
title: "No GRUB after fresh Ubuntu install"
date: 2017-05-17
forum: Installation &amp; Upgrades
---

### Post by mdobrenko on 2017-05-17
[COLOR=#242729][FONT=Arial]I have a Microsoft Surfacebook, and tried to install Ubuntu 17.04 via a bootable USB (not a dualboot setup). I previously had Windows 10 (not dualboot) and had it removed via the Linux installation (clear all existing data).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After the installation indicated everything was successful, I restarted my computer, only to find that there was no GRUB loader. It showed the SurfaceBook logo/loading screen, which flashes a few times (odd) and then just goes into the BIOS menu. I checked the boot sources, and Ubuntu was nowhere to be seen -- the Windows Boot Manager is also missing.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I therefore ran the boot-repair-tool for Linux, and everything was seemingly 'fixed' after it ran (according to the success message). Here is the output:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][http://paste.ubuntu.com/24591526/](http://paste.ubuntu.com/24591526/)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have tried different Linux distributions (these resulted in the same problem), as well as Windows from a bootable USB (it was simply ignored altogether during boot -- worked fine on my other machines, however).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have run out of ideas at this point -- any help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by oldfred on 2017-05-17
Did you use the Boot-Repair live version which is now old and does not support newer NVMe drives?
Better to use the Ubuntu live installer and add Boot-Repair with ppa.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

You are missing ubuntu entry in UEFI. But some systems only boot the fallback or hard drive entry at /EFI/Boot/bootx64.efi. Boot-Repair will copy shimx64.efi to be that file, but probably will not add UEFI entry which we can do if needed.
Since only booting Ubuntu another work around is to in effect change UEFI description from "ubuntu" to "Windows Boot Manager", since UEFI checks description not actual boot file which needs to be shimx64.efi or grubx64.efi.

With only Ubuntu, you will not normally get grub menu, unless you press escape key, perhaps more than once from UEFI but before grub loads & starts booting kernel.

More details in workarounds for UEFI systems in link in my signature.

Bit older version of Ubuntu:
[https://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](https://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)

---

### Post by mdobrenko on 2017-05-17
I went ahead and ran these commands -- seems to have ran successfully. 
This time around, however, when I boot up instead of just getting the flickering screen and general process described earlier, I get these messages:
```

Failed to open \EFI\BOOT\grubx64.efi - Not found
Failed to open \EFI\BOOT\grubx64.efi: Not found
start_image() returned Not Found
```

Sounds to me that the entry may be missing, or it is named incorrectly? How does one add the UEFI entry?

---

### Post by oldfred on 2017-05-18
UEFI only boots external drives from /EFI/Boot/bootx64.efi. It can use that as fallback to boot internal drives also.
I copy both grub & shim (all of /EFI/ubuntu) into /EFI/Boot on internal drive and rename shimx64.efi to bootx64.efi, but still have a (non-usuable) grubx64.efi in /EFI/Boot.
Live installers for both Ubuntu & Windows will have /EFI/Boot/bootx64.efi (different actual files) for UEFI boot.

       Check entry is there.
sudo efibootmgr -v  

see this for details:
man efibootmgr

Depending on if ESP - efi system partition is sda1 or some other drive/partition makes a different on commands. The efibootmgr defaults to sda1 for ESP. If any  other drive or partition you have to specify.

An example, more in link in my signature.

 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2
 sudo efibootmgr -c  -l *EFI*ubuntu/shimx64.efi -L "ubuntu" -d /dev/sda -p 2

---

### Post by mdobrenko on 2017-05-18
The output of ```
sudo efibootmgr -v
``` is:
```

BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0001,0002
Boot0000* Internal Storage    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)SDD.
Boot0001* USB Storage    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)USB.
Boot0002* PXE Network    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)PXE.
Boot0003* MsTemp    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/USB(0,0)/HD(1,MBR,0x4294967177,0x800,0x3b8200)

```

I could not tell which one to pick based on that output -- but gathering from the command you listed, I took this info from g-parted:



And ran the following command:
```
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/nvme0n1 -p 1

 
```

Got this output:
```
Could not prepare Boot variable: No space left on device
```

Any idea why this happens? Is my command incorrect?

---

### Post by oldfred on 2017-05-18
Please attach screen shots, not post in line.
Some do not have faster Internet.
You can easily attach with Forum's advanced editor and paper clip icon.

Do you have a file /EFI/Boot/bootx64.efi in ESP?
You often have to copy shimx64.efi from internal drive to be that file.
And that version of shim/grub has to also have all of /EFI/ubuntu folder as it looks for other files in that location.

Post Summary Report from Boot-Repair.

---

### Post by Vic_Paine on 2017-05-19
The flickering seems to be a hardware problem on boot, my surface book does it even after the latest USB reload from MS. Which to be fair did cure a load of other problems and made the thing actually useable.  Sorry I can't help with your major problem though.

---

### Post by mdobrenko on 2017-05-20
Closing this thread as the circumstances have changed, so much that the original post is too far off (installed Windows 10, needed to have my machine for work) -- still having problems installing dualboot ubuntu, however. Posting a new thread.

---

