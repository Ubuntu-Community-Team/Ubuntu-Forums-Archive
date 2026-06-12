---
title: "Need terminal help to install"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by malangbaba on 2007-09-05
So...Im trying to [follow this]("https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28fromlinux%29")....

My current setup:
hda1: Puppy Linux - out of which im trying to do this...
hda2: (For Xubuntu install) + Xubuntu ISO
hda3: (to copy ISO as step 2 listed below into here)

Step 2 of the process asks me to do this:
> Step 2. Copy CD contents over to the new partition using the command
 mkdir /tmp/install_cd
 mount ubuntu-7.04-desktop-i386.iso -o loop /tmp/install_cd
 mkdir /mnt/installer
 mount /dev/sda1 /mnt/installer
 cp -r /tmp/install_cd/* /mnt/installer
 cp -r /tmp/install_cd/.disk /mnt/installer
 umount /tmp/install_cd

I am completely new to Linux.  Could someone guide me on what I have to type (or what directory to be in, or if i have to add directories to the above commands) to get through this...

ie. If I am typing "mkdir /tmp/install_cd" how do i know it is doing it to the right partition?

---

