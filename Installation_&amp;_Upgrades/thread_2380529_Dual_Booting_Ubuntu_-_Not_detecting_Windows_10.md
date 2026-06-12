---
title: "Dual Booting Ubuntu - Not detecting Windows 10"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by carterpaul on 2017-12-18
I'm dual booting Ubuntu and Windows 10 on my dell xps 13. I've gotten most of the way through the installation process, but am running into a snag near the end.

I have partitioned my hard drive leaving a 60GB "unallocated" space which I intend to install Ubuntu to. The problem occurs when going through the installation process after booting from the USB.

After getting through the first few steps I go straight from this screen:
[IMG]https://i.imgur.com/0MOYQ16.png[/IMG]

To this screen:
[IMG]http://i.imgur.com/MtRanoo.png[/IMG]

It seems to completely skip the screen in which it detects that i also have windows installed and asks what I want to do. If I try to click the plus, minus, or "Change..." buttons, I get this error:

[IMG]http://i.imgur.com/l113PPN.png[/IMG]

I assume the issue has something to do with the way the drive is partitioned. I am booting through UEFI and have fast boot disabled. I would boot through legacy boot mode but my laptop seems to have trouble with it. I'm using xubuntu in this example because it is the only flavor I have tried that actually shows the error. Ubuntu 17.10 just freezes when I try to click a button, but I assume the internal problem is the same.

Any suggestions or help would be appreciated.

---

### Post by oldfred on 2017-12-18
Please attach screen shots. Easy to do with Forum's advanced editor and paperclip icon.

Dells have some unique requirements.
The seem to be the only one that wants CSM mode on but have you still boot in UEFI mode. Most systems, once CSM/BIOS/Legacy mode is on, then only boot in CSM mode.

Many Dells have needed both Dell UEFI updated and SSD firmware driver updated.
Dells also need drives changed from RAID or Intel SRT which looks like RAID to AHCI. If dual booting with Windows you must add the AHCI driver to Windows before change (or change back and then install AHCI driver). Windows without driver will not boot if AHCI on.

Also Windows must have fast start up or the always on hibernation off.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

 Dell XPS 13 with Factory 16.04 fixes/issues
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

