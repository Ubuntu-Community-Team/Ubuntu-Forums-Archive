---
title: "UGH! Can't install LM 32bit with UEFI disabled on UEFI Asus X200MA laptop"
date: 2015-10-15
forum: MINT
---

### Post by DwDtEXp on 2015-10-15
I only want Ubuntu (actually LM), no dual boot on this machine, and only 32bit Linux at that (though the machine is capable of 64bit and UEFI). 

Why 32 bit? I've had flaky behavior with 64bit LM (17.2), and found once before (another Asus) that the problems went away after switching to 32bit (same LM 17.2 using same home dir.). Previously Windows was installed (came with the machine). At the time, I wiped windows off and I did a 64bit LM 17 install successfully on this machine with UEFI still on. But as I said, I want 32bit if I can get it.

There are BIOS switches for on the machine to disable UEFI stuff ("CSM") and "fast boot", and "Secure Boot" was already disabled. With these switches actvated to disable UEFI, I was able to build and boot a USB with a 32bit LM 17.2  (using usb-creator-gtk) to boot and install LM 17.2 over the 64bit LM 17.2 partition I had before. The install went OK (though it first demanded a "grub-bios" marked partition as the first partition on the disk (which I created using gparted). I then ran boot-repair after the install completed to make ensure I had a bootable system. (I also made sure on Boot Repair options that "use uefi partition" was unchecked.) And with the boot usb running, I can click "Computer"  and see the LM 17.2 32bit partition and my /home partition. No problem.

However, the machine is unbootable. After powerup, the machine goes straight into setup (BIOS/UEFI setup). There's nothing listed in the "boot order" page of the BIOS, only a sinister message asking me if I want to add a UEFI bootable partition, which makes me think that although UEFI is supposedly off, the BIOS will still only recognize UEFI partitions. (PS I updated to the latest Asus BIOS for the X200ma before starting all this).

Some questions: 1) is it even possible to install a 32bit OS on a UEFI system, even if UEFI is supposedly turned off and you're in legacy BIOS mode. 2) Do I need to do something with UEFI in order to boot?

If it will help, here's the boot-repair output....

[http://paste2.org/sw5bLD3C](http://paste2.org/sw5bLD3C)

PS: In the USB install, I chose "something else", because I already had an LM partition, a /home partition, and a swap partition existing on the disk---so I didn't really install "from scratch".

---

### Post by howefield on 2015-10-15
Thread moved to the "*MINT*" forum.

---

