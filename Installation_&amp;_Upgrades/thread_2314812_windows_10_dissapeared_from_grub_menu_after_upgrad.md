---
title: "windows 10 dissapeared from grub menu after upgrading kernel"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by Nathan_Vreeland on 2016-02-24
my windows 10 install is no longer showing up in grub. partition is still there and still flagged boot.

```
sudo parted -lModel: ATA WDC WD3200AAJB-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  157GB  157GB  primary  ntfs         boot
 2      157GB   320GB  163GB  primary  ntfs

```
 i run  upgrade-grub
```
sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.19.0-47-generic
Found initrd image: /boot/initrd.img-3.19.0-47-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

here is ```
 cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

and upon looking in sda1 there is no boot directory or Boot directory. I would rty to fix it with the windows install media, but it is windows 10 and it was installed from an OTA update.
any help would be appreciated.

UPDATE: I found a download link for win10 install media [here]("https://www.microsoft.com/en-us/software-download/windows10ISO"). I'll update again when i make more progress.

---

### Post by oldfred on 2016-02-24
Grub only boots working Windows or even sees it.
That means no hibernation nor chkdsk required.
And Windows 8 or later uses fast start up which is always on hibernation. And Windows updates may turn it back on, even if you turn it off.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

You may want to also houseclean old kernels. I normally only keep 2, one older that I know that works and current. 

 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
# or command line
cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic

If you did leave Windows fast start up on, you have to boot into Windows to turn it off. If on separate drive, directly boot from its boot loader.
If not, you have to reinstall the Windows boot loader with your Windows repair or install flash drive and its repair console. Run fixMBR.
Then you have to restore grub to MBR to boot and run sudo update-grub to find Windows to add it to menu.

While not able to do most Windows repairs, you can use Boot-Repair to install a Windows type boot laoder to directly boot Windows and use it to restore grub.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

