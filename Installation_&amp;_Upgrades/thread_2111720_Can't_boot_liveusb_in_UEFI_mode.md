---
title: "Can't boot liveusb in UEFI mode"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by jboy671 on 2013-02-02
I have spent the last three days on this.

I am not new to installing ubuntu or windows.  I am new to installing ubuntu on a 64 bit architecture that has uefi and secure boot.

I have created the liveusb 64 bit ubuntu amd for my asus k55n.

In uefi mode the uefi grub menu appears but when I choose try ubuntu without installing I get one of two scenarios.

If secure boot is enabled I get a "binary is whitelisted" text and nothing else.

If secure boot is disabled I get a blank screen.

In the past three days I have tried everything within my searching power and results to no success.

nomodeset, nosplash, verbose text, text, gfxmode set explicitly

It just will not boot into uefi mode.  I can't install to dual boot alongside windows 8 because it always says files are missing from the boot section.  

Since I can't boot ubuntu from the liveusb in uefi mode alone I can't use boot-repair to fix it.

I am at a loss.  At this point I'm starting to give up.  If I can I would like to just dump win8 (I bought this laptop new to replace my now 7 year old laptop) and put ubuntu solely on the drive with my partitioning but even that is scary to think for now because I have to make an esp partition.

For now my main problem is that ubuntu amd 64 will not boot in uefi mode from liveusb.

Thanks for any help.

BTW, I forgot my old account info for this forum so I had to make a new one again.  Is there a way to retrieve login info?

---

### Post by oldfred on 2013-02-02
If you want you can post in Forum Feedback & help. I am surprised an Admin has not yet complained to you for duplicate accounts. You will not be able to merge and must know original email (do not post it).
[http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

Some Asus that worked.
       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

            Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

            Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)


A few systems only install in BIOS mode. But Boot-Repair can convert a BIOS install to UEFI. 

       
 You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 

Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by jboy671 on 2013-02-05
Just to update people...

The asus k55n laptop is incapable of booting anything in efi mode other than windows 8.

I verified this by making efi/uefi bootable usb sticks of win8, win7, ubuntu12.10 and ubuntu12.10 secure remix.

All were 64 bits, properly formatted sticks (bios/efi/uefi interface listed them as UEFI in the boot options).

In the k55n, with the exception of win8, all of them loaded to a certain point and then just stopped/froze altogether.  Ubuntu/Secure Remix would show grub2 (efi/uefi) menu but when choosing "Try ubuntu without installing" it would get stuck on a blank screen.  

Many boot parameters were tried with the ubuntu loaders (pci=nomsi, nomodeset, acpi_osi=""/Linux/Windows 2006, vga=771, nosplash, start_pcmcia=false, etc. nearly every boot parameter I could find/try) but they could never load as a true efi/uefi install loader.

Win7 would detect efi environment but not truly install as efi.

Secure boot was disabled for all these installers including win8.  Win8 installed as true efi with secure boot disabled.

The same usb sticks including win8 were not altered and booted in my wife's asus x501a.

Asus x501a with secure boot disabled, all loaders booted and installed in true efi mode. Ubuntu/Secure Remix identified gpt partition, created ESP partition, installed efi loader into ESP partition and booted ubuntu/secure remix in true efi mode.  Same results for win7/8.

Asus x501a did not require extra boot parameters to load in efi mode.

So after over a week of trial and error the conclusion is that asus k55n for now is incapable of booting anything in efi/uefi mode until they update their bios/efi/uefi software.

It's not to say ubuntu can't be installed on this laptop.  It will install anything except win8 in bios mode.

---

### Post by oldfred on 2013-02-06
I would think Asus would have one UEFI. But they must have some difference where Intel versions work and AMD currently do not.

---

### Post by jboy671 on 2013-02-14
It seems there may be hope for this notebook after all.

I just have to confirm my steps (at least for win7) and duplicate the success.

For now I managed to get win7 in true efi mode according to bcdedit. :KS

[IMG]http://dl.dropbox.com/u/14081160/cmd.jpg[/IMG]

---

### Post by jdfoote on 2013-04-17
I just bought this same laptop - have you been successful in installing Ubuntu?

---

### Post by yateendra on 2013-04-17
I've subscribed to this thread to be alerted if others have found a solution. There are various workarounds, and I settled on creating a grub boot disk for the DVD-ROM (which I rarely use) and setting the BIOS for a non-UEFI DVD boot. On the rare occasions I want Windows, I interrupt the boot with F2 and use a menu there to boot in UEFI.

 The version of the K55N I now have has Windows 8 (this is a replacement of the previous machine which had Win7, in which I assume the BIOS NVRAM got confused by my modifications of the UEFI boot menu). I am not convinced of the security of Win8 (so much Internet connectivity--MetroUI, even the login if I recall correctly) so the machine would be of no use without Kubuntu.

---

### Post by jdfoote on 2013-04-18
I'm still trying to decide whether or not to keep this laptop. Those of you with the K55N, running Ubuntu - has it worked pretty well for you, or do you think it's worth getting a laptop with better supported hardware?

---

### Post by Aide9aic on 2013-04-21
I'm wondering if you might be able to boot the Ubuntu Server ISO, which doesn't throw GRUB into a graphical mode. Graphics hardware behaves differently in UEFI mode than in BIOS mode; perhaps something in your ASUS is simply confusing GRUB's graphical mode detection. If the Server ISO allows you to get the base OS installed, you can then Kubuntu -- which is what I think you mentioned -- like this:
```
sudo tasksel install kubuntu-desktop
```

---

### Post by kylemsguy on 2013-04-21
I've been having the same problem with the K55N laptop. I don't think the problem is with the graphics because I haven't been able to boot Arch Linux in UEFI mode (from the live CD or from the hard drive). It just hung on "Loading Initial Ramdisk..." after the boot menu (both gummiboot and grub)

---

### Post by jboy671 on 2013-04-22
> **jdfoote said:**
> I just bought this same laptop - have you been successful in installing Ubuntu? I have only been able to install ubuntu on the k55n in bios mode...no go on efi/uefi mode for any linux distro on the k55n.

> **yateendra said:**
> I've subscribed to this thread to be alerted if others have found a solution. There are various workarounds, and I settled on creating a grub boot disk for the DVD-ROM (which I rarely use) and setting the BIOS for a non-UEFI DVD boot. On the rare occasions I want Windows, I interrupt the boot with F2 and use a menu there to boot in UEFI.

 The version of the K55N I now have has Windows 8 (this is a replacement of the previous machine which had Win7, in which I assume the BIOS NVRAM got confused by my modifications of the UEFI boot menu). I am not convinced of the security of Win8 (so much Internet connectivity--MetroUI, even the login if I recall correctly) so the machine would be of no use without Kubuntu.

The only way to get ubuntu or any linux distro I have found on the k55n is through bios mode.  This means if you wanted to dual boot windows and linux on the k55n you would have to install both in bios mode.  The reason I was seeking the efi/uefi install method was to be able to use and boot off a 1tb hdd.

> **jdfoote said:**
> I'm still trying to decide whether or not to keep this laptop. Those of you with the K55N, running Ubuntu - has it worked pretty well for you, or do you think it's worth getting a laptop with better supported hardware?

You can keep it if you want to and don't mind being bound to bios booting ubuntu.  The only good thing about bios booting ubuntu/linux is it makes it easier to dual boot with windows.  The downside is if you are using a 1tb hdd then efi/uefi install mode is preferred.

> **kylemsguy said:**
> I've been having the same problem with the K55N laptop. I don't think the problem is with the graphics because I haven't been able to boot Arch Linux in UEFI mode (from the live CD or from the hard drive). It just hung on "Loading Initial Ramdisk..." after the boot menu (both gummiboot and grub)

This is the behavior I have seen from the k55n when trying to efi/uefi install/try any linux distro.  In bios mode it runs with no problems.  I agree it is not graphics related but more "bios" or firmware related.  

In summation, I have found that as far as linux goes it is practically impossible to install in efi/uefi mode on the k55n even after downgrading the "bios" or firmware.  Installing in bios mode is no problem and runs without incident.  Getting windows 7 to install and boot in efi/uefi mode involves some "trickery" and downgrading of "bios"/firmware.  

The only logical and pain free solution with this particular laptop is to install linux in bios mode and if you want dual boot you must also install windows in bios mode alongside linux.  

I hope this helps others out who have been relying on this thread.

---

