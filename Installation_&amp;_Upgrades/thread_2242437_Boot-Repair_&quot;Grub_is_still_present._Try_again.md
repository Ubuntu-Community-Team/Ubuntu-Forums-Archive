---
title: "Boot-Repair &quot;Grub is still present. Try again.&quot;"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by guilhermebdias on 2014-09-01
Hi guys,
I just installed Ubuntu to an HD that already featured Windows 7 (in different partitions). When I restarted the computer no GRUB menu was shown and the system booted with Windows 7 withou asking.
So I ran boot-repair. After a while it asked for me to run the following commands:
```
sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub* shim-signed
```
but I get the message: > zsh: no matches found: grub*
If I select "forward" in the boot repair app it says > GRUB is still present. Please try again.
Here is the log (?) [http://paste.ubuntu.com/8210531/](http://paste.ubuntu.com/8210531/)
.
Any help would be wellcomed
ps. I know very little of Linux, but am willing to learn o/

---

### Post by grahammechanical on 2014-09-01
Did you see this?

>  [COLOR=#000000] Windows 7/8/2012 is installed in the MBR of /dev/sda. [/COLOR]

The Windows manager will not recognise a Linux OS.

Did you also see this?

> [COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to fix packages[COLOR=#666666])[/COLOR] and reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

Try running boot repair again and agree to the request from Boot Repair to make the recommended repair.

When you installed Ubuntu did you allow the installer to install Grub into the MBR of sda? Or did you prevent that from happening? The Ubuntu installer by default installs Grub into sda unless we tell it otherwise. Whatever happened, Grub did not get installed into the MBR of sda.

Regards.

---

### Post by guilhermebdias on 2014-09-01
Hey [COLOR=#000000]grahammechanical, thanks for the quick reply.

The boot-repair routine is automatic and I didn't deliberate on any action from it. This log file I submitted was generated with a specific option in the Boot-Repair tool. I only did this after I tried to run[/COLOR][COLOR=#000000] the Boot-Repair many times making no alterations to its recommended actions.[/COLOR][COLOR=#000000] And that's why the user chosen settings show "BootInfo". As I told above in the thread, Boot-Repair is returning error messages:
[/COLOR]> [COLOR=#000000][I]zsh: no matches found: grub*
and
[/I][/COLOR][COLOR=#000000]*GRUB is still present. Please try again.*[/COLOR]
[COLOR=#000000]But indeed I must have installed the bootloader in the wrong device (dev/sdb).[/COLOR]
[COLOR=#000000]Is there any way to repair that without removing and installing the Ubuntu again?[/COLOR]

---

### Post by fantab on 2014-09-02
>  UEFI/Legacy mode:
BIOS is EFI-compatible, and **is setup in EFI-mode for this live-session**.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])

This happens because you have UEFI booting enabled in your UEFI/BIOS menu.

```
parted -l:

Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
[B]Partition Table: msdos
[/B]
Number  Start   End    Size    Type      File system     Flags
1      1049kB  106MB  105MB   primary   ntfs            boot
2      106MB   157GB  157GB   primary   ntfs
3      157GB   360GB  202GB   primary   ntfs
4      360GB   500GB  141GB   extended
5      360GB   372GB  12.6GB  logical   ext4
6      372GB   381GB  8808MB  logical   linux-swap(v1)
7      381GB   500GB  119GB   logical   ext4
```

The above code tells us that the HDD is 'msdos', ie it boots from MBR and not EFI. Hence your booting issue.
UEFI boot is not possible from 'msdos' disk, we'd need a GPT disk for that.
You have to disable UEFI boot from UEFI/BIOS menu and enable 'legacy/csm' boot.

---

### Post by guilhermebdias on 2014-09-02
Hi fantab,

I couldn't change the UEFI to legacy mode because there is no such option in the Asus UEFI BIOS utility (EZ or Advanced menu). I can only change boot priority (HD, CDR and UEFI-USB, which is the LiveUSB from which I installed Ubuntu).
Is there a way to manually boot to Ubuntu? (the one installed in my HD and not in the LiveUSB).
Because perhaps running Boot-Repair from my HD would fix the GRUB problem...

What do you think?

---

### Post by fantab on 2014-09-02
If your UEFI menu looks anything like [this]("http://www.extremetech.com/wp-content/uploads/2011/09/ASUS-EFI-01.jpg"), then look at the boot priority... there are two HDD images, one with 'uefi' and the other without it... 
if my guess is right then you will have to choose the HDD without uefi to be able to enable 'legacy boot'.

That option will be there, if its not as described in the above screenshot... it will be elsewere keep looking.
It is impossible to boot Windows from a MBR disk in UEFI setup. Something must have changed the setting...

This is a UEFI related issue and Boot-Repair won't help.

---

### Post by guilhermebdias on 2014-09-02
[ATTACH=CONFIG]256077[/ATTACH]
This is what my EFI menu looks like. My HD is not UEFI enabled, and both Windows 7 and Ubuntu 12.04 are installed in it (in different partitions).
I just want to be able to choose between the two OSs when I boot. Right now Windows 7 boots automatically and I don't even know how to access Ubuntu.
(The LiveUSB I used to install Ubuntu appear as UEFI device if connected, but I don't want to boot Ubuntu from it. I want to boot from the installed copy in my HD)
.
I feel this is a rather simple matter and I'm just messing things up =p

---

### Post by fantab on 2014-09-02
Something in there is confusing the Ubuntu usb to boot in efi mode, when it should boot in 'legacy mode'. Keep looking, what's in the F8 and 'default' menu, from your screenshot. 
See the difference [**Here**]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") between Ubuntu USB/DVD booting in EFI and Legacy modes... make sure your Ubuntu usb is booting in 'legacy' or 'non-UEFI' mode.

Lets use [fixparts]("http://www.rodsbooks.com/fixparts/") and see if there is any stray GPT data on the HDD which may confuse the ubuntu usb.
```
sudo fixparts /dev/sda
``` and post the output here.

---

### Post by guilhermebdias on 2014-09-02
> **fantab said:**
> Something in there is confusing the Ubuntu usb to boot in efi mode, when it should boot in 'legacy mode'. Keep looking, what's in the F8 and 'default' menu, from your screenshot. 
See the difference [**Here**]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") between Ubuntu USB/DVD booting in EFI and Legacy modes... make sure your Ubuntu usb is booting in 'legacy' or 'non-UEFI' mode.

Lets use [fixparts]("http://www.rodsbooks.com/fixparts/") and see if there is any stray GPT data on the HDD which may confuse the ubuntu usb.
```
sudo fixparts /dev/sda
``` and post the output here.

Actually I don't want to boot from the USB. I want to boot from my HDD.
Is that what you're trying to help me achieve?

---

### Post by fantab on 2014-09-02
Ubuntu install DVD/USB can boot in both UEFI and Legacy mode. If it sees EFI then it will boot in UEFI mode and if not it should boot in legacy mode.
So when you boot your usb/dvd to install ubuntu its booting in Uefi mode, and this is the reason why it wants to install 'grub-efi' when it should be installing simple 'grub-pc' for legacy machines.
The same thing is probably confusing your HDD boot as well. Grub is looking for 'efi' files.

Yes, we are trying to make your PC boot from HDD in 'legacy' mode because your Windows install and your HDD is setup to boot in 'legacy/csm/MBR' mode.

---

### Post by guilhermebdias on 2014-09-03
Ok. So I installed the Fixparts tool and ran the code.
This is what it shows up
> 
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems in some OSes.

MBR command (? for help): 

---

### Post by guilhermebdias on 2014-09-03
And here it is the MBR partition table. (sorry for doubble posting)
[ATTACH=CONFIG]256090[/ATTACH]

The /dev/sda5 is where Ubuntu is installed.

---

### Post by fantab on 2014-09-04
That looks good, no great worry.
> The "0xEE partition doesn't start on sector  1" error is a bug in the version of FixParts that ships with Ubuntu.  Please add your voice to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gdisk/+bug/1281306")  to try to get it updated. Beyond that, using the "Something Else"  option is appropriate. Don't worry about GRUB at this point; the  algorithms GRUB uses to detect OSes are entirely unrelated to those used  by the installer to decide what installation options to show. The  installer has been doing a poor job of identifying candidates for  "install-alongside" type options recently.                 &#8211;                      [Rod Smith]("http://askubuntu.com/users/93977/rod-smith")                 

Keep looking in UEFI menu to enable 'legacy/csm' boot. I don't see any other issue.
use boot-repair to create a bootinfo summary and post back the url to the file here.

---

### Post by guilhermebdias on 2014-09-04
Hey guys, it finally worked!
I was looking for a switch to enable/disable UEFI boot mode. It happens that my Asus motherboard utility menu doesn't have such a button. Instead, it offers me two options in the boot menu (F8): SMI USB or UEFI USB boot modes (and no "legacy mode" :?, it must be SMI anyways).
Then I just cleaned the old partition and booted using the SMI USB option. I reinstalled Ubuntu alltogether and it worked smoothly. GRUB is up and running ;)
Thank you guys for all the help and patience with me. And I just learned a lesson: when s*** ain't working, think differetly and listen to the folks who know better.

Thanks!

---

### Post by fantab on 2014-09-04
> two options in the boot menu (F8): SMI USB or UEFI USB boot modes (and no "legacy mode"

Well, **SMI USB** is non-UEFI and in other words. 'legacy'. When you were booting in UEFI USB grub was looking for EFI system partition as couldn't find one and the the installer was booting in UEFI mode.

Glad you found the switch...

---

