---
title: "Booting after Uninstall?"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Naatan on 2007-01-06
Hi,

Im currently using ubuntu on vmware, however I also installed it on a seperate harddisk, at the moment when my computer boots up ubuntu gives me the choice to startup ubuntu or windows (windows is on the primary hd, ubuntu on secondary).

When I select windows it gives me the default windows boot screen.

My question, I want to format my secondary hard disk, which currently has ubuntu on it. However, will I still be able to boot up on windows afterwerds?

I suspect I will but I just want to be sure.

Thanks in advance.

---

### Post by Naatan on 2007-01-06
Anyone........ ?

---

### Post by orb9220 on 2007-01-07
Well the easy way is to boot up with your xp disk and enter recovery mode.

Use the Windows Setup floppy disks or the Windows CD-ROM to start your computer. At the "Welcome to Setup" screen, press F10 or press 'R" to repair.

After you start the Windows Recovery Console, you receive the following message:
Microsoft Windows(R) Recovery Console

The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.

1: C:\WINDOWS

Which Windows Installation would you like to log on to
(To cancel, press ENTER)? 

type 1 and enter
then type fixboot and enter
or fixmbr and enter 

and that should do it.


FIXBOOT


fixboot drive name:
Use this command to write the new Windows boot sector code on the system partition. In the command syntax, drive name is the drive letter where the boot sector will be written. This command fixes damage in the Windows boot sector. This command overrides the default setting, which writes to the system boot partition. The fixboot command is supported only on x86-based computers.

FIXMBR
fixmbr device name

Use this command to repair the MBR of the boot partition. In the command syntax, device name is an optional device name that specifies the device that requires a new MBR. Use this command if a virus has damaged the MBR and Windows cannot start.

---

