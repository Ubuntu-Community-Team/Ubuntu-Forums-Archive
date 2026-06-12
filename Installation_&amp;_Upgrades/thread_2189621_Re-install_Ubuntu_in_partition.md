---
title: "Re-install Ubuntu in partition?"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by algadams13 on 2013-11-23
I am completely new to this, so forgive me please if it's a stupid question. My situation is thus:
I got a new computer in August, and it came pre-installed with Windows 8. I HATED it, so I partitioned my computer and installed Ubuntu. It was a difficult installation, because the computer was a brand-new HP Pavilion. Eventually, after installing various kernals and updates, I managed to get 13.04 working - then I had trouble with the internet for awhile. Today I finally got the internet to work on my Ubuntu OS (yay!), and started updating Ubuntu. Big mistake. Now I'm back where I started. Ubuntu will only load to the title page again, and won't take me to the login. I really like using the Ubuntu OS but at the same time I don't want to go back to installing all kinds of little updates to get it functioning (and in any case, it's pretty hard to access right now). Is there a way to keep the partition itself intact, but wipe the Ubuntu 13.04 off it and install 13.10?
Again, I apologize if the question makes no sense. I'm a teacher, not a techie.

---

### Post by grahammechanical on 2013-11-23
The way we re-install Ubuntu is to use the Something Else option. That will bring up a partitioner program that will show you your partitions. You select the partition with 13.04 on it, click Change and in the dialog box that appears, select Use As Ext4 with a mount point of / and tick to format. Then click OK. Then, when back at the partitioning screen click Install Now. I have done this dozens of times when testing versions of Ubuntu. I have a non-complicated machine. Problems occur with Windows 8 machines and also with machines that have hybrid graphics. I know nothing of these things.

Regards.

---

### Post by fantab on 2013-11-23
> **algadams13 said:**
> I am completely new to this, so forgive me please if it's a stupid question. My situation is thus:
I got a new computer in August, and it came pre-installed with Windows 8. I HATED it, so I partitioned my computer and installed Ubuntu. It was a difficult installation, because the computer was a brand-new HP Pavilion. Eventually, after installing various kernals and updates, I managed to get 13.04 working - then I had trouble with the internet for awhile. Today I finally got the internet to work on my Ubuntu OS (yay!), and started updating Ubuntu. Big mistake. Now I'm back where I started. Ubuntu will only load to the title page again, and won't take me to the login. I really like using the Ubuntu OS but at the same time I don't want to go back to installing all kinds of little updates to get it functioning (and in any case, it's pretty hard to access right now). Is there a way to keep the partition itself intact, but wipe the Ubuntu 13.04 off it and install 13.10?
Again, I apologize if the question makes no sense. I'm a teacher, not a techie.

Do you still have Windows 8 installed? Are you Dual-Booting? Or have you removed Win8?
What Graphics card do you have on board? Do you have [hybrid-graphics]("https://help.ubuntu.com/community/HybridGraphics")?
HP Pavilion- what model?

---

### Post by algadams13 on 2013-11-23
1. Yes, I still have Windows 8 installed. I am dual-booting.
2. Graphics info: Radeon HD Graphics 2.00 GHz, I think
3. I have an HP Pavilion G6

---

### Post by fantab on 2013-11-23
> **grahammechanical said:**
> The way we re-install Ubuntu is to use the Something Else option. That will bring up a partitioner program that will show you your partitions. You select the partition with 13.04 on it, click Change and in the dialog box that appears, select Use As Ext4 with a mount point of / and tick to format. Then click OK. Then, when back at the partitioning screen click Install Now.

That's it.

You probably have EFI boot, so make sure you [boot your Ubuntu DVD/USB in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode"), if not then you will have use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") to fix your boot.

Good Luck.

---

### Post by algadams13 on 2013-11-26
Hi again,
I didn't think I'd be back, but I've been trying to work this problem for days and it's not budging. I can't seem to be able to install Ubuntu 13.10. I manage to make it to the install/try menu (install ubuntu/try without installing). As soon as I select "install," I get the purple Ubuntu loading screen, and then the screen goes black. I know that the computer is supposed to do this, but the blackout has lasted for 40 minutes at one point, and I stopped hearing anything from the CDR so I don't think it was working. The same thing happens if I choose "try without installing." The only thing I HAVE been able to do is check the disc for errors, and none were found.
Am I just really impatient, or is something not working?
Note: As far as I know, my computer can only do EFI mode for the install.

---

### Post by fantab on 2013-11-26
In Windows have you disabled '[Faststartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'?
Try [NOMODESET ]("http://ubuntuforums.org/showthread.php?t=1613132")to see if it is a Graphics Issue.
If you have '[Fastboot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm")' in BIOS, disable it.
Also confirm that you have burned the DVD correctly, with [right tools]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows").
If you have a USB pen drive, then burn ubuntu.iso on it and try. [Ubuntu USB]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows").

Don't try to install until you have successfully 'Try Ubuntu without installing'.

---

### Post by howefield on 2013-11-26
At the Live CD boot screen, press F6 (Other Options) and remove the words quiet and splash from the boot options line, then press enter to continue the boot, this will scroll messages instead of showing a purple screen, you might get a clue as to where it is stuck.

---

### Post by oldfred on 2013-11-26
Actually if you get the purple screen you are booting the installer in BIOS boot mode, not UEFI. You should get grub menu if booting in UEFI mode.
And how you boot installer is how it installs.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

