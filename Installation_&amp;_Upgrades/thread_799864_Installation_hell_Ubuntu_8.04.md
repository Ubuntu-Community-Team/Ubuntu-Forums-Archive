---
title: "Installation hell Ubuntu 8.04"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by _33 on 2008-05-19
Under the advice of a forum user at blitzbasic.com, I've registered to this forum to follow suit on the issues I have with my installation of Ubuntu 8.04 !!!  It's very well possible that all new Linux installations have a hard time on my system, but Ubuntu is the first one I am trying as I wish to get into the Linux OS for learning and usage.

First here is the link to the old thread: [http://www.blitzbasic.com/Community/posts.php?topic=78100](http://www.blitzbasic.com/Community/posts.php?topic=78100)

Right now, I have no clue where to point in this installation.  But so far, here is what I have done:
- Installed the Ubuntu 8.04 AMD X64 edition cd content on a 30 GB partition created by the Windows installer of Ubuntu form Windows XP SP3.
- Reboot my system, boot manager works, shows 2 OSes (first one being Windows, second one Ubuntu)
- Proceeded with installing Ubuntu but it rebooted from it's loading (as described in the blitzbasic thread)
- Rebooted, selected Ubuntu on the boot loader, then ESC, chose the second alternative installation which circumvents stuff.  This one shows a trace of the install.  One of the comments in the trace was "complain to your system vendor" or something in the likes !!! Anyhow it showed a funky backdrop when it finished showing up a bunch of checklist stuff saying most often OK, some were FAILED...  Then a window showed up over the backdrop with a progress bar and names of stuff it was installing like OO 2.4 and others.  Finally, it ended up back on a command line with a $ (or was it %) and 2 seconds later rebooted.
- Selected Ubuntu once more, but then it gave me an Error 15 !!!

What to do?

My system:
- Mainboard is DFI Lanparty UT NF4 Ultra (with onboard Marvell gigabit LAN, Nvidia Nforce 4 chipset)
- 2GB DDR400 memory
- Nvidia Geforce 8800GTS 512mb graphics display adaptor (G92 gpu)
- One nvraid RAID0 partition built using two(2) Western Digital WD2500JS 250GB SATA hard drives, which is set as DRIVE C: (this is not the boot drive)
- One Samsung Spinpoint F1 750GB SATA hard drive, which is set as DRIVE H: containing my primary Operating System (Windows XP SP3) and now a faulty 30GB Ubuntu partition.

I have to add that in the text that was showing off from the installation process, that Ubuntu didn't properly detect my onboard Marvel Gigabit LAN (seconds before it locked and rebooted)

You'll also note that I had problems detecting my USB keyboard, but that was a mistake on my part, as the BIOS indicated that the USB keyboard feature was disabled, which I re-enabled after notice.

Also, how do you remove the faulty installation now?

---

### Post by dstew on 2008-05-19
I read your previous thread. I appears you installed onto the 30 Gb partition, but the computer reboots at some point as its loading the operating system. Is this correct?

It seems you booted in Recovery Mode at one point, and were able to see the system messages. To get a good idea of the failure, we need to analyze those messages. If you can get your Recovery Mode boot to stay on (not reboot) perhaps we can look in the boot logs for an answer. Try hitting enter, or enter a command to see if you can keep it from rebooting. If you can't keep it from rebooting, look at the messages to see if you can see why it is rebooting.

Also, did the Live CD system work for you? Did you get a functional desktop? Did you install from the Live CD, or Alternate Install CD?

EDIT: The Ubuntu installer will not recognize your RAID, so take that into consideration when installing. It will recognize the RAID after installation if you install the dmraid program.

As far as removing the installation, just delete the partition. However, it you installed the grub boot loader, it will still be there, and you will have to use Windows recovery tools to restore the boot record.

---

### Post by _33 on 2008-05-19
I'm a total newbie on Linux when it comes to installing!  How do you get the logs when you can't even boot the Linux install in the first place?  It stays in the boot manager with an error 15 code when I select Ubuntu :(

C: is my RAID0 setup on SATA (2x 250GB, NTFS)
H: is the boot on SATA (Samsung 750GB) also containing Windows XP SP3 (NTFS) and the broken 30GB partition install of Ubuntu

---

### Post by dstew on 2008-05-19
Which boot manager are you using? Can you boot Windows?

Did the Live CD system work for you? Can you get a functional Live CD desktop? If so, we can de-bug your system.

---

### Post by _33 on 2008-05-19
I'm super newbie, the boot manager is the one that comes with the Ubuntu 8.04 AMD x64 install.  The only time I got a graphical interface was when it tried to install the packages.  And when it rebooted (I don't know why it did) on the install form a shell prompt, I never got back to the desktop since the boot manager can't find the Linux install in the first place.

EDIT:  Here is the message when I try to run either Ubuntu 8.04 generic, 8.04 recovery mode, or the memtest using Grub4dos 0.4.3
> Booting 'Ubuntu 8.04,kernel 2.6.24-16-generic'

 Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a65c24995c246671 loop=/ubuntu/disks/root.disk ro quiet splash acpi=off noapic nolapic

error 15: File not found

Press any key to continue...

---

### Post by dstew on 2008-05-19
I have no experience with Grub4Dos. The error message looks like a regular grub boot item, but I do not know much about configuring Grub4Dos, so I don't think I can help you much.

I know that grub error 15 (at least with regular grub) means that the disk and partition exist, but the file could not be found. In this case, the file might be the kernel image /boot/vmlinuz. The error message tells us that the root disk has an ntfs file system type, which is not usual for a Linux file system. This suggests that the boot loader is mis-installed or mis-configured. But, since I don't know much about that particular boot loader, I can't help you further.

---

### Post by _33 on 2008-05-19
Well, the 30GB Ubuntu partition was created from Windows with the Ubuntu CD menu 9Wubi) middle option; install in windows.

---

### Post by avtolle on 2008-05-19
> **_33 said:**
> Well, the 30GB Ubuntu partition was created from Windows with the Ubuntu CD menu 9Wubi) middle option; install in windows.
Since you used Wubi, please look at the Wubi subforum:
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234)
where there may be something of assistance to you.

---

### Post by _33 on 2008-05-20
> **avtolle said:**
> Since you used Wubi, please look at the Wubi subforum:
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234)
where there may be something of assistance to you.

But it has bnothing to do with Wubi, in the sense that I can't even load the CD's Kernel correctly without a solid reboot.  This happens and when the prograss bar is around 9/10th filled.  But when I try to install Ubuntu from Wubi, the partition gets created, the CD content gets copied, but then when I boot the partition, I get a bunch of errors.  I'll try to gather a trace if I have the courage to re-install this.  I'm not sure but I think it has a hard time with my SATA setup.

---

### Post by molafish on 2008-05-20
Why not trash the install from windows attempt and just boot from an installer CD?

Use the partition editor to make sure you don't doink your windows install. Being a "total newbie" here would not be good...

It's definitely not usual to have your /boot partition be NTFS.

You should have at least a swap partition and a root partition for your linux system. I also use a seperate /boot partition (all but the swap partition should be a filesystem such as ext2 or ext3). You set this up in the ubuntu installer's partition editor.

---

### Post by _33 on 2008-05-20
> **molafish said:**
> Why not trash the install from windows attempt and just boot from an installer CD?

Use the partition editor to make sure you don't doink your windows install. Being a "total newbie" here would not be good...

It's definitely not usual to have your /boot partition be NTFS.

You should have at least a swap partition and a root partition for your linux system. I also use a seperate /boot partition (all but the swap partition should be a filesystem such as ext2 or ext3). You set this up in the ubuntu installer's partition editor.

Agreed, but as stated above, the Ubuntu install CD doesn't want to load, it reboots by itself.  That is why I tried the Wibu for an install.  But the outcome is basically the same: "incapacity for the distro to recognize / use the SATA hardware (it seems)."

---

