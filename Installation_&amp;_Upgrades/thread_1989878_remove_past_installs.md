---
title: "remove past installs"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by mr hippie on 2012-05-28
I messed up...  I was running 11.10 from wubi, I then installed 12.04 beside windows from usb.  Once I rebooted after install, Windows 7 did not start. so I put in my windows recovery cd.  Then my I no longer could find my ubuntu.  So no neither ubuntu's were working.  

I have now used gparted and installed 12.04 on the new partition. 

So, is there a way to delete my old ubuntu (wubi and side by side) via the file manager or live usb?

---

### Post by wilee-nilee on 2012-05-28
> **mr hippie said:**
> I messed up...  I was running 11.10 from wubi, I then installed 12.04 beside windows from usb.  Once I rebooted after install, Windows 7 did not start. so I put in my windows recovery cd.  Then my I no longer could find my ubuntu.  So no neither ubuntu's were working.  

I have now used gparted and installed 12.04 on the new partition. 

So, is there a way to delete my old ubuntu (wubi and side by side) via the file manager or live usb?

A screenshot of the HD would help using gparted, use a live cd or install it in ubuntu, and take a screenshot and post it.

Identify exactly what you want gone and what stays.

---

### Post by jadtech on 2012-05-29
> **wilee-nilee said:**
> A screenshot of the HD would help using gparted, use a live cd or install it in ubuntu, and take a screenshot and post it.

Identify exactly what you want gone and what stays.

wubi can be removed from remove programs in windows then there isa line in windows boot INI file that needs quoting out  or removed completely ..

---

### Post by mr hippie on 2012-05-29
Thanks, I have it removed from programs... But I think the content is still hiding.

---

### Post by wilee-nilee on 2012-05-29
> **jadtech said:**
> wubi can be removed from remove programs in windows then there isa line in windows boot INI file that needs quoting out  or removed completely ..

Boot ini is XP this is W7.

This is what XP would look like in a bootscript

File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   **/boot.ini** /ntldr /NTDETECT.COM

This is W7

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by wilee-nilee on 2012-05-29
> **mr hippie said:**
> Thanks, I have it removed from programs... But I think the content is still hiding.

So you are getting the windows boot menu and Ubuntu is still there? I am a having a problem getting to exactly what is happening, and what you want removed is all.

---

### Post by mr hippie on 2012-05-29
Sorry, I am so confused my self.  I just want to delete all the old ubuntu stuff (since old grub was broken...by me) and everything I did to fix made it worse.  

My latest install works great on a partitioned drive.   I just want to clean up the hard drive, so less confusion in the future.  So I just want to delete my side-by-side install and wubi install files via ssh or...?


Thanks,
Brian

---

