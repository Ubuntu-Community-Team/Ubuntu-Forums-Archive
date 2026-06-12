---
title: "Big mess to my boot sequence and grub installation."
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by loopingz on 2020-05-05
I had the following:
Sda Not EFI - Grub2.04 - Win 10 - Ubuntu 20.04 - Swap

Then I installed mint cinnamon on sdc, which was formatted at install.
Sdc is now EFI and can boot cinnamon if I boot to sdc efi. But if I boot sda I have windows and ubuntu only (no mint)on sda.

So I went further and did some damage.
Destroyed ubuntu and swap from sda (it was dumb I know now)
Installed ubuntu alongside mint on sdc.

Now from sda grub cannot work (logic as I have deleted ubuntu parition). I would like at least to be able to boot windows from sda (imagine sdc failure), but evrything from sda would be great.
From sdc I boot to linux mint boot which looks different than bare grub. I can access either mint or ubuntu but not windows.
I tried boot-repair through mint ubuntu, installed and live. I have also tried boot-repair iso and supergrub2 iso. It either fail because of conflict with gpt or it pass but I have no difference at startup.

[http://paste.ubuntu.com/p/8K8mkyRxrS/](http://paste.ubuntu.com/p/8K8mkyRxrS/)

I can format sdc or unplug if necessary. I can do any iso on usb. I wish to maintain my windows partition and be able to boot it. My usb stick always appear as EFI in bios, I don't know if it is part of my problem. I have a2gb and a 16gb stick on hand.

But I don't know how to tackle my issues and in what sequence.
Any advice?

---

### Post by crip720 on 2020-05-05
Do not know enough to help, but main problem would seem to be mixing EFI and Not EFI(legacy).  Think you can have both, but for most people it is a PITA.  Think you will need to unplug sdc and use a windows repair disk/USB for windows.  If sda is legacy/MBR disk, sdc will need to be the same.  Need to check if sda is MBR or GPT and legacy or EFI.

---

### Post by oldfred on 2020-05-05
You have new UEFI hardware.
Microsoft has required vendors to install Windows in UEFI boot mode since 2012. But most Windows 7 systems were BIOS.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives.
Windows only boots in UEFI mode from gpt (GUID) partitioned drives.
You have to use gpt on drives over 2TiB, but smaller drives can be either MBR or gpt. Newer gpt highly recommended, unless you have to boot Windows in BIOS boot mode.

Your sda & sdb are MBR drives, so Windows in sda, must be a BIOS boot system.
But sda1 somehow was changed to FAT32 and looks like an ESP - efi system partition for UEFI boot. Windows has to have that partition as NTFS with boot flag to boot in BIOS mode. Do not reformat sda1, just change to NTFS and see if your Windows boot files are still there (it shows them now). If not you need your Windows repair disk to restore those boot files.
If you can copy them, it would be best to back them up, so if change back to NTFS erases them, you still have them.

Best not to mix UEFI & BIOS. Since newer hardware with UEFI, best to have Windows in UEFI boot mode, but that would be a total new install of Windows.

Since you have multiple drives, you can have sda in BIOS boot mode and sdc in UEFI boot mode, but can only boot from UEFI boot menu. Some older systems also needed you to change default UEFI setting from UEFI to Legacy/BIOS/CSM, most newer recognize boot mode and will boot.

Since you cannot change boot mode once you start booting, grub can only boot other installs in same boot mode.
You could keep gpt on sdc and convert installs to BIOS boot by adding a tiny 1MB unformatted partition with bios_grub flag using gparted. Then grub could offer to boot Windows. 
Or only boot from UEFI menu.

Note that Windows 7 is End of Life and should not be used.

---

### Post by loopingz on 2020-05-05
Thanks crip720 and oldfred.
sda was a windows 7 updated to 10. So it was a good old bios boot.
sda is around 500gb and sdc is around 120gb. They don't need to be UEFI.
Motherboard is 2011 (and still kicking), works with UEFI and autoswitch to harddrives with UEFI when there is a hdd partition change.
The fat32 on the sda boot partition seems strange, but I haven't touched that at least not voluntarily. The data is on the following partition which is ntfs and yeah I should make a copy.

So I guess that I should first restore windows alone, I am currently burning a pen drive.
Then I would better set the distro on sdc but not in GPT/UEFI, anything special to do during install not to arrive to that same situation? I guess I did a gpt mistake when installing Mint.
Should I format sdc to mbr and install ubuntu, is there a chance it would fix all boot without having to trust microsoft for the first step?

I tried to add the 1mb unformatted partition, but is is for sda, sdc or both? And gparted does not offer me the option of bios_grub: I can only set bios flag. I would love to manage this method.

I could also perform a clean install of windows gpt but I would loose days to setup everything again...

I will post progress tomorrow.

---

### Post by oldfred on 2020-05-05
You do not need to change any Linux drive or data drive to MBR.

I started converting drives to gpt with old BIOS only system in 2011, before UEFI. But had to have the bios_grub partition.
That partition is not required on MBR drives as there is space for grub just after MBR and before first partition. With gpt there is a protective MBR, but no space after the MBR as gpt structures start right away.

You have to convert sda1 to NTFS first, Windows may not even fix it unless it is NTFS with boot flag.

You can either add bios_grub to sdc and reinstall grub, so it uses the BIOS version of grub. Only one of your installs will then be in MBR and boot, but then grub will have all three in its boot menu.
But Windows 10 likes to turn fast start up back on or may need chkdsk. Then grub will not boot it. If you have Windows boot loader in MBR of sda, you then can directly boot it and maybe repair using f8 internal repair console. Best to have Windows repair/recovery flash drive.

---

### Post by loopingz on 2020-05-06
It looks like I managed to do the bios_grub partition, protip this flags exist only for gpt, so it worked well at the begining of sdc.
I enclosed my partition. I don't know how to set flags correctly on sda. Is boot sda1 or sda2?, same for esp?
So far windows tool is a total fail, but maybe it is all about setting the flags correctly. (see edit later)

sdc is a partitioning shame.

On last test I managed to boot from sda but sdc was not booting.

edit:
[https://paste.ubuntu.com/p/dmYfCbbHJd/](https://paste.ubuntu.com/p/dmYfCbbHJd/) 7.05utc
So I can boot windows or anything booting from sda.
[ATTACH=CONFIG]285760[/ATTACH]
Menu is like that. I think that I can remove or hide that windows 7 line which do not work well anyway. I guess win10 boot sequence is sda1 ==> sda2
Can I remove sda3? what is there? Maybe windows use it...
But I can't boot from sdc. Maybe another go at boot-repair?

To take it further, I would be glad to be able to boot from sdc too.
And also I would feel more confident not to loose windows boot in case of sdc failure. It is a ocz vertex 3, firmware up to date, no issue for me, but this drive has been a nightmare for a lot of people. Can I do some kind of minimal partition on sda to hae grub ok even with a sdc failure? My main goal at the beginning was to give a go at mint and to add some space on sda for windows. I will wait a bit before resize the main partition.


Huge thanks for the valuable input so far, and also for the pointed post.

---

### Post by oldfred on 2020-05-06
I do not use nor particularly like grub customizer. For a few minor changes, I guess it is ok.
It replaces all of grub with its own files with proxy files. Then it is not standard grub anymore.

Boot-Repair normally copies bootmgr & BCD from sda1 to sda2 as many users do not know that sda1 is a required Windows boot partition and just delete it. Usually those same users do not have backup nor Windows repair disk. So Boot-Repair copies the two essential boot files into main c: drive partition. But then grub sees both sda1 & sda2 as bootable which they then are. Standard Windows is to have small boot partition with boot flag, your sda1. But then probably ok to have either one with boot flag (not both).  
Reason for boot partition was in case main install partition was encrypted. But could make a difference if main partition needs chkdsk and then you may not be able to boot. The boot partition is not often written into, so less likely to ever need chkdsk or any repairs. But as long as you have repair/recovery flash drive you can always fix it.

You must have run auto fix in Boot-Repair. Not recommended. I need to talk to Yann on that. Again I believe he does this so no matter what drive is default in BIOS it will boot grub. Many new users do not understand BIOS settings.

When you have multiple installs on multiple drives, best to have each boot loader in that install's drive. 
Particularly now with Windows 10 and its fast start up which it keeps turning back on. Grub then will not boot it. And you have to directly boot. So you want Windows boot loader in MBR of Windows drive, so from UEFI/BIOS you can directly boot it ( & f8 for repairs) and maybe fix without booting your Windows repair/recovery flash drive.

You can use Windows to install the Windows boot loader to MBR of sda. Boot-Repair can install a Windows type boot loader to sda using Boot-Repair's advanced options where you select install & drive to put boot files into.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Looks like install in sda5 has converted to BIOS boot as mount of ESP (/boot/efi) is commented out. But install in sda4 still has mount of ESP. It just depends on which install you want to default boot as that is the one you need the grub installed to MBR. Updates may re-install grub and change default boot.

When I was first converting or planning on converting drives from my old BIOS system to newer UEFI system, I added ESP & bios_grub as first two partitions and had swap as last partition. Those should not normally need to ever change or be move. And then are out of way of any partition that may need resize or change. Now installer does not need swap partition but will use it. I have swap on sdb but for my new install on NVMe drive had to click on swap and say do not use. It then created swap file and did not use old swap. Have seen and had issues where new install reformats swap. The other install will not boot as UUID of swap changed.

---

### Post by loopingz on 2020-05-06
Thanks for the follow up. I need to digest a bit more all the info to start doing some updates and cleaning.
I have found something else bad. My motherboard propose sdc and another disk for boot, I need to check which one it is but it is not sda (i got confuse being almost the same size disk), so it is less than ideal.
As for the tools I have been using mainly boot-repair, some gparted and I tried grub customizer too. I guess the non standard stuff got me a working boot by luck. i thought it was cool for fast change boot menu order and timer.
I was about to launch boot-repair again and I canceled to save my day... The mistakes are very time consuming.

edit: booting disk:
[ATTACH=CONFIG]285773[/ATTACH]

---

### Post by oldfred on 2020-05-06
Since Boot-Repair installed grub to every drive, you system may now see that and add boot options.
But it is one grub that will only boot one system.
And grub should have given an error on trying to install grub to any gpt drive that did not have a bios_grub partition.

---

### Post by loopingz on 2020-05-07
In boot-repair what will go differently whether sdc is a removable disk or not? My understanding is that it would not boot as is if sdc was removed...
Current pastebin:
[https://paste.ubuntu.com/p/V72ymgwwhT/](https://paste.ubuntu.com/p/V72ymgwwhT/)

I tried to boot-repair only to sdc. It is strange because it does not boot this way from sdc, but it changes the boot menu from sda/sdb.
[ATTACH=CONFIG]285775[/ATTACH]

I have found my way into my motherboard, it is like boot sequence is managed differently with a UEFI disk in between.
I don't know why I have two different "ubuntu" option for sdc, they both fail currently.
I have a submenu where I can choose boot order for non uefi disk, there I can check sda and it boots.
[ATTACH=CONFIG]285774[/ATTACH]

I am feeling the "power" of UEFI... Now windows cannot stop, it kind of goes into sleep and then back to the login screen. No idea how to get that right. If I look at the pastebin, I guess something is wrong with windows...

---

### Post by oldfred on 2020-05-07
UEFI installs normally set up both grubx64.efi and shimx64.efi.
This will show that you have two UEFI entries.
sudo efibootmgr -v

But I thought you reinstalled grub in BIOS boot mode. Then you get the error you have on normal not found.
It also may be possible to have grub in MBR boot one install and UEFI boot other? Not sure I have seen that?

Windows is still hibernated. Grub will not boot it. Windows 10 turns it back on with many updates.
You have to use Boot-Repair and choose Windows & sda. Or you use your Windows repair disk. And then directly boot Windows from sda to be able to turn off fast start up.

Any entry in UEFI with a name is a UEFI boot entry. BIOS boot just boots to MBR. May or should show which drive.

---

