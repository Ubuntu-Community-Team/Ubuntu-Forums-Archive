---
title: "grub_put_ error"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by shiwak on 2010-06-03
Hi,

I upgraded the ubuntu from 9.10 to 10.04 last night through update manager. 
Before upgrade to 10.04 i took care of keeping up-to-date in update manager.

I have two hard drives. one is 40GB normal and other is 1TB STATA.
9.10 was installed on 40GB (sda1,sda2(swap)), home is mounted on sata drive.
While upgrading pop up question came asking where to install grub. 
I installed at sda1.

**Upgrade to 10.04 is done successfully and when the system restarts it is giving *'grub_put_' error*. Please some body help me to restore my OS. **

My system doesn't have windows OS at all. I hate windows.

Note: Why do users are being given options to control grub while installation. Mostly users doesn't require that. It should be automatic. I had seen most of the linux installations will end up with grub error. With out grub nobody can boot the OS. There should be some way to keep this hidden from the user unless required for advanced users.

---

### Post by shiwak on 2010-06-03
I had seen other threads and found that i also did the same mistake like this below.

"I did the ultimate mistake and changed something I was not sure about.  When I got to the Keep existing Grub setting's I chose to load the new  ones rather than keep the current file set."

Some body help me how to restore Ubuntu OS now.

---

### Post by bumanie on 2010-06-03
You should try to reinstall grub via a live cd. Follow point 13 from [here]("http://ubuntuforums.org/showthread.php?t=1195275"). Essentially from the live cd you should go to terminal and > sudo mount /dev/sda1 /mnt> sudo grub-install --root-directory=/mnt /dev/sda> sudo umount /mntand then reboot. Hope it works.

---

### Post by kansasnoob on 2010-06-03
> **shiwak said:**
> Hi,

I upgraded the ubuntu from 9.10 to 10.04 last night through update manager. 
Before upgrade to 10.04 i took care of keeping up-to-date in update manager.

I have two hard drives. one is 40GB normal and other is 1TB STATA.
9.10 was installed on 40GB (sda1,sda2(swap)), home is mounted on sata drive.
While upgrading pop up question came asking where to install grub. 
I installed at sda1.

**Upgrade to 10.04 is done successfully and when the system restarts it is giving *'grub_put_' error*. Please some body help me to restore my OS. **

My system doesn't have windows OS at all. I hate windows.

Note: Why do users are being given options to control grub while installation. Mostly users doesn't require that. It should be automatic. I had seen most of the linux installations will end up with grub error. With out grub nobody can boot the OS. There should be some way to keep this hidden from the user unless required for advanced users.

> I installed at sda1.

That in itself is a problem because sda1 is a partition. It's very seldom wise or necessary to install grub to a partition rather than the MBR of the drive.

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

> Note: Why do users are being given options to control grub while installation. Mostly users doesn't require that. It should be automatic. I had seen most of the linux installations will end up with grub error. With out grub nobody can boot the OS. There should be some way to keep this hidden from the user unless required for advanced users. 

The devs almost never read the forums, please comment at my bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

If you need more detailed help fixing this please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by shiwak on 2010-06-06
Hi bumanie and kansasnoob

"sudo mount /dev/sda1 /mnt 			 		
sudo grub-install --root-directory=/mnt /dev/sda" 			 		

It worked, cool..
Thanks for your reply.

I recommend people who read this thread could get more info on grub and MBR from the following links

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

