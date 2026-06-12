---
title: "Delete ubuntu folder under C after installation?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by gepolv on 2011-02-27
Hi, all,
I am a newbie to ubuntu. I just have a simple question:
I used wubi to install ubuntu and the installation procedure was perfect. One problem arose after installation, the c:/ubuntu becomes almost 30G!!! Can I delete it?

Thanks.

Gepo

---

### Post by gepolv on 2011-02-28
Any help? thanks.

---

### Post by oldos2er on 2011-02-28
Are you asking how to remove Wubi? [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by bcbc on 2011-02-28
> **gepolv said:**
> Hi, all,
I am a newbie to ubuntu. I just have a simple question:
I used wubi to install ubuntu and the installation procedure was perfect. One problem arose after installation, the c:/ubuntu becomes almost 30G!!! Can I delete it?

Thanks.

Gepo
NO!

Wubi installs Ubuntu on a virtual disk: c:\ubuntu\disks\root.disk (which if you look will be about 29GB). If you delete that it will delete Ubuntu.
Even though you're only using perhaps 3GB on Ubuntu, the virtual disk is fixed in size and is the total space available to you to use in Ubuntu. Think of it as a partition, but without the hassle of partitioning.

If you want to uninstall Ubuntu, go to the Control Panel and remove it from there.

---

### Post by Scootty83 on 2011-08-30
I recently cloned my 64GB SSD and upgraded to a 128GB SSD on my Asus EP121 which runs Windows 7. Before I cloned it, though, I had done a Wubi install of Ubuntu. After the cloning I discovered that Ubuntu was not cloned along with it, but the boot loader still gave me the option to boot into Ubuntu or Windows 7 (I attempted to boot into Ubuntu, but it did not work). However, the C:\Ubuntu , C:\wubildr and  C:\wubildr (zune streaming file) are still there. Can I just drag these to the trash can and empty it? it is taking up almost 7GB. I have tried doing the unistall option in the Windows Add/Remove Programs as well as the uninstaller in the Ubuntu folder, but both give this error:
 
"An error occurred:
 
Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete
{d6f4a23c-1429-11e0-8810-86ab205b7778} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.
The system cannot find the file specified.
 
>>stdout=
 
For more information, please see the log file:".....
 
Also, I installed a different Linux Distro (Linux Mint 11) via a live USB just for fun (I am new to Linux and am wanting to check out some other distros before committing to one). Would it be affected if I just deleted the said "C:\" directories above?
 
Thanks in advanced.

---

### Post by bcbc on 2011-08-31
Scootty83,

Refer to the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F")

If you installed Mint directly (not with Mint4win) it won't be affected. If you installed mint4win (Mint's equivalent to Wubi), I think it also uses wubildr and wubildr.mbr so don't delete these.

PS create a new thread next time.

---

### Post by Scootty83 on 2011-08-31
Thanks for the quick reply.
 
I refered to the Wubi Guide before posting my question and saw how to uninstall Wubi, but it did not adress my question I posted here.
 
I installed via a Live USB, not Mint4win, so all is good then. I deleted the files, and all seems to be running just fine.
 
I posted here instead of a new thread because the original poster's question was if it is okay to delete c:\Ubuntu which was basically what I was asking with a little twist, so I figured this was the correct place to post my question. But, if my logic is flawed, next time I will just create a new thread.
 
Thanks again for you help.

---

### Post by bcbc on 2011-08-31
They refer to it as necromancing ;) (reviving old threads), but I see your point.

Yes - you can manually delete those pieces, but you indicated that there was an Ubuntu entry still in the Windows boot loader. For that you need to run bcdedit or install easyBCD. (Personally I'd use bcdedit - never tried easyBCD - but I understand easyBCD is user friendly). Also any registry entries will have to be done separately.

Good luck.

---

