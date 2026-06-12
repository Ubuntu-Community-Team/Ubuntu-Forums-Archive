---
title: "How can I link an existing home hard drive to a new install?"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2014-11-15
Hello

What i would like to do is use my existing 'Home' hard drive (SSD) and link it to a new 'system' hard drive (SSD).

That is, two drives, one containg a new Ubuntu system install, the other containing my home folder that I want to retain.

I have tried using 'something else' when freshly installing unbuntu. I select the new drive for the system install and then tell the installation dialogue that I want my existing home drive mounted as /home, without formatting.

Then what happens is my home drive is wiped and I get the default home folders instead.

So how can I use two drives, one with a fresh Ubuntu system install and the other as 'Home' using an existing hard drive containing my home folder and keep my home data?

---

### Post by oldfred on 2014-11-15
Are you sure you are selecting the correct drive and not clicking Format on /home existing partition but mounting it?

I do prefer to partition with gpt and create my partitions in advance with gparted. Then in the installer I just choose which partition is / & which it /home. You do have to choose drive as well as partition. I now do not use /home but have separate /mnt/data partition which then I have to separately add after the install. My screen shot below is reusing an old install's partition on sdc and partition on sdd.

Several examples of Something Else with screen shots. If a dual boot with Windows just ignore that part.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

