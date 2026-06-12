---
title: "Installing on a RAID array."
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by TimMcE on 2008-09-05
I currently have 3 hard drives in my computer.  Two are RAID'd together and have Windows and most of my data on them.  The third had been sitting blank, so I decided to install Kubuntu on it.  Since it was a 1TB drive, I gave Kubuntu 750GB, and left the rest to be shared space for both OS's.  I thought it was odd I no longer had the option to format that partition as NTFS, but figured I could do it later.  

The installation seemed to work fine, aside from the installer still seeing the RAID'd HDDs as two separate drives, but when I rebooted, it booted straight into Windows with no boot loader screen.  More strangely, when I was back in Windows, it didn't see the third hard drive anymore.

All I know at this point is that something went pear-shaped, but I haven't the foggiest notion where to even start fixing it.  I've done some googling, and I can find are how-to's on installing onto a RAID array, but nothing on installing on a drive outside the array.

Edit:  I should probably add that I'm using a software RAID (I think), configured through the motherboard's BIOS, with no external controller, and I was using the standard i386 32-bit CD version, and it's a RAID 0 array, if that helps.

---

### Post by tamoneya on 2008-09-05
i think the confusion starts with the motherboard raid controller.  Software raid is a linux feature which allows you to RAID to drives on a normal controller.  The raid "chipsets" that are in desktop motherboards are typically referred to as fakeRAID.  They are poorly supported by linux and that is why you are not seeing them during the install and my guess is that grub isnt able to handle them so it just left NTLDR as the bootloader.  I would suggest attempting to get (k)ubuntu into NTLDR.  That may be your best option that keeps the fakeraid for windows while still allowing linux.  I cant really speculate much more than that since I dont know much about the fakeraid difficulties.  I have worked a lot with software raid because on my server and it has worked great but fakeraid is a whole different monster.

---

### Post by TimMcE on 2008-09-06
Ok, thanks for that.  With what you told me, I found this: [http://hol.net.nz/blog/kubuntu-with-fakeraid](http://hol.net.nz/blog/kubuntu-with-fakeraid) which seems helpful, but again it's dealing with installing kubuntu onto the RAID drives.  I'm just wondering, do you think once I got to the point where kubuntu recognized the RAID, I'd be able to install it onto the non-RAID drive and have it install Grub on the RAID array?

---

### Post by tamoneya on 2008-09-06
i dont think grub in general has very good support for raid arrays.  I setup a software raid and it could only boot from a mirrored array.  Since my disks were in raid 5 parity I had to make a separate boot partition that was mirrored.  This is most likely also true when it comes to fakeraid so grub is probably seeing that your windows OS cannot be launched from grub so it isnt installing itself.

---

