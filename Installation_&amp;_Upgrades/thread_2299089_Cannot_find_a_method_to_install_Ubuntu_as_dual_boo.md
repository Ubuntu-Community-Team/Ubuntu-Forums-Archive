---
title: "Cannot find a method to install Ubuntu as dual boot"
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by igor49 on 2015-10-15
Hello Ladies & Gentlemen. Please forgive me if I am posting this in the wrong forum, but I am brand new to Ubuntu.
I need to install it as a dual boot, I boot from my USB that I made with the Ubuntu Desktop ISO, and I start clicking through the installation process, but it doesn't show me an option anywhere to install it as a dual boot.

What am I doing wrong? Does Ubuntu not allow dual boot? PS, I am trying to do this on my W10 machine.

Thank you very much

---

### Post by agillator on 2015-10-15
Just to alert you, the UEFI requirements make the procedure a little (?) different from the "old" way, so be sure whomever answers addresses Windows and UEFI or you could really screw things up. The 'old' way is to adjust the partitions on the hard drive to make room, install linux in the created space, and then let grub handle the master boot record. Since I haven't been forced into the UEFI nightmare yet I really can't do more than alert you to the difference but this DOES NOT work with today's BIOS (I believe).

---

### Post by mcduck on 2015-10-15
It's not that different to install on UEFI. Just a few things you need to do first:

- make sure you are installing 64-bit version
- Go to your UEFI settings and disable FastBoot/QuickBoot & Intel Smart Response
- in Windows, disable Fast Startup
- Make sure the computer is booting in UEFI mode (it most likely is since you have Windows 10)

After checking those, you should be able to run the install as usual. If you use manual partitioning, make sure you set the EFI boot partition to mount as /boot/efi.

Once installed, you can turn FastBoot and other stuff back on. However if you want to access the Windows partition from within Ubuntu, you should leave Fast Startup disabled. (if you are sure you'll only ever want to read from the windows partition, not write to it, you can enable fast startup and then configure the partition to mount in read-only mode)

More detailed instructions are available here: [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by yancek on 2015-10-15
Did you install windows 10 yourself?  If more likely, it is an upgrade from an earlier version of windows, which one?
Boot the Ubuntu install medium and select the option to Try Ubuntu.  When you get  to the Desktop, hold down the Ctrl+Al+t keys simultaneously to open a terminal.  When it opens type:  sudo gparted (then hit the Enter key) and you should see a windows showing your drives/partitions.  Post that here.  That should give some basic info so others can make suggestions, at least will know if you are using EFI.

---

### Post by igor49 on 2015-10-15
> **yancek said:**
> Did you install windows 10 yourself?  If more likely, it is an upgrade from an earlier version of windows, which one?
Boot the Ubuntu install medium and select the option to Try Ubuntu.  When you get  to the Desktop, hold down the Ctrl+Al+t keys simultaneously to open a terminal.  When it opens type:  sudo gparted (then hit the Enter key) and you should see a windows showing your drives/partitions.  Post that here.  That should give some basic info so others can make suggestions, at least will know if you are using EFI.

Hi Yancek. I installed W10 myself ...but I cannot recall if it was an upgrade or fresh install.
Here is the screenshot from the ubuntu desktop

---

### Post by sandyd on 2015-10-15
You don't have free space to install Ubuntu as a dual boot, and since it's not a good idea to resize the Windows partition to make room for Ubuntu, we can resize the main Windows partition (/dev/sda4) in Windows.

Go to Control Panel -> Administrative Tools -> Computer Management.

There should be an entry named "Disk Management". Choose that, and resize your primary OS disk to make room for Ubuntu. The amount of room you resize is the amount of room your Ubuntu installation will be.

Before continuing on the install, read mcduck's [post]("http://ubuntuforums.org/showthread.php?t=2299089&p=13373704&viewfull=1#post13373704")

When installing, choose "Something Else"

You should be able to see the free space.

Create two/three partitions depending on what you want:

One partition will be the root (/), and should be formated as ext4. The root will hold all your OS data, and user data unless you created a seperate partition for user data (see below). The mount point should be set to "/" (no quotes)

One partition will be the swap and should simply be formated as "swap". The swap is sort of a paging file for Linux, and allows you to hibernate (Only if your Swap is larger than your RAM; Ubuntu does not enable hibernation by default, but it can be enabled)

One partition (Optional) will be for your home folder, which contains your user data. Some people like to have one, some dont't. Its a good idea if you are beginning to test out Ubuntu, as you can reformat the Ubuntu installation without losing your user data.

---

### Post by Geoffrey_Arndt on 2015-10-15
Igor49,  also, it's recommended to restart windows twice after any downsizing of space (first time for win to run chkdsk, and second time to confirm normal boot).    Further, be sure to check if Windows hibernation is turned off, as well as any option for fast/quick boot.   May also need to uncheck "secure boot" until after installation of Ubuntu successful.

---

### Post by igor49 on 2015-10-15
> **sandyd said:**
> You don't have free space to install Ubuntu as a dual boot, and since it's not a good idea to resize the Windows partition to make room for Ubuntu, we can resize the main Windows partition (/dev/sda4) in Windows.

Go to Control Panel -> Administrative Tools -> Computer Management.

There should be an entry named "Disk Management". Choose that, and resize your primary OS disk to make room for Ubuntu. The amount of room you resize is the amount of room your Ubuntu installation will be.

Before continuing on the install, read mcduck's [post]("http://ubuntuforums.org/showthread.php?t=2299089&p=13373704&viewfull=1#post13373704")

When installing, choose "Something Else"

You should be able to see the free space.

Create two/three partitions depending on what you want:

One partition will be the root (/), and should be formated as ext4. The root will hold all your OS data, and user data unless you created a seperate partition for user data (see below). The mount point should be set to "/" (no quotes)

One partition will be the swap and should simply be formated as "swap". The swap is sort of a paging file for Linux, and allows you to hibernate (Only if your Swap is larger than your RAM; Ubuntu does not enable hibernation by default, but it can be enabled)

One partition (Optional) will be for your home folder, which contains your user data. Some people like to have one, some dont't. Its a good idea if you are beginning to test out Ubuntu, as you can reformat the Ubuntu installation without losing your user data.

Thank you Sandy.

Also... what the heck does this mean? "*Don't waste your energy trying to change opinions ... Do your thing, and don't care if they like it."  *What don't I like? I don't understand.

---

### Post by Bucky Ball on 2015-10-15
*Thread moved to **Installation & Upgrades**.*

Sandy's quote is just her signature, not part of her advice to you (about your issue). Read and reflect. :)

---

### Post by igor49 on 2015-10-16
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Sandy's quote is just her signature, not part of her advice to you (about your issue). Read and reflect. :)

Thank you Bucky Ball, thank you everyone, this doofus is going to try to follow some instructions and get this ubuntu installed.

Thanks

---

### Post by Bucky Ball on 2015-10-16
All good. We all start somewhere. :)

sandyd's advice in post #6 (and mcduck's) should do it. You don't have the free space to install so you need to make some is the first step. Booting to Windows and shrinking what is shown here as /dev/sda4, your Windows partition, would be first cab off the rank. Then just boot the Ubuntu install media and follow your nose ...

PS: Once you have created free space, before shutting down the computer, switch off hibernation and fast startup (I think it's called, I don't use Windows) in Win so the machine shuts down completely and Win doesn't 'hibernate' the drive instead. If that happens, problems. 

Probably best to boot to the BIOS before the install and also switch off 'secure boot'. Good luck.

---

### Post by igor49 on 2015-10-18
Bucky Ball, I am so stupid, that it physically hurts. I am afraid I will never be able to install Ubuntu.
Someone, yesterday, recommended to me that I install it on a Virtual Machine, so I installed the Oracle Virtual Box, and through it's wizard I created a partition for enough space and whatever else it required. But now.. I am stuck on this step... screenshot attached

---

### Post by Bucky Ball on 2015-10-18
Why are you going for a virtual machine? That is a step in another direction and questions about that don't really belong on this thread ...

But I will say from your screenshot ... you haven't set up any partitions. Nowhere for the OS to install, and thus you are getting that message. I see the disk, sda, and that's it. You need partitions, at least sda1 and sda2, and to set them up, you need to create them. 

Look for the 'Something Else' method [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"), but as I say, unsure why you're going the VM route.

---

