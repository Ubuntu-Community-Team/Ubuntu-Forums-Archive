---
title: "installed ubuntu 1404 on windows 8, ; cant boot windows any ore"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by brettmichaelis on 2014-11-02
Hi,

I ran the ubuntu installed on windows 8 pc.

I think  I did automatic partition

The pc only boots ubuntu now, It doesnt give me boot option for ubuntu / windows

how do I boot windows or get the dual boot menu?

---

### Post by QIII on 2014-11-02
The very first thing I would do is only boot the machine from a live medium.  Do not boot from the hard drive.

Due to a terribly worded (perhaps even rising to the level of negligent) warning in the installer, the path you chose probably wiped out your entire drive and installed Ubuntu only.

The more you continue to use the machine from the hard drive, the less likely it is that you will be able to recover your important files.

When you are running from a live session, please download and install the bootinfoscript at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions for posting the results.

---

### Post by Rrory on 2014-11-02
I just did a partitiion with logical on my new computer HP with Win 8.1, clicked F9 to boot from the flashdrive and it booted immediately (and to my surprise) into Ubuntu what happened? The choices at F9 are Ubuntu and boot in EFI mode (have no clue!)
 Where is the old OS choice and  Windows (which I hate but need for some things..ugh).

---

### Post by brettmichaelis on 2014-11-02
I see a windows8 device in ubuntu with all my windows folders in it.

How can I get ubuntu to dual boot ubunutu / windows 8

---

### Post by Bucky Ball on 2014-11-02
Perhaps take a screenshot of that drive in Gparted and post it back here (attach it to a post) so we can see exactly what you have there.

If you are booting into Ubuntu and you're ABSOLUTELY positive you can see your Windows partitions and files and you know FOR CERTAIN they are intact, open a terminal and try:

sudo update-grub

Reboot. Can you choose Windows? If that doesn't work, try [Boot Repair. ]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by oldfred on 2014-11-03
@brettmichaelis

Did you install Ubuntu in BIOS mode and Windows is in UEFI boot mode. The two are not compatible, but all new systems will boot in either mode. And how you boot install media is how it installs.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You may be able to boot Windows then just by going into UEFI and turn back on UEFI boot mode. One time boot key may give choice to boot either system, but some systems require you to turn on/off UEFI or BIOS/CSM boot mode.
Boot-Repair can convert a BIOS install to UEFI install if drive is gpt and you have efi partition.

@Rrory
Please do not hijack thread with a different issue. If not exactly the same as this thread, please start a new thread and post summary report from Boot-Repair.

---

