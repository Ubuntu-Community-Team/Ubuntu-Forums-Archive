---
title: "Install on fakeRAID0"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by pgn674 on 2012-03-18
I've built myself a new computer, with this configuration:

Motherboard: EVGA Z68 SLI (Intel Z68 north bridge)
Graphics card: NVIDIA GeForce GTX 560 Ti (MSI N560GTX-TI Twin Frozr II/OC)
CPU: Intel Core i7 2600 (Sandy Bridge)
Disks: 2 of: OCZ Octane OCT1-25SAT3-128G SSD SATA III, in a RAID 0

I set up the RAID 0 in the BIOS using Intel Rapid Storage Technology, which I think means it's a fakeRAID. I'm using a firmware level RAID because I will be dual booting Windows and Linux. The BIOS is EVGA UEFI v. 685 A105 x64. Other than the RAID, all BIOS settings are at default.

I am trying to install Ubuntu 11.10 amd64. I have already installed Windows 7 Pro x64, telling it to partition and install to half of the RAID0 volume (called 'volume0'). I have downloaded the desktop and alternative installers, and burned them to DVD and used LiLi USB Creator to create bootable flash drives from them.

For the desktop installer, from both mediums, it scrolls through some text, and stops after finding my USB mouse and keyboard (and flash drive if I'm using that). It then just stays there, though sometimes it reboots the computer at a seemingly random time. The longest I have waited is 10 minutes.

For the alternative installer on both mediums, all seems to go OK (well, one time the "Select and install software" step kept failing), but then at some seemingly random time the computer reboots.

The RAM tested OK. I tried checking the CD from the installer in both the desktop and alternative installers, but it always rebooted before finishing.

Has anybody installed Ubuntu on this hardware or in this kind of configuration? I've looked at the [FakeRaidHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FakeRaidHowto"), but it only goes up to 10.04, and it basically says everything will take care of itself for that version. I've seen hints around of setting nomodeset for the graphics card, and adding libata.ignore_hpa=0 for the RAID0, but they haven't helped. I've also seen that GRUB may need to be installed to a non-RAID part, but the boot up installer keeps stopping or the computer keeps restarting before it gets to the GRUB step. If I have to re-do the RAID and reinstall Windows, that's OK; I've barely configured it. In Windows, the system is completely stable.

If anyone can provide any help or hints or troubleshooting steps, that would be awesome.

---

### Post by pgn674 on 2012-03-19
An update: I tried unplugging the SATA drives, resetting all BIOS settings back to default, putting in a graphics card from my old computer, and swapping out memory. With the older graphics card, the desktop CD finished booting OK. But, I still have that random restart problem. It's as if the power button was just pushed, and then after a couple seconds the computer turns on again.

I think I've narrowed the problem to the EVGA Z68 SLI motherboard (model 130-SB-E685-KR). I looked through the BIOS for any advanced options I can turn off, but didn't find anything. I'll try looking again, and making sure I know what everything is. I'll also look through the Ubuntu CD boot options, see if there's anything else useful there.

---

### Post by pgn674 on 2012-03-22
I finally got it!

I tried turning off all sorts of BIOS options, and had to re-flash it a few times (luckily that's easy on this motherboard), but nothing helped. Boot CDs and flash drives of both desktop and alternate installers kept rebooting at random times.

So then I tried going through the boot options for the alternate CD, and I found one that worked. In the first screen that comes up after booting from the Ubuntu 11.10 Alternate amd64 CD, I went into the F6 Other Options menu, and selected the acpi=off item. That's it. I was then able to continue with the install without it ever rebooting randomly.

Some notes: During the install, it asked whether I wanted to activate some RAID thing, and I selected yes (since I do have a fakeRAID0). GRUB wanted to install to /dev/mapper, which didn't work. Nor did /dev/sda. So I had to press Ctrl-Alt-F2, and use that prompt to run the command "ls /dev/mapper/". In there, I saw that I may want to install GRUB to /dev/mapper/isw_cadbcjiedi_Volum0. That worked.

After the install, I noticed that GRUB was sending the kernel the acpi=off option. I kept that there and booted into Ubuntu and installed updates, then tried rebooting and removing that option. My computer ran quieter, but it randomly rebooted after a bit, just like in the CD. So, I'm running with acpi=off right now, but now I know what to research.

I hope this helps anyone with a similar problem.

---

### Post by pgn674 on 2012-04-04
An update to the ACPI problem. I submitted a bug report: [https://bugs.launchpad.net/bugs/973933](https://bugs.launchpad.net/bugs/973933)

---

