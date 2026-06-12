---
title: "Ubuntu UEFI installation"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by giovilix47 on 2016-05-20
Hi, I'm a new user and I've been using Ubuntu for a month now. I'm using Ubuntu 16.04 LTS Xenial Xerus 64 bit on my Notebook.
I'd like to have a clarification about Ubuntu installation with UEFI and Secure Boot both enabled. Indeed I read that the file that should be marked as trusted by Secure Boot should be "shimx64.efi", but there are other files:  "grubx64.efi", "fwupx64.efi" e "MokManager.efi". I marked as trust only "shimx64.efi", but what are the differences between these files and what should be marked as trusted?

---

### Post by user1397 on 2016-05-20
First of all, you don't need to have secure boot enabled (I always disable it) but obviously it's not possible on certain laptop models (which really sucks).  But, ubuntu should be able to install itself with secure boot on without any issues or messing with shimx64 files.  It should just work automatically.  If you already installed ubuntu successfully, why are you asking about those files?  Or are you asking in theory or for another PC you have?

---

### Post by oldfred on 2016-05-20
You must have Acer as that is the only one that needs the "trusted" setting.

The shimx64.efi is the version of grubx64.efi for UEFI Secure boot. Your Acer may require you to set trusted on grubx64.efi, but grubx64.efi would only be used if not using Secure boot. Shim also works with Secure boot off, so not sure why both files still available?

Mokmanger is a key manager. Ubuntu uses the Microsoft key for UEFI boot. Lots of complaints about using a Microsoft key, but that is built into system to easy to use. The current instructions I attempted to read are not particularly easy on creating your own key, compiling all your own boot software, grub & kernel to use your key and reconfigure system. 
I would not suggest using mokmanager.

I would set trust on fwupx64.efi. If you look at grub menu you should have this setting:

```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}

```

Most new UEFI systems have fast boot in UEFI, which is different than fast start up in Windows. Normal BIOS or UEFI boot scans entire system for hardware and lists that on drive for operating system to use. Most times no changes, so fast boot skips scan for changes. But if you have changes you may need to go into UEFI to change settings. But fast boot is so quick that you do not have time to press the key(s) to get directly into UEFI.
Windows assumes you can boot into Windows and from Windows get into UEFI. But what if Windows does not boot?
Grub has its setting to get into UEFI, then but if grub does not boot, you may still have issues.

My motherboard has separate fast boot settings for cold boot or power on and warm boot or reboot. So I set cold boot to normal and reboot to fast boot with a delay. Many systems do not have those extra settings and just have on or off. Most of those will use normal boot if system off for period of time or all power drained. Some require coin battery on Motherboard removed for a bit to totally reset system. But then you have to go back into UEFI to reset all the changes in UEFI you made. I have many UEFI settings I changed.

---

### Post by user1397 on 2016-05-20
> **oldfred said:**
> You must have Acer as that is the only one that needs the "trusted" setting.I haven't heard this before...I have an Acer and I don't need to mess with any of this stuff.  Ubuntu installs on my Acer with or without secure boot enabled.

---

### Post by oldfred on 2016-05-20
Many threads with Users & Acers who had to set trust. Just about every version. 

Descriptions they post are similar to this, but this is one with a screen shot.
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

---

### Post by user1397 on 2016-05-20
Huh, weird. I've owned two different acers and neither had that requirement.  Guess I just got lucky

---

### Post by ubfan1 on 2016-05-20
Probably with secure boot off, the trust business does not apply.  
shimx64.efi is a really simple little program (last time I looked), which only runs grubx64.efi from the same directory.  Cannonical paid Microsoft to sign a version of shim, and since shim is so limited, changes/fixes are few, so the resigning a new executable is avoided.

---

### Post by giovilix47 on 2016-05-21
Hi, and thanks for the replies.

Indeed, I've got an Acer, more precisely an Acer Aspire ES1-512-P2C7. I made this thread mainly because I have an issue with Ubuntu on this notebook, indeed I made another thread just after this one about Ubuntu freezes. I'll try for sure to do what you suggested. Maybe my PC will work in a proper way.

Again, thanks a lot.

---

### Post by giovilix47 on 2016-06-02
Hi everybody, again. I've found the solution to this problem: just choose "shimx64.efi". And also, the freezes I was talking about aren't caused by this choice.

---

