---
title: "Wine installation question"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-07-28
Before attempting to install Wine (using Synaptics), I read the [Wine-HOWTO ]("http://www.witch.westfalen.de/Wine-HOWTO/ch-installation.html")to make sure that I install it properly the first time.

The first thing I noticed was the statement: > Note: There is a section  called _Wine Without a Windows Partition_. If you have no Windows partition, you should read it first and return here later.

Now... I read that section but it is unclear to me what it means by "Wine Without a Windows Partition": I do have a Windows XP installation on a different partition, but it is NTFS and thus mountable as **read-only**. 

So, if it is read-only where is wine going to be installed?

If Wine is going to be installed on the Linux partition (where other Ubuntu binaries and libraries are), then why a Windows partition is necessary for Wine?

I need to understand the reason for the "requirement for a Windows partition" so that I can better plan the installation/configuration: Ideally, I would like to install Windows applications/executables on XP's NTFS partition only. However, since it is read-only for Linux, I will have to do that while booted to Windows XP. That is fine, AFAIAC, but is it possible? Does this make sense?

Thanks!
Alex

---

### Post by dtfinch on 2006-07-29
I've never used Wine in conjunction with a real Windows partition, or even pondered the idea. That howto might be a little outdated.

When you install Wine, and run it for the first time, it creates a directory called ".wine" in your home directory, with a "drive_c" directory under that. If you want to map other drives, you can do so by creating symbolic links to them in the "dosdevices" directory.

---

### Post by collgra on 2006-11-14
This isn't a help on this same problem but, I have a related question. I installed wine by loading it into the synaptic package manager then installing it with the add remove console. It seemed to install correctly but I can't find installed evidence of wine in any of the program applications lists or file system. 

Windows programs seem to install normally but result in the same situation. Not in program lists and not installed.

This is frustrating, every linux release I have ever looked was like this cryptic and frustrating. 

Can anyone help?

Gary

---

