---
title: "Unable to install any ubuntu flavour: &quot;Couldn't get size&quot; &amp; &quot;Registered PHC Clock&quot;"
date: 2019-08-23
forum: Installation &amp; Upgrades
---

### Post by luukf8 on 2019-08-23
[COLOR=#242729][FONT=Arial]I want to completely get rid of Microsoft (thus Windows), and I really love the Ubuntu operating system and applications.
I had Ubuntu installed before on my computer, and it worked perfectly. For some reason I switched back to Windows, but now I want to completely get rid of Windows, but I can't.
I've installed Ubuntu several times on mine and others' pcs. It has always worked, but now I'm stuck at the very unclear sentence Couldn't get size.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This is a screenshot I took when I tried starting the Ubuntu installer using nomodeset: 
[/FONT][/COLOR][[IMG]https://i.imgur.com/T1qtT5tl.jpg[/IMG]]("https://i.imgur.com/T1qtT5t.jpg")[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][IMG]https://i.imgur.com/a/8VgBCnFl.jpg[/IMG][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][IMG]https://i.imgur.com/8VgBCnFi.jpg[/IMG]
[COLOR=#242729][FONT=Arial]I've searched on this and other forums, and I've found a couple of solutions, including:[/FONT][/COLOR]

[LIST]
[*]Using nomodeset & nouveau.modeset=0 (See screenshot)
[*]Using no splash
[*]Using CSM in UEFI setup
[*]Using Secure Boot either enabled or disabled in UEFI (Tried both)
[*]Using Safe Graphics when booting from GRUB
[*]Plug the USB drive into a 2.0 port instead of 3.0
[*]Disconnect ethernet cable
[*]Flash the USB drive with Rufus, Etcher, and UNetBootin (tried them all)
[*]Using the motherboard graphics instead of GPU by plugging in the HDMI cable directly to the motherboard
[/LIST]
[COLOR=#242729][FONT=Arial]Actually, nothing worked... I keep getting Couldn't get size. And when I remove quiet splash or use no splash, I see Registered PHC Clock. I know this isn't an error, but it hangs on that one and don't continue booting (even after 30 minutes).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I hope someone has a brilliant idea, which makes my system at least boot into the installer & desktop where I can fix some issues.
Thanks in advance for anyone who wants to help![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Regards, Luuk.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]*P.S. I don't think it's caused by the GPU, because it also doesn't work with the motherboard graphics...*[/FONT][/COLOR]

---

### Post by oldfred on 2019-08-23
What brand/model system? Which model nVidia card?
Some need additional boot parameters. With nVidia you probably at lease need nomodeset.

Have you updated UEFI
And if SSD updated SSD's firmware?

Are you able to get to grub menu? 

I would stay with UEFI Secure Boot off, boot in UEFI mode, have fast boot off in UEFI.

Is Windows still installed? You need fast start up off or the installer cannot correctly see drive as NTFS is the hibernated. Or even if you uninstalled Windows but left a NTFS partition which may then still have hibernation flag set.
Or perhaps other issues with drive?
Is drive set to AHCI? Not RAID nor Intel SRT. 
Some have had to remove hidden RAID data on drive if drive was really part of RAID at one time.

---

### Post by luukf8 on 2019-08-23
> **oldfred said:**
> What brand/model system? Which model nVidia card?
Some need additional boot parameters. With nVidia you probably at lease need nomodeset.

Have you updated UEFI
And if SSD updated SSD's firmware?

Are you able to get to grub menu? 

I would stay with UEFI Secure Boot off, boot in UEFI mode, have fast boot off in UEFI.

Is Windows still installed? You need fast start up off or the installer cannot correctly see drive as NTFS is the hibernated. Or even if you uninstalled Windows but left a NTFS partition which may then still have hibernation flag set.
Or perhaps other issues with drive?
Is drive set to AHCI? Not RAID nor Intel SRT. 
Some have had to remove hidden RAID data on drive if drive was really part of RAID at one time.

It's a custom-build pc by gamepc.nl
My Nvidia card is "GeForce GTX 1050 Ti".
I just updated the UEFI, but it didn't worked.
I am able to boot into GRUB, but when I start Ubuntu it says "Couldn't get size", immediately after I choose to boot from grub.
Fast startup is disabled and secure boot too.
My drive has always been in AHCI.
As I said in my first post, I have previously installed ubuntu several times on this pc, but now it doesn't work anymore...:confused:
Everything I have tried doesn't work. :(

---

### Post by oldfred on 2019-08-23
Some motherboards need boot parameters. Exactly what model?

Is error like this one?
[https://askubuntu.com/questions/1142981/ubuntu-installer-couldnt-get-size0x800000000000000e](https://askubuntu.com/questions/1142981/ubuntu-installer-couldnt-get-size0x800000000000000e)

---

### Post by luukf8 on 2019-08-23
Btw, when I turn off secure boot, I also get the following error beside the "Couldn't get size":
[I]MODSIGN: Couldn't get UEFI db list

[/I]> **luukf8 said:**
> Btw, when I turn off secure boot, I also get the following error beside the "Couldn't get size":
*MODSIGN: Couldn't get UEFI db list*

Yes the error looks like that.
My motherboard is _ASUS TUF B360M-PLUS GAMING_

---

### Post by oldfred on 2019-08-23
Are you installing 19.04?
Have you got UEFI set to boot UEFI only?
My older z97Asus would only boot correctly with UEFI only, even UEFI or CSM/Legacy would not boot correctly.

---

### Post by luukf8 on 2019-08-23
> **oldfred said:**
> Are you installing 19.04?
Have you got UEFI set to boot UEFI only?
My older z97Asus would only boot correctly with UEFI only, even UEFI or CSM/Legacy would not boot correctly.

Yes, I'm trying to install 19.04.
I do not know exactly what you mean with UEFI "only". I have CSM disabled, and I choose the UEFI entry from the boot menu...

---

### Post by oldfred on 2019-08-23
Even though newer, since Asus & Intel, you should have very similar UEFI screens:
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)

Mine has Windows or Other for Secure Boot, but also CSM, CSM or UEFI and UEFI only as boot options. I also have to turn on Allow USB boot.

If you updated UEFI, that often resets many settings to defaults. So you have to redo them. I keep a list.

---

### Post by luukf8 on 2019-08-24
> **oldfred said:**
> Even though newer, since Asus & Intel, you should have very similar UEFI screens:
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)

Mine has Windows or Other for Secure Boot, but also CSM, CSM or UEFI and UEFI only as boot options. I also have to turn on Allow USB boot.

If you updated UEFI, that often resets many settings to defaults. So you have to redo them. I keep a list.

I have changed all the settings from your screens, but not all options are available in mine.
The options that where available in my system where the same as in your screenshots. It didn't worked... :(
I still don't understand why it worked previously, but it doesn't work anymore when I try to install it now.
Hopefully, there will be a solution soon. ;)

---

### Post by oldfred on 2019-08-24
I would expect as a newer system, you would have more options.
I did find it very unusual that I had to turn on CSM to get more settings under CSM to change UEFI settings. Seemed backwards.

---

### Post by luukf8 on 2019-08-24
> **oldfred said:**
> I would expect as a newer system, you would have more options.
I did find it very unusual that I had to turn on CSM to get more settings under CSM to change UEFI settings. Seemed backwards.

Okay, now I have written the ISO image on my USB again, and it still didn't worked.
Now when I boot the USB, I see the following message:
"usb1-5: new low-speed usb device number 2 using xhci_hcd"
I think this is some issue with the USB devices. Sometimes it displays my keyboard, and sometimes my mouse.
Directly before the usb message, It says "Registered PHC Clock", still don't know what it means...

---

### Post by oldfred on 2019-08-24
I have a setting for USB partital or full. And have to enable that to allow USB boot.

---

### Post by luukf8 on 2019-08-24
> **oldfred said:**
> I have a setting for USB partital or full. And have to enable that to allow USB boot.

Unfortunately, I don't see that option. When I search for "USB", I get these results:
[[IMG]https://i.imgur.com/TizgOjdl.png[/IMG]]("https://i.imgur.com/TizgOjd.png")
Also, I am able to boot the usb, but I don't get any further after selecting "Start Kubuntu" from grub.

---

### Post by Autodave on 2019-08-24
Listen to oldfred: he knows way more about this than I ever will.

If it were me, I would probably be trying 18.04 since that is a long term service (LTS) release.  Fast boot must be off.  Sometimes the short term releases have issues.

---

### Post by luukf8 on 2019-08-24
> **Autodave said:**
> Listen to oldfred: he knows way more about this than I ever will.

If it were me, I would probably be trying 18.04 since that is a long term service (LTS) release.  Fast boot must be off.  Sometimes the short term releases have issues.

I tried both 19.04 & 18.04. Neither worked. :(
I'm stuck at this problem for at least one week. And I really don't know anything I can try anymore...

---

### Post by oldfred on 2019-08-24
I have the same USB settings.

But also have in boot options menu  full initialization which allows USB boot.
And then under CSM (CSM on) more UEFI options where boot from storage devices - UEFI only. UEFI or CSM has never worked for me.

---

### Post by luukf8 on 2019-08-24
> **oldfred said:**
> I have the same USB settings.

But also have in boot options menu  full initialization which allows USB boot.
And then under CSM (CSM on) more UEFI options where boot from storage devices - UEFI only. UEFI or CSM has never worked for me.

Again, it didn't worked. I have set it to UEFI only. But I couldn't find the full initialisation the full initialisation option.

---

### Post by oldfred on 2019-08-24
I am starting to run out of ideas. Others with similar models just work.

Suggest making sure ISO is correctly downloaded.
Some find different install tools, different flash drives, or different USB ports solve issues, but we cannot find any consistent solution.

confirm ISO is correct.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode 

Have you tried in UEFI turning off external video & just use Intel video. See VT-D settings. 
You have always been using nomodeset?

---

### Post by luukf8 on 2019-08-25
> **oldfred said:**
> I am starting to run out of ideas. Others with similar models just work.

Suggest making sure ISO is correctly downloaded.
Some find different install tools, different flash drives, or different USB ports solve issues, but we cannot find any consistent solution.

confirm ISO is correct.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode 

Have you tried in UEFI turning off external video & just use Intel video. See VT-D settings. 
You have always been using nomodeset?

I really don't know what to do now... Nothing works!
It's really strange this doesn't work a anymore, while it has worked previously...

---

### Post by oldfred on 2019-08-25
If it worked  before and is not some setting that change, it could be a hardware issue.
Test memory, try without nVidia and whatever else you can do.

---

### Post by luukf8 on 2019-08-26
> **oldfred said:**
> If it worked  before and is not some setting that change, it could be a hardware issue.
Test memory, try without nVidia and whatever else you can do.
I've selected "test memory" from grub, and my computer suddenly reboots to windows...
I've already tried without Nvidia, but it gets the same error.
I've contacted the manufacturer of my pc, they said me they only use windows, and cannot tell me anything about Ubuntu. :(

---

### Post by oldfred on 2019-08-26
Most vendors will not officially support anything other than Windows. It may even be in the support contract with Microsoft.
But they often make fixes to UEFI/BIOS to improved Linux use. 
Both Intel & AMD support Linux kernel with patches/updates for their devices.

To me if they support UEFI update with this, then they do at least indirectly support Linux.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

