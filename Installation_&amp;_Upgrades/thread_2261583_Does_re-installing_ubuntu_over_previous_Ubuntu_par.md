---
title: "Does re-installing ubuntu over previous Ubuntu partiton delete the user files?"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by varun10 on 2015-01-19
**Does Re-installing ubuntu over previous Ubuntu partiton delete the user files that were there before?**



I  installed windows 8,1 and I think the bootloader got messed up and I  tried the "check disk for errors" when you first boot the installer and  it fixed them, but ubuntu wouldn't start. I have to try to launch from my bios since the GRUB doens't appear. 
 So I'm thinking about  installing it again, but I wanna keep the files. Would re-installing it  again delete files? I'm afriad choosing the option "Reinstall over  ubuntu" will delete my windows 8.1 partition. 


(sorry images are kinda big so I had to link them)
 [http://i.imgur.com/N75fJro.jpg?1](http://i.imgur.com/N75fJro.jpg?1)



  [URL="http://i.imgur.com/p8FH4NS.jpg?1"]http://i.imgur.com/p8FH4NS.jpg?1

[/URL]

---

### Post by grahammechanical on 2015-01-20
> [COLOR=#000000]"Reinstall over ubuntu" will delete my windows 8.1 partition. [/COLOR]

It will but it should not. It is a bug. It should just reinstall Ubuntu over the existing Ubuntu installation which will over-write any data in Ubuntu. But this bug causes the re-install to use the entire disk.

Do you only have one hard disk? If so it will be called sda. So, run the Try Ubuntu session and use the file manager to open the partition Ubuntu is installed on and then open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sda
```

That should reinstall the Grub boot loader and, fingers crossed, you should be able to load both Ubuntu and Windows. I had to do this when I installed Windows 8 preview edition. I have 2 hard disks and even though I was installing Windows 8 on the second hard disk its install put the Windows boot manager into the MBR of both hard disks. It stopped me from loading Ubuntu on the first hard disk. Now, that is what I call impolite behaviour.

Oh, by the way, we can reinstall using the Something Else option and provided we do not mark the Ubuntu partition to be formatted it should not delete the user configuration files or the user data. Some of us avoid this risk by either using a separate /home partition which we do not format during a reinstall or we keep all our data on another partition and let Ubuntu have a /home folder.

Regards.

---

### Post by kansasnoob on 2015-01-20
Bad, bad bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

It'll be fixed in 14.04.2 but that won't help you now.

I'd first try Boot Repair from the live DVD/USB:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Boot Repair won't fix it then post the URL to the boot info here and someone should be able to help you.

---

