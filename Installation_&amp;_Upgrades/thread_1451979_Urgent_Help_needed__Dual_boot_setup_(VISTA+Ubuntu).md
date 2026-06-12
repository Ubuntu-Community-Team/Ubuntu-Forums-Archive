---
title: "Urgent Help needed : Dual boot setup (VISTA+Ubuntu) problem"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by hgadre on 2010-04-11
Hi All,

I have a Dell Studio laptop, which I am trying to make dual boot and in big trouble :(
These are the steps I completed.

1. Backedup all my important data on a USB drive.
2. Prepared a Ubuntu LiveUSB and booted in Ubuntu.
3. Used GParted tool to repartition my hard drive (320GB) as follows,
    
 Partition 1   NTFS (Primary)   ~50GB
 Partition 2   NTFS (Primary)   ~100GB
 Partition 3   EXT4 (Extended)
   Root         EXT4 (Logical)   ~20GB
   Swap        Linux-swap        ~2GB
   Home        EXT4 (Logical)    ~129GB

4. Accepted all these changes in GParted and restarted the machine.
5. Used VISTA installation disk to start VISTA installation on 1st NTFS partition (Partition 1).

-------------------Everything was fine until now ----------------------------

6. The VISTA installer took a really long time (around half hour) just showing copying files with 0% completion status message.
7. Somehow I got impatient and tried to cancel the installation.

NOW, the problem is the system does not boot up even with my USB LiveCD or Windows VISTA installer. It just shows blank screen and nothing appears.

Have anyone faced this problem before? What mistake have I committed? 

I would be grateful if someone can atleast provide some workaround for this problem (so that I can atleast use Ubuntu LiveCD). 

Thanks

---

### Post by coffeecat on 2010-04-11
Suggest you check your BIOS boot order. It may be that when you bailed out of the  Vista installer, somehow the BIOS got reset. If it's trying to boot from  the hard drive with no Windows MBR written, that might explain the blank screen, although I would expect a 'no OS detected' error message.

One little detail:

> **hgadre said:**
> 2. Prepared a Ubuntu LiveUSB and booted in Ubuntu.

<snip>

NOW, the problem is the system does not boot up even with my USB LiveCD or Windows VISTA installer.

The Ubuntu live disk - do you mean a live USB pendrive, or a live CD that you're booting from an external USB optical drive? Not that it makes any difference if the BIOS boot order is wrong, but I'm curious.

---

### Post by adam814 on 2010-04-11
I'm guessing the BIOS boot order isn't quite right too.

Once you get back to the installer, try letting it format the partition you're installing to.  Vista can be finicky about installing to partitions it doesn't format.

---

### Post by hgadre on 2010-04-11
Hi All,

Thanks a lot for the quick turnaround :).

I am using a Ubuntu LiveUSB using a USB pen drive. I am not sure if it could be a BIOS boot order problem because until now I have been explicitly selecting the device to boot from (using F12 during the system startup). I even changed the boot order to use the USB drive before the hard drive but no avail.

I somehow feel that aborting VISTA installation created some problem because before that I was able to boot into Ubuntu using the Live USB (and the same one now is not working without any changes on my part :confused:). Same is the case with Windows Installer CD.

I am really confused as to what steps should I take to restore my system. If installing VISTA is problem, I am prepared to work with an working Ubuntu setup (which was working fine before I tried to install VISTA :()

---

### Post by adam814 on 2010-04-11
Could you have accidentally tried to install Vista to the USB stick?  It's less than intuitive about that sort of thing.

---

