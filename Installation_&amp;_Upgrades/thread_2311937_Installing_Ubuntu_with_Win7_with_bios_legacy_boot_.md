---
title: "Installing Ubuntu with Win7 with bios legacy boot - starting to despair..."
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by Thomas_Voigt on 2016-01-31
Hi,

I wanted to create my first Ubuntu installation (well, modern installation, I used Ubuntu a few years ago) and failed miserably. I use an Acer Travelmate P253E which has a Windows 7 installed and boots in BIOS legacy mode. I tried switching to UEFI, but then the BIOS would just hang and I had to do an emergency BIOS flash to get it running again. So UEFI is not an option. But I can't get Ubuntu to boot after installation. 

What I did:
1. Shrank Windows partition and installed Ubuntu from the live CD.
2. After Ubuntu didn't start, I ran Boot-repair ([http://paste.ubuntu.com/14748557/](http://paste.ubuntu.com/14748557/)). No help.
3. Switched BIOS to UEFI. First time it worked - I could boot Ubuntu, but not Windows anymore. (No surprise there.) Ubuntu was running fine.
4. Switched back to legacy boot. Ran boot repair again. Nothing.
5. I read that I have to create a boot partition that is the first on the drive. Booted from gparted CD, but couldn't resize the Windows partition because it claimed that NTFS drivers are not loaded.
6. Booted the Ubuntu live CD, run gparted from there, got the same message. Tried to install the missing ntfs drivers, just to get the information that they were already installed.
7. Switched back to UEFI, and figured I could repair Windows to boot from UEFI. This time, the laptop would not boot anymore and I had to flash the bios from an USB stick via emergeny flash. 
8. Almost threw the laptop out of the window.

 There seem to be plenty of guides around how to install Ubuntu with UEFI, but no guide how to install it in legacy mode - or rather, how to fix grub that it can boot the already installed Ubuntu.

So, any help would be appreciated.

Regards, Thomas

---

### Post by oldfred on 2016-01-31
Why did you think your Windows booted in BIOS/CSM/Legacy mode? It is installed in UEFI boot mode.
And Ubuntu is installed in UEFI boot mode.

With Windows 7 you do not use Secure Boot as only Windows 8 or later support that. Some UEFI have settings for "Windows" and "other" but that really is secure boot, and you would want other.

Install looks normal for UEFI boot of both Windows & Ubuntu. Can from one time boot key, like f10 or f12 (check manual for correct key) choose Windows or Ubuntu?
Have you updated UEFI/BIOS from Acer? That will also reset to defaults and you will have to change your settings in UEFI to correct settings again.

Acer with Windows 8 have to create a supervisor password, and enable trust on efi boot files. 
Not sure if required with your system or not?
       Very latest UEFI/BIOS works, downgrade not required:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
[/URL]
 Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post1334175]("http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757")  [ ]("http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141")

---

### Post by Thomas_Voigt on 2016-01-31
No, Windows is installed in legacy mode and will not boot in UEFI mode.

There is no boot menu that allows me to boot Ubuntu.

---

### Post by oldfred on 2016-01-31
[FONT=arial]If that is the correct pastebin, then you have UEFI, not BIOS.[/FONT][FONT=arial]

For BIOS boot you have to have a boot loader in the MBR.
> No boot loader is installed in the MBR of /dev/sda. [/FONT]And Windows only boots in UEFI boot mode from gpt(GUID) partitioned drives.
> GUID Partition Table detected.



You need to have UEFI on, and secure boot off. And may need "Trust" settings on UEFI boot files.

---

### Post by Thomas_Voigt on 2016-01-31
It's possible this is from the run after turning on UEFI.

I won't do it again, because it was quite some procedure to burn this BIOS, and I'm not going to do it a second time. Also Windows didn't start in UEFI.
UEFI is not an option.

---

### Post by Thomas_Voigt on 2016-01-31
> **Thomas_Voigt said:**
> It's possible this is from the run after turning on UEFI.



Ran bootinfo again: [http://paste.ubuntu.com/14837615/](http://paste.ubuntu.com/14837615/)

---

### Post by yancek on 2016-01-31
Your most recent boot repair output from post #7 shows that you have no boot code in the Master boot record.  In order to boot without that code, you need to use UEFI.  You show an EFI partition on sda1, the first partition with the efi files needed for both windows and Ubuntu.   The output clearly shows you are using GPT partitioning so as pointed out above, you must install windows UEFI.  Have you tried the suggestion at the bottom of the boot repair output?   If you had windows installed using MBR rather than UEFI/GPT then it would have been necessary to install Ubuntu MBR also.

---

### Post by Thomas_Voigt on 2016-01-31
The computer never was in UEFI mode when Windows was installed, and I installed Ubuntu in legacy mode too. I switched to UEFI after the boot problems occured and I realized that for some reason Ubuntu had installed an UEFI loader.

I thought I made clear that I need pointers how to install Ubuntu in legacy mode, using the MBR or whatever. I really don't get why you keep telling me I have to switch to UEFI if I had a 0% success rate on 2 attempts, once Windows not booting and once a frozen BIOS that would not even allow me to enter setup. 

But I guess I'll just forget about finally giving Windows the boot. The laptop is for my mother, who sometimes clicks on email attachments that she really shouldn't click on, so I thought I'd finally convince her to learn something new. But you know, installing Linux 20 years ago was easier than installing Ubuntu now, because I actually knew back then which configuration files to edit. Now we're so friggn user friendly that we don't allow the user to make the necessary choices, and just install in UEFI mode no matter what. Jeez.

---

### Post by oldfred on 2016-01-31
You have to totally erase drive and convert from gpt to MBR if you want Windows in BIOS boot mode.
Windows only boots from gpt with UEFI.
Windows only boots from MBR with BIOS.
Ubuntu can boot in either BIOS or UEFI from gpt partitioned drives.
But for UEFI boot (which you have) you must have an ESP - efi system partition which is normally shared by Windows & Ubuntu.
Or from gpt only booting Ubuntu in BIOS mode you must have a 1MB unformatted partition with the bios_grub flag. But better to keep UEFI as Windows is UEFI.

If you have issues with Windows you may need to make Windows repairs. Chkdsk or other repairs from Windows repair console.
You should be able to boot Ubuntu but may have to go into UEFI, set password, and enable trust on Ubuntu/grub's efi boot files in the ESP as posted above.

Did you update UEFI from Acer?

---

### Post by yancek on 2016-01-31
>  really don't get why you keep telling me I have to switch to UEFI if I  had a 0% success rate on 2 attempts, once Windows not booting and once a  frozen BIOS that would not even allow me to enter setup. 

Nobody is telling you that you have to or should install UEFI.  You already did that which is what the boot repair script states explicitly.  The steps you need to take now are in the post above by oldfred.

---

### Post by Thomas_Voigt on 2016-02-01
Yeah, I must have dreamed installing Windows in legacy BIOS mode a few years ago, and then explicitly deciding against going to UEFI before installing Ubuntu.
But of course you all know better what I did.  I can see that I will get no help here. Bye bye.

---

