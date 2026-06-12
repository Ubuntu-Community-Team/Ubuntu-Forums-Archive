---
title: "Trouble with grub boot (Windows 8.1/Ubuntu 14.04)"
date: 2015-06-26
forum: Installation &amp; Upgrades
---

### Post by archie6 on 2015-06-26
Hi everybody! There's a problem with my grub..
I've already tried to update grub and Boot-Repair ([http://paste.ubuntu.com/11777106/](http://paste.ubuntu.com/11777106/)) but nothing worked for me. Can anyone help?
Maybe this additional screen of my Gparted will help.

---

### Post by ajgreeny on 2015-06-26
You say you have a grub problem but don't actually tell us what the problem is.

More info is needed if we are to help you properly.
Can you boot to one OS only, or both, and if only one, which is it?

---

### Post by cariboo on 2015-06-26
As ajgreeny asked, can you boot to any OS, from your attachment, it seems your hard drive is missing several partitions. This is what gparted looks like on my laptop that dual boots wilt and Windows 8.1

[[img]http://i.imgur.com/CBXsuqLm.png[/img]](http://imgur.com/CBXsuqL)

My system if fairly new and uses UEFI, in order to boot wily, I need to go into the system bootloader, and select Ubuntu from the list, before I see the grub screen.

---

### Post by archie6 on 2015-06-27
I can boot both of them, but before booting I have this messages:
1. If Ubuntu: "error: attempt to read or write outside of disk 'hd0'. Press any key to continue..."
2. If Windows: "setting partition type to 0x7.
error: failure writing sector 0x0 to 'hd0'. Press any key to continue..."

---

### Post by archie6 on 2015-06-28
> **ajgreeny said:**
> You say you have a grub problem but don't actually tell us what the problem is.

More info is needed if we are to help you properly.
Can you boot to one OS only, or both, and if only one, which is it?
So, do you have any ideas?

---

### Post by oldfred on 2015-06-28
Boot-Repair's summary report says partition type is 07.
But Windows also keeps various bits of vital info in the NTFS partition boot sector. That can be updated with chkdsk, so it may be worthwhile to run chkdsk on all 3 NTFS partitions you have.

 Chkdsk
[http://technet.microsoft.com/en-us/library/cc730714.aspx](http://technet.microsoft.com/en-us/library/cc730714.aspx)

Newer version has /b parameter:

 Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

Since you have two drives, often better to just have Windows on one drive with its own boot loader in the MBR, so it can boot without grub.
And then have Ubuntu & grub on sdb drive, so it can boot without sda. 
And then set BIOS to boot from sdb drive.
That way each system has its own drive. And then you can use the Windows drive to backup some Ubuntu info, and Ubuntu drive to backup some Windows data.

---

