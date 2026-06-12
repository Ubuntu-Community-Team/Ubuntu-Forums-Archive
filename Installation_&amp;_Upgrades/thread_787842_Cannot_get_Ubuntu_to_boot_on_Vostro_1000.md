---
title: "Cannot get Ubuntu to boot on Vostro 1000"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by Mind537 on 2008-05-09
I'm trying to get Ubuntu 8.04 on my Vostro 1000 and I can't get anywhere. I switch to safe graphics mode before I try to do anything, but nothing works. When I try ubuntu with no changes, or just go straight to the install, with safe graphics or no, I get the same thing. It takes me to the BusyBox prompt and doesn't display any error at all. I'm a big n00b when it comes to Linux, so any help at all would be very useful, thanks

BTW, I know the CD is fine, because I've used the same cd to install Ubuntu on 2 desktops successfully.

---

### Post by Rallg on 2008-05-09
I have Ubuntu (both amd64 and i386) on my Vostro 1000, along with Vista. No problem.

Let's start at the beginning. Are you referring only to use of the live CD. or to install? I assume you refer to install problems.

First, did your Vostro come with Vista or XP? Are you retaining Windows, or trying to get rid of Windows? Are you using the amd64 or i386 version of Ubuntu?

If your Vostro is like mine, the hard drive came from the factory with 3 partitions. The first partition (hd0,0) is FAT16, very small, and contains some stuff put there by Dell. This partition does not show up from within Windows. The second partition (hd0,1) is NTFS, locked, and contains some Recovery stuff accessible from Windows. The third partition (hd0,2) is the Windows Operating System. This partition is marked for boot.

When you install Ubuntu, you will shrink the Windows (hd0,2) partition, and install Ubuntu in the newly available space. There are several ways to do that (one of them is to let the CD do the thinking for you).

So far, is that what you did?

The Vostro 1000 uses an ATI XPRESS 1150 graphics card (at least, mine does). This can be driven by generic software that comes with the installer, but for best performance you can download and install a proprietary ATI driver, via Ubuntu's hardware manager. Did you do that? If you did, and if you are having display problems, you can use the generic driver by logging in as Gnome fail-safe mode.

The Vostro 1000 uses a Broadcom 1390 wireless (WiFi) card (at least, mine does). This card does not have a built-in driver. The proprietary software driver is not included with the Ubuntu CD, but must be downloaded and installed separately via the hardware manager. Of course, to download and install the WiFi driver, you must be connected to the Internet by other means, such as cable. Did you do that? If you do not install the proprietary driver, then you will get no WiFi at all. It might be possible to obtain the necessary *.deb software package via Windows, then transfer it to Ubuntu, and install it. But since there have been changes within the past month or two, I won't discuss that further (because I don't know).

In my case, I had the amd64 version in beta test on my computer, and I upgraded without using the CD. I installed the i386 version from final CD, and it worked the first time, without problem.

There is one other possibility: When Ubuntu loads, it detects hardware. Sometimes, if there is a hardware incompatibility, the loader will halt. So, does your laptop have anything connected to it (iPod, external hard drive, printer, camera memory card, etc.) when you are trying to boot Ubuntu? If so, disconnect the stuff, then try to boot. I had no problem with a Targus wireless USB mouse, but your results may differ.

If all else fails, try logging in via recovery mode. If the boot sequence hangs before you get to the login prompt, then the messages may help debug your problem. To login as recovery mode, select that option from Grub. If all goes well, you will eventually be asked for your login name and password. If still OK and you are connected to the Internet via cable, try:

sudo apt-get update && sudo apt-get upgrade

and maybe you will download something that fixes your problem (probably not, but it's worth the try).

To get out of recovery terminal mode, switch to root and reboot:

sudo -s
shutdown -r now

---

### Post by Mind537 on 2008-05-09
What I did to get it working was enter the following parameters with the LiveCD

all_generic_ide floppy=off irqpoll

Mad props to Jong for those parameters

Also went into Safe Graphics Mode and Voila! Booted into the installation.

Thank you much, Rallg, for your very informative post. I hadn't even gotten that far yet, but I too have the same ATI card and broadcom. So that will greatly helpe me out.

This took me forever to finally find out (days), I hope anyone else in my situation will benefit from this fix, thanks again guys.

---

