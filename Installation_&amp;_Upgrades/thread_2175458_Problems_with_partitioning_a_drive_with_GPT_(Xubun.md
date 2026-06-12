---
title: "Problems with partitioning a drive with GPT (Xubuntu will not boot - Grub)"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by gianfranco2 on 2013-09-19
Hi everybody, I recently bought [this]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03664130") HP laptop with Windows 8 preinstalled. Long story short, I grow increasingly frustrated with Windows 8 and install Windows 7 (x64) instead, erasing the entire drive (I wanted to get rid of GPT, essentially, having been told that booting Windows 7 with it would prove difficult and that simply formatting it would do the trick), and deciding to install Xubuntu 13.04 (I've been using Linux for over a year, and XFCE is my favourite DE so far); despite being very unexperienced, instead of choosing the option to install it alongside my other OS, I choose the custom installation, and partition my drive like [this]("http://sdrv.ms/18CsTmr"). (/dev/sda4 is a logical partition containing the root, /dev/sda5 is the Home folder and /dev/sda6 is the swap partition).
However, Xubuntu does not boot (the system apparently does not see Grub).
I run Grub Repair from in Live Mode and decide to take no action; and [here]("http://paste.ubuntu.com/6124723/") is the report that it has generated; 
So basically, here are the questions that I would like to ask, before I decide to do anything else:

[LIST=1]
[*]What is it that I did wrong, essentially? Does it have anything to do with EFI and would the way I have partitioned my drive have worked with an older laptop without EFI\GPT?
[*]What do I need to do to solve the problem (preferrably without having to reformat the drive)?
[*]Should running Grub Repair solve it? I am somewhat reluctant to use the program, because I would like to know if there are other, more efficient solutions. (my concern here being - hypothetically - the presence of leftover and\or redundant files that would occupy space needlessly and could be easily removed should the procedure be done manually or in some other way)
[/LIST]

---

### Post by oldfred on 2013-09-19
Welcome to the forums.

You are still showing both Windows and Ubuntu in UEFI mode. 
Unless link is to someone else's system?
You still have gpt partitioning and no extended nor logical partitions.

Other users with HPs seem to have issues. Some have limited UEFI configurations with only secure boot on/off and legacy boot that will boot UEFI if found or boot BIOS if found.

 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by gianfranco2 on 2013-09-19
I just managed to boot Xubuntu by pressing f9 and selecting 'Ubuntu' among the devices; this, however, does not completely solve the problem and does not address the question of why I do not see the Grub screen which, to me at least, is a much better (and easier) option, because otherwise I have to be fast enough and press the f9 button before Windows 7 is selected. Secure Boot is disabled on my machine, and I think legacy boot is enabled, so I do not get why this happens. Yes, indeed, the info contained in that report baffles me...I think I will need some time to figure out what the problem is. Oh, and by the way, thanks for your reply; I am extremely busy right now so I will get back to you later and read the links that you have posted.

---

### Post by oldfred on 2013-09-19
You have no boot loader in MBR, so you cannot boot with BIOS/CSM/Legacy.

Grub should show menu, you may just need to run sudo update-grub to get os-prober to find Windows. But it has a bug and adds incorrect entries and you have to use the entries Boot-Repair creates. I would not run the rename files if you can boot Ubuntu in UEFI mode. That is for the few systems that only boot the Windows efi file and the work around is a rename of Windows efi file to really be grub2's shim which has the Microsoft secure boot signing key. 

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'

---

