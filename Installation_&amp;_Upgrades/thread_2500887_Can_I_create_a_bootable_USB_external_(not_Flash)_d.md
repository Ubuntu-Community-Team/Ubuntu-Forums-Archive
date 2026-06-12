---
title: "Can I create a bootable USB external (not Flash) drive?"
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by robert99999 on 2024-09-14
I'd like to create a bootable external USB SATA3 SSD, which I will then install internally in another laptop. Do I need to go through the step of creating a bootable USB stick first, or can I write the system directly to the SSD?

--- Edit ---
Nevermind, I just realized that I already have a bootable USB flash stick. So, I might as well use it to do the install.

---

### Post by yancek on 2024-09-15
You could do that in the same way you write the iso to a USB/flash drive.  The problem is that most software used to do this will then make the device readonly and the additional space useless until you re-create a partition table and format it.  Another method is to simply download the iso and create a loopback entry in your /boot/grub/grub.cfg file pointing to the path where the iso file exists.  Obviously, you would need a Linux OS with Grub2 to do this. Writing the iso to a flash drive is simpler for new users.

---

### Post by oldfred on 2024-09-15
UEFI installs, put an UEFI boot entry into the UEFI that uses GUID/partuuid to find ESP partition on drive.
If moving to a another system, and keeping as internal drive best to create new entry in UEFI.

You will only be able to initially boot by using a drive entry like you do when booting USB flash drive.

If fstab has correct UUID for ESP, then you can create new UEFI entry with this which assumes a lot of defaults.
sudo grub-install

To see UEFI entries, used to need -v to see details, but now efibootmgr has details & -v has even more data:
sudo efibootmgr
or 
sudo efibootmgr -v

To see if ESP mounted:
cat /etc/fstab
mount

To see uuid, partuuids & other useful info:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

### Post by robert99999 on 2024-09-15
Thanks for the answers. They're probably above my pay grade though.

Just to clarify, I have an existing PC running Ubuntu, and I wanted to use that to create the bootable drive that I would then install in another PC. So, I have an existing Ubuntu machine available to do this.

But as I mentioned in the edit of my first post, I did find an installer USB stick that I forgot that I'd made a few months ago. So, that turned out to be the simplest and quickest route. It's all up and running now.

---

