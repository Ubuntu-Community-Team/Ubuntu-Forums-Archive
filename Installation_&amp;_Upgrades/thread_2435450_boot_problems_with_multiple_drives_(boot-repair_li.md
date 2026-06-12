---
title: "boot problems with multiple drives (boot-repair link included)"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by jeff-5 on 2020-01-21
I have a gaming computer, so Windows 10 is its focus. I wanted access to the GPU for my serious work, so I was trying to give this machine an Ubuntu 18.04 install as well, without screwing up Windows. I didn't get there.

The hardware has been upgraded through the years. Every time I upgrade, I typically install the current Windows flavor on a new drive, but include the old hard drives on the side. It is now sporting four hard drives going back 8 to 10 years.

After installing Ubuntu from a USB stick, it defaulted to booting to a grub command prompt (not menu; prompt "grub>" or whatever). Or I can choose a specific boot drive from the BIOS and get Windows to boot still (yay!). But the two BIOS boot options that claim to be "ubuntu" only take me to the grub command prompt.

I have attempted boot-repair's recommended fixes, with no change. It's output is at this link:[URL="http://paste.ubuntu.com/p/qTCmVh7jzj/"]
http://paste.ubuntu.com/p/qTCmVh7jzj/[/URL]

To help you navigate that info:
[LIST]
[*]The Windows 10 that I want to keep running is on nvme. nvme0n1p4 appears to be the bulk of the OS and data.
[*]The new Ubuntu 18.04 install is on sdc5 (and the swap that was to go with it is sdc6). But I haven't been able to boot it yet.
[*]There is an old Ubuntu 12.04 at sda5 -- I don't think I care about that one any longer.
[*]The rest of sdc, the rest of sda, and all of sdb are old Windows drives. They possibly include old OS versions and definitely include data I'd like to preserve.
[*]I had the install USB stick inserted when I ran boot-repair, so sdd is the USB stick.
[/LIST]

The hardware should all be fine. The live USB of 18.04 worked/works fine.

How can I reach a state where I can either:
[LIST]
[*] a) have a boot menu choosing Windows or Ubuntu, or
[*]b) boot to Windows unless I direct the BIOS to boot from something Ubuntu.
[/LIST]

Thanks so much for any help sorting this out!

---

### Post by oldfred on 2020-01-21
It looks like you have UEFI boot of both Windows & Ubuntu.
But have old BIOS boot loaders in MBRs of the old drives. Do not boot in BIOS mode. Make sure UEFI has UEFI boot, often better as UEFI only, not UEFI or BIOS. And often better (for now) to have UEFI Secure boot off.

If both installs are UEFI, you can always directly boot from UEFI one time boot key, often f12, but varies by vendor.

You show Windows fast start up on. That sets hibernation flag and then Linux NTFS driver will not mount the NTFS partition(s). And grub2's os-prober cannot find Windows. Turn off fast start up in Windows and then run `sudo update-grub` in Ubuntu.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by jeff-5 on 2020-01-21
Thanks for the quick reply. I've tried that to the best of my ability, with no luck.

I've disabled Windows fast start (the BIOS one and the in-Windows setting, which have similar names). Secure boot was already off.  I've turned everything I can find to be UEFI and not BIOS. I believe that means I'm booting in UEFI. My BIOS boot settings now look like this:
[ATTACH=CONFIG]284844[/ATTACH]

[IMG]https://photos.app.goo.gl/Vw25H6RD7h3gyieF7[/IMG]
I tried installing Ubuntu again, thinking I might have made a bad choice along the way. (I removed the swap partition while I was at it.) Nothing meaningful changed, though some of the .efi files in efibootmgr did change. I specified nvmen01 as the EFI partition (rather than nvmen01p2?). That's the only part I'm not sure about, but it seemed to be the default selection. I assume that means the new install is UEFI, as you requested. Like this:

[ATTACH=CONFIG]284845[/ATTACH]

Yet I get to the grub prompt (because the menu still won't come up), and that drive just seems to be absent:
[ATTACH=CONFIG]284846[/ATTACH]

I've done an `ls (hdX,Y)/` on all of those (and combos that weren't listed, just in case), and none of them is the drive that has Ubuntu 18.04 on it. Like this (and one more screen worth, but I've hit the attachment cap):

[ATTACH=CONFIG]284847[/ATTACH][ATTACH=CONFIG]284848[/ATTACH]

 I can find the Windows 10 drive (hd1). I can find Ubuntu 12.04 (hd2,5). I can find the USB stick (hd0). But not the drive I've just installed Ubuntu 18.04 on, or its NTFS partition either. I imagine it is hd4, but when I `ls (hd4)` is gives `unknown filesystem` and `ls (hd4,1)` (or 2,3,4,5) gives `disk not found`.

Since I can't boot Ubuntu 18.04 at all, I don't see how I can follow instructions I see about updating grub.

Any ideas?
Thanks!

---

### Post by dragonfly41 on 2020-01-21
I don't intend to decode your boot-repair log. But your configuration (apart from your use of nvme) is rather similar to my setup.
I have ..
Windows 10 and old Ubuntu 16.04 in hd1.
Ubuntu 18.04 on SSD in hd2.
Ubuntu 18.04 on HDD in hd3.

I had to jump through many hoops to get my quad-boot to work. My problems started after I added an external USB SSD.
Often the SSD was not recognised and the boot menu varied from boot to boot session.

In this thread ... [https://ubuntuforums.org/showthread.php?t=2434349](https://ubuntuforums.org/showthread.php?t=2434349)

I and another user in that thread opted to install rEFInd and got our systems back again.

Another ploy I have used (found by browsing the many threads) is to manually unplug the internal power cable to the Windows internal hard drive and then use LiveUSB to install Ubuntu on the target external USB drive(s).  And I started the partitions with an ESP partition (/dev/sdb1) which has boot flags boot,esp.
Having got your external drive with Ubuntu to work (on its own) you can plugin the power to Windows drive and reboot.
Of course unplug at mains when playing around with power cables.

These are ideas when all else fails.

---

### Post by oldfred on 2020-01-21
I missed that you installed in UEFI boot mode to a MBR(msdos) partitioned drive. That still should work, but is not recommended.
Best to always use gpt and have an ESP on every drive. Ubiquity will only install grub to ESP first drive usually sda or first NMVe. Does not matter what you select during install with UEFI. Only with BIOS can you change where Ubiquity installs grub.

Since old and new installs are both in partition 5 and sdc is DOS, we then know new install is in sdc5 & (hd2,5).
At grub> try this:

configfile (hd2,5)/boot/grub/grub.cfg

---

### Post by Dennis N on 2020-01-21
> Ubiquity will only install grub to ESP first drive usually sda or first NMVe. Does not matter what you select during install with UEFI. Only with BIOS can you change where Ubiquity installs grub.

This is no longer true in all cases. If you have an NVMe drive and a SATA drive, Ubiquity will install grub boot loader to the ESP of the drive you select - sda or NVMe. I discovered this back in May 2019, when I installed my first NVMe drive. The default boot loader location is set to NVMe.

Examples:
Linux installed on NVMe, and grub installed to sda drive's ESP (sda1):

```
Filesystem                        Size  Used Avail Use% Mounted on
udev                              5.8G     0  5.8G   0% /dev
tmpfs                             1.2G  2.0M  1.2G   1% /run
[COLOR="#FF0000"]/dev/mapper/sn500_vg-ubuntu_1804   16G   11G  4.3G  71% /[/COLOR]
tmpfs                             5.9G     0  5.9G   0% /dev/shm
tmpfs                             5.0M  4.0K  5.0M   1% /run/lock
tmpfs                             5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/mapper/os_vg2-Common          85G   47G   34G  58% /mnt/Common-Files
[COLOR="#FF0000"]/dev/sda1                          79M   25M   55M  31% /boot/efi[/COLOR]
tmpfs                             1.2G   16K  1.2G   1% /run/user/121
tmpfs                             1.2G   32K  1.2G   1% /run/user/1000

```

Example 2:
Linux installed on NVMe, and grub installed to NVMe drive's ESP (NVMe0n1p1). 

```
Filesystem                       Size  Used Avail Use% Mounted on
udev                             7.8G     0  7.8G   0% /dev
tmpfs                            1.6G  1.9M  1.6G   1% /run
[COLOR="#FF0000"]/dev/mapper/wdsn500-ubuntu_1904   31G   14G   16G  47% /[/COLOR]
tmpfs                            7.8G     0  7.8G   0% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            7.8G     0  7.8G   0% /sys/fs/cgroup
[COLOR="#FF0000"]/dev/nvme0n1p1                    99M  7.7M   91M   8% /boot/efi[/COLOR]
/dev/mapper/os_vg-Common         214G  171G   34G  84% /mnt/Common-Files
tmpfs                            1.6G  8.0K  1.6G   1% /run/user/123
tmpfs                            1.6G   24K  1.6G   1% /run/user/1000

```

---

### Post by jeff-5 on 2020-01-21
> [COLOR=#000000]Since old and new installs are both in partition 5 and sdc is DOS, we then know new install is in sdc5 & (hd2,5).[/COLOR]
[COLOR=#000000]At grub> try this:[/COLOR]

[COLOR=#000000]configfile (hd2,5)/boot/grub/grub.cfg[/COLOR]

Okay. That does "work", in that it brings up a grub menu and allows me to select between Windows and Ubuntu. But (hd2,5) is the old Ubuntu 12.04 install, so the Ubuntu it is talking about booting is the old one. No sign of the newer Ubuntu on the grub menu (including in "older versions" or whatever it was called). In case it matters for next steps, the Ubuntu 12.04 install isn't totally happy and only lets me login at the command line.

I still think the problem is that grub can't even see the drive. None of hd0, hd1, hd2, hd3 are it. And hd4, which could be it, doesn't seem to have any partitions -- no (hd4,1), etc. [COLOR=#000000]`ls (hd4)` is gives `unknown filesystem` and `ls (hd4,1)` (or 2,3,4,5) gives `disk not found`. Like this screenshot:

[/COLOR][ATTACH=CONFIG]284859[/ATTACH]

> [COLOR=#000000]Best to always use gpt and have an ESP on every drive.[/COLOR]

Isn't the point of the ESP/EFI just to load the chosen OS from the correct partition? And, in theory, that partition could be on other drives? Or is there really something valuable about having the ESP partition on each drive? I could try physically disconnecting the NVMe and all the other drives, so it would have no choice but to install EFI on that drive. I'm hoping it can carve out some space from the NTFS partition that is there. But isn't the theory that it should be able to load from other drives, and when it loads from other drives it ignores that drive's ESP?

It is certainly true that gpt is only used on nvmen01, and the others are "msdos".

> [COLOR=#000000]I and another user in that thread opted to install rEFInd and got our systems back again.[/COLOR]

I had a quick look at rEFInd. Looks like a big project, and relatively invasive, with scary probabilities of screwing up the working Windows 10 install. I'm going to put it further down my list of things to try...

---

### Post by oldfred on 2020-01-21
New install is LVM? Is it also encrypted?

I do not know LVM, but you may have to install drivers for LVM and encrypted partitions to be seen and load grub drivers (.mod) for grub to boot your LVM install.

Your old BIOS install will not see an UEFI install. And new UEFI install will not boot your BIOS install.
UEFI & BIOS are incompatible, you only can switch boot from UEFI as either UEFI or CSM. Once started to boot in one mode, you cannot change. Or grub only can boot other installs in same boot mode.

---

### Post by Dennis N on 2020-01-22
> And, in theory, that partition could be on other drives? 
The OS you are booting can be on a different disk entirely than the ESP's disk. That's illustrated in the first display of post #6.

> Is there really something valuable about having the ESP partition on each drive?
Some users (myself included) have an ESP, plus an operating system with boot loader installed to that ESP, on more than one disk.  In case one disk fails, they can still boot the computer.

When you install Ubuntu on a system with NVMe drive and SATA drive present, Ubuntu's installer accepts your choice of where to install boot loader. See Post #6 for an example.

---

