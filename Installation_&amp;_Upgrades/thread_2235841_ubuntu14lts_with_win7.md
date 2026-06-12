---
title: "ubuntu14lts with win7"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by ggg2 on 2014-07-23
i would like to install ubuntu with win7. i know the way i watch many vedios but i have qustion what should i choose begininning or end (from "somthing else") to make  the both systems work. i install ubuntu this way to be able to set swap section, i will cut partition from d drive not from c.
can i make win7 works automatically.

---

### Post by grahammechanical on 2014-07-23
You should outline the drives/partitions that already exist on that machine. Otherwise, it would be unwise to confirm your intended actions.

Use Windows utilities to defrag Windows at least twice; make sure Windows loads and use Windows utilities to create free/unallocated space and again make sure that Windows loads afterwards.

Those are the basic precautions that I have seen offered on this forum.

Regards.

---

### Post by oldfred on 2014-07-23
Beginning or end is just where partition will be in the unallocated space. So you can put a new partition at the end first if desired. Usually I just plan what partitions I want and start at beginning and specify beginning all the way thru.
I do prefer to use gparted to create partitions in advance, and really suggest shrinking Windows with Windows own disk tools and reboot Windows so it will run chkdsk and make repairs for its new size. But do not create partitions with Windows as it may convert to dynamic which does not work with Linux.

Make sure you only have 2 partitions. Most Windows 7 systems use all 4 primary partitions, but the others are hidden in Windows.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by ggg2 on 2014-07-24
thank you all i found some vedios in my language(arabic) and make every thing i want

---

### Post by bulrush2 on 2014-07-26
You can install Ubuntu under Windows using [VirtualBox](https://www.virtualbox.org/) without having to do a dual boot. The virtual machine, created and managed by VirtualBox keeps your Windows installation safe. I'm sure they have free VM software for Macs too. Install the Ubuntu server as a VM and practice away. 


You can google "free virtual machine for windows".

---

