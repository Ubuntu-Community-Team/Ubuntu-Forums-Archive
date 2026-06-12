---
title: "12/10 install disc won't boot"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by RealGomer on 2012-10-19
I downloaded the ubuntu 12.10 iso from the canonical website. My pc is set to boot from cd/dvd. When the computer boots it hangs at the Boot from cd/dvd screen. The "press any key to boot from cd/dvd" prompt does not appear. The Win7 install disc works fine.
Suggestions? Yes, I'm going to download another copy from the main ubuntu site.

---

### Post by darkod on 2012-10-19
There is no message "press any key to boot" on the ubuntu cd like the windows install media.

It might be issue with video driver. The boot actually starts, and freezes, etc.

Does it show any ubuntu type screen (in 12.04 they were purple, not sure about 12.10), even for a short while, anything at all?

---

### Post by CryptAck on 2012-10-19
How did you burn it? Did you burn the ISO as a file to the media? You have to ensure you select an ISO format, and not a typical data format (for example). 

Browse the media and verify that it's a hierarchy of directories and not a single file.

---

### Post by wykedengel on 2012-10-19
I am having the same issue. It only happens with the 64-bit iso. Everything works with the 32-bit version. I have tried making discs and bootable USBs and it's just a no go with the 64-bit iso.

---

### Post by CryptAck on 2012-10-19
> **wykedengel said:**
> I am having the same issue. It only happens with the 64-bit iso. Everything works with the 32-bit version. I have tried making discs and bootable USBs and it's just a no go with the 64-bit iso.

I had trouble with creating a 64-bit ISO with [universal usb]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") earlier, but I was able to do it just fine with [unetbootin]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/").

---

### Post by wykedengel on 2012-10-20
> **CryptAck said:**
> I had trouble with creating a 64-bit ISO with [universal usb]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") earlier, but I was able to do it just fine with [unetbootin]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/").

Thanks, I will give that a try.

---

### Post by wykedengel on 2012-10-21
Just an update, UNetbootin works for AMD 64 discs. I successfully made a bootable USB install Ubuntu on my desktop.

---

