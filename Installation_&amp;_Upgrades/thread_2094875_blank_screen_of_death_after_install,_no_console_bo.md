---
title: "blank screen of death after install, no console boot"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by RAMSESray on 2012-12-15
tl;dr New Asus laptop, LiveUSB works fine, installed distros do not start - blank screen, cannot start in console mode


When I do this in the grub edit menu, I get the same results:
linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro  nosplash --verbose text

Full History below:

 **[FONT=&quot]From:[/FONT]**[FONT=&quot]  Y
**Sent:** December-14-12 3:01 PM
**To:** RAMSESray
**Subject:** Re: Purple Screen after boot-repair[/FONT]
   
  sorry, i have no more idea. please ask on [ubuntuforums.org]("http://ubuntuforums.org")
  2012/12/14 [FONT=&quot]RAMSESray[/FONT]
    [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Y,[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I end up with a catch 22 situation.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]-I disable Secure Boot, no problem[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]-Cannot enable/disable Fast Boot as this variable does not exist in the BIOS menu (so far).[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]-I disable “Launch CSM” in the BIOS boot option[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]-“Fast Boot” option now appears as selectable and Enabled. “Launch CSM” is still a selectable variable.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]-I can now enable or disable Fast Boot[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I get the blank screen on installed distros no matter what combination I try.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]If “Launch CSM” is disabled, the pc does not recognize the LiveUSB stick with Ubuntu.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Therefore, I cannot run Boot repair AFTER disabling Fast Boot.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I spent a few hours trying different combinations with no avail.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Only once I was able to get into an installed Linux Mint KDE but I could not replicate this result with the same procedure.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  Kubuntu with Secure Boot off: [http://paste.ubuntu.com/1431887/](http://paste.ubuntu.com/1431887/)
  Kubuntu with Secure Boot off & a Boot-repair run that was shorter than usual without the grub purge code etc: [http://paste.ubuntu.com/1432417/](http://paste.ubuntu.com/1432417/)
  Linux Mint with Secure Boot off & Boot-repair run immediately after installation from LiveUSB without restarting pc: [http://paste2.org/p/2601061](http://paste2.org/p/2601061)
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I get the impression that linux doesn’t jive well with Asus laptops. A couple of years ago NO linux distro worked on my current Asus except for Fedora 14 which later caused bigger problems when I decided to update it.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Ideas?[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Thanks,[/FONT][/COLOR]
  [FONT=&quot]RAMSESray[/FONT]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  **[FONT=&quot]From:[/FONT]**[FONT=&quot] 
**Sent:** December-13-12 5:31 PM[/FONT]
  
**To:** [FONT=&quot]RAMSESray[/FONT]
**Subject:** Re: Purple Screen after boot-repair
   
  Try disabling SecureBoot and QuickBoot in your BIOS.
Then run Boot-Repair.

Y
  2012/12/13 [FONT=&quot]RAMSESray[/FONT]
  [COLOR=#1F497D][FONT=&quot]Y,[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I tried:[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D]Ubuntu 13.04: [/COLOR][http://paste.ubuntu.com/1429038/](http://paste.ubuntu.com/1429038/)
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Xubuntu: [/FONT][/COLOR][http://paste.ubuntu.com/1429104/](http://paste.ubuntu.com/1429104/)
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Lubuntu: [/FONT][/COLOR][http://paste.ubuntu.com/1429141/](http://paste.ubuntu.com/1429141/)
   
  [COLOR=#1F497D]Linux Mint Cinnamon: [/COLOR][http://paste2.org/p/2596569](http://paste2.org/p/2596569)
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Linux Mint Mate: [/FONT][/COLOR][http://paste2.org/p/2597323](http://paste2.org/p/2597323)
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]All with identical results as per the steps in my email below!![/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I also tried replacing “quiet splash” with “nomodeset” as per my quick google search and that didn’t fix it.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I don’t understand why all these systems run fine from the USB but not from the HD after I’ve installed them.[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]Thanks,[/FONT][/COLOR]
  [FONT=&quot]RAMSESray[/FONT]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  **[FONT=&quot]From:[/FONT]**[FONT=&quot] 
**Sent:** December-12-12 3:03 PM
**To:** [/FONT][FONT=&quot][FONT=&quot]RAMSESray[/FONT] 
[/FONT]
[FONT=&quot]**Subject:** Re: Purple Screen after boot-repair[/FONT]
   
  Hi [FONT=&quot]RAMSESray[/FONT]

this may be a kernel problem.
Please try to install Ubuntu 13.04 (alpha stage) instead, as it contains a very new kernel: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Regards
Y
  2012/12/12 [FONT=&quot]RAMSESray[/FONT]
  Hi,
   
  I installed Ubuntu 12.10 “alongside” Windows 8.
   
  After installation, it would still just boot straight to windows.
   
  I followed Boot-Repair “recommended” repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) : [http://paste.ubuntu.com/1426986/](http://paste.ubuntu.com/1426986/)
   
  I now see Grub 2 when I boot.
   
  Any incarnation of Ubuntu (recovery mode or not) does not start. I get stuck at a purple screen. The recovery mode version prints two lines before freezing “Loading Linux 3.5.0-17-generic … Lading Initial ramdisk …”
   
  I tried the steps on this page [http://askubuntu.com/questions/138700/ubuntu-12-04-blank-purple-splash-screen-after-live-install](http://askubuntu.com/questions/138700/ubuntu-12-04-blank-purple-splash-screen-after-live-install) via a liveUSB Ubuntu but could not execute the last 2 lines because it was “read only”
  “sudo update-grub2
  sudo update-initramfs –u”
   
  Ideas?
   
  Thanks,
  [FONT=&quot]RAMSESray[/FONT]

---

### Post by oldfred on 2012-12-15
It looks like you were installing in BIOS mode. With Windows 8 pre-installed you have UEFI with gpt partitioning.

To install Ubuntu correctly you have to boot the installer in UEFI mode not BIOS/AHCI/legacy mode. But Boot-Repair can fix that.

From grub menu does Windows boot from this entry?
> Windows UEFI loader

Did you boot from installer in live mode to see if it worked ok with your system?

If now you are getting to purple screen grub has loaded and it probably is a video issue, but may also or need other boot parameters.

What video card/chip do you have? Exactly which model Asus?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
    
       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

    
older UEFI with Windows 7
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

            efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

---

### Post by RAMSESray on 2012-12-15
> **oldfred said:**
> It looks like you were installing in BIOS mode. With Windows 8 pre-installed you have UEFI with gpt partitioning.

Yes, my installations were in legacy mode as opposed to UEFI for reasons below.

> **oldfred said:**
> To install Ubuntu correctly you have to boot the installer in UEFI mode not BIOS/AHCI/legacy mode. But Boot-Repair can fix that.

If I start the installer (LiveUSB) from the "UEFI: USB XX etc.." as opposed to the legacy start "USB XX etc.." then I also end up with a frozen blank screen when I select start ubuntu from the menu.
If I start the installer (LiveUSB) from legacy mode than I am able to carry on with the installation.
i.e. I can't start the installer in UEFI mode without the same error.

Can Boot-repair convert a legacy install into a UEFI-install?

> **oldfred said:**
> From grub menu does Windows boot from this entry?
Yes.

> **oldfred said:**
> 
Did you boot from installer in live mode to see if it worked ok with your system?
The live installer works fine as long as I start in legacy (not-UEFI) mode as I mentioned above.


> **oldfred said:**
> 
If now you are getting to purple screen grub has loaded and it probably is a video issue, but may also or need other boot parameters.

Is it a video issue even though i still can't get it to start with the "nosplash --verbose text" edit? (again, in the non-UEFI installation)


> **oldfred said:**
> 
What video card/chip do you have? Exactly which model Asus?

It's Asus K55N with AMD Radeon HD 7640G.

       > **oldfred said:**
> How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

    Yes I went through this, from what I gather i have a kernel problem  since the text only boot does not work (i.e. loading to console).

       
       > **oldfred said:**
> ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Couldn't figure where I would put this parameter...

    

       > **oldfred said:**
> older UEFI with Windows 7
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

            efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

I don't think I can use this since I can't start any LiveUSB via UEFI..

---

### Post by oldfred on 2012-12-15
Not being able to start live system was a clue. I do not know AMD very well as I have nVidia on Desktop & Intel on laptop, both are old and work well. There may be better settings for AMD than nomodeset, but try that first.

You need to look at link on nomodeset & boot parameters. You change the quiet splash to nomodeset and the linked thread said to also include the pci=nomsi parameter also. just type it in with a space between the parameters like quiet splash are.

Even if you install in BIOS mode Boot_Repair converts to UEFI if you have a 12.10 64 bit version. It uninstalls the BIOS version of grub, grub-pc and installs the UEFI version of grub, grub-efi. Your Ubuntu install is identical either way (some minor editing of settings).

---

### Post by RAMSESray on 2012-12-15
I deleted "quiet splash" and tried different combinations of the following parameters with the exact same result - blank screen...

```
 nomodeset acpi_osi= noapic nolapic pci=nomsi --verbose text
```

---

### Post by oldfred on 2012-12-15
With nomodeset you did not get scrolling commands, at least at first? 

These were options for older verisons, not sure they work with the newer.
xforcevesa
 or
 nouveau.modeset=0
or
radeon.modeset=0

 I would go thru the mega thread as a lot of different alternative have been posted.  

Is this a system with two video modes? If so try the other in a setting in UEFI/BIOS.

---

### Post by RAMSESray on 2012-12-16
> **oldfred said:**
> With nomodeset you did not get scrolling commands, at least at first? 

Whatever I put there on the linux /boot line, I get the EXACT same result - blank screen.
It's only different with recovery mode when it freezes after printing out two lines: Loading Linux 3.5.0-19-generic ...
          Loading initial ramdisk ...

> **oldfred said:**
> 
These were options for older verisons, not sure they work with the newer.
xforcevesa
 or
 nouveau.modeset=0
or
radeon.modeset=0

I get the same thing still.

> **oldfred said:**
> 
 I would go thru the mega thread as a lot of different alternative have been posted.  

I went through the mega thread flow and I basically get stuck at Step 2 where my I can't start it in text mode (i.e. --verbose text)

> **Step 2** "Does the Linux Kernel Boot?"  At Grub Menu, go into edit mode and boot into a text console (see instructions below)
- Yes. Go to Step 3
 - No. Messages will be verbose on what is loading, what are warnings     and what are error messages.  Shortcut keys will start to work as the     kernel modules load.  If if stops at an error, you will be able to use     the shortcut navigation cuts to review the errors.  Depending on the     error, if it is a kernel error, you may be able to reinstall or  renew    the kernel image.  If it is a device module, at least you have  somewhere    to go to reload that device module or driver.,,, Goal is to  get a    "booting kernel."> **oldfred said:**
> Is this a system with two video modes? If so try the other in a setting in UEFI/BIOS.
Two video modes? I don't understand. The system does appear to have option for legacy as well as UEFI. USB's are often shown twice (one preceded by UEFI: ). You said that Boot-repair reinstalls grub into UEFI so I'm not sure what I'm supposed to try here.

I pasted my hardware info here after I ran "hwinfo" in a live session.

[http://pastebin.com/hCma8Vem](http://pastebin.com/hCma8Vem)

---

### Post by oldfred on 2012-12-16
You should only install with UEFI. But a few could not and installed in BIOS mode and used Boot-Repair to convert and that worked.

But your issue seems like it is not even starting. That is more often the issue with a bad download that is missing something or the installer did not install correctly and something is missing. As part of the install process it create the init file that is customized. That is copied into memory and starts boot process. Yours does not seem correct. 

At this point all I can really suggest is redown load the 64bit version of 12.10, verfiy that it is correct and try a reinstall.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
    
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RAMSESray on 2012-12-16
It would seem kind of odd that it's something wrong with the download since I tried at least half a dozen distros already. Anyways, I tried again and did the "check disks for defects" and there were no errors. Same result of course - blank screen.

However, when I did the "test memory" I got this:

[http://i48.tinypic.com/10ngqwj.jpg](http://i48.tinypic.com/10ngqwj.jpg)

What does this mean?

---

### Post by oldfred on 2012-12-16
Something not good.

Are you overclocking memory? Or it seems part of memory is not quite right.

You may be able to test if you have several memory modules and can remove and test each. 
Sometimes memory just needs to have contacts cleaned with an eraser and alcohol to remove any eraser bits and firmly reseated.

---

