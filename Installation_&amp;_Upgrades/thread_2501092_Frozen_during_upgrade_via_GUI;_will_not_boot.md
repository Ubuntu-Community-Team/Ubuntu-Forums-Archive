---
title: "Frozen during upgrade via GUI; will not boot"
date: 2024-09-22
forum: Installation &amp; Upgrades
---

### Post by wsmin on 2024-09-22
I will preface this saying I'm not new to Ubuntu (using since '15 on the same HP laptop), but I am also not fluent with Ubuntu.  I use it as an alternative to the expense of Windows.  I'm also not even 50% sure of what version I was currently using when attempting to upgrade (pastebin shows 22.04), and I can only assume that upgrade was to 24.04....I was prompted ~ 09/10/24 to update.  I know that's extremely vague, but I'm hoping that along with the pastebin that will provide enough information for suggestion from more experienced users.

Approximately 1/4 to 1/3 of the way through the upgrade, the installation froze.  I was unable to launch any applications, however the GUI was still "functional".  I waited 24 hours, but the installation remained at the same point.  This is where I should've sought advice, but I forced a shutdown/reboot via power button.  CL showed multiple daemon service failures for Power Profiles and Thermal.  The last messages were:
[INDENT][FAILED] Failed to start Power Profiles daemon
[    OK   ] Stopped Thermal Daemon Service
[FAILED] Failed to start Thermal Daemon Service
[   OK    ] Finished GRUB failed boot detection
[   OK    ] Finished resolvconf-pull-resolved.service
[   OK    ] Finished Secure Boot updates for DB and DBX
[/INDENT]

After some research here, I acquired another laptop to create a Boot-Repair-Disk and here I am. The suggestion on the documentation was to share the pastebin with the boot issue description for advice here before proceeding with "Recommended Repair".  I yield to the community for suggestions. I would obviously like to repair and retain the data on my HD, either completing this installation or reverting to the old version.  Thank you.

[https://paste.ubuntu.com/p/z6F3h4Fvjr/](https://paste.ubuntu.com/p/z6F3h4Fvjr/)

---

### Post by grahammechanical on 2024-09-22
I am assuming that you only have Ubuntu on that machine. So, you will not see the Grub boot menu. Is the motherboard BIOS or UEFI? 

To bring up the Grub boot menu on a BIOS motherboard press the SHIFT key as the machine's splash screen loads.

To bring up the Grub boot menu on a UEFI motherboard press the ESC key (perhaps repeatedly) as the machine's splash screen loads.

When you get to the Grub menu select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. The machine should load Linux and show a recovery menu.

Select Network to set up an internet connection. When back at the recovery menu select Root shell prompt. Then run

```
apt update
```

followed by

```
apt upgrade
```

Make a note of any error messages. The hope is that the update/upgrade will complete the online upgrade to the next Ubuntu LTS version that was interrupted. Further commands might be necessary. When finished type exit to get back to the recovery menu and then select Resume. Hopefully Ubuntu will load to the login screen and a desktop environment using an open source video driver. If Ubuntu is now usable you may be able to run more commands to fix things. You could try rebooting. That should load Ubuntu with your normal video driver (proprietary).

You may wish to disable any proprietary video driver using Software & Updates>Additional drivers tab. I am of the opinion that before doing an online upgrade proprietary video drivers should be disabled especially Nvidia drivers as Nvidia usually drops support for its video drivers over time.

Regards

---

### Post by wsmin on 2024-09-23
Yes, Ubuntu is the only OS on the device.  As far as BIOS or EFI...I don't know, but I assume BIOS because...  According to your instructions, holding (either) SHIFT key during boot does nothing.  Repeatedly pressing ESC during boot gets me to the system BIOS.  Exiting from BIOS gets me to the grub> prompt.  However, the pastebin shows the following, so I'm led to believe it is EFI:

The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

From the prompt I do not know how to get to the GRUB menu, but I assume that's not possible with the following message in the pastebin:

 => No boot loader is installed in the MBR of /dev/sda.

---

### Post by tea for one on 2024-09-23
After a frozen upgrade and a forced shutdown, the first priority is to backup your personal data.
Also, you may have damaged filesystems and fsck (file system check) may be necessary.
> **wsmin said:**
> Repeatedly pressing ESC during boot gets me to the system BIOS.  Exiting from BIOS gets me to the grub> prompt.
```
grub>[COLOR="#0000FF"]normal[/COLOR] #hit enter key
```
or
```
grub>[COLOR="#0000FF"]exit[/COLOR] #hit enter key
```
Anything transpire?
```
No boot loader is installed in the MBR of /dev/sda
```
This is correct for UEFI systems
You have boot files in your ESP (sda1) - see lines 7 to 15 of the boot-repair report.

---

### Post by wsmin on 2024-09-23
I am unable to run fsck from the grub> prompt.  Upon research it appears that needs to be done when I boot Live.  
Should I attempt the following process to check the filesystem, or proceed with the "recommended Repair" on the Boot-Repair?

"For 18.04 or newer... you MUST do it this way...  
[LIST]
[*]boot to a Ubuntu Live DVD/USB
[*]open a terminal window by pressing Ctrl+Alt+T
[*]type sudo fdisk -l
[*]identify the /dev/sdXX device name for your "Linux Filesystem"
[*]type sudo fsck -f /dev/sdXX, replacing sdXX with the number you found earlier
[*]repeat the fsck command if there were errors
[*]type reboot
[/LIST]
     
"
_____________

At the grub> prompt, both 'exit' and 'normal' end in the same results:

common_interrupt: 1.55 No irq handler for vector
common_interrupt: 2.55 " "
common_interrupt: 3.55 " "
/dev/sda2: clean..........
/usr/lib/systemd/system-generators/netplan failed with exit status 127


idles for a few minutes, then attempts booting GUI, wherein I hit ESC to show the long list of originally posted [FAILED] and [     OK     ] messages

---

### Post by tea for one on 2024-09-23
I did not expect you to try and run fsck from the grub prompt.
File system check has to be run on unmounted partitions, usually during a live session

Please confirm that you have backed up your data?.

---

### Post by wsmin on 2024-09-23
This is where my lack of Ubuntu knowledge comes into play.  I did not know an fsck can only be run on an unmounted partition.

How would I go about backing up data at this point, or were you asking if I have a recent backup prior to this "crash" occurring?  And that would be a 'no'.

---

### Post by oldfred on 2024-09-23
You have UEFI.
Because, no boot loader in MBR (used for BIOS boot), you have an ESP - efi system partition (used for UEFI boot) and you have ESP mounted in fstab, see line 156.

But you booted live installer in old BIOS boot mode.
How you boot live installer, is then how it installs or repairs.
Only boot in UEFI mode. That should be a choice as you use one time boot key in UEFI to choose boot mode. One should clearly be UEFI.

You seem to be using Mint for repairs, line 47? That is not an official flavor of Ubuntu.

Do you have latest UEFI firmware? Line 51 and compare to latest version available on vendors support site for your model system.

What model HP?
Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings
Escape key just after HP logo, but before grub menu normally appears should get you to grub menu. Timing can be an issue.
If UEFI fast boot on, you may not have time to press a key. Make sure UEFI fast boot is off when making system changes. Or "cold" boot from full power down.

---

### Post by tea for one on 2024-09-23
> **wsmin said:**
> How would I go about backing up data [COLOR="#0000FF"]at this point[/COLOR], or were you asking if I have a recent backup prior to this "crash" occurring?  And that would be a 'no'.
Boot into a &#8220;Try Ubuntu&#8221; session
Open the file manager
Attach a formatted external device to store your backup
Mount the partition(s) where your data resides
Copy and paste the important files/folders to the external location
When finished, safely remove the backup device.

There is a wealth of backup suggestions in these forums and throughout the internet.
Perhaps, start here [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by wsmin on 2024-09-23
> **oldfred said:**
> 
Only boot in UEFI mode. That should be a choice as you use one time boot key in UEFI to choose boot mode. One should clearly be UEFI.

Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI  boot menu, <kbd>F10</kbd> for UEFI/bios settings
Escape key just after HP logo, but before grub menu normally appears should get you to grub menu. Timing can be an issue.
If UEFI fast boot on, you may not have time to press a key. Make sure  UEFI fast boot is off when making system changes. Or "cold" boot from  full power down.

When pressing ESC during bootup, that brings up Startup Menu:

      "F1  System Info
      F2   System Diag
      F9   Boot Drive Options
      F10 BIOS Setup
      F11 System Recovery
      "

F9 options are as follows:

      "USB Hard Drive (UEFI) - KingstonDataTraveler
      ubuntu (Hitachi HTSxxxxxxxxxxxx)
      Ubuntu (Hitachi HTSxxxxxxxxxxxxx)
      Boot From EFI File
      USB Hard Drive - KingstonDataTraveler
      Notebook Hard Drive

      F10 for BIOS
"

In BIOS, the Boot Order is:

      "UEFI Boot Order
      Internal CD/DVD ROM Drive
      USB Diskette on Key/USB Hard Drive
      OS boot Manager
      USB CD/DVD ROM Drive
      ! Network Adapter

      Legacy Boot Order
      Internal CD/DVD ROM Drive
      USB Diskette on Key/USB Hard Drive
      Notebook Hard Drive
      USB CD/DVD ROM Drive
      ! Network Adapter
      "

I do not see an option for UEFI fast boot.

> **oldfred said:**
> 
You seem to be using Mint for repairs, line 47? That is not an official flavor of Ubuntu.

I initially tried researching a solution which led me to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
The "1st Option" link led to [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/) , which is the Mint I downloaded and created a Boot-Repair USB.

> **oldfred said:**
> 
Do you have latest UEFI firmware? Line 51 and compare to latest version available on vendors support site for your model system.

Line 51 shows F.21.  Latest firmware on HP shows F.19, but that is only for Windows; Linux redirects to Kernal archives but that is completely foreign to me.

> **oldfred said:**
> What model HP?

Envy M6, born 05/15/2013

---

### Post by wsmin on 2024-09-23
> **tea for one said:**
> Boot into a “Try Ubuntu” session

I assume in order to do this that I would need to download an ISO of the current version that crashed, or the version it was upgrading to, and create a boot USB?  I do not have 100% certainty on whether or not 22.04.4 was my current version or the failed upgrade based on line 41 of the pastebin.

---

### Post by oldfred on 2024-09-23
UEFI settings are where fast startup setting will be, not UEFI one time boot key.
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

UEFI firmware, is not specific to Windows or Linux.
But Linux may need different settings than default or those used by Windows. 

Because this is now older, not sure if these settings still required. Both UEFI & Linux kernel & drivers are regularly updated, so boot parameters may not be required.

HP Envy m6-p113dx with AMD FX-8800P Radeon R7 Multiple boot parameters
pci=noearly acpi_no_static_ssdt acpi_sleep=nonvs amd_immu=force_isolation
[https://ubuntuforums.org/showthread.php?t=2448727](https://ubuntuforums.org/showthread.php?t=2448727)
[https://forums.linuxmint.com/viewtopic.php?t=268675](https://forums.linuxmint.com/viewtopic.php?t=268675)
HP UEFI menus New UEFI 
[https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237](https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237)
HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)



Your post #10 shows UEFI boot options.

---

### Post by deadflowr on 2024-09-23
> **wsmin said:**
> I assume in order to do this that I would need to download an ISO of the current version that crashed, or the version it was upgrading to, and create a boot USB?  I do not have 100% certainty on whether or not 22.04.4 was my current version or the failed upgrade based on line 41 of the pastebin.

No.
For what is suggested any ole live session (Try Ubuntu option) will work.
It helps to have the version you want to install, but if only using it to get the files for backup it doesn't matter.
Can even be a very old end-of-life live session.

---

### Post by yancek on 2024-09-23
In post 10, you show two separate boot options for Ubuntu under the one boot option with F9 as well as the Boot from EFI file option.  Have you tried all 3 options with the same result?
In that same post,  you show UEFI Boot Order which includes  OS boot Manager.  If you arrow down to OS boot Manager and highlight it and hit Enter, do you see boot options for Ubuntu?  You should.

---

### Post by wsmin on 2024-09-23
> **oldfred said:**
> UEFI settings are where fast startup setting will be, not UEFI one time boot key.
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

UEFI firmware, is not specific to Windows or Linux.
But Linux may need different settings than default or those used by Windows. 

Because this is now older, not sure if these settings still required. Both UEFI & Linux kernel & drivers are regularly updated, so boot parameters may not be required.

HP Envy m6-p113dx with AMD FX-8800P Radeon R7 Multiple boot parameters
pci=noearly acpi_no_static_ssdt acpi_sleep=nonvs amd_immu=force_isolation
[https://ubuntuforums.org/showthread.php?t=2448727](https://ubuntuforums.org/showthread.php?t=2448727)
[https://forums.linuxmint.com/viewtopic.php?t=268675](https://forums.linuxmint.com/viewtopic.php?t=268675)
HP UEFI menus New UEFI 
[https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237](https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237)
HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)


Your post #10 shows UEFI boot options.

So ESC, F9 gets me to the options.  
There I select 'USB Hard Drive (UEFI) - KingstonDataTraveler'
That brings me to:

"* start boot-repair-disk 64-bit
* start boot-repair-disk 64-bit (compatibility mode)
* UEFI firmware settings
"

Selecting the firmware settings brings me to a 'GNU Grub 2.06' displaying the following:

"setparams 'UEFI Firmware Settings'[INDENT]fwsetup
[/INDENT]
 "
At the bottom of this screen is:

"enter to boot selected OS, 'e' to edit commands before boot, or 'c' for command line
"
Do I add to this?  Do I delete everything an add the ' pci=noearly acpi_no_static_ssdt acpi_sleep=nonvs amd_immu=force_isolation' ?
After a period of a couple minutes with no input from me, the laptop powers off.
Forgive the lack of understanding by me, but I want to be sure I'm doing the correct thing (unlike when I tried to fsck a mounted drive earlier!)

---

### Post by wsmin on 2024-09-23
> **deadflowr said:**
> No.
For what is suggested any ole live session (Try Ubuntu option) will work.
It helps to have the version you want to install, but if only using it to get the files for backup it doesn't matter.
Can even be a very old end-of-life live session.

Again, here's my lack of knowledge with Ubuntu... but the Try Ubuntu option/ole live session...the Boot-Repair USB (my Kingston drive) doesn't have that option.  I don't have any version of Ubuntu on a CD or USB.  A coworker originally installed it via USB back in 2015. Do I need to delete the Boot-Repair (Mint) from my USB stick and download an actual Ubuntu version?

---

### Post by wsmin on 2024-09-23
> **yancek said:**
> In post 10, you show two separate boot options for Ubuntu under the one boot option with F9 as well as the Boot from EFI file option.  Have you tried all 3 options with the same result?
In that same post,  you show UEFI Boot Order which includes  OS boot Manager.  If you arrow down to OS boot Manager and highlight it and hit Enter, do you see boot options for Ubuntu?  You should.

The two ubuntu/Ubuntu options both result in the long list showing [FAILED] / [    OK    ] / [DEPEND] daemons, etc.

The Boot from EFI file flashes a quick screen with what appeared 3 lines of text, then the laptop shut down and won't let me power it back on.  I've unplugged it and will wait overnight to try again in the a.m.

The OS Boot Manager in the BIOS settings has no options when hitting Enter when it is selected.  I was under the impression that there would be if this was a dual boot system, but I'm only running Ubuntu.... but I'm likely wrong thinking that.  Regardless, no options for that.

---

### Post by oldfred on 2024-09-23
You seem to have downloaded the Boot-Repair ISO, which I did not recommend.
It is limited to running Boot-Repair and often is older as not updated as frequently as the ppa.

You want to download the Ubuntu live installer and per the Boot-Repair link add the ppa to download Boot-Repair into the live installer.
You want to boot live installer in UEFI mode from UEFI one time boot menu choices.

I would only experiment with optional boot parameters after fully testing with live installer and having issues.

---

### Post by wsmin on 2024-09-24
Ok, I downloaded 22.04 and booted live to it from the USB via "Try Ubuntu".  I'm able to see my files (some with a red circle/white X which I assume means corrupt) and I'm in the process of transferring them to an external drive.

I understand the concept of the ppa, but I'm completely in the dark on the syntax of it.  I looked over [https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en), but is it just the URL for the Boot-Repair I add, like so?...


[https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

### Post by oldfred on 2024-09-24
To run ppa, all you have to do is copy the commands shown in option two for ppa.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[FONT=monospace]
Generally a new user should not install from ppa unless known as a trusted site.
[/FONT]

---

