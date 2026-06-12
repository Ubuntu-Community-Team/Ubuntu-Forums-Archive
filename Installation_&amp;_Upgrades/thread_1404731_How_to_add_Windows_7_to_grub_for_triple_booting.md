---
title: "How to add Windows 7 to grub for triple booting"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by TheHH on 2010-02-11
I will like to triple boot Ubuntu, XP and Windows 7, but I already had Ubuntu and XP running on separate HDDs, Ubuntu was installed first, then I installed XP on a separate HDD (with the Ubuntu HDD disconnected), now I did the same for Windows 7, I disconnected all other HDDs (Ubuntu, XP and Data)and installed windows 7 on a separate HDD.

When I connected everything back(Ubuntu HDD, XP, Data HDDs and Windows 7 HDD, Windows 7 does not appear on grub boot menu and now Windows 7 does not boot up by it self.

Is there a way to simply add Windows 7 to Grub so I can have all 3 OS's on grub menu?
Can grub search HDDs to look for OSs to add to the menu?

Funny thing is the XP entry on grub appeared by it self, I've never edited grub to add XP on the booting menu, I was booting directly to XP by going into the BIOS and selecting the XP HDD as my booting drive instead of Ubuntu HDD, somehow XP was added to the grub booting menu.

Thanks in advance!

---

### Post by Sef on 2010-02-11
Which Ubuntu do you have?  If it is Koala, how did you install it?

---

### Post by northrup on 2010-02-11
There is a way: chainloading.  Basically, you should be able to point GRUB to the Windows 7 bootloader (WinLDR, right?), which is exactly what it does for your Windows XP installation, assuming you installed all three normally.  Just add an entry in the menu.lst file.  I don't remember how exactly to do it, though.

However, I would have just let the Windows 7 installer overwrite GRUB, download/burn the SuperGrub iso (Google it), and re-install GRUB as the primary bootloader.

[This page]("http://blog.lokonopa.com/grub-up-windows-7/") will likely be helpful, too.

---

### Post by kansasnoob on 2010-02-11
> **TheHH said:**
> I will like to triple boot Ubuntu, XP and Windows 7, but I already had Ubuntu and XP running on separate HDDs, Ubuntu was installed first, then I installed XP on a separate HDD (with the Ubuntu HDD disconnected), now I did the same for Windows 7, I disconnected all other HDDs (Ubuntu, XP and Data)and installed windows 7 on a separate HDD.

When I connected everything back(Ubuntu HDD, XP, Data HDDs and Windows 7 HDD, Windows 7 does not appear on grub boot menu and now Windows 7 does not boot up by it self.

Is there a way to simply add Windows 7 to Grub so I can have all 3 OS's on grub menu?
Can grub search HDDs to look for OSs to add to the menu?

Funny thing is the XP entry on grub appeared by it self, I've never edited grub to add XP on the booting menu, I was booting directly to XP by going into the BIOS and selecting the XP HDD as my booting drive instead of Ubuntu HDD, somehow XP was added to the grub booting menu.

Thanks in advance!

So we can get a better look please post the Output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2010-02-11
If Win7 is installed on its own physical drive, and if that drive does not boot by itself, then you may have written GRUB to the boot sector of that drive.

The script you were told to run will show us if that is the case.

---

