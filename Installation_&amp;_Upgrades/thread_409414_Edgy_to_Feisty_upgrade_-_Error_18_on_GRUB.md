---
title: "Edgy to Feisty upgrade - Error 18 on GRUB"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Woodsy on 2007-04-14
Hello All,

Most of the answers to my questions are already posted (so thanks to all you guys for that!) but this time I haven't been able to find anything :( 

I've been using Ubuntu Edgy 6.10 for the past few months.  Its been working ok and I've done alot of stuff to get it working the way I'd like to but this morning I decided to upgrade to Feisty 7.04.  After some initial problems (which was solved by commenting out some repositories) the upgrade ran fine with no problems.
After my reboot, the grub menu appeared and I choose the latest version to run.
I then got a dreaded "Error 18 : Selected Cyclinder exceeds Maximum supported by BIOS"
I understand that this kind of error is down to old motherboards not being able to read beyond a part of the HDD.
I'm a bit puzzled at why I've got this kind of this error.  It was working fine before the upgrade.

I'm a bit stuck at what to do now and if anyone can help I'd be grateful,

Please be gentle - I'm a newbie!! Many thanks,

Woodsy.

---

### Post by zvacet on 2007-04-14
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

---

### Post by Woodsy on 2007-04-15
Thanks for this.  A few things to try there!

---

### Post by asnd16 on 2007-04-15
> **zvacet said:**
> [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

yeah this does not HELP how the f do I get this fixed please explain.

---

### Post by bollix47 on 2007-04-16
I recently had a problem with Grub Error 18 as well.  I found that if I removed "savedefault" in the menu.lst file the problem went away.

In order to edit that file I started up my system with a live cd (I used 6.06).

After opening a terminal I made a folder in /media for my root(or boot) partition of the affected file system.  You can use fdisk -l to see your partition info.

Than I mounted the partition I wanted to fix into that folder.

You can use the following as a guide but the drive hda6 will probably be different in your case.

If you have a separate boot partition use that instead of the root partition.

Load and start the live CD.
Open a terminal.  (Applications > Accessories > Terminal)

```
sudo fdisk -l
sudo mkdir /media/hda6
sudo mount /dev/hda6 /media/hda6
cd /media/hda6/boot/grub         #if on the root partition
cd /media/hda6/grub                 #if you have a separate boot partition
sudo cp menu.lst menulst.old    #backup 
sudo gedit menu.lst
```

Search for all the savedefault entries and delete them. (except for the one in the comments section)
Save the file and reboot.

This worked for me but I had to do it again whenever the kernel updated and menu.lst was regenerated.

I'm not sure if it's related but during some updates I noticed a message that said the file /etc/kernel-img.conf was wrong and needed to refer to /usr/sbin/update-grub, not just update-grub or /sbin/update-grub, so I changed that but will have to wait for a kernel update to see if they're related.

Good Luck.

---

### Post by Woodsy on 2007-04-17
Many thanks for for help but the problem seemed to have resolved itself after an update.

I tried loading with an earlier Kernel 2.6.17-11.  This got further than 2.6.20-15 but hung on the Ubuntu loading percentage bar.
I then tried the next earlier Kernel 2.6.17-10 which got me in.  The system wanted to do an update which I did and rebooted.  It now goes in under Kernel 2.6.20-15
It is flashing up with a "PCI : failed to allocate memory resource blah blah blah" error message but goes in fine.  From what I can see all my PCI hardware is working.

Thanks for the suggestion anyway.

---

### Post by sg_57 on 2007-04-20
> **Woodsy said:**
> It now goes in under Kernel 2.6.20-15
It is flashing up with a "PCI : failed to allocate memory resource blah blah blah" error message but goes in fine.  From what I can see all my PCI hardware is working.

I am having the same error message when reaching the GRUB screen... 
(otherwise seems to work fine so far)
::same kernel - running Feisty installed as an upgrade from Edgy::

Would love to know what this stems from.

SG

---

