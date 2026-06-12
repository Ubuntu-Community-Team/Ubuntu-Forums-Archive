---
title: "dual boot win7 and ubuntu on 2 HDD's"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by TheTobi213 on 2013-01-24
Hello all!
I've wanted to try to dual boot Windows 7 and Ubuntu 12.04 ever since i first tried out Ubuntu 11.08 (i think that's where i started anyway...). I have a 500gb hard drive that had Ubuntu on it previous to this, and I'm using a 150gb hard drive with Windows 7 on it right now, and i have 8gb RAM. What I'd like to do is have the ability to choose between Ubuntu and Windows 7, using the 2 hard drives as a single unit, using Ubuntu as my basic OS and having Windows 7 there just for my windows-only games (Supreme Commander, Borderlands, Skyrim, etc.). I've been going into the BIOS of my machine and manually switching the OS/hard drive... it sucks and it's time-consuming. I figured i'd at least ask for help on how to do this before i mess up both of my hard drives and end up losing them. Is this even possible, or do i need to explain myself better? 
^^ Thanks in advance for the help!

As a side note, I've tried using Ubuntu through VMware on Windows 7 and vice versa. The VM, for some reason, really bogs up.

---

### Post by lukeiamyourfather on 2013-01-24
When setting up Ubuntu I'd install the boot loader to the second drive (likely "sdb" in the install). It should recognize Windows from there and then set the BIOS to boot to the second disk. Or use something like EasyBCD to tell the Windows boot loader to add the Linux install as an option when booting.

---

### Post by oldfred on 2013-01-24
From Ubuntu did you run this. then the grub menu should let you boot either system.

sudo update-grub

My suggestion always has been to keep Windows on one drive and Ubuntu on another including boot loader. Then if one drive fails you can boot the other. I then have data partition on both drives and copy data back & forth as backups.

If you really want to know what is installed where, and document all of that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

