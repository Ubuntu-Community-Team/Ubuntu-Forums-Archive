---
title: "GRUB will not install"
date: 2017-07-11
forum: Installation &amp; Upgrades
---

### Post by meatchop on 2017-07-11
I've tried installing , both, kali linux and Ubuntu but ran into problems when installing grub.

I'm using a Surface pro 3.

Boot-Info I got from Boot-Repair on a live Ubuntu usb: paste.ubuntu.com/25066386.

Any help would be appreciated.

---

### Post by meatchop on 2017-07-11
Do I need to install a phone emulator?

---

### Post by oldfred on 2017-07-11
Boot-Repair says this:
Locked-ESP detected.

Try this:
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
 Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

    Surface Pro 3 - USB/MicroSD Only Install 
 [http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)

---

### Post by meatchop on 2017-07-11
> **oldfred said:**
> Boot-Repair says this:
Locked-ESP detected.

Try this:
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
 Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

    Surface Pro 3 - USB/MicroSD Only Install 
 [http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)

I have yet to try what you suggested.

I am no longer able to boot the live cd. I will try setting up a new usb to see what happens.

---

### Post by meatchop on 2017-07-12
I am still not able to get GRUB working. 

Dosfsck doesn't seem to be working on /dev/sda1

After displaying a message about i8042, It goes straight to Bios if I don't have the USB plugged in.

---

### Post by oldfred on 2017-07-12
Do not know details of Surface Pro.
Did you follow the entire procedure posted in the link on Surface Pro Install. That user says it works.

But expect you may need a work around to get an Ubuntu only system to boot.
List UEFI entries:
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

then add a new Windows entry that really boots shimx64.efi.
(from link in my signature below).

 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by meatchop on 2017-07-13
I have read the instructions even though I am creating a single boot system. I would prefer to use my ssd as the boot drive.

Should I try version 17? I'm on 16.0.4

I followed your instructions, but it doesn't look like it helped.

---

### Post by oldfred on 2017-07-13
You can experiment with 17.04 or even 17.10, but 16.04 is LTS and usually the better install unless very new hardware. 

I have all 3 currently installed and each works, but system is now a couple years old so all drivers have mostly caught up with my versions of hardware. I consider my 16.04 as main working install and any others as tests/experiments.

---

### Post by meatchop on 2017-07-14
I installed rEFIND on a USB and booted Ubuntu using that.

Once logged in, I used Boot-Repair.

It works!

---

