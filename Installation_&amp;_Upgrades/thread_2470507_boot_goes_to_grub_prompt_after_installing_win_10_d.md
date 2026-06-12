---
title: "boot goes to grub prompt after installing win 10 dual-boot, boot-repair not fixing"
date: 2022-01-01
forum: Installation &amp; Upgrades
---

### Post by eflister on 2022-01-01
hi-

i installed ubuntu 21.10 on a new machine. then i needed to dual-boot windows 10, so i shrank ubuntu's partition using gparted from a live usb. windows installed fine, but squashed grub. so i tried running boot-repair from the live usb. 
the automatic repair didn't work -- booting goes to a grub prompt rather than a grub menu.

so i tried again with the "advanced options" -- "purge GRUB before reinstalling it"  ends up giving me a dialog that says "GRUB is still present. Please try again." this is after confirming to remove GRUB after being asked to run: sudo apt-get purge --allow-remove-essential -y grub*-common shim-signed. at that point i have no choice but to cancel. 

latest bis from boot-repair: [https://paste.ubuntu.com/p/nkWcdPrNXT/](https://paste.ubuntu.com/p/nkWcdPrNXT/)

also asked here: [https://askubuntu.com/questions/1384496/boot-hangs-at-grub-prompt-instead-of-grub-menu](https://askubuntu.com/questions/1384496/boot-hangs-at-grub-prompt-instead-of-grub-menu)
thanks for your help!

---

### Post by grahammechanical on 2022-01-01
Please confirm that you did this:

> Please do not forget to make your UEFI firmware boot on the Ubuntu 21.10 entry (nvme0n1p1 file) !

Also confirm that after cancelling the "advanced options" the machine still boots to a Grub prompt. Do you get a Grub menu? A Grub prompt is often a sign that Grub cannot find its configuration file (grub.cfg). Does Windows load?

It might be simpler to re-install Ubuntu 21.10.

Regards

---

### Post by eflister on 2022-01-01
yes, my bios tries the ubuntu install first, and i can also one-time override to it.  neither works, they both go to the grub prompt.  i cannot get a grub menu.  if i tell the bios to boot the windows install, windows launches successfully.  i can launch my ubuntu install successfully by manually entering `linux...`, `initrd...`, and `boot`at the grub prompt.

does the bis paste i sent show any problems with the grub.cfg file contents or location?

i do know i could reinstall ubuntu, but i prefer to learn by avoiding brute-force methods.

---

### Post by cigtoxdoc on 2022-01-01
I have the same problem on my hp eb 840.  Was working fine in windows 10 pro.  Went over to 21.10.  When I tried to go back, GRUB menu did not show mount point for Win that it had before.  Can someone please explain how to do "lease do not forget to make your UEFI firmware boot on the Ubuntu 21.10 entry (nvme0n1p1 file) ! "

Thank you,

John

---

### Post by eflister on 2022-01-01
john - do you know how o get into your BIOS?  as far as i understand, "UEFI firmware" just means "modern BIOS," the standards changed a few years ago so the graphics are a little better and you can use your mouse etc.  usually there's a message right when you boot that says how to get in, it's usually holding down delete or some function key.  inside the BIOS, one of the menus will let you indicate the boot order -- which devices/OS's installed on partitions to prefer.  as far as i understand that instruction, they're just saying make sure it tries to boot your linux partition, not the windows one.  that's what is supposed to launch grub.  anyone please feel free to correct what i've mis-stated or over-simplified here...

---

### Post by tea for one on 2022-01-02
Something unusual in one of your partitions [COLOR="#0000FF"]nvme0n1p3[/COLOR]:-

[COLOR="#0000FF"]Line 95[/COLOR] - Mounting failed:   mount: /mnt/BootInfo/nvme0n1p3: wrong fs type, bad option, bad superblock on /dev/nvme0n1p3, missing codepage or helper program, or other error.
[COLOR="#0000FF"]Line 204[/COLOR] - 3:501GB:501GB:16.8MB:ext4:Microsoft reserved partition:msftres;

I've never seen Microsoft reserved partition with ext4 and I suspect that it cannot be fixed without starting from scratch.

---

### Post by cigtoxdoc on 2022-01-02
Thank you.  I checked BIOS on my hp eb840g1.  No mention of UEFI.  What got me back up on the Win 10 side was selecting the other Win 10 boot option.  John

---

### Post by oldfred on 2022-01-02
In gparted you can select unformatted as a "format" and that is what a Microsoft Reserved requires.
But do not think that is related to boot issue. It will eventually cause a Windows issues when Windows tries to use the reserved partition and cannot write into it. 

Yann posted there was an issue with Boot-Repair & he was rolling back some changes. 
I did get a new version downloaded just an hour ago with my daily update script.
[https://ubuntuforums.org/showthread.php?t=2470405](https://ubuntuforums.org/showthread.php?t=2470405)

If you can boot you can totally reinstall grub from inside your install.
Can you boot with this?
ls # Do you see (hd0), (hd0,2) ? If so, run the next command. 
configfile (hd0,2)/boot/grub/grub.cfg
Script is not showing grub menu, not sure if script or if menu missing. Configfile will not work if menu, grub.cfg missing.
OR Ubuntu puts links to newest kernel. Used to be in /, but now in /boot:
set prefix=(hd0,2)/boot/grub
set root=(hd0,5)
linux (hd0,2)/boot/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/boot/initrd.img
boot

Since config looks otherwise correct, perhaps you just need menu update.
If you can boot and run this from inside your install to update menu. If any errors post those. And then you need a total reinstall of grub.
sudo update-grub

---

### Post by eflister on 2022-01-02
hi oldfred -- i'm the same guy you're helping over at [https://askubuntu.com/questions/1384496/boot-hangs-at-grub-prompt-instead-of-grub-menu](https://askubuntu.com/questions/1384496/boot-hangs-at-grub-prompt-instead-of-grub-menu)

yes, i can boot manually from the grub prompt using linux/initrd/boot.
how do i check if the grub menu is missing, what its contents are, or update it?

do the errors indicated at the top of the bis (scripts in /usr/share/boot-sav, many commands not found, etc) not matter? 

> If you can boot and run this from inside your install to update menu.

i can't tell what you are referring to by "this" -- what are you saying i should run from inside my install to update the menu?  "update-grub"?


```
flister@flister-desktop:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

```

```
flister@flister-desktop:~$ ls -al /boot/grub
total 44
drwxr-xr-x 5 root root  4096 Jan  2 10:54 .
drwxr-xr-x 6 root root  4096 Jan  1 20:49 ..
drwxr-xr-x 2 root root  4096 Jan  1 22:56 fonts
-r--r--r-- 1 root root   150 Jan  2 10:54 grub.cfg.new
-rw-r--r-- 1 root root  1024 Jan  1 22:56 grubenv
drwxr-xr-x 2 root root  4096 Jan  1 23:00 locale
drwxr-xr-x 2 root root 20480 Jan  1 23:00 x86_64-efi
```


```
flister@flister-desktop:~$ cat /boot/grub/grub.cfg.new 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

```

```
flister@flister-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
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
GRUB_DISABLE_OS_PROBER=false


flister@flister-desktop:~$ ls -al /etc/grub.d
ls: cannot access '/etc/grub.d': No such file or directory

```

```
flister@flister-desktop:~$ ls -al /etc/grub.d.bak/
total 152
drwxr-xr-x   2 root root  4096 Dec 29 21:50 .
drwxr-xr-x 138 root root 12288 Jan  2 00:18 ..
-rwxr-xr-x   1 root root 10627 Sep  2 05:37 00_header
-rwxr-xr-x   1 root root  6260 Dec 13 05:27 05_debian_theme
-rwxr-xr-x   1 root root 18683 Dec 13 05:27 10_linux
-rwxr-xr-x   1 root root 43031 Sep  2 05:37 10_linux_zfs
-rwxr-xr-x   1 root root 14180 Dec 13 05:27 20_linux_xen
-rwxr-xr-x   1 root root  1992 Oct  7 03:20 20_memtest86+
-rwxr-xr-x   1 root root 12910 Dec 13 05:27 30_os-prober
-rwxr-xr-x   1 root root  1372 Dec 13 05:27 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Sep  2 05:37 40_custom
-rwxr-xr-x   1 root root   215 Dec 13 05:27 41_custom
-rw-r--r--   1 root root   483 Sep  2 05:37 README
```





```
flister@flister-desktop:~$ apt list --installed | grep grub

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


grub-common/jammy,now 2.06-2ubuntu3 i386 [installed,automatic]
grub-efi-amd64-bin/jammy,now 2.06-2ubuntu3 amd64 [installed]
grub-efi-amd64/jammy,now 2.06-2ubuntu3 amd64 [installed,automatic]
grub-efi/jammy,now 2.06-2ubuntu3 amd64 [installed]
grub2-common/jammy,now 2.06-2ubuntu3 amd64 [installed,automatic]
```

---

### Post by jeremy31 on 2022-01-02
What about results for ```
sudo cat /boot/efi/EFI/ubuntu/grub.cfg
```
You will likely need to rename /etc/grub.d.bak/ back to /etc/grub.d/

---

### Post by tea for one on 2022-01-02
Post no. 9 indicates that you are using 22.04 (in development).
Post no. 1 tells us that you installed 21.10.

Please post the output from:-```
lsb_release -a
```

---

### Post by oldfred on 2022-01-02
If you have this: /boot/grub/grub.cfg.new, then grub.cfg is not updated.
You have a typo somewhere.
I had that once where I forget a closing } in a boot stanza in 40_custom. 
But error can be in /etc/default/grub or elsewhere.

This says you deleted all the grub scripts.
flister@flister-desktop:~$ ls -al /etc/grub.d
ls: cannot access '/etc/grub.d': No such file or directory

Then only fix is a full reinstall of grub. 
And then it is a good thing that grub did not update menu with a defective version of grub which would prevent you from booting.

This should work, if booted into your system. It will know its the UEFI version & the mount of the ESP in fstab tells it which ESP to use.
sudo grub-install

But if other issues, may need extra parameters on the install.

---

### Post by eflister on 2022-01-02
[FONT=courier new]

flister@flister-desktop:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 2f6e8ca5-3f9a-4bde-a90d-754d749c278e root
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


did the following, rebooted, and got no change in results


flister@flister-desktop:~$ sudo cp -r /etc/grub.d.bak/ /etc/grub.d
flister@flister-desktop:~$ ls -al /etc/grub.d
total 152
drwxr-xr-x   2 root root  4096 Jan  2 13:03 .
drwxr-xr-x 139 root root 12288 Jan  2 13:03 ..
-rwxr-xr-x   1 root root 10627 Jan  2 13:03 00_header
-rwxr-xr-x   1 root root  6260 Jan  2 13:03 05_debian_theme
-rwxr-xr-x   1 root root 18683 Jan  2 13:03 10_linux
-rwxr-xr-x   1 root root 43031 Jan  2 13:03 10_linux_zfs
-rwxr-xr-x   1 root root 14180 Jan  2 13:03 20_linux_xen
-rwxr-xr-x   1 root root  1992 Jan  2 13:03 20_memtest86+
-rwxr-xr-x   1 root root 12910 Jan  2 13:03 30_os-prober
-rwxr-xr-x   1 root root  1372 Jan  2 13:03 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Jan  2 13:03 40_custom
-rwxr-xr-x   1 root root   215 Jan  2 13:03 41_custom
-rw-r--r--   1 root root   483 Jan  2 13:03 README[/FONT]

---

### Post by eflister on 2022-01-02
oldfred:  woot!  it works now -- i get a grub menu and both the ubuntu and windows installs work right from the menu.  thanks so much!  i'll mark the thread solved.

i really don't get why it worked this time, i fee like i've tried update-grub and grub-install a million times.  no idea what was different now.

i never edited any files, but i've run boot-repair, update-grub, grub-install, etc alot.  those are the only things i know of that could have edited/created/moved grub.cfg, grub.cfg.new, 40_custom, etc.

[FONT=courier new]flister@flister-desktop:~$ sudo grub-install
Installing for x86_64-efi platform.
Installation finished. No error reported.


flister@flister-desktop:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.13.0-22-generic
Found initrd image: /boot/initrd.img-5.13.0-22-generic
Found linux image: /boot/vmlinuz-5.13.0-19-generic
Found initrd image: /boot/initrd.img-5.13.0-19-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done




[/FONT]tea for one: where does it say i'm using 22.04?

[FONT=&quot]flister@flister-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 21.10
Release: 21.10
Codename: impish[/FONT]

---

### Post by tea for one on 2022-01-02
> **eflister said:**
> 

[/FONT]tea for one: where does it say i'm using 22.04?

[FONT=&quot]flister@flister-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 21.10
Release: 21.10
Codename: impish[/FONT]

In post 9, there was this output:-
```
flister@flister-desktop:~$ apt list --installed | grep grub

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

grub-common/jammy,now 2.06-2ubuntu3 i386 [installed,automatic]
grub-efi-amd64-bin/jammy,now 2.06-2ubuntu3 amd64 [installed]
grub-efi-amd64/jammy,now 2.06-2ubuntu3 amd64 [installed,automatic]
grub-efi/jammy,now 2.06-2ubuntu3 amd64 [installed]
grub2-common/jammy,now 2.06-2ubuntu3 amd64 [installed,automatic]
```

Jammy Jellyfish is the 22.04 Ubuntu version in development.

Anyway, now that your Grub dilemma is solved with oldfred's advice, it's clear that my question had no bearing on the problem.

Best wishes

---

