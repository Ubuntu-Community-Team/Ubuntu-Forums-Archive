---
title: "Recovering a hard drive that ran ubuntu 10.04"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by diomedestydeus on 2011-11-12
Dear Ubuntu Forums,
I had an older PC that I ran Ubuntu 10.04 on, I used it as a personal FTP server as well as a media center for my TV, it was really pretty spiff.  Unfortunately the motherboard doesn't seem to post right now, so I'm working on figuring that out, but here's my problem:

* I have important data on that hard drive, I popped it out and tossed it into my other box which is running windows 7.

* Neither Windows 7, nor any of the free utilities I have seem to be able to read that drive (DiskInternals linux reader, explore2fs... I think I may have used ext4? that may be my issue)

* I tried setting that drive as my primary drive on boot from BIOS, but it just sits there 

* I created a bootable usb drive with ubuntu 10.04 live and using that, could mount my old hard drive

* Most of the contents seemed to require root access... but once I setup a password, I could see and confirm all of my old content is on that drive and looks good (score)

My question:
How can I just boot from that drive?  I'm not totally clear why just changing my bios didn't solve that.  If I need to reinstall to that drive, I don't want to lose my data, will a reinstall wipe out that data?  Also, I needed root access to view some of my files... does that mean that they're stored in some kind of encrypted state?

Sorry to be lengthy, any input would be greatly appreciated.  Ideally, I'd just like to be able to pick my OS on boot and work on the linux drive from time to time until I fix my other PC, but barring that I really need my data off.

---

### Post by raja.genupula on 2011-11-13
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu-rescue-remix.org/About](http://ubuntu-rescue-remix.org/About)

---

### Post by dandnsmith on 2011-11-13
> * Neither Windows 7, nor any of the free utilities I have seem to be able to read that drive (DiskInternals linux reader, explore2fs... I think I may have used ext4? that may be my issue)

* I tried setting that drive as my primary drive on boot from BIOS, but it just sits thereY
You haven't said whether the drives are PATA or SATA.

> * I created a bootable usb drive with ubuntu 10.04 live and using that, could mount my old hard drive

* Most of the contents seemed to require root access... but once I setup a password, I could see and confirm all of my old content is on that drive and looks good (score)
OK - that's a good start, and rules out encryption of files.

> How can I just boot from that drive?  I'm not totally clear why just changing my bios didn't solve that.  If I need to reinstall to that drive, I don't want to lose my data, will a reinstall wipe out that data?  Also, I needed root access to view some of my files... does that mean that they're stored in some kind of encrypted state?
You should be able to configure the BIOS appropriately, but some are rather tricky, and you've given no details to help us.
A re-install would probably lose your data, unless you have it in a separate partition - so you would need to save it (USB stick?) first.
The needing of root access to view some files probably reflects the ownership and access permissions on the files - that should be a minor worry at this stage.

---

### Post by darkod on 2011-11-13
From ubuntu live mode you can run the bootinfoscript (the link in my signature) and that will tell you much more details. If you want you can post the results here, please follow the instructions and post in code tags.

The main thing to see is if your disk still has the bootloader.

Also you can try disconnecting all other disks and leave just that one. It has to boot from it, unless the boot process is broken.

---

### Post by diomedestydeus on 2011-11-13
Thank you for all of the replies, I'm sorry I frustrated some of you by providing insufficient information.

It is a SATA drive for the record.

I didn't realize since I've never dual booted that windows couldn't read my ext4 drive but ubuntu was more than happy to read/write to my ntfs drive.  I copied all of the files off onto my other drive and then imaged my drive and copied that too in case I forget something in the short term.

I tried running the suggested boot_info_script but I got a syntax error around like 350 (I apologize, the ubuntu live disk doesn't recognize my wireless card so I seem to be without the internet on that side, so I couldn't google it).  

For the moment, I'm happy that my data is safe, thank you for the replies.

---

