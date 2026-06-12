---
title: "Late 2019 Computer Upgrade King Hewlett Packard Omen 15t: GRUB2 installation failed"
date: 2020-12-04
forum: Installation &amp; Upgrades
---

### Post by Welly Wu on 2020-12-04
I own a late 2019 Computer Upgrade King Hewlett Packard Omen 15t gaming notebook PC with the following specifications:

[COLOR=#050505][FONT=&amp]Late 2019 Computer Upgrade King Hewlett Packard Omen 15t[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Microsoft Windows 10 64-bit Pro edition version 20H2[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]15.6” 323 nit, 1.88 Delta-E, 240 Hz 1920 X 1080P FHD with Nvidia G-SYNC[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Intel 9th generation Core i9-9880H mobile CPU[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Nvidia Geforce RTX 2080 Max-Q 8 GB GDDR6 VRAM mobile GPU[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]64 GB DDR4 2,666 MHz SO-DIMM RAM[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]2 TB ADATA SX8100NP M.2 PCI-e NVMe x4 SSD[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]1.92 TB Kinston A400 SATA-III 6 GB/s SSD[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]3x Super Speed USB 3.1 generation one Type-A (1x HP Sleep & Charge)[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]1x Super Speed USB 3.1 generation two with MiniDisplay Port 1.2, USB Type-C Power Delivery and Intel Thunderbolt 3 x4 PCI-e lanes[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]SDXC UHS-1[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]MiniDisplay Port 1.4[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]HDMI 2.0B[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]802.11 dual-band AC MU-MIMO Wi-Fi[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Bluetooth 4.2[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Gigabit Ethernet[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Four-zone RGB backlit keyboard[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Elan touchpad with Microsoft Precision drivers & discrete left/right buttons[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]69 WHr lithium-ion battery[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]200-watt HP slim power adapter[/FONT][/COLOR]
[COLOR=#050505][FONT=&amp]Headphone-out & Audio-in Combo Jack, Card Reader (SD/MMC)

I recently updated the BIOS version to F.35 using the Hewlett Packard BIOS update utility by copying the files to a FAT32 formatted USB 2.0 1 GB thumb drive and restarting my PC by pressing the escape button and clicking on diagnostics to be followed by firmware manager and then selecting the appropriate BIOS F.35 files. It updated my BIOS version to F.35 successfully after a couple of restarts of my PC.

Mr. Thomas Winters wrote his Medium article here: [https://twinters.medium.com/dual-booting-hp-omen-15-laptop-with-windows-10-ubuntu-276e19cc80dd](https://twinters.medium.com/dual-booting-hp-omen-15-laptop-with-windows-10-ubuntu-276e19cc80dd). He details step-by-step instructions on how to prepare Ubuntu 18.04 64-bit LTS to create a bootable USB thumb drive, configure his 2019 HP Omen 15 by restarting his PC and pressing the F10 button to get into the HP UEFI and then selecting the thumb drive as his first boot device along with enabling legacy mode and disabling Microsoft Secure Boot prior along with saving the changes. Restarting his 2019 HP Omen 15 and then booting up from the Ubuntu installation USB thumb drive involves getting into the GRUB2 bootloader and modifying the parameters including pci=nommonconf modprobe.blacklist=nouveau. I learned by doing this in the past to also add ACPI=off to the parameters to be able to boot up into the Ubuntu live environment.

My problem is that the GRUB2 bootloader keeps failing to install. I tried to install Ubuntu 20.04.1 64-bit LTS both with the logical volume management and full-disk encryption options checked and I tried it again by using the default partition layout without full-disk encryption enabled and turned on. Each time, GRUB2 fails to install and I can not boot up Ubuntu 20.04.1 64-bit LTS GNU/Linux on my late 2019 CUK HP Omen 15t gaming notebook PC.

Please note that I chose to install Ubuntu on my secondary Kingston A400 SATA-III 6 GB/s 1.92 TB solid-state disk each time. Microsoft Windows 10 64-bit Pro edition version 20H2 is installed on my ADATA SX8100NP M.2 PCI-e NVMe x4 2 TB solid-state disk and I want to keep it that way. I already used the latest version of Kingston SSD Manager in Windows 10 to check for the latest firmware update for my Kingston A400 solid-state disk as I already know that this brand and product model sometimes has technical issues when it comes to installing GNU/Linux distributions and versions bare metal on it on a PC if the firmware version is too old.

I was able to install Linux Mint 20.0 64-bit "Ulyana," Red Hat Fedora Workstation 33 64-bit, and System76's Pop_OS! 20.04.1 64-bit GNU/Linux on my late 2019 CUK HP Omen 15t on the Kingston A400 SSD in the past, but I want to install Ubuntu 20.04.1 64-bit LTS GNU/Linux on it successfully in the near future. I only want to use Ubuntu proper as my chosen GNU/Linux distribution on my HP PC in the future.

If anyone can help, then please reply. Thank you.[/FONT][/COLOR]

---

### Post by tea for one on 2020-12-05
Isolate, de-activate or physically remove the drive you do **not** want to use.

Only leave the target drive in the PC.

Please use UEFI mode and GPT (assuming your other drive is also configured with UEFI mode and GPT)

Try the installation again..........any errors?

---

### Post by Welly Wu on 2020-12-05
It has been some time since I last attempted to install Ubuntu 20.04.1 64-bit LTS GNU/Linux bare metal on my late 2019 CUK HP Omen 15t gaming notebook PC. As for your recommendation to deactivate, disable, or remove the internal disk drive that is not going to be the target drive for an Ubuntu installation, I am going to wait and see responses from others within this community before I give it serious consideration. Per your recommendation to re-enable UEFI, Mr. Thomas Winters in his Medium article specifically instructs his readers to disable UEFI by enabling legacy CSM as well as Microsoft Secure Boot. Why would you recommend to re-enable UEFI? I already disabled UEFI and I enabled legacy CSM while disabling Microsoft Secure Boot, but I have not attempted to install Ubuntu on my Kingston SSD yet. I would like to wait for responses from other community members before deciding which one to pick before I re-attempt an Ubuntu installation. I am not going to enable and turn on logical volume management or whole disk encryption during my next attempt to install Ubuntu on my HP PC again. My research indicates that whole disk encryption is not compatible with some HP PCs and my past experiences prove that to be a fact. I may decide to download updates and to enable third-party codecs and drivers, but I would appreciate feedback from other members with similar 2019 HP Omen 15 gaming notebook PCs to see if checking off those two boxes within the Ubuntu Ubiquity installer will cause GRUB2 to fail to install yet again. I am a bit skittish about trying to install Ubuntu on my HP PC for now and I am open to reading feedback from other affected community members to gather more technical research and to do my own and share it with future edited replies to my own thread. I am in research mode right now so I think it would be best to collect reliable and trustworthy sources of information before proceeding with another Ubuntu installation in the near future. Please let me know what I should consider if other community members own 2019 HP Omen 15 gaming notebook PCs and someone else has installed Ubuntu successfully and how you were able to do so. Thank you.

I tried everything and Ubuntu's Ubiquity installer keeps failing to install the GRUB2 bootloader successfully. I tried with UEFI + GPT = failure. I tried legacy CSM + GPT = failure. I tried legacy CSM + MBR = failure.

In the past, Linux Mint 20.0 64-bit "Ulyana," System76's Pop_OS! 20.04.1 64-bit, and Red Hat Fedora Workstation 33 64-bit along with Manjaro 20.1 64-bit "Mikah" installed successfully on either the ADATA or Kingston SSDs on my late 2019 CUK HP Omen 15t gaming notebook PC. I think that I am not going to be able to install Ubuntu proper successfully given that Canonical + HP Omens are not compatible. I am going to take a break and consider competing GNU/Linux distributions and versions for now. I may not try to reinstall Ubuntu proper on my HP PC again. I may not update this thread in the future.

---

### Post by tea for one on 2020-12-05
Your Windows 10 OS - is it installed in UEFI or Legacy BIOS mode?

---

### Post by Welly Wu on 2020-12-05
My Windows 10 is installed in UEFI mode. Originally, Secure Boot was disabled because I downloaded the Windows 10 20H2 .ISO file and used Rufus to create an installation USB thumb drive. Rufus tells its end-users to disable Secure Boot so the Windows 10 installation thumb drive will boot up properly to install it on your PC.

I tried almost every possible way to install Ubuntu proper on my HP PC and it is still no dice. I am considering to reinstall Red Hat Fedora Workstation 33 64-bit GNU/Linux on my Kingston SSD again. It is so cutting-edge that almost all of my installed PC hardware components are properly detected with the correct firmware and device drivers installed automatically. Heck, my Intel Sound Open Firmware, ALSA, Pulseaudio, ALSA-UCM just work with my internal laptop speakers and my digital microphone array so I can use my Microsoft Skype subscription to make and receive telephone calls worldwide. I can use Facebook telephone and video chat with Chromium-based or Google Chrome web browsers just fine. The only thing that I do not like about Fedora is that some Ubuntu-specific software packages and third-party products are not available like VPNSecure.Me and Perfect-Privacy VPN which I subscribe to. AirVPN and Ivacy VPN just work along with Microsoft SSTP VPN protocol for Ivacy. I have no problems with my other favorite cross-platform free and open-source along with closed-source, commercial, and proprietary software products while using Fedora and they sure as heck are compatible with Ubuntu-based GNU/Linux distributions.

I think that I am going to have to go back to Fedora again. Based on fairly recent past history on my late 2019 CUK HP Omen 15t gaming notebook PC, it was the best fit and a compelling alternative to Windows 10. If I do reinstall it on my Kingston SSD, then I am not going to enable and turn on LVM or whole disk encryption again. It is the whole disk encryption on my Kingston A400 SSD that particularly kills disk I/O performance to a slow crawl. This Kingston A400 brand and product model of SSDs is known to be troublesome with bare metal installations of BSD UNIX, GNU/Linux, and Open Solaris free and open-source desktop operating systems. I need Windows 10 to keep the Kingston A400 firmware up to date or it may fail. Furthermore, I should share that the Kingston A400 SSD is known to slow down to a few kilobytes per second in terms of disk I/O performance randomly when a GNU/Linux distribution is installed on it bare metal inside a PC. When I bought it, I thought I had sworn off free and open-source desktop operating systems and I originally intended for it to be used as a budget-priced SSD product to store mass data. Whole disk encryption regardless of the host desktop operating system or third-party software applications or products slow down the Kingston A400 SSD product models quite severely in my research and direct experience.

---

### Post by tea for one on 2020-12-05
> **Welly Wu said:**
> I tried almost every possible way to install Ubuntu proper on my HP PC and it is still no dice. 

My suggestion in post 2 has not yet been tried because, quite correctly, you say
>  I am going to wait and see responses from others within this community before I give it serious consideration

Well, I agree - it is important to be cautious and examine all possibilities as forensically as possible.

I wish you luck with your research.

---

### Post by Welly Wu on 2020-12-05
I have erased my USB 3.0 4 GB thumb drive and it has been written with Red Hat Fedora Workstation 33 64-bit so I can plug it into my HP PC or just about any other PC that I own and install it bare metal. I have given up on trying to install Ubuntu proper on my HP PC as my repeated failures are due to the fact that Hewlett Packard violates the UEFI standard by creating descriptors within their locked-down UEFI. The HP Omen 15 UEFI is non-standard and it is non-compliant with the UEFI standard. This is why Ubuntu keeps failing to install GRUB2. Yet, it can also be written that other owners of HP Omen 15 PCs have had similar failures in installing older and current Ubuntu proper versions as well based on my research due to GRUB2 failing to install successfully. It is this combination of my 2019 HP Omen 15t and the Ubuntu Ubiquity installer that keeps producing the same failure to install GRUB2 successfully and I have to cut my losses and move on based on my ongoing research. Even if I were to install Ubuntu 18.04.x 64-bit LTS or 20.04.1 64-bit LTS on my 2019 HP Omen 15t, the problem is that the Linux kernel versions at 5.4 and earlier are not fully compatible with my Intel Sound Open Firmware which means that my internal speakers and the digital microphone array will not be detected and they will both show dummy outputs until I update ALSA, Pulseaudio, ALSA-UCM, and upgrade to Linux kernel 5.8.x 64-bit based on past experiences with System76's Pop_OS! 20.04.1 64-bit which also uses Linux kernel 5.4 not to mention Linux Mint 20.0 64-bit "Ulyana" that uses the same Linux kernel version. Current Ubuntu proper and Ubuntu-based GNU/Linux distributions based on the 20.04.x 64-bit LTS base simply are not up to date enough for my 2019 CUK HP Omen 15t to ensure the maximum level of compatibility with the installed PC hardware components based on research and past experiences.

Red Hat Fedora Workstation 33 64-bit GNU/Linux and Manjaro 20.1 64-bit "Mikah" GNU/Linux are two few exceptions to this rule. Both installed successfully and Manjaro allows me to choose the destination of where to install the GRUB2 bootloader within their Calamares installer so both Manjaro and Windows 10 will not conflict with each other on separate internal disk drives on the same PC. Furthermore, Manjaro sets the date and time correctly and automatically so there is no discrepancy between Manjaro and Windows 10 on the same PC regarding the date and time. I am hesitant to use Manjaro again because my extensive past history in using different GNU/Linux distributions and versions taught me valuable lessons including that choosing Ubuntu-based, Red Hat-based leads to greater compatibility with PC hardware components, attached devices, and especially with regard to software packages and products. The further away I get from Ubuntu or Red Hat based distributions by choosing another competing distribution that is in of itself a fork of a parent distribution, I wind up with more complexity and I must do more highly specialized technical research and hard work to get my favorite cross-platform software packages and products installed and running as best as possible. This is the case with Arch and Manjaro in my past experience; I usually need to use the AUR to download and build software packages simply because Ubuntu and Red Hat based distributions already include what I want and need while Arch and Manjaro based distributions make me search the AUR and build software packages manually and to repeat this process for software updates in the future. Building software from PKGBUILDS or source code sometimes leads to failures due to missing software dependencies, misconfigurations in the compiler or missing software packages needed to build software in the first place, and a whole host of other technical issues based on my past experiences.

Fedora is my best chance at this moment, but I am hesitant to install it on my Kingston A400 SSD. Part of me wants to give up on using free and open-source desktop operating systems on current and future PCs. I have a mid-2015 Apple Macbook Pro 15" with Retina Display high-end mobile workstation that runs macOS 11.0.1 64-bit "Big Sur" almost flawlessly since it was released. I have a late 2019 CUK HP Omen 15t gaming notebook PC that runs Microsoft Windows 10 64-bit Pro edition version 20H2 almost flawlessly. I own a mid-2018 Huawei Matebook X Pro ultrabook that also runs the same Windows 10 version almost flawlessly. I have switched between Windows 10 and GNU/Linux repeatedly in the past. I have switched between Windows 8.1 and older GNU/Linux distributions repeatedly in the past. I have used almost every major versions of Microsoft Windows and older GNU/Linux distributions repeatedly since June 2009. This pattern of switching back and forth is driving me crazy and I was diagnosed with Schizo-Affective Disorder by my psychiatrist in June 2009 at my local hospital and I was admitted on an in-patient basis voluntarily for two weeks for psychiatric evaluation, treatment and long-term care management including medication. My psychiatrists and psychotherapists told me to stop using free and open-source desktop operating systems on my former and current PCs because each one drives me batshit crazy.

---

### Post by oldfred on 2020-12-05
If Windows & system is UEFI, you should install in UEFI boot mode to gpt partitioned drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 


Technically you can install in the now 40 year old BIOS boot mode, but then can only boot from UEFI boot menu, not from grub.
UEFI & BIOS/Legacy/CSM modes are not compatible. Once you start to boot in one mode, you cannot switch. Or grub can only boot other installs in same boot mode.
I believe that rEFInd, can use the UEFI one time reboot to boot installs in other boot modes, it is actually rebooting or booting directly from UEFI.

HPs have not been UEFI dual boot friendly. 
But other installs do not use Ubuntu's Ubiquity installs and let you install to some other ESP, than the one on the first drive.

---

### Post by Welly Wu on 2020-12-07
I reinstalled Red Hat Fedora Workstation 33 64-bit GNU/Linux on my Kingston A400 SATA-III 6 GB/s 1.92 TB solid-state disk using UEFI with Microsoft Secure Boot disabled. Fedora installed successfully and 99.9% of my recent installed PC hardware components were detected with the appropriate firmware and device drivers installed. I spent the past few days getting Fedora up to my high standards of usability by installing a slew of first and third-party software repositories, packages, and products and I am almost done with my fresh installation. I used Timeshift to create a RSYNC backup of my root partition and Deja-Dup with duplicity to make a backup of select folders within my home folder to my QNAP TS-251B 2 TB RAID-1 network-attached storage product. Fedora is working just fine and I logged into my online account at Fedora Forums. For some reason, Ubuntu proper refuses to install the GRUB2 bootloader, but Fedora installed it successfully on the first attempt to my Kingston A400 SSD. I am not anticipating that future Microsoft Windows 10 64-bit Updates should overwrite the GRUB2 bootloader on my Kingston A400 SSD and I do not expect to need to use Boot-Repair in the future. Fedora just works on my recent late 2019 CUK HP Omen 15t gaming notebook PC and it does so very well with excellent compatibility with my installed PC hardware components and attached devices along with the reliability and stability of a modern GNU/Linux distribution and version along with full-throttle PC performance when compared to Microsoft Windows 10 64-bit Pro edition version 20H2. I love Fedora and I still like Ubuntu and its forks as well. I chose the standard partition scheme and I did not enable and turn on whole disk encryption for enhanced and improved performance. I use GNU Privacy Guard and Microsoft Encrypting File Service to encrypt select folders and individual files and I backed up my public and private keys within my keyring as well as my certificates and encryption keys. Fedora is wonderful with the latest GNOME 3.38.x 64-bit desktop environment and I did technical research to discover and install my favorite GNOME shell extensions and I am not experiencing technical issues in using GNOME yet. This is the ideal dual-boot configuration and setup for my personal use cases and workflow and I love using both desktop operating systems on the same HP PC. So, this is quasi-solved in a different manner.

---

### Post by P-I H on 2020-12-08
I think this might be related to the "Fast Startup" setting in W10. When this is enabled the first disk, nvme or SSD, is locked for writing and as Ubuntu always install Grub in the first disk, it's not able to do this.
Fedora does it in another way and install Grub on the same disk as the installation disk, in your case the Kingston disk.
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by Welly Wu on 2020-12-09
You may have pointed out something that I had read about prior to installing Ubuntu proper, but I forgot to disable within Microsoft Windows 10 64-bit Pro edition version 20H2 on my late 2019 CUK HP Omen 15t gaming notebook PC. I never disabled Microsoft Windows Fast Boot and I had read to disable it prior to attempting to install Ubuntu proper. This may be the final technical reason that causes the GRUB2 bootloader to fail to install successfully on my HP PC. Nevertheless, I would prefer to continue enjoying Red Hat Fedora Workstation 33 64-bit GNU/Linux on my Kingston A400 SSD in a dual-boot configuration for now. I am reconsidering to turn off Microsoft Fast Boot and reinstall Ubuntu 20.04.1 64-bit LTS GNU/Linux, but I am concerned that the Ubiquity installer will install GRUB2 on my ADATA SX8100NP SSD and future Microsoft Windows 10 64-bit Updates will overwrite the GRUB2 bootloader and I would need to boot into an Ubuntu live environment to download, install, and use Boot-Repair in the future periodically. I would prefer not to have to go through that and I know that I can create a custom partition scheme to achieve just that result within the Ubiquity installer, but it is a hassle. I would reconsider attempting to reinstall Ubuntu proper after disabling Microsoft Fast Boot for the reason that some Debian and Ubuntu software packages are available which are required by some of my third-party software products and an Ubuntu environment is more user-friendly than competing GNU/Linux distributions and versions in my extensive past history of using free and open-source desktop operating systems. So, let me think about making these requisite changes and consider if I want or need to attempt another Ubuntu proper installation in the future, but I am keeping my eyes and ears open to new feedback for my own consideration. Thank you.

I can not disabled and turn off Microsoft Windows 10 64-bit's Fast Startup feature on my late 2019 CUK HP Omen 15t gaming notebook PC. I followed this guide here: [Windows 10 Fast Startup: How to Disable it and Why You Should (winbuzzer.com)]("https://winbuzzer.com/2020/05/19/how-to-disable-windows-10-fast-startup-hiberboot-hybrid-boot-hybrid-shutdown-xcxwbt/"). The "turn on fast startup (recommended) is not displayed which means that I can not turn it off within Microsoft Windows 10 64-bit Pro edition version 20H2. I may have to do research to open up a command prompt or power shell with administrator privileges to disable and turn off Microsoft Fast Startup which I am going to do soon.

I opened up a command prompt with administrative privileges. I typed in powercfg /a and this is the output:

Microsoft Windows [Version 10.0.19042.630]
(c) 2020 Microsoft Corporation. All rights reserved.


C:\Windows\system32>powercfg /a
The following sleep states are available on this system:
    Standby (S3)


The following sleep states are not available on this system:
    Standby (S1)
        The system firmware does not support this standby state.


    Standby (S2)
        The system firmware does not support this standby state.


    Hibernate
        Hibernation has not been enabled.


    Standby (S0 Low Power Idle)
        The system firmware does not support this standby state.


    Hybrid Sleep
        Hibernation is not available.


    Fast Startup
        Hibernation is not available.




C:\Windows\system32>

I also found this source: [HiberbootEnabled | Mike's Blog (mikerodionov.com)]("https://mikerodionov.com/tag/hiberbootenabled/"). HP Enterprise has an official answer for modifying my registry here: [Disabling Windows 10 Fast Startup (bromium.com)]("https://support.bromium.com/s/article/Disabling-Windows-10-Fast-Startup").

According to my technical research, Microsoft Fast Startup is already disabled and turned off on my HP PC. So, back to square one and trying to scratch my head why Ubuntu fails to install the GRUB2 bootloader or just stick with Fedora for now.

---

### Post by oldfred on 2020-12-09
If installing a second Ubuntu to second drive and want grub in second drive's ESP, I do this:

[https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153](https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153)
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by Welly Wu on 2021-03-22
I am thinking about installing Ubuntu 20.04.2 64-bit LTS GNU/Linux bare metal on my late 2019 CUK HP Omen 15t gaming notebook PC on the ADATA SX8100NP M.2 PCI-e 3.0 NVMe x4 2.0 TB SSD again, but I am not sure if it is going to work. I plan to remove the administrator password that I set for the custom HP UEFI and disabling and turning off Microsoft Secure Boot and enabling and turning on Legacy CSM mode. After I figure out how to boot up a live Ubuntu session, I am going to use gParted to erase and create two GPT partitions for both of my internal SSD before I attempt an installation again. When I first received this personal computer about a year or longer ago, I did install Ubuntu 20.04.0 64-bit LTS successfully by wiping Microsoft Windows 10 64-bit Pro edition and choosing Ubuntu as the primary and sole desktop operating system. I think that I remember disabling Secure Boot and enabling Legacy CSM prior to attempting my first Ubuntu installation which was successful not too long after I received my new gaming notebook PC. What do you guys think instead of a dual-boot configuration? What do you suggest?

---

### Post by Welly Wu on 2021-03-22
Ubuntu 20.04.2 64-bit LTS GNU/Linux installed successfully bare metal on my late 2019 CUK HP Omen 15t gaming notebook PC on my primary ADATA SX8100NP M.2 PCI-e 3.0 NVMe x4 2.0 TB SSD! Now, I get down to doing my hard technical work. Thanks guys and gals!

---

