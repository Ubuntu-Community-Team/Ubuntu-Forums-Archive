---
title: "Jolicloud installation wiped out existing Ubuntu installation"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by gargleblaster on 2009-12-10
I have an old Dell Latitude D600 running Windows XP Pro.  A couple of days ago, I installed Ubuntu on it using the Windows installer, allowing me to choose between Ubuntu and XP at boot time.  That's been working great.

Today, I read about Jolicloud and decided to try it.  I assumed (I know, I know!) it would add itself to the boot menu, so that I could then choose between Ubuntu, XP, and Jolicloud.

Well, instead, I can now choose between Jolicloud and XP.  Ubuntu has vanished from the boot menu.

Is my Ubuntu installation gone?  Or is this a GRUB issue?  Or an MBR issue?  Is there any way for me to get back to my Ubuntu installation???  I had important work on there that I would like to recover!

Please help.

Thanks,
Lee

---

### Post by gargleblaster on 2009-12-11
It seems that the Jolicloud installer REPLACED my Ubuntu entry in boot.ini with its own Jolicloud entry.  And, I'm assuming, it overwrote the Ubuntu wubildr and wubildr.mbr files in C:\ with its own.

I first tried editing the Windows C:\boot.ini file to add an Ubuntu entry pointing directly at C:\ubuntu\winboot\wubildr.mbr, but that still booted to Jolicloud.

I was able to boot my original Ubuntu installation by copying wubildr and wubildr.mbr from C:\ubuntu\winboot to C:\, replacing the ones that Jolicloud had put there.

I'd like to have all three as options, but I'm relieved to at least have access to Ubuntu again.  If you can tell me how to put a path in boot.ini that works (maybe it needed to be in Linux format, rather than Windows format?), that would be nice.

Thanks,
Lee

---

### Post by darkod on 2009-12-11
> **gargleblaster said:**
> It seems that the Jolicloud installer REPLACED my Ubuntu entry in boot.ini with its own Jolicloud entry.  And, I'm assuming, it overwrote the Ubuntu wubildr and wubildr.mbr files in C:\ with its own.

I first tried editing the Windows C:\boot.ini file to add an Ubuntu entry pointing directly at C:\ubuntu\winboot\wubildr.mbr, but that still booted to Jolicloud.

I was able to boot my original Ubuntu installation by copying wubildr and wubildr.mbr from C:\ubuntu\winboot to C:\, replacing the ones that Jolicloud had put there.

I'd like to have all three as options, but I'm relieved to at least have access to Ubuntu again.  If you can tell me how to put a path in boot.ini that works (maybe it needed to be in Linux format, rather than Windows format?), that would be nice.

Thanks,
Lee

If they work on similar principle, I'm not sure you can have both of them working. I'm not expert on wubi (that's what you have, not full ubuntu), so maybe someone else knows how.
One of the options is to install Ubuntu properly to its own partition with its own filesystem. In that situation, you can boot as many OSs as you want because all of them are sort of side-bys-de installs, next to each other.
Wubi just installs sort of virtual ubuntu inside windows, and if jolicloud did the same that's why it replaced the wubi entry with its own.
In side by side installs the bootloader (usually grub) is controlling the boot process and just calls the selected OS from its partition.

---

### Post by ers11121 on 2009-12-11
I'm new to Linux myself, but it sounds like something I did in a previous installation. If you can boot into Windows try using EasyBCD, it seemed to straighten out the mulitboot problem I had
Ed

---

### Post by craftygirl on 2010-02-02
Gargleblaster - you said you figured out how to get back to your original Ubuntu, were all of your contents still there?  Like personal files?  Or was it just like starting from scratch again?  Thanks.

---

