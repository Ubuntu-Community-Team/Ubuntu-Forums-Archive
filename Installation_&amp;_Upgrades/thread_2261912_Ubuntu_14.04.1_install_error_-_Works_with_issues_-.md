---
title: "Ubuntu 14.04.1 install error - Works with issues - UEFI - using M.2 Ultra PCIe x 4 as"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by rob-wilkins on 2015-01-21
I installed 14.04.1 on a system with eufi and used a Samsung XP941 PCIex4 hard drive as boot drive in the M.2 Ultra slot on my ASrock Extreme 6 ae motherboard. At the end of the install there was an error that tried to take me to ubuntu as user "Woopsie" but I backed out of it. The install seemed to work, with the exception of some kind of authentication issue.

I get this warning in my sys log:
dbus[1007]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jan 13 03:22:40 rob-desktop kernel: [ 3659.575150] systemd-hostnamed[10364]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Jan 13 03:22:40 rob-desktop dbus[1007]: [system] Successfully activated service 'org.freedesktop.hostname1'

I've been working on the system for a week with no big issues, except there seem to be some user authentication problems. theres an install release application in my programs that when I attempt to use it, it wants to install all over again. Is there a way to authenticate the installation without overwriting my current install?

When I run install RELEASE I choose the something else option and it asks to select a device for boot loader installation. My options are:
[LIST]
[*]/dev/mapper/ubuntu-vg-root with no info for type, mount point, format, size used or system 
[*]/dev/mapper/ubuntu-vg-root ext4 no mount point 494445mb unknown Linux device-mapper (linear) (494.4GB) 
[*]/dev/mapper/ubuntu-vg-swap_1 with no details 
[*]/dev/mapper/ubuntu-vg-swap_1 Type swap, 16852 MB Unknown 
[*]/dev/sdc no info 
[*]free space 1mb 
[*]/dev/sdc1 type efi 536 MB 33MB used 
[*]/dev/sdc2 ext2 255 MB 153 MB used 
[*]/dev/sdc3 511316 MB used-unknown 
[*]free space 0MB 
[/LIST]

When I look at disks in Ubuntu going to settings>disks, my 512 GB Samsung drive using GUID partition Table has three partitions with /dev/sdc1 listed as 537 MB partition type EFI System, Contents Fat(32-bit version) - Mounted at /boot/efi

Anyone know what I need to do to fix this?

---

### Post by oldfred on 2015-01-22
Are you installing in UEFI or BIOS boot mode.

If UEFI you must have an efi partition formatted FAT32 with the boot flag if using gparted to create it. If using gdisk it is code ef00.

If BIOS you must have a bios_grub partition if drive is gpt partitioned. That is unformatted, only needs to be 1 or 2MB. Code with gdisk is ef02.

If BIOS with MBR not special partitions are required.

May be best to see details. With multiple drives do not run any auto fix as that installs grub to every drive.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rob-wilkins on 2015-01-22
Thanks for helping. I am using UEFI and I do have an efi partition formatted FAT32 with the boot flag. My 512 GB Samsung drive using GUID partition Table has three partitions  with /dev/sdc1 listed as 537 MB partition type EFI System, Contents  Fat(32-bit version) - Mounted at /boot/efi

My system boots up fine. I think the part of the install that failed has to do with user authentication due to the warning error regarding nss-myhostname needing to be installed. Where I get into trouble is when certain permissions are required, notably, when I try to download software that requires a purchase transaction. Ubuntu wont authenticate my purchase. I press the buy button and I get a page that says "Bad Request Bad bot, go away" it has a link to log into Ubuntu One, and when I do, manually, I still can't download Steam. I was thinking of doing sudo apt get nss-myhostname to try to fix the install authentication, but I'm not sure if that is a safe idea to attempt. Does that make sense?

I'll study those links you gave me and report back if I find a resolution, but if anything I said here give you an idea for a resolution, please let me know.

---

### Post by rob-wilkins on 2015-01-22
Here's the boot info link: [URL="http://paste.ubuntu.com/9825824/"]http://paste.ubuntu.com/9825824/
[/URL]
The suggested repair seems to want me to use my 2gb raid array (two 2 gb platter drives in raid1) as the boot device, but I really want to keep boot on my 512gb M.2 ultra PCIex4 drive as it is currently. I am not running Windows at all, but may add a seperate OS disk for it at a later date.

Also, the final advice in case of repair says to make my BIOS boot on SDA (2000GB) disk! But I'm booting with EUFI. Does that seem correct?
When it says the boot repair utility would "Purge"... Does that mean it will wipe my current install?

I have Secure Boot disabled in EUFI. I also have CSM disabled.

---

### Post by oldfred on 2015-01-22
While I thought Boot-Repair worked with LVM type installs, it must be having issues.
But you also are showing sda & sdb as RAID devices, so it starts to get very confusing.

I do not see much advantage to LVM on your sdc SSD drive. The LVM is used for encryption, so it that why you have it? Otherwise it adds complications as you cannot use standard partition tools but have to use LVM tools.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

You have two /dev/mapper, one is the LVM and the other is the RAID. It looks like it wants to convert to BIOS boot on the RAID drives. Do not run any auto fixes with Boot-Repair.

---

### Post by rob-wilkins on 2015-01-22
Thanks for your good advice. I really appreciate the help. I did not realize that I had configured the SSD for LVM, that was not something I felt I needed. Is it too late to change that without wiping it and starting over?
I anticipated a learning curve with this build. The M.2 Ultra PCIex4 hard drive as boot drive seems pretty new so far, not to mention adding EUFI and Raid to the picture. My board also has a hybrid Broadcom wifi/bluetooth card that is not quite Linux compatible yet that I thought may have affected the install process as well, but I could be way off base there.

Thanks for the links, I'm checking them out now.

---

### Post by oldfred on 2015-01-23
Afraid the only way to remove LVM is to reinstall. Partitioning is so different.

Always install with hard wired Ethernet. The installer usually supports most Ethernet devices, but only some wireless. Then it is easier to download a correct wireless driver.

Not sure how well desktop supports RAID. Did you end up having to add the RAID drivers afterward, or did the installer uninstall the RAID drivers after install. In my installs I see it uninstall a lot of drivers and software, some that I still want like gparted and then reinstall.

If you have installed lots of software you can export a list of installed apps. And if you have configured system, you want to backup /home to save those settings.

I backup so I can easily do a new clean install. I do run several dumps of configuration and hardware info just to have it, not really required, otherwise.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

