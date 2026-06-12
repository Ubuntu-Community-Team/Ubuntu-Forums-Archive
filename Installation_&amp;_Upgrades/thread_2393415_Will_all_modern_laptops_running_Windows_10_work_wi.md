---
title: "Will all modern laptops running Windows 10 work with Ubuntu?"
date: 2018-06-03
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2018-06-03
Some time ago, I spent ages trying to figure out how to dual-boot Ubuntu and Windows. My impression was that Windows 10 changed the BIOS settings so that it was increasingly difficult to dual-boot without good knowledge of the intricacies of the UEFI / BIOS system.

However, if I want to remove Windows 10 (from a new laptop) and install the latest version of Ubuntu (single boot), will this work for any modern laptop? Can I just buy an Asus or Acer (for example), run the ISO from flash memory, and have the hard drive dedicated to Ubuntu?

Or is there something more specific where some Windows 10 laptops will allow Windows 10 to be replaced with Ubuntu and some will not? I don't want to get a new system, remove Windows 10, and discover that Ubuntu doesn't run. Thanks.

---

### Post by TheFu on 2018-06-03
It isn't like it was 5+ yrs ago when UEFI was new. Almost all modern laptops work.  There might be some models that don't follow UEFI standards or have locked boot loaders, and I would avoid those since you'll need to manually fix stuff in /boot/efi/ forever or wait for a hack to get in.  

3 steps.

1) Flash drive testing
 Take a flash drive with an Ubuntu ISO on it into a store and boot off it there with the customer service guys watching.  They shouldn't have any issue with that, just explain that you want to boot Linux too.  When you boot, use the "try ubuntu" option and test out networking (wired/wifi), sound, video playback and I'd look at **inxi** output to get a full list of the insides.  Do this on a few of the different laptops there and take notes.  

2) Do specific Linux boot research
I think the MSFT-Surface line might have locked boot loaders and some HP models a few years ago didn't follow EFI standards. That might have changed. I don't know. Check.  Look at specific models.

3) New SSD/HDD for Linux install
After that research, buy the laptop you want, also buy a new HDD. Pull the original HDD out and put it on a shelf, since you'll need it for any warranty stuff anyways.  Then install Linux onto the new disk inside the machine.

Ultra-cheap, low-end laptops might not have storage that can be replaced. These have eMMC storage, usually 32G or less. Best to avoid those when you are really good at Linux and storage stuff. I've put Linux on a few chromebooks, but was able to avoid eMMC storage.  One of them was relatively easy and the other requires that I manually fix the boot file locations after every install.  Both required that I violate the warranty, there is a physical screw that has to be removed to short an electrical connection, but that is required for all chromebook installs of Linux.

Hopefully someone else here will post with all the current links about UEFI and secure boot stuff.

At least, that is what I would do.

---

### Post by oldfred on 2018-06-03
Most systems work, but many have unique requirements and need some sort of work around. 

Acer is unique in that within UEFI, you have to set "trust". Many with UEFI installs have explained details and not really difficult and better than some other systems that violated UEFI spec and only boot by description. And only valid description is "Windows Boot Manager". 

But if only booting Ubuntu you can make the description be Windows but actually boot grub/Ubuntu. They do not check actual boot file, just description in UEFI.

Also some systems may need Windows to update UEFI. Most have other ways like directly from within UEFI from a file in a FAT32 partition, or a DOS boot flash drive with update files & program. Many may have those options, but only explain the from Windows option.

So best to save a few dollars on new system and get it with HDD, and separately purchase SSD  and install Ubuntu onto that as suggested by TheFu.

---

