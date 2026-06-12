---
title: "Windows 10 update, Stuck in grub rescue"
date: 2017-10-02
forum: Installation &amp; Upgrades
---

### Post by colony11 on 2017-10-02
I am/was dual booting windows 10 and ubuntu.  Windows recently asked me to do an update and after it was complete on reboot I get stuck in the grub rescue menu.
I tried all the partitions and none of the them had a bootable file system.  Also tried boot-repair default repair and it didn't fix anything.

Grub repair info is here:
[http://paste.ubuntu.com/25661172/](http://paste.ubuntu.com/25661172/)

Advice anyone?

Matt

---

### Post by oldfred on 2017-10-02
Many threads with exactly the same issue going back to Windows 7 updates/upgrades. 
Microsoft has a bug that "forgets" to write logical Linux partitions back into a MBR(msdos) partition table. More prevalent now that many are upgrading Windows 7 to 10 or any upgrade within 10.

```
/dev/sda3         210,554,878   475,406,335   264,851,458   5 Extended
/dev/sda5         435,165,184   475,406,335    40,241,152  82 Linux swap / Solaris
``` 
Your gap is from the start of the Extended partition at 210... and the start of swap at 435...
If just one partition that will be the approx start & end of missing partition. There is normally at least one or two sector between partitions.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors (already shown above for you, more for anyone else reading thread):
sudo parted /dev/sda unit s print 

You should be able to use testdisk or parted rescue.
You probably will have to reinstall grub to MBR.

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by colony11 on 2017-10-02
Thanks, worked perfectly.

Used the parted/rescue command based on the start of sda3 to end of sda5.  Although the partion it found only went to the start of sda5 so I'm not sure if I had to list to the end.
Then ran boot-repair to find grub.
New time I ran linux I had to also run update-grub.

---

