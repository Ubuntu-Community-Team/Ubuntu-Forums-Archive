---
title: "usb boot disk detected but won't boot from usb (memtest86 works)"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by freemant on 2022-08-19
Hi,

I am trying to run the live Ubuntu iso by booting from a usb boot disk made with Startup Disk Creator. The computer is running Windows 10 fine. The disk is detected by BIOS and I can select to boot from it. However, nothing happens then: no error and just blank screen as if nothing is happening. The strange thing is the memtest86 iso works. I have also tried the system rescue CD iso and Fedora iso and the result is the same as the Ubuntu iso (just blank screen). I have tried enabling/disabling secure boot and there is no visible difference.

Is there any way I can troubleshoot this thing?

The firmware is aptio from American megatrends dated 2020.

The open source memtest86+ v6.00 Beta 3 (which is unrelated to the freeware memtest86 above) sometimes work if I choose to boot from partition 2 instead of the disk. Sometimes it just reboots automatically.

Thanks in advance

---

### Post by yancek on 2022-08-19
Which Ubuntu release are you using, 22.04?  Did you do a checksum on the downloaded iso before putting it on the USB?  See the link below which explains it.

[https://ubuntu.com/download/desktop/thank-you?version=22.04.1&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=22.04.1&architecture=amd64)

---

### Post by freemant on 2022-08-20
> **yancek said:**
> Which Ubuntu release are you using, 22.04?  Did you do a checksum on the downloaded iso before putting it on the USB?  See the link below which explains it.

Yes, 22.04. I didn't do a checksum but it can boot properly on other computers. The problem probably lies in grub as all other open source boot programs fail and only the closed source freeware memtest works.

---

### Post by oldfred on 2022-08-20
What brand/model system?
What video card/chip?

Are you booting in UEFI boot mode and using Safe boot in grub, if you can get to grub menu?

---

