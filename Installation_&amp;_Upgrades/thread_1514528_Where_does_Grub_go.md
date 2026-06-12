---
title: "Where does Grub go?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by God Dammit on 2010-06-21
I'm trying to dual boot between 64-bit Windows 7 and Ubuntu 10.04. I just have one question. Should I install Grub in the EFI system partition (/dev/sda1) or is there some place else I should be installing it?

---

### Post by ajgreeny on 2010-06-21
I'm not totally sure about Windows 7, but I have always put grub on the MBR of the first disk and never had a problem with it.  I would add, however, that this was with WinXP and Vista, and I think Win 7 may be different in so many ways, but nevertheless, I don't think grub needs to go on a partition but onto the MBR, ie in your case, just /dev/sda (with no number).

Wait for others to answer as well, but that is what I have always done, and I will be surprised if things have changed greatly.

I spite of some users unhappiness with grub 2, I have found it to be extremely good, once you realise that it has changed, and everything is now done differently from legacy grub.  It is also I believe much better a bootloader than some of the alternatives around, and it will manage windows very well, in my experience.

---

### Post by wojox on 2010-06-21
Same here, I install it on MBR

---

### Post by wilee-nilee on 2010-06-21
I looked up EFI and found conflicting info.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
I don't have a clue.

---

### Post by God Dammit on 2010-06-21
The MBR on my hard disk simply tells the computer where to find the EFI system partition. If I install Grub at /dev/sda I won't be able to boot Windows 7. EFI is not specific to Windows. Most Linux distributions use it as well. I'm surprised that Ubuntu doesn't seem to know what EFI is considering most motherboards use it to boot the computer.

---

### Post by ajgreeny on 2010-06-21
> **God Dammit said:**
>  I'm surprised that Ubuntu doesn't seem to know what EFI is considering most motherboards use it to boot the computer.
I have to admit that ubuntu is not the only thing that doesn't know what EFI is; I had to google it to find out a bit more.

It's the first time I have ever heard of it, or seen anything written or asked about it, on this or any other computer website.

---

### Post by darkod on 2010-06-21
Look here if it can help:
[http://ubuntuforums.org/showthread.php?t=1466252](http://ubuntuforums.org/showthread.php?t=1466252)

Post #22 seems to explain how to install 10.04 with OSX and EFI.

---

### Post by God Dammit on 2010-06-22
I'm not using a Mac. My PC has an Intel DP43TF motherboard which uses EFI.

---

### Post by darkod on 2010-06-22
> **God Dammit said:**
> I'm not using a Mac. My PC has an Intel DP43TF motherboard which uses EFI.

Most EFI and grub2 tutorials seem to be written from Mac perspective.

I guess you can put grub2 to the ubuntu root partition but how do you tell EFI to boot from it I have no clue. Can't the MB manual help?

---

### Post by wilee-nilee on 2010-06-22
I suspect this EFI partition is a add on from the manufacturer of the computer. I would call them and see if a OEM disc set installs without the EFI and reinstall and get rid of it, since it will be nothing but trouble. The best at this on the forum have no clue about it and the web is conflicting about it's use, and sporadic in information. I have found links that say that Linux can't even use it, probably not true, but a indicator of looking for a more stable setup. Call the manufacturer and get more information at the least

---

### Post by darkod on 2010-06-22
> **wilee-nilee said:**
> I suspect this EFI partition is a add on from the manufacturer of the computer. I would call them and see if a OEM disc set installs without the EFI and reinstall and get rid of it, since it will be nothing but trouble. The best at this on the forum have no clue about it and the web is conflicting about it's use, and sporadic in information. I have found links that say that Linux can't even use it, probably not true, but a indicator of looking for a more stable setup. Call the manufacturer and get more information at the least

I didn't want to go that far, but I agree.
It's time to talk to the manufacturer if your machine came with it.
If you assembled it and decided to use EFI, then you should have searched for information how to add ubuntu to EFI before you started.

I can't really find anything about grub2 and none-Mac EFI.

---

### Post by wilee-nilee on 2010-06-22
> **darkod said:**
> I didn't want to go that far, but I agree.
It's time to talk to the manufacturer if your machine came with it.
If you assembled it and decided to use EFI, then you should have searched for information how to add ubuntu to EFI before you started.

I can't really find anything about grub2 and none-Mac EFI.

I don't think the EFI is a embedded partition in the motherboard just hidden, somebody could PM herman or meierfra, and see what they think. oldfred says he will install it to figure it out, I sure would like to know whats up.

---

### Post by darkod on 2010-06-22
> **wilee-nilee said:**
> I don't think the EFI is a embedded partition in the motherboard just hidden, somebody could PM herman or meierfra, and see what they think. oldfred says he will install it to figure it out, I sure would like to know whats up.

I didn't mean to say it's on the MB, just that if you build your own computer and decide to set it up and use EFI, you should know what to do with it. Or the manufacturer needs to give you support if they shipped the computer with it.

It's part of the boot process so I was hoping the MB manual might have some info on it.

Another alternative is just to create small FAT32 partition, so you can install grub2 on it, in addition to the standard /, swap, /home, etc. But you still need to know how to "add" grub2 from that FAT32 partition to the EFI, or how to make the EFI recognize it.

---

### Post by wilee-nilee on 2010-06-22
> **darkod said:**
> I didn't mean to say it's on the MB, just that if you build your own computer and decide to set it up and use EFI, you should know what to do with it. Or the manufacturer needs to give you support if they shipped the computer with it.

It's part of the boot process so I was hoping the MB manual might have some info on it.

Another alternative is just to create small FAT32 partition, so you can install grub2 on it, in addition to the standard /, swap, /home, etc. But you still need to know how to "add" grub2 from that FAT32 partition to the EFI, or how to make the EFI recognize it.

I wasn't referencing your post I was just sharing what this partition seemed to be after looking at the web information.

---

### Post by oldfred on 2010-06-22
Three years ago I read an article about efi being the future and wanted to buy a motherboard with it. None at reasonable price and only one or two were available. Then Apple adopted.

More info
[http://packages.ubuntu.com/hardy/grub-efi](http://packages.ubuntu.com/hardy/grub-efi)

It also uses the gpt partition scheme which is a new improvement over the 20+ year old MBR scheme that has a max of 2TiB.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
grub2 & GPT info
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)

---

### Post by God Dammit on 2010-06-23
I built the computer myself. Intel seems to assume the operating system should know how to handle EFI and includes no special installation instructions for any OS.

---

