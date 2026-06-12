---
title: "Recover partition after windows installation"
date: 2015-08-21
forum: Installation &amp; Upgrades
---

### Post by Nayef_Muhiar on 2015-08-21
I tried installing windows on a separate partition and I found that is deleted my Ubuntu 15.04 installation, I tried boot repair but it didn't work, here is my summary
[http://paste.ubuntu.com/12141207/](http://paste.ubuntu.com/12141207/)

---

### Post by oldfred on 2015-08-21
Windows has for years rewritten the partition table leaving off the Linux logical partition.

```
 /dev/sda4 [COLOR=#ff0000]        567,173,118[/COLOR]   976,771,071   409,597,954   5 Extended
/dev/sda5         [COLOR=#ff0000]938,266,624[/COLOR]   976,771,071    38,504,448  82 Linux swap / Solaris


```

It looks like your Linux partition was a logical starting one or two sectors after the start of the extended partition and ending before the start of the swap partition. It probably was sda5 & swap was sda6, but that is not critical as UUID is used for booting.

You should be able to use testdisk or parted rescue to restore the missing partition.
       [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

---

