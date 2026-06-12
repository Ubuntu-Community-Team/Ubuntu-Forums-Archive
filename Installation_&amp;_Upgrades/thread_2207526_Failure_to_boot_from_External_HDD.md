---
title: "Failure to boot from External HDD"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by Yatharth_Rai on 2014-02-24
I guess this is the right section, and I don't think there's a duplicate since I've googled like crazy for 4 days but still no help :'( 

My BIOS is not UEFI. 

So, I've installed Ubuntu on my External HDD. I made a partition of 200GB, and then made two 10GB partitions for /swap and /. The remaining space was for /home. I installed Ubuntu. The Bootloader was on dev/sdb, That's my External HDD. So, whenever I try to boot from it, I get a black screen. When I press shift, it gets stuck at GRUB Loading, sometimes at file not found, elf header smaller than expected and sometimes out of partition. I'm stuck a big time :( Help will be appreciated. And thanks for replying :)

My Internal HDD has Windows 7. It's busted, but works, so I installed Ubuntu on external hdd.

EDIT: I've been trying to install Ubuntu 12.04.4 LTS

---

### Post by Bucky Ball on 2014-02-24
Why exactly did you decide to install to an external hard drive? Your BIOS is not UEFI. Doesn't matter. That's easier than if it was. Windows is on the drive and you didn't want to accidentally wipe it? 

Anyhow, could you be a lot more specific about the errors you are getting when trying to boot from the Ubuntu external install.

PS: Unless you are intending to hibernate then a 10Gb /swap is unnecessary. 2Gb is fine. I would say that 10Gb for / is slim, but doable, depending on what you are intending to install into Ubuntu once it's up. 15-20Gb is better. If they are side by side you could shrink the /swap and give the free space to / by expanding that partition. You need to do resizing of / from a Live boot (CD/DVD/USB).

---

### Post by Yatharth_Rai on 2014-02-24
> **Bucky Ball said:**
> Why exactly did you decide to install to an external hard drive? Your BIOS is not UEFI. Doesn't matter. That's easier than if it was. Windows is on the drive and you didn't want to accidentally wipe it? 

Anyhow, could you be a lot more specific about the errors you are getting when trying to boot from the Ubuntu external install.

PS: Unless you are intending to hibernate then a 10Gb /swap is unnecessary. 2Gb is fine. I would say that 10Gb for / is slim, but doable, depending on what you are intending to install into Ubuntu once it's up. 15-20Gb is better. If they are side by side you could shrink the /swap and give the free space to / by expanding that partition. You need to do resizing of / from a Live boot (CD/DVD/USB).

Uh, I was thinking of installing Ubuntu on my External HDD and then booting from it, so that I could use my computer.  I've set the USB Removable Storage as the first boot priority. When I boot from the External HDD, I get a black screen which stays. If I rebooted and pressed shift, the system would again get stuck at GRUB Loading or give me one of the following messages:-

1. error: file not found
2. error: ELF Header smaller than expected
3. error: out of partition
each followed by >grub rescue

EDIT: I've been trying to install Ubuntu 12.04.4LTS

---

### Post by Bucky Ball on 2014-02-24
Ok. All I'm saying is that, even if Win is not working, the hard drive should be fine and there is nothing stopping you from installing to that drive alongside Win (or wiping it). If you have tried and there is something stopping you from installing to that drive, I'd be wondering what that problem is because that should be completely fine. Nothing to do with Win not working. ;)

---

### Post by Yatharth_Rai on 2014-02-24
> **Bucky Ball said:**
> Ok. All I'm saying is that, even if Win is not working, the hard drive should be fine and there is nothing stopping you from installing to that drive alongside Win (or wiping it). If you have tried and there is something stopping you from installing to that drive, I'd be wondering what that problem is because that should be completely fine. Nothing to do with Win not working. ;)

Ah Sorry, my bad, I didn't make myself clear lol
I want to install Ubuntu on my external HDD since my Internal HDD is filled up with Bad sectors and I don't think that using it now is safe, so I installed Ubuntu on the External HDD so that I don't have to use my internal HDD anymore. I cannot disconnect the Internal HDD since it's a laptop and I don't feel like opening it since I think I'll mess it up.
So, I want to continue using my laptop using only my External HDD with Ubuntu OS. I think I've elaborated it now haha :)

---

### Post by Bucky Ball on 2014-02-24
> **Yatharth_Rai said:**
> 
So, I want to continue using my laptop using only my External HDD with Ubuntu OS. I think I've elaborated it now haha :)

Got ya. Thanks. ;)

Well, there should be two plugs connecting the internal hard drive in the laptop. Fairly straightforward. It is usually in a compartment by itself and simply pulls out. 

There is a SATA connection and a power cable connection. That should be it. Out with the old and pop the new one in. You should only need to undo a few screws to get to it. 

As the internal drive is now dodgy and you are attempting to install to an external drive, there is not really much that you can stuff up when replacing the HD, but I do understand that the hardware side of things can be a little daunting for some users not used to it. 

Check out Youtube and there will be visual demonstration of how to replace the drive, possibly for your machine model.

See [HERE]("https://www.youtube.com/results?search_query=replace%20laptop%20drive&sm=3") for some clues ... good luck. ;)

---

### Post by Yatharth_Rai on 2014-02-24
> **Bucky Ball said:**
> Got ya. Thanks. ;)

Well, there should be two plugs connecting the internal hard drive in the laptop. Fairly straightforward. It is usually in a compartment by itself and simply pulls out. 

There is a SATA connection and a power cable connection. That should be it. Out with the old and pop the new one in. You should only need to undo a few screws to get to it. 

As the internal drive is now dodgy and you are attempting to install to an external drive, there is not really much that you can stuff up when replacing the HD, but I do understand that the hardware side of things can be a little daunting for some users not used to it. 

Check out Youtube and there will be visual demonstration of how to replace the drive, possibly for your machine model.

See [HERE]("https://www.youtube.com/results?search_query=replace%20laptop%20drive&sm=3") for some clues ... good luck. ;)

Ah, Thanks!
Just another little question,
is it possible to install Ubuntu on external hdd and boot from it? And use it on other PCs just by connected through the USB? Not as a Live version but as a fully installed OS.

---

### Post by Bucky Ball on 2014-02-24
> **Yatharth_Rai said:**
> 
is it possible to install Ubuntu on external hdd and boot from it? And use it on other PCs just by connected through the USB? Not as a Live version but as a fully installed OS.

I see no reason why not and certainly people do it. As long as you don't have a bunch of drivers installed for specific graphics and wireless. That would be your main concern. This might help: [http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html](http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html)

Linked from the post numbered 1 [HERE.]("http://askubuntu.com/questions/43174/installing-ubuntu-on-external-hard-disk")

---

### Post by Yatharth_Rai on 2014-02-24
> **Bucky Ball said:**
> I see no reason why not and certainly people do it. As long as you don't have a bunch of drivers installed for specific graphics and wireless. That would be your main concern. This might help: [http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html](http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html)

Linked from the post numbered 1 [HERE.]("http://askubuntu.com/questions/43174/installing-ubuntu-on-external-hard-disk")

Thanks again.
Did all the steps given at [http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html](http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html)
But when I try to boot from the External HDD, I get
 error: no such partition
>grub rescue

---

### Post by sudodus on 2014-02-24
Please specify your computer:

- Brand name and model
- RAM (size)
- graphics chip/card
- wifi chip/card/dongle

It makes it easier to give relevant help. Depending on the hardware of the computer, there are different alternatives.

But in every case the following test and check are valuable:

- When booting from the CD/DVD/USB drive, run ***memtest*** (to check that the RAM is good, run for hours, one single error is too much).
- And check the ***md5sum*** (that downloading the iso file was successful). See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ubfan1 on 2014-02-24
If you installed from a USB stick to the USB hard disk, you might be experiencing bug 384633.  Take a look at the grub commands before selecting one (type "e" and you will see all the commands).  With the USB install media present, it might have been assigned hd0 (sda), the internal hard disk hd1 (sdb), and the USB hard disk hd2 (sdc).  After pulling the USB install media, the internal hard disk becomes hd0 (sda) and the external USB hard disk hd1 (sdb), but if you see any sdc or hd2 in the grub commands, you can edit them to be one letter/number lower and try to boot.  After first boot, immediately run sudo update-grub to fix the problem.

---

### Post by oldfred on 2014-02-24
Also is / (root) the first partition or fully inside the first 137GB of external drive.
Some BIOS give those type of boot errors when parts of grub or kernels are beyond the 137GB point in drive. So / needs to be fully inside first 100 or so GB of drive.
Post this:
sudo parted -l

---

### Post by Yatharth_Rai on 2014-02-25
> **oldfred said:**
> Also is / (root) the first partition or fully inside the first 137GB of external drive.
Some BIOS give those type of boot errors when parts of grub or kernels are beyond the 137GB point in drive. So / needs to be fully inside first 100 or so GB of drive.
Post this:
sudo parted -l

ubuntu@ubuntu:~$  sudo parted -l 
Model: ATA WDC WD3200BEVT-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16        diag
 2      41.9MB  13.2GB  13.2GB  primary   ntfs         boot
 3      13.2GB  174GB   160GB   primary   ntfs
 4      174GB   320GB   146GB   extended               lba
 5      174GB   320GB   146GB   logical   ntfs


Model: Seagate Portable (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  778GB  778GB   primary   ntfs
 2      778GB   779GB  1024MB  primary   ext4
 3      779GB   994GB  215GB   extended
 5      779GB   794GB  15.0GB  logical   ext4            boot
 6      794GB   984GB  190GB   logical   ext4
 7      984GB   994GB  9999MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


> **ubfan1 said:**
> If you installed from a USB stick to the USB hard  disk, you might be experiencing bug 384633.  Take a look at the grub  commands before selecting one (type "e" and you will see all the  commands).  With the USB install media present, it might have been  assigned hd0 (sda), the internal hard disk hd1 (sdb), and the USB hard  disk hd2 (sdc).  After pulling the USB install media, the internal hard  disk becomes hd0 (sda) and the external USB hard disk hd1 (sdb), but if  you see any sdc or hd2 in the grub commands, you can edit them to be one  letter/number lower and try to boot.  After first boot, immediately run  sudo update-grub to fix the problem.

Nope, I didn't install Ubuntu using a USB but through a disc. 



> **sudodus said:**
> Please specify your computer:

- Brand name and model
- RAM (size)
- graphics chip/card
- wifi chip/card/dongle

It makes it easier to give relevant help. Depending on the hardware of the computer, there are different alternatives.

But in every case the following test and check are valuable:

- When booting from the CD/DVD/USB drive, run ***memtest*** (to check that the RAM is good, run for hours, one single error is too much).
- And check the ***md5sum*** (that downloading the iso file was successful). See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Ran the memtest, RAM turns out to be good.
I will check the md5sum

I own a Dell Inspiron N5010
RAM is 4GB
Graphic Card is AMD Mobility Radeon HD 5450
Intel wireless chip.

---

### Post by sudodus on 2014-02-25
> **Yatharth_Rai said:**
> ubuntu@ubuntu:~$  sudo parted -l 
...
Model: Seagate Portable (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  778GB  778GB   primary   ntfs
 2      778GB   779GB  1024MB  primary   ext4
 3      779GB   994GB  215GB   extended
 5      779GB   794GB  15.0GB  logical   ext4            boot
 6 [COLOR=#ff0000]**794GB**   984GB  190GB   logical   ext4[/COLOR]
 7      984GB   994GB  9999MB  logical   linux-swap(v1)

You might have the problem that *oldfred* mentioned (that the linux partition is too far from the drive head)
> 
...
Ran the memtest, RAM turns out to be good.
I will check the md5sum
OK> 
I own a Dell Inspiron N5010
RAM is 4GB
Graphic Card is [COLOR=#ff0000]AMD Mobility Radeon HD 5450[/COLOR]
Intel wireless chip.

You might have problems with the graphics card. Try some boot options, start with ***nomodeset*** according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and then try to install a proprietary driver

---

