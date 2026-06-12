---
title: "Ubuntu Vs XP on Grub2 not recognising drive after &quot;boot Repair&quot;"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by Midgetprawn on 2012-12-07
I have been redirected from
[http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub2&page=67]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub2&page=67")
Grub continues to say the drive cannot be found

Boot Repair URL is [http://paste.ubuntu.com/1417204/]("http://paste.ubuntu.com/1417204/")

Thanks in advance

---

### Post by oldfred on 2012-12-07
You are showing two XP installs.

The install in sda2 is missing boot.ini, so I do not think it was bootable and grub will not offer to boot it as it does not have all its boot files.

The install in sdb1 has a boot.ini. But Windows is like old versions of Ubuntu before using UUIDs in that it is hard coded to boot from a device. Or your boot.ini is wrong.

You can change drive order so sdb becomes sda and that will "fix" boot.ini. Physically change ports drives are plugged in on motherboard. Ubuntu uses UUIDs so it will still boot but you still have to run sudo update-grub. May still have to change disk(1) to disk(0).
 Or manually edit boot.ini so it says it is rdisk(1) not rdisk(0).
```
[boot loader]
timeout=30
default=multi(0)disk(1)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(1)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```If editing be careful to save in Windows format not Linux format. Line endings are different.
       If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

---

### Post by Midgetprawn on 2012-12-07
Thanks OldFred
I tried what you have suggested but I still get the message that the drive is not recognised. Any suggestions why GAG an get it to boot? SuperGRUB  has failed to boot either. Swapping drives has made no difference.
Yes it was an older copy of XP on Sda. I had to reinstall xp as it crashed on me I keep all my files in it and the new install is the shell.

---

### Post by oldfred on 2012-12-07
If both changing drive order & changing rdisk could continue to have issues. It just has to be consistent.
Often other issue is chkdsk. Windows does not like change so a chkdsk may repair things.
If you want to auto fix boot.ini you can run the repairs from a Windows XP install disk.

       XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.
# is comment do not type.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by Midgetprawn on 2012-12-09
Well I tried every trick in the book as you suggested but I was running in circles.
Fixmbr got nowhere and the "no partition message persisted"
I ended up reinstalling windows on another partition and modifying the boot.ini as suggested to redirect to the sdb1 location. This reset the mbr. I then used a live CD of Ubuntu to reinstall Grub2 and ran update-grub once i was back in.
Hey presto I have Ubuntu and XP within the Grub menu and it links up again.
Thanks again for your advice.):P

---

