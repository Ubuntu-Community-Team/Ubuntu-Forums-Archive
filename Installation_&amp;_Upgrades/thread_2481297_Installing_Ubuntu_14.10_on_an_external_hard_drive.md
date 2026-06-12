---
title: "Installing Ubuntu 14.10 on an external hard drive"
date: 2022-11-24
forum: Installation &amp; Upgrades
---

### Post by rtroxel2 on 2022-11-24
Hi, everyone,

I'm almost ready to take the plunge and install Ubuntu 14.10 on my LaCie 1-Terabyte external hard drive which connects to my custom-made PC via USB.

Here are some of the PC's specs:

16GB of RAM
64-bit operating system, x64-based processor
Windows 10 Home version, on a 465GB internal hard drive

The installation will, I hope, create a dual-boot setup, though the Ubuntu OS will be on the external drive, not on the PC's hard drive. I plan to set up the BIOS (or UEFI - I'm not sure of the difference) to first see the Ubuntu OS; however, if the external drive is not plugged in, then the boot system will bypass Ubuntu and go to the Windows 10 OS.

This seems cut-and-dried to me, but is there something I should know before I begin the installation?

Thanks, in advance,

Roy

---

### Post by ne29914 on 2022-11-24
Yes. Why would you want to install an outdated version of Ubuntu?
Current is 22.04.1 LTS.

---

### Post by ubfan1 on 2022-11-24
Danger Will Robinson! See launchpad bug 1396379 Grub wrong disk
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Several workarounds are present in the bug report.
Basically, a straight install will simply ignore your input on the location for the bootloaders and use the first EFI partition it finds, on your hard disk. Leaving you with no bootloaders on your second disk, and grub on your first disk, but needing files on your second disk, so without the attached disk, grub fails.

Workarounds range from removing the hard disk, disabling the hard disk in UEFI settings, or just running a terminal in parallel with the install (install from the try option), and unmounting the hdd's EFI from /target/boot/efi and mounting the target's efi there.

And do use 20.04 or 22.04 or 22.10, not some long EOL release (which would still have the ancient bug mentioned).  Do add your self to the bug's "Does this affect me?" list.

---

### Post by rtroxel2 on 2022-11-24
> **ne29914 said:**
> Yes. Why would you want to install an outdated version of Ubuntu?
Current is 22.04.1 LTS.

I have the 14.10 DVD for Ubuntu. I've installed this several times since it was released in 2015. and was usually prompted if I wanted to install the latest version. I would answer, yes, and would download the 18.00 version, or whatever. That was a few years ago, of course, but wouldn't I get the same prompt this time?

Thanks,

Roy

---

### Post by crip720 on 2022-11-24
Question becomes why install an old version and then download and install a newer version, when you can do the same thing faster by installing a new version first.  14.10 is so old now that a direct install of a newer version might not be possible/easy.

---

### Post by rtroxel2 on 2022-11-24
> **crip720 said:**
> Question becomes why install an old version and then download and install a newer version, when you can do the same thing faster by installing a new version first.  14.10 is so old now that a direct install of a newer version might not be possible/easy.

OK, I just downloaded this latest version of Ubuntu onto my blank external hard drive: ubuntu-22.04.1-desktop-amd64

Can I just run it on the drive to install it?

Thanks,

Roy

---

### Post by TheFu on 2022-11-24
> **rtroxel2 said:**
> OK, I just downloaded this latest version of Ubuntu onto my blank external hard drive: ubuntu-22.04.1-desktop-amd64

Can I just run it on the drive to install it?


No. The ISO needs to be place onto an empty Flash drive (8GB is a good size for this) and booted by the computer to be installed.  There are many tools to do this. Etcher is a bloated, but clear one to use: [https://www.omgubuntu.co.uk/2017/05/how-to-install-etcher-on-ubuntu](https://www.omgubuntu.co.uk/2017/05/how-to-install-etcher-on-ubuntu)  Of course, Linux has built in programs that can do the job, but those require specific knowledge about how storage devices, partitions and other storage types are named.  Linux is enterprise-capable, so storage isn't simple like with _that_other_OS_.  Etcher has been around.  Get the appimage version if you are using a Linux computer to create the installation media from the ISO downloaded.   Inside etcher, you'll say which ISO file to write to the USB Flash storage.  Then you'll shutdown and boot up being certain to boot from that flash storage. Then the Ubuntu ISO will ask if you want to install or "Try Ubuntu".  Best to choose the "Try" option and test that networking, sound, and video work.  If they don't, stop and ask for help.  

If it isn't clear, everything on the flash drive will be gone.  Also, you'll want to keep it as it is, since any boot issue will likely need it to help resolve the issue.  

You mentioned wanting to run this from an external drive.  If that drive is empty, it should work fine.  If you have files there and it is formated for use by some other OS, then the file system likely is wrong for what is required for any Linux to work.  So you'll want to make room for a few partitions to be used by the installer and to run the OS and have data.  If you don't know much about file systems, choose ext4 for all of them.  With 22.04, you'll want at least 40G of space to install, not counting room for data.  It is smart to keep the OS and data on different partitions.  NTFS cannot be used for the OS.  The OS cannot be shared with other existing data. Any partition you point the installer at will be wiped.

22.04 is a good choice. Standard support for it ends in April 2027.  Be certain to patch weekly if you use it on the internet.  I'm a little worried that all the GUI "cheese" will be hard for a 2014 computer to handle.  You might chose to have a more responsive system by running Xubuntu or Lubuntu or Ubuntu-Mate, but the support for those is only 3 yrs.  Linux Mint is another option. It follows the Ubuntu LTS releases and can be nice for lots of people. I think the default GUI is Cinnamon, which is lighter than Gnome or KDE. Should work well enough on a 2014-period computer.

I'm not a fan of dual booting with Windows.  At least once a year, MSFT will break your ability to boot Linux with one of their forced updates. Especially if you are new to Linux, I'd strongly suggest using a virtual machine solution to run Linux at least for a few months.  Then all sorts of issues go away because the hypervisor ( buzzword for the virtual machine controller software), will only offer to emulate the most common hardware that is well supported, unlike what we each have in the real world.  For non-games, these virtual machines will perform fine as you become used to Linux.  Also, all sorts of dangers with dual boot setups breaking disks, partitions, and accidentally overwriting each other go away. The host computer OS controls access to storage for the "guest VM".  Cameron's post below will address that during the install.

BTW, don't expect that the boot manager will like it if it expects an OS to be there and it isn't available.  UEFI booting shares a single EFI boot area for all OSes.  They have to be on the same partition.  If you do something different, don't expect the motherboard BIOS to be happy. If you have Win10, that came preinstalled, then it is a UEFI booting computer and you should use that for Linux in dual boot mode. Doing anything is asking for lots of hassles - well - more than dual booting alone.  Dual booting is a hassle.  I've been using virtual machines since the 1990s and essentially put my main desktop into a VM in 2008.  It has made all sorts of things possible that aren't otherwise, with just a few negatives.  Of course, those negatives can be the entire issue for some people.

---

### Post by C.S.Cameron on 2022-11-24
I would suggest unplugging your internal drive before proceeding, (you can't break what is not there).
Plug in the external drive and install Ubuntu as normal.
Plug in the internal drive, boot Ubuntu and run ```
sudo update-grub
```
This will add your internal OS to Ubuntu's boot menu.

Edit:
If you plan on using the external drive on other computers, it might be good to create a drive that boots BIOS and UEFI. 
[https://askubuntu.com/a/1403793/43926](https://askubuntu.com/a/1403793/43926)

---

### Post by yancek on 2022-11-25
Follow the suggestions above by writing the iso of Ubuntu to a flash drive.  It is possible to boot the Ubuntu iso on a hard drive but you will need a bootloader capable of doing this such as Grub2.  If you don't have that on the computer, it won't boot.  The other caveat is that even if you had Grub2 and could boot the iso, it would be a "live" system similar to having it on a flash drive and you could not save any changes and I doubt that is what you want.

---

### Post by rtroxel2 on 2022-11-25
Thank you, everyone, for your suggestions.

Roy

---

### Post by C.S.Cameron on 2022-11-27
For a UEFI booting computer, you can just extract the ISO to a FAT32 or NTFS partition, (either on the USB or HDD).
UEFI will boot it. 
It may have a different name in the UEFI  menu than the ISO.

---

### Post by rtroxel2 on 2022-11-27
> **TheFu said:**
>   At least once a year, MSFT will break your ability to boot Linux with one of their forced updates.

Whoa! If MSFT's midnight downloads can mess up the OS, then a dual boot is not for me. Fortunately, there is a technician in town here who can build a PC to my specs, and I can install Ubuntu directly to it. I think I'll give him a call.

Thanks again for all the tips and info,

Roy in New Mexico

---

### Post by TheFu on 2022-11-27
> **rtroxel2 said:**
> Whoa! If MSFT's midnight downloads can mess up the OS, then a dual boot is not for me. Fortunately, there is a technician in town here who can build a PC to my specs, and I can install Ubuntu directly to it. I think I'll give him a call.

Thanks again for all the tips and info,

Roy in New Mexico

Or run one of the OSes inside a virtual machine.  I never understand why people avoid that.  Any 2-core system from 2010 on can do it, provided there is at least 6GB of RAM.  Performance is good to great for most VMs.  If you have a Core i3 or Ryzen 3 (or better), the VMs will fly too.  We have all this hardware. Why not use it?

For most people new to virtual machines, the tool, VirtualBox is the normal first tool used.  It is simple, runs on Windows and Linux with guests for either possible.  Basically, the hypervisor (virtualbox in this case) provides virtual hardware for the guest VM to use.  So, setting up the VM entails giving it some CPU, RAM, video, storage and networking.  The guest gets installed onto that hardware and will not break out of that hardware, so when you give it 40G for the HDD, that's all the disk it will see locally.  During the install, when it says to wipe the entire drive ... that's just the fake 40G virtual drive, not the storage on the host machine running the hypervisor.  There must be 500+ vitdeos showing how to setup Ubuntu inside virtualbox on Windows ... or a similar number for how to setup Windows inside a virtualbox running on Linux.  Your choice.  Plus, the ISO file can be provided to virtualbox as installation media directly - no need for any flash drive to perform the install.

Virtualization is a great tool for your kit, even if it doesn't work out for your needs, knowing about it and having the 45 minutes of experience using it will open your eyes.

---

### Post by ian-weisser on 2022-11-28
> **TheFu said:**
> Or run one of the OSes inside a virtual machine.  I never understand why people avoid that.

Oh, goodness yes. That's the best answer.

I stopped dual-booting over a decade ago when VMs became reliable. No regrets. Smooth and easy.

---

### Post by yancek on 2022-11-28
I agree that using virtual software is the simplest solution for new users.  Some windows updates will put windows at the top of the boot order on an EFI machine and turn on Secure Boot, both of which are fairly simple to change but for users not familiar with it, virtul software will be better.

---

### Post by rtroxel2 on 2022-11-28
> **yancek said:**
> I agree that using virtual software is the simplest solution for new users.  Some windows updates will put windows at the top of the boot order on an EFI machine and turn on Secure Boot, both of which are fairly simple to change but for users not familiar with it, virtul software will be better.

So where do I find a Virtual Machine? I'm assuming it doesn't come packed with Windows 10.

Thanks, as always,

Roy

---

### Post by TheFu on 2022-11-28
> **rtroxel2 said:**
> So where do I find a Virtual Machine? I'm assuming it doesn't come packed with Windows 10.

Thanks, as always,

Roy

> VirtualBox is the normal first tool used
Google will find the download easily. [https://www.virtualbox.org/](https://www.virtualbox.org/)  Windows has their own VM hypervisor, but few people here use it.  VirtualBox is the most commonly used for people new to Virtualization.  
The vbox manual is here:   [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)

When you decide to switch to Linux as the OS running on the physical hardware and place Windows into a VM, there are many, many, many, more great options for hypervisors.  Most of the worlds internet servers are running on the KVM/QEMU hypervisor that isn't too hard to setup on any Linux desktop.  All that power, for free. What's not to love?

---

### Post by rtroxel2 on 2022-11-28
> **TheFu said:**
> Google will find the download easily. [https://www.virtualbox.org/](https://www.virtualbox.org/)  Windows has their own VM hypervisor, but few people here use it.  VirtualBox is the most commonly used for people new to Virtualization.  
The vbox manual is here:   [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)

When you decide to switch to Linux as the OS running on the physical hardware and place Windows into a VM, there are many, many, many, more great options for hypervisors.  Most of the worlds internet servers are running on the KVM/QEMU hypervisor that isn't too hard to setup on any Linux desktop.  All that power, for free. What's not to love?

Sounds good, Fu. So if I install Virtual Box on my Windows 10 machine, I can then run Ubuntu 22 in the virtual box, or will I be running Windows 10 in the virtual box?

Many thanks again,

Roy

---

### Post by TheFu on 2022-11-28
> **rtroxel2 said:**
> Sounds good, Fu. So if I install Virtual Box on my Windows 10 machine, I can then run Ubuntu 22 in the virtual box, or will I be running Windows 10 in the virtual box? 

In theory, you can run any x86 operating system made, one at a time, or 50 at a time, depending on resources.  After all, they all need CPU, RAM, disk, networking, so in reality, there are limitations.  With 16G and a dual core system, I've run 20 VMs, but I wasn't using virtualbox.  I may have run 4 VMs concurrently under virtualbox.  The hostOS doesn't matter much.

---

