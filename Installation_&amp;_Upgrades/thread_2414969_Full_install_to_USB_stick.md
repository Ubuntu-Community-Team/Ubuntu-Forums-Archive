---
title: "Full install to USB stick"
date: 2019-03-18
forum: Installation &amp; Upgrades
---

### Post by alexandrosfa on 2019-03-18
[SIZE=3]Hi!

I am trying to install Ubuntu 14.04 to a 64GB usb stick. I want to make a full installation and not a live cd or anything like that. Whatever I try, it doesn't seem to work (the installation goes ok but it never boots afterwards). Perhaps it is a GRUB issue. But even when I set it to install the GRUB to a usb partition, it still doesn't boot.

Is there an easy guide to do that? If possible I would like to do it with full disk encryption as usb sticks are easily lost.

[/SIZE]

---

### Post by yancek on 2019-03-18
I would first suggest that you not use 14.04 as support for it will end next month.  Pick one of the releases from the Ubuntu site below which is still supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Does the computer you are using to install have another OS?  If so, what is it?  If you have another OS, is it a Legacy/MBR install or UEFI?  Are you familiar with Linux device/partition naming conventions (/dev/sda, /dev/sda1, etc.)?  If you want to be able to boot the usb and it is a Legacy install, you will need to install Grub to the MBR of the usb.  If it is an EFI, install you will need to have an EFI partition on the USB and install Grub code there.

---

### Post by alexandrosfa on 2019-03-18
> **yancek said:**
> I would first suggest that you not use 14.04 as support for it will end next month.  Pick one of the releases from the Ubuntu site below which is still supported.

Will upgrade to 16.04 it as soon as I install it. Need to start with 14.04 though.

> **yancek said:**
>  Does the computer you are using to install have another OS?  If so, what is it?  If you have another OS, is it a Legacy/MBR install or UEFI?  Are you familiar with Linux device/partition naming conventions (/dev/sda, /dev/sda1, etc.)? 

Tried it to several laptops and desktops. Some of them had only Ubuntu installed, others were dual boot (windows/ubuntu). Always the same issue. It just doesn't boot afterwards whatever I try.

That's why I search for a step by step guide.

---

### Post by oldfred on 2019-03-18
It depends a lot on whether UEFI or BIOS.
And if system is newer than 2014, better to use newer Ubuntu to have support for newer hardware. Older versions do have kernel updates, if using 14.04.5.
       Ubuntu 16.04.6 LTS Released With APT Vulnerability Fix, Other Security Updates  

If using full drive encryption best to review this:
       [https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

But however you install you do need to partition in advance and use Something Else install option, unless you can disconnect internal drive, so flash drive seen as first and only drive.

See also:
       [http://ubuntuforums.org/showthread.php?t=2312651](http://ubuntuforums.org/showthread.php?t=2312651)
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i) 
    [https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)

---

### Post by 1clue on 2019-03-18
I would recommend that you install the 16.04 or 18.04 right away. The key failure point of a USB stick is how many times it writes before it has a failure. USB sticks are not the same as an SSD, they fail much much more easily. I've had some fail after just a few full-disk writes.

I would strongly recommend that swap, if any, be on some other device, and that you minimize logging or put it on some other device too.

Are you trying to make a pocket drive you can boot on any x86_64 computer, for travel? Or are you just trying to be economic?

If you'll always boot on your local LAN or on your work LAN, for example (always a known place) then you might consider setting one system up as a network logger, and your stick-boot device can log over there.

---

### Post by alexandrosfa on 2019-03-18
> **oldfred said:**
> you can disconnect internal drive, so flash drive seen as first and only drive.

That's an excellent idea. Perhaps I should do that...

---

### Post by alexandrosfa on 2019-03-18
> **1clue said:**
> Are you trying to make a pocket drive you can boot on any x86_64 computer, for travel? 

Yes!

---

### Post by ra7411 on 2019-03-18
I installed Ub 18.04 to a usb a couple months ago on a bios machine just to see how well it would work.

It did work (after making sure bios was set to boot from the usb versus an HD), but everything slowed down so much that it wasn't useful for me. The machine only has usb 2.0 ports so 3.0 might be ok speed-wise.

---

### Post by 1clue on 2019-03-18
> **alexandrosfa said:**
> That's an excellent idea. Perhaps I should do that...

That might work, but on some of my hardware I know it won't. The machine I'm thinking of is server hardware and won't boot to anything not explicitly declared in the BIOS. So you may need to tinker with the BIOS on each system, to allow boot from USB stick. If it's supported on that box.

---

### Post by C.S.Cameron on 2019-03-18
This works for me on both BIOS and UEFI machines.
[https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412](https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412)
Don't forget to check ISO file for corruption using MD5SUM.

---

### Post by 1clue on 2019-03-19
I haven't done the traveling boot thing, but there are some pretty well-documented setups on the net.

From what I undertand you can't just take a normal distro and install it to make this type of setup and hope for good results. There are extra steps you take to trim the distro down, and to reduce writes to the flash drive. Sometimes you want drive encryption or a TOR setup.

I would start by deciding what exactly you need from this and then go about finding a travel boot flash drive setup that meets your needs.

Personally I would recommend that you make it both UEFI boot and the old style. You never know what you'll get when you're using random PCs with random BIOS settings. I'd also suggest using a flash drive that can be mechanically made read-only, and your OS should be that one, and any writing you want should be on a separate flash drive that your OS knows to look for by some token (maybe UUID)

---

### Post by sudodus on 2019-03-19
If portability has highest priority (that it works in many and various computers), choose a persistent live system according to these links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

If system stability and possibility to upgrade the kernel and device drivers, and 'disk encryption' has highest priority, choose an installed system (installed like into an internal drive but into a USB drive, a fast USB 3 pendrive, or better into a USB SSD). See the following link,

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

and/or [Post #10 by C.S.Cameron](https://ubuntuforums.org/showthread.php?t=2414969&p=13845797#post13845797).

[hr][/hr]
Edit:

If you want both, you can make a USB drive with both a persistent live system and an installed system according to the following link,

[Portable system that boots and works in most computers - Live, persistent live and installed systems](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1)

---

### Post by ubfan1 on 2019-03-19
For a random selection of PCs, with all different hardware and driver needs, it's still hard to beat a persistent install media.  For performance, adding the "toram"  parameter (a mkusb or kernel option) copies the system libraries into ram and  greatly reduces startup time on things like libre Write.  If you plan a bit, you can even have the persistence file/partition on a separate USB, and start with a fresh one for each new PC.  A /home file/partition  may be treated the same way,    if you still want a full install, search for "optimize USB" here and on askubuntu for many suggestions to reduce wear/writes.

---

### Post by jdeca57 on 2019-03-19
You could consider using Knoppix since that is a live-usb distribution that has as main advantage that it is meant to be used on different computers and has a good initial hardware recognition. And it limits write to usb since it takes in account the wear of that medium.

---

### Post by ram148280 on 2019-03-20
[COLOR=#000000]I would first prefer you that you not use old ubuntu 14.04  this old version also not supported in some case download from the [Ubuntu site]("https://www.compressware.in/2019/03/game-making-software.html") below which is still supported.[/COLOR]

---

### Post by C.S.Cameron on 2019-03-21
This worked for me as a Full install pendrive with Full Disc Encryption:
[https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314)

---

### Post by pjlam on 2019-05-05
> **C.S.Cameron said:**
> This works for me on both BIOS and UEFI machines.
[https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412](https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412)
Don't forget to check ISO file for corruption using MD5SUM.

Hi - I tried out C.S.Cameron UEFI/BIOS install on my 128GB Sandisk USB stick with mkusb (removing the internal SSD when installing)..

[ATTACH=CONFIG]283199[/ATTACH]
The USB stick works great on multiple laptops (after sorting out the WiFi drivers), HP, Sony and Apple laptops.

However, I repeatedly tried but failed to hide the GRUB menu when booting up the USB stick, since it has only 1 OS (Ubuntu) on it. I use the boot menu shortcut keys on the laptops set the boot order.

Right now, the GRUB menu shows [IMG]https://imgur.com/iG8eTpN[/IMG]up on both BIOS or EFI mode on the laptops (I tried HP, Sony, and Apple one which only does EFI). There are 2 Linux kernels on it in the Advanced Options.
[ATTACH=CONFIG]283198[/ATTACH]
...despite using every single method documented on askubuntu below: modifying the parameters on /etc/grub/grub.cfg, adding parameters/disabling OS Prober, or even modifying /boot/grub/grub.cfg (which is generated automatically)

[https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot](https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot)
ihttps://askubuntu.com/questions/879881/how-can-i-get-my-grub-menu-to-be-hidden-and-have-the-shift-or-esc-keys-show-the/882268

What I suspect is there are multiple GRUB configuration presents, C.S. Cameron method involves copying the GRUB from sdx5 to sdx3...So I have one on ext4 partition and one on EFI partition. I went to the EFI partition mount point /boot/efi and found /boot/efi/grub/grub.cfg, but not sure if I should change it.

How can I get my GRUB menu to be hidden at boot time? (with BIOS/EFI secure mode or not)

Below are the Boot repair boot info script output:
[http://paste.ubuntu.com/p/9G3kWqzkCt/](http://paste.ubuntu.com/p/9G3kWqzkCt/) - This one has 2 disks, sdb is the USB stick, sda is the HP Samsung SSD that I cloned from USB using clonezilla disk copy[URL="http://paste.ubuntu.com/p/PRQ8CCDJPN/"]
http://paste.ubuntu.com/p/PRQ8CCDJPN/[/URL] - To simplify thing, this one only has the HP Samsung SSD booted (From the USB stick clone)

Thanks a lot for your help...

---

### Post by C.S.Cameron on 2019-05-05
@pjlam
Try setting timeout=0

---

### Post by pjlam on 2019-05-05
> **C.S.Cameron said:**
> @pjlam
Try setting timeout=0

Thank you. I did change setting timeout to 0, experimented with all the timeout setting. I also changed CMDLINE_LINUX_DEFAULT parameters, I tried quiet, splash, quiet and disabled OS prober...it didn't put the GRUB menu away in BIOS/UEFI mode.

```
GRUB_DEFAULT=0
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_RECORDFAIL_TIMEOUT=0
GRUB_DISABLE_OS_PROBER=true
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""
#GRUB_FORCE_HIDDEN_MENU="true"
#export GRUB_FORCE_HIDDEN_MENUT
```

The /etc/grub/grub.cfg above is sdb5 partition (ext5). I'm wondering if GRUB is reading from sdb3 efi partition parameters instead?

```
Filesystem      Size  Used Avail Use% Mounted on
udev            8.4G     0  8.4G   0% /dev
tmpfs           1.7G  9.9M  1.7G   1% /run
/dev/sdb5        91G   44G   43G  51% /
tmpfs           8.4G   91M  8.3G   2% /dev/shm
tmpfs           5.3M  4.1k  5.3M   1% /run/lock
tmpfs           8.4G     0  8.4G   0% /sys/fs/cgroup
/dev/sdb3       252M   70M  183M  28% /boot/efi
tmpfs           1.7G   74k  1.7G   1% /run/user/1000
/dev/sdb1        31G   91M   31G   1% /media/alphaone/usbdata
```

---

### Post by C.S.Cameron on 2019-05-05
I also had a "set timeout" down at the end of "d30_os-prober" that prevented the menu from disappearing.
(d30_os-prober has a menuentry to boot ISOs on other drives).

I expect my external drive to boot from sdx3 not sdx5. which did you use for boot loader?

---

### Post by pjlam on 2019-05-06
> **C.S.Cameron said:**
> I also had a "set timeout" down at the end of "d30_os-prober" that prevented the menu from disappearing.
(d30_os-prober has a menuentry to boot ISOs on other drives).

I enabled os_prober on /etc/default/grub.cfg, modified ```
 [COLOR=#4F4F4F][FONT=&amp]sudo vim /etc/grub.d/[/FONT][/COLOR][FONT=&amp]30[/FONT][COLOR=#4F4F4F][FONT=&amp]_os-prober[/FONT][/COLOR]
```
*```
timeout_style=menu
``` to ```
 timeout_style=hidden
```*

> I expect my external drive to boot from sdx3 not sdx5. which did you use for boot loader?
I don't know a good way to find a way which boot loader (GRUB grub.cfg) to use if there are multiple ones, in this case sdx5 (on ext4 Linux filesystem) vs sdx3 (on EFI system)

Thanks to your suggestion that external drive boot from sdx3...I suspect the config file is not updated on sdx3. Sure enough I did a diff and they are different. So I copied the grub.cfg from sdx5 to sdx3 (boot/efi is the mount point for sda3)

```
sudo cp -p   /boot/grub/grub.cfg /boot/efi/boot/grub/ 
```

And voila the GRUB boot menu disappeared

---

### Post by oldfred on 2019-05-06
If you have multiple installs, the /EFI/ubuntu/grub.cfg in the ESP controls which is default boot. But that grub menu should let you boot into all other installs. 
And you have to update grub in the default boot install.

But with external drives you should have an ESP on the external with its own boot configuration. 
Grub installs to first drive usually sda or first NVMe drive. But UEFI directly boots external drives from /EFI/Boot/bootx64.efi. So you can copy /EFI/Boot & EFI/ubuntu from internal drive's ESP to external drive's ESP and then be able to directly boot from UEFI.
Then if any issue with internal drive, you can boot external like the flash drive installer.

---

### Post by pjlam on 2019-05-07
Thank you Fred, especially for all your answers in the forums and elsewhere, they are super useful.=d>

Your explanation above makes sense. 

But I'm not clear could one particular grub controls both internal and external drives? Say If I brought the external Ubuntu USB drives (with BIOS and ESP partition so bootable with BIOS/UEFI, and grub) to an unknown computer and unknown OS on it (The internal HD can be Windows / Mac / Linux. It can have  too grub or a Windows NTLDR).

My limited understanding is the grub does look for all the systems on the HD (I saw recommendation when installing bootable USB, remove the internal HD first), and grub communicates with the NVRAM.

On some computer's boot options (particular Dell one), when I press F12 on Dell, with bootable USB flash say a Sandisk USB 3.0, on UEFI partition it will confusingly list this USB twice, one probably points to the ESP and another to BIOS. This confuses admin I talk to. See below...

The reasons I'm asking these is we are distributing an Ubuntu application (in semi-kiosk "mode"), say to schools and charities in bootable full-installation Ubuntu USB flash. 

We clone these USB via clonezilla, and we don't assume schools or charities admins have detailed Linux (We asked them to download iso first, but most admin don't know how to burn a USB bootable iso). Their laptops/desktops maybe running Windows or Mac. So our bootable USB must be compatible with most of their systems. To them, configure the BIOS to boot from USB is already a tall order. 

We thought of having a script updating the grub after they booted and ran the application for the first time with the external USB, so we can present them a menu of OSes to boot. But I don't know if it's desirable. Say if the admin remove the USB, we don't want the GRUB to be out-of-date or to be present (as it will go back to a single OS only, say Windows).

---

### Post by oldfred on 2019-05-07
A bootable installer flash drive has two boot modes, one UEFI and one BIOS/CSM/Legacy. Usually it says something like UEFI: pmap and pmap (for BIOS boot on my system), but others have name or label of flash drive like your Sandisk in place of my pmap.   

A full install will typically have two UEFI boot entries, one using shimx64.efi and one using grubx64.efi. The shimx64.efi is for secure boot but works for Secure boot off also. So when Secure boot is off, both entries work.

UEFI only boots external devices directly from /EFI/Boot/bootx64.efi. Ubuntu installer has that file as a version of grub/shim to boot installer in UEFI mode and uses syslinux in MBR to boot in BIOS mode. Those then are the two entries UEFI finds to boot an external directly.

A full install to an external drive does not have to have an ESP - efi system partition on the external, but then all boot files are on an internal drive and it only boot from the ESP on that internal drive. I have a full install on sda, and every time I install to a flash drive or USB SSD, it overwrites my /EFI/Ubuntu folder with the external drive's UUID & partition. If I unplug flash drive, system does not boot. But if I copy back my original /EFI/ubuntu then I can boot internal install. And if I run sudo update-grub it may add external. But I never do that as I copy /EFI/Boot & /EFI/ubuntu to an ESP on external drive to directly boot it with UEFI, not thru grub, often have to change/edit grub drive from hd3 to hd0 as directly boot drive is always first drive in UEFI/BIOS/grub or hd0. UUID should work but does not always seem to with external drive.

If you plug in a flash drive with grub, and directly boot it,  it only wants to boot that install, unless you then after booting run sudo-grub grub. But those entries become invalid, if you plug into another system.

When I had issues with my grub & UEFI, I used rEFInd. It finds all UEFI bootable installs & offers to boot them. I liked rEFInd as it fit on an very old tiny 256KB flash drive that was too small for anything else.
I did not use, but think Super-grub's UEFI version,  Rescatux, would also work. But I have not used it since BIOS and then only using Super-grub.

Almost all systems since 2012 and release of Windows 8 are UEFI, but many users have installed Windows 7 in BIOS mode and maybe updated to Windows 10. So we do not know if system is booting in UEFI or BIOS boot mode, just because user says they are booting Windows 10 (or *).

So if Booting a flash drive, you need to know if system is UEFI or (now old) BIOS for current installs. And then you need to boot USB drive in same boot mode as new UEFI systems do not automatically boot flash drive in same mode as installs, each user has to choose.
If Secure boot is on, then system will only boot in UEFI Secure boot mode. But most systems then need in UEFI a setting change to allow USB boot or full USB access. Often required even if Secure boot off.

So you need to check if current installs are UEFI or BIOS, if system is after 2012, then UEFI and you may need or want to turn off UEFI Secure boot, and turn on allow USB  boot. And then be sure to boot flash drive in same boot mode as installed systems.
Many older UEFI need updates from vendors. And new systems with NVMe SSDs need firmware updates.

---

### Post by sudodus on 2019-05-08
> **pjlam said:**
> 
The reasons I'm asking these is we are distributing an Ubuntu application (in semi-kiosk "mode"), say to schools and charities in bootable full-installation Ubuntu USB flash. 

We clone these USB via clonezilla, and we don't assume schools or charities admins have detailed Linux (We asked them to download iso first, but most admin don't know how to burn a USB bootable iso). Their laptops/desktops maybe running Windows or Mac. So our bootable USB must be compatible with most of their systems. To them, configure the BIOS to boot from USB is already a tall order. 


- I think it will be necessary that the admins at schools and charities can configure the BIOS to boot from USB, because I think it will be more difficult for them to modify the original boot system. In many computers F12 (or another special key) will activate a 'temporary' menu, that includes USB.

- An **installed** system is flexible concerning update & upgrade, and it is portable between computers, except when a proprietary hardware driver is necessary (for example for the graphics chip or wifi chip).

- A **persistent live** system is *more portable* between computers (than an installed system), but can also be limited when a proprietary hardware driver is necessary. Furthermore, it is not as flexible concerning update & upgrade (as an installed system), it is not possible to use full disk encryption, and it is more sensitive to corruption (so it is important with a good backup if the users want to save data).

I made a system for a USB drive, that combines the two. It is described at the following link, and you can create your own system according to the description (but first you can simply clone from the uploaded image file to test it).

[help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1)

---

