---
title: "cannot boot into windows after dual booting"
date: 2019-11-03
forum: Installation &amp; Upgrades
---

### Post by kneehar on 2019-11-03
I tried to set up a dual boot for ubuntu 18.04 next to windows 10. My setup is, I have a 128GB SSD with my windows installation on it, and a 1TB HDD with my windows files. I shrunk off 150GB from my HDD for ubuntu, and installed a 32GB swap, ~700ish MB EFI sector for booting (followed a tutorial that recommended doing so) and the rest for my root. After installing, I tried to set up grub. It was able to boot into ubuntu just fine, but there was no entry for windows. I ran the boot-repair utility, to no avail. At first, I was able to use my boot manager to still get into windows if needed. But either the boot manager or running ```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
``` as was recommended by some other sites, now makes using the boot manager to get into windows just load grub again, making windows inaccessible right now.

Pastebin link for my boot-repair attempt: [http://paste.ubuntu.com/p/sRK8t6QncG/](http://paste.ubuntu.com/p/sRK8t6QncG/)

I am no expert, but here's extra info that I think is correct and may be of use:
I tried to install ubuntu under UEFI, I loaded the live usb with UEFI and performed the installation with that. Running os-prober does not print anything. I am able to mount my ssd filesystem by clicking on it in nautilus, and I can see the root fs, but if I try to go into any subdirectories (Users, Windows, Program Files, etc.) I get the error 'Sorry, could not display all the contents of "Windows": Error when getting info for "/media/user/<uid>/Windows/explorer.exe": input/output error'.

Any assistance in being able to access Windows again would be greatly appreciated! Thanks in advance!

---

### Post by ajgreeny on 2019-11-03
I suspect you have not disabled fast-start on your Windows installation so grub could not add it properly during the installation of Ubuntu.

It will help us more to see all the details of where you really are at present so see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may give us more clues as to what has happened..

---

### Post by yancek on 2019-11-03
Posting the output of the boot repair script from the Create BootInfo Script option is your best bet now as suggested above.  Did you read the Ubuntu documentation on dual booting UEFI with windows 10 at the link below before trying the install?   

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-11-03
UEFI and BIOS are not compatible.
Or once you start booting in one boot mode, you cannot switch. And then grub can only boot other installs in same boot mode.
I believe UEFI's one time reboot can be used by some systems to in effect convert boot from one to another.
But best to have all installs in same boot mode. 
And since Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since Windows 8 released in 2012, better to use UEFI/gpt.

Your Windows is installed in the old BIOS/MBR boot mode.
It looks like Boot-Repair reinstalled grub in BIOS boot mode. The mount of the ESP - efi system partition is commented out in fstab.

Now that both systems are booting in the old BIOS boot mode, you still have issue of Windows fast start up or other Windows issues.
Grub only boots working Windows or Windows that is not hibernated.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) & 

Since newer UEFI hardware, better to eventually plan on backing up all your data and reinstalling both Windows & Ubuntu in UEFI boot mode. But that is a major task with Windows. How you boot install media UEFI or BIOS for both Windows & Ubuntu is then how it installs.

---

### Post by kneehar on 2019-11-03
Thanks for your replies!

I ran boot-info and the results are here [http://paste.ubuntu.com/p/pYwHzykx7F/](http://paste.ubuntu.com/p/pYwHzykx7F/)

For the fast startup, I followed this tutorial [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) and did disable both fast startup and hibernation, and then disabled secure boot afterwards.

I admittedly did assume my windows was UEFI, and didn't double check. I checked that it was MBR instead of GPT since tutorials were saying that it's important, but went no further and assumed it must be UEFI and that I needed to install Ubuntu the same way. The original Windows OS was not from a vendor, I had a vendorless license key and just let it make the decisions for me as far as what gets installed where and when (this was back in 2014), so I do not recall if it gave me an option for UEFI vs BIOS or how that was chosen. In hindsight I should have definitely done more research on what these acronyms mean...will probably do that before attempting any other fixes. That said, if anyone has any ideas from the boot-info as to whether there is an easier fix than re-installing windows and ubuntu, I'd love to hear it!

Also looking into the link you posted yancek, wrt converting Ubuntu into legacy mode, if that's the correct way to go about this.

Thanks again!

---

### Post by oldfred on 2019-11-03
How you boot install media UEFI or BIOS, is then how it installs. UEFI/BIOS should show two boot entries for a flash drive installer.
Back in 2014 UEFI had only been out for a year and a half, and both UEFI, Windows & Ubuntu often had to have updates to work well with UEFI.

Grub only boots working Windows. And when Windows updates turn on fast start up or Windows is corrupted and needs chkdsk, grub will not boot it.
You should have Windows boot loader in SSD's MBR, so you can from UEFI choose to directly boot that drive. You may then be able to use Windows internal repair console to make repairs. But also best to have a Windows repair disk or installer with repair console and Ubuntu live installer  for current installed verisons always available.

If Windows is not hibernated, Boot-Repair may in its advanced options let you install syslinux which is a Windows type boot loader to Windows drive. Or use your Windows repair disk to run fixMBR to install Windows boot loader.

You really do not need large swap unless editing videos and then you want unlimited amounts of RAM. If you have 4GB of RAM or more, you may not use swap at all. New installs now use a swap file, but do use the swap partition if found.

I also started converting drives to gpt before UEFI became Windows standard. I had to have a bios_grub partition for grub to install in BIOS boot mode.
But then when Windows standardized on UEFI/gpt, I started adding both bios_grub for current boot and an ESP - efi system partition for future boot. Then I could move drive to new UEFI system without having to totally repartition and reformat.

---

