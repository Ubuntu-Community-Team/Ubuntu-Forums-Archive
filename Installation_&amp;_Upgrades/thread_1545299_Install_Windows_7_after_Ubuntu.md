---
title: "Install Windows 7 after Ubuntu?"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by michaelzap on 2010-08-03
Anyone tried this yet? How did it work out? I don't mind having to reinstall GRUB, but I don't want to lose my existing Ubuntu installation by accident.

Here's what I currently have on my laptop:
[LIST]
[*]Lenovo system restore partition
[*]Vista image partition (for reinstallation)
[*]Vista
[*]Ubuntu Lucid (+swap)
[/LIST]

What I'd like to do is to delete all of the partitions on the drive except for Ubuntu and then install Windows 7 to a new partition. I'd ideally like to leave two more partitions free (one for OSX and another for Linux beta testing and experimentation), but that's probably not an essential detail. If there's any danger of losing my Ubuntu installation in this process, I probably wouldn't do it now, since I'm about to go on a work trip and I don't want to deal with any surprises on the road.

Thanks in advance for any advice.

---

### Post by Rubi1200 on 2010-08-04
It is possible to do what you want and, as you already pointed out, you will need to reinstall GRUB.
 
First and foremost, make a backup of all important files before you start.
 
I recommend using GParted from the LiveCD to work on your partitions.
 
Install Windows 7 and then reinstall GRUB.
 
Here are some links I hope you will find useful:
 
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling)
 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2010-08-04
You should be able to install win7 into the Vista partition. I would shrink it first with windows tools before installing. If you have created the backup Vista disk, you probalby do not need the Vista recovery partition. Would you ever want to totally erase your drive and reinstall Vista as it was when you bought your system?

I like having several extra 20-25GB partitions for system installs. If you create separate shared NTFS and/or separate ext3 or ext4 data partitions, your system partitions do not have to be very large. It is easier to share data partitions and you should not share /home except as part of an upgrade, and once upgraded the older system's software may or may not recognize all the new settings.

---

