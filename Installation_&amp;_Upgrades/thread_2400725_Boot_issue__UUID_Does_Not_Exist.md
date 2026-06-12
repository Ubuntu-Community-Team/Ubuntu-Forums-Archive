---
title: "Boot issue:  UUID Does Not Exist"
date: 2018-09-09
forum: Installation &amp; Upgrades
---

### Post by aeb105 on 2018-09-09
Hello All,

Wondering if you can assist wih my post install boot issue.  I installed Ubuntu Studio and when I rebooted it hung.  So I booted from the LInux Boot Repair disk and performed the repair.  When I reboot this time, I get the menu but then the boot is interrupted with a message like this:

[B]"
Gave up waiting for root file system device  Common problems

yatta yatta yatta

Alert!  **************UUID does not exist.  Dropping to a shell:
"
[/B]

Here is the pastebin link from the boot info file from the Linux Boot Repair disk


[URL="http://paste.ubuntu.com/p/fNk6QFBGkB/"]http://paste.ubuntu.com/p/fNk6QFBGkB/


[/URL]

---

### Post by yancek on 2018-09-09
Looks like you installed GRub code in the MBR even though you have an EFI partition/system so the code in the MBR is not necessary or used.  Have you set your BIOS to boot UEFI?  THe UUID you see in the error message should correspond to a UUID for one of your partitions.  We can't tell because you didn't post the UUID.  THe UUID shown in your boot repair output for the root filesystem is: 

> f474ae12-d71a-4a26-a0d2-630417a28af8  
[URL="https://ubuntuforums.org/newreply.php?p=13799357&noquote=1"]

[/URL]

---

### Post by aeb105 on 2018-09-10
UUID=38212bef-3c30-496a-b9e4-b86655601cff

BIOS is set to boot legacy and uefi.  In fact, when I hit the boot menu, the usb stick I'm installing from is under UEFI   It installs without a hitch.  But when I reboot the system hangs.   After I use the Linux Boot Repair disk, it gives the message above.

---

### Post by oldfred on 2018-09-10
You have an old grub in the protective MBR. So if you attempt to boot in BIOS mode from system then it will fail.
You also have to have system set to boot in same boot mode as your install. And install is based on the way you boot UEFI or BIOS the live installer flash drive.
May be better to have setting at UEFI only, but not UEFI Secure boot on.

---

### Post by aeb105 on 2018-09-11
Secure Boot is off.  I have followed those instructions as well. Anything else could cause it?

---

### Post by oldfred on 2018-09-11
From Boot-Repair in UEFI boot mode with live installer, run the full uninstall/reinstall of grub2.

Are you just letting system boot or using f key to get to UEFI boot menu, often f10 or f12, check your manual.

This should be what you are booting which is an UEFI boot.
```
BootOrder: 0000,0001,0002,0008,0005,0006,0007
Boot0000* ubuntu	HD(1,GPT,d104af76-9c3c-4a44-8591-1a2c98bc5ab5,0x800,0x100000)/File(EFIubuntushimx64.efi)

```

---

### Post by aeb105 on 2018-09-11
I use ESC key to get menu where I select boot options.  Then I select UEFI boot option.  I don't see your picture when I boot

---

### Post by oldfred on 2018-09-11
The UEFI boot entry normally just shows "ubuntu".

---

### Post by aeb105 on 2018-09-11
So I am doing a custom partition now and installing boot loader in EFI area  SDA1 instead of SDA which lists the hard drive.

---

### Post by aeb105 on 2018-09-11
Still the same

---

### Post by oldfred on 2018-09-11
When you install grub, you always specify a drive.
But with UEFI installs Ubuntu's grub only installs to first drive's ESP - efi system partition.
So specifing sda1 instead of sda, should not make any difference.
In BIOS mode, installing to a FAT32 or NTFS partition damages Windows. 
So best to never install to a partition.

Have you run the Boot-Repair summary report?

---

### Post by aeb105 on 2018-09-12
Here is the summary on pastebin:


[http://paste.ubuntu.com/p/5pBRhnHKBN/](http://paste.ubuntu.com/p/5pBRhnHKBN/)

---

### Post by oldfred on 2018-09-12
Are you sure you are booting in UEFI mode?
Many HP will not boot the ubuntu entry, will then try BIOS/CSM/Legacy mode and then fail. But since you have grub installed for BIOS boot, it may be trying to BIOS boot system even if you think you are booting in UEFI mode. And BIOS version of grub you have installed will give the error you are getting.

I might try this as one of the several work arounds for HP. And then try booting "Windows" boot entry.
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

HP violates UEFI standard which says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager".

Most HP also boot the fallback/hard drive entry which uses /EFI/Boot/bootx64.efi. That is the same path & filename used for all external drives. But I do not see an UEFI hard drive entry in your list of boot options. Boot-Repair copies shimx64.efi to bootx64.efi to have that option if available.

Also some with HP have ubuntu now working it seems. Have you updated UEFI? That may be a fix also.

---

### Post by aeb105 on 2018-09-12
If I could upload a picture, I would show you UEFI options and the ubuntu one I select.  I had accidentally erased the Windows partition a while back so there is no option for that.

---

### Post by oldfred on 2018-09-12
But UEFI or BIOS go thru boot options in order. If first selection does not work it tries the next.

Your pastebin shows the UEFI boot options, just with more detail. You just see the names.
but if that option does not work it tries the next & next until it gives up.
And typically after UEFI, then it tries BIOS as last resort. And since you have a grub boot loader as BIOS boot, it tries that. And grub starts but is not correctly configured for BIOS boot.

You can install the grub/shim boot loader with Windows description as posted above. And boot "Windows Boot Manager" which will really boot Ubuntu.

Another alternative is to boot Boot-Repair in BIOS and convert install to BIOS boot by installing grub-pc. Then grub in MBR for BIOS boot will work.

---

### Post by aeb105 on 2018-09-13
I deleted the windows partition.  How do I do what you are saying with Windows?

---

### Post by oldfred on 2018-09-13
See post # 13 above. 

In live installer copy that command to create a Windows boot entry that really boots Ubuntu.
Then see if you can boot the Windows entry.

---

### Post by aeb105 on 2018-09-14
I lost the system recovery cd.  Is that what you say I need?  Or the Linux Boot Repair?

---

### Post by oldfred on 2018-09-14
From Ubuntu live installer in live mode, run the posted efibootmgr command.

---

### Post by aeb105 on 2018-09-16
You mean boot the Ubuntu Studio all the way up to live and at the desktop issue a command?

---

### Post by oldfred on 2018-09-16
Boot live installer in live mode, and use terminal to copy & paste command into terminal.

---

### Post by aeb105 on 2018-09-17
When you say Live Installer do you mean the Boot Repair disk or my Ubuntu Studio distro?

---

### Post by oldfred on 2018-09-17
I typically do not recommend using Boot-Repair's ISO as a live system.
Use your Ubuntu installer in live mode and add Boot-Repair to it using the ppa. Details on the two or three lines you have to copy are on the Boot-Repair site.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by aeb105 on 2018-09-18
So I will need to drill down to SDA1 then I guess.

---

