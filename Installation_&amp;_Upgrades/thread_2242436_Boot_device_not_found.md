---
title: "Boot device not found"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by rosswmcgee on 2014-09-01
I recently bought an HP Pavilion slim line desktop computer with windows 8.1. with AMD64 1tb hd  and 6gb ram

I wanted to get rid of windows and install mint Ubuntu 14.04lts. I have done this many times on other computers, but this time this is what I get after install.

Boot  device not found, please install an operating system on your hard disk no boot disk or disk has failed. Or sometimes I get this:

[http://www.hp.com/go/techcenter/startup](http://www.hp.com/go/techcenter/startup)

I ran the diagnostics disk is fine. I am at a loss as to what to do?

---

### Post by gdesilva on 2014-09-01
Did you follow the guidelines for uefi installation? If not check out this...[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by fantab on 2014-09-02
Windows 8 lapies have 'SecureBoot' and 'Fast Startup' features, you need to disable those to install any OS including Ubuntu. 
Go through the url link posted above... 

Boot with Ubuntu Live and install & run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")... don't repair anything, just create the *Bootinfo Summary*, note down the url link to the file and paste it here.

---

### Post by hg-knight on 2014-09-02
wild shot but had a similar problem with any live boot media i tried to install.
Turn out as i used a windows desktop to install the OS to memory stick, the memory stick kept formatting to NTFS.
formatted it to fat32 and all worked ok.
like  i said a wild shot but

---

### Post by rosswmcgee on 2014-09-02
returned computer, will bought computer with older style bios, ubuntu installed fine. shy away from the windows 8 computers with the new type bios that blocks linux.

---

