---
title: "Install hangs infinitely at &quot;Preparing to install Ubuntu-Netbook&quot;"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by phrnk on 2010-10-16
I'm using a EeePC 1000H and wanted to upgrade 8.10 to 10.10. As  suggested by [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) I chose to  do a new install.

The following partitions are present:
- WindowsXP, 2 NTFS partitions
- ext3 where 8.10 sits. It is of EasyPeasy-flavour (no other version available at that time)
- hidden partition where WinPE resides

I downloaded the ISO and put it on a USB stick (4GB). Booting works fine. Using it as a live-system works fine as well.

Problem came when I want to install it. The process hangs at "Preparing  to install Ubuntu-Netbook" after clicking "forward". Nothing happens  afterwards. In the menubar a crash-report detected-notification appears,  saying:
> The problem cannot be reported:
The program crashed on an assertion failure, but the message could not  be retrieved. Apport does not support reporting these crashes

Unfortunately no other information available. Looks similar to [http://ubuntuforums.org/showthread.php?p=9960455](http://ubuntuforums.org/showthread.php?p=9960455) but not the same hardware. The thread there seens bot to be of much use anyway, therefore this new post.

Any help is appreciated.

---

### Post by Nihrena on 2010-10-19
Same hardware. Same problem.

I ran partition editor from "Try ubuntu" and deleted all partitions i could. Installation went fine after reboot.

---

### Post by littleralph on 2010-10-20
Different Hardware. Very similar issue.
 
Acer Aspire One. (Don't know any further details as am loading this for my son's friend)
 
I get no response after hitting forward but have no crash message that I can determine. I have used the disk utility in the live version to firstly format and then completely remove any partitions that I can.
 
Earlier this evening I attempted to load 9.10 but came up against a "No DEFAULT or UI configuration directive found!" issue which I couldn't solve. I then tried recreated the USB drive with 8.04.4 and was successful at running live and installing on hard drive.
 
I then acquired 10.10 Netbook version and have encountered this issue when trying to load to disk.
 
Any thoughts would be greatly appreciated. (Rank noob BTW)

---

### Post by defex on 2010-10-21
I was experiencing this problem with the Desktop edition, and after reading this forum and how deleting partitions worked, I discovered a USB thumb drive plugged into my computer.

Removing the USB thumb drive fixed the problem. This may be related as I suspect you'll be install off a thumb drive on a netbook?

---

### Post by vahnx on 2010-10-21
Same problem on a Dell Mini 10v. I actually rebooted and then I wasn't able to boot from my USB until I re-create the live USB on my Windows machine. Tried again, only this time I booted into the live desktop and ran the install from there, same issue. Unplugged my USB to no avail. Ubuntu has been getting worse and worse since 8.04+.

---

### Post by scope on 2010-10-30
Same problem here.. Dell mini 10v with 16GB SSD Samsung drive. I didn't have problems installing 10.04 with a pen drive, but with 10.10 I am not able to..

---

### Post by thebravoman on 2010-12-24
Same problem here. Dell Studio XPS with windows 7 and I am trying to isntall 10.10.

I have ran the live cd, chose a language, and on the second page "Preparing to install" pressing the "Forward" button hangs the installation. In the menubar a crash-report detected-notification appears,  saying: 
The problem cannot be reported:
The program crashed on an assertion failure, but the message could not   be retrieved. Apport does not support reporting these crashes.

Has anyone found a solution?

---

### Post by dk412 on 2010-12-28
Ugh. Same problem with Eeepc 1005pxd. Will keep searching the forum for answers. This blows. I'm starting to hate this computer.

---

### Post by Colonel Boris on 2010-12-30
I've got a Thinkpad R500 and I've got the same problem trying to install 10.10 alongside windows XP.  Rather annoying...

---

### Post by thedaver on 2010-12-30
OK, I just blew 6 hours trying to install Maverick 10.10 onto an Acer Revo 3610... I encountered the same issues with not being able to enter the Partitioner, etc...

here's how I got it done...

BIOS - disable AHCI and revert to SATA/IDE for onboard HD, configure/enable USB as first boot device

UNetbootin - built Ubuntu 10.10 LIVE, booted to live, and deleted all partitions on the HD

UNetbootin - built Ubuntu 10.10 NETINSTALL, booted, ran with USB still plugged in until I answered the second set of keyboard locale questions - THEN I REMOVED the USB Thumbdrive (that I used to boot).

The Netinstall process completed, including entering the partitioning process without error.

MY CONCLUSIONS:

1) There is at least one conflict between the Ubuntu 10.10 Live installer and the presence of AHCI and potentially the presence of a Linux SWAP partition on the local HD.   I found that some partitioning tools may have seen the local HD as "busy/locked" because of either AHCI or that the Live install was using the local SWAP (dunno).  I imagine if I google carefully this would have been a well-documented warning...

2) Ubuntu partitioning tools are inherently unable to work around the physical presence of the Kingston (or other) USB booted Thumbdrives when the goal is to partition a local HD.

Good luck!

---

### Post by thedaver on 2010-12-30
I'm going to update that last step...

I removed the USB bootable thumbdrive while on the screen to answer my locale (before partitioning starts).   I reattached the USB after the formatting was completed (while the Installing Base system screen was running)...  That may or may not make a difference.

I think it's also safe to say that the NetInstall can have connection issues which may cause the process to hang for a moment or fatally, you may need to restart the NetInstall.

---

### Post by thedaver on 2011-01-01
After review of the netinstall output, I didn't like it.  I wasn't experienced enough to fully profile xorg to run the way mythbuntu/ubuntu desktop install them.

I spent some time trying to get a USB install working, including straight to Debian Squeeze.  Squeeze must use the same version of the partitioner that Maverick uses - same failure.

I have finally (and happily) resolved my issue by installing Ubuntu 9.10 from USB stick (partitioner works there) and then upgrading to 10.04LTS - which meets my needs to run Mythtv.

Good luck!

---

### Post by udonmez on 2011-01-27
Same problem on a Toshiba NB200. I followed that link: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) but I could not able to setup ubuntu and wasted my 3 hours.

---

### Post by juhapeh on 2011-02-26
I managed to solve problem by using SD-card instead of USB-stick.

---

### Post by jayblingham on 2011-04-10
I can confirm that installing from an SD card, instead of a USB drive, works flawlessly.  I spent a good amount of time troubleshooting, and searching for this resolution before I landed here.  Thanks juhapeh.

Jay

---

### Post by sunyata_ on 2011-04-30
Hi, i had the same problem after booting from a usb stick.


For me the solution was to use unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
instead of universal usb installer

Following the instructions in the link above i used a previously downloaded file by activating the second radio button: "Diskimage" - instead of "Distribution".
(The file downloaded file i used: ubuntu-10.10-netbook-i386.iso)

The last step "4. Installation Complete, Reboot" is meant to be done on the netbook (or other computer)


Other changes made at the same time (that i don't think was the reason it worked):
- switched the usb input slot
- changed to another usb drive (now larger, 8 GB, the old one was 4 GB)


Hope this helps

---

### Post by thebiggiant on 2011-06-08
My install of Ubuntu 11.04 (along side of Windows 7) was hanging at "Preparing to install". I solved it by booting with [Gparted liveCD]("http://gparted.sourceforge.net/livecd.php"), shrinking my Windows partition (leaving a new 10GB partition), I did not format the new partition, then booted with Ubuntu CD and installed.

I recommend this article for explaining the install process...
[Dual-Boot Windows 7 and Ubuntu in Perfect Harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

I'm disappointed that the Ubuntu installer was not more helpful with the problem. I think there are log files, but displaying a list of the current install process would have been more helpful. Also, if a lack of hard drive partition or space will prevent install, the installer should notify the user.

Kevin

---

### Post by aseries on 2011-08-20
Dell Inspiron 910 (Mini-9).
The Live USB worked perfectly so I tried to install from live desktop.
Hung just like all the other complaints.
I deleted the SSD partitions and tried a hard install.
Hung again.
Strange, because I just tried a different distro called JOLI that runs on a UBUNTU kernal and it worked flawlessly. It had to install over a previous CHROME OS installation. No problem.
I think I will try an older version of REMIX and see if it will upgrade.

---

### Post by metatechbe on 2012-06-22
Hi,

I had the same problem on a MacBook Pro with 12.04 64-bit.
I needed to select "Try before install" instead of "Install", so that I could open a Terminal and type "ps -efH", and I saw that there was a tree of frozen scripts launched by ubiquity (the installer) trying to detect other partitions.
I did "sudo killall -9 grub-mount", and after 3 more times I could proceed with the installation.

metatech

---

### Post by oldos2er on 2012-06-22
Old thread closed.

---

