---
title: "Want to Upgrade but Used Desktop ISO"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by 'Gator on 2010-06-14
Confused by the different documentation Web pages, I tried to UPGRADE from Ubuntu 8.04 to 10.04 using the DESKTOP .iso download file instead of the ALTERNATE one.  I discovered that the desktop file does not permit an upgrade option, only one for a new, fresh installlation.

When I tried to reboot to 8.04, which clearly is still on my Linux hard drive, I discovered that I could only boot Ubuntu from the desktop installation CD.

My system multiboots Ubuntu and Windows XP Pro.  I have downloaded the alternate Ubuntu 10.04 installation file to my NTFS file system and used ISO Recorder to transfer the ISO image to a CD.  I have confirmed the MD5 checksum, but have not yet examined the CD for files and directories like those I've seen on the desktop CDs.

While clearing temp files and folders from my XP file system, I noticed that a folder had been placed in my temp directory.  Its contents clearly indicate that it was related to Linux.

Is there an equivalent set of files and directories in my Linux file system that's keeping me from booting to Ubuntu 8.04, or would interfere with an upgrade from 8.04 to 10.04?  Is there a simple way to "back out of" the 10.04 installation as another, new system (instead of upgrading 8.04 to 10.04)?

I'm not familiar with gParted; the layout of partitions, directories, and files in the boot redirection sequence; or the differences between grub 0.97 and 1.98.  I could try to install 10.04 in addition to 8.04, but I'd lose the upgrade advantages of absorbing my current file system into the 10.04 installation; and I'd almost certainly do something wrong that would take forever to fix.

Can you help me?

---

### Post by zvacet on 2010-06-16
Can you boot in Windows?I meaqn does grub work or not?If not reinstall it with your HARDY live CD following [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).After that boot in Ubuntu and when it is running put Lucid alternate CD in drive.Ubuntu should recognize disc and ask you if you want to upgrade.If upgrade message doesn´t show type in terminal

```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by 'Gator on 2010-07-02
> **zvacet said:**
> Can you boot in Windows?I meaqn does grub work or not?If not reinstall it with your HARDY live CD following [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).After that boot in Ubuntu and when it is running put Lucid alternate CD in drive.Ubuntu should recognize disc and ask you if you want to upgrade.If upgrade message doesn´t show type in terminal

```
gksu "sh /cdrom/cdromupgrade"
```
zvacet,

Sorry about the delay in responding to you.  You see, I lost the ability to boot into any sane state of Windows just after I received your message.  I'm still recovering.  I think the latest release of Firefox for Windows is the culprit.

grub only works for ubuntu if it sees the Desktop CD.  I'll take your suggestion about reinstalling grub and let you know what happens.

Thanks,

--'Gator sends

---

### Post by 'Gator on 2010-07-04
zvacet,

I find that I don't have a Hardy CD of any sort.  I seem to remember that I upgraded from a previous version (7.10?) via the Update Manager.

I tried using the 9.10 CD, but every method listed in the 224351 thread failed.

Perhaps I don't understand what a "live CD" is.  I've downloaded both the "...-desktop-..." and the "...-alternate-..." files to my desktops, then used the default ISO processor in Lucid (while running Lucid from the desktop CD) and the current ISO processor in Windows XP Pro to burn CDs.  Do the procedures produce a live CD?

I know that I must create mount points in my Hardy file system, since (if I'm using the term "live" correctly) the live boots create a read-only file system mount for the existing Hardy directory structure.  I just keep getting errors in the last command before "quit".

I'm thoroughly confused about what's going wrong.  I'll rerun the command sequence and send you the exact error message if that will help you help me.

Note: thread ...24113 seems redundant to this thread.  Also, I just noticed the reference to the grub2 guide in thread ...1195275 in thread ...224351 that you referred me to.  I'll research that now.

--'Gator sends

---

