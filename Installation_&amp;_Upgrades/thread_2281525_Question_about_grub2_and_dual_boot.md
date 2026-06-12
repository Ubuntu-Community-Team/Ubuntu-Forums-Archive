---
title: "Question about grub2 and dual boot"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by Aqxea on 2015-06-07
Hello.  I am still pretty new to using Linux.  I installed Kubuntu 15.04 x64 on my ssd in a dual boot config with Windows 10.  My pc is a few years old and it is UEFI enabled, but I don't think it has the Secure Boot feature.  When I installed Windows 10 x64 a few months back, I used GPT partition table.  I didn't know if that would make a difference when installing Linux.  I used Rufus to create my Kubuntu live usb, but it wouldnt' let me select the GPT option.  I had to use MBR.   I created a new 100GB partition and installed Kubuntu using the manual set partitions option.  I initially messed up by creating my root folder too small.  Downloaded and messed around with GParted until I think I have everything set up correctly.  

After a few weeks, my grub2 menu was getting cluttered with too many options and I didn't know what half of them did.  I removed a few old linux-image packages and that helped a little.  My question is, Is my partitioning and grub config setup correctly?  I am thinking about installing a GUI like BURG but before I do, I wanted to make sure my current configuration was optimal.   Also, why do I have 3 different Windows UEFI options?   I've attached a few screenshots so you can see what I'm looking at.  Please let me know if you have any questions.   Thanks.

Screenshots
[http://imgur.com/a/AQQG2](http://imgur.com/a/AQQG2)

grub.cfg file
[https://dl.dropboxusercontent.com/u/12158770/grub](https://dl.dropboxusercontent.com/u/12158770/grub)

---

### Post by oldfred on 2015-06-07
You should not be using MBR partitioning if booting with UEFI.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Burg has not been updated for eons, not sure it even works with UEFI. If using UEFI, you can use rEFInd which is a gui for UEFI boot.
      
 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by Aqxea on 2015-06-07
Thanks OldFred.  I'll get right on that and report back in a few minutes.  Been mowing for the last two hours and regret not wearing sunblock.  I was looking for an excuse to sit in the air conditioner for a few minutes anyway.  BTW, your title says you are a super master roaster.  Do you have a preferred roast?

---

### Post by Aqxea on 2015-06-07
Here you go.  Thanks again!

[http://paste.ubuntu.com/11635319/](http://paste.ubuntu.com/11635319/)

---

### Post by oldfred on 2015-06-08
Travelling from FL back to IL. Lawn really needs mowing. 

You have both Windows & Ubuntu in UEFI mode on your one gpt partitioned drive.
It looks fine to me. But you do want to houseclean kernels is system is not. I thought they started keeping it to two kernels which is what I have historically maintained. I usually let it grow to 3 or 4 then delete back to 3.

Not particularly a fan of gui boot managers. But I have wanted to try rEFInd and will soon try it on my second test install in sdb. My main working install is on my sda, SSD drive.

You may want to think about eventually converting other drives to gpt partitioning, but no immediate requirement. I started boot Ubuntu on my sdb drive with gpt in BIOS boot and Windows on sda with BIOS/MBR boot on sda back when I installed 10.10. And then every new drive and larger flash drives have been gpt partitioned as I knew eventually I would get an UEFI system.

I do prefer to have an operating system on every drive, but if you have an SSD you want both systems on SSD.

---

### Post by Aqxea on 2015-06-08
> **oldfred said:**
> Travelling from FL back to IL. Lawn really needs mowing. 

You have both Windows & Ubuntu in UEFI mode on your one gpt partitioned drive.
It looks fine to me. But you do want to houseclean kernels is system is not. I thought they started keeping it to two kernels which is what I have historically maintained. I usually let it grow to 3 or 4 then delete back to 3.

I will make a habit in the future to keep at least one extra kernel installed for backup.

> **oldfred said:**
> Not particularly a fan of gui boot managers. But I have wanted to try rEFInd and will soon try it on my second test install in sdb. My main working install is on my sda, SSD drive.

I didn't realize BERG hasn't been maintained in a while.  If I decide to install a gui boot manager, I'll consider rEFInd instead.

> **oldfred said:**
> You may want to think about eventually converting other drives to gpt partitioning, but no immediate requirement. I started boot Ubuntu on my sdb drive with gpt in BIOS boot and Windows on sda with BIOS/MBR boot on sda back when I installed 10.10. And then every new drive and larger flash drives have been gpt partitioned as I knew eventually I would get an UEFI system.

Is this possible without data lose?  What are the advantages to using GPT over MBR?  I currently have 4 drives in my system.  My primary boot drive is SSD and already GPT.  The other 3 are single partition and just store data.

---

### Post by oldfred on 2015-06-08
With any change there is risk. That is why I say you should plan for change, but not essential.

And you need gpt if drive is over 2TB or you want to boot in UEFI mode. Data drives really do not matter.

Gpt has improvements but mostly minor.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

I have never converted a drive with data, only when totally reformatting or new.
But there is a tool to convert.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

