---
title: "Ubuntu 16.04 boot stuck on usb flash stick driver but working OK with VMWare"
date: 2018-03-16
forum: Installation &amp; Upgrades
---

### Post by superudisk on 2018-03-16
Hi all,

Thanks for your attention.

I try to make a super usb flash disk which include these features:
1. System diagnosis tools & rescue disk(Win PE x64, Win PE x32)
2. Windows 7 installation disk
3. Ubuntu 16.04 installation disk
4. Running Ubuntu 16.04 from USB stick

My resources:
1. Dell XPS 13z with Windows 7 OS
2. SanDisk Cruzer Facet 32 GB USB stick driver
3. VMWare Player 12.0

Now, I almost done except I can't run Ubuntu 16.04 from USB driver directly.
When I boot my XPS 13z from USB stick driver, The Ubuntu almost stuck every time(Just one time bootup success) and report error like:
EXT4-fs error (device sdb2): ext4_find_entry:1431: inode #24998: comm gmain: reading directory lblock 0
usb 3-1: device descriptor read/64, error -110

BUT, when I create a VM in VMWare Player and use the USB stick as physical driver, I can boot up Ubuntu 16.04, it works perfect for every thing!

I follow below steps to create the super disk:
1. Use the Windows7-USB-DVD-Download-Tool to formatting the USB flash disk, and make the Windows installation USB stick driver
2. Use DiskGenius to create a new free partition(Ubuntu partition, we call the old partition "Windows Partition") at USB stick(End of the USB disk, 6GB size)
3. Create a VM, use USB flash disk as physical hard driver, and use ubuntu-16.04.2-desktop-amd64.iso as installation media
4. Install Ubuntu 16.04 to usb new free partition(Just select the 6GB free parition as installation destination without swap partition)
5. After install, boot up Ubuntu, and edit /boot/grub/grub.cfg, add menuentry:
menuentry 'ubuntu-16.04.2-desktop-amd64.iso' {insmod fat
insmod loopback
insmod iso9660
loopback loop (hd0,1)/ubuntu-16.04.2-desktop-amd64.iso
set root=(loop)
linux /casper/vmlinuz.efi boot=casper iso-scan/filename=/ubuntu-16.04.2-desktop-amd64.iso noprompt noeject --
initrd /casper/initrd.lz
}.
Save and power off VM.
6. Copy ubuntu-16.04.2-desktop-amd64.iso to usb driver Windows partition root folder.
7. Entry command prompt(with Administration priviledge), enter <USB driver>/boot folder and use bcdedit command to add new menu entry for new WIM files, and copy new WIM files to USB driver.


My problem, I can't boot up my XPS 13z with the USB flash disk when I select "Ubuntu 16.04", it stuck at some steps and report above error, but every thing works fine in VMs.

---

### Post by superudisk on 2018-03-17
Information:
I use this USB stick at another Dell XPS15 L502X, everything works great!

---

