---
title: "Installing Ubuntu on a Secondary Drive"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by Pinnacle441 on 2013-02-14
Hi there, I don't really know much about Ubuntu or hard-drives and I'd like to give Ubuntu a shot. I need all the space I can get on my Windows 7 drive so I want to install Ubuntu on a second drive. 

I was hoping you guys could walk me through preparing Ubuntu for installation on this second drive, if anymore info is needed I will gladly provide, thanks.

---

### Post by carl4926 on 2013-02-14
Assuming you added the drive.
And already booted Ubuntu in Live mode from either the CD or a USB, to see how well it works and are happy with that.

I would use Gparted to partition the drive manually.
Create 3 primary partitions

swap = 2x RAM
ext4 = 25GB for /
ext4 = all the remaining space for /home

Now using the ubuntu installer choose:
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Then at the advanced  partitioner set the mount points for / and /home
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

Set grub to sda if sda is your first boot HD

---

### Post by oldfred on 2013-02-14
carl4926 partition suggestions are ok. Swap maybe does not have to be quite that large and only if you want to hibernate.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
    
If dual booting with Windows I might add on the Ubuntu drive a shared NTFS data partition if you have room. Otherwise you may want to make that partition on the Windows drive. Best to set Windows system partition as read only and use a shared NTFS for any data you may want in both systems.

I prefer to keep boot loader on same drive as Ubuntu. Then each drive can boot its operating system without the other drive when one fails. And one will eventually fail.
If you set Ubuntu drive as boot from BIOS then you can add the chain load entry into grub to also boot Windows.
sudo update-grub

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by C.S.Cameron on 2013-02-15
Unplug the current drive.
Plug in new drive.
Install Ubuntu, (use full disk).
Plug back in old drive.
Boot new drive to Ubuntu, (may have to set as first drive in BIOS).
Run:

```
sudo update grub
```

You will have option which system to use next time you boot.

---

### Post by Pinnacle441 on 2013-02-15
Thanks for the replies guys! As great of help as this all is, does anyone have any links to any full written tutorials explaining this in complete depth, or a video?

Thanks again for the help.

---

### Post by C.S.Cameron on 2013-02-15
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

