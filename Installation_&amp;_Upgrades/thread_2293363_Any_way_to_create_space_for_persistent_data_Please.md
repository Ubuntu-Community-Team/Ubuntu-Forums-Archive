---
title: "Any way to create space for persistent data? Please read details"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-09-04
I've used Unetbootin a few times with great success, but I've recently come across Rufus and decided to test it out.  It does not seem to have a persistent data option, but the creator of Rufus seems to think it's possible to create the space after booting into the OS.

"Once you boot the OS, you should have everything you need to create some  space for persistent data, so there's no real need for Rufus to do  that. "

Source: [https://github.com/pbatard/rufus/wiki/FAQ#Do_you_plan_to_add_Linux_persistent_data_support_eg_for_Ubuntu](https://github.com/pbatard/rufus/wiki/FAQ#Do_you_plan_to_add_Linux_persistent_data_support_eg_for_Ubuntu)

Or am I misunderstanding the statement?

If it's possible, can anyone show me how?

Also, using Unetbootin, if I don't want to install any heavy software on the live USB but just little stuff like customizing the panel, setting wall paper, setting the screen brightness to level 5 at start up, how much space would you recommend for persistent data?

Thank you!

---

### Post by sudodus on 2015-09-04
1. If Unetbootin works well for you, I suggest that you use it in order to create a persistent live system. That is by far the easiest way.

2. If you want to add persistence to a system, that you made with Rufus, I think the easiest way is to boot from another drive (assuming you have another pendrive or a DVD disk or an installed system with Lubuntu.)

- ***Unmount*** all the partitions on the target drive (that you made with Rufus)
- Start ***gparted***
- Shrink the main partition to release drive space at the end of the drive
- Create a partition in the free space at the end of the drive
- Create the **ext2** file system in that partition
- Put the label **casper-rw** onto the ext2 partition

Now, when you boot from the Rufus drive, edit the linux command: add a space and the word **persistent** at the end, and continue the boot process.

'It is easy when you know how to do it', but definitely more complicated than using Unetbootin or some other tool, where it is prepared automatically.

3. If you want to try something else, I suggest that you try [mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10), which can make these things automatically (create a casper-rw partition and supply booting from grub with the boot option 'persistent' already there).

---

### Post by KayeNg on 2015-09-06
"Now, when you boot from the Rufus drive, edit the linux command: add a space and the word **persistent** at the end, and continue the boot process."

I don't quite get that.  Is your statement missing something?  Apologies, I'm not an expert Ubuntu user.

---

### Post by yancek on 2015-09-06
> I don't quite get that.  Is your statement missing something?  Apologies, I'm not an expert Ubuntu user. 		

He is referring to the boot menu you see on boot.  The option to edit the boot entry on boot.  You add the word 'persistent' to the end of the linux line.  This is with Grub as I believe unetbootin uses syslinux/isolinux which uses kernel to begin the line with thee kernel entry.  Not sure how or if this works with syslinux.  Not much lost in trying as it won't change anything on your system.  Maybe sudodus will post back with more specifics.

---

### Post by ubfan1 on 2015-09-06
I'm not sure about doing editing at boot time for syslinux, but the file to change is /isolinux/txt.cfg.  The line on which to add the word "persistent" is a line starting with "append" just after a line starting with "kernel".  That's a permanent change, but it assumes you have a file named "casper-rw" in a FAT partition or a partition with an ext? filesystem labeled "casper-rw" as a location to actually write out the data to save.

---

### Post by sudodus on 2015-09-07
> **sudodus said:**
> 1. If Unetbootin works well for you, I suggest that you use it in order to create a persistent live system. That is by far the easiest way.

2. If you want to add persistence to a system, that you made with Rufus, I think the easiest way is to boot from another drive (assuming you have another pendrive or a DVD disk or an installed system with Lubuntu.)

- ***Unmount*** all the partitions on the target drive (that you made with Rufus)
- Start ***gparted***
- Shrink the main partition to release drive space at the end of the drive
- Create a partition in the free space at the end of the drive
- Create the **ext2** file system in that partition
- Put the label **casper-rw** onto the ext2 partition

Now, when you boot from the Rufus drive, edit the linux command: add a space and the word **persistent** at the end, and continue the boot process.

'It is easy when you know how to do it', but definitely more complicated than using Unetbootin or some other tool, where it is prepared automatically.

3. If you want to try something else, I suggest that you try [mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10), which can make these things automatically (create a casper-rw partition and supply booting from grub with the boot option 'persistent' already there).

If you find it difficult to edit these things manually, I suggest that you use a tool that does it for you, at least now. Maybe later you can start experimenting. The following link may help for the Ubuntu family syslinux systems.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I don't use Rufus, so I don't know the details of its boot configuration.

---

