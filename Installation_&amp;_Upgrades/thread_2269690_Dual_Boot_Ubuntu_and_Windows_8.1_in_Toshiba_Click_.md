---
title: "Dual Boot Ubuntu and Windows 8.1 in Toshiba Click 2 Pro"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by austin30 on 2015-03-17
I returned my Lenovo Yoga 2 pro (yellow issue) and got this Toshiba Click 2 Pro. (i7/8GB/128 GB SSD)
Can anyone help me with a step by step instructions or a URL for installing Ubuntu on it. I need a dual boot system with Windows.
I already have the 14.10 Live USB and with a live session Wifi, touchpad, touchscreen everything seemed to work. 
I don't have much knowledge on the UEFI stuff and Genral Linux/Ubuntu things. And  I heard with Toshiba it is generally tough.

---

### Post by oldfred on 2015-03-17
Do not know if this model is like others with Toshiba, but they installed ok, but then needed a work around to get system to boot Ubuntu in UEFI mode.
Vendors are modifying UEFI to only boot Windows using UEFI entry description. But they still allow a hard drive entry to work, so we copy grub/shim into the /EFI/Boot folder and rename either grub or shim(secure boot grub) to be bootx64.efi. 

Always backup efi partition and Windows before doing any install.

Use Windows to shrink the NTFS partition and reboot immediately to let it run chkdsk and make repairs. Make sure fast boot or always on hibernation is off. If UEFI has a separate fast boot setting either turn it off or set it to allow several seconds so you can get into UEFI from the keyboard. 
Some systems are designed to boot so fast that you cannot change anything. And if Windows breaks you cannot fix system.

Also make a Windows repair flash drive. Links to details if needed in link in my signature.
You should not need Boot-Repair anymore. Ubuntu installs and works. But if issues then the Summary report from Boot-Repair is very useful for review of issues.

Many useful links on installing in the link in my signature below. First couple may be all you need:
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
More info on Windows:
[http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by austin30 on 2015-03-18
Will try this some day later. Thank you.

---

### Post by austin30 on 2015-03-19
I have made USB as the first boot device and created Macrium Reflect backup (external HDD) and Rescue Disk (Pen Drive).
Isn't that enough if something happens?
Couple more questions:
Can I go with Along with Windows 8.1 option (if that comes up) as mentioned in the updated guide in the links above instead of "something else"?
Is SWAP partition really needed? I have disk space constraint (128 SSD). My RAM is 8 GB. I don't want hibernate, but do need suspend. The maximum memory hungry task I do will be RAW photo editing.
Is it possible to make Ubuntu option appear in Windows bootloader (EasyBCD?) so that I don't have worry about  GRUB being removed with Windows updates etc.

---

### Post by oldfred on 2015-03-19
UEFI is not like BIOS. With BIOS you only have one MBR and only that boot loader in MBR controls booting.
With UEFI every system is equal and adds its own folder into the efi partition. From UEFI you should be able to boot any system that has a folder in the efi partition. It is like having many MBRs and from UEFI choosing any one.  Of course a backup of efi partition is also good to have.
But some vendors modify UEFI to only boot Windows, so then various work arounds end up being required.

If installer does not show Windows 8, then you can only use Something Else. There has been a major bug where installer does not correctly see Windows 8 and usually then totally overwrites it. Something Else install has worked without overwriting.  There are major updates to installer with 15.04 that will be out in April, that will make it more clear if partitions are overwritten or not, based on user selection of install options.

---

### Post by austin30 on 2015-03-19
OK. Thanks for the explanation. In my Toshiba Click 2 pro, I tried Del, F9 F12 etc..but it always go to Windows directly. So that means having GRUB as the primary in EFI is the only option? If so that means restoring GRUB after the Windows updates, right? I am OK with that, but just to confirm.

So if Windows 8 is shown is it safe to give "Along with option"?
If not safe or if it is not detecting Windows 8 I will go with "Something Else" option. In that case do I need SWAP partition?

Do you think it is worth waiting for 15.04? Also Can I upgrade to 15.04 from 14.10?

I know it is lot of questions, but sorry I am quite new with all these. Thanks again for your support.

---

### Post by oldfred on 2015-03-19
If you have 8GB of RAM, you may never use swap, but I still suggest 2GB just to have some. Some users have posted that they do not have any swap and it has worked.

I do not suggest 15.04, now for a new user unless you are just experimenting, but a few with very new hardware find the newer version does work better as it includes lots of updates to kernel, support software & video drivers. You should be able to upgrade to the next version, soon after it becomes official. But I normally backup /home, some other settings and a list of installed apps and just reinstall, with Something Else. But I keep a LTS version as my main working install and have other / (root) partitions for experimenting with settings or versions. That way I know I have one working system and do not mess it up with changes.

---

### Post by austin30 on 2015-03-19
Thanks a lot. That helps.
Could you please answer my first two questions in my previous post - About GRUB & Windows updates and "Along with Windows 8" option.

---

### Post by oldfred on 2015-03-19
Grub & Windows co-exist in efi partition, and if Toshiba followed UEFI standards correctly you would have no issue booting either Windows or Ubuntu from UEFI menu.
But it seems Toshiba now modifies UEFI to only boot Windows. The main work around other Toshiba users have posted it to change the hard drive boot entry to really be grub or shim. Then you can boot either Windows or Ubuntu from UEFI. 

Some change the Windows efi file to really be grub, but then updates to Windows overwrite that change and then you can only boot Windows until you redo change. And if grub is the Windows file you can only boot Windows from grub menu, or if you have grub boot issues nothing boots.

I only suggest the Something Else install option. Anything else depends totally on whatever logic is going on behind installer. And almost always better to have a smaller / of 25GB which auto installer will not do.

---

### Post by austin30 on 2015-03-20
OK. I will go for the "Something Else" then. 
What is the difference in the two ways you told:
>> T[COLOR=#000000]he main work around other Toshiba users have posted it to change the hard drive boot entry to really be grub or shim
[/COLOR]and 
>> [COLOR=#000000]Some change the Windows efi file to really be grub

[/COLOR]In any case, if something happens, I should be able to recover with my USB Rescue Disk and Macrium Recovery Images, right? I have USB as the first boot device in the UEFI Settings. Whatever happens the boot order won't change, unless I change it in UEFI settings, right? And any idea how I can get on to UEFI settings other than from Windows? As I told you F12, F9 didnt work.

---

### Post by oldfred on 2015-03-20
Windows has a fast boot setting, your UEFI may also have a fast boot setting. 

My UEFI motherboard had a fast boot setting that had multiple options where it offered fast boot on/off hard/cold reboot, on/off on warm reboot and a number of seconds delay so you could press f8 or f10 (already forgot). I first set UEFI fast boot off as I was changing a lot of settings. Then I changed it to on with a 3 second delay on warm reboot and off on cold reboot, so I can get into it if needed.


You can also see if this grub entry takes you to your UEFI.
```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

```

If dual booting do not change the Windows efi boot file bootmgfw.efi to be grub. You want to be able to directly boot Windows from UEFI menu not just from grub. And you have to create a new grub entry for whatever you rename the real bootmgfw.efi to, so you can boot Windows from grub. But grub only boots working Windows so if any issues, you want to be able to directly boot Windows.

Best to also have Windows repair flash drive. If you do not know how to make that, links are in the link in my signature.

---

### Post by mattharris4 on 2015-03-20
> **austin30 said:**
> I returned my Lenovo Yoga 2 pro (yellow issue) and got this Toshiba Click 2 Pro. (i7/8GB/128 GB SSD)
Can anyone help me with a step by step instructions or a URL for installing Ubuntu on it. I need a dual boot system with Windows.
I already have the 14.10 Live USB and with a live session Wifi, touchpad, touchscreen everything seemed to work. 
I don't have much knowledge on the UEFI stuff and Genral Linux/Ubuntu things. And  I heard with Toshiba it is generally tough.

I have a Toshiba Satellite that I bought about eight months ago, a Lubuntu install went flawlessly using the standard dual-boot installer.  I am not familiar with the Click 2 Pro but I would think it is similar if you have bought it new in the past year or so.  However, make sure your swap area is not on the SSD (if you have one, you need it for hibernate and sleep to work properly but with 8GB RAM otherwise you do not), swap in any OS (and defragging in Windows) will kill it quickly.

---

### Post by austin30 on 2015-03-21
Thank you oldfred and Matt.
I could get to UEFI settings with the F2 key.
Also created Windows repair drive. So I think I can try it soon.

Matt what did you mean by dual boot installer?

I was planning to put minimal 2gb for swap. Some people say swap needed only for hibernate and not for suspend. If that is the case I don't want swap either. I just need suspend. 

Oldfred,
Could you please tell me the best and safest steps to follow if after Ubuntu install it takes me to Windows directly. That is mostly the case since my UEFI settings does not have a boot menu option.

---

### Post by austin30 on 2015-03-21
So finally installed Ubuntu with Secure boot ON and 2 GB of swap. Maybe I will put swappiness of 10 or something to reduce the writes. 
Right now everything looks great. Ubuntu works fine. Suspend works. I got the GRUB menu directly and Windows also works fine. Thank you very much oldfred. Thanks Matt too. 
One final question before I close this thread. What should I do when the grub possibly gets replaced with a windows update and it boots directly to Windows?

---

### Post by oldfred on 2015-03-22
You need Ubuntu live installer, so you can just copy grub back again.

Most with Toshiba's find it better to copy grub to /EFI/Boot and rename bootx64.efi. So then you can directly boot Windows from Ubuntu.I do not think Windows updates bootx64.efi, just its bootmgfw.efi.

---

### Post by austin30 on 2015-03-22
So since in my case I didn't have to do any renaming, i think this should just work fine even after a windows update, right?
Anyways, if at all I have to do that renaming stuff, could you please give more details on what to do after booting live usb.

---

### Post by oldfred on 2015-03-23
If you can boot without renaming that is even better.

Details are in link in my signature.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by austin30 on 2015-03-23
Thanks a lot oldfred again.
I will close this thread.

---

