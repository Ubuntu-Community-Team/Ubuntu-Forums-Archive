---
title: "How do you install 12.04  with Windows 7?"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2012-05-30
I want to install 12.04 on one hard disk and Windows 7 on another.
Windows 7 is set already installed on one hard disk, but when I try to boot
to it I get a "grub rescue" prompt and I don't know what to do with that.
I installed 12.04 to the other drive and again I got the grub rescue prompt
when I restarted the system to complete the installation. 

I want the boot loader screen to appear at each bootup and I want the option to
boot to either operating system, with ubuntu being primary (default).
On which drive, windows of ubuntu, should I place GRUB2 bootloader?
How should this decision be related to the boot sequence of the two hard drives,
as determined in my  bios settings?

Please be specific and provide details.  I was on to top of  these installation
issues, including GRUB2, but I've forgotten almost everything as everything has
been going very well with 11.04 for almost 2 years.  I know how to modify a working
grub2 configuration but I don't know what to do when its not working.

Thanks so very much (fortunate to have this support forum).

---

### Post by oldfred on 2012-05-31
You want to have the Windows boot loader ( or any work alike)  in the Windows drive and grub2's boot loader in the Ubuntu drive. Then in BIOS set to boot the drive that is the Ubuntu drive. If Windows not in grub menu when you reboot run this in terminal:

sudo update-grub

May be best to post link to boot-info report, so we can make suggestions, but Boot-Repair works for many.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

To avoid the issue with more than one drive, partition in advance and use manual install. Only manual install with Ubuntu gives the combo box option on where to install the grub2 boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Randy Schilling on 2012-06-01
Oldsef:  thank you so much: your suggestions, right on, supported by your references.
excellent references - keepers.   Thanks and best regards - Randy

---

