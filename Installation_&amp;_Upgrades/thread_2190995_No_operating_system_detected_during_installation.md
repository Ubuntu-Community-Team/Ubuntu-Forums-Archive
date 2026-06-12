---
title: "No operating system detected during installation"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by LyTningB0LT on 2013-11-30
I'm trying to install Ubuntu alongside windows 8 on my laptop. I downloaded the 13.10 iso and burned a live dvd, but when I boot from the dvd and try to install Ubuntu it says 'no operating system detected'. Why isn't it detecting my windows 8?

---

### Post by rackit on 2013-11-30
At what point in the installation do you get this message?

---

### Post by LyTningB0LT on 2013-11-30
The third installation screen, right after I selected to install the updates and third party software

---

### Post by heir4c on 2013-11-30
Stop the installation and start gParted (Partition Manager) to see how the drive is partitioned at this moment.
Post here a screenshot.
Or use the terminal and type:
```
sudo parted -l
```
and post the output here.
(The -l is a little L )

---

### Post by LyTningB0LT on 2013-11-30
Here's what I got. Not sure what the error means
[ATTACH=CONFIG]248212[/ATTACH]

---

### Post by heir4c on 2013-11-30
It's with the GPT partition lay-out. 
Someone else will have to help.
I have no experience with GPT.

---

### Post by rackit on 2013-11-30
Was Windows shutdown properly? Sometimes a partition flagged as dirty will have issues.

---

### Post by oldfred on 2013-11-30
The error messages are from the CD/DVD as it is oversize. Those you can ignore.

With Windows 8 you have to turn off fast boot as that is always on hibernation and the Linux NTFS driver will not normally mount hibernated file systems.
Also after a resize Windows has to run chkdsk and again the NTFS driver will not mount it.

So resize Windows to make room for Ubuntu using Windows disk tools and reboot to make sure it has run its chkdsk and make whatever repairs it likes to do on a new partition size. Make sure fast boot is off and then it should work.

       Backup efi partition and Windows partition before Install of Ubuntu. And best to have a Windows repair flash drive.

Shows install with screen shots for both BIOS & UEFI, so you know which you are using. You want to boot in UEFI mode as how you boot installer is how it installs.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

More details in link in my signature on UEFI installs.

---

### Post by LyTningB0LT on 2013-11-30
I've already disabled fast boot and also SecureBoot in my BIOS. I'm pretty new to this, so I was hoping I could go the automatic route instead of manually resizing partitions. Is there a way I can still do that? Or do you think doing it manually is the only way around this? Thanks for the help.

---

### Post by fantab on 2013-11-30
Have you '[Disabled FastSTARTUP]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'?

---

### Post by rackit on 2013-11-30
Great info @oldfred! Thanks much!

---

### Post by oldfred on 2013-11-30
If you shrink Windows with Windows to make unallocated space then an auto install option should work. 
Do not use LVM or encrypted as some have just had entire drive overwritten. Not sure if user or Ubuntu issue. But those should only be considered advanced install options anyway.

---

### Post by LyTningB0LT on 2013-12-01
Ok I shrunk the windows partition by 50GB, which now shows up as unallocated space next to drive C. I rebooted to Ubuntu, tried to install again and had the same problem. Then I remembered windows had to run chdisk, so I rebooted windows, and then rebooted Ubuntu again, but with the same result. The installer is obviously detecting my hard drive, since it says I have the necessary space available to install, so I don't understand why it's not recognizing windows 8 as an operating system. Fastboot is off.

EDIT: Fast startup is off, I couldn't find fast boot anywhere in the BIOS to disable it

---

### Post by oldfred on 2013-12-01
Is this an Ultrabook? That has Intel SRT which uses RAID somehow and the RAID on the drive can cause issues. Your parted output did not look like it as there was no sdb.

Does gparted show all the partitions normally?

---

### Post by LyTningB0LT on 2013-12-01
I have an AMD processor so intel SRT shouldn't be an issue. I don't have gparted, but here's what windows disk manager looks like.

[ATTACH=CONFIG]248230[/ATTACH]

---

### Post by oldfred on 2013-12-01
gparted is on the live installer. 
I do not see anything wrong if fast boot or quick boot is off. Not sure if there are any other UEFI settings that cause issues.
Some have mentioned passwords in UEFI to allow UEFI changes.

What computer, model? Maybe someone with similar system has posted some info?

---

### Post by LyTningB0LT on 2013-12-01
Here's the computer I have: [http://www.staples.com/HP-Pavilion-15-N066US-15-inch-Laptop/product_284386](http://www.staples.com/HP-Pavilion-15-N066US-15-inch-Laptop/product_284386)

I'll take another look and see if there's some other UEFI settings that might apply, but I didn't see any before.

---

### Post by oldfred on 2013-12-01
No idea what this is, but it sounds like a problem. What does it do?
You may have to turn it off.

 750GB 5400RPM hard drive with HP ProtectSmart Hard Drive Protection

---

### Post by LyTningB0LT on 2013-12-01
From what I understand it's a hardware protection thing, so it shouldn't make a difference. Do you think I should try installing an older version than 13.10? Would that possibly help?

---

### Post by oldfred on 2013-12-01
Is not the issue that we cannot write to hardware?

Most have better success with the newest version of Ubuntu as it has many UEFI updates.
If you UEFI the latest version from HP? Vendors also are making major updates.

---

### Post by LyTningB0LT on 2013-12-01
What I understood is that it's something actually built into the laptop, physically protecting the hard drive if it's dropped or something. I believe I have the latest updates, but I can check to make sure.

---

### Post by LyTningB0LT on 2013-12-01
Ok I updated my BIOS, but it didn't change anything.  It's still not detecting windows 8. If I click 'something else' in the installer it lets me view all the different partitions, but I'm pretty new to this so I'm not sure exactly what (if anything) I could do from there that would manually install it in the space I freed up.

---

### Post by oldfred on 2013-12-01
Then I would use manual install.
You have to create partitions by size, choose a format like ext4, select mount like / (root) or swap which has no format. You can also create other partitions but that is not required.

I prefer to format in advance with gparted, but it does not save much as during install you still format & choose mount.

I would just make swap 2GB and not plan on hibernating. When dual booting hibernation can cause issues. 
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

