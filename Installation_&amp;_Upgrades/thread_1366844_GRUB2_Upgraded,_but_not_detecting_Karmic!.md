---
title: "GRUB2: Upgraded, but not detecting Karmic!"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by monkeys on 2009-12-28
Hey all,

I updated my Karmic using this: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I had Error 15, but fixed a LiveCD. I've been trying to use the fix for the dual-boot provided on the wiki as well, but it hasn't been working. Working inside of /mnt with chroot, libdebian-installer cannot be reinstalled, and so the os-prober only detects Windows 7 - working in the terminal as a general, libdebian-installer is reinstalled, the os-prober finds both my Ubuntu partition and my Windows 7, but the grub-update doesn't work.

Here's *some* of what I've been doing:

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x307a63df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12004    96422098+  83  Linux
/dev/sda2   *       12005       19083    56862067+   7  HPFS/NTFS
/dev/sda3           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda2  /mnt/boot
fuse: mount failed: Device or resource busy
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-reconfigure grub-pc
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/# os-prober
/dev/sda2:Windows 7 (loader):Windows:chain
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo os-prober
/dev/sda1:Ubuntu 9.10 (9.10):Ubuntu:linux
/dev/sda2:Windows 7 (loader):Windows:chain
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.



Please help! Should I convert back to Grub legacy?

---

### Post by drs305 on 2009-12-28
From what you posted, it looks like you tried to mount your Windows partition to /mnt/boot (sudo mount /dev/sda2 /mnt/boot) for some reason.

It also looks like you tried to run update-grub after you left the chroot and did it while you were on the LiveCD.

Try reinstalling GRUB 2 from the LiveCD. Although this is documented in the GRUB 2 community doc, just do the following after booting to the LiveCD desktop:

```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```
Try rebooting after removing the CD. If you get a normal boot, run "sudo update-grub" if you don't see Windows in your GRUB 2 menu during boot. If you get stuck at a command prompt when rebooting, there are instructions for trying to boot from the G2 command line in the community doc:  [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by monkeys on 2009-12-29
Hey drs305

Wow, that was utterly easy. Thanks so much! I was mounting my sda2 because I thought it was necessary to mount /boot when altering GRUB2... As is evident, this stuff is all relatively new to me and for some reason I didn't come across the documentation on the searches.

Thanks again for your help!

---

