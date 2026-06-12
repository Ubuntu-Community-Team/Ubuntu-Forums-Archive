---
title: "Ubuntu 14.04 on SanDisk Extreme USB 3.0"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by Igor_Diminich on 2015-11-26
I installed Ubuntu 14.04. on a USB without any problem. However, it was a "test" on an old 2.0 stick and Ubuntu was running really slow. I'm considering buying an SanDisk Extreme USB 3.0 (up to 245 mb/s read, 50 mb/s write) - would that give a "smouth" performance?

---

### Post by ubfan1 on 2015-11-26
You will definitely have improved performance with a USB3.0 stick.  Some machines may have trouble booting USB3 though.  I have a little USB3 button with a full install which I use to run on a Windows netbook with acceptable performance (for me).  If you can put up with the slower boot time, adding "toram" (on the linux boot line ) to a live media gives very good performance.

---

### Post by Igor_Diminich on 2015-11-26
Thanks a lot :D

I guess that an external hard drive would give the best performance...?

---

### Post by ubfan1 on 2015-11-26
Most likely.  The USB sticks come in a wide variety of speeds as well as sizes -- pick a fast one for an OS installation.

---

### Post by Igor_Diminich on 2015-11-27
Today I installed 14.04. on my external hdd and it works great.

So, next step:)
Now the disk is formatted to ext4, but windows don't recognize ext. Should I format that disk differently, and then install Ubuntu again? Is it possible to have the same external hdd working with both linux AND windows machines?

---

### Post by sudodus on 2015-11-27
Windows will only recognize partitions on USB drives with the following conditions:

1. It it a Windows files system (FAT32, NTFS) or UDF.

2. It is the first partition (logically, that is partition #1, but it need not be at the beginning of the drive).

-o-

So you can create the first partition and locate it at the end of the drive, and create an NTFS file system with the label **usbdata**.

After that you can create partitions at the head end of the drive for Ubuntu (the root partition and the swap partition). This way you can store data files (pictures, video-clips, documents) in the usbdata partition, and they will be available to both Ubuntu and Windows.

See also this link about making persistent live systems with such an NTFS file system.

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

I do not recommend that you use a persistent live system, you are probably better off with an installed system, but I illustrate how to layout the partition table in order to have a huge usbdata partition, and still no problems to boot the drive. If the Windows partition is greater than 137 GB, and the Ubuntu partition is behind it, several BIOS systems cannot boot. I have tested with a 4 TB drive, and it works like the illustration :-)

---

### Post by Igor_Diminich on 2015-11-27
Thanks.

So, that way I would be able to boot Ubuntu form my external hdd both on Windows and Ubuntu PCs, and the data I create and store on it would be readable and writable in both circumstances?

---

### Post by sudodus on 2015-11-27
If the drivers are compatible, and you can select BIOS/UEFI mode to match how Ubuntu was installed, it should run in many computers without bothering about what is installed in the internal drive.

A live or persistent live system is more portable between computers, but there are other drawbacks. How do you intend to use the system? Only in some computers, that you know well? If you need more detailed help, you can specify the hardware of those computers, and if they are running in BIOS mode or UEFI mode.

---

### Post by Igor_Diminich on 2015-11-27
Well, it's only one or two PCs at the public library (... a great place to work, but I don't want always drag the laptop around town;)). They are both very recent "all in one pc" Lenovos with Windows 8.1

So, **first** I need to create a big NTFS partition at the _end_ of the drive. **Then**, at the _head end_ of the drive I'll create the other two partitions, root and swap. 

Question: the root and swap partitions also have to be NTFS formatted?

---

### Post by sudodus on 2015-11-27
You can expect that the two PCs at the library with Windows 8.1 are installed in UEFI mode. They might be locked such that you are cannot boot them from your USB drive, but maybe not, depending on the policy of the library.

Anyway, a persistent live system with Ubuntu 14.04.3 LTS amd64 (64-bit) would do the job, and an installed system in UEFI mode. (It must be installed in UEFI mode, otherwise you have to edit in the BIOS/UEFI menus, and you should avoid that because it could make it hard for the librarians to get Windows working again.)

The root partition should have an **ext4** file system. The swap partition should have '**linux swap**', which is not a file system, but it is set a the same place in the gparted interface. You can actually let the installer fix the ext4 file system and the linux swap configuration, but it is a good idea to create the partitions with gparted.

---

### Post by Acharn on 2015-11-28
Excuse me, but the initial question asked specifically about the Sandisk Extreme 3.0 USB 3 thumb drive, and I think all the responses were talking about USB 3.0 drives in general. I'm trying to decide whether to go for the Sandisk Extreme 3.0 because it's faster than its competitors, but I've seen that it is not recognized as a bootable device by some computers. My Google searches have been inconclusive, because most of the results are about booting Windows 7 or installing Windows 7 from the USB drive. Does anybody have experience with installing Ubuntu to a Sandisk Extreme 3.0 32 GB USB 3 stick? I don't need to have a FAT32 or NTFS file system on it, I'm never going to transfer data to Windows from it. I just want reassurance that I'll be able to boot from it. I know that I can boot Ubuntu 14.04.2 from my Kingston DataTraveler G4 USB 3.0 stick, but the benchmarks show it's considerably slower than the Sandisk. Works fine, though, and incomparably better than USB 2.0. I can get both for almost the same price here in Thailand, the Sandisk actually a little cheaper, but I don't want to spend &#3647;750 and find out it can't be made bootable.

---

### Post by sudodus on 2015-11-28
Well, I can't issue a guarantee, but I can tell you my experience. I have Sandisk Extreme 3.0 pendrives, 16 GB as well as 32 GB, and both can boot my computers and the computers of my friends, when I have tried. The only exception is a very old computer, that lacks the drivers for USB, but it does not boot from any USB drive.

Sometimes there are problems to boot HP computers from installed systems on USB. It might be fixed by adding the boot flag (although booting from grub should not need any boot flag.) And it is not only affecting Sandisk pendrives but also other brand names.

---

### Post by Acharn on 2015-11-29
Thanks for the reply. I've been dealing with computers long enough not to expect guarantees except (maybe) from the maker. This is just the reassurance I need. I'll go ahead and buy the Sandisk. At the current exchange rate it's only a touch over $20 (the same as it's offered for on Amazon) and I can order it here with no shipping cost.

---

### Post by sudodus on 2015-11-29
@ Acharn,

Please come back and report how the pendrive works for you! Good luck :-)

---

### Post by furtom on 2015-11-29
You can install a driver to allow windows to read your ext4 partitions. I've been doing it for years without any problems. Just be careful what you are doing when you are modifying things. Just accessing data isn't any problem.

this link sums it up nicely:
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by sudodus on 2015-11-29
> **furtom said:**
> You can install a driver to allow windows to read your ext4 partitions. I've been doing it for years without any problems. Just be careful what you are doing when you are modifying things. Just accessing data isn't any problem.

this link sums it up nicely:
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

I've read both positive and negative comments about tools to access ext4 partitions from Windows. I'm glad it works well for you. I guess it is a good idea to avoid writing.

Which tool are you using?

---

### Post by furtom on 2015-11-29
> **sudodus said:**
> I've read both positive and negative comments about tools to access ext4 partitions from Windows. I'm glad it works well for you. I guess it is a good idea to avoid writing.

Which tool are you using?

[Ext2 Volume Manager (Ext2Fsd)]("http://www.ext2fsd.com/"). I think most of the warnings against data loss/corruption are outdated. It's true that permissions can get messed up, which is why I don't do much except with data files. I've always mounted it read/write also.

You just need to remember you have access to the partition as root. In general, you would have to be as careful with accessing your linux partitions in Windows as if you were messing with them in a Live CD Ubuntu enviornment. No more, no less.

I have a big fat ext4 partition with all my data on it. I see no reason not to use it when I have to boot windows.

---

### Post by sudodus on 2015-11-29
Thanks for sharing :KS

---

### Post by Igor_Diminich on 2015-12-03
Thanks a lot... but I'll stick to portable apps, for the time being ;)

I have Ubuntu on all my PCs since 2008, but I never went that "deep" in playing with it, and since my idea was to have Ubuntu on an usb stick to *do more*, well, if I spend hours or days *trying* to put it on a stick - I've just missed a lot of work. 
But, I did bought the SanDisk 3.0 Extreme, and the portable apps work like a charm :p

---

### Post by sudodus on 2015-12-03
Congratulations and thanks for sharing your result :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

