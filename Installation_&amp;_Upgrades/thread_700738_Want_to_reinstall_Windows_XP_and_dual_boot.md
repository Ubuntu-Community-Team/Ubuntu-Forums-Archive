---
title: "Want to reinstall Windows XP and dual boot"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by CUrza on 2008-02-18
Hey everyone!
Just got Ubuntu and love it. Problem is, when I installed from the live cd, I chose to use the entire partition because I didn't need anything on my Windows.

Now, I realized I can't use Reason 4.0 or Ableton Live 6.0.7! So I inserted my Windows XP install cd, but the only disk partition that comes up is the one with my Ubuntu on it. So I selected that one, but then I got a message saying that Windows was unable to install, despite the fact that I have 47GB available. Any ideas? I know that once I redo Windows I will need to fix GRUB, and that's fine. My concern is that I am unable to put Windows on again. I'm a Linux noob, so any explanations will have to be pretty clear. Thanks in advance everyone! This is easily the most helpful community I have ever been a part of. I love Linux so far!!

---

### Post by Pumalite on 2008-02-18
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Format the 47 GB ntfs and see if XP will install there. Truth is, it's much better to delete everything in your hard drive and make a new large partition of your whole hard drive, formatted ntfs, install XP. Reboot Gparted, resize XP partition (right click, choose 'resize') and install Ubuntu again.

---

