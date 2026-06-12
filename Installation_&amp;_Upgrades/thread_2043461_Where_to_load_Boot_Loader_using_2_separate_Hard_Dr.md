---
title: "Where to load Boot Loader using 2 separate Hard Drives"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-16
Hi Members

I am currently installing Ubuntu on a system with windows 2000. I'm installing Ubuntu on a second hard drive. I installed ed another hard drive on the same cable and set that drive to slave. I checked the BIOS and it recognizes both drives.

I started the installation process and choose "Do Something Else" as I was not sure what "Install alongside windows" actually meant. Does that mean install alongside on same drive or install alongside windows on a second drive? 

Thus I chose "Do Something Else". I was then presented with a screen that successfully identified both hard drives (as well as the partitions on the Master drive containing windows 2000).

And now it is asking me where I want to install the boot loader via a drop down box that contains all my drives and partitions.

I'm looking to be able to select either OS at start-up thus where do i load the boot loader please? Thank you.

---

### Post by wheeze on 2012-08-16
Can you set your new 2nd drive to be the main boot drive in BIOS? That's how I have my computer configured and it works well this way.

I install grub to the MBR on the 2nd drive. For me this is /dev/sdb. Grub will list your Linux OS as well as your Windows OS in its menu so you can boot either system. You never have to mess with the Windows disk MBR this way, very clean.

---

### Post by ajgreeny on 2012-08-16
> **wheeze said:**
> Can you set your new 2nd drive to be the main boot drive in BIOS? That's how I have my computer configured and it works well this way.

I install grub to the MBR on the 2nd drive. For me this is /dev/sdb. Grub will list your Linux OS as well as your Windows OS in its menu so you can boot either system. You never have to mess with the Windows disk MBR this way, very clean.
Definitely the "cleanest" way to do it, and as wheeze says it leaves your windows bootloader untouched.  This can be important these days when windows seldom comes with an installation CD, not even a recovery CD.

---

### Post by WindsOfChange on 2012-08-16
Hi Wheeze

Thanks for helping. Can you clear up a question or two please?

[COLOR=Blue]>>>Can you set your new 2nd drive to be the main boot drive in BIOS?[/COLOR] 

Yes, I can tell my BIOS to do anything in regards to boot order. No problem.

[COLOR=Blue]>>>I install grub to the MBR on the 2nd drive. For me this is /dev/sdb.  Grub will list your Linux OS as well as your Windows OS in its menu so  you can boot either system.

[COLOR=Black]Ok here is where I am confused. Do I have to partition the second drive for Ubuntu install if its not currently partitioned? I can create the partitions using the Ubuntu install CD correct?

If I do in fact have to create partitions, do I have to create the following 3 partitions?

1) Boot partition for Ubuntu/Grub boot loader (about 500 MB)?

2) Swap partition for temporary internet files (about 1 gig)?

3) Partition for Ubuntu OS ?

Thank you
[/COLOR][/COLOR]

---

### Post by oldfred on 2012-08-16
If you use manual install you have to create partitions, specify what to mount as ( / (root), /boot,/home & swap), and format(swap has no format. 

Swap is for use when you run out of RAM, not Internet files.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Your computer may be old enough that you need a separate /boot as first on drive or a smaller / (root) partition at the beginning of the drive. Older BIOS have to find all the boot files inside the first 137GB. If you are using a smaller / and not /boot then use the rest for a /home partition.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

Installer has not really changed, so these are still examples. Herman has update to use the alternative installer, which is similar but text based not gui.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by wheeze on 2012-08-17
> **WindsOfChange said:**
> [COLOR=Blue][COLOR=Black]Ok here is where I am confused. Do I have to partition the second drive for Ubuntu install if its not currently partitioned? I can create the partitions using the Ubuntu install CD correct?[/COLOR][/COLOR]

Correct. The installer has options for partitioning.
[COLOR=Blue][COLOR=Black] 
[/COLOR][/COLOR]> **WindsOfChange said:**
> [COLOR=Blue][COLOR=Black]If I do in fact have to create partitions, do I have to create the following 3 partitions?

1) Boot partition for Ubuntu/Grub boot loader (about 500 MB)?

2) Swap partition for temporary internet files (about 1 gig)?

3) Partition for Ubuntu OS ?[/COLOR][/COLOR]

I just create one partition for root and one for swap, and install the boot loader directly to the MBR of the drive itself, not into a partition on the drive. Where it asks where to install the boot loader, choose /dev/sdb, not /dev/sdb1 or any other partition. That will put it in the MBR of your second drive.

Change your BIOS to boot from the 2nd drive and you should be good to go.

---

