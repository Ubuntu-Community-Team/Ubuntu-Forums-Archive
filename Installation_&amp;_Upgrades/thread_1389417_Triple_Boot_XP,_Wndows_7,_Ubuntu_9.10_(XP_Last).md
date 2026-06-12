---
title: "Triple Boot XP, Wndows 7, Ubuntu 9.10 (XP Last)"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by ZachMitchell on 2010-01-24
I have a bit of a challenge.

My current setup is 3 hard drives. 2 100GB's, and 1 200GB. On my 200GB I have Windows 7 installed, which was the first operating system installed. On one of the 100GB drives is Ubuntu 9.10, which was installed after Windows 7. Now I didn't plan on needing XP, but I recently acquired some recording studio equipment that needs to run with XP, therefor I now need to install XP. I can manage to triple boot it if I install XP first, followed by Windows 7 and Ubuntu, however that isn't an option. I finally have my operating systems configured the way I want and I wish to avoid reinstalling everything. Please note that I am also using GRUB bootloader, not the Windows Bootloader.

So my question is, overall, how would I go about installing Windows XP with Windows 7 and Ubuntu 9.10 already installed first?

Thanks in advance!

---

### Post by kansasnoob on 2010-01-24
> **ZachMitchell said:**
> I have a bit of a challenge.

My current setup is 3 hard drives. 2 100GB's, and 1 200GB. On my 200GB I have Windows 7 installed, which was the first operating system installed. On one of the 100GB drives is Ubuntu 9.10, which was installed after Windows 7. Now I didn't plan on needing XP, but I recently acquired some recording studio equipment that needs to run with XP, therefor I now need to install XP. I can manage to triple boot it if I install XP first, followed by Windows 7 and Ubuntu, however that isn't an option. I finally have my operating systems configured the way I want and I wish to avoid reinstalling everything. Please note that I am also using GRUB bootloader, not the Windows Bootloader.

So my question is, overall, how would I go about installing Windows XP with Windows 7 and Ubuntu 9.10 already installed first?

Thanks in advance!

Well I would absolutely avoid installing XP to the 200GB Win 7 drive. What is the third 100GB drive used for? Storage only?

IMHO the safest route would be to resize the Ubuntu partition and install XP on the same drive as Ubuntu like it shows on pages 3 & 4 here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

Notice that they leave the disc space where they want XP installed unpartitioned and unformatted. Then they select "Unpartitioned space" from the XP installer menu as shown in the first sreenshot on page 4. I've found that to be safer than creating an NTFS partition ahead of time.

Exactly how XP's installer might recognize the Win 7 drive I'm not sure. I'd personally disconnect the Win 7 drive and the "storage" drive before installing so it doesn't mess with the boot sector of either Win 7 or XP.

**[COLOR="Red"]Note:[/COLOR]** the info about grub in that tutorial is probably **wrong**! Since you're using 9.10/Karmic you probably have grub2 and that guide describes restoring legacy grub!

Anyway before I go any further tell me if that sounds like a reasonable option to you and post the output of the following commands while booted into Ubuntu:

```
grub-install -v
```

```
sudo fdisk -l
```

```
df -H
```

And also please include a physical description of the drives. Are they all SATA? A mix of IDE and SATA?

BTW feel free to click on my user name and send me a brief PM just pointing me back to this thread.

---

### Post by oldfred on 2010-01-24
Do you want to be able to boot both windows from windows ever? If not this will allow grub to boot either directly:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by kansasnoob on 2010-01-24
Another option might be running XP in a virtual machine by installing either VirtualBox or VMware in Ubuntu.

---

### Post by ZachMitchell on 2010-01-24
Each operating system does/will have a dedicated hard drive. Windows 7 is on the 200 GB, Ubuntu on one of the 100 GB, and the third hard drive is unformatted which I will put XP on.

So I'd rather not put multiple operating systems on a hard drive.. since i have 3 available.

---

### Post by erictherev on 2010-01-24
I have an Acer Aspire One 0751h netbook that I am attempting to install three operating systems on. The end result will hopefully net me Vista, XP Pro and Kubuntu 9.10. I have installed all three numerous times, and I can only get two working at a time. I can have Vista and Kubuntu or XP and Kubuntu. I believe the problem lies with XP putting boot.ini on sda1, but Vista formats this drive completely during installation. I am installing Vista using an Acer OEM CD, XP is a full version disc, and Kubuntu is a live CD. Vista requires a Windows drive letter of C:, so I'm putting it on sda1.

Here is the partitioning scheme I am working with:

Vista | swap | XP Pro | Kubuntu | storage
sda1 | sda2 | sda5 | sda6 | sda4
NTFS | swap | NTFS | ext4 | NTFS

I have tried installing XP then Vista, as is the general online consensus of how to do this, but then after installing Kubuntu only Vista is recognized.

I have no problem with formatting any or all of the partitions and reinstalling any or all of the OS's. I just want this to work and reinstalling may or may not be the simplest solution.

Factors I believe to be contributing to my problems:

1) Grub2 is not made to be manually edited, as Grub-legacy is.
2) Grub2 does not detect both XP and Vista when I run grub-update.
3) Vista insists upon being located in the first partition.
4) XP puts boot.ini in the first partition.
5) My Acer OEM Vista disc does not allow for a repair, just a complete reinstall.
6) If I install XP prior to installing Vista, the first partition will be formatted, removing boot.ini.
7) Vista does not use boot.ini. This has been replaced with the BCD (Boot Configuration Data).

Any help or ideas would be greatly appreciated.

---

### Post by oldfred on 2010-01-25
If you want to indepentantly boot windows see the links I have above. You have to install both windows to primary partitions also. The second install of windows may install to a logical partition but it will only be able to boot thru the first install on a primary partition.

---

