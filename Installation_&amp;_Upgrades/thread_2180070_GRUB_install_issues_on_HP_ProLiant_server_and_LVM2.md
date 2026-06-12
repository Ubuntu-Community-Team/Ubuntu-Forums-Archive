---
title: "GRUB install issues on HP ProLiant server and LVM2"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by bmw-man on 2013-10-11
Hi All,
I've been looking for info on this issue for couple days now and all I can find is the same thing, which doesn't work for me. Basically I have an HP ProLiant server that was running on RAID5 and with Ubuntu 10.04LTS. I wanted to upgrade the OS to 12.04LTS and I did with do-release-upgrade. Everything went through fine, until the end where GRUB failed to install. It turns out it doesn't support LVM2 volumes. There is a small 100mb partition called /boot and I believe that is where it was supposed to install, but it failed. All the info I could find is basically this : [http://nozell.com/blog/2004/05/08/some-tips-to-reinstall-grub-on-an-hp-proliant-server/](http://nozell.com/blog/2004/05/08/some-tips-to-reinstall-grub-on-an-hp-proliant-server/), but it does not work for me. I can boot the machine with a Live Ubuntu disk, but there is no /etc/grub.conf or /boot/grub/grub.conf. Also when I try running this **/sbin/grub --batch --device-map=/boot/grub/device.map         --config-file=/boot/grub/grub.conf --no-floppy** it says no such thing. Right now I'm dead in the water. Any hints or tips how to fix the bootloader please? I really appreciate any guidance.

---

### Post by oldfred on 2013-10-11
I think other distributions may use grub.conf.
With Ubuntu grub2 uses grub.cfg.
But grub2 does support lvm2. If you have a desktop install not a server install you need to install the drivers.
sudo apt-get install lvm2
Grub also has a lvm.mod file that it should automatically be adding to your grub.cfg.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by bmw-man on 2013-10-11
I ended up formatting the volume and did a fresh install. Everything is working great right now. Thankfully there wasn't any data on the machine that I needed.

---

