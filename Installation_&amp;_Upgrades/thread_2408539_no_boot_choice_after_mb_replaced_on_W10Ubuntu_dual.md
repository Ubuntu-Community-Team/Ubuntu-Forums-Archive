---
title: "no boot choice after m/b replaced on W10/Ubuntu dual boot system"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by dwater on 2018-12-19
A Dell engineer just replaced the motherboard on my Dell XPS 13 system, which has been dual booting between Windows 10 and Ubuntu for over a year, but now it no longer goes to the menu to choose between Ubuntu and Windows (it was Ubuntu by default).

Can anyone tell me what I need to do to get the boot menu back again?

I tried the BIOS changes that I think I had to make when I first installed Ubuntu, and had to turn off secure boot and some legacy support option, as mentioned on a web page that tells how to install dual boot the first time, but it hasn't made any difference.

---

### Post by TheFu on 2018-12-19
I'm guessing they fixed the Windows boot or allowed Windows Update to take over the boot sequence. I understand this happens about once a year on dual-boot systems with Windows now.


I'm making all sorts of assumptions which might not be true.   From a high level, I would
* boot from Ubuntu Flash media
* go into rescue mode
* setup a correct chroot so the installed Ubuntu is seen as the correct ubuntu. I think there are about 5 commands to do this.
* install grub to the HDD I intend (careful not to install to the wrong place)
* update grub
be happy.

Let me see if I can find a guide for doing these things "grub install ubuntu chroot" is the search term I'm using.
[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2) looks like what I intended to find, sorta.
There are many complications thanks to different partitioning types, LVM, RAID, encryption, legacy and UEFI booting and how your system is partitioned.

To be absolutely safe, we really need to see the output from a **boot-info** script.  [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)  The boot-repair tool has that capability, but isn't safe to blindly run anymore, so please don't do that. It is very tempting, but there's a difference between the system issues you have now and what might happen by running boot repair and it does more harm. There's a **boot info** button at the bottom of the boot-repair GUI - run that and post the URL.

---

### Post by oldfred on 2018-12-19
UEFI has its own memory, but if you have a new motherboard, you have to redo all the UEFI settings & add back UEFI boot entries.

Did you update drive settings in UEFI to be AHCI, default with most newer Dell is RAID or Intel SRT.

You can add UEFI boot settings or reinstall boot loaders completely which will add new UEFI entries.
Run the Boot-Repair summary report as suggested by TheFu and we can make further suggestions.
Boot-Repair in advanced mode to do a full reinstall of grub, walks you thru a minimum chroot.

---

### Post by dwater on 2018-12-20
Thanks guys, lots of clues there.

I've managed to boot into live ubuntu, and run the boot info command, which gives me this url:

[http://paste.ubuntu.com/p/xgMXpWcfdP/](http://paste.ubuntu.com/p/xgMXpWcfdP/)

Thanks for any further guidance.

TBH, I don't think he did a whole lot apart from replace the motherboard, and set the service ID, perhaps one other setting, in the BIOS. I'd guess it's a setting that 'came with' the new motherboard.

I did set the UEFI option and disable a couple of other ones - secure boot and legacy support - as mentioned in the guides for setting up a dual boot system.

---

### Post by oldfred on 2018-12-20
Even though new motherboard, I would suggest you check that it has latest UEFI from Dell and check if SSD's firmware is most recent version also.
If you do update you probably have to redo some or most of the settings. Back with BIOS you had to redo everything, but now UEFI does remember some settings, mostly the UEFI entries.

Does Windows boot from f12 and does the hard drive entry also boot Windows?
You show no UEFI entry for ubuntu.

Script is not as good about the new NVMe drives, so some info is missing.
Make sure Windows fast start up is off.
I would then just run the suggested repair by Boot-Repair.
If still issues then post a new version of report.

---

### Post by dwater on 2018-12-20
> **oldfred said:**
> Even though new motherboard, I would suggest you check that it has latest UEFI from Dell and check if SSD's firmware is most recent version also.


OK, I generally use Dell's Windows tool to do that, so I can do that again with this new m/b (I've not done it).

> **oldfred said:**
> If you do update you probably have to redo some or most of the settings. Back with BIOS you had to redo everything, but now UEFI does remember some settings, mostly the UEFI entries.


Hrm, ok. I don't recall doing anything in the past, when I've updated things, but perhaps I did; or just put up with problems (like some tool complaining I have no disk drive when I reboot Windows).

> **oldfred said:**
> Does Windows boot from f12 and does the hard drive entry also boot Windows?
You show no UEFI entry for ubuntu.


I'm not sure what 'f12' is.....trying it now I see some menu....'Boot mode is set to: UEFI; Secure Boot: OFF', and UEFI BOOT: 'UEFI: THNSN5256GPIK NVMe TOSHIBA 256GB, Partition 2'...and some other options.

> **oldfred said:**
> Script is not as good about the new NVMe drives, so some info is missing.
Make sure Windows fast start up is off.


Yes, I think I picked up on that from the dual boot setup instructions, so made sure it is off (I think it was on, as it happened).

> **oldfred said:**
> 
I would then just run the suggested repair by Boot-Repair.
If still issues then post a new version of report.

Cool, thanks.

---

### Post by oldfred on 2018-12-20
Your UEFI boot menu should have Windows, ubuntu & a drive boot option (your NVMe Toshiba option).

The drive boot option is a UEFI fallback boot and is /EFI/Boot/bootx64.efi. That is the same file location as both Ubuntu & Windows installers and is required for external drive boot. But it is available as a boot option (fallback) for internal drives if other options do not boot. A few systems will only boot Ubuntu using the fallback.
 
The bootx64.efi file is normally a copy of Windows boot file, so it just is another way to boot Windows. But Boot-Repair will back that file up and copy shimx64.efi to be bootx64.efi. Then you should have ubuntu boot entries and a fallback that boots Ubuntu also.

---

### Post by dwater on 2018-12-20
I couldn't get boot-repair to do anything useful - it doesn't have the option to repair anything, just the prompt to do a back-up and then to create a bootinfo summary. I tried updating things in general, but to no avail...it still doesn't give me any 'recommended repair' or 'advanced' option as on this image:

[https://pix.toile-libre.org/upload/original/1335260967.png](https://pix.toile-libre.org/upload/original/1335260967.png)

I'm not sure where to go from here :/ Any ideas?

---

### Post by oldfred on 2018-12-20
Do not need link to Boot-Repair thread, I closed that a long time ago.

But report said this, can you not run it now?:
      >  The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of nvme0n1p6, using the following options:        nvme0n1p2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file 



---

### Post by dwater on 2018-12-21
> **oldfred said:**
> Do not need link to Boot-Repair thread, I closed that a long time ago.

But report said this, can you not run it now?:

Eh? I linked that page for the image of the utility as it is supposed to be, and noted that, when **I** run it, I don't have any options to repair anything, so it doesn't do anything. Perhaps I should have just linked the image itself:

[https://pix.toile-libre.org/upload/img/1315191717.png](https://pix.toile-libre.org/upload/img/1315191717.png)

I don't have the 'recommended repair' or 'advanced options' options - only 'Create a Bootinfo summary (to get help by email or forum)', and 'About' and 'Quit' buttons...so I don't think I've had the opportunity to have boot-repair do the below:

> **oldfred said:**
> [COLOR=#000000]*The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of nvme0n1p6, using the following options: nvme0n1p2/boot/efi,*[/COLOR]
[COLOR=#000000][I]Additional repair would be performed: unhide-bootmenu-10s fix-windows-boot use-standard-efi-file
[/I][/COLOR]

[COLOR=#000000][I]I'm still not sure what to do next.

Any reason I'm not getting the repair options in boot-repair?[/I][/COLOR]

---

### Post by oldfred on 2018-12-21
Are you running Boot-Info and not Boot-Repair?

Boot-Info, but it shows advanced options where you manually select changes/fixes.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dwater on 2018-12-21
> **oldfred said:**
> Are you running Boot-Info and not Boot-Repair?

Boot-Info, but it shows advanced options where you manually select changes/fixes.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Well, I have to say I am sure I was running boot-repair and not boot-info, but you questioning it made my try it again and this time it worked. I was following the instructions on this page:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

'2nd option'

and I did the same thing again (I still had the same page open), so I'm (close to) 100%. In any case, the UI didn't look even like the boot-info command, so I'm still pretty sure.

However, all's well that ends well since this time I *did* have the options as expected and it actually brought back the boot menu - though it is different, but hey ho.

One thing I did differently this time was to do 'sudo apt update && sudo apt upgrade' before installing boot-repair. Perhaps that made more of a difference than I was expecting.

Thanks very much for the help :D

---

