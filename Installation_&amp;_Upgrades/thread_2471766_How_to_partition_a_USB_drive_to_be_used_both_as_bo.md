---
title: "How to partition a USB drive to be used both as boot and back-up?"
date: 2022-02-08
forum: Installation &amp; Upgrades
---

### Post by josefranw on 2022-02-08
Ok, here's the deal.

I want to install Xubuntu on my laptop. But I only have a 64 GB pendrive that I intend to use as a booting device (to burn the .iso) as well as use the remaining free space as storage to keep and save all my documents currently on the laptop so as not to lose them.

Can it be done?

If so, how?

(PD: English is not my first language so I might not be using the "most technically-expert" language here, but I do hope my message and what I intend to do can be understood)

---

### Post by foxsquirrel on 2022-02-09
If I am understanding your question correctly, no.

If your laptop has an internal hard drive you only need a small USB drive to load the OS, not sure about Xubuntu but its assumed that it will fit on a 8GB  usb drive.

Move your important files to a second USB drive and reinstall them after setting up the OS on your "boot" drive.

Messing around with important files is not a good thing to do, keep them safe until the OS is installed and ready to run.

---

### Post by C.S.Cameron on 2022-02-09
If you use mkusb to create your pendrive, it will format the space left over after creating the persistent drive as NTFS. It will then be usable by Windows and Linux computers.

---

### Post by tea for one on 2022-02-09
Are you currently using Windows 10?
You can use one USB device as an ISO installer together with space for a back up.

Download Rufus software [https://rufus.ie/en/](https://rufus.ie/en/)
Create your Xubuntu drive [COLOR="#0000FF"]with persistence[/COLOR]
The persistent partition will be [COLOR="#FF0000"]ext3[/COLOR] (which Windows cannot read)
Use Windows Disk Management to re-format the persistent volume to [COLOR="#0000FF"]NTFS[/COLOR]
Safely remove the USB stick
Re-attach the USB stick
Hopefully Windows will now be able to read/write to the NTFS volume

Proceed cautiously if you are new to bootable usb devices.

Personally, I would purchase a dedicated disk for backups and a second disk for bootable operations.
Back ups are the most important part of managing a PC and, in essence, should not really be compromised with other OS activities.

---

### Post by Draciron on 2022-02-12
From what I understand you want to use a USB drive as both your boot device and system drive. Booting into Linux from the USB drive. Basically having a go anywhere Linux system.  If you already have the drive set up.  Download and install Gparted to re-partition and ignore the rest of this. 

My suggestion is do this and you may already know some/have done some of this. 

First make sure you have a large enough USB drive. 128 Gig is probably the bare min. Perhaps a better alternative is a USB hard drive.  Then a 2nd drive, to set up Linux on the portable Linux setup. 

Next  create the install drive through the startup disk creater utility. on another Ubuntu machine. It is installed by default I believe. If not it's in the repos for all variants I'm aware of. 

Use that smaller thumb drive to install to the USB drive or external hard drive.  Select custom build.  My suggestions for partitioning are a /  /home and /swap with this kind of installation it'll be slow enough since everything is going through USB channel. So the extra performance kick you get from using a perm swap drive will be noticeable.   / and /home formatted to ext4 and /swap formatted to swap.  

Then the rest of the install as normal. If you are using an external hard drive, you'll likely have more space, a terabyte external is fairly reasonably priced these days.  With a 500 gig drive I'd give 100 to /  and since you don't know how much RAM you'll have I'd just do a 4 or 10 gig swap drive. The rest going to /home. 

If you don't do it at install, you can download gparted to the startup disk or drive you are setting up, and use that on the Linux system you are making to accomplish the same thing.  Disks might work for that, but Gparted I'd trust more and it's easier with Gparted in my opinion.  

The advantages of an external drive is considerably more space at a lower cost.  The thumb drive will probably be a little faster, though you can get an SSD external drive. They are pricey but not astronomical. Though usually pretty tiny relative to other external HDs.  Both will boot just fine as long as the boot order is set in the bios. Both are easily duplicated. Both are portable and my experience has been that external drives are a bit more durable than thumb drives. Probably because of the temptation to put a thumb drive in your pocket.  The thumb drive is a little easier to carry around everywhere. Though you could use a cell phone holster to carry an external drive around everywhere you go and protect it. They make some external drives that are armored, thus pretty durable for every day carrying around. Put one of those in a holster and you have a pretty easily carried and durable Linux box anywhere you go.

---

### Post by breakdaze on 2022-02-14
> **josefranw said:**
> Ok, here's the deal.

I want to install Xubuntu on my laptop. But I only have a 64 GB pendrive that I intend to use as a booting device (to burn the .iso) as well as use the remaining free space as storage to keep and save all my documents currently on the laptop so as not to lose them.

Can it be done?

If so, how?

(PD: English is not my first language so I might not be using the "most technically-expert" language here, but I do hope my message and what I intend to do can be understood)

So you want a bootable pendrive that you can use to install Xubuntu and also store data, correct? Are you going to dual-boot? The laptop is now using Windows, correct? Does it use UEFI for firmware? Is the pendrive formatted FAT32?

If it is exfat or ntfs, my trick won't work.

One way is to install GRUB from Windows, then make a menu entry in /EFI/boot/grub.cfg to point to the iso, mounted as a "loop" device. You could have the iso on the pendrive, or on a regular fixed disk in your laptop. For ease of use, I recommend just using the pendrive to hold the iso.

First, follow this guide using Windows. It will make your pendrive bootable, and it won't delete the contents: [https://www.pendrivelinux.com/install-grub2-on-usb-from-windows/](https://www.pendrivelinux.com/install-grub2-on-usb-from-windows/)

Copy your download of the iso to the root of your pendrive (formatted FAT32).

The next part is more tricky, you need to open notepad.exe and edit the /EFI/boot/grub.cfg

Add this, or similar depending on which iso you downloaded:

```
menuentry "Xubuntu 21.10 Desktop iso" {
  set isofile="/xubuntu-21.10-desktop-amd64.iso"
  loopback loop (hd0,1)$isofile
  linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
  initrd (loop)/casper/initrd
}

```

This example assumes the iso is xubuntu-21.10-desktop-amd64.iso, and GRUB is seeing your pendrive as (hd0,1) which just means the first disk, and first partition. This may depend on your UEFI selection, but I recommend just making the UEFI bootable pendrive your first boot device in your settings, and not using an on the fly selection from a boot order hotkey.

Once you have edited your grub.cfg, save it, and reboot, again making sure the pendrive UEFI selection is the first boot device.

Now you should be able to launch the Live ISO, and install as normal, without having to format the pendrive.

The mkusb or the Rufus method mentioned above may also work, but this is how I do it.

---

### Post by C.S.Cameron on 2022-02-14
@breakdaze
It sounds to me like the OP wants a Persistent install pendrive.
In that case you have to create an ext4 partition on the thumbdrive and name it "writable", then add the word persistent to your menuentry thus:
"linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject persistent"

---

### Post by breakdaze on 2022-02-14
@C.S.Cameron I know that, but to me it sounded more like OP just wanted to install it, not have a persistent Live USB. Perhaps the OP will clarify. I was trying to keep OP from having to partition anything. If starting from Windows, you need special software to make the ext4.

---

### Post by breakdaze on 2022-02-14
By the way, if you don't mind the USB flash drive being wiped to get it ready, and you do want a NON-persistent Live Linux USB, the easiest way to do this is to write the iso file directly to the drive. In Linux use dd, in Windows use something that works the same way, such as Win32 Disk Imager. I used RMPrepUSB with the File -> drive option. The iso has all the stuff you need embedded.

EDIT: HOWEVER, I forgot this method can't be used to make the drive for storage as seen under Windows, so not what the OP wants to do!

I just did this on a 4Gb USB flash drive with the latest Ubuntu 21.10 Desktop ISO, and I'm typing this from the Live USB. Here is what the partition screenshot looks like:
[https://imgur.com/a/gLiKBKR](https://imgur.com/a/gLiKBKR)

Under Windows, disk management can't see the drive because of the way the boot sector is, I suppose.
[https://imgur.com/a/4P9T18o](https://imgur.com/a/4P9T18o)

BUT, if you just want a small USB drive for testing and installing Ubuntu, you don't need Rufus or anything like that, just write the iso raw to the usb flash.

Apparently, though, it doesn't support persistence. So, apparently it's only good for testing and installing, no settings or files.

---

### Post by shaira24 on 2022-03-07
> **tea for one said:**
> Are you currently using Windows 10?
You can use one USB device as an ISO installer together with space for a back up.

Download Rufus software [https://rufus.ie/en/](https://rufus.ie/en/)
Create your Xubuntu drive [COLOR=#0000FF]with persistence[/COLOR]
The persistent partition will be [COLOR=#FF0000]ext3[/COLOR] (which Windows cannot read)
Use Windows Disk Management to re-format the persistent volume to [COLOR=#0000FF]NTFS[/COLOR]
Safely remove the USB stick
Re-attach the USB stick
Hopefully Windows will now be able to read/write to the NTFS volume

Proceed cautiously if you are new to bootable usb devices.

Personally, I would purchase a dedicated disk for backups and a second disk for bootable operations.
Back ups are the most important part of managing a PC and, in essence, should not really be compromised with other OS activities.


rufus is really great for creating bootable usb on windows or macOS. but you need to know that Rufus does not support Legacy boot, 
so if you have one of those older PCs you need to find some other solution.


In our test for Rufus, we found a choice that can be executed successfully.


[LIST]
[*]Select GPT if you only need UEFI support.
[*]Select MRB + FAT32 will support both UEFI and Legacy boot mode.
[*]Choose NTFS instead of FAT32 if install.wim file larger than 4 GB.
[/LIST]

source on how to create bootable usb using rufus.
[https://www.sysgeeker.com/how-to-create-windows-10-bootable-usb-with-rufus.html](https://www.sysgeeker.com/how-to-create-windows-10-bootable-usb-with-rufus.html)
[LIST]
[*]
[/LIST]

---

