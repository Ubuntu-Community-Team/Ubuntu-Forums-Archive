---
title: "New install 16.04 to 20.04 - ext4 as external disk for file transfer"
date: 2021-01-29
forum: Installation &amp; Upgrades
---

### Post by iqdesigner on 2021-01-29
Hi

I am a happy user of Ubuntu 16.04 since start. But now come the time to move to 20.04
I have a new disk in my hands and I am thinking to make a new install in it with 20.04

My current disk is ext4. Can I bring it out of my laptop put it in an external case and use it after the new installation as a usb device to transfer my files in my new disk?
Will have any permission problems? Do I need specific commands to mount it? or take any other steps before move to new installation?
As I understand I need only read access to just read and copy my files (no apps just files docs, images, data etc)

My old disk is a 1TB disk (mostly full) and want to avoid to backup in another disk and then transfer in the new disk. 
Shall I proceed?

Thanks

---

### Post by Impavidus on 2021-01-29
* Can I bring it out of my laptop put it in an external case and use it after the new installation as a usb device to transfer my files in my new disk?
==> Yes, you can.

* Will have any permission problems?
==> If you use the same user ID on both the old and the new system, there won't be a permissions problem. The user created during installation of Ubuntu always has user ID 1000, so unless you manually changed that, no problem.

* Do I need specific commands to mount it?
==> Nothing special. Just mount it like you mount any storage.

* or take any other steps before move to new installation?
==> No other steps.

* My old disk is a 1TB disk (mostly full) and want to avoid to backup in another disk and then transfer in the new disk. 
==> Best to have backups anyway. Just in case you drop and break your drive.

---

### Post by ActionParsnip on 2021-01-29
Sure, it's a Linux file system in Linux. It will be seen as casual data.

---

### Post by iqdesigner on 2021-01-31
Yes that work 20.04 see all my files from 16.04. I give and a chmod for some files.
Thanks [[COLOR=#000000]Impavidus[/COLOR]]("https://ubuntuforums.org/member.php?u=1417721"), [[COLOR=#000000]ActionParsnip[/COLOR]]("https://ubuntuforums.org/member.php?u=1079078")

---

