---
title: "Help with Grub (Stopped working after windows 10 update)"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by gonter94 on 2017-10-19
Hello, first of all I know there are a couple (maybe maaaany) threads about this issue but I still can't figure out what is wrong, grub was displaying and everything was working perfectly before a major windows 10 update. I'll link the bootInfo repair-tool gave me. Thanks in advance and hope anyone here has the time to help me...

[URL="http://paste.ubuntu.com/25776234/"]http://paste.ubuntu.com/25776234/

[/URL]And bcdedit looks like this:

[IMG]http://i65.tinypic.com/2zzhnp1.png[/IMG]


):P

---

### Post by gonter94 on 2017-10-20
Will testdik help me?

---

### Post by oldfred on 2017-10-20
You can use testdisk or parted rescue.
You were bitten by an old Microsoft bug where on installs or major updates where it rewrites partition table it "forgets" to write the logical Linux partition(s) back into partition table. You  data all should be there, but you may have to reinstall grub to MBR.
This may happen on other major Windows updates, best to keep a backup of just partition table, make sure you update it if you change partition layout.

 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

All of these are essentially the same using testdisk or parted rescue.
It seems newer version of testdisk has finally converted from CHS to sectors so much easier to use.

It probably renumbered your Linux partition from sda5 and made swap sda5, but that normally not critical.
Your missing partition starts a couple of sectors after the start of the extended 764,002,302 and ends somewhere before that start of swap 
968,802,304.

```


/dev/sda4         764,002,302   976,771,071   212,768,770   5 Extended 
/dev/sda5         968,802,304   976,771,071     7,968,768  82 Linux swap / Solaris

``` [SOLVED] Windows 10 update, Stuck in grub rescue 
[https://ubuntuforums.org/showthread.php?t=2373061](https://ubuntuforums.org/showthread.php?t=2373061)
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
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

