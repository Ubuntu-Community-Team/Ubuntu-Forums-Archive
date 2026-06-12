---
title: "Questions About Backing up Win 10 64 on HP Spectre x360 Before Installing Ubuntu"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by Elaphe on 2016-02-14
Hi guys! I recently purchased an [HP Spectre x360 model 13-4105dx]("http://www.bestbuy.com/site/hp-spectre-x360-2-in-1-13-3-touch-screen-laptop-intel-core-i7-8gb-memory-512gb-solid-state-drive-natural-silver/4334300.p?id=1219732370298&skuId=4334300&cmp=RMX") and I would like to dual boot with Ubuntu, but I have some questions about backing up my Windows 10 64 installation. On my previous laptop, I was able to "shrink" the install of Windows using some utility that escapes me now. Is this still possible, or is it best to use a bootable backup of Windows and reinstall it on a dedicated partition? If a backup is preferable, is it best to contact HP and ask for a DVD image and then use an external DVD to do the install? And last, I'm assuming most people are creating a bootable USB backup of Windows, but my question about doing so is what size USB stick do I need to do this? I'm finding a lot of answers from 3GB to 64GB, what is correct? I have 4GB sticks currently, but would need to order a larger one if needed. And, am I backing up just the "hidden" patition that holds the Windows reinstallation info, or am I backing up my working Windows partition, aka "C drive"? I hope someone here can help point me in the right direction as I'm anxious to get Ubuntu going on this machine. If you need any more info about my system or please just let me know.

Thank you in advance for your help!

---

### Post by oldfred on 2016-02-14
I purchased a Dell SFF system for use with TV. My first experience with Windows 8 as I last shut down XP about 5 years ago.

Dell recommended a backup, that used 3 DVDs. I think that was the install image that would let me reinstall as purchased. And then would not need Dell recovery partition on drive.
Windows then recommended a backup that took 8GB flash drive. And I think that replaces the Windows recovery partition.
And I ran Macrium Reflect full backup on a 32GB flash drive that used about 25GB. And created two DVDs for booting it, one Windows PE and one Linux.

Of course a few months later Windows updated to Windows 10. And 10 has been working ok. I only use Windows to watch Comcast remotely. But with 10 I started getting low memory, but only occasionally. New drivers from Dell for Windows 10 helped but still not totally solved.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Elaphe on 2016-02-15
Hi! Thanks for the reply! I should mention my laptop is basically brand new, and I have nothing saved on it or installed to it that I wouldn't mind losing. It came with very little bloat, though there's a couple things that I probably would uninstall. So that being said, I would be perfectly fine with a backup of Windows just as it shipped with the laptop new. Would it be best to just contact HP, get the DVD images, and get an external drive? Do these external drives work without any extra drivers on modern machines? If I went this route, I would clean out and repartition the drive, so I'd be starting from a blank drive, essentially. Would this work?

Thank you very much for your help, I really appreciate it!

---

### Post by Mark Phelps on 2016-02-15
My suggestion, is if you want to create recovery media for Win10, then consider using a third-party solution known as Macrium Reflect (MR). 

What I recommend is the following:
1) Download and install Macrium Reflect (MR)
2) Connect the new drive to the PC using a USB drive adapter
3) Run MR and choose the option: "Backup --> Image Selected Disks" to clone the current drive onto the new drive.

Now, you have a complete copy of all the partitions on the drive -- and can restore it to the current state at any time in the future.

Good Luck

---

### Post by oldfred on 2016-02-15
One user, who must get new laptops regularly, posted that his backup is just removing hard drive from new laptop and installing SSD to make system a lot faster. Then when he sells it, he puts hard drive back in and has a "brand new" Windows to sell it with.

Most external drives work. Just some brands install proprietary backup software that only works with Windows and may need total reformatting. Many buy a standard drive and a USB caddy. But if you buy a caddy make sure it says it supports USB3 and larger drives. Some have found caddies that just do not work on USB3 or with drives over 2TiB.

Your hard drive should have a recovery partition on it, and HP should have instructions on how to make recovery DVDs or flash drive. I would still use Macrium Reflect to make another backup.

---

