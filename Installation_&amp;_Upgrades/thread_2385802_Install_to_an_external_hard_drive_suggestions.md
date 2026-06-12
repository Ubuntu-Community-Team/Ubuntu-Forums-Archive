---
title: "Install to an external hard drive suggestions"
date: 2018-02-25
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2018-02-25
Hello Everyone,

I have a newish laptop with an A10-9600P with 8gb ram.  Of course, it has Windows 10 on it and I have to leave it there for my wife (she refuses to use Linux, I despise Windows 10.)  I want to install a full blown Ubuntu (17.10), but I have a couple concerns with the installation on this drive.

1.  I don't want the Grub boot loader on the laptops hard drive.  I want to leave that alone.  I have tried this before and it insists on installing Grub on the laptop's hardrive with a path to sdb1 (or where ever it was for the external drive.)

2.  With the new UIFI configurations and Windows locking everything down with Secure boot, I am unable to boot from USB without enabling CSM and disabling Secure Boot, as well as fast boot.  What happens to the Windows boot if I do these things?  Some research I have done suggests nothing with change with Windows, it will boot as normal.  Others have said Windows will not boot if a change those configurations.  

Unless I change those things, this laptop with not give me the choice to boot from USB.  Some have suggested I remove the hard drive during installation, but on this particular laptop I have to disassemble the back and open it up, which I am a little concerned about doing.

Anyone have any ideas how I can do this with the least about of risk to the Windows boot?

Any replies appreciated.

Regards

Bob

---

### Post by sudodus on 2018-02-25
I suggest that you try according to the following link and links from it,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

If you can remove/unplug/disconnect the internal drive

1. you avoid tampering with the internal drive,

2. you get 'everything' written to the external drive (including the bootloader in UEFI mode).

[hr][/hr]
It is another task to make the computer boot from USB, but if you can make it boot from a live drive (USB pendrive or a memory card connected via a USB card adapter), you can also boot from an installed system in a USB drive.

You may have to turn off secure boot (in the UEFI/BIOS system) and fast startup (in Windows).

- Secure boot might stop you from booting into a USB drive.

- Fast startup is a kind of semi-hibernation, which sets the Windows partitions in a state that should not be mounted by Ubuntu.

---

### Post by bobnutfield on 2018-02-25
Thank you for that link.  That looks like the route I need to take, but I was hoping to find a set of instructions that avoided removing the internal drive because it is not that easy to do.  That may not be possible.

Thanks again.

Bob

---

### Post by oldfred on 2018-02-25
It gets complicated to do a UEFI install to an external if you do not disconnect drive.

You have to manually partition in advance and include the ESP - efi system partition (FAT32), preferably as first partition.
You still must have Windows fast start up off.
And often better to have UEFI fast boot off and UEFI Secure Boot off.
You may still have to in UEFI turn on allow USB boot or similar USB setting like full access.

Grub with Ubuntu will only install its boot loader to the ESP on internal drive. But does not overwrite the Windows folder in the ESP.
While still in live installer, after install, you need to copy /EFI/ubuntu folder from internal drive's ESP to external drive's ESP. You need to then copy again and copy to a new folder /EFI/Boot. Grub only boots from files in /EFI/ubuntu  but UEFI with external drives only boots from /EFI/Boot/bootx64.efi. So you have to rename shimx64.efi in /EFI/Boot on external to bootx64.efi.
You can reset UEFI to make Windows first entry in UEFI  or with efibootmgr. But have to then use one time UEFI boot key to boot external drive. Just like you do to boot installer flash drive.
You also then need to edit fstab with ESP's UUID of external drive as it has UUID of internal drive. Updates will write to the ESP in fstab. You can do this after you boot into external drive.

I have done full installs to flash drives multiple times without issue. 
But I just did a full install to an older SATA SSD in external USB adapter I had, and desktop system fully locked up. My normal procedure of full power down & total cold boot did not work. Only thing that did work was unplugging first internal drive and removing coin battery on motherboard.
Not exactly sure what the difference is between flash drive & my SSD install to cause issues other than use of SATA to USB adapter. Some other threads have users with issues with some USB drive caddy or adapters, but others have worked.

Or sudodus' suggestion of unplugging internal drive is often the easier solution even if drive not particularly accessible.

More info if you cannot unplug drive.
       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL][http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876) 
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 
[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by bobnutfield on 2018-02-25
Well, it's been a very long time since I attempted something like this.  Certainly not like the old days when you just repartition the Windows drive and install.  This just too complicated.  My answer will be to just buy a new laptop, wipe the hard drive and install whatever I want.  This is a clear reminder why I disliked Microsoft for these years.

Thank you so much for taking the time to help.

---

### Post by C.S.Cameron on 2018-02-25
The following has worked for me making an external drive Full install that boots both BIOS and UEFI:

Mkusb will make a Persistent drive that works on BIOS and UEFI.
You can confirm if this works on your machine before proceeding.

It is easy to change a mkusb Persistent USB to a Full install USB that also works on BIOS and UEFI.

Use mkusb to make a Live system on a USB (2GB or larger).
Use mkusb to make a Persistent system on a USB 16GB or larger, using default settings with ~12GB persistence.
Remove HDD before proceeding, (optional but recommended).
Insert both USB drives.
Boot Installer drive, select Install.
Select Something else.
Select sdb5, (the target drive), and click Change.
Select Use as: ext4, Format, Mount point /.
Don't touch any other partitions.
Select sdb5 for boot loader installation.
Complete installation.
Cut grub.cfg from sdb5/boot/grub and paste to sdb3/boot/grub, overwriting the existing grub.cfg file.
Delete sdb4, the ISO9660 partition and expand sdb5 into the recovered space.
Boot the target drive and run sudo update grub, (optional).

---

### Post by bobnutfield on 2018-02-25
Thank you.  That looks doable.  I have another computer with Lubuntu on it, but it doesn't seem to have mkusb and it isn't in the repositories.  I think I recall that Mint has it, so I will look into that.  But, wouldn't I have to install while connected to my target Windows laptop so all the hardware can be configured?  Just a question from my lack of knowledge.  

Dual booting used to be so easy.

Many thanks

---

### Post by C.S.Cameron on 2018-02-25
From [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

```
sudo add-apt-repository universe
```

```
sudo add-apt-repository ppa:mkusb/ppa
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

---

### Post by monkeybrain20122 on 2018-02-25
> **bobnutfield said:**
> Hello Everyone,

I have a newish laptop with an A10-9600P with 8gb ram.  Of course, it has Windows 10 on it and I have to leave it there for my wife (she refuses to use Linux, I despise Windows 10.) 


Maybe just me, it seems that divorce is easier than going through the gymnastic for dualbooting with Win these days. :)

---

### Post by oldfred on 2018-02-25
One user who must be an Ubuntu only user, posted he regularly buys a new laptop, but immediately removes the Windows HDD and installs a new SSD. Then he installs Ubuntu.
Later he restores unused Windows HDD and sells it. He the also does not have to worry about any of his data in Windows, or doing a new full install of Windows before selling system.

I prefer desktop systems, which I build myself and only have Ubuntu on them. Then I have my own hardware configuration and larger screen with separate keyboard for better ergonomics.

---

### Post by bobnutfield on 2018-02-25
> **monkeybrain20122 said:**
> Maybe just me, it seems that divorce is easier than going through the gymnastic for dualbooting with Win these days. :)

I love it!  It's been this way for 18 years now.  She refuses to use Linux and constantly yells "HELP" when something she is doing in Windows goes south.  I haven't  been a regular user of Windows since Windows 98.  I bought her own laptop a couple of years ago and she won't use it now because it is "too slow".  She bought me a new laptop for Christmas (a rather meaty A10-9600P with 16GB of memory).  It had been years since I had a new laptop and I had no clue about UEFI or secure boot or any of the latest Microsoft extortionate threats to manufacturers to lock down their products to make it as difficult as possible to dual boot with Linux.  My plan was to just wipe the drive and install Ubuntu again.  But NOOOOOO!  Since her Windows 10 laptop is so slow, she MUST use my nice new one.  So, if I wanted Ubuntu installed it had to be a dual boot.  So much for that idea.

---

### Post by bobnutfield on 2018-02-25
> **oldfred said:**
> One user who must be an Ubuntu only user, posted he regularly buys a new laptop, but immediately removes the Windows HDD and installs a new SSD. Then he installs Ubuntu.
Later he restores unused Windows HDD and sells it. He the also does not have to worry about any of his data in Windows, or doing a new full install of Windows before selling system.

I prefer desktop systems, which I build myself and only have Ubuntu on them. Then I have my own hardware configuration and larger screen with separate keyboard for better ergonomics.

Not a bad idea, but wouldn't be easy to recoup your investment.  I have had about a dozen laptops in the last 18-20 years.  Starting in 2002, I wiped all of the drives and installed some flavor of Linux.  But it was much easier up until UEFI and secure boot came into being.  I'll probably just buy something fairly recent hopefull just slightly used with no hard drive.  I'll put in an SSD and off I'll go without having to worry about any of this.

---

### Post by monkeybrain20122 on 2018-02-25
> **oldfred said:**
> 
Later he restores unused Windows HDD and sells it. He the also does not have to worry about any of his data in Windows, or doing a new full install of Windows before selling system.
.

I won't bother. If my computer is old enough I probably can't sell it anyway, if it is still working reasonably well I may just give it to a friend, if they want Windows they have to install it themselves.

 If I get a PC from craiglist I would wipe the hard drive even if I were a Windows user, who knows what the previous owner has done with it. Buying  a second hand machine with OS preinstalled is like wearing someone else's underwear :) (unless you buy a refurb from an actual store, but still that may be iffy as OS may be pirated) So I would just sell the machine without OS if I want to sell.

Also it is a mistake to think that only Windows and Mac can sell, it is not 2000 any more. :) There is a local outfit that sells reburb laptops and desktops preinstalled with Linux Mint, their price is unbeatable and they are doing well, many of their customers are semi computer literate people who want a cheap machine for web browsing, social media, music and  videos, that sort of things. In fact it was a definitely non geeky old lady who told me about it. She was bragging to people what a great deal she got and she was extremely happy with the laptop.

---

