---
title: "Ubuntu can't see the Win7 pro installation"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by SixOfOne on 2015-08-08
I've been caught before so I'm cautious...
3 HDD's, 1x 2tb with win7pro, 1x 500gig storage and 1x650gig divided into 200/450 both empty.
I want to put Ubuntu on the 200gig partition, and I really don't care what it does to the drive, but it can't see win7, says there's no OS and seems hell bent on installing on the 2tb drive.
Not being that familiar with Ubuntu, the way it describes drives and what to do when you click on them is a tad confusing.
I'm fairly sure if I disconnect the 2tb drive, then I will have boot problems.

I'm not sure why it says it's free space, as I'm running it from the DVD and when I click on files, it shows all the files on the HDD, but when I click instal, it says it's free space.

Any ideas?

Thanks

---

### Post by Vladlenin5000 on 2015-08-08
With such multiple drives configuration you should use "Something else" and there create the required partitions.

---

### Post by oldfred on 2015-08-08
More details on Something Else. But be sure to change default install of grub from drive that is sda to drive that is Ubuntu.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):


[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

---

### Post by SixOfOne on 2015-08-08
Thanks for you help,
This is the first time that I have had a problem with dual boot, though last time was Win XP and Ubuntu 12 something.
I did choose "something else" but struggled to distinguish between the partitions.... that may have been Mr Beam's fault.
I'm off to do some reading :)

Oh, one last thing, if I chicken out completely and disconnect the drive with Win7 on it, I can use is it grub, to fix the boot section so i have a choice?

---

### Post by oldfred on 2015-08-09
If you only have one drive connected that is the Ubuntu drive, the default install of boot loader to sda is the only and is the correct option.

Then when all drivers are plugged back in, run this to add Windows to grub menu.
sudo update-grub

Be sure to plug Windows drives back into same SATA ports on mother board.

---

