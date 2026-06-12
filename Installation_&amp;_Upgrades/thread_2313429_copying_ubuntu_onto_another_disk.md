---
title: "copying ubuntu onto another disk"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by theone964-8 on 2016-02-12
Hello everyone.
I have been trying to resolve this myself and since I haven't quite found joy yet I'm turning to the experts.

I recently bought a laptop with Windows 8.1 it came with a 1 TB hard drive .  I have never used this kind of space since I have a desktop installation with Ubuntu 14.04 on it and all my data lives there. I installed ubuntu 14.04 on this drive also and it has worked flamelessly.

So here's what Im trying to do. I have a 320GB hard drive that's perfect for my new laptop and its in good condition too. 

I have already shrank the partitions (gparted) and made backups of each individual partion (opened up disks and clicked on the gears icon and selected create image) (9 of them) from the 1tb. I confirmed that shrinking the partitions didn't ruin anything and that the 1tb drive is still working. I should mention the the laptop has uefi and the 1tb is got formatted.

Now when I restore the partitions to the 320gb and slip the hard drive in the laptop it doesn't boot.

Any help would be seriously helpful.

Thank you

---

### Post by furtom on 2016-02-12
It should be simple. Run a live session from DVD/USB and install boot repair. It should do all the dirty work for you correctly with the click of a button. If it doesn't, post back and well have to take a look.

---

### Post by grahammechanical on 2016-02-12
> Now when I restore the partitions to the 320gb and slip the hard drive in the laptop it doesn't boot.

Does the laptop have the same video adapter as the desktop machine? Did you revert 14.04 to using an open source video driver before you made an image of the disk?

Can you load Ubuntu from the 320GB drive when it is in the desktop machine?

You will need to give a better description of what "doesn't boot" means. At this point we do not know if it means that you do not see a Grub boot menu. Or perhaps you do but Linux does not load to a login screen. Or perhaps it does, but the login fails. Or perhaps you can login but the desktop is lacking a user interface.

If you are not using an open source video driver then there will be booting problems if each machine has a video adapter by a different manufacturer. Even if they have the same video adapter manufacturer there can still be problems if the desktop machine has a newer model than the laptop. It could mean that the desktop is using a newer proprietary video driver that no longer supports the older model in the laptop.

Of course, the reverse situation is also true. The proprietary video drive in the desktop does not support the newer video adapter in the laptop.

Regards.

---

### Post by oldfred on 2016-02-12
How did you image partitions to new drive.

GUID(gpt) has partition guid's in the partition table. So you really should not image, copy, dd, partitions but can do an entire drive.

If GUIDs get out of sync, you may be able to use gdisk or sgdisk to resync GUIDs, I do not know details. 

But Windows may also have issues. Grub would have to be installed. And UEFI entires deleted & readded as they refer to GUID.

 Copy gpt partition table from one drive to another first copies second randomizes GUIDs 
see man sgdisk
But I think this assumes same size drive.
sudo sgdisk --backup=table /dev/sda <br>
sgdisk --load-backup=table /dev/sdb <Br> 
sgdisk -G /dev/sdb <br>


 
[URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/
http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html[/URL]

---

### Post by furtom on 2016-02-12
He shrank partitions, etc. I think he just copied partition by partition. Which is why I suggested the simplest solution first. It may just work!

Windows will certainly have issues, but may be salvageable. We can look at that in a new thread later in the right sub-section. :p

---

### Post by theone964-8 on 2016-02-13
Ok I did the boot-repair method. It now loads and shows several grub entries. I can load up ubuntu and it works flawlessly. However there are several (r) different windows partions and none of them load. 2 of them bring up a recovery screen and the other 2 bring up a message after loading for a while saying one touch recovery damaged and if I click the only available option "ok" it just reboots the laptop.

I tried the sgdisk method but as you guessed it keeps saying that the source is larger than the target, even though the total partition sizes on the 1tb ads up to like 250gb.

So I need help getting my windows 8.1 to load.

---

### Post by sudodus on 2016-02-13
Microsoft uses methods to prevent copying Windows to other computers because it is commercial software, and they want you to pay for using it in another computer. It is possible to make a ***cloned copy of the whole drive*** to another drive of the same size or larger and make it work (with a new hard disk drive in the same computer). If a GUID partition table (GPT) you might need to repair the partition table if the drive has a different size because the backup of the partition information at the end must be moved to the new end. I'm not sure about the details how to do it, but I think you can use gdisk in expert mode to do it.

1. You can use ***Clonezilla*** to clone the whole drive to another drive. Clonezilla can also create a compressed image, and that image can be used by Clonezilla to make a working cloned copy.

2. If GPT you might need ***gdisk***, run in expert mode to get the partition table completely correct.

-o-

It is much easier to copy or clone partitions in order to port an installed Ubuntu system to another drive, because it is free software without any methods to prevent copying.

-o-

You can create ***recovery disks*** from Windows, and use those disks to reinstall Windows into a new drive. It might be the easiest way to migrate a system with Windows in UEFI mode into a new hard disk drive or solid state drive. (This is the method used by millions of people, a lot waiting and work to reinstall your own programs and copying your personal files, but not too difficult.)

After windows is installed you shrink the Windows partition (while running Windows), and reboot Windows and check that Windows will be happy with it.

The next step is to boot from an Ubuntu DVD or USB boot drive and install it (into the unallocated drive space). If you want full control, you can create partitions with ***gparted*** and then start the installer. Select ***Something else*** at the partitioning window.

---

### Post by theone964-8 on 2016-02-13
Thanks for you response. I tried using clonezilla disk to disk with icsd option checked to bypass size checking and somehow it still checked the size and failed.

I think you gave me the best option of reinstalling windows on the new drive. It came preinstalled on the laptop so I just assumed that I wouldn't be able to install it on another drive and the only way would be to clone the drive. Any ideas on how to create the recovery disks? I was able to create a recovery backup but the only seems to work to fix any errors in the 1 tb windows installation.
If I could reinstall windows on the 320gb drive I'd call it a day and just copy the ubuntu or install it.

---

### Post by sudodus on 2016-02-13
Many people describe creating and using recovery disks, but I don't use Windows nowadays, so I can't give you any details except to refer to links via the internet. Maybe the following links are good starting-points

[windows-8/system-recovery-disk](http://windows.microsoft.com/en-us/windows-8/system-recovery-disk)

[How To Use Windows 8 Recovery Disc](http://www.tomshardware.co.uk/faq/id-1653296/windows-recovery-disc.html)

---

### Post by theone964-8 on 2016-02-13
Ok so I created a recovery usb and started the recovery (wiped the harf drive including existing partitions) 
and man is it super slow, after 2 hours it got to 42% and then said there was an error an quit. Any ideas why it would do this?

With this failing I'm back go the original position of not being able to load windows 8.1 on the 320gb hard drive

---

### Post by sudodus on 2016-02-13
Did it work without errors to create the recovery USB drive? Was it complete, when it finished? In that case I don't know what went wrong.

Please give us all information possible, for example what was the error text! Let us hope someone can chip in and help you get further :-)

---

### Post by furtom on 2016-02-13
Ha. I thought it would work, but only for linux. Windows was always going to be a separate matter.

Since it appears you have deleted everything again, anyway, then we'll do this from the beginning the way it should have been done.

You need to first install windows. Do you have Windows 8.1 install media? I'm guessing not. Somehow, you should obtain an installation CD (no need to go into detail about that...) Then install Windows on the portion of the drive you wish and leave the remaining space free. You can migrate your windows data after that. Then use a live environment to create your linux move your partitions back as you already did successfully. Then do boot repair again and your good.

The problem is, since your target drive is smaller than your original, you can't clone the disk.

That's the best way, though I know it may not be easy.

---

### Post by theone964-8 on 2016-02-14
I did exactly that but instead of getting windows 8.1 I just went straight for the windows 10 instead :) 
My windows didn't just activate the way it should've, contacted support and they gave me a new activation key :-)

Problem solved. Thank you guys

---

### Post by theone964-8 on 2016-02-14
Well one slight issue, since I did a clean install I made the windows partition smaller as I rarely use it (Ubuntu is wayyyy better) I made the ubuntu partion larger.

When I copied the image to the drive it worked, but it only shows the old image size so I have like 20gb free instead close to 100gb (I made the new ubuntu partition 80gb or so larger).

 Anyway to adjust anything in ubuntu to make it see/use the whole partition?

---

### Post by sudodus on 2016-02-14
> **theone964-8 said:**
> I did exactly that but instead of getting windows 8.1 I just went straight for the windows 10 instead :) 
My windows didn't just activate the way it should've, contacted support and they gave me a new activation key :-)

Problem solved. Thank you guys

Congratulations :KS

> **theone964-8 said:**
> Well one slight issue, since I did a clean install I made the windows partition smaller as I rarely use it (Ubuntu is wayyyy better) I made the ubuntu partion larger.

When I copied the image to the drive it worked, but it only shows the old image size so I have like 20gb free instead close to 100gb (I made the new ubuntu partition 80gb or so larger).

Anyway to adjust anything in ubuntu to make it see/use the whole partition?

Boot a live session from the DVD/USB drive with Ubuntu, and try with ***gparted*** to edit the size of the Ubuntu root partition. (I suspect that the file system is not expanded to fill the space in the partition.)

Sometimes it is easier to make a fresh install of Ubuntu than to try to copy/clone/expand/shrink an already installed system.

---

