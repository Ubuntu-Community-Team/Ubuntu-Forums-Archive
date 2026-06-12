---
title: "created ntfs partition, but xp won't install"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by bistro on 2011-02-01
Hi

I used gparted to create 60GB free space which I then formatted as ntfs. However,when I go to install XP I get the blue screen of death.

I know the XP installation disc is OK.

The ntfs partition (sda3) is after the ext4 partition (sda1) - could this be the source of the problem?

Thanks

Dave

---

### Post by Rubi1200 on 2011-02-01
Are you booting Ubuntu?

If yes, post the output of the following command please:

```
sudo parted -l
```
(lowercase L not 1)

Thanks.

---

### Post by bistro on 2011-02-01
Hi

thanks for your help:

Model: ATA TOSHIBA MK5055GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  420GB  420GB   primary   ext4            boot
 3      420GB   488GB  67.1GB  primary   ntfs
 2      488GB   500GB  12.6GB  extended
 5      488GB   500GB  12.6GB  logical   linux-swap(v1)

Regards

Dave

---

### Post by Rubi1200 on 2011-02-01
Odd, I would have assumed your setup would be okay.

How about trying this:

Keep the partitions setup as they are, but rather than formatting as NTFS leave the partition as unallocated space (leave it as a primary partition of course) and then try the Windows installation again.

---

### Post by ronnielsen1 on 2011-02-01
>  but rather than formatting as NTFS leave the partition as unallocated space (

agree, I've had problems with windows recognizing a ntfs partition that was made with linux.

---

### Post by coffeecat on 2011-02-01
> **bistro said:**
> Hi

I used gparted to create 60GB free space which I then formatted as ntfs. However,when I go to install XP I get the blue screen of death.

I know the XP installation disc is OK.

The ntfs partition (sda3) is after the ext4 partition (sda1) - could this be the source of the problem?

Thanks

Dave

I don't believe the order of the partitions will worry the XP installer. At what point does it BSOD? Before or after loading the driver? Before or after the EULA? 

One minor point: you have the boot flag set on sda1 which is your Linux partition. Linux doesn't need the boot flag in order to be able to boot, but Windows does. The Windows installer should sort this out if you can solve the BSOD problem.

---

### Post by Rubi1200 on 2011-02-01
And don't forget that Windows will overwrite the MBR when it installs.

Reinstalling GRUB is easy though:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

---

### Post by ronnielsen1 on 2011-02-01
> I don't believe the order of the partitions will 
worry the XP installer.
 

Shouldn't mess with the installer but I have had to add the 
following to grub to make windows on the 2nd partition think
it's on the first partition

map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,1)
chainloader +1

---

### Post by bistro on 2011-02-03
Hello

thanks for all the replies. I went away and tried again, unfortunately I've been unsuccessful.

Each time I see the BSOD once Set Up has loaded the files and the 'starting windows' message appears. Tried deleting the ntfs partition to no avail. I tried removing the boot flag from the first partition. 

Finally, I started to think that my installation disc was corrupted after all, even though I had installed XP via virtualbox earlier that day (then I uninstalled virtualbox). So today I borrowed some other windows installation discs:
[LIST=1]
[*]I tried two XP discs - same result.
[*]I tried my old win 2000 disc - first of all I had a message 'bios not acpi compliant', pressed F7 to by-pass this then the BSOD included the message 'inaccessible boot device'.
[*]Then tried Vista and windows did start with no BSOD. It's an upgrade though so I have to install XP/2000 first!
[/LIST]
I am completely baffled. I'd be really grateful for any suggestions or else I suppose I'm looking at wiping the hard drive with gparted and installing the two OS's from scratch.

Many thanks

Dave

---

### Post by Rubi1200 on 2011-02-03
Sorry to hear this has been so problematic.

The only thing I can think of right now is that somehow, even though we thought it would not be an issue, that the Windows CD is having a problem reading past the first 137GB of the disk.

On systems with an older BIOS, this was the limit.

Three options:

1. check in your BIOS to see if there is an option to read larger disks

2. try moving the partitions so that the NTFS will be first, followed by Ubuntu (risky in my opinion)
3. backup Ubuntu using something like Clonezilla and start over wiping the drive installing XP then Ubuntu (safer)

Wait though for other opinions before proceeding, but this is my take on the situation.

---

### Post by coffeecat on 2011-02-03
The only other thing I can think of is that you are trying to install to a partition 420GB in to a 500GB disc. 500GB discs were unknown when XP first came out and perhaps it simply can't install to a partitition whose start sector is at the 420GB mark. I'm not saying that XP can't cope with a 500GB disc - it can - but that it can't cope with a partition in that position. But this is just a theory - I could very well be wrong.

However...

> **bistro said:**
> Then tried Vista and windows did start with no BSOD. It's an upgrade though so I have to install XP/2000 first!I am completely baffled.

That's where I can help. There's a workaround where you can do a fresh install of Vista with an upgrade DVD. This is not a contravention of the EULA **so long as you have a valid XP licence which you are no longer going to use**. See this link:

[http://www.whatthetech.com/2007/01/31/workaround-for-clean-install-with-vista-upgrade-dvds/](http://www.whatthetech.com/2007/01/31/workaround-for-clean-install-with-vista-upgrade-dvds/)

Step 4 is not very well explained. What they mean is that once you've got the desktop running from the first installation, you insert the DVD again, and run setup from the DVD whilst still in the desktop.

---

### Post by ottosykora on 2011-02-03
Somehow I could not find an info in the thread regarding to what type of drive is the it you are going to install XP to?

ATA (IDE) drive, no problem, partitioning and installation

SATA, no, XP will not install to SATA drive by on its own,you have to supply SATA drivers separately on second media (floppy, second CD, sometimes usb) or slipstream the installation CD with the drivers before.

So let us know what technology harddrive you use.

----

have read somewhere that this might be scsi drive?
You have the drivers for that ready? Works similar as SATA, have them on other media and it could work.

---

### Post by coffeecat on 2011-02-03
> **ottosykora said:**
> SATA, no, XP will not install to SATA drive by on its own,you have to supply SATA drivers separately on second media (floppy, second CD, sometimes usb) or slipstream the installation CD with the drivers before.

This is only true of the original and SP1 discs. SP2 discs will install to a SATA drive. I have done it. But a good point. @bistro, were the XP discs you used service pack 2 or were they earlier?

---

### Post by bistro on 2011-03-02
I'm very sorry, I forgot to post back to thank everyone for their help. In the end I used the "double Vista install" method as XP would not work, even though it was SP2 (my hard disk is PATA).

All up and running now - thank you!

Dave

---

### Post by oldfred on 2011-03-03
Just for reference, the boot flag has to be on the NTFS partition when it is created in advance. If a blank drive windows creates the NTFS partition and adds the boot flag itself.

---

