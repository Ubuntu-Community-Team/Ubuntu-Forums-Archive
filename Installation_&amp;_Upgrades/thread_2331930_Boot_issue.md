---
title: "Boot issue"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by hlx13 on 2016-07-26
Hi all,

I have a laptop that has Windows 7 and Ubuntu 14.xx (I don't recall for sure) on there, and while I was using Windows, it froze and I shut it down. Now I am unable to load anything and it enters grub rescue as soon as the computer turns on.

I've attempted to follow a few guides to make sure root and prefix are correct and I tried all of the choices and none of them work. Occasionally it goes into Grub after insmod normal -> normal, however all boot choices from that menu gives an error.

I also attempted to use Boot repair from a USB, and the recommended boot repair option didn't work.

Here's the paste bin: [http://paste.ubuntu.com/21083051/](http://paste.ubuntu.com/21083051/)

I attempted to recommended boot repair again and that didn't work either, here's the paste bin for the second attempt: [http://paste.ubuntu.com/21084062/](http://paste.ubuntu.com/21084062/)

Any idea?

Thanks in advance.

---

### Post by oldfred on 2016-07-26
You have 14.10 which reached "End of Life" in July 2015.
Very difficult to repair now. 

Best to backup all you data if  you have not done that already and just reinstall.
But you have AMD. And if the open source driver works ok, then you can install 16.04, but if you have to use the AMD proprietary driver install 14.04.
See release notes Graphics & Display near bottom:
       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Windows (or any system) that freezes and you do a hard shutdown often causes file corruption. In Windows you then have to do chkdsk. And you can only do that from Windows. If Linux you run e2fsck to make Linux file system repairs.
Best to use your Windows repair disk or install disk's repair console. You may be able to temporarily reinstall a Windows type boot loader to directly boot Windows and then f8 may get you into the internal repair console.

But Boot-Repair may not see Windows and offer to install a Windows boot loader in its advanced options. You can manually install syslinux which is a Windows type boot loader. But easier just to use your Windows repair flash drive, which you should have made as soon as you got your system. My new Windows system wanted a Dell backup, a Windows backup and make a repair disk which I did.

You want just boot loader portion of syslinux in MBR, not full syslinux boot loader as that would erase some essential Windows boot data in Windows PBR.
        
 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

