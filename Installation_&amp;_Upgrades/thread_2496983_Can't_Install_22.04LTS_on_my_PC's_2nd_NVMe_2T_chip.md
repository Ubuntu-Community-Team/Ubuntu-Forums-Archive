---
title: "Can't Install 22.04LTS on my PC's 2nd NVMe 2T chip"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by goodbot on 2024-04-18
Hi All:

I installed a new blank (unformatted) 2TB NVMe chip in my notebook PC's second (of 2) available slots ("nvmes1"). My intention was to download the 22.04LTS iso and install it on this chip, where I can afterwards selectively boot to it (I have a long ago installed win10 instance on the first NVMe chip "nvmes0").  

I downloaded and installed (on Win10) the recommended "balenaEtcher" iso writer package.  After running, it looked like I successfully got this utility to write an installation config to the nvmes1 device - I had a p1 (uncited format type) with 5 GB in it, a p2 FAT partition with 5 MB on it; a p3 seemingly of "unformatted" type of 300kb size, and the remainder of the device, p4 unformatted with 1.8TB available.  

When I booted to the chip - the Ubuntu graphical installation screen successfully came up. It gave me the duo option of either running a live demo of Ubuntu (to try it out) or installing Ubuntu. I chose to install Ubuntu. So I stepped through the various options... selecting my US local keyboards, choosing a regular (not minimal) installation, but with all additional options (auto update plus something else) NOT selected. I choose to direct the installation to that large empty unformatted p4 area on the chip. I choose the ext4 type partition.

The installation process started... and soon a status screen appeared with a status message "Detecting file systems". Below this was a small terminal window (minimally expandable) that displayed a log of installation status messages scrolling  by.  

During my first try at this... my patience was 2 hours. After two hours seeing that one same status message and a series of similar terminal messages that may have been in a loop, I force rebooted the machine (back to my Win10 instance). When I inspected the chip, nothing had been written to the p4 partition. 

At midnight before going to sleep, I repeated my earlier installation routine... kicking off the process the same way, again directing the installation to this large empty p4 partition.  The next morning, about 9 hours later, I turned my screen on and discovered that the status message was exactly the same "Detecting file systems" and the installation log terminal window again appeared to be looping a series of the same messages (starting and stopping anaconda, starting and stopping zsystemd.service, couldn't delete a esoterically named file because it couldn't be found)... so I force exited/rebooted the PC.

Once back into my stable Win10 environment, I inspected the device partition info and discovered that the p4 was successfully formatted to EXT4, and contained 31GB of data.

So it took 9 hours to (download?) write 31GB of installation data to my speedy NVMe device.

This is my work day machine. I don't have the time to give it days to do this installation. Apparently there's something going wrong with the installation.  Since the installation did not complete successfully, I' m figuring that if I try it again, it'll just start me at the beginning of the process all over again.

So I'm not able to install Ubuntu LTS 22.04 onto my NVMe chip. Any ideas?

---

### Post by ajgreeny on 2024-04-18
It  sounds as if you are running the live session of Ubuntu from the disk on which you want to install Ubuntu.
Even if you choose a separate partition to install Ubuntu I am not sure if it is possible. 

The simplest way is to create a live Ubuntu install USB, not a hard disk, and then install Ubuntu from that USB on to the hard disk.

Apologies if I misunderstood but your post was not very clear about what you actually did.

---

### Post by tea for one on 2024-04-18
> **goodbot said:**
> 
I downloaded and installed (on Win10) the recommended "balenaEtcher" iso writer package.  After running, it looked like I successfully got this utility to write an installation config to the nvmes1 device - I had a p1 (uncited format type) with 5 GB in it, a p2 FAT partition with 5 MB on it; a p3 seemingly of "unformatted" type of 300kb size, and the remainder of the device, p4 unformatted with 1.8TB available
You should not allow Balena Etcher to write anything to your new internal nvme1n1 disk. You should use balena etcher to "burn" the Ubuntu ISO to a separate thumb drive.
In effect, you will then have an Ubuntu bootable installation medium.
Section 3 here [https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)

The installation should then take 20 minutes approx.
Also, isolate/remove your Windows disk (only have the target disk accessible)
Boot the installer in UEFI mode and create a GPT (partition table) before starting the installation procedure.

---

### Post by goodbot on 2024-04-18
OK... I figured I'd get thinks done faster by putting the Ubuntu installer on a device 1000x faster than a USB stick... I readily achieved my desired 1000x metric,  but unfortunately it was in the opposite (longer time) direction.  I'll go back and start from scratch... and maybe read the documentation ...

---

### Post by goodbot on 2024-04-18
tea for one:  

I confess I was taking a short cut through the woods (putting the installer on the fast NVMe chip instead of the slow USB stick) that got me lost (didn't work).. your highlighted instructions look knowledgeable/seasoned; I'll try following them.

> Boot the installer in UEFI mode

Boot my notebook from the USB stick in UEFI mode? I've never booted my notebook from a USB stick, so I'm not sure where I'll see the option to set this variable (maybe in my bios?)...

> ... and create a GPT (partition table) before starting the installation procedure.

Will the installer process present me this option... or are you saying I need to separately myself create the GPT partition on the NVMeS1 prior to running the installer on it? How about the creation of my desired EXT4 FS... will the installer offer me this option, or again do I have to do this separately myself before I run the installer?

Unfortunately I can't readily do this installation process and stay connected here... both things are on the same machine. 

I have a few hours of work still to do. Once completed, I'll again kick-off my installation attempt following these latest instructions.

Thanks for your help.

---

### Post by tea for one on 2024-04-18
> **goodbot said:**
> 
Boot my notebook from the USB stick in UEFI mode? I've never booted my notebook from a USB stick, so I'm not sure where I'll see the option to set this variable (maybe in my bios?)...
Yes, the setting will definitely exist in the UEFI set up pages.
> Will the installer process present me this option... or are you saying I need to separately myself create the GPT partition on the NVMeS1 prior to running the installer on it? How about the creation of my desired EXT4 FS... will the installer offer me this option, or again do I have to do this separately myself before I run the installer?
Select "Try Ubuntu"
Open Gparted
Create  GPT on your target disk
Then, start the the installation - two partitions, ESP and System partition will be created automatically
> Unfortunately I can't readily do this installation process and stay connected here... both things are on the same machine.
You can use the internet via Firefox during the installation process.
Ubuntu is very versatile
> Thanks for your help.
You're welcome
Looking forward to a successful result

---

