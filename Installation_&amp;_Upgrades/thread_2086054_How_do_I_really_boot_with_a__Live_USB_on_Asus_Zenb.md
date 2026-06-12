---
title: "How do I really boot with a  Live USB on Asus Zenbook Prime UX31A (UEFI)"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by Linux on a Laptop on 2012-11-19
Hello,
I have been searching for an answer before posting this question that seems trivial.

I just bought an Asus Zenbook Prime UX31A-R4003P with Windows 8 Pro on it.
My aim is to install Ubuntu on it but so far I was not able to boot from a Live USB.

I  tried to boot with the ordinary ubuntu-12.10-desktop-i386 version and  soon found out that because the laptop was now using UEIF and not the  BIOS type I used to know.
So I followed the instruction found here:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and created a Live USB with  ubuntu-secure-remix-12.10-64bits.iso.

I managed to boot on the  USB on the UEIF mode by pressing ESC just after the laptop started. I  arrived on the the screen with the four options: Try, Install, OEM and  Check.
After pressing Enter with any of the options nothing happens. The screen stays blank (or black).
I tried the USB Key on another computer (BIOS type) and it worked fine.

Here is what I tried but still with no success:
- I changed '*quiet splash*' to '*nomodeset'* in the file *boot/grub/grub.cfg* on the USB drive.
- I used another USB drive
- I used ubuntu-12.10-desktop-amd64.iso.
-  I used ubuntu-12.04.1-desktop-amd64.iso. Here I got a red warning:  "Invalid signature detected. Check Secure Boot Policy in Setup"

If you have any more ideas to do the "simple" step 1: Boot Ubuntu from a Live USB, I would be glad to try it.

Thank you for any help.

Flash Type: Winbond 25X/Q Series
Current BIOS Platform: UX31A
Version: 214
Build Date: Aug 28 2012

Here is the other link I read:
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

---

### Post by oldfred on 2012-11-19
Because you have Windows 8, you also have secure boot. 12.10 should work with secure boot option still on. All the others would require you to turn it off.

Only the 12.10 with grub2 2.00 has the Ubuntu secure boot compatible installer. And you have to boot that in the UEFI mode not the BIOS/legacy/AHCI or whatever it may be called. Ubuntu 12.04 will get the new grub with the next point release in Jan.

So use ubuntu-12.10-desktop-amd64.iso to boot. But if you are getting blank screen you may also have the video issue. nomodeset should help but other boot option settings may also be required. What video card/Chip does you computer have.

I think this was Windows 7, but may have some hints for you, but not dual boot.
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

    Older still, and  newer version should work with less issuesl:
       efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

Another link with lots of technical details.
       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Some other boot options.
       
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Linux on a Laptop on 2012-11-20
Thank you for this detailed reply.
I have a lot of reading to do and testing.
I will keep you posted on, hopefully, what worked.
Have a nice day

---

### Post by zenbookquery on 2012-11-21
Similar problem! But it looks like I'm more noob than you as I have no idea what to do. And this is my very first time trying to install a Linux OS, so I'm very noob.
 
Computer is new Asus Zenbook UX31A-DH71 - 4GB DDR3 - 256GB SSD - Windows 8.
 
So far, I tried installing Ubuntu 12.10 thru two methods:
- Ubuntu 12.10 32bit/64bit installer via USB thumb drive - loaded thru pendrive
- Ubuntu 12.10 64bit via external USB Asus DVD drive - burned Ubuntu.com installer
 
Both the install DVD and the install USB thumb drive were burned/loaded from my friend's MacBook when he was in the room with me - not sure if that matters. I could try to re-load the USB stick/ re-burn a DVD using my Windows 8 OS if that will make a difference?
 
Both times (booting from USB drive and external DVD drive) I re-started while holding down F9 until I got the same four options: try, install, OEM and check. Both ways (~3 attempts each) I went with the TRY test drive to make sure Ubuntu would work on this machine. So far it hasn't.

The TRY test drive didn't work off of either the DVD or USB thumb drive. It just halted on a black screen for 5-10 minutes until I restarted the machine back into Windows, which made me nervous about choosing the install option since that would presumably wipe out the Windows OS. I want to get out of Windows 8 as fast as possible but don't feel comfortable committing to doing a full install if the test drive hasn't worked so far.
 
FWIW - Longtime Mac user, close to zero experience with running Windows commands; was hoping to install the 64bit Ubuntu OS on this 64bit Zenbook and totally wipe Windows 8 - don't see any reason to keep that thing around - just from using it temporarily to get rid of itself I'm very frustrated.
 
Would love to get Ubuntu working on this machine. If I can't I'll have to return it and go back to Mac, because I can't use Windows 8.
 
Help please!

---

### Post by oldfred on 2012-11-21
Again only the 64bit version of Ubuntu will work with UEFI computers.

It sounds like the Asus also has video issues. Often nomodeset or other settings will get you into a default video mode that will work. But depending on video chip used best quality may require proprietary drivers. Also some have dual video and need BIOS/UEFI setting for only one or the other to work with nomodeset.

And some of the very new computers like this need additional boot parameters assigned as part of the boot optins, see links above.

---

### Post by Linux on a Laptop on 2012-11-21
Hello,
To answer your question, the video is an Integrated Intel® HD Graphics  400.

Using the ubuntu-12.10-desktop-amd64.iso and the 
 ubuntu-secure-remix-12.10-64bits.iso on USB stike created from Ubuntu 12.10 32 bits on my current laptop.
I have tested a lot of boot options by editing before boot with 'e' then F10 (Ctrl+x does not work) and to be sure directly in the file /boot/grub/grub.cfg on the USB stike.

I press ESC to select on what I want to boot on and I see:
[I]Please select boot device:
* Windows Boot Manager (PO: SanDisk SSD U100 252GB)
* UEFI: VerbatimSTORE N GO 1.00[/I]
When selecting Verbatim I guess the boot is in UEFI mode.

Before modifying we have:
[I]menuentry "Try Ubuntu without installing" {
        set gfxpayload=keep
        linux   /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet nosplash acpi_osi=Linux --
        initrd  /casper/initrd.lz
}[/I]

Here is what I tested:
* [I]quiet splash nomodeset -- 
[/I]* [I]quiet splash nomodeset acpi_osi= --
[/I]* [I]quiet splash nomodeset acpi_osi=Linux --
[/I]* [I]quiet splash vt.handoff=7 rootdelay=90 reboot=a,w --
[/I]* *quiet splash -- vga=771*
and some times with *nosplash* or without *quiet splash*

I still the blank screen.

While on the Blank screen I tested this with no success:
* Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
* Generally pressing and holding Ctrl+Alt and then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring) should do a clean reboot.

And before trying to boot I went to the Grub shell:
* GRUB> echo $linux_gfx_mode
* GRUB> echo $gfxmode
Gave me no answer 
* GRUB> vbeinfo
Gave me an error.

I'm open to new ideas.

I don't know if it's my English and/or my linux/computer knowledge that stops me from going forward...

Thanks for your time oldfred. I saw your replies on those posts.

---

### Post by oldfred on 2012-11-21
It was my understanding that the Intel 4000 just worked. Does your system have dual video and you have to turn one off in BIOS/UEFI?

I think this is now older but you can try it. I would also leave off quiet splash just to see if any lines are posted while starting to boot. Perhaps some other device is also causing issues.
       if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot


       
 Intel i5, uninstall nVidia from old drive and convert to Intel driver.
[http://ubuntuforums.org/showthread.php?t=2064695](http://ubuntuforums.org/showthread.php?t=2064695)

    
Someone also posted this as good options:
       Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by Linux on a Laptop on 2012-11-21
I didn't found in the BIOS/UEFI where I counld Enable/Disable a Dual Screen I modified some options and went back to the Try/Install/OEM/Check choices I realized their was an error message that was shown in just a flash (very fast) before the Try/Install/OEM/Check choices. So I booted several time to catch some words.

The solution to the blank screen is the Disable the Secure Boot Control.
The answer is that simple!!

I'm going to have a good night sleep and try to install Ubuntu tomorrow and I might come back with other issues as I see that the Asus Zeebook Prime UX31A has a lot of painful staff to go through.

Thank you oldfred and have a nice day.

PS: How do I put Solved on the thread?

---

### Post by oldfred on 2012-11-21
Some have posted that Ubuntu & Windows both work with or without secure boot. But it must depend on vendors implementation.

See my signature.

---

### Post by phly95 on 2013-01-12
You could try the Wubi installer, which is completely automatic.

---

### Post by tariqsheikh on 2013-04-20
> **Linux on a Laptop said:**
> I didn't found in the BIOS/UEFI where I counld Enable/Disable a Dual Screen I modified some options and went back to the Try/Install/OEM/Check choices I realized their was an error message that was shown in just a flash (very fast) before the Try/Install/OEM/Check choices. So I booted several time to catch some words.

The solution to the blank screen is the Disable the Secure Boot Control.
The answer is that simple!!

I'm going to have a good night sleep and try to install Ubuntu tomorrow and I might come back with other issues as I see that the Asus Zeebook Prime UX31A has a lot of painful staff to go through.

Thank you oldfred and have a nice day.

PS: How do I put Solved on the thread?


Asus F201E here. Had the same problem, and your answer saved my life! Thanks a lot!

---

### Post by Pander on 2013-06-29
Does [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current) work? Please let me know.

---

### Post by oldfred on 2013-06-29
@Pander
Please do not post same question in mulitple threads. We all are volunteers and need to see other responses and do not want to duplicate effort.
[http://ubuntuforums.org/showthread.php?t=2149954&p=12710967#post12710967](http://ubuntuforums.org/showthread.php?t=2149954&p=12710967#post12710967)

---

