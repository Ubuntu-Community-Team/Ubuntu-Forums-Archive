---
title: "Uninstalling Ubuntu then reinstalling on a different drive/partition"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jj.moreland on 2011-05-02
Hi, can anyone help me out, I'm a newbie to Linux/Ubuntu though want to become more involved with it as a movement.

I want to install and run Ubuntu from an external harddrive. I downloaded the installer into the external and then launched it from there accordingly. During the installation a message came up about partitions etc but I didn't recognise the name of the drive I wanted it to be installed on so just carried on hoping I'd get another chance to allocate the correct drive I want to launch Ubuntu from. I didn't...:P

So now the OS is installed on an internal harddrive, how do I remove it and recover the partition then how do I reinstall ubuntu on a specific external harddrive?

Thanks for any help you can give :D

John

---

### Post by dino99 on 2011-05-02
well removing can be done if you format its partitions (/ & swap)

how to install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sanderd17 on 2011-05-02
if you lost data (e.g. you erased that partition), you probably won't be able to recover it (unless you use some specialised tools like here: [http://joereth.com/2011/01/recover-files-like-a-forensic-expert/](http://joereth.com/2011/01/recover-files-like-a-forensic-expert/))

If you did not lose data, you can just launch a live-CD (or live-USB), open gParted (it should be somwhere in the system settings or so), remove the / and swap partition and enlarge the other ones. Then you wil have to repair the windows mbr, so you need a windows reparation disk.

Look in gParted for the name of the external disk and reinstall ubuntu.

---

### Post by oldfred on 2011-05-02
Good instructions on installing to a second drive from Herman. Grub2 likes to install its boot loader to sda or usually the internal. To get the choice of where to install grub you have to use manual install.

Screens will be slightly different for Natty, but procedure is the same.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you overwrote entire drive you will not be able to recover a bootable system. You may be able to recover some data. If you installed side by side, you may just want to convert the Ubuntu partition to a shared NTFS data partition for any data you want in both Ubuntu & windows.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jj.moreland on 2011-05-02
Great! Thanks for you replies. Maybe I should elaborate a little.

I forgot to mention that when installing I chose to install Ubuntu alongside the Windows Vista already installed on my system. 

I have an internal harddrive already partitioned into a C and D drive. After I installed Ubuntu the size of the D drive has been considerably reduced. I would simply format the partition Ubuntu installed itself in (which I'm assuming it broke away from the D drive) but I'm not sure where to look for it, it's like David Blaine has been playing a disappearing trick with parts of my internal memory.

I'm going to try some of your suggestions in the meantime an will get back to you with what helps resolve my problem.

Thanks!

P.S. Except for between 50-70 unused GB formally part of my D drive I haven't actually lost any files or data (to my knowledge). Hence all I want to do it wipe Ubuntu from my system, hoping the GBs will be returned to my D drive, then I can reinstall Ubuntu to my external harddrive.

---

### Post by oldfred on 2011-05-02
Deleting the partitions Ubuntu automatically created will not automatically restore the space to your D: drive.

As I suggested before you could make the space another drive, but if you already have a d: drive as a data drive you can just totally remove the Ubuntu partitions and expand the partition that is your d: drive. You can use gparted for that. But if Vista or 7 I would use its partitioning tools for any changes to the windows system partition.

Generally use windows tools for windows and Linux tools for Linux.

---

