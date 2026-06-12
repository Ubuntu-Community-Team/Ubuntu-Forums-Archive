---
title: "System refuses to boot from disc or USB"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by shamusl on 2012-01-13
My Gigabyte GA-EP-UD3P refuses to boot to anything but Windows, even without any hard disk connected.The BIOS says: Boot from CD/DVD... and then it boots to a screen saying the Windows hard disk is missing, which I didn't know was even possible. I was previously using Bitlocker w/ TPM on the drive, so I'm not sure if that's related.

I've reset and cleared the CMOS/BIOS, and tried moving the SATA port around for the DVD drive. The USB stick I have the .iso on also won't boot, but I booted from it and installed a system from it on another system just a few minutes prior.

I'm not really sure how to proceed, is there anything I can do that I haven't done yet?

---

### Post by carl4926 on 2012-01-13
You should read this
[http://windows.microsoft.com/en-US/windows-vista/BitLocker-Drive-Encryption-Overview](http://windows.microsoft.com/en-US/windows-vista/BitLocker-Drive-Encryption-Overview)

Note the part about TPM

---

### Post by shamusl on 2012-01-13
Edit: I disabled the TPM, no change. The only screen the computer will produce is still Windows Boot Manager. Have I destroyed this motherboard? Is there any solution to this? The computer says insert a Windows disc, but when I do, it doesn't do anything but kick me back to the same screen.

---

### Post by shamusl on 2012-01-13
Computer responded to the Windows recovery disc, and the Win7 system runs well. However, the motherboard refuses to boot from anything other than Windows, even if I remove that drive. I wasn't using Bitlocker on the main drive, which is the SDD I'm trying to install Ubuntu on. Wubi works just fine, but I can't install the system in its own partition. Could reinstalling Windows 7 over the other old system help this?

---

