---
title: "Grub Rescue After ubuntu 14 Partition Wipe"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by boykai on 2016-10-23
Hey guys,

So I have the following setup:
- C:/ Windows 8.1
- D:/ HDD Hard Drive I used on Windows 8.1
- E:/ Ubuntu 14.04


So I wanted to format my Ubuntu hard drive so that I could use it on my Windows setup for more space.

I used the following guide:
[http://askubuntu.com/questions/342857/how-to-wipe-format-entire-disk-using-gparted](http://askubuntu.com/questions/342857/how-to-wipe-format-entire-disk-using-gparted)
(Answer that was posted by [Galgalesh]("http://askubuntu.com/users/172367/galgalesh"))

After I did the guide on my E:/ Drive and rebooted. I am not booting into "grub rescue". 
So I then used this guide:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


The Boot-Repair did not work. 
Here is my output for the repair:
paste2.org/6kdWLbY6


In grub rescue terminal, none of my filesystems displayed by using "ls" work when applying "ls (hd0,msdos2)/boot" or any of the other filesystems listed by "ls" command. For all of the systems I get the error: "error: unknown fileystem."




I just want access to my C:/ Windows 8.1 back, with my E:/ wiped and ready for use on my Windows 8.1 system.




Please help.



Thanks in advance.



SOLVED:
Used this guide:
[https://www.quora.com/How-do-I-fix-a-grub-rescue-unknown-file-system-error](https://www.quora.com/How-do-I-fix-a-grub-rescue-unknown-file-system-error)
Solution by [Vigneshwaran Mani]("https://www.quora.com/profile/Vigneshwaran-Mani-2")


Still don't have access to my Ubuntu formatted hard drive on Windows though.

---

### Post by oldfred on 2016-10-23
[http://paste2.org/6kdWLbY6](http://paste2.org/6kdWLbY6)
Is above your link?

You show no Linux partition.
If you manually deleted it why would you expect to see it?

And Windows has no driver as standard to see Linux partitions. Generally we suggest using a shared NTFS data partition so you do not write into system partitions.

If you did not intend to delete Linux partition it looks like there is space in extended partition in sdb. You may be able to recover with parted rescue or testdisk like these examples.
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

