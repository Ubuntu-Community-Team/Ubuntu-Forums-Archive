---
title: "Update last line of fstab for bootable clone?"
date: 2022-06-05
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2022-06-05
I used FoxClone to clone my entire internal SSD from my ASUS Flip 15 laptop to a 2TB USB-C HDD, no problems. It boots on my other laptop, a Lenovo G710 (but the WiFi HW is different, so I didn't go any further, I didn't want to modify anything on the clone). So that all seems well. FYI, I have installed Xubuntu on the ASUS (no Windows) with a separate /home partition, and a 32GB swap partition, and two other partitions of ~ 50GB so I could experiment with other installs. I cloned the entire drive, didn't mess with anything like choosing partitions, etc.


But, I would like to be able to boot this on the ASUS that I cloned, and I am aware that this will cause a UUID conflict since the clone has the cloned UUIDs. I don't want to have to remove the internal SSD to test this.


I thought I found a clever work-around: in the BIOS I disable the internal SSD as a boot device. Well, it did appear to boot from external HDD, but I saw that didn't prevent it from seeing the /home on the internal SSD. I shut it down as soon as I realized that.


OK, so I've seen the comments about updating /etc/fstab for this, I wasn't sure what that entailed, but it was (mostly) pretty obvious, I saw each of the partitions listed with their UUID, and some other info. So I used Gparted to check and create new UUIDs for each partition, verified with the blkid command, then backed up and edited fstab with those new UUIDs. All seemed smooth, until I see the last line if fstab:    


/dev/disk/by-id/wwn-0x50004cf20811b9b9-part2 /mnt/wwn-0x50004cf20811b9b9-part2 auto nosuid,nodev,nofail,noauto,x-gvfs-show,rw 0 0


That's not a UUID. And when I try booting it seems to try to go to the ext HDD, but ends up booting from the internal SSD. I don't know if there are any logs to look at for hints? I'm guessing that last line is telling the system to mount the '/' (which is partition 2 on my system), but instead of UUID, it's this “/dev/disk/by-id”, still pointing back to the internal SSD?  And I'm not seeing this “wwn-0x50004cf20811b9b9-part2” with blkid, and  ls -la /dev/disk/by-id/ references to part 2 are:


“lrwxrwxrwx 1 root root  15 Jun  5 07:49 nvme-eui.0000000001000000e4d25ca4e32f5301-part2 -> ../../nvme0n1p2”
“lrwxrwxrwx 1 root root  15 Jun  5 07:49 nvme-INTEL_HBRPEKNX0202A_PHTE105600BR512B-1-part2 -> ../../nvme0n1p2”


and on the external HDD clone:
“lrwxrwxrwx 1 root root  10 Jun  5 07:49 usb-WD_My_Passport_260D_5758563245343144594B5A37-0:0-part2 -> ../../sda2”


**My question:** What am I supposed to do to update that last line to make the external HDD bootable on my ASUS with the cloned source drive attached? I seem to be very close, I think just this last step is the hangup.

TIA - NTL2009

---

### Post by oldfred on 2022-06-05
I would think the id or device identification would avoid conflict. 
I prefer UUID or labels. But ID is another option as is partUUID (GUID) with gpt drives.
Labels often have more meaning, so you really know which partition is which. UUIDs are not easy to remember which is which.

ls -ld $(find /dev/disk)
ls -F  /dev/disk/by-* 
by-id/  by-label/  by-partuuid/  by-path/  by-uuid/

for details and examples:
man mount 

Good examples:
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)

---

### Post by tea for one on 2022-06-05
> **NTL2009 said:**
> I thought I found a clever work-around: in the BIOS I disable the internal SSD as a boot device. Well, it did appear to boot from external HDD, but I saw that didn't prevent it from seeing the /home on the internal SSD. I shut it down as soon as I realized that.

Rather than disable the internal ssd as a boot device, it's possible that you have a UEFI/BIOS setting to disable access to the ssd completely.
Please see similar setting in attached screenshot.

---

### Post by NTL2009 on 2022-06-05
OK, thanks. So from that, is this the correct sysntax for fstab (using the 'new' UUID from my external clone)? Here's my original and 'new' UUIDs (new on WD2TB):

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
# UUID=3421a03d-a5ef-40e1-994b-ad5c081d6c5f /               ext4    errors=remount-ro 0       1
#   on WD2TB ssd2
UUID=b92b1932-6f97-4c14-9352-9821ef7ed8ba /               ext4    errors=remount-ro 0       1

So change that last line from:
# /dev/disk/by-id/wwn-0x50004cf20811b9b9-part2 /mnt/wwn-0x50004cf20811b9b9-part2 auto nosuid,nodev,nofail,noauto,x-gvfs-show,rw 0 0

to:

/dev/disk/by-uuid/b92b1932-6f97-4c14-9352-9821ef7ed8ba /mnt/b92b1932-6f97-4c14-9352-9821ef7ed8ba auto nosuid,nodev,nofail,noauto,x-gvfs-show,rw 0 0

is that all? Or do I need to run something for these to update/populate other parts of the system?

---

### Post by oldfred on 2022-06-05
As long as it is not a duplicate UUID.
I prefer to create a mount point that says something about what is in the partition.
so I create /mnt/data or /mnt/photos etc.
And then use that, so file browser does not show some UUID that I do not know what it is.

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -e 7 -o model,name,fstype,size,fsused,label,partlabel,mountpoint [/COLOR]
MODEL                          NAME        FSTYPE   SIZE FSUSED LABEL     PARTLABEL            MOUNTPOINT 
HGST HTS721010A9E630           sda                931.5G                                        
                               &#9500;&#9472;sda1      vfat   510.2M        ESP_B     EFI System Partition  
                               &#9500;&#9472;sda2      ext4    30.3G   6.1G hirsute   hirsute              /media/fred/hirsute 
                               &#9500;&#9472;sda3      ext4    49.8G  51.8M ISO_b     ISO_b                /media/fred/ISO_b 
                               &#9500;&#9472;sda4      ext4   147.6G 114.2G backup_b  backup_b             /media/fred/backup_b 
                               &#9500;&#9472;sda5      ext4    30.3G   6.3G focal_a   focal_a              /media/fred/focal_a 
                               &#9500;&#9472;sda6      ext4   302.7G 110.2G data      data                 /media/fred/data 
                               &#9500;&#9472;sda7      swap     2.1G                                        
                               &#9500;&#9472;sda8      ext4    24.4G   8.2G impish    impish               /media/fred/impish 
                               &#9500;&#9472;sda9      ext4      24G     7G groovy_k  groovy_k             /media/fred/groovy_k 
                               &#9492;&#9472;sda10     ext4    33.3G   9.7G jammy-b   jammy_b              /media/fred/jammy-b 
SSD 850 EVO                    sdb                232.9G                                        
                               &#9500;&#9472;sdb1      vfat     510M        M2_ESP    EFI System Partition  
                               &#9500;&#9472;sdb2      vfat     5.9G        FAT       FAT                   
                               &#9500;&#9472;sdb3      ext4    35.2G        jammy-ssd                       
                               &#9492;&#9472;sdb5      ext4   127.4G 101.6G m2_data   m2_data              /media/fred/m2_data 
Samsung SSD 970 EVO Plus 500GB nvme0n1            465.8G                                        
                               &#9500;&#9472;nvme0n1p1 vfat     512M  12.8M ESP_NVME  esp_nvme             /boot/efi 
                               &#9500;&#9472;nvme0n1p2 ext4    29.3G   8.7G focal_0   focal_0              /media/fred/focal_0 
                               &#9500;&#9472;nvme0n1p3 ext4    29.3G  10.2G focal_k   focal_k              /media/fred/focal_k 
                               &#9500;&#9472;nvme0n1p4 ext4    29.3G  10.8G jammy     jammy                / 
                               &#9492;&#9472;nvme0n1p5 ext4   195.3G 141.7G nvme_data nvme_data            /mnt/data


[/FONT]
```

---

### Post by NTL2009 on 2022-06-05
Thanks all - I'll try these later, I have to run, won't get to this until tomorrow.

---

### Post by NTL2009 on 2022-06-06
OK, back to this now. I tried the above change to fstab:


/dev/disk/by-uuid/b92b1932-6f97-4c14-9352-9821ef7ed8ba /mnt/b92b1932-6f97-4c14-9352-9821ef7ed8ba auto nosuid,nodev,nofail,noauto,x-gvfs-show,rw 0 0


And on my ASUS (the system I cloned from, then mod'ed the UUIDs) I can set the ext clone as the boot device, I see the disk activity led, but then boots from the internal SSD (Disks shows nothing mounted from the external).


Do I need to run something (grub update?) for these to update/populate other parts of the system? If so, is there a good tutorial on that somewhere? I recall trying some of this years ago, and ending up with a grub that only let me boot when the external drive was connected! I somehow got that fixed, but I know one needs to be careful.

---

### Post by NTL2009 on 2022-06-06
> **tea for one said:**
> Rather than disable the internal ssd as a boot device, it's possible that you have a UEFI/BIOS setting to disable access to the ssd completely.
Please see similar setting in attached screenshot.

Nice idea, but unfortunately no, I see no way to disable the entire drive from my BIOS.

---

### Post by oldfred on 2022-06-06
This report shows all the details of your boot, except settings in UEFI.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You boot from UEFI boot menu, not from grub, unless in grub you add a boot stanza or configfile to boot another install.
Some examples, many others thoughout this thread.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by NTL2009 on 2022-06-06
Thanks, I installed boot-repair, here's the link:

[https://paste.ubuntu.com/p/VZqVPDBQ89/](https://paste.ubuntu.com/p/VZqVPDBQ89/)

For reference - The internal SSD is my normal boot (nvme0n1), I installed Xubuntu w/o any windows boot options. Separate /, /home, 32GB swap, and two other partitions to 'play with'.

The clone that I'm trying to be able to boot on this same machine for testing is a 2TB Western Digital HDD (sda).

I've changed the UUIDs on the etc/fstab on the HDD, and made that last line change from 'by-id' to by-UUID' discussed above.

I did just change secure boot to disabled - it didn't seem to make any difference in terms of booting, should I change that back and re-run the report?

TIA

---

### Post by oldfred on 2022-06-06
I see partUUID which are gpt's GUID for each partition are still duplicated.
UEFI uses partUUID to know which partition to boot from, so that is an issue. Not sure if others are major issues, but best not to have duplicates.
This is part of why I always suggest a new install & restore from backup. Often quicker & easier.

gdisk's expert's menu has a change GUID/partUUID option. Never had to use it, so do not know details more than man page.

---

### Post by NTL2009 on 2022-06-07
OK, thanks - I saw those part-id's on blkid, I never heard mention of changing these in my searches. I just really don't understand why this process is so obtuse/tedious.

Also, you mentioned that 'grub' is not used with UEFI booting. The boot menu I see looks like what grub always gave me - so it looks the same, but is completely different (under the hood)? I did notice that grub.cfg had the original root UUIDs in it.

Anyhow, I'll try changing the part-UUIDs and see what I get.

I understand what you are saying about new install and restore, and especially with a separate /home, that makes it a little easier. But I'm always afraid I'll miss something, forget to install a program, miss a setting. I guess that's easy to fix in most cases, but it just seems to me a clone is what I really want, and getting it to boot ought to not be so hard. Oh, and I'm stubborn :).  

Alternately, is there a really good tutorial somewhere on getting a fresh install to really "mirror" my current install? Things I've found before make a lot of assumptions and provide general directions, rather than specifics. Although I've used Ubuntu/Xubuntu since 2009, and as my main daily use machine since 2015, I'm just not all that familiar with the under-the-hood workings. But I do a *lot* of customizing of the setup to get things fitting the way I work, so it's a pain when most of those are set, but some aren't and I'm hunting around to figure it out. OK, maybe that should be a separate thread.

I'll report back after changing the part-UUIDs.

---

### Post by oldfred on 2022-06-07
With UEFI & grub the boot process is UEFI using partUUID to find ESP.
UEFI boot menu shown with 
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
Partuuid must match entry in efibootmgr.

Then UEFI boots /EFI/ubuntu & ubuntu uses grub.cfg in ESP to find full grub.cfg in your install with grub boot menu.
The /EFI/ubuntu/grub.cfg is just 3 line configfile entry to load install's grub.cfg.
UEFI also can directly boot /EFI/Boot/bootx64.efi. That is used for all external devices and should be a fallback or drive entry in an internal install.

For best & full backup info search forum for TheFu.
site:ubuntuforums.org theFu backup
[https://ubuntuforums.org/showthread.php?t=2440220&p=13944839#post13944839](https://ubuntuforums.org/showthread.php?t=2440220&p=13944839#post13944839)
Oldfred's list of stuff to backup May 2011, desktop only, servers need more:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
[https://ubuntuforums.org/showthread.php?t=2260658](https://ubuntuforums.org/showthread.php?t=2260658)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by NTL2009 on 2022-06-07
*OOOps, I had this written up before I saw your recent reply, so I'll get this out there, and then go back and absorb your latest post:*

Progress???

I changed the partition UUIDs per this ref: [https://askubuntu.com/questions/1250224/how-to-change-partuuid](https://askubuntu.com/questions/1250224/how-to-change-partuuid)

I had noticed that the DISK-IDs were the same, and this instructs you to change that as well, so I did. For p1, I had to use fdisk, then gdisk for p2~p6.

When I booted into the BIOS, my hopes were up. For the first time, the BIOS recognized _both_ the int SSD and the ext HDD as separate bootoable systems. Previosly, I could only get one or the other (by disabling boot on the int SSD). But, selecting the  external HDD ended the same, some disk activity light, but then goes back and boots from the internal SSD.

Here's my latest Boot-Repair report, if you are interested:  [https://paste.ubuntu.com/p/bdkhQRgvts/](https://paste.ubuntu.com/p/bdkhQRgvts/)

---

### Post by oldfred on 2022-06-07
I have multiple Kubuntu & Ubuntu installs, many obsolete. And also have at least two ESP on internal drives and many on external full installs one SSD & many flash drives.

I prefer to change name in UEFI. I change entry in /etc/defaults/grub and then reinstall.
But found new folder created in ESP only partially works. Something is hard coded to only use /EFI/ubuntu/grub.cfg.
Comment this out:
[FONT=monospace][COLOR=#000000]#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
Add this [FONT=monospace][COLOR=#000000]
GRUB_DISTRIBUTOR=jammy

Then after this, uses default ESP in fstab & label from grub.
[/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]sudo grub-install[/COLOR]
Then in efibootmgr you get this:
[/FONT][/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\jammy\shimx64.efi)[/COLOR]


You can also just specify in grub-install
sudo grub-install --bootloader-id=<some_name_for_LinuxX> --no-uefi-secure-boot
See
man grub-install
[/FONT]
[/FONT][/COLOR]


[/FONT]:
[/COLOR]

[/FONT]

---

### Post by NTL2009 on 2022-06-07
> **oldfred said:**
>  ....
Comment this out:
[FONT=monospace][COLOR=#000000]#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
Add this [FONT=monospace][COLOR=#000000]
GRUB_DISTRIBUTOR=jammy ...[/COLOR][/FONT][/COLOR][/FONT]

[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]OK, is that the grub in my ext HDD /etc/default/grub? That's the only place I see that line.

[/COLOR][/FONT][/COLOR][/FONT]> **oldfred said:**
>  .... [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]Then after this, uses default ESP in fstab & label from grub.
[/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]sudo grub-install[/COLOR]
Then in efibootmgr you get this:
[/FONT][/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\jammy\shimx64.efi)[/COLOR]


You can also just specify in grub-install
sudo grub-install --bootloader-id=<some_name_for_LinuxX> --no-uefi-secure-boot
See
man grub-install[/FONT][/FONT][/COLOR][/FONT][/COLOR]
[/FONT]

OK, I'm leery of sudo grub-install, I think I've seen problems before when that's not done correctly. Don't I need to be booted into that system to do that, or it will be doing it on my internal SSD, rather than the external HDD? I seem to recall I ended up with a system that would only boot with the external attached (I guess I finally got it working).

Or is this where you need to do some "chown" to redirect? This is all getting pretty deep for me!

Like this: [https://askubuntu.com/questions/740253/how-to-install-grub-in-an-external-hard-drive](https://askubuntu.com/questions/740253/how-to-install-grub-in-an-external-hard-drive)

---

### Post by oldfred on 2022-06-07
If you are booted into your system, the grub install works fine. But the entry in fstab must be correct.

The simple grub install has lots of assumptions on defaults. I actually ran it on my system just to test that it worked correctly before posting.

Often the issue with external drives is that the internal drive's ESP is in fstab as that is Ubiquity's default. I always change any second drive to use the correct ESP for that drive.

If not booted into your system, you may need chroot or Boot-Repair which allows you to change some of the defaults.

---

### Post by NTL2009 on 2022-06-12
I had to take a little break from this, which maybe was good. We do seem to be down a rabbit-hole here! I know, I was told it's easier to do a fresh install than to make a clone boot-able on the same system, so I was warned!

So I took a step back, and decided to clear out another HDD, I took it to my older Lenovo G710, and installed Xubuntu 20.04 on that external drive, being careful to select the external as the boot device, and it booted fine on that G710. The idea was to think about just making that 'look like' my main install, and keep their /home directories in sync occasionally. This would provide a back up system if I had problems.  But it would not boot on my ASUS. I look at the EPS on the external drive, and it is blank. On the external, fstab tells me the boot info is on sda (the internal of the G710). I repeated this with a 'simple install' and got the same results. Why didn't it put boot information on the external drive?

This was reported as a bug ( [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1970995](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1970995)), but only one person, so I added my notes.  And I see some write ups about how to fix it. But they are also involved.  Here's one that references some others:

[https://github.com/danielTobon43/ubuntuExternalHDD](https://github.com/danielTobon43/ubuntuExternalHDD)

So I suppose this should be a different thread for this problem. Seems I'm hitting rabbit holes anywhere I go.

---

### Post by oldfred on 2022-06-12
Many of us have posted this bug & added to it. It really is the same bug as you posted.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

This work around is also in bug report.
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

---

### Post by NTL2009 on 2022-06-12
Wow, thanks, I didn't find those other bug reports in my search.

I'll try the flag changes later, when I have time. It seems this bug has been around a long, long time. Seems to me that if no one has been able to fix it, they ought to just put in a warning that this does not work as expected, and point to the bug report and/or workarounds. Why waste people's time and add to their frustration level over this?

Bugs like this really hurt Ubuntu (and derivatives). The most likely way that I might try to 'sell' someone on Ubuntu, is to have then install to an external drive to try it out, and assure them nothing will be changed on their hard drive (just anticipate it will be slow running from external). But this would completely turn them off. what a shame. I only wish I had the coding chops to help out with a fix (but other distro don't have this bug, how hard can it really be?).

Thanks, will try later....

---

### Post by NTL2009 on 2022-06-13
An FYI update to this rambling thread (that's just the way things go sometimes!) on the subject of the External HDD not getting the boot information set on it, even though the installer was told correctly, the internal drive was modified.

So I tried the approach above, of un-checking the "boot" & "esp" flags on the internal drive.  I went back to my old (purchased 2015) Lenovo G710, and did this, ran the installer and pointed it to my external HDD, and it seemed to work _for me_ (oldfred mentioned this doesn't seem to work for some people, curious what the conditions are for that).

Further to the story, it crashed with a kernel panic on my ASUS Zenbook Flip 15 (purchased 2021). I figured maybe the hardware is just too different? So I repeated this install approach on the ASUS, so it would pick up the ASUS HW config, and that boots fine on both G710 and ASUS. I probably should have tried recovery mode earlier, oh well, too late now.

Oddly, I didn't seem to have to reset those flags, it boots internal if I select that anyhow? I guess it falls back to other methods?

Further to that... hah! I got my ASUS DEC 2021, so the most recent LTS was 20.04. Now that I'm doing all this, I see 22.04 is out. SO unless there are some warning flags about that release, I guess I should step back and upgrade (fresh install) before I go to far. I have my unmodified clone, so that's good, if things go wacky, just wiping the internal and restoring that should get me going.

So, I suspect I'll be back later, searching for advice on the best way to sync up a fresh install with my previous one. Although I'm not too familiar with the "under the hood" working of the OS, I do a *lot* of tweaking of the desktop and my apps to configure everything. My Xubuntu just 'fits like a glove', and I want to get my new/backup installs set up the same with the least effort. I know many configs are stored in /home, but there's more. OK, that's for another thread - thanks for all the help so far! I sure wish making that clone bootable on the same machine/drive was easier (it takes no effort on the Mac OSX, at least the last time I tried - you clone, reboot holding the option key, select the clone, and away you go! EZ-peasy. I wonder why this is so complicated under Linux?).


*edit add for completeness:* I should mention, my old G710 appears to me to have installs that use legacy and some that use UEFI boot modes. I get different menus depending what boot mode I have set. It originally had 10.04 Ubuntu, then 14.04 (ubuntu or Xubuntu, not sure), and 18.04 Xubuntu. So I'm assuming things changed along the way, but I don't recall. So after I verify I got everything off the drive that I need, I'll do a totally fresh install of 22.04 Xubuntu, that should make things cleaner on that old machine.

---

### Post by NTL2009 on 2022-06-25
An update, and a question (I'll start a new thread on this if warranted):

Got busy with other things, and then did as I mentioned above and updated both computers to Xubuntu 22.04 (left /home in place on my newer 2021 ASUS, totally wiped my 2015 Lenovo G710, it had several old installs on it).

Got things set up with help from this forum on copying/installing the manually installed programs to my ASUS, after setting up and configuring my G710 (at this thread: [https://ubuntuforums.org/showthread.php?t=2476244&p=14101202#post14101202](https://ubuntuforums.org/showthread.php?t=2476244&p=14101202#post14101202) ).

I now have both laptops set up the way I want, so I freed up a 500 GB ext HDD and used FoxClone to clone my ASUS. As above, I'd really like to be able to boot this clone on the ASUS to validate it, which would get me back down the conflicting UUID rabbet-hole. Despite the help here, and lots of reading, I've never been able to get a clone to boot after changing the UUIDS, and even if it can be done, there seems to be a lot of steps to it. But I think I found a pretty simple way around this, and I'd really appreciate some feedback from the experienced people here. And as mentioned above, I'll start a new thread to document this if it seems worthwhile to others:
[B]

My idea to boot the clone on the same source machine:[/B]

We must do _something_ to get around the cloned UUID conflicts to boot on the same machine. I just thought of this, approach it backwards, **don't modify the UUIDs of the clone**. **Instead just (_temporarily_) modify the UUIDs of the internal (clone source) drive** (from a LIVE USB) so there is no UUID conflict. The computer should now boot  to the external drive with no UUID conflict (assuming BIOS is set to boot the external drive).

When done verifying the external clone, from a LIVE USB, set the internal drive UUIDs back to their original values, shut down, remove the external, and boot from internal as before.

To be clear: Since _we would never intend to boot from the internal with the modified UUIDs_, we would never try to make any other changes to it (like fstab) to make it work that way, it's really just to avoid the UUID conflicts with the clone. It has to be reset to be made boot-able.

**Apparent PROS:** Fairly simple, avoids all the work to make the modified clone boot-able, since we don't modify the clone. From LIVE USB change the UUID of the internal drive partitions that are mounted by the system. Change them back when done.

**Apparent CONS:** You are making changes to your "golden" system, and it is unboot-able until you reset the UUIDS! This doesn't sit well with me on principle, but it really does seem to be rather manageable and relatively safe. Obviously, record the original UUIDS (they'd still be in etc/fstab, but make copies!).

If this seems workable, I'd make it even simpler by changing the UUIDS on any install before installing - make the last four digits of the UUIDs "0000". Then just make a change  within the last four digits to disable, and you know you only need to take them back to ".....0000" to make it boot-able, you don't really even need to know the original UUID, since you've standardized on this format. Of course, record them anyway (belt and suspenders). I could/should probably write a small script to do this.

It seems that tune2fs is a default install in Xubuntu, so I'd use this format for the changes:

sudo tune2fs /dev/sda1 -U *266584be-d7b7-11eb-8c76-c3eef48c7257* (substituting the desired UUID of course).

Thoughts? Is this crazy, or should it work, or both?

---

### Post by oldfred on 2022-06-25
With UEFI you also use gpt partitioning which have GUIDs. They also must not be duplicates.
I have always believed in new clean install. Then restore from backups.
Makes sure you have no issues with duplicates as most are related to fstab & grub, but there may be some other locations also.

But UEFI installs to any second internal or external drive that you want separately bootable must be partitioned in advance to make sure drive has an ESP - efi system partition. See this old but current bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)

While my methods works, it may be too complicated for any user not familiar with using terminal to mount & unmount devices.
Others have found these also work, most are in various comments in bug report.

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive.
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

All versions of Ubuntu official & unofficial that use Ubiquity installer have this issue. They only install one grub to first drive's ESP.
External drives also only directly boot from EFI/Boot/bootx64.efi, typically as UEFI:drivelabel in external drive's ESP. Where internal drives boot from /EFI/ubuntu. If an external drive has boot loader installed to internal drive, it will boot from /EFI/ubuntu, but external drive must always be connected even to boot any other install in grub menu.

---

### Post by NTL2009 on 2022-06-25
> With UEFI you also use gpt partitioning which have GUIDs. They also must not be duplicates.
I have always believed in new clean install. Then restore from backups.

Well, my thinking was that when I was _trying_ to get a drive to boot after changing the UUID, and it seemed so hard to do, that any change I did make would render it un-bootable (the temporary intention here). Of course, I guess that doesn't mean the system would fall back to boot the external drive properly, it might get 'stuck' trying on the internal?

I decided to test it on my 'second' machine (the Lenovo G710 laptop), no big deal if I hose something up there. I used FoxClone, and cloned the entire drive.

Then I used tune2fs to alter the UUIDs of / and /home on the _internal_. It would not let me change the EFI partition, or the swap ( I figure swap is no big deal, nothing there). So I disabled the boot, esp flags on it, as that worked before.

It partially worked. It was using the external / and /home, but used the internal boot partition. Then I renamed the internal from p1-EPS to XXXX-p1-EPS, rebooted, and now it showed that the external boot partition was used. **Success! **It still went to internal swap, but no big deal.

I then went and returned the / and /home internal UUIDs to their original, reset the boot, esp flags on internal, shut down, unplugged the external clone, and it booted normally from the internal.

Still a bit of a hassle, but I'm firmly in the camp that says *"If you have not tested your back up, assume you do not have a back up".* My ASUS is still under warranty, and it looks like one screw is a 'tamper-signal', it's got a plug that has to be broken out to get to the screw. Otherwise, I'd probably just open the case and unplug the internal, but even that is a bit of a pain once it's out of warranty.

I agree with you that a re-install is pretty easy/quick. And now that I have the info from the other thread on package management, that's pretty easy/quick as well. But it still takes time getting the settings right, there's a number of steps. For example, I realized that my panel configs had an export/import feature - great, but that's a separate step to know and remember to do (I'm making a much cleaner list for this process), and it looked like that touched on stuff in both /home and root, so it's not just a matter of copying settings I don't think - it's a process, different steps for different items. Some stuff is right there in /home/.config, some in /home/.local - it's just not so easy, IMO. I didn't find the printer set up files, but a few clicks got that working, but just another thing to note.

I should add, I do a *lot* of tweaking of the desktop. I have things set up the way I like, and when I get on a newly installed system, I feel like I'm in a foreign land and don't know the language and have both hands tied behind my back. When I get things set up, I know just where to go to get what I want. Muscle memory kicks in. And there's a lot of tweaks, I use multiple workspaces, and little details as to how the windows respond makes a big difference to my everyday experience. As my wife says, I bet most people just get Windows, and don't change anything. She's probably right, but it would (and did, at work), drive me nuts. I hated (but understood, mostly) that when my work Windows would have problems, the IT guys response was almost always "We'll re-image your drive." Sigh, that means me spending time setting up things again. Oh well. This is one area that MacOS excelled (I assume still does). Make a clone, reboot holding the option key, select the clone, it boots, you test, and you're done. That's it.

Thanks for all the help. I keep working on the process to streamline it.

---

