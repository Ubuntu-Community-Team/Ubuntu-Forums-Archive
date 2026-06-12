---
title: "Configuring GRUB for Fedora 9"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by OskarS on 2008-05-17
Out of curiosity, I just installed the new Fedora 9. I don't expect to move off of Ubuntu, but it's nice to check out what's out there.

It installed fine, but in the installation it asked me if I wanted to install a boot-manager. I said no, figuring I already have GRUB nicely set up from Ubuntu, and I figured I can always add the necessary configuration myself. Not so easy, as it turns out.

Fedora is installed at /dev/sda2, which by my reckoning is hda0,1 in grub-speak. I added these lines to my menu.lst file: 

```

title		Fedora Core 9
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.25-14.fc9.i686 root=/dev/hda2
initrd		/boot/initrd-2.6.25-14.fc9.i686.img
quiet
```

The "root=/dev/hda2" part I added when I realized that it didn't work without it. It still doesn't work, however, and I don't know why. GRUB says something like that the files or directories are invalid (it's an ext3-filesystem, so it's not like GRUB can't read it). The filenames are definitely correct. I know that the ubuntu installation has some neato tool that automatically detects operating systems and configures GRUB for you (I know because when I first installed ubuntu, it correctly identified and added my now removed Windows installation). Can I run that again? Or can someone help me with properly configuring the menu.lst file?

Thanks a bunch! You guys are always super-helpful! Cheers.

---

### Post by Herman on 2008-05-17
You should be able to boot Fedora directly by symlinks to the kernel and initrd.img in the root of it's file system. (You don't need to know the exact path and filenames).
Here's a link to help you, [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), and here's another link, [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
Or. if you prefer, use [Super Grub Disk]("http://www.supergrubdisk.org/") and find the menu item for 'Boot Gnu/Linux Directly' in there somewhere, I think it's in 'Gnu/Linux' maybe, that way you don't have to use any command line.

Once you get Fedora booted up, you can probably run the command 'grub-install /dev/sda2' from a terminal. 
That command should install GRUB files in Fedora's /boot/grub and also in the boot sector of your Fedora partition to allow it to be chainloaded by Ubuntu's GRUB.

Either that or, re-install Fedora and make sure this time you install GRUB in Fedora and install it to /dev/sda2 if you can. (Or to MBR if you have to, it doesn't really matter).
[How to back up and restore your MBR]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR")

If you install Fedora's GRUB to the boot sector of /dev/sda2, you can set up Ubuntu's GRUB to chainload it, or boot it by Fedora Grub's configuration file.
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

If you end up installing Fedora's GRUB to MBR, either set Fedora's GRUB up to boot Ubuntu, or re-install Ubuntu's GRUB to MBR and configure Ubutu's GRUB to chainload Fedora.

---

### Post by VMC on 2008-05-17
> **OskarS said:**
> Out of curiosity, I just installed the new Fedora 9. I don't expect to move off of Ubuntu, but it's nice to check out what's out there.

It installed fine, but in the installation it asked me if I wanted to install a boot-manager. I said no, figuring I already have GRUB nicely set up from Ubuntu, and I figured I can always add the necessary configuration myself. Not so easy, as it turns out.

Fedora is installed at /dev/sda2, which by my reckoning is hda0,1 in grub-speak. I added these lines to my menu.lst file: 

```

title		Fedora Core 9
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.25-14.fc9.i686 root=/dev/hda2
initrd		/boot/initrd-2.6.25-14.fc9.i686.img
quiet
```

The "root=/dev/hda2" part I added when I realized that it didn't work without it. It still doesn't work, however, and I don't know why. GRUB says something like that the files or directories are invalid (it's an ext3-filesystem, so it's not like GRUB can't read it). The filenames are definitely correct. I know that the ubuntu installation has some neato tool that automatically detects operating systems and configures GRUB for you (I know because when I first installed ubuntu, it correctly identified and added my now removed Windows installation). Can I run that again? Or can someone help me with properly configuring the menu.lst file?

Thanks a bunch! You guys are always super-helpful! Cheers.

I find this post interesting. I did the exact same thing. What I did was to copy and paste ubuntu to the end of Fedora's Grub menu.list.

I'll be curious as to how you like it. I didn't. Stangely it created a small seperate boot partition that grub was install to, and then it put its partition to my unallocated and use ReiserFS. For whatever reason I don't much like that FS. For one you can't resize it. You can resize inside of it, but the whole partition is locked.

One final thought is that Fedora boot time was a lot greater than ubuntu. I removed it after just a couple of days. I don't like YUM either. In fact this new Fedora9 doesn't seem all that different than the one I installed a few years ago.

Depending on your setup, be aware of that boot partition. It messed up ubuntu's when I removed Fedora. Nothing to do with the "/" or "/home", just grub. A simple grub-install fixed everything. It was just something to play around with. I have ubuntu partition cloned anyway so no worry.

---

