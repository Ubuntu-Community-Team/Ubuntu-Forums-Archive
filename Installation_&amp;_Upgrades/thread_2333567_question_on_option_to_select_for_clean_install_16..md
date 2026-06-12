---
title: "question on option to select for clean install 16.04.1"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by Nosphky on 2016-08-11
I have a dual installation Windows10 and Ubuntu14.04. Each os has its own 1TB hard disk. Gparted shows sda for the windows disk and sdb for the linux disk. The linux disk (sdb) currently uses LVM to partition and resize partitions. This has worked fine for a couple of years.

Now I want to install 16.04.1 onto sdb, retaining the dual boot option but I thought to abandon LVM. My plan was to make a 100GB partition for linux, keep a small swap partition, and just use the rest as Home.

When I boot 16.04.1 with a liveUSB stick and select 'install', after a few pages, I get to select an option with the message that the system has detected the windows installation :

option 1 : install UbuntuStudio alongside Windows Boot Manager
option 2 : erase disk and install UbuntuStudio (losing all files on both os)
option 3: something else.

I don't mind losing all the linux files - I have a full backup of all my data but I don't want the linux installation to touch the windows disk.

I selected option 3 'something else' and got a GParted like view of the sda1-4 (windows) and sdb1, the lvm allocated and free space.

When I select sdb1 (some 310 GiB's) and go for a change, I see the option to format the partition but I have to chose between /, /boot, etc and there doesn't appear to be a way to specify the sizes.

For fear of messing up - I abandoned the install before doing something irrevocable and would hope that someone can provide further info and advice.

Would option 1 or 2 be more appropriate, bearing in mind that Windows is on its own hard disk ?
Is it a problem to get rid of LVM ?

---

### Post by grahammechanical on 2016-08-11
Use the live session to run Gparted to re-partition sdb. Make sure you are indeed working on sdb. You may need to format sdb first to clear away the LVM stuff. I have never worked with LVM so I am not giving advice based on personal experience. Create what new partitions you want.

If the drive has GPT partitioning you will need a efi_boot partition and some of us also advise to have a bios_boot partition as well. You can make them the same size as the efi_boot partition on the Windows 10 drive.

 With Windows 10 installed in EFI mode you will need to run the Ubuntu installer also in EFI mode to install Ubuntu Studio in EFI mode. And then use the Something Else option to install Ubuntu Studio into the already existing partitions.

There usually is an option to resize the partition when we use the Something Else option and select the partition and click Change. But I prefer to use Gparted in a live session and install Ubuntu into existing partitions.

Regards.

---

### Post by Nosphky on 2016-08-11
Hi grahammechanical - thanks for the response.  I don't know about GPT but I guess it applies. GParted under my 14.04 installation doesn't show any efi_boot stuff but the info shown by the install procedure, as far as I got with the liveUSB16.04.1, for sda was :

sda1  efi  104 MB Windows Boot Manager   (GParted shows Fat32, boot flag)
sda2        134 MB   unknown          (GParted shows unknown, msftres)
sda3  ntfs 737.348 GB unknown     (GParted shows ntfs, msftdata -  and this is all the Windows10 stuff)
sda4  ntfs 471 MB                      (GParted shows  ntfs, hidden, diag)
free space   262144 MB              (GParted shows unallocated)

I like the suggestion to use GParted from the live session to create the partitions.  Is it at that stage that I should create efi_boot and bios_boot partitions or later in the install procedure under the 'something else' option ?

So I guess I need efi_boot.  Where do I see the option to run the Ubuntu installer in EFI mode ?  My initial foray with the install under the live session didn't talk about EFI mode, at least not up to the point I got to.

---

### Post by Nosphky on 2016-08-12
A bit of feedback - the job's done, I'm now running 16.04.1 UbuntuStudio from a clean install.

For info in case others have the occasion to want to do the same :  GParted won't do anything useful on a disk that's using LVM.  I tried as per suggestion above to use the GParted in the live installation on the usb stick to clean up my hard drive because I had decided not to use LVM anymore. I had to use the live installation to install lvm manager and with that, I could remove all the lvm stuff. Then I used GParted to set up new partitions as I wanted.

I then did the clean install using 'something else' options and all went well.

Now I've got the inevitable lengthy period of getting the system to work as I want (and what I was used to with 14.04) because there seem to be lots of differences - some I don't care about either way, some I don't care for.  At the time, it does seem like a high price to pay for keeping up to date.

---

