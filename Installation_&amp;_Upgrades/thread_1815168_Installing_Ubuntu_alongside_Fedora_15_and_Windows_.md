---
title: "Installing Ubuntu alongside Fedora 15 and Windows 7"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by x0a.cake on 2011-07-30
My question is simple:

How do I make sure that Ubuntu doesn't overwrite the GRUB configuration that Fedora 15 has set and that it merely adds itself to that list?

I have attached a screenshot of the window I am at in Ubuntu as well as a screeshot of Gparted for those who would like to see how my partitions currently look like. I plan to install Ubuntu on the unallocated space.

I'm trying to keep Windows 7, Fedora and Ubuntu on the same drive.

---

### Post by x0a.cake on 2011-07-31
I keep reading around and apparently this is impossible with just Ubuntu. I guess I should just save a copy of menu.lst and install Ubuntu then copy the values to the menu.lst that Ubuntu creates?

I was thinking this wouldn't be necessary because my sd5 partition is mounted as /boot in Fedora, which contains my menu.lst file.

I'm not sure what to do from here. Should I make Ubuntu install the bootloader to sd5?

---

### Post by haresear on 2011-07-31
> **x0a.cake said:**
> I keep reading around and apparently this is impossible with just Ubuntu. I guess I should just save a copy of menu.lst and install Ubuntu then copy the values to the menu.lst that Ubuntu creates?

I was thinking this wouldn't be necessary because my sd5 partition is mounted as /boot in Fedora, which contains my menu.lst file.

I'm not sure what to do from here. Should I make Ubuntu install the bootloader to sd5?

Since no one else is responding, I'll offer some observations, but I suggest you wait for a response from one of the experts here.

If you install Ubuntu, it is not going to create a menu.lst file because Ubuntu is now (since 10.04 and later) using a later version of grub (grub2) that has a more elaborate configuration scheme. Ubuntu will want to install grub2 into the MBR of the sda drive (/dev/sda). It will also try to detect the other OS on your drive -- not sure if it will detect Fedora 15 or not -- I seem to remember some posts of a possible problem with detecting Fedora.

If you really want to retain Fedora's install of grub-legacy in the MBR, you will need to tell Ubuntu to install grub2 somewhere else. The only option I have experience with is to install grub2 to the Ubuntu partition. This is not recommended by the experts, because it is unreliable and may or may not work. I've had two cases where I installed grub2 into the Ubuntu partition. One worked and one did not. For the case that did not work, I uninstalled grub2 and installed grub-legacy into the Ubuntu partition. In this case, a menu.lst file is created for Ubuntu.

Again, I recommend you wait for more expert advice, and perhaps do some reading about grub2.

---

### Post by varunendra on 2011-07-31
> **x0a.cake said:**
> I keep reading around and apparently this is impossible with just Ubuntu. I guess I should just save a copy of menu.lst and install Ubuntu then copy the values to the menu.lst that Ubuntu creates?
If you are using menu.lst file, it means you are using grub legacy. It may not be able to boot ubuntu versions newer than 9.04.

Besides, why do you want to do so when Grub2 (included in Ubuntu) is capable of automatically detecting and booting all your installed operating systems?

I'd suggest to create a logical partition in the empty space (you've already reached the limit of 4 primary partitions), install Ubuntu on it, and for the rest, just go with the default options.

Just for your information and an answer to your original question, it is always possible to prevent grub from being installed during installation (but not recommended in your case). Before starting the actual installation, you are prompted to confirm the partitioning plan. At this stage, the conformation dialogue provides an 'Advance' button which further provides you with the option to install grub(2) on a non-default location, or to not install it at all!

But as I said above, it is best for you not to mess with grub defaults during installation.



**EDIT:**
Oops! Evidently, I'm slow on typing. :) But +1 to haresear. I'm not aware of any problems with fedora. But in case (if) it happens, your current menu.lst file will be safe in its current location because by default grub2 will create its own configuration files in /boot directory of Ubuntu's own partition.

---

### Post by x0a.cake on 2011-07-31
Okay just one (possibly stupid) question:

Why can't I get Ubuntu to install the grub2 to sd5 instead? The 500MB partition in the second screenshot that Fedora created (where menu.lst is stored).

---

### Post by varunendra on 2011-07-31
> **x0a.cake said:**
> Okay just one (possibly stupid) question:

Why can't I get Ubuntu to install the grub2 to sd5 instead? The 500MB partition in the second screenshot that Fedora created (where menu.lst is stored).
You can (following the 'Advance' option I mentioned), but as pointed out by haresear, it is not guaranteed to work. On the contrary, it is more likely for it not to work if installed on a partition rather than the MBR. It just does not like to be installed on a PBR (prtition Boot Record) instead of MBR. :)

If you choose to install it on sda5 (which you shouldn't - for above reason), it will be installed on the PBR of sda5 and its configuration files would still be installed in the Ubuntu partition (in /boot/grub directory). Your current menu.lst file would still be retained as it is and where it is, but won't be effective anymore.

If you also want to place its config. files in sda5 (for reasons I don't understand), you may do so by choosing 'not to install grub' during installation, and install it manually later, setting root-directory=sda5. For more info, have a look at this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
and this:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


And no questions are stupid.. :)

---

### Post by Hakunka-Matata on 2011-07-31
Grub2 should be installed to the MBR (sda, sdb, only), it should not be installed to a PBR (sda3, sdb5).  (**RECTRACTED**, not always true)

---

### Post by haresear on 2011-07-31
> **x0a.cake said:**
> Okay just one (possibly stupid) question:

Why can't I get Ubuntu to install the grub2 to sd5 instead? The 500MB partition in the second screenshot that Fedora created (where menu.lst is stored).

Well, you can I suppose, but that option has the same potential reliability problem as installing grub2 to the Ubuntu partition. I'm not sure if there is any issue with writing into the boot sector of a partition that is used by Fedora. As pointed out above, (and unless you direct otherwise) Ubuntu will create and use its own /boot subdirectory in the Ubuntu partition. If you direct the installer to install grub2 into /dev/sda5, the grub2 configuration (menu) file will be "/boot/grub/grub.cfg". There will be no menu.lst file for Ubuntu, so you will need to manually create an Ubuntu entry in Fedora's menu.lst using grub.cfg as a guide, or create an entry to chainload grub2 in /dev/sda5. You will not be able to boot Ubuntu until you do one of these things, because Fedora's grub-legacy will still be in control of the boot process.

PS - you cannot just copy the entries in the grub2 configuration file (grub.cfg) to Fedora's menu.lst file, because grub2 uses different command syntax. You will need to translate them back into grub-legacy commands.

---

### Post by x0a.cake on 2011-07-31
Thanks to everyone for the replies. I have decided that I'm going to just let Ubuntu install grub2 in /dev/sda.

Now I'm back to the basics: At the first window (which you see in the first screenshot). Do I select the freespace and click on "add"?  Or do I just select it and click on "install now"?

---

### Post by haresear on 2011-07-31
> **x0a.cake said:**
> Thanks to everyone for the replies. I have decided that I'm going to just let Ubuntu install grub2 in /dev/sda.

Now I'm back to the basics: At the first window (which you see in the first screenshot). Do I select the freespace and click on "add"?  Or do I just select it and click on "install now"?

I don't think it is going to be quite that simple. You appear to have a challenging disk partition configuration that might require you to edit the partitions manually, rather than letting the installer make its own automatic decisions.

1. You already have the maximum of four primary partions (one extended), so a new partition can't just be added in the unallocated space. The extended partition (/dev/sda4) will first have to be resized to enclose the unallocated space. Then a new logical partition can be created in the unallocated space within the resized /dev/sda4. I don't know if the installer can or would do this automatically -- personally I wouldn't count on it.

2. Partition /dev/sda6 is an lvm partition. I know nothing about lvm partitions, but I believe not all partitioning tools are capable of handling them safely. I assume this partition was created by Fedora 15, in which case I would try to use Fedora tools to resize the /dev/sda4 partition.

3. I've never tried to resize an extended partition by moving the beginning of the partition while preserving the logical partitions inside, so I don't know if or how it can be done safely. I would do some searching/reading on this situation before proceeding.

---

### Post by x0a.cake on 2011-07-31
I'd be getting myself into a mess that I know nothing about.

I have three empty and spare 80GB laptop hard drives which I could use as external hard drives to install Ubuntu on.

Would you know of anything that I should use to get started on that?

---

### Post by haresear on 2011-07-31
Do you have a way of connecting one of them to your system so it can be seen as an additional hard drive, such as an external usb hard drive enclosure? If so, you would be all set.

---

### Post by varunendra on 2011-07-31
x0a.cake, if you wish to install it on an external drive, make sure to install grub on the MBR of the same (external) drive. This would allow you to boot normally as you currently do, without the need to connect the external drive everytime you boot. In this case, if you let grub install at its default choice, it'll get installed on sda (your native hard drive), and then you will have to connect the external drive every time you boot because of grub's configuration files being located in it.

However, if you chose to install grub on the external drive, you'll have to choose (from BIOS's Boot-Menu) to boot from the external drive whenever you wish to boot Ubuntu. But this shouldn't be a problem since most of the BIOS have a hot key assigned to bring up that boot menu at booting time - mostly F9, F12, Esc or F8. In fact, it is a good choice for this kind of OS installation. (It is irritating to require connecting an external drive just to boot an OS even if it isn't the one installed on that drive.)

If you wish to try fiddling with the extended partition and also want to ensure the security of fedora installed on it, you may wish to create its backup first using clonezilla or remastersys (not sure if remastersys works with fedora or not).

---

### Post by Blasphemist on 2011-07-31
I believe you may want to start over. When you installed Fedora it did some of its default things that are going to make life hard for you and make things more complex. Fedora without guidance uses lvm (logical volume management) and uses a boot partition. The boot partition can be dealt with but it will cause you and extra level of complexity. LVM is another story I think. I'm not sure you can get Ubuntu to install on that.

How much do you have invested in you current Fedora installation? Things will go better if you kill it and fix the partitioning and then install Ubuntu first. After that, you can install Fedora with proper guidance and all will be much cleaner.

What are your thoughts? I have win 7, ubuntu x 4 flavors, Fedora 15 and openSUSE on my laptop. I've gotten to understand the installations and booting these multiple distros pretty well so I can help if you want to do this.

---

