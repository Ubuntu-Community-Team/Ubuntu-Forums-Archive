---
title: "BIOS install issues"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by curvx-007 on 2016-11-11
I have Windows 7 64 bit installed on my 750GB HHD at the moment. Created a unallocated partition of 75 GB for Ubuntu 16.10 64bit installation. Created bootable UbuntuOS in my 4GB Pendrive. I have 3 Drives in Windows i.e; C:/ (~70GB) D:/ and E:/ (~600GB).

Now the issue is

1). I dont have UEFI Capability in my BIOS ie a Legacy One. T.T

2). Installed Windows 7 in "BIOS-Compatibility Mode" as stated in the "UEFI Forced Installation" Window.

3). When I continue to install after booting OS in LIVE mode and selecting "Install Ubuntu 16.10" I m prompt with same issue and when I further continue to install in drive I dont have my "Unallocated Volume" that I created while I was in Windows using Diskmanagement and except my Windows 7 installed Drive every single partition is together as "Unknown" 650GB.

4). Now I need a way to install Ubuntu in the Unallocated Space keeping my Windows 7 intact by Loading the Ubuntu Installer in Legacy Mode instead of UEFI.


What I have Tried So far -

1). Used Rufus to make Bootable OS using "MBR mode for BIOS and UEFI Partition".

2). Used Universal USB Installer.


HELP APPRECIATED.

---

### Post by curvx-007 on 2016-11-11
[TABLE="width: 500"]
[TR]
[TD]"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.

If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.")[/TD]
[/TR]
[/TABLE]


I have Windows 7 64 bit installed on my 750GB HHD at the moment. Created a unallocated partition of 75 GB for Ubuntu 16.10 64bit installation. Created bootable UbuntuOS in my 4GB Pendrive. I have 3 Drives in Windows i.e; C:/ (~70GB) D:/ and E:/ (~600GB).

Now the issue is

1). I dont have UEFI Capability in my BIOS ie a Legacy One. T.T

2). Installed Windows 7 in "BIOS-Compatibility Mode" as stated in the "UEFI Forced Installation" Window.

3). When I continue to install after booting OS in LIVE mode and selecting "Install Ubuntu 16.10" I m prompt with same issue and when I further continue to install in drive I dont have my "Unallocated Volume" that I created while I was in Windows using Diskmanagement and except my Windows 7 installed Drive every single partition is together as "Unknown" 650GB.

4). Now I need a way to install Ubuntu in the Unallocated Space keeping my Windows 7 intact by Loading the Ubuntu Installer in Legacy Mode instead of UEFI.


What I have Tried So far -

1). Used Rufus to make Bootable OS using "MBR mode for BIOS and UEFI Partition".

2). Used Universal USB Installer.


HELP APPRECIATED.

---

### Post by curvx-007 on 2016-11-11
[COLOR=#000000][TABLE="class: cms_table, width: 500"]
[TR]
[TD]"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.

If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.")[/TD]
[/TR]
[/TABLE]
[/COLOR]


[COLOR=#000000]I have Windows 7 64 bit installed on my 750GB HHD at the moment. Created a unallocated partition of 75 GB for Ubuntu 16.10 64bit installation. Created bootable UbuntuOS in my 4GB Pendrive. I have 3 Drives in Windows i.e; C:/ (~70GB) D:/ and E:/ (~600GB).[/COLOR]

[COLOR=#000000]Now the issue is[/COLOR]

[COLOR=#000000]1). I dont have UEFI Capability in my BIOS ie a Legacy One. T.T[/COLOR]

[COLOR=#000000]2). Installed Windows 7 in "BIOS-Compatibility Mode" as stated in the "UEFI Forced Installation" Window.[/COLOR]

[COLOR=#000000]3). When I continue to install after booting OS in LIVE mode and selecting "Install Ubuntu 16.10" I m prompt with same issue and when I further continue to install in drive I dont have my "Unallocated Volume" that I created while I was in Windows using Diskmanagement and except my Windows 7 installed Drive every single partition is together as "Unknown" 650GB.[/COLOR]

[COLOR=#000000]4). Now I need a way to install Ubuntu in the Unallocated Space keeping my Windows 7 intact by Loading the Ubuntu Installer in Legacy Mode instead of UEFI.[/COLOR]


[COLOR=#000000]What I have Tried So far -[/COLOR]

[COLOR=#000000]1). Used Rufus to make Bootable OS using "MBR mode for BIOS and UEFI Partition".[/COLOR]

[COLOR=#000000]2). Used Universal USB Installer.[/COLOR]


[COLOR=#000000]HELP APPRECIATED.[/COLOR]

---

### Post by oldfred on 2016-11-11
Moved to a new thread. You were posting in an UEFI thread and have BIOS issues, I think?
But best to have your own thread as issues often are not the same.

What brand/model system? What video card?

Post this:
sudo parted -l

With BIOS and Windows 7 you often have the MBR(msdos) issue of only 4 primary partitions and must create an extended partition to allow you to install Ubuntu into logical partitions.

---

### Post by oldfred on 2016-11-11
If you have booted live installer in UEFI mode then your hardware is UEFI with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And if you force a UEFI install of Ubuntu it will either erase Windows or convert to gpt partitioning. 
Windows only boots from gpt with UEFI, but must be installed in UEFI boot mode.
Windows only boots from MBR(msdos) in BIOS boot mode.

Both Windows & Ubuntu install in the mode you boot install media.
UEFI systems will offer two boot modes for installers.
Actually you have three boot modes, UEFI with Secure Boot, standard UEFI, and BIOS/CSM/Legacy.

Many UEFI/BIOS do not call it secure boot, but have a setting for "Windows" and "Other" but fine print somewhere says if installing Windows 7 you must use "other". Windows 7 does not support Secure boot, so it has to use the non-Windows or really non-secure boot setting.

Post this:
sudo parted -l

---

### Post by oldfred on 2016-11-11
OK, I saw new posts in another thread but did not pay attention to user name and made new thread.

But then saw you also posted your own thread. Merged both threads.

Please do not post same question in multiple places as that dilutes forum help. 
We all are volunteers and need to know what has already been posted, so as not to duplicate effort.

---

