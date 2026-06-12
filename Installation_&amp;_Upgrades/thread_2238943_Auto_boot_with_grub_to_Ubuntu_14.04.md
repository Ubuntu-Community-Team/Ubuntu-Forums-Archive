---
title: "Auto boot with grub to Ubuntu 14.04"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by rxt on 2014-08-11
I installed Ubuntu 14.04 on a Lenovo Ideapad, which was quite a hassle. I've got it running, and can startup. But... when I start up I boot into the grub commandline. Then I have to enter the following three commands:

```
linux (hd0,3)/boot/vmlinuz-3.13.0-32-generic root=/dev/sda3
initrd (hd0,3)/boot/initrd.img-3.13.0-32-generic
boot
```

It's nice to know this, but I don't want to do this all the time. So I created the following file in /boot/grub/menu.lst, like described in the grub manual:

```
title Ubuntu
root (hd0,3)
kernel /boot/vmlinuz-3.13.0-32-generic
initrd /boot/initrd.img-3.13.0-32-generic
```

This doesn't result in normal booting, and I still enter the grub commandline. How can this be fixed?

---

### Post by grahammechanical on 2014-08-11
The first thing you should know is that menu.list was useful in Grub legacy. But Grub has not used menu.list for a few years now. In Ubuntu 14.04 we have Grub 2.0. That uses grub.cfg in /boot/grub/. But the Grub developers do not want us to edit that file. Instead we are given scripts in /etc/grub.d/ that we can edit.

When we run update-grub the script runs grub-mkconfig and that draws in all the information in the grub.d scripts and creates grub.cfg for us.

I suggest that you try this command

```
sudo update-grub
```

and see if the printout shows Linux kernel 3.13.0-32 as being detected on sd3. If it does then there should now be a newly generated grub.cfg that points to the right place to load Ubuntu.

Regards.

---

### Post by rxt on 2014-08-11
Thanks for the reply. I found an old manual about grub which helped me startup the OS, but for this it was probably too old. 

I tried your suggestion, and this came out:

```
root@ubuntu:~# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
done
```

That seems correct. The grub.cfg is also updated, with information like to this:

```
linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=de69305d-0631-4ca7-b551-ced72b71b61b ro  quiet splash $vt_handoff
initrd    /boot/initrd.img-3.13.0-32-generic
```

Still I boot into the commandline...???

---

### Post by oldfred on 2014-08-11
BIOS or UEFI. It sounds like it is BIOS boot?

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc (BIOS) 
or
 sudo dpkg-reconfigure grub-efi-amd64 (UEFI if not secure boot)
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

    If that does not work, then it may be best to see details just to confirm everything is otherwise correct.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Jonathan Precise on 2014-08-11
I think this is a UEFI boot because of:

> [COLOR=#008000]/boot/vmlinuz-3.13.0-32-generic.efi.signed[/COLOR]

---

### Post by oldfred on 2014-08-11
Then post link to the report from Boot-Repair. Do not run auto fix yet.

Some systems require the grub.cfg in the /efi/ubuntu folder to be updated or changed?
Boot report does not show the grub.cfg in the efi partition, it usually is just 3 lines and a configfile entry to grub.cfg in actual install. Post the grub.cfg from the efi partition also.

---

### Post by rxt on 2014-08-12
Thanks for the replies. The system is UEFI, not BIOS. I disabled secure boot. I tried boot repair before. You can see my attempts in the following [discussion]("http://ubuntuforums.org/showthread.php?t=2238060"). This [pastebin ]("http://paste.ubuntu.com/7992134/")shows the setup of the system, although the EFI used is not listed. In the end I could startup by copying the downloaded 32 bit EFI into /boot/EFI/bootia32.efi. 

I don't know what boot-repair can do at this point. I did run the following commands:

```
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub
sudo dpkg-reconfigure grub-efi-amd64
```

That resulted in the following output, with no result for "grub-pc/install_devices". I ran the command "modprobe efivars" as suggested in the output below, but nothing came up.

```
root@ubuntu1404:~$ debconf-show grub-pc
  grub-pc/install_devices_failed: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_disks_changed:
  grub-pc/disk_description:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/timeout: 10
  grub-pc/partition_description:
  grub-pc/hidden_timeout: true
  grub-pc/install_devices:
  grub-pc/install_devices_empty: false
  grub2/device_map_regenerated:
  grub2/linux_cmdline:
  grub-pc/kopt_extracted: false
  grub-pc/mixed_legacy_and_grub2: true
  grub2/linux_cmdline_default: quiet splash
root@ubuntu1404:~# grub-probe -t device /boot/grub
/dev/sda3
root@ubuntu1404:~# dpkg-reconfigure grub-efi-amd64
Installing for x86_64-efi platform.
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
Installation finished. No error reported.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
done
```

Any ideas how to proceed, or did I misread your comments?

---

### Post by oldfred on 2014-08-12
What I do not yet understand are some of the command that are the package name like the debconf-show grub-pc. Should that not also then be grub-efi or grub-efi-amd64. Naming does not seem consistent.

Both the dpkg and Boot-Repairs install give that same error message on sysfs or procfs directories missing. Are you booting in UEFI mode on live installer.

Also what are contents of grub.cfg in /efi/ubuntu folder.

From Boot-Repair you could thry the full uninstall and reinstall of grub from advanced options.

Is this a 32 bit UEFI system? That I thought was still in early stage of development?
What model Ideapad?

Other Ideapad threads, may have similar issues and solutions even if not exact model.
       Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
      
 Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

---

### Post by rxt on 2014-08-12
I have installed Ubuntu 14.04 on the internal harddisk, and I can start up from that disk. I do not use the live system anymore, although I might use it to boot up 12.04 to get boot-repair working which doesn't install on 14.04 AFAIK. The only problem left is that when I power the laptop on, I see the grub commandline. Then I enter three commands (linux.../initrd.../boot), which takes me half a minute, and then Ubuntu boots from the harddisk. 

It took quite some effort to get this working this far, thanks to the 32 bits EFI that someone compiled for this laptop, which is a Lenovo Ideapad Flex 10. This system has UEFI. Althought it's a 64 bit system (Ubuntu 14.04 64 bit is installed), the UEFI is 32 bit. In the menu there is an option for UEFI, but this has only one item, so it cannot be changed. This is my first experience with UEFI, quite a challenging one. (I'm still used to saying BIOS - I guess I'll have to let that go.)

I want to press the power button, and then see the login screen, not the grub commandline. I hoped I could create something like menu.lst which would make it all work.

---

### Post by rxt on 2014-08-12
The contents of /boot/efi/EFI/ubuntu/grub.cfg. I don't know if this location is where it should be. 

```
search.fs_uuid de69305d-0631-4ca7-b551-ced72b71b61b root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by oldfred on 2014-08-12
Your grub.cfg has a wrong UUID for sda3.

 /dev/sda3 [COLOR=#ff0000]       de69305d-0631-4ca7-b551-ced72b71b61b[/COLOR]   ext4       pendrive

Replace the de82....  with the correct de69.... in your grub.cfg in your /boot/efi/EFI/ubuntu/grub.cfg

---

### Post by rxt on 2014-08-14
You're correct that those two UUIDs are different. But that is my error, bad case of copy and paste. The value in grub.cfg and the UUID of the disk are the same. I'll correct that in the postings to be clear.

---

