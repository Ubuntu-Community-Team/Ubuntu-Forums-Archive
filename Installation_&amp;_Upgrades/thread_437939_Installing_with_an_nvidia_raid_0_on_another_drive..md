---
title: "Installing with an nvidia raid 0 on another drive."
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by ghell on 2007-05-09
Here is my current configuration:

SATAII NForce4 RAID 0, 2*250GB (1 big 500GB NTFS partition) - Windows Vista Ultimate x64
IDE 200GB - Fedora Core 6 x86_64

I want to change from Fedora Core 6 to Ubuntu 7.04 (Alternate x64)

I used to have Windows XP Pro x86 on that RAID. When I had this, Fedora put it in /dev/mapper/nvidia_grserdgdbv or something. When I installed Vista, this disapeared and I get a big mess of I/O errors on sdb1 when Fedora starts (presumably its forgotten its a RAID)

This didn't bother me too much, after all, I'm not planning on using Fedora any more (unless F7 is better for me than Feisty of course) However, when I load the Ubuntu 7.04 x64 Alternate text installer, I get a mess of I/O errors too.

I do not want to install on the RAID but I will want to be able to 1) chainload to it if possible, 2) view its files and 3) not get a bunch of errors every time I turn the machine on.

Way back when I tried Dapper x64 Desktop (ended up not using it because it was crap at RAID and kept switching my devices around so almost every time it tried to boot from /dev/sda it ended up trying to boot from 1 of 4 empty card reader drives on an internal usb header, there were a lot of posts about this problem at "mounting root filesystem" on here at the time) I could just apt-get install dmraid, reboot and it would find my raid, but I don't know how I can do anything like this as I am using the Alternate install. 

Does anyone know how I can get it to work?

Thanks

---

### Post by ghell on 2007-05-09
OK, apparently dmraid is in feisty ([http://packages.ubuntulinux.org/feisty/admin/dmraid](http://packages.ubuntulinux.org/feisty/admin/dmraid)) so why do I get all these I/O errors?

EDIT: Ok, the page I was looking at was useless, it claimed that URL was proof that dmraid worked during the installer.

I have found this: [https://wiki.ubuntu.com/FakeRaidSpec](https://wiki.ubuntu.com/FakeRaidSpec) I am pretty much the "John" use case. Does anyone know what I can do?

I don't mean to be impatient but please, somebody answer. In my experience if a post makes it to page 2 of the thread list without an answer, it isn't going to get answered and then in 6 months someone posts "I also want an answer" because they searched the forums.

---

### Post by ubunubu on 2007-05-17
i found this pretty helpful

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I've got an Asus M2N-SLI Deluxe board and am dual booting XP & Feisty off my RAID0,..

I found that Vista x32 would natively recognize my nvidia RAID.  

Visata x64 needed drivers for the RAID

hope this helps!

---

