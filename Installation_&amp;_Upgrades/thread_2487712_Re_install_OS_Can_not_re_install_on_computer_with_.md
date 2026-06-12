---
title: "Re install OS Can not re install on computer with 3 OS"
date: 2023-06-13
forum: Installation &amp; Upgrades
---

### Post by lizzie22 on 2023-06-13
New computer [64bit] loaded with 16.04 / 18.04 / 22.04 [all Ubuntu Mate]
Computer loaded EFI boot partition [never seen this before ?]
Later some how 18.04 would not load. Blank Screen

 OK just reinstall 18.04, can not !!!
Comes up with faults 
 0.100 392
 0.100 394
 0.100 397
 Does not load on "Try before loading" or "Install at once"

 Both set to with load CD first
 There is a key marked against EFI boot partition ? in Gparted

 Any help very much appreciated
 Les

---

### Post by Rubi1200 on 2023-06-13
From either a working install or live medium run the system info script in my signature and post the results here. Someone will come along and have advice on the next steps once the results are posted.

Thanks.

---

### Post by lizzie22 on 2023-06-13
Thanks Rubi1200,
I have pasted it to ? it is 38 pages long
My brain is getting a bit old for all this tec bits
Les

---

### Post by yancek on 2023-06-13
Are all 3 installs Legacy/MBR or are some UEFI and are they all on the same drive or different drives?  Try running boot repair from the site at the link below.  Make sure you select the 2nd option explained on the page and select to Create BootInfo Summary and do NOT try to make any change.  You will get a link to post here when boot repair finishes.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by MAFoElffen on 2023-06-14
Either / Or...

Both those scripts upload their reports to a pastebin, where you should copy down the URL that it uploaded to and post that URL in a post here for us to review.

For the 'system-info' script, instead of having to rerun it to re-upload the report, you can check the upload transmission log at the ~/system-info-link.log file to see the log of the upload, and the URL of where it uploaded to... The report is also written to ~/system-info.txt... and if over 19.5k, is optionally compressed into an archive file (~/system-info.tar.gz), to uploaded here as a backup, because 19.5k is the Forum limit for uploaded attachments.

The next system-info PPA Debian installer will include the man page files explaining the formats and more details on those files. I have them done. Just not uploaded there yet.

Both reports will show us what it is going on, and the layout of what is there. The 'system-info' script is about the hardware and the installed system settings. The 'boot-info' script will show us the grub and boot kinds of details. I authored the system-info script... Since I contribute to the boot-info script and help with it's testing, I kept most of those details of the grub and boot kinds of information out of the 'system-info' script, and tell the user "For more details, please run the 'boot-info' script report.

But, as I said, most people here can see what they are recommending solutions for, from those two reports. Both are tools for the members here to use as they please, to help them make informed recommendations.

---

### Post by oldfred on 2023-06-14
Unless you have extended support, 18.04 has expired.
So repositories are closed.

[https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/](https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/)

---

### Post by guiverc on 2023-06-14
> **lizzie22 said:**
> New computer [64bit] loaded with 16.04 / 18.04 / 22.04 [all Ubuntu Mate]
Computer loaded EFI boot partition [never seen this before ?]
Later some how 18.04 would not load. Blank Screen

 OK just reinstall 18.04, can not !!!
Comes up with faults 
 0.100 392
 0.100 394
 0.100 397
 Does not load on "Try before loading" or "Install at once"


I don't know your issue, but you do mention Ubuntu-MATE & a EFI boot partition (ESP).

The original 18.04 EFI keys were revoked, meaning the original media cannot be used to re-install Ubuntu 18.04 if Secure-EFI is used **unless** [newer 18.04.6 media is used]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") (see [https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/](https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/) ) however all *flavors* of Ubuntu 18.04 were already EOL, thus they didn't have newer media.

> Unlike previous point releases, 18.04.6 is a refresh of the amd64 and  arm64 installer media after the key revocation related to the BootHole  vulnerability, re-enabling their usage on Secure Boot enabled systems.

If you have Secure EFI enabled, that could be your issue. One fix is to *disable* that security, install, update system ... etc then you maybe able to re-enable that security, OR use later 18.04.6 media that has the newer keys & then add MATE,  though I'd not recommend that we're talking about an EOL OS, so really you should only consider that if used offline.

FYI:  How a machine will deal with the *revoked* keys of older 18.04 media is *firmware* specific, but it shouldn't boot is the only expected result with or without any error messages.  This may or may not be your issue though.  I don't know the messages you revealed.

---

### Post by lizzie22 on 2023-06-15
Thanks every one for helping.
 
 
 System-info = [https://paste.ubuntu.com/p/mMfFNXTXZd/](https://paste.ubuntu.com/p/mMfFNXTXZd/)
 
 
 Boot Info = Down loaded to disk, [with usb in tower] when run
 “Unable to find a medium containing live file system”
 
 
 All OS on one hard drive.
 Legacy / MBR [What's that ?] All ways had Grub, first time for UEFI
 
 
 Was Running 16.04 & 18.04 on old computer.
 [16.04 In case I wanted to install a new OS. 18.04 is Family tree [Gramps]. 22.04 Day to day use.
 
 
 **Are you having these problems?** 
- Error- "Cannot display this graphics mode" **NO**
There appears to be no Grub just UEFI
- No Grub Menu? Just blank screen
 
 
 On start up there is a tab for UEFI settings, but it just goes to the standard settings for the computer.

 On Gparted there is a grey key on UEFI partition, locked ? But can not see a way to unlock it ?
 
 
 There is clearly a lot of reading been supplied for me to read.
 
 
 Thank you
 Les

---

