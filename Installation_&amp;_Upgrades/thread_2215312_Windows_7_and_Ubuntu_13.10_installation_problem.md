---
title: "Windows 7 and Ubuntu 13.10 installation problem"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by Piotr_Sumela on 2014-04-06
Hello.
I have a Lenovo y580 with:
[COLOR=#333333]**Procesor:**[/COLOR][COLOR=#333333] Intel Core i3-3110m[/COLOR]
[COLOR=#333333]**Mainboard:**[/COLOR][COLOR=#333333] QIWY4 MB QC GE 2G U2 W/BT/TV[/COLOR]
[COLOR=#333333]**RAM:**[/COLOR][COLOR=#333333] 8GB[/COLOR]
[COLOR=#333333]**Disk:**[/COLOR][COLOR=#333333] Seagate 1TB
[/COLOR]And installed MS Windows 7. The whole disk is formatted like that:
[https://drive.google.com/file/d/0BwvpM- ... ptQjd4YUE/]("https://drive.google.com/file/d/0BwvpM-Sf72Q2ay1OQVptQjd4YUE/") (~70GB left for Ubuntu).
My problem is, that I cant install Ubuntu next to Windows, because Ubuntu 13.10 does not see it in any way. I have to use them both, so I cant resign from Windows. I can wipe my whole disk if that would help, but that should be the last thing that I need to do. 
Screenshots will show you that problem:
[https://drive.google.com/file/d/0BwvpM- ... sp=sharing]("https://drive.google.com/file/d/0BwvpM-Sf72Q2blBPUXRsLVB6SkE/edit?usp=sharing")
[https://drive.google.com/file/d/0BwvpM- ... sp=sharing]("https://drive.google.com/file/d/0BwvpM-Sf72Q2dkZ5eG8taU5pTHc/edit?usp=sharing")[COLOR=#333333] [/COLOR](you may see, that it does not see any OS installed).
[https://drive.google.com/file/d/0BwvpM- ... sp=sharing]("https://drive.google.com/file/d/0BwvpM-Sf72Q2SVE4SjhmUTBaMEk/edit?usp=sharing")
The last part - I'm a soldier and I'll be gone for easter, so if you could help me untill that, I would do exactly everything you need.

Thanks for help.

[COLOR=#333333]
[/COLOR]

---

### Post by Double.J on 2014-04-06
Hi there!

Did this machine previously have a guid partition table? (Such as a windows 8 install) if so, checkout oldfred's post [here]("http://http://ubuntuforums.org/showthread.php?t=2215237") 

If not, could you post what gparted see's or the output 
```
 sudo fdisk -l
```

Jj

---

### Post by oldfred on 2014-04-06
It looks like a typical Windows 7 BIOS install with all 4 primary partitions used. You will need to backup one partition and delete it. And use Windows partitioning tools to shrink Windows to make space for one extended partition. An extended partition then can hold all the Linux logical partitions you need or want.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)


 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

