---
title: "Duel booting windows 7 and ubuntu with two harddrives"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by chriscowling on 2010-11-23
Hi guys,

I want to boot both windows 7 and Ubuntu on my computer. I have two hard drives and would like to put Ubuntu on the master and Windows 7 ultimate on the slave so that I can play games but use Ubuntu as my normal everyday operating system. I have Googled it but all I found was how to put them on the same HD.  

Any help would be appreciated.

Thanks
Chris

---

### Post by kansasnoob on 2010-11-23
If you're installing 10.10 (Maverick) you might find some of the info I compiled here useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

However that's quite general! Before making any specific installation and/or partitioning recommendations I'd at least want to see the output of these two commands:

```
sudo fdisk -l
```

```
free
```

---

### Post by Mark Phelps on 2010-11-23
Simply do the following (what I do):
1) Disconnect the MS Windows drive
2) With only the target Ubuntu drive connected, boot from the Ubuntu CD and do a full install
3) Reconnect the MS Windows drive but continue to boot from the Ubuntu drive
4) Boot into Ubuntu, open a terminal, enter "sudo update-grub".  This will regenerate the GRUB menu, adding entries for MS Windows
5) Reboot.

Should now get a GRUB menu with entries for Ubuntu and for MS Windows.

---

### Post by pricetech on 2010-11-23
Another option you might have is to choose the specific boot device in the BIOS at each boot.  Some BIOSs support that and some don't.  If yours does you might want to exercise that option.  Some folks just like it better that way.

You'll still need to install each OS with only its drive connected to avoid any chance of wiping the wrong drive.

---

