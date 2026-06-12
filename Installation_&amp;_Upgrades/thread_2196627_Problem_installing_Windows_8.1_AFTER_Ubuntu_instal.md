---
title: "Problem installing Windows 8.1 AFTER Ubuntu installation"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by amir-attoun on 2013-12-30
Hey guys --

This questions probably has been asked a million times before, so I apologize. Please move if in the wrong sub-forum.
Sadly, I was never able to find the solution for my exact problem.

**Situation:**

I've decided to wipe my Windows 8.1 setup in favor of a dualb boot Ubuntu / Windows 8.1 setup. (Sadly, I have to partially stick to Windows for various reasons)
What I did:
 
- I wiped my boot SSD
- I installed Ubuntu 12.04 LTS

So far so good. GRUB shows, I can boot into Ubuntu no problem, updated kernel headers etc.
Now, I'm at the point where I want to install Windows 8.1. I realize that Windows 8 seems to further complicate the matter with UEFI (yep, I have one of those Mainboards too!), secure boot etc.....
What I did:

- I booted Ubuntu via USB stick so I could shrink the main Ubuntu partition to make space for windows.
- Formated new space as a NTFS partition.
  GParted info:

 [IMG]http://i.imgur.com/IwYRyAV.png?1[/IMG]


**Problem:**

I can boot the Windows 8 installation for DVD/USB without a problem. I reach the window where you have to choose a partition to install Windows 8 on. I see /dev/sda2 show up okay **BUT** for some reason
Windows refuses to install on **ANY** partitions (ideally sda2...) on the harddrive!!!! 
If i click on the NFTS partition it says: **"Windows can not be installed on this partition" - "Windows cannot install on this disk. The hardware of this computer might not support booting from this disk. Make sure the controller is activated in BIOS".** (roughly translated as it is in German...)
What I tried:

- HD controller is in AHCI Mode (Switching to IDE made no difference).
- Booting from USB or DVD makes no difference. Different images (Windows 8/ Windows 8.1) make no difference.
- Setting the boot flag to the NTFS partition makes no difference.

Welp, this **MUST** have something to do with Ubuntu?! I know that Windows installs perfectly well if I do a fresh installation without any "competing" partitions on the disk. **Does anyone know what is going on here?**
Thank you for your help! Feel free to hit me if the questions is moronic... :p

Amir

---

### Post by dsc1596 on 2013-12-30
Check out [this thread]("http://askubuntu.com/questions/235218/how-to-deal-with-windows-8-boot-partition"). Also, in general it is a better idea to install Windows first, THEN linux. Linux installations are much more tolerant of other OSes on the hard drive than Windows.

---

### Post by oldfred on 2013-12-30
How you boot installer is how it installs. This applies to both Ubuntu and Windows. 
So drive looks like you have it now as MBR(msdos) so Windows must be installed in BIOS boot not UEFI boot mode.
Windows only boots with UEFI from gpt partitioned drives.

It this a full install, upgrade or a image you made of your system?

---

### Post by amir-attoun on 2013-12-31
Hey Guys --

Thank you for your answers!!

> **dsc1596 said:**
> Check out [this thread]("http://askubuntu.com/questions/235218/how-to-deal-with-windows-8-boot-partition"). Also, in general it is a better idea to install Windows first, THEN linux. Linux installations are much more tolerant of other OSes on the hard drive than Windows.

[B]Hm, I'll have a look at the thread. I tried to avoid reinstalling the whole system but if there is no other way....
I already spent a good amount of time customizing ubuntu to my liking (+ installing windows drivers for wifi etc....).
Any easy backup solutions to recommend?[/B]



> **oldfred said:**
> How you boot installer is how it installs. This applies to both Ubuntu and Windows. 
So drive looks like you have it now as MBR(msdos) so Windows must be installed in BIOS boot not UEFI boot mode.
Windows only boots with UEFI from gpt partitioned drives.

It this a full install, upgrade or a image you made of your system?

[B]I'm using a full retail Win 8 disc. When trying to install from USB, I've used the disc as the image.
Yeah, I've realized I need to boot up the installation in BIOS/LEGACY mode. Sadly, neither UEFI or BIOS work.
When booting in UEFI it informs me I have MBR and UEFI need GPT. Anyway, i would like to install in BIOS/LEGACY mode but no dice :-(
It gives me the error from above.[/B]

Cheers,
Amir

---

