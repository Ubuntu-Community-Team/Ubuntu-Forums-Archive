---
title: "New Install boots to grub"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by foxrow on 2011-03-09
I have downloaded and run the latest WUBI. The first part has completed and downloaded the necessary files and performed an install. 

On the first reboot however I end up in grub and cannot find any help to explain why this has happened.

Can somebody please explain what has gone wrong and how to fix it please.:mad:

---

### Post by Rubi1200 on 2011-03-09
Hi and welcome to the forums :-)

Are you still able to boot Windows normally?

Are you seeing a GRUB menu or a grub prompt?

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by foxrow on 2011-03-09
Hi,

thanks for coming back on this. I finally worked out after a lot of searching that the partition I gave to wubi must be at the start of the disk (1024 cylinders) which is not mentioned in the guides.

However, I now have a new problem in that the first boot gets as far as checking battery ... [ok] and then hangs. I've tried the boot with ACPI workarounds but that does the same. 

I don't have a CD image as I am using wubi to install within windows (which is still bootable at the moment) so can't actually get anywhere until the wubi first reboot manages to get through to the end.

Not happy, especially since everybody seems to say Ubuntu is the most user friendly Linuxy thing out there - I'm starting to disagree! (Even more so since to move partitions I had to uninstall the original wubi which meant even more of my broadband allowance was used up downloading the files again!)

---

### Post by bcbc on 2011-03-09
Wubi retains a hidden copy of the Ubuntu Desktop ISO so you don't need to download it again (see [http://ubuntuforums.org/showthread.php?t=1663306](http://ubuntuforums.org/showthread.php?t=1663306) ). Not sure why it's hidden, but ... there it is.

It doesn't have to be on the first partition. There is an issue with the wubildr.mbr (which is grub4dos and that uses 'bios' functions to locate the wubildr file in the root of (any) partition) so if that file is > 137GB it can cause some issues on some bioses. Also I've heard excessively fragmented computers might interfere with grub4dos using the wubildr.

That checking the battery is probably not related to your problem. I would guess that it's your graphics card... just because I had a similar issue and I thought it was the battery...
So what graphics card do you have?

And PS regarding Ubuntu not being user friendly... I scrubbed my XP the other day and reinstalled (but turned out my resource CD with the drivers was the incorrect model - dell 6000 instead of 6400). So guess how much of my computer worked? I had to boot Ubuntu to download the Windows wireless driver before I could get online and then manually download each driver from the Dell site.
So XP with a DVD... none of the hardware worked out of the box. Ubuntu with a CD, everything working. 
It's just a pain for some people because some graphics card makers don't share their info with the open source community, and since the computer came with everything installed and working - they assume that Ubuntu should be the same.

---

### Post by foxrow on 2011-03-10
With regard to the redownload of the ISO, WUBI forced me to uninstall in order to change the partition to one earlier on the disk (BIOSes only seem to access the first 1024 cylinders from what I have found). This uninstall removed the downloaded ISO and rather than use one squirreled away it downloaded it again. Even if I dropped a copy of the file into the relevant location.

I have an NVidia GeForce3 Ti 500 which has caused me problems every time I try and use Linux no matter what the flavour and that despite the fact that the boot shows text and the Ubuntu moving dots graphics without a problem. 

The ISO that wubi downloads is too big for a cd and the machine won't boot from USB so I can't go down those routes.

---

### Post by Rubi1200 on 2011-03-10
You could try following the instructions here for your graphics card:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by bcbc on 2011-03-10
> **foxrow said:**
> With regard to the redownload of the ISO, WUBI forced me to uninstall in order to change the partition to one earlier on the disk (BIOSes only seem to access the first 1024 cylinders from what I have found). This uninstall removed the downloaded ISO and rather than use one squirreled away it downloaded it again. Even if I dropped a copy of the file into the relevant location.

I have an NVidia GeForce3 Ti 500 which has caused me problems every time I try and use Linux no matter what the flavour and that despite the fact that the boot shows text and the Ubuntu moving dots graphics without a problem. 

The ISO that wubi downloads is too big for a cd and the machine won't boot from USB so I can't go down those routes.
Wubi uses the same desktop image that is used for a normal desktop install. It can't be too big for a CD or else no one would be able to create install CDs. If you look at the reported size in bytes it may appear bigger than the CD, but if you consider the MB size it fits.

The only reason that Wubi would download a new image is if there is a problem with the old one, you're running a wubi.exe from a different release, or you selected a different type of Ubuntu (e.g. switched from Ubuntu to Netbook editition).

---

### Post by bcbc on 2011-03-10
That 137GB limit is for older BIOSes. I understand that this affects ntldr, grub, grub2, grub4dos as they use BIOS functions.

---

