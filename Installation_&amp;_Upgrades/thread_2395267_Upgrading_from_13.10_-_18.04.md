---
title: "Upgrading from 13.10 - 18.04"
date: 2018-06-29
forum: Installation &amp; Upgrades
---

### Post by Kratos758 on 2018-06-29
Hi all, I've recently jumped back and had a look around Ubuntu I installed years ago. I'm currently dual booting with Windows 10 and running Ubuntu 13.10 (yes, very old release..)

Anyway, the main reason I installed Ubuntu in the first place (this was in 2013 I guess?), was so if for some reason I couldn't boot Windows (happened when I first got my laptop, repaired under warranty) I could boot into Ubuntu and retrieve files and documents easy enough.

My question:
I'm running 13.10. I've done basic research and so far I've found that ideally you'd want to upgrade to each release as it comes out. What would be the best way to go about this?
I'm assuming that the dual boot screen would change too? FYI - I turn my computer on, the screen I get is this below. I can choose Ubuntu to boot, or the third option to boot Windows (I found this photo online)

[IMG]https://www.pcsuggest.com/wp-content/uploads/2017/09/ubuntu_dual_boot_grub_menu.jpg[/IMG]

Sorry if I'm missing something completely obvious or my terminology is off or what not.

I guess also, with my main use of Ubuntu for access to my drives if Windows fails, is it even worth really upgrading it?

Thanks in advance for your help!

---

### Post by Autodave on 2018-06-29
Yes: you need to get rid of that older system that no longer has any security updates!  I, however, would not try updating that: it will take forever and probably not be successful anyway. Download 18.04 and install it by replacing your 13.10 install.

---

### Post by Kratos758 on 2018-06-29
Thanks for your response Dave. Sounds like the logical idea.

I'm looking at my partitions now to delete the one with Ubuntu installed. And I've come across this mess:

[IMG]https://i.imgur.com/9GlgNtJ.png[/IMG]

Advice for the best way to clean this up??
My understanding is I have the C: drive which is my main one, X: which for whatever reason I created years ago? D: which I THINK is the one with Ubuntu on it (not sure though). The other ones I'm not sure what's happened there.

Any way I can be sure on which Ubuntu is installed?

---

### Post by Impavidus on 2018-06-29
If you only need Ubuntu to rescue your files if Windows breaks, there's no need to install Ubuntu at all. Just use a live disk if you need it. But Windows doesn't make it as easy as it used to be to read its files from a Linux system.

If you want Ubuntu installed anyway, make it a fresh install of 18.04.

Your Ubuntu partition must be partition 7, 8 or 9. It's not the EFI partition and the others are NTFS, meaning Windows partitions. When running Ubuntu, you can check using```
sudo parted -l
```which will show the partitions on your drive with a little more detail than the Windows tool. Also try```
mount
```to see how your partitions are used by Ubuntu.

---

### Post by Kratos758 on 2018-06-29
Thanks Impavidus.

I typed that first command and got this result:

```

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  316MB   315MB   fat32           EFI system partition          boot
 2      316MB   945MB   629MB   ntfs            Basic data partition          hidden, diag
 3      945MB   1079MB  134MB                   Microsoft reserved partition  msftres
 4      1079MB  301GB   300GB   ntfs            Basic data partition          msftdata
 5      301GB   362GB   60.5GB  ntfs            Basic data partition          msftdata
 6      362GB   519GB   157GB   ntfs            Basic data partition          msftdata
 7      519GB   569GB   50.0GB  ext4
 8      569GB   669GB   100GB   ext4
 9      669GB   689GB   20.0GB  linux-swap(v1)
10      729GB   750GB   21.5GB  ntfs            Basic data partition          hidden, diag


```

I also used the mount command, but I'm not 100% on what I'm looking at there :o

Any suggestions moving forward? Haha cheers

---

### Post by oldfred on 2018-06-29
You did not post entire command, but I expect it said gpt.
And then Windows is installed in UEFI boot mode.
You need to be sure to re-install Ubuntu in UEFI boot mode. How you boot install media UEFI or BIOS is how it then installs. UEFI will show two boot options for booting live installer.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lots more info in link in my signature.

Your existing partitions will work. Is second ext4 partition a /home. If so you need to use Something Else install option and choose that partition as /home, but DO NOT check the format box.

But new versions of Ubuntu now use swap file, rather than a swap partition. But if installer sees a swap partition it will reuse it. Your swap is very large, and probably does not need to be. If you have 4GB or RAM or more, only 2GB of swap is suggested (some have none). Only if hibernating was larger swap equal to RAM suggested, but if dual booting you should not hibernate, both Windows nor Ubuntu.

---

### Post by mikewhatever on 2018-06-29
An upgrade is out of the question. Just do a clean install.

---

### Post by Kratos758 on 2018-06-29
Thanks gents. I'm about to give this a go to remove Ubuntu partition and then re-install. So those two ext4 partitions and the linux-swap partition are what Ubuntu is installed on (which would be disk 7,8,9 from the windows disk management)? I would like to try clean these partition drives if I can and uninstall and then do a clean install on a new partition with 18.04.

Edit: ok I found (from my old forum posts) that 
> - When I went to install Ubuntu, I think I created the first partition  at 50GB, the /Home at 100GB and the SWAP partition at 20GB

So if that's the case, can I just delete those three partitions completely, and then go about re-installing Ubuntu?

---

### Post by RobGoss on 2018-06-29
Before you start deleting partitions I would also suggest making sure you have a **complete backup **of your Windows system that way if anything goes wrong you can at least restore your system. As suggested a clean installation would be the best choice

---

### Post by yancek on 2018-06-30
If you plan to install a new Ubuntu to the same partitions there isn't much point in deleting them and re-creating them.  You could simply select those partitions to install to with the new system and make sure you format them.  If you have any personal data on any of those partitions you will need to remove the data before installing.  20GB seems like massive overkill for a swap partition.  Ubuntu 18.04 no longer uses a swap partition but uses a swap file.  Either way, simply formatting and installing to the current partitions or deleting them and re-creating should work.

---

