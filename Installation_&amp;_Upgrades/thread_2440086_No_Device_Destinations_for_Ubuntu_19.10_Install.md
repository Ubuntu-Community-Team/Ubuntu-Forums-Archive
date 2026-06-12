---
title: "No Device Destinations for Ubuntu 19.10 Install"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by srobuhson on 2020-04-05
Hi, 

I am trying to install Ubuntu 19.10 on an HP Pavillion running Windows 10. I have created a 64 GB partition to house the installation. I used Rufus to create a bootable USB containing Ubuntu 19.1 and am able to boot the Ubuntu Installer. However, when it comes time to actually install Ubuntu, no locations are available on my PC and the installation freeze when I try to add a partition. I am connected to Wi-fi. 

Here is the resulting screen with the download option I selected in case that is relevant:


[ATTACH=CONFIG]285412[/ATTACH][ATTACH=CONFIG]285413[/ATTACH][ATTACH=CONFIG]285414[/ATTACH]


Any help that you could provide on the issue would be greatly appreciate! I apologize if a similar question has been answered. I've looked through the forum for a while with no success.

---

### Post by Autodave on 2020-04-05
Did you shut off *fast boot* in the BIOS?

---

### Post by srobuhson on 2020-04-05
Autodave,

Thanks for the response. I had not, but I did so and got the same result. I noticed this time that before the Ubuntu installer boots, there is an error message that says something to effect of "Error communicating with TCM ... " , however it disappeared before I could take a picture.

---

### Post by CelticWarrior on 2020-04-05
You need to:

[LIST=1]
[*]Install support for AHCI in Windows (Google it)
[*]Change the SATA mode from whatever that is (RAID or Intel RST) to AHCI.
[/LIST]

---

### Post by oldfred on 2020-04-05
You also need Windows fast start up off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Many systems also need UEFI update and if SSD, SSD firmware update.

More info on UEFI install in link in my signature below.

HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)

---

