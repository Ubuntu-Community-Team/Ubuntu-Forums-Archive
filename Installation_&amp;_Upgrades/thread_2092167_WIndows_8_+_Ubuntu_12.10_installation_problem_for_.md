---
title: "WIndows 8 + Ubuntu 12.10 installation problem for UEFI"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by j1234d2003 on 2012-12-06
Have a windows 8 system. Shrunk the windows 8 partition, installed Ubuntu 12.10 in free space using manual partitioning (reusing win-8 efi). Installation ended without any error messages.

On reboot, only Windows 8 loading - no sign of ubuntu or grub.

Used Ubuntu Live USB to run Boot Repair - 
  1) first with Recommended repair: [http://paste.ubuntu.com/1416146](http://paste.ubuntu.com/1416146)
  2) Later with advanced options: [http://paste.ubuntu.com/1416169](http://paste.ubuntu.com/1416169)

Both seem to indicate 
 Line 789:
Reinstall the grub-efi-amd64-signed of sda6
mkdir: cannot create directory `/boot/efi/EFI/ubuntu': Input/output error

Please advice.
-JD

---

### Post by oldfred on 2012-12-07
Some of the new Windows 8 systems work with Secure boot on as Ubuntu is using the signed grub2 loader. Others have to have the secure boot off and some do not work at all which says it really is a bug in UEFI by the Vendor.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)


Have you tried turning secure boot off?

I have some older HP instructions and they seem to not specifically say secure boot  off, but say UEFI boot on meaning without the secure boot? Please check you manuals on details.


This user has HP and installed UEFI but to two drives.
       
 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by j1234d2003 on 2012-12-07
Yes secure boot is off.

I have only one 500G disk - shows up as /dev/sda. /dev/sdb is cdrom.

Installed windows 8 on /dev/sda4 160G, Configured /dev/sda5 as swap 16G and /dev/sda6 as ext4 306G.

In manual install, tried using Device for boot load installation as /dev/sda2 (EFI device) but installation fails with grub-dummy installation fatal error.

Mounted EFI in a live USB terminal to examine it and it shows a ubuntu directory but unlike other directories, ls -l shows all ???. Windows directories show normal details.

So EFI does not have ubuntu information. Any pointers on how to populate EFI with correct information?

-JD

---

### Post by YannBuntu on 2012-12-07
Hello

grub-install returns "Input/Output" error, which means generally a hardware problem, but in your case i wonder if it is not a permission problem on the ESP. (or some kind of naughty blocker from HP)

Please :
1) boot your Ubuntu disc, choose "Try Ubuntu"
2) open a terminal, and type this 1st command:
sudo mount /dev/sda2 /mnt
3) Press Enter, then type this 2nd command:
sudo mkdir /mnt/EFI/ubuntu
4) Press Enter, then type this 3rd command:
ls -l /mnt
5) Press Enter, then type this 4th command:
ls -l /mnt/EFI
6) Press Enter
7) Tell us the outputs of these 4 commands

Also please show us pictures of your BIOS.

---

### Post by YannBuntu on 2012-12-15
Hello
I found 2 other users with the same problem:
[https://bugs.launchpad.net/bugs/1090829](https://bugs.launchpad.net/bugs/1090829)

you can add a comment (indicate your pc maker/reference), and mark yourself "Affected" by the bug.

---

### Post by kochouloo on 2013-03-18
I ran into the same issue (Asus UX51VZ with dual boot Win8/Ubuntu 12.10 / secure-boot OFF) as my dual boot was perfectly working using grub2 (I guess 1 update broke my grub)
I booted on the Ubuntu Secure Remix 12.10 live-cd to be able to execute boot-repair
I was able to fix the issue by running [B]e2fsck -f -y -v /dev/{your_linux_partition}

[/B]Details of my journey trying to fix that issue here : [B][http://ux51vz.blogspot.com](http://ux51vz.blogspot.com)
[/B]I put all the bootinfo summaries after each execution of boot-repair.
At least it prooves that this bug can - in some cases - be fixed.

Hope this can help!
Cheers,
Sebastien

---

