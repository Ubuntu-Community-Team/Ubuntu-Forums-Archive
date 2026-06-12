---
title: "Grub2 Does not boot ubuntu After Install"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by FireDemonSiC on 2014-01-05
It's been a few years since I dabbled with anything Linux so please bear with me.

I have a Dell Inspiron 3521 that I am trying to setup to dual boot Win7 and Ubuntu.

I formatted the drive clean of Win8, then installed Win7 Ultimate x64 in UEFI mode.  Boots great.  So far so good.

I then attempted to install Ubuntu, and it did not recognize windows as being installed.  It did however give the "something else" else so I figured I'd install then clean up the breaks later on.

I formatted a 540GB XFS partition and an 8gb swap partition.  Install completed successfully.  The XFS partition shows up as bootable in the UEFI menu and has over 3GB of used space so I know Ubuntu is there, however it's as if Grub doesn't know where to find it.  When you turn the laptop on you are greeted by a command line with a prompt that says "grub>".

I vaguely remember having to define in the grub config file the partition and kernel path in order to boot Linux but for the life of me I can't remember the process.

Really appreciate the help in advance.

The Win7 install boots fine from the UEFI menu btw.

---

### Post by fantab on 2014-01-06
Boot with Live Ubuntu DVD/USB, Download and install '[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")'....
Run the 'Recommended Repair'... it should fix most of the booting issues. However I am not really sure whether Grub supports XFS or not.

Do note LINK Boot-Repair creates and post the link here.

---

### Post by oldfred on 2014-01-06
Others with unusual partition formats have had issues. Some have just added a /boot with ext4. Some have found a specific grub.cfg in the efi partition's ubuntu folder works. 
Often better to have smaller system partition of 20 or 30GB and then a larger /home or data partition.

grub.cfg with this entry and your partition number. 
       configfile (hd0,gpt8)/boot/grub/grub.cfg

---

