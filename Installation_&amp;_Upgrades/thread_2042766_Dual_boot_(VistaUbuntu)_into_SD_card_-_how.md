---
title: "Dual boot (Vista/Ubuntu) into SD card - how?"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by michael5 on 2012-08-15
Hi,

I have installed Ubuntu 12 onto a computer which has had Vista only for a while, but now I want a dual boot so I can start migrating from Win to Ubuntu. Ubuntu was installed onto H: which is a 40 GB SD card. 

It works fine to boot into Vista, but if I choose Ubuntu from GRUB, then it won't boot into the Ubuntu installation on the SD card, but just jumps back to the GRUB menu immediately. 

It's probably because the BIOS doesn't allow booting into the SD card slot. 

However, is there some kind of work around so I can boot into Ubuntu on the SD card even though the BIOS doesn't recognize the SD card?

/Michael

---

### Post by darkod on 2012-08-15
I am confused with you mentioning H: because that's what windows calls ntfs partition and ubuntu doesn't install on ntfs. Are you talking about wubi inside windows? You need to be more precise because there is a difference, wubi ISN'T ubuntu.

I see no reason for any OS not to be able to be used on the SD card even if booting from it is not allowed by your computer. In that case you would have to have the bootloader on the internal hdd (there is one, right? ).

If from what ever reason you don't want the bootloader on the internal hdd, and the computer can't boot from the SD card, I don't see how it would work.

---

### Post by BrianBlaze on 2012-08-15
I have a question... is grub installed on your HDD or via the SD card? and why not install ubuntu locally? also do you know if your SD card is /dev/sda or /dev/sdb or whatever?

---

### Post by michael5 on 2012-08-15
> **darkod said:**
> I am confused with you mentioning H: because that's what windows calls ntfs partition and ubuntu doesn't install on ntfs. Are you talking about wubi inside windows? You need to be more precise because there is a difference, wubi ISN'T ubuntu.

I see no reason for any OS not to be able to be used on the SD card even if booting from it is not allowed by your computer. In that case you would have to have the bootloader on the internal hdd (there is one, right? ).

If from what ever reason you don't want the bootloader on the internal hdd, and the computer can't boot from the SD card, I don't see how it would work.

I used this one: 
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

According to these instructions: 
[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

The installer file is indeed wubi.exe but it should result in a dual boot as far as I can see when I read the above links. 

There's one internal SATA disk which has two partitions C:\ (Windows system plus program files) and D:\ (documents). E:\ is the DVD/RW drive and H:\ is the SD card. 

The computer's BIOS recognizes the SATA hard disk and the DVD/RW drive on boot. The SD card isn't recognized although it's being treated as a "Removable device" in Windows, which is a little bit strange because USB devices are discovered by the BIOS. 

Maybe it's the SD card that is just crappy?

/Michael

---

### Post by michael5 on 2012-08-15
> **BrianBlaze said:**
> I have a question... is grub installed on your HDD or via the SD card? and why not install ubuntu locally? also do you know if your SD card is /dev/sda or /dev/sdb or whatever?

Grub was installed on the HDD. I have reformatted the SD card so it's not mounted. 

I have thought about installing locally because I have 23 GB free space on D:\ (the hard disk). The only reason for hesitating is that then I will have to shrink that partition and divide it into two new ones and before doing that I would have to back up the data just in case it'd be lost during the shrink operation and right now I don't have any external media to use for an additional backup. 

Any suggestions?

---

### Post by darkod on 2012-08-15
Wubi inside windows is not a dual boot in the true meaning of the term. Best evidence for that is that you don't have any linux partitions on any hdd.

If selecting ubuntu from the grub (wubi) menu takes you to another grub, it might be that you have two grub installs. All of that would be much easier to troubleshoot if this was a real dual boot, which is another downside of wubi.

I don't work with wubi so I don't know details about it and I'm not sure I can help. In general, you would need to mount the virtual disk root.disk and take a look if it has another grub on it or not.

---

