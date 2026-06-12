---
title: "How to install Ubuntu on Asus X205TA?"
date: 2021-11-02
forum: Installation &amp; Upgrades
---

### Post by cwblanch on 2021-11-02
I recently dug out this older laptop, Windows is completely broken on it, mouse and keyboard don't work at all and nothing I've done has fixed anything. I decided to try Linux to see if that will make it functional again, but nothing I've done will make it install. 

I read that it is a 32-bit filesystem so I downloaded a 32bit version of Ubuntu but no matter what I do I can't get the BIOS to see a USB drive. From what I understand it needs the bootia32.efi file but the drive is set to read only and I can't seem to set it to be writable at all. I tried copying from terminal (maybe I didn't use the right commands I've only recently come back to linux) but nothing would happen. No error or anything.
I have turned off secure boot and try to select the usb drive specifically for booting but it's just never there. The forum posts I've found either don't work for me, or the files recommended for downloading have been removed.


Any help would be awesome, it would be nice to get this damn laptop working again, it hasn't worked since I installed Win10 on it back in 2015 lol

---

### Post by ubfan1 on 2021-11-03
My x205CA is very picky about USB drives.  Insert the drive when running (hard if not capable of running, I know) then a reboot might see the drive and allow selection as a boot device.  There's nothing 32bit at all on the 205CA, the standard 64 bit EFI files boot fine.  Try Lubuntu for more limited memory (full Ubuntu runs fine in 4G). Both secure and non-secure boot work.

---

### Post by grahammechanical on 2021-11-03
> I read that it is a 32-bit filesystem so I downloaded a 32bit version of  Ubuntu but no matter what I do I can't get the BIOS to see a USB drive.  From what I understand it needs the bootia32.efi file

It is possible that what you read is referring to the BIOS/UEFI being 32 bit and the ISO image needing a 32 bit boot efi file. The ISO image I have of Ubuntu 20.04 has /EFI/BOOT/BOOTx64.efi & grubx64.efi & mmx64.efi. But not bootia32.efi. To paste bootia32.efi into /EFI/BOOT/ you would need to change the permissions of that folder. I do not know if it is possible to change the permissions of folders in an ISO image.

Regards

---

### Post by cwblanch on 2021-11-03
> **ubfan1 said:**
> My x205CA is very picky about USB drives.  Insert the drive when running (hard if not capable of running, I know) then a reboot might see the drive and allow selection as a boot device.  There's nothing 32bit at all on the 205CA, the standard 64 bit EFI files boot fine.  Try Lubuntu for more limited memory (full Ubuntu runs fine in 4G). Both secure and non-secure boot work.


I'll give that an attempt, I don't think I left the USB drive in there between boots. 

And I'll definitely use Lubuntu now that I think about it, this really isn't a very powerful device.

---

### Post by cwblanch on 2021-11-03
> **grahammechanical said:**
> It is possible that what you read is referring to the BIOS/UEFI being 32 bit and the ISO image needing a 32 bit boot efi file. The ISO image I have of Ubuntu 20.04 has /EFI/BOOT/BOOTx64.efi & grubx64.efi & mmx64.efi. But not bootia32.efi. To paste bootia32.efi into /EFI/BOOT/ you would need to change the permissions of that folder. I do not know if it is possible to change the permissions of folders in an ISO image.

Regards


That is possible, I was taking so much information in I couldn't organize it all lol.

I think I'll download 64 and 32-bit versions of Lubuntu and hope that it already has the bootia32.efi, if not I'll have to find a way to make the USB drive accessible so I can put that file on it.
Do you know of any way to change permissions via terminal? I'll look it up too, but I just can't remember anymore.

---

### Post by cwblanch on 2021-11-03
Quick update, neither Lubuntu USB even showed up in the BIOS but I randomly decided to plug in the original USB I used for my desktop (Ubuntu 20.04) and THAT showed up. But whenever I tried to boot from it the screen would turn black for a second and then just show the BIOS again. I clicked it 20 times or so and nothing changed. Idk why that drive showed up but it's something I guess

---

### Post by ActionParsnip on 2021-11-04
Do you have the latest BIOS?

---

### Post by cwblanch on 2021-11-04
> **ActionParsnip said:**
> Do you have the latest BIOS?

I'm not sure now that I think about it, it's been so long since I've attempted to use it. I'll double check that and see if it does any thing.

Thanks

---

### Post by cwblanch on 2021-11-06
> **ActionParsnip said:**
> Do you have the latest BIOS?

I am on the latest BIOS

and I can't actually figure out why one usb shows in the bios and others don't. I use Etcher for all of my bootable drives so in theory they'd all be the same right?

---

