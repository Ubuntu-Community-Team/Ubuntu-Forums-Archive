---
title: "Can't install 16.04 or 17.10 - not possible to install the bootloader"
date: 2017-12-12
forum: Installation &amp; Upgrades
---

### Post by David4321 on 2017-12-12
* I had a bad crash, OS corrupted, I was running 16.04.
* I replaced my motherboard with a brand new one, it's an ASUS Maximus X Formula.
* I burned the current downloads for both 16.04 & 17.10 to disc on another system.
* I tried installing, both failed with that error, "not possible to install the bootloader".
* I've been choosing LVM, and no partition changes, erase & install.
* I tried to install on another hard drive, with both again, same result.
* In all cases, install screen froze, and I was unable to continue with no bootloader, or cancel. Had to force quit.
* Plenty of RAM, i7 CPU, new board, only OS drive & DVD connected, wired connection.
* I'm desperate, I have a heap of work to get done yesterday.

What could be going on? More importantly, what can I try? Thanks!

---

### Post by sudodus on 2017-12-12
Is the live system ('Try Ubuntu' booted from the install disk) working well?

In that case you can use the computer like that or a step better, make a persistent live system, and **do the most urgent tasks with such a system**. If you can make the computer boot from a USB drive, you can try to make a persistent live system with mkusb,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Otherwise, please tell me if you must boot from DVD, and I will suggest how to make a persistent live system.

-o-

After that we can focus on a full installation, which might be tricky with very new hardware because linux might not have fully implemented everything for it to work yet.

---

### Post by brian666 on 2017-12-12
I had these exact same symptoms in trying to install both Xubuntu and now Ubuntu Studio, both 17.10 and 16.04 LTS. What I found was that I got into that loop when I tried to install the bootloader to a disk which was > 2 TB in size - well, OK, it might be specifically a 4TB drive - and if I got the error and then tried to select the smaller drive, I was just stuck, as you say. NONE of the options - change drive, no bootloder or cancel - worked, I had to use the power button. 

The solution I found was to put the bootloader on a drive that's less than 2 TB, ***_and you must select this option right at the start. _***

Once I pointed the bootloader to the sole remaining 1.5 TB drive in my system, everything worked perfectly.

***_AFTERTHOUGHT_*** I admit that I am guessing that the magic limit is 2TB. What I can say for certain is that the installation got into this 'cannot install bootloader' loop when pointed at either of my 4TB drives, but the installation worked perfectly on a 1.5 TB drive.

---

### Post by sudodus on 2017-12-12
@brian666,

Interesting information. Was/is there an MSDOS partition table or a GUID partition table (GPT) on the 4 TB drive?

---

### Post by brian666 on 2017-12-12
Yes, a GUID table - I was running Debian 9 with grub on /dev/sda (the 4TB drive). Debian's version of grub had no difficulty with the large drive, BTW. I had previously tried Ubuntu, but got into a problem (which turned out to be a hardware fault) and had reverted to Debian as part of my efforts to solve the problem. I then ended up with a new barebones system but took all of my drives across, and it was in reinstalling the drives in the new system that I managed to switch the order in which the system 'found' the drives, and so ended up with a 4TB drive as sda. I had tried Ubuntu again, but it was only last night that the penny dropped and I switched to pointing the installer at the 1.5 TB drive to install grub, and now everything worked flawlessly. 

I think the installer has two problems :-

1) Not installing to the large drive. Whether the existing (Debian) information is the cause of that problem or not, I can't say. 

2) That loop which gives you the option of switching the target drive for grub, cancelling or continuing without a bootloader doesn't work.

---

### Post by David4321 on 2017-12-12
Thanks, I'll try USB tomorrow. Hardware is new to me, but not new build, it's a bit backdated actually, to cope with my older socket.

Original drive is 250gb SSD, other one I tried was 500gb HD. Just an OS drive.

---

### Post by oldfred on 2017-12-12
With gpt partitioned drives, you have to have either the ESP - efi system partition (FAT32) or the bios_grub partition (unformatted) depending on which way you want to boot UEFI or BIOS.
But that is if gpt drive is seen as sda. If you have another drive as sda, and gpt drive is sdb or higher, you then must have ESP on sda for UEFI install. BIOS install will work if you during Something Else install select sdb as grub boot loader install drive. Selecting drive does not work with UEFI installs.

I suggest & use for all new gpt drives (all my new drives are gpt including larger flash drives) these two partitions as first two. Even for data only drive, just in case later you want to add an install to drive.
 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

### Post by David4321 on 2017-12-12
I really appreciate the attention Oldfred, but you're talking over my  head here. I'm not a newbie, but I don't really understand terms like  gpt, ESP - efi, & UEFI. I haven't been messing with partitions at  all, I'm just looking for a clean erase & install on a 250gb SSD. I  have data drives that are disconnected until I get system up, but the  only drives connected in install are the SSD & the DVD.

If you can turn any of that into suggested steps to get a successful install, or diagnostic steps, I'll be super grateful. 

And I'm about ready to pay someone for attentive focused support until success, does Canonical have a paid support option?

---

### Post by sudodus on 2017-12-12
Canonical has paid support (I think mainly intended for companies); you can ask for the price. If too expensive you can come back and ask here again (for free support from us (volunteers)).

[hr][/hr]
How is the live system working for you? Did you try a persistent live system?

---

### Post by QIII on 2017-12-12
Hello!

You need only say that things are going over your head and ask that the techie-speak be broken down into more understandable terms for you.  We're all here to help and most will take the time to be clear.

Paid support from Canonical is likely to be prohibitively expensive for personal use.

Cheers!

---

### Post by brian666 on 2017-12-12
> **oldfred said:**
> With gpt partitioned drives, you have to have either the ESP - efi system partition (FAT32) or the bios_grub partition (unformatted) depending on which way you want to boot UEFI or BIOS.
But that is if gpt drive is seen as sda. If you have another drive as sda, and gpt drive is sdb or higher, you then must have ESP on sda for UEFI install. BIOS install will work if you during Something Else install select sdb as grub boot loader install drive. Selecting drive does not work with UEFI installs.

I suggest & use for all new gpt drives (all my new drives are gpt including larger flash drives) these two partitions as first two. Even for data only drive, just in case later you want to add an install to drive.
 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)


Well that's all fair enough as it goes, but there's still a problem with the installer - because obviously NO combination of circumstances should lead to a situation where the only way out is the power button. That piece of code which is the result of grub not being able to be installed needs some attention, because there is simply NO way out of it once you get there. Even the option to cancel the installation didn't work! 

It would also be a great improvement if there's a known problem like this if there could be code to test for it BEFORE you go through the rest of the installation. Setting all your partitions up and then installing the system only to hit that unexitable loop can wear a bit thin, to put it mildly. 

Thanks for the (presumed) solution, though (I say presumed on the grounds of my not having tried it). Perhaps Ubuntu should 'borrow' the installation routines from Debian? :-;  In any case, it all worked for me once I selected the option for grub to be installed to the smallest drive, so I'm not complaining (well, not too much...)

---

### Post by David4321 on 2017-12-12
I do see that the desktop support has a 50 system minimum, not for single user. I AM saying that the recent response was over my head, and I'm urgently seeking suggestions for getting Ubuntu re-installed.

The "try Ubuntu" doesn't seem worth spending time trying to work in, I need my applications & data on a stable system. I didn't try the persistent live system option yet, because it seems like another time consuming thing to try to understand and implement, and time is so precious right now. I really need help just getting full install to work. Thanks again.

---

### Post by sudodus on 2017-12-12
It is getting late here. I can help you for half an hour tonight, and then continue tomorrow. So you need help from somebody else.

-o-

You can start by telling us as much as possible about your hardware. For example, you can run the following command from Ubuntu live

```

sudo bash -c 'lshw -sanitize > lshw.txt'

```

and then copy and paste the content of the output file  lshw.txt into a reply here and render it as code like this

[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by kansasnoob on 2017-12-12
Looks like this is the motherboard:

[https://www.asus.com/us/Motherboards/ROG-MAXIMUS-X-FORMULA/specifications/](https://www.asus.com/us/Motherboards/ROG-MAXIMUS-X-FORMULA/specifications/)

And I see it's definitely UEFI BIOS. Since there is no data to save on the drive you're using, and you're going to use the entire drive try exactly these steps:

#1: Boot the Ubuntu Live DVD/USB and **make sure it boots in UEFI mode**. When booted in UEFI mode the boot screen should be black with white text: 

[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_UEFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_UEFI_mode)

#2: Once you're booted to the live desktop in UEFI mode open Gparted, select the target drive (it would be wise to have only the desired target drive installed), click on Device and select create partition table. **Be sure to select gpt from the dropdown menu**.

#3: Close Gparted and proceed with the installation as you desire. Since you're using LVM there's nothing to really tweak.

#4: If the LVM install fails I assume that we're dealing with a bug (or at least a fluke) so repeat the above steps but do just a normal non-LVM, non-encrypted entire disc install and see if it also fails.

---

### Post by sudodus on 2017-12-12
I know that you tell us details about the hardware in your opening post.

If you cannot run the command with lshw, maybe you can add some details according to this list:

- Brand name and model of computer or motherboard: ASUS Maximus X Formula
- CPU - generation of i7?
- RAM (size)
- internal drive (size)
- graphics chip/card
- wifi chip/card

---

### Post by David4321 on 2017-12-14
Thanks everyone for your help. I was able to find someone on upwork who helped me get it installed using Rufus to make a flash drive installer. I succeeded with LVM, but updates and 3rd party software did not install. This seems like a significant issue with the installer that many are encountering, I wish I could stay and help troubleshoot further. It seems the installer should have functioning options, even if it encounters difficulties with hardware, etc, and this is a serious bug.

---

### Post by kansasnoob on 2017-12-15
> updates and 3rd party software did not install

Updates are only downloaded during installation, not installed. If you had to wait for all updates to be installed it would take a very long time if it had been months since the initial release.

Some 3rd party software does install during installation if you request it, but not all can be without either increasing the size of the .iso image considerably or changing the  software sources used by the live image. It seems like it does usually install broadcom wifi drivers and intel-microcode, but NOT nvidia drivers or amd-microcode.

IMHO it would be best to just remove those options from the installer anyway since both tasks can easily be performed post-install :)

---

