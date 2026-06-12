---
title: "Can I resize the Linux partition?"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Wabash on 2007-08-30
Instead of setting up a dual-boot scenario with Windows 2000, I decided to try VMWare this time -- so I installed Ubuntu Feisty Fawn on a 99GB sda1 partition with a 1GB sda2 swap partition filling out the rest of my 100GB hard drive.

All has gone well -- Ubuntu is great, VMWare works astonishingly well.

But there's one problem: VMWare won't let my Windows 2000 virtual machine see my USB backup hard drive, and I'm often working offline -- so it can be difficult making files available to Windows.

I now wish I'd left room for a 5GB FAT32 partition that both Ubuntu and VMWare could read. So here's the question: Can I do that retroactively? In other words, can I boot the Ubuntu CD, delete my swap partition, resize my root partition to be 5GB smaller, create a new swap partition, and be left with enough space for a 5GB sda3 parttion -- without confusing or demolishing my Ubuntu install?

Is there another, better way to accomplish what I have in mind?

Thanks for all help!

---

### Post by ajgreeny on 2007-08-30
Yes, after backing up everything important, boot into the ubuntu live CD, open gparted (gnome partition manager) and reduce the size of your ubuntu partition by as much as you want.  Now reformat the new bit to fat32, and there you are.  You may need to delete this new partition part before you can reformat, I can't remember.

You can either move your swap partition or leave it as it is, just make sure that the reformatting has not changed its device name usually dev/hda5 or sda5.  If it has changed you can edit /etc/fstab accordingly, but I don't think it will have.

If you want the new partition mounted automatically at boot just add the following line at the bottom of /etc/fstab
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
making sure that the dev/hda1 is changed to the new partition dev name.

---

### Post by Wabash on 2007-08-31
Thanks for the courage! I've accomplished the resizing project without incident. I deleted sda2 (swap), resized sda1 (Linux) (this took about half an hour in my case, and gparted can look like it's just stuck -- patience!), then created a new sda2 swap partition and the desired sda3 fat32 partition. My chief remaining concern was whether the new swap partition would have a new and different uuid that would require modifying the existing line in fstab -- but that seems not to have been the case, as the installed Ubuntu booted normally.

Thanks again!

---

### Post by Wabash on 2007-08-31
I fooled myself: The new swap partition did indeed have a new uuid, so fstab didn't mount it (I'm actually surprised at how well Ubuntu ran without a swap). I found the new uuid (ls -l /dev/disk/by-uuid) and edited fstab to reflect it. All well now.

---

