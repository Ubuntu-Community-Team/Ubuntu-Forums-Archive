---
title: "How can I create a WORKING dual boot system with XP and Ubuntu?"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by christiandransfield on 2006-06-29
I've been trying to create a dual boot system with XP and Ubuntu, but can't seem to get XP to work. I install XP first and then install Ubuntu. Ubuntu runs fine, but when I choose to boot XP, it shows the XP loading screen, but then shows me the 'blue screen of death' for a fraction of a second and then restarts the computer.
My laptop is a Tiny laptop with Athlon64 3400+ processor, Ati Radeon 9600 graphics card and 1gig memory. 
Does anyone have any ideas what the problem might be?

---

### Post by glotz on 2006-06-29
Well, since it starts to boot the windows, it's out of the GRUB and Ubuntu territory. It's some crazy windows issue. I think you might be looking at a windows reinstall + GRUB reinstall...

---

### Post by Malac on 2006-06-29
The way I did it was to install XP onto the first partition.
Then install Ubuntu onto the second partition.
To do this I did the following:
You will need a bootable DOS disk with a copy of fdisk.exe on it.[LIST=1]
[*]Choose to install Ubuntu on the second, unused partition (aka D)
[*] When asked, choose GRUB as the boot loader
[*] Install GRUB on the first sector of the /boot partition
      *Important: If you tell it to install on the drive's       master boot record (MBR) you wipe out Windows XP's boot selector.       Not what you want.*
[*]Make sure this partition (/dev/hda2) is active i.e. bootable
[*]Reboot, it should go into Ubuntu
[*] Login and get to a shell
[*] Use *df* to check which filesystem device holds /boot (e.g. /dev/hda2)
[*] Insert the DOS floppy disk it should be mounted automatically but if not  mount it. (*sudo mount -t msdos /dev/fd0 /media/floppy*)
[*]Substituting your /boot device, enter:
      dd if=/dev/hda2 of=/mnt/floppy/bootsect.ubu bs=512 count=1
[*]Reboot off the floppy
[*]You will need to set the first partition active but this can be done with fdisk.
[*]Remove floppy and Reboot.
[*]**Set up the Windows boot menu**
[*] Boot into Windows XP if you're not already there
[*] Insert the DOS floppy disk
[*] Copy the BOOTSECT.UBU file from A:\ to C:\
[*] Open the System Properties window
[*] Click the Advanced tab
[*] Under *Startup and Recovery*, click Settings
[*] Click Edit to open the boot.ini file in Notepad
[*] Add this line to the end of the file and save:
      C:\BOOTSECT.UBU="Ubuntu"
[*] Close the Startup and Recovery settings, open it again, and Ubuntu should now appear in the *Default operating system* drop-down menu.
[*] Reboot and test it out[/LIST]Hope this Works for you.
If not let me know.

---

### Post by RRS on 2006-06-29
Did Windows boot normally before you installed Ubuntu?

After the restart does it boot into Windows OK or does the BSOD/restart sequence keep repeating?

---

### Post by christiandransfield on 2006-06-29
Windows XP works fine before I install Ubuntu. I then install Ubuntu and it keeps restarting whenever I try to run XP. It keeps on restarting every time I try to load it up and never actually loads up.

---

### Post by leo_m on 2006-06-29
Although I am not very sure, but it could be that you did not have any partitions for Ubuntu (I mean, no linux partitions) before you installed Ubuntu and you created new linux partitions using Ubuntu utilities during installation of Ubuntu.  That could have resulted in your Windows getting confused about where to find Windows startup files...

Can you paste here the contents of boot.ini file which would be there in your Windows partition.  Also, can you do an fdisk <your hard-drive, such as /dev/hda> and paste the results of the p command while in fdisk UI?

---

### Post by christiandransfield on 2006-06-29
I've already formatted it and just put XP on. I'll try Malac's guide sometime before the end of the weekend and let you know if there are still any problems.

---

### Post by RRS on 2006-06-29
While I don't claim enough experience to properly analyse Malac's instructions and I'm sure his method works well but  it does seem a bit complicated.

I've done 3 dual boot installs following [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") with no problems, as have many others.  

You might want to check it out before reinstalling Ubuntu.

---

### Post by wifiabc on 2006-06-30
I followed these instructions for safe dual boot, windows XP untouched. 
[http://www.justlinux.com/forum/showthread.php?t=130715]("http://www.justlinux.com/forum/showthread.php?t=130715")

---

### Post by leo_m on 2006-07-01
As an addendum to that guide, with Windows XP, one hard-disk and no floppy-drive etc.:

Caveat: This scheme does not work if your installer does not have the facility to give you a shell with fdisk command, or does not allow to set bootable flag on partitions arbitrarily, or does not automatically set bootable flag on the Linux partition on which you install Grub.

As in Guide, when installing Linux, DO NOT install Grub onto MBR, instead install it in the Linux partition.  Be sure to make the Linux partition active, so that the next time, Linux is booted instead of Windows when you reboot after finishing the installation.  I think that Windows MBR just loads the boot-sector from the active partition, so that next time Linux will load upon restart because you have made sure that Linux  partition where you installed Grub is marked active.

Once you boot into Linux, assuming grub is on partition /dev/hda2:

```

dd if=/dev/hda2 of=/boot_lin bs=1024 count=1

```

then if Windows partition is FAT32/VFAT, mount it and copy the file to that partition:

```

mkdir /mnt/windows
mount -t vfat /dev/hda2 /mnt/windows
cp /boot_lin /mnt/windows

```

If it was an NTFS partition, the above step for copying does not apply; instead we shall copy the file when we boot into Windows.

Lastly, we want to mark Windows partition active again:

```

fdisk /dev/hda

```
Then type 'a' to toggle bootable flag on the partition, do it for Windows partition and Linux partition (the first will make Windows partition bootable, the second will unmark Linux partition - this 'a' command is a toggle for bootable flag).  Write the changes with 'w' and exit from fdisk.

Reboot. You should land into Windows with no trace of Linux. If you did not copy the /boot_lin file earlier, download explore2fs (a small program to read linux partitions from Windows).  Copy the file /boot_lin from Linux onto the Windows boot partition if not done already.

Edit boot.ini to create an entry to that file.  Also set a reasonable timeout.

Reboot.

You should get a menu which has entries for both Windows and Linux now.

Having said this, I do not remember when I tried this combination.

I usually want to have two menus - one Grub, one Windows - both by default pointing to the other OS (e.g., Windows bootloader's default entry set to Linux, Linux bootloader's default entry set to Windows), so both menus keep loading each other after timeouts until I deliberately select one of them to boot.  Perhaps you would want that behaviour, perhaps not.

I also prefer to keep Grub on MBR instead of boot record, but  NOT while installing Linux.  So, when installing Linux, I install Grub NOT on MBR but on Linux partition, then when I boot into Linux [remember to set Linux partition as active - if your installer does not allow that (ie, setting Linux partition as active, by using fdisk during installation), then you cannot use my method].  After installation, I boot into Linux, unmark Linux as active partition and mark Windows partition as active partition, then use dd command to take a backup of MBR (dd if=/dev/hda of=/mbr bs=1024 count=1) just in case I need to restore Windows MBR in future, then  a grub install on MBR, thus overwriting the Windows MBR, then doing a dd of MBR again naming the file to mbr_lin and pointing to this file in Windows boot.ini as the second entry to make the menus point to each other unless user makes a choice)

If you adopt what I like to do (as in para above), you have copies of grub boot code in the Linux partition as well as MBR and in the Windows bootable partition as the file mbr_lin; and this gives you great flexibility, in that you could now restore Windows MBR and still load Linux from the Windows menu because that menu now has an entry pointing to C:\mbr_lin, the file which stores Linux MBR.  You also have Linux boot code on the Linux partition which you can use to boot by marking that partition as active.

It is a good idea to take a backup of boot-sector code for both Windows (/dev/hda1) and MBR (/dev/hda) because you may use Linux to restore these in case these sectors get affected by some virus code...

I took 1024 bytes insead of 512 bytes while taking backups of boot-sectors/MBR because I had read some quirk about Windows somewhere, do not remember exactly, but it should not hurt to take 1024 bytes instead of 512...

---

