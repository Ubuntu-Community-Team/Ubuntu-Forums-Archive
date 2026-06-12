---
title: "Should I leave open space on hard drive for eventual Ubuntu install?"
date: 2021-08-15
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2021-08-15
Hello,

I am presently using Windows 10 and I have run out of space in the Windows partition on my hard drive. So I am extending the Windows partition to create more space. 

BUT, I want to eventually install Lubuntu and dual boot. I will probably install Lubuntu 20.04 LTS. This only requires 64 bit processor and at least 256MB of RAM to boot and run  the basic desktop environment and about 8GB of space for the  installation according to this webpage [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/) . 

QUESTION(S): Should I leave some space on the hard drive for the eventual Lubuntu install? Or when I install Lubuntu in the future, will the install make room for the Lubuntu on the hard drive by using unused space and also asking me how much space on the hard drive I want to use for Lubuntu?

Thanks,

A.

---

### Post by guiverc on 2021-08-15
> **AbleTassie said:**
> 
I want to eventually install Lubuntu and dual boot. I will probably install Lubuntu 20.04 LTS. This only requires 64 bit processor and at least 256MB of RAM to boot and run  the basic desktop environment and about 8GB of space for the  installation according to this webpage [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/) . 

QUESTION(S): Should I leave some space on the hard drive for the eventual Lubuntu install? Or when I install Lubuntu in the future, will the install make room for the Lubuntu on the hard drive by using unused space and also asking me how much space on the hard drive I want to use for Lubuntu?


[Lubuntu has **not** provided minimum specs]("https://lubuntu.me/taking-a-new-direction/") since Lubuntu 18.04 LTS, or the last release using LXDE. 

Walter (*wxl*) was speaking about a system where you don't add any software packages, update & maintain your system very regularly etc - ie. a minimum installation, and where you don't *release-upgrade* your system, but *nuke & pave* (ie. fresh install to upgrade to the next release).   There are numerous costs implied in that 8GB comment, so don't forget them and take into account how you'll use your system.

The amount of space required varies on what you'll do with your system?  Are you happy not adding any additional packages to your system (ie. Lubuntu provides all you'll ever need *out-of-the-box* ?)  Maybe you're happy with `firefox`, save everything to the web or network servers, will use & update your system regularly (*so upgraded packages don't pile up needing free disk space to download & install*), so that's plenty of space - I don't know.

Personally I'd leave space for another OS; as there are risks involved with *shrinking *any partition to create the space for a new OS (Lubuntu or any other OS).

As to how much space to allow - that will depend on how you'll use your system.  Yes I can install Lubuntu in a 8GB partition (*I've done it in ~12GB in the last week I believe in QA-test installs*), however how I use my systems I would struggle with that size limit & wouldn't want to *live* with a partition that small (*I was only QA-testing the install itself, not living with a partition that small*)

---

### Post by yancek on 2021-08-15
The amount of space needed is basically a personal decision based upon what you will be using it for and what software you will install.  8GB might be OK if it is just a trial but 20-30 would be better.  Use the windows Disk Management tool to modify your windows partition, shrink or enlarge, to leave unallocated space to install Lubuntu.

---

### Post by AbleTassie on 2021-08-16
Thanks guiverk and yancek,

I understand that leaving space, maybe at least 30 GB for Lubuntu would be a good idea. I don't think that is a problem, because the Unallocated Partition is about 275 GB and I do not think I will need anywhere near 275 GB of additional space for Windows 10, **see the attached/inserted screenshot of the partitions on my hard drive.** I had to move the "519 MB Healthy Recovery Partition" that was formerly adjacent to 184.62 GB Windows partition in order to be able to extend the Windows partition to the adjacent Unallocated Partition using the Windows Disk Management tool. I used G-parted to move the 519 MB Healthy Recovery Partition. I have not yet extended the Windows Partition using the Windows Disk Management tool. (yancek-- thanks for the caution to use the Windows Disk Management too to extend the Windows partition; I read that caution elsewhere as well.)   

QUESTION(S):Will there be a problem if the new larger extended Windows Partition is _not_ adjacent to the 519 MB Healthy Recovery Partition? (This does not seem to be a problem now, as I am using the PC now to write this post). In other words, if the unallocated partition is not fully used by windows, then, there will be unallocated partition between the Windows partition and the 519 Healthy Recovery Partition. 

Could that fact that the 519 Healthy Recovery Partition is not adjacent to the Windows Partition be a problem in the future, if/when Lubuntu occupies the unallocated partition that is left after I extend the Windows partition?  

Thanks,

A.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288994&stc=1[/IMG]

---

### Post by yancek on 2021-08-16
Having Lubuntu installed between windows partitions should not be a problem for using Lubuntu.  I'm not sure if your having moved the recovery partition will be a problem if you ever need to use it.  You might try just booting the recovery partition to see if you can or asking the question at a windows forums

---

### Post by AbleTassie on 2021-08-17
> **yancek said:**
> Having Lubuntu installed between windows partitions should not be a problem for using Lubuntu.  I'm not sure if your having moved the recovery partition will be a problem if you ever need to use it.  You might try just booting the recovery partition to see if you can or asking the question at a windows forums

Thank you Yancek,

I just tried to boot into Recovery Mode using manufacturer instructions for my PC and it did not appear to work. I will consult a Windows Forum as well. 

I think I could go ahead and extend the Windows Partition, but leave some space still unallocated for Lubuntu. And then I could move the 519 MB Healthy Windows recovery partition back (using Gparted) so that it is adjacent to the extended Windows partitions and try to reboot into recovery mode and see what happens. I think I will try to consult a Windows forum first, however.

Thanks for your suggestions,

Any more comments from you or others will be appreciated.

A.

---

### Post by MAFoElffen on 2021-08-17
On your last post:
You didn't mention what your hardware was... Or what version of Lubuntu you were trying to boot... Or how it was prepared.

By just looking at your drive mapping that you posted a picture of and knowing it has Windows... In the first 3 partitions, I see the MS reserved system partition, a 100MB partition that is probably the UEFI EFI boot partition and the The Main Windows Partition. So guessing the system is UEFI Firmware BIOS...

Which means the USB device you prepared needs to be prepared to be able boot from UEFI. That is one caveat. The next is that the boot media either needs to have digitally signed kernels to be able to boot in the UEFI Secure Boot mode, or you need to get into UEFI Firmware settings and turn Secure Boot off. Any Ubuntu Branch LiveCD, at 20.04 and beyond, now can boot as Secure Boot...

But is a good idea to go into your UEFI setting and turn off the Fast Boot setting. The Fast Boot setting is a feature in BIOS that reduces your computer boot time,but... If Fast Boot is enabled: Boot from Network, Optical, and Removable Devices are disabled. Video and USB devices (keyboard, mouse, drives) won't be available until the operating system loads. Just saying, a lot of times your need to be able to interact with the computer as it boots up.

Next, whether you plan to dual-boot Linux with or not, please go to your Windows settings and turn off the Windows "Fast Startup" feature. This is different than the BIOS "Fast Boot". The Fast Startup feature in Windows 10 allows your computer start up faster after a shutdown. When you shut down your computer, Fast Startup will put your computer into a hibernation state instead of a full shutdown. That means that the Windows filesystem is still "open". Never a good idea, and at times will cause a data corruption failure. If you turn that off, you can rescue your Windows installation, with a basic Linux LiveCD.

On your thread and original question:
YES.

Even if your were not to install something else... Always a good idea to leave some unassigned space for emergencies, growth and what not.

What I do... Format a 10GB (NTFS) partition somewhere to copy a few ISO files for a system recovery partition. Setup whatever boot loader to be able to boot those ISO's. In case of emergency, you then have options.

Next, on booting that Lubuntu ISO... I notice with 20.04 Ubuntu Branched ISOs, sometimes the screen will "appears" as a black screen when they first boot... USB Thumb Drives are slow... And it's is still running, preparing to start... But appears to the user as not doing anything... In the background, it is checking/verifying the files of the LiveCD... If you just "wait" (seems like forever sometimes...) it will go to the first try/install panel. To speed that up, or to work-around that for those systems...

If your system is one of those that the Grub Boot menu does not appear in the first 3 minutes, reboot and start pressing the left shift key as it boots. At the Grub Boot Menu... Press <E> to edit...<Arrow-Down> until you get to the line that say's "linux"... Then <Arrow-Right> until you get to the word "quiet" and erase it. The Press <Cntrl><X> to boot...

This will then display the boot messages a it starts to boot. This seems to put the graphics in a mode that helps those system see the splash better. At the splash, you will then see the messages in the splash screen on it verifying the LiveCD filesystem before it actually boots. If you are sure of the download, you can press <Cntrl><C> to skip this part. Have patience. Sometimes you have to do that a few times before it actually skips that part...

You can imagine that a basic cheap USB 2.0 thumb drive speed is only (average) about 15mbs to 30mbs. It is going to take a while to get through the 1.9GB of the Lubuntu 20.04 LTS ISO file to verify that...

Then enjoy.

If that doesn't work... then please post back what it did or didn't do. We will then need more of your computer's spec's to help you adjust for that.

---

