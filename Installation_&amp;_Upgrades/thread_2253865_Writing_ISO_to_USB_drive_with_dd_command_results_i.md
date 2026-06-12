---
title: "Writing ISO to USB drive with dd command results in corruption"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by ronniepinsky on 2014-11-23
Edit: Problem solved.  The gpt tables corrupt error was irrelevant.  The problem was I needed the 32-bit EFI boot file.  The disk I made about a year ago worked because I had already added the 32-bit EFI boot file.

-----------

The USB drive fails to boot and GNU parted shows "both the primary and backup gpt tables are corrupt" when I do the print command.  The system will boot off another Linux live USB drive.  GNU parted shows a normal configuration on the drive that boots.

I am using:

```

dd if=nameofiso.iso of=/dev/sdb

```

dd finishes without any errors.  I have tried several different block sizes with the same result.

1. Must isohybrid be used on the ISO first, or has that already been done?  I get the same result with and without isohybrid.

2. Must the ISO be mounted as a loopback device first, or is that unnecessary?  The mkusb source code ([http://phillw.net/isos/linux-tools/mkusb/mkusb](http://phillw.net/isos/linux-tools/mkusb/mkusb)) seems to indicate so here about 3/4 of the way down: 
```

echo "The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:"

```

3.  Is there anything I am missing?  The rest of the mkusb source code looked straightforward.

This page ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)), under the mkusb section informs that this is a reliable method, saying:
```

This method with **dd** has a high success rate. 

```

Just to be clear I do not want to use unetbootin, mkusb, or any other scripts.  I want to use this "high success rate" method instead.  Thank you.

---

### Post by sudodus on 2014-11-23
mkusb is using dd under the hood. Its main purpose is to make it safer by showing clearly which drives you have connected asking checking questions, so that you write to the drive (usually a USB pendrive) that you want to write to.

Your command line looks correct to me. I would run it with superuser privileges, so

```
sudo dd if=nameofiso.iso of=/dev/sdx
```

where x is the drive letter (in your case b).

Isohybrid should be used only once. If the iso file is already treated with isohybrid, you should ***not*** do it. So if you have tried first before running isohybrid, and after running it, you have done what you should do.

But the download might have failed. Please check the original iso file with ***md5sum***, that the checksum matches the published string. See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

-o-

All current Ubuntu iso files make working pendrives via dd except Ubuntu 12.04 mini.iso. Many other iso files work too, but there are some iso files, that do not work, not even after treatment with isohybrid.

Please tell me ***which iso file you try*** to copy/clone/flash to the pendrive, and I can download and test it here :-)
[HR][/HR]*Edit to reply directly to your questions:*

The iso file must not be mounted during the dd process (that is only done at an earlier stage to detect what system it contains). [I]Furthermore, no partition on the target drive should be mounted.
[/I]
Maybe it works better with sudo. Maybe your download was bad. Maybe that particular iso file does not work with dd.

---

### Post by ronniepinsky on 2014-11-23
Unfortunately, all steps have failed.  

I have tried a different ISO, done an md5check, tried a different usb device, and tried a different computer with a different dd version.  I have tried with kubuntu-13.10-desktop-amd64.iso and kubuntu-14.10-desktop-amd64.iso.

I have also tried this method on the previously working USB drive with 13.10 on it with the result that it is also no longer working.  GNU parted says it's primary gpt table is corrupt but the backup is used.  It still fails to boot.

I am more convinced than ever that I am missing a step somewhere.  Either that or I have multiple failed computers and USB drives.

Edit: same problem with Ubuntu 14.10 iso.

---

### Post by oldfred on 2014-11-23
the dd type install is not creating a standard flash drive with MBR, and partitions. It is an image of DVD that then boots more like a DVD. If you want to later use flash drive as a standard data drive you need to use dd to zero out MBR and then create new partition table.

And MBR and gpt will conflict. Gpt has a backup partition table at end of drive, so you start to get conflicts as backup gpt does not match anything.

Do not waste effort with 13.10 as it is obsolete and cannot be updated. 

There is no one way that works for everyone. Some USB ports work better with some BIOS/UEFI. Some only work with USB2. Some flash drives work better or not at all.
And some installers work where another installer does not.
But first check md5sum to be sure you downloaded a good ISO.

       The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. Or you can use dd.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)
dd creates hybrid which does not have standard partition table, you need to delete with dd beginning of flash drive to restore it to full size.

I normally do not recommend dd as its other name is "Data Destroyer". Since it totally overwrites exactly whatever you tell it to do, any typo will destroy data.

I think all the install methods have a high sucess rate, but none are perfect in every case.

---

### Post by sudodus on 2014-11-23
> **ronniepinsky said:**
> Unfortunately, all steps have failed.  

I have tried a different ISO, done an md5check, tried a different usb device, and tried a different computer with a different dd version.  I have tried with kubuntu-13.10-desktop-amd64.iso and kubuntu-14.10-desktop-amd64.iso.

I have also tried this method on the previously working USB drive with 13.10 on it with the result that it is also no longer working.  GNU parted says it's primary gpt table is corrupt but the backup is used.  It still fails to boot.

I am more convinced than ever that I am missing a step somewhere.  Either that or I have multiple failed computers and USB drives.

Edit: same problem with Ubuntu 14.10 iso.

You received a good reply from *oldfred* already. I would just like to add some comments.

I have installed several Ubuntu flavour iso files with ***mkusb*** into USB pendrives from version 13.10 as well as 14.10. I know that it works with mkusb and hence with ***dd***. As *oldfred* already explained, these iso files are already treated with isohybrid, so you should *not* do it (double treatment destroys an iso file).

The file systems of the iso files, that are copied via dd are 'strange', and do not make ***gparted*** happy. But they work from DVD as well as from USB, and the 64-bit versions work in BIOS as well as in UEFI mode. You should try booting, not listen to the complaints of gparted.

Furthermore, there is no need to prepare the USB drive, it will be overwritten anyway by mkusb or dd. But as oldfred pointed out, when you want to re-use the USB drive after booting and installing, you should wipe it. Actually it is enough to ***wipe the first megabyte*** (mibibyte with base 2), and it is very convenient to do that with mkusb. After that ***gparted*** will be happy to create a new partition table and partitions according to your wishes.

-o-

You might have a problem with your pendrive, that it does not co-operate with your motherboard or UEFI-BIOS system. Please specify your computer and USB pendrive

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it possible to give you relevant advice.

Finally, the following link and links from it might help you find the problem.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2014-11-24
> **ronniepinsky said:**
> Edit: Problem solved.  The gpt tables corrupt error was irrelevant.  The problem was I needed the 32-bit EFI boot file.  The disk I made about a year ago worked because I had already added the 32-bit EFI boot file.

...

Congratulations, and thanks for sharing your solution :KS

---

