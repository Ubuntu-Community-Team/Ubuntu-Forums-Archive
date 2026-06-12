---
title: "external hard drive dual boot"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by danilo287 on 2007-01-05
Hey everyone...i am interested in dual booting with my external hard drive.  Right now i have windows xp x64 and ubuntu dual booting on my pc.  I was not able to install ubuntu on my hp pavillion (set up would hang).  I was wondering how i could install ubuntu on my external hard drive so then i could dual boot on my laptop with windows on the laptops hard drive and ubuntu on my external.  I all ready have windows xp installed on my laptop as well.  So i guess the real question is how do i install ubuntu on my external for my laptop, using my PC so my laptop can dual boot with the grub boot loader (windows and ubuntu).

---

### Post by logos34 on 2007-01-05
Does your hp notebook BIOS support booting from an external or usb device? If so, you could put ubuntu on the external drive (USB? Firewire? Firewire800?) and delete ubuntu from your desktop, leaving the entire disk to winxp x64 and your entire lappy disk to winxp. Make sure grub installs to /(root) on the external drive and not the mbr on the windows disk (unplug if necessary).  Set the boot order in the bios to boot first from ext. drive and second from windows.  If you want to go into Windows, just disconnect ext. drive at boot. Then just plug it back in and you can read your linux files using a program like Explore2fs (the latter only works on x86 windows.  I know--I have a WinXpx64/Ubuntu setup).  [[Dual Boot on Two drives]("http://www.ubuntuforums.org/showthread.php?t=275728")]

[edit: explore2fs does work in x64 windows--however your filenames must include the file type extension (i.e. .htm, .html, .abw, .jpg, etc) otherwise    it will try to open them in wordpad.]

If this is a usb drive we're talking about, it is slow compared to internal drives, so if speed is an issue you might want to try once more installing ubuntu on your notebook drive after fixing or reinstalling windows--maybe there are paging or hibernation files that need to be disabled, preinstalled software on unmovable files at the end of the disk, etc. (This [article]("http://www.linuxdevcenter.com/lpt/a/6554") might interest you). 

Once you're in ubuntu you can read all your files on both windows volumes.  You could also just replace the ubuntu partition on the desktop with fat32 to allow read and write.

If your pavilion doesn't support external boot it's a little more involved but there is a way. (Read [this]("https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29"))

Then again, you could devote both computers entirely to ubuntu and chuck windows!  What's it good for, anyway? 
(hardly ever use mine)

---

### Post by danilo287 on 2007-01-05
thanks for the quick reply.  Ill try out your recommendation and see how that works.  My external is a USB drive and my laptop does support booting from external hard drives.  THe problem i had with installing ubuntu on my laptop was that everytime it went to load the Enterprise Volume Management the install would just hang there and would never go past.  Its an hp pavillion dv6000 with AMD Turion 64 x2 dual core.  I tried making other posts about it in the forums but never got an answer.... do you have any idea how i can get around that, because i would love to just dual boot my laptops internal hard drive instead of having to use my external!!

---

### Post by logos34 on 2007-01-05
> everytime it went to load the Enterprise Volume Management the install would just hang there...do you have any idea how i can get around that

sorry, wish I did.  Read through the forum posts for 'evms' + 'install'--maybe someone's found a workaround.  Are you using the alternative install cd? Try the livecd or vice-versa.  Same for architecture (your turion can run either x86 or amd64 ubuntu).

---

