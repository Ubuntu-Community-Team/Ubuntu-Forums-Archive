---
title: "Windows Boot Manager won't appear"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by Clex19 on 2011-03-28
I have downloaded and run Wubi. I had it reboot my computer. It did, but the Windows Boot Manager didn't show up; it just went straight to Windows XP like a normal reboot. How do I get it to let me choose Ubuntu instead of Windows XP?

---

### Post by wilee-nilee on 2011-03-28
Check the time out of the windows loader.
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by Clex19 on 2011-03-28
@wilee-nilee
Okay, I made the timeout 30 seconds like it has in the link you provided. I tried rebooting my computer again, and it still didn't work.

---

### Post by wilee-nilee on 2011-03-28
If it was me and a fresh install I would probably remove it, but here are a couple of links. Notice the first does it look familiar, and did you do any thing outside the basic auto install. Such as build a partition, put the wubi in other then the C partition....etc.
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Did you download from here?
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
This installer guide is on the above links page.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Clex19 on 2011-03-28
I believe that I did everything correctly. I only did what Wubi told me to do, and I did get it from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer). This is the second fresh install I've tried, so I'm not so sure if another will work...Can you think of anything else?

---

### Post by wilee-nilee on 2011-03-28
Here is a megathread that may have information, there are two common problems.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I'm not real familiar with wubi so i have just suggested the problems I have seen others have.

---

### Post by Clex19 on 2011-03-28
Well, the two common problems in the megapost do not apply to me, because I'm able to boot Windows normally. I just can't get to Windows Boot Manager, where I can choose to use Ubuntu instead. My computer reboots as if Wubi was never used at all.

Thanks for trying. :)

---

### Post by bcbc on 2011-03-28
what are the contents of the boot.ini?

---

### Post by pasokon925 on 2011-05-15
> bcbc: what are the contents of the boot.ini?> pasokon925: "Computer: HP a1240n. OS: Windows XP SP3 with AVG Free Edition 2011"
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

---

### Post by bcbc on 2011-05-15
> **pasokon925 said:**
> [boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdconsYou're missing the entry for Ubuntu. I'm not sure what causes this, but it does seem to happen every now and then.

If you feel brave you can add the entry yourself. Best to backup C:\boot.ini first, and make sure you have a rescue disk (because if you mess it up Windows will sometimes not boot).

Add this to the bottom:
```
C:\wubildr.mbr = "Ubuntu"
```To edit, right click on My Computer, Properties, Advanced, Startup & Recovery settings, click on "Edit".

PS you also need to change the Timeout to 15 or 30.

---

### Post by pasokon925 on 2011-05-16
The installation via USB Drive for Windows XP works perfectly.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Thank you everyone.

Computer: HP a1240n
OS: Windows XP SP3 with AVG Free Edition 2011
[B]
[/B]

---

### Post by mooseman123 on 2011-05-16
> **bcbc said:**
> 
Add this to the bottom:
```
C:\wubildr.mbr = "Ubuntu"
```To edit, right click on My Computer, Properties, Advanced, Startup & Recovery settings, click on "Edit".

How could I do this on Windows 7?

Thanks!

---

### Post by bcbc on 2011-05-16
> **mooseman123 said:**
> How could I do this on Windows 7?

Thanks!

bcdedit or easyBCD. I haven't used easyBCD but I believe it would be simplest (however you need to install it). If you want to use the existing bcdedit command line tool refer to microsoft site for instructions or enter: bcdedit /? from an administrator command prompt.

For windows vista/7, the Wubi installation process normally adds an entry to the BCD that points at \ubuntu\winboot\wubildr.mbr on the installation 'drive' (not C:\wubildr.mbr).

---

### Post by mooseman123 on 2011-05-16
> **bcbc said:**
> bcdedit or easyBCD. I haven't used easyBCD but I believe it would be simplest (however you need to install it). If you want to use the existing bcdedit command line tool refer to microsoft site for instructions or enter: bcdedit /? from an administrator command prompt.

For windows vista/7, the Wubi installation process normally adds an entry to the BCD that points at \ubuntu\winboot\wubildr.mbr on the installation 'drive' (not C:\wubildr.mbr).

It was added and working, but somehow Windows reverted the mbr back to just Windows. Is there a way I can do it without a download?

---

### Post by bcbc on 2011-05-16
> **mooseman123 said:**
> It was added and working, but somehow Windows reverted the mbr back to just Windows. Is there a way I can do it without a download?

You can use bcdedit.exe. I'm not sure of the commands - I've used this to delete the entry, but not add it. I recommend using the /? help option I referenced above and/or referring to support.microsoft.com. 

Here's a link I found that looks reasonable: [http://wiki.birth-online.de/know-how/software/windows/install-wubildr](http://wiki.birth-online.de/know-how/software/windows/install-wubildr)
I haven't checked this link so please verify the commands before running

---

### Post by mooseman123 on 2011-05-17
Thanks for the link. It worked, and I can now un-install. I can't re-install, however. I'm over on the thread: [http://ubuntuforums.org/showthread.php?p=10826985]("http://ubuntuforums.org/showthread.php?p=10826985")

---

