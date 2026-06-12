---
title: "no luck putting supergrub2 on stick"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by Kris_M on 2015-12-29
Under 14.04.3Unity using /home/kris/Downloads/super_grub2_disk_hybrid_2.02s3.iso
I have tried with tuxboot. it completes writing but won't boot.

tried under win7  rescatux_cdrom_usb_hybrid_i386_amd64-486_0.30.2_sg2d.iso  with UUI from pendrivelinux.com - won't boot.

no error messages.

Bad ISO?

Bad karma?

---

### Post by sudodus on 2015-12-30
The names of the iso files indicate that they are hybrid iso files. Such iso files will boot when cloned to a USB pendrive. I suggest that you make a live-only pendrive (the default method) with [mkusb](https://help.ubuntu.com/community/mkusb/).

You need the universe repository in standard Ubuntu with Unity. Then you add the PPA for mkusb, update and install:

```
sudo add-apt-repository universe

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter to accept it
sudo apt-get update
sudo apt-get install mkusb
```

***Edit:***

You may want to check to iso files with md5sum. Get a [published] checksum from where you downloaded each file, run

```
md5sum /home/kris/Downloads/super_grub2_disk_hybrid_2.02s3.iso

md5sum rescatux_cdrom_usb_hybrid_i386_amd64-486_0.30.2_sg2d.iso  # in the current directory or add the correct path
```

and compare the results with the published checksums.

-o-

I was curious, downloaded and checked **super_grub2_disk_hybrid_2.02s3.iso**.

```
md5sum super_grub2_disk_hybrid_2.02s3.iso
e7515b7d4e9ea90f28b7f5a534906b85  super_grub2_disk_hybrid_2.02s3.iso
```

which matches the downloaded checksum, and I could make a working pendrive with ***mkusb***.

-o-

Check at the following link if you still have problems

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by sudodus on 2015-12-30
Are you running the computer in UEFI mode or BIOS mode? I noticed that there are seperate EFI versions of ***supergrub***.

---

### Post by Kris_M on 2015-12-30
Thanks! I'll try that when I get back on Linux.

I really have no idea whether I'm running in BIOS or UEFI - it's a UEFI mobo but I have selected the windows 8 BIOS option thing to "other OS" so I think I'm running in BIOS. ie NOT win8 type stuff.

I'm on the rocks for the moment - I flashed F6 BIOS and now I can't boot from USB sticks - put a incident in to Gigabyte (GA-Z87N-WIFI) but probably fixed by "new mobo" - rats! - at least my HD and SSD are okay though probably win7 won't like a new chipset.  Maybe I can find another Z87...

Darn and things were going so well!

THANKS!!! (posted from win7 darn it... :(  )

---

### Post by oldfred on 2015-12-30
"Other" can be UEFI or BIOS. 
The Windows setting is for Windows 8 or later that can use UEFI secure boot. With other secure boot is off, but you still could have UEFI or CSM/BIOS/Legacy on.
But Windows 7 default install is BIOS, you have to slightly modify installer on flash drive to allow Windows 7 installer to boot in UEFI mode.

Not sure SuperGrub works on UEFI. I last used it with my grub boot of ISO on BIOS only system. But I was able to directly boot that with grub2's loopmount.

---

### Post by Kris_M on 2015-12-30
Fixed the F6 BIOS boot from USB flash drives problem but my last blank one (the one I had grub on) went bad so it's off to MicroCenter again.  I'll play with it later.  Thanks all!!!!!!!!!!!

> **sudodus said:**
> The names of the iso files indicate that they are hybrid iso files. Such iso files will boot when cloned to a USB pendrive. I suggest that you make a live-only pendrive (the default method) with [mkusb]("https://help.ubuntu.com/community/mkusb/").

You need the universe repository in standard Ubuntu with Unity. Then you add the PPA for mkusb, update and install:

```
sudo add-apt-repository universe

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter to accept it
sudo apt-get update
sudo apt-get install mkusb
```

***<snip>***

which matches the downloaded checksum, and I could make a working pendrive with ***mkusb***.

<snip>

I grabbed rescatux-0.40b2.iso from sourceforge and used  **mkusb** to flash it and voila. I am finding with this new BIOS that I often have to go in to BIOS and edit the boot order to get it to boot to the stick, but at least it boots.  THANKS!!!

And thanks all for looking in and advice!!!!!!!!!!!!!!

---

### Post by sudodus on 2015-12-31
Congratulations and thanks for sharing the solution :KS

---

### Post by Kris_M on 2015-12-31
> **oldfred said:**
> "Other" can be UEFI or BIOS. 
The Windows setting is for Windows 8 or later that can use UEFI secure boot. With other secure boot is off, but you still could have UEFI or CSM/BIOS/Legacy on.
But Windows 7 default install is BIOS, you have to slightly modify installer on flash drive to allow Windows 7 installer to boot in UEFI mode.

Not sure SuperGrub works on UEFI. I last used it with my grub boot of ISO on BIOS only system. But I was able to directly boot that with grub2's loopmount.


So how do I tell if i'm "UEFI or BIOS"  It seems as if they are inseparable on this mobo.  for every usb flash drive I stick in it offers me both (in BIOS) as a way to boot, though I can't remember if UEFI was ever successful.  I think they invented that stuff for the security in win8 and beyond, but I'm using UBUNTU (and win7(tiny letters)).



"sudodus 	 	 		[INDENT] 			 				Re: no luck putting supergrub2 on stick
 			 			Congratulations and thanks for sharing the solution :KS "
[/INDENT]You're welcome - I love successes!  :D:D

---

### Post by sudodus on 2015-12-31
[Test if running in UEFI mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)

---

### Post by Kris_M on 2015-12-31
> **sudodus said:**
> [Test if running in UEFI mode]("https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode")

Thanks!!  Ubuntu came back "BIOS" - I then went to win7 and looked in disk mgt and it did NOT say EFI so it's legacy BIOS.  Double YAY!!!!!  :D:D

---

### Post by Kris_M on 2016-01-18
rescatux 40 (see post 6) just saved my behind.  
I had gotten a few big games to work on 14.04.3 and thought to remove them from win7.
I booted to win7 and uninstalled them and then used easeus partition manager to remove the 2 partitions.
Rebooted and mbr was hosed. said something like grub recover>   Looked in bios but no joy.
Booted usb flash gparted and all looked fine.
Booted usb flash rescatux and asked it to restore grub.  It said success.
Grub looked like it did before so config wasn't touched.
Test booted win7 - fine
Booted 14.0403 - fine!
Boy am I happy that I researched this!!!  I sure would have hated to lose all that!!!
:D

---

