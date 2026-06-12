---
title: "Confused about installation and partitions."
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by BIAtech on 2012-08-08
Hi,

I'm not too sure what is going on with my computer and I would like someone to let me know what all of this means. I accidently downloaded Ubuntu twice. From what I read the installation will overwrite the other installation. I downloaded both of them next to Windows 7. I've attached a photo of what gparted found. Also I have no devices hooked up to my computer but in the devices column of my window I says I have 747GB and 128GB attached to my machine. The amount of space I partitioned for one Ubuntu was 630 something or 750 total and the other was about the same, but since I overwrote it, I'm assuming there is just one partition. I just need help understanding what is going on with my computer. Any education on what I have done or what is going on would be much appreciated! Is there a way to fix what is happening here?

---

### Post by darkod on 2012-08-08
As you can see, that only shows windows ntfs partitions. So I guess you used wubi, not a dual boot next to windows (along side). That is not correct. Wubi installs inside windows, so you will not see linux partitions when looking at the hdd.

As for wubi, I don't use it and I have no idea what would happen if you install it twice, does it install over the old one or not. When you want to remove wubi, you do it in Programs like any other software.

If you have more than one disk, you should select in Gparted the other disk too, in the drop down box top right. The screenshot you posted shows only one 750GB hdd. And no ubuntu partitions on it.

---

### Post by BIAtech on 2012-08-08
Thanks for responding!

I don't think I use wubi. I simply went to the ubuntu site downloaded the iso and made a live usb with universal usb installer. I went into bios and loaded from the usb. From these methods is is still possible I used wubi? I just wanted a dual boot. Could you help me fix this dilemma and clean up my partitions?

---

### Post by darkod on 2012-08-08
But did you install or you only loaded the usb in live mode (Try Ubuntu)?

Ubuntu can run in so called live mode, from the bootable cd or usb without installing anything on the hdd. When you shut down the live mode, nothing remains.

At this moment I don't see anything to "fix".

Run ubuntu again in live mode with the usb, open terminal and post the output of:
```
sudo parted -l
```

That will show more details about your disks and partitions.

---

### Post by BIAtech on 2012-08-08
It's possible I only loaded the usb on live mode. I can't run from live mode right now, because I have a a few scripts running that need to process over night. Is there a way I can get you the information you need from inside live mode (if that's what I'm in). If not, I will have to get back with you either tomorrow or in a couple days. I will get to this as soon as possible.

---

### Post by darkod on 2012-08-08
> **BIAtech said:**
> It's possible I only loaded the usb on live mode.[COLOR=Red] I can't run from live mode right now[/COLOR], because I have a a few scripts running that need to process over night. [COLOR=Red]Is there a way I can get you the information you need from inside live mode[/COLOR] (if that's what I'm in). If not, I will have to get back with you either tomorrow or in a couple days. I will get to this as soon as possible.

I don't understand. First you say you can't run it in live mode, and then asking whether you can do it from inside live mode.

Yes, you can run that command from either live mode or from installed ubuntu, doesn't make a difference.

No problem if you can't do it right now, post it when ever you can.

---

### Post by BIAtech on 2012-08-08
What I mean is I can't 
> Run ubuntu again in live mode with the usb
because I have things currently running.
What I'm asking is if I run
```
sudo parted -l
```
from where I am right now will it give you the information you need?

---

### Post by darkod on 2012-08-08
The thing is, I have no idea where are you right now so I can't answer that. :)

If you already have live mode running and you only can't reboot, no problem. Open terminal and run that command, you don't need to reboot anyway.

If you are inside a booted ubuntu installation, again, open terminal and run it.

As long as you run it on the same computer, no problem.

---

### Post by BIAtech on 2012-08-09
I ran ```
sudo parted -l
``` in wherever I am right now. I attached the result.

---

### Post by oldfred on 2012-08-09
For terminal output better to just copy & paste into message, use screenshots for gui output. If output is long use code tags or highlight & click on # in edit panel above. Also attach screenshots with paperclip icon in edit panel.

You have two 750GB drives. Windows is on one, & Ubuntu on the other. You show two Linux partitions. That could be two installs, or an install with a separate /home. Does it boot ok?

May just be easier to post BootInfo from Boot-Repair to see all the details of your install(s).

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

With larger drives I prefer a smaller / (root) of 25GB and then larger /home and/or other data partitions for all user data. System is  a bit more efficient as files used most often are closer together on drive.

---

### Post by madjr on 2012-08-09
you may also try this link:

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

### Post by BIAtech on 2012-08-09
Thanks for the help everyone!

This is what my GRUB looks like. I don't know if this is much help.
```

Ubuntu, with Linux 3.2.0-27-generic
Ubuntu, with Linux 3.2.0-27-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows7 (loader) (on /dev/sda1)
Windows7 (loader) (on /dev/sda2)
Ubuntu, with Linux 3.2.0-23-generic (on /dev/sdb)
Ubuntu, with Linux 3.2.0-23-generic (recovery mode ) (on /dev/sdb)

```

I always choose
```

Ubuntu, with Linux 3.2.0-27-generic
Ubuntu, with Linux 3.2.0-27-generic (recovery mode)

```


I finally had the opportunity to restart my computer. However, I didn't do what Darko had said to do.
> Run ubuntu again in live mode with the usb
(Darko: This was by accident, I just forgot to plug the usb in. I can still do this if it would be helpful.)
To my liking, everything I had there.....was still there! So, I believe I wasn't in live mode.

> You have two 750GB drives. Windows is on one, & Ubuntu on the other. You show two Linux partitions. That could be two installs, or an install with a separate /home. Does it boot ok?
oldfred: The boot has some weird multi-colored lines, but then it opens my home page. 

Here is the url to my bootrepair info [http://paste.ubuntu.com/1138245/]("http://paste.ubuntu.com/1138245/").

Oldfred: Could you explain this further? I'm just not that partition savy. Or maybe provide me with a link that has reading?
> With larger drives I prefer a smaller / (root) of 25GB and then larger /home and/or other data partitions for all user data. System is a bit more efficient as files used most often are closer together on drive.

---

### Post by oldfred on 2012-08-09
You have two installs sdb1 & sdb6. The grub2 boot loader in the MBR of both sda & sdb boot the install in sdb1.

I like to have the boot loader for an install in the same drive. So if the other drive ever fails I can use BIOS to choose to boot other drive. I do like having Windows in one drive & Ubuntu in another & I usually do at least some backups from the Windows drive onto the Ubuntu drive & vice-versa. You still should backup most important data to DVDs, flash drives or other images to also have some history.

Boot-Repair can install a Windows like boot loader or you can use Windows to run its BootRec.exe /fixMBR to sda only. Then set BIOS to boot sdb and you can boot both from the grub menu. 

You can use gparted from liveCD to delete sdb6, if you do not want that install. Since you have larger drives you should have room for another install if you just want to experiment. 

When dual booting I also suggest a separate NTFS shared data partition. Then you can set the Windows system partition as read- only in Ubuntu and only write into the shared data. Windows for whatever reason does not like too many writes into its system or users accidentally damage Windows as the Linux NTFS driver shows all files & folders. Windows hides important system files & folders for your own protection.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

If a new install you can easily reinstall. Or you can shrink the Linux system partition with gparted, create a new partition for /home and maybe shared NTFS. Then you can move your /home folder to the new /home partition.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I only had / (root) and swap for a couple of years but almost immediately created the shared NTFS. So it is not required to have a partition for /home. But I used shared NTFS for Firefox & Thunderbird profiles, so I had same bookmarks & email in both system & all photos, so I could use the Windows version of Picasa in both.

General info:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by BIAtech on 2012-08-09
Thanks!

I will probably use gparted to delete the sdb6. Is there a way I can tell how big sdb6 is? I don't know if I should attempt this, but I would like to have the > bootloader for an install in the same drive for each OS. I will do some reading and then decide. Thanks for the literature! I will mark this thread as solved.

---

### Post by oldfred on 2012-08-09
Post #9 said it was 128GB.

I was suggesting installing Windows boot loader to sda, just so the Windows drive could boot without sdb. And if booting with the grub2 boot loader in sdb, you can boot Ubuntu without sda.

---

