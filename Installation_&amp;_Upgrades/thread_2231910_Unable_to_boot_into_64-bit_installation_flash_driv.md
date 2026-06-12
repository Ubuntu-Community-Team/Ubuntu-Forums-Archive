---
title: "Unable to boot into 64-bit installation flash drive"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by david-slagh123 on 2014-06-28
I have a Gigabyte 970A-DS3 motherboard (UEFI), link here: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2932738](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2932738) 

When first going to try dual-booting Windows 8.1 and Ubuntu (Multiple versions tried: 12.04 LTS, 13.10, 14.04 LTS), I downloaded the 64-bit version.  I "burned" it to a 4GB flash drive using the Linux Live USB creator.  When I tried booting into Ubuntu using the "Try Ubuntu without installing", I got the Purple Ubuntu loading screen, and then it gave me the BusyBox error.  (Unable to find a live file system).  I then downloaded a 32-bit version, formatted the flash drive, and tried again, using the 32-bit iso and Linux Live USB creator again.  That worked just fine, and I dual-booted Ubuntu and Windows 8.1 for a while until something else happened, which is another story and irrelevant.  Now I am only running Windows 8.1, and wanted to try dual-booting again, but I wanted to do it right this time, and use 64-bit. I tried Unetbootin, I tried using Active ISO burner and a DVD.  Nothing worked.  I tried multiple versions of Ubuntu, and even Linux Mint 16 and 17 (with Cinnamon).  The 32-bit version always will boot and let me start the installation process, but the 64-bit never does.  I'm not sure if I have secure boot enabled or not.  

So, now my question: 

Is the problem with my Motherboard?  Is my model the problem, or do I simply need to find and disable Secure boot?  Should I use a different program to make installation media?  Would a flash drive be preferable to a DVD, or vice versa?  On that note, I was later able to install 64-bit on a computer at my Tech Center (yes, I had permission) with the exact same installation media that I originally tried at home, so it wasn't faulty installation media.

My main purpose to dual-boot is because the number of Linux-supported games in my Steam library is growing, and I wanted to try some Linux gaming, hence my desire for 64-bit.  

I would greatly appreciate any help you could give me.

---

### Post by gordintoronto on 2014-06-29
A Newegg review of the board, by a Linux user, says, "you have to disable the IOMMU in the BIOS."

Overall, the board has pretty mediocre reviews. I am very happy with a 2009 Gigabyte board, but it has no USB 3 or Sata 6 GB.

---

