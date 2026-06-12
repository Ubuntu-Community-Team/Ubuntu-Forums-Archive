---
title: "Manual install has no option for encryption"
date: 2024-10-09
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2024-10-09
Installing on a 1TB SDD with Windows already installed.
I created 500GB free space using GParted to install Ubuntu on.
I am reliably informed the system is GTP.
When I use the installer in manual mode, there's no option to encrypt the / partition.
Is this normal?
Have I missed something?

---

### Post by yancek on 2024-10-09
I don't use encryption but from what I have read, you need to encrypt the full disk during install and if you have windows encrypted, there will be problems.  Encrypting the /home partition after install might work, see the link below.

[https://askubuntu.com/questions/366749/enable-disk-encryption-after-installation](https://askubuntu.com/questions/366749/enable-disk-encryption-after-installation)

---

### Post by Gordonbp531 on 2024-10-09
> **yancek said:**
> I don't use encryption but from what I have read, you need to encrypt the full disk during install and if you have windows encrypted, there will be problems.  Encrypting the /home partition after install might work, see the link below.

[https://askubuntu.com/questions/366749/enable-disk-encryption-after-installation](https://askubuntu.com/questions/366749/enable-disk-encryption-after-installation)

Thanks for that - there's only an option to encrypt if the "erase the whole disk" option is selected, and no option to encrypt the Home directoty on the new user account. 
Windows is not encrypted.
Ihad been informed that as my SDD is GPT, then there should be no problem in creating a separate install as if it was on a separate disk...

---

### Post by yancek on 2024-10-09
The link below explains creating an encrypted system using the Something Else/Manual option.  This is for 20.04 and I don't use 24.04 so I don't know if the options are different.  I see you do not mention which Ubuntu you are using which would be useful for you to get help.

[https://maciej-sady.medium.com/the-easiest-way-to-install-ubuntu-on-an-encrypted-partition-a882320dd6bb](https://maciej-sady.medium.com/the-easiest-way-to-install-ubuntu-on-an-encrypted-partition-a882320dd6bb)

As I said, I don't use encryption and would suggest that if you try to use this, you keep detailed notes of the steps you took and the results including any warning/error messages you might receive. 

> Ihad been informed that as my SDD is GPT, then there should be no  problem in creating a separate install as if it was on a separate  disk... 		 

Installing Ubuntu on the same disk with another OS be it windows or Linux should not be a problem and hasn't been for decades whether it is GPT or not.

---

### Post by TheFu on 2024-10-09
There has never been any easy, checkbox, method to install Ubuntu with Encryption for the OS without wiping the disk.  I've been using LUKS encryption with Ubuntu since 2012.

A few people have tried to setup it up manually. I looked into doing that back in 2016 (not for dual boot) and after seeing 10 pages of "how-to" steps decided it wasn't worth the hassle to me and that it probably wouldn't support OS upgrades at the next release anyway.

On a practical side, if you choose to run multiple OSes on the same computer, I'd urge you to pick one to run on the physical hardware and have the other setup to run inside a virtual machine. Then only 1 OS would deal with the booting and complications that strong encryption demands from that.  It also avoids the breakage that having 2 OSes trying to share the boot areas on a disk seem to run into every year when 1 will take over the booting and prevent the other OS from working.  Just a few months ago, MSFT caused this sort of issue for millions of computers.

---

### Post by donald187 on 2024-10-10
The installer has changed for 24.04.  For 22.04 and before you used to be able to encrypt a single partition using LUKS from manual partitioning.  I've done it many times.  That option is gone in the 24.04 installer.  See this post:

[https://ubuntuforums.org/showthread.php?t=2498966&p=14196370#post14196370](https://ubuntuforums.org/showthread.php?t=2498966&p=14196370#post14196370)

It may be possible to do a LUKS encryption on a partition using terminal commands from the Try Ubuntu selection, open it, and then install Ubuntu onto the opened partition but I don't know if the 24.04 installer will support this.  I could muddle through it on my own but I'm not good enough to tell someone else how to do it.

---

### Post by Gordonbp531 on 2024-10-10
Apparently there is a solution here:
[https://www.mikekasberg.com/blog/2024/05/20/dual-boot-ubuntu-24-04-and-windows-with-encryption.html]("https://www.mikekasberg.com/blog/2024/05/20/dual-boot-ubuntu-24-04-and-windows-with-encryption.html")
However I've now got another issue in that the Ubuntu installer (24.04) is not seeing the Windows install, even though the SDD is unencrypted and Fast startup is disabled.....grrrrr!

---

### Post by TheFu on 2024-10-10
It isn't hard to encrypt a non-OS partition with LUKS.  There are lots of how-tos for accomplishing that.  It is just the OS where it becomes more complex. [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) is one.  Because it is all handled without a GUI, I can't see why it wouldn't work under 24.04.

The 24.04 installer added a few features and dropped some that had been possible for over 10 yrs.

---

### Post by yancek on 2024-10-10
>  However I've now got another issue in that the Ubuntu installer (24.04) is not seeing the Windows install

You don't indicate which version you are using but if it is a newer one (8 or newer) the default is to use hibernation so the system appears to boot faster.  Mounting a hibernated system can cause data loss which is why Linux does not attempt to mount windows partitions.  When you booted the Ubuntu USB previously, were you able to view the partitions?  When you select the Try Ubuntu option and open a terminal, do you see correct output including the windows partitions from the commands below?  

```
sudo fdisk -l
sudo parted -l
```

Do you have hibernation off in the windows power settings?  Do you see the unallocated space on the drive?

---

### Post by Gordonbp531 on 2024-10-11
The solution link I posted above worked after solving the non seeing of the Windows install...

---

### Post by TheFu on 2024-10-11
Could you please post the output from the 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
command so we can see the resulting layout?

---

