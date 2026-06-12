---
title: "Dual boot Xp and Ubuntu with windows bootloader"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Metres2007 on 2007-02-28
I want to dual boot Xp and Ubuntu with windows bootloader. 
I ran the df command. but it did not show which partition linux boot sector is on.
philip@philip-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             34108232  18208508  14167116  57% /
varrun                  517836       112    517724   1% /var/run
varlock                 517836         0    517836   0% /var/lock
procbususb               10240       192     10048   2% /proc/bus/usb
udev                     10240       192     10048   2% /dev
devshm                  517836         0    517836   0% /dev/shm
lrm                     517836     17580    500256   4% /lib/modules/2.6.17-11-generic/volatile

---

### Post by Malac on 2007-03-03
[LIST=1]
[*]Get a DOS formatted floppy
[*] Use df to see which filesystem device holds /boot (e.g. /dev/hdc1)
[*] Insert the floppy disk and enter:
      mount -t msdos /dev/fd0 /mnt/floppy
[*] Substituting your /boot device, enter:
      dd if=/dev/*hdc1* of=/mnt/floppy/ubuntu.bin bs=512 count=1
[*] Remove the floppy and reboot to Windows
[*] Insert the DOS floppy disk
[*] Copy the UBUNTU.BIN file from A:\ to C:\
[*] Open the System Properties window
[*] Click the Advanced tab
[*] Under *Startup and Recovery*, click Settings
[*] Click Edit to open the boot.ini file in Notepad
[*] Add this line to the end of the file and save:
      C:\UBUNTU.BIN="Ubuntu [COLOR=DimGray]*<whatever-you-want-to-put>*[/COLOR]"
[*] Close the Startup and Recovery settings, open it again, and Linux should now appear in the *Default operating system* drop-down menu.
[*] Reboot and test it out 

If you can access your Windows ( "C:" ) partition directly you can miss out step 3 the floppy and dump it straight to your partition replace /mnt/floppy/ with /mnt/[COLOR=DimGray]*<wherever-you-have-windows>*[/COLOR]/ in step 4.

Hope this Helps.[/LIST]

---

