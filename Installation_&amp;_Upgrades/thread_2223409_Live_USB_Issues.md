---
title: "Live USB Issues"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by vincent14 on 2014-05-10
My main ubuntu install has encountered a few issues after a recent update. I accidentally made things even worse while trying to fix it. One of my issues is that my OS no longer recognizes USB sticks. My problem is as follows. I made a ubuntu live USB on one of my old computers (winxp) so I could reinstall the OS and format my HDD. Upon booting from the USB, I got the message "remove discs or other media...press any key to restart." I tested multiple  live USBs with different distros on them, and I got the same message for all of them. I was using unetbootin on my alt pc to make the live USBs. I had them all formatted to FAT32. Any idea where I went wrong?

---

### Post by sudodus on 2014-05-11
Please describe the computer which does not want to boot from your USB pendrive! The more we know, the better we can help :-)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- BIOS or UEFI?

- Windows version?
- Ubuntu version installed (12.04 LTS, 13.10, 14.04 LTS)?

-o-

- Ubuntu version in the USB boot drive (12.04 LTS, 13.10, 14.04 LTS)?

- Does the old computer (where you made the USB boot drive) boot from the USB boot drive?

---

### Post by vincent14 on 2014-05-11
> **sudodus said:**
> Please describe the computer which does not want to boot from your USB pendrive! The more we know, the better we can help :-)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- BIOS or UEFI?

- Windows version?
- Ubuntu version installed (12.04 LTS, 13.10, 14.04 LTS)?

-o-

- Ubuntu version in the USB boot drive (12.04 LTS, 13.10, 14.04 LTS)?

- Does the old computer (where you made the USB boot drive) boot from the USB boot drive?

- ASUS mobo 
- AMD Phenom Black Edition II 
- 4 gigs ram
- Wired ethernet

- Windows on cpu used to make live usb=xp
- Using 14.04 LTS

- Using Mint 14 for the boot 
- Old cpu doesn't boot from USB

---

### Post by sudodus on 2014-05-11
I would try to boot the same version live as was working as installed (until it was borked), using Ubuntu14.04 LTS.

If still no go, try the [boot options]("https://help.ubuntu.com/community/BootOptions") in the live session. You can also try boot options with Mint.

---

