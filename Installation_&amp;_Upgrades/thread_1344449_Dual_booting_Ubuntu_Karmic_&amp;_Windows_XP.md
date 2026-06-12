---
title: "Dual booting Ubuntu Karmic &amp; Windows XP"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by ddas4 on 2009-12-03
I have a Win XP & OpenSuse 11.2 installation currently on my Dell Inspiron 6000 (100 GB HDD, 2 GB RAM). I want to replace my OpenSuse 11.2 with Ubuntu 9.10. My Win XP and OpenSuse are installed on the same HDD but different partitions. Currently, OpenSuse bootloader shows both OpenSuse & Win XP and it works great.
 
I read on some forums that people have been experiencing problems with dual booting Windows & Ubuntu 9.10 and that the MBR gets overwritten by Ubuntu Karmic. [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic) also talks about it as below:
 
"Warning: Ubuntu Desktop edition installer no longer allows a custom installation of GRUB, and it now uses GRUB2, which allows very little customization. DO NOT USE the Karmic Koala Desktop edition if you use a boot partition, use multiple OS (more than 2), or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in Karmic Koala. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop)."
 
Just wanted to check whether given my specific case; is this is going to be a problem??

---

### Post by u.b.u.n.t.u on 2009-12-03
Perhaps delete the OpenSuse 11.2 partition, thereby totally removing it. You will have a HDD with no partitions, only XP that boots.

Ensure that the bootloader reflects this change.

Then install Ubuntu 9.10 creating a new partition and GRUB in the process.

---

### Post by ddas4 on 2009-12-03
Noob here. How do i delete the OpenSuse partition. Can i do that during the Ubuntu installation process ; by saying that 'create new partition / format / mount' on top of my existing openSuse root, boot, home, swap partitions?
 
Also, what you mean is i can go ahead without any risks of having my MBR overwritten? I am reading that finally i can only boot into the Ubuntu partition only and Windows will show a black screen.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **ddas4 said:**
> How do i delete the OpenSuse partition.

From within XP. I am not running XP so unfortunately I cannot provide details.

> **ddas4 said:**
> Can i do that during the Ubuntu installation process

You should be able to install Ubuntu 9.10 into the linux partition containing OpenSuse 11.2 as they both use the ext4 file system.

You would need to use GParted to do this but the easier method is what I have suggested, delete the partition and let Ubuntu 9.10 create a new one.

* Just checked what you wrote, but you updated it, so I will post this now. Feel welcome to ask follow up questions.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **ddas4 said:**
> Also, what you mean is i can go ahead without any risks of having my MBR overwritten? I am reading that finally i can only boot into the Ubuntu partition only and Windows will show a black screen.

From within XP you can:

1. Create, resize, format, delete partitions.
2. Modify the boot loader.

I am using Windows 7 and haven't used XP since Vista first came out so I am unable to assist you with the details. However this information should be enough to give you a good understanding of the theory and how to proceed to get the needed detailed information.

You want to find information pertinent to the two points I enumerated above.

---

### Post by ddas4 on 2009-12-03
Thanks u.b.u.n.t.u. I will try that today through my Win XP ; but currently my Windows is unable to see my OpenSuse partition. Do you think i still will be able to delete this partition ?

---

### Post by u.b.u.n.t.u on 2009-12-03
> **ddas4 said:**
> Thanks u.b.u.n.t.u. I will try that today through my Win XP ; but currently my Windows is unable to see my OpenSuse partition. Do you think i still will be able to delete this partition ?

Yes.

I do not have XP so I cannot assist with the details.

Maybe start a new thread here with the title along the lines of:

"From XP how to delete linux partiton?"

Then:

"I have a HDD with XP as the primary operating system and OpenSuse 11.2 on a partition. They are configured for dual boot.

I wish to maintain XP, delete the linux partition, so that the entire HDD is NTFS with XP as the sole operating system.

I want to ensure that the boot loader correctly loads XP.

In essence, I want to replace OpenSuse 11.2 with Ubuntu 9.10.

Please advise and thank you."

Something like that perhaps.

---

### Post by Ginsu543 on 2009-12-03
You will be able to partition your linux partition in Windows if you use a partitioning program like Partition Magic. However, I don't think there is a way for Windows to recognize a linux partition natively.

---

### Post by ddas4 on 2009-12-04
I have not attempted this yet but here are a couple of good tutorials on how to delete the Linux partitions:
 
[http://www.softwaretipsandtricks.com/forum/windows-xp/22183-how-would-i-remove-suse-linux-dual-boot-system-xp.html](http://www.softwaretipsandtricks.com/forum/windows-xp/22183-how-would-i-remove-suse-linux-dual-boot-system-xp.html)
 
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)
 
If things don't go too well, i will probably resort to a new thread. But for now my question stands answered in a way that i can go ahead and switch over to Ubuntu without worrying about my MBR being overwritten.

---

### Post by u.b.u.n.t.u on 2009-12-04
ddas4, sounds logical and like you are on the right track.

Just the obvious, make sure all important data is backup up and verified on an external medium.

---

### Post by Jc.in.van on 2009-12-04
> **ddas4 said:**
> Noob here. How do i delete the OpenSuse partition. Can i do that during the Ubuntu installation process ; by saying that 'create new partition / format / mount' on top of my existing openSuse root, boot, home, swap partitions?
 
Also, what you mean is i can go ahead without any risks of having my MBR overwritten? I am reading that finally i can only boot into the Ubuntu partition only and Windows will show a black screen.

I installed Ubuntu 9.10 from within Win XP Media Edition to a different partition (simply formatted (fat32 or NTFS).  I used PowerISO to mount the Ubuntu live cd image and install using Wubi.  At boot MBR was intact 1st acronis loader then boot loader with windows as default and ubuntu is arrow down.  both work just fine (except for unrelated errors with Ubuntu desktop).  I have not been able to install from USB Media so far.

---

