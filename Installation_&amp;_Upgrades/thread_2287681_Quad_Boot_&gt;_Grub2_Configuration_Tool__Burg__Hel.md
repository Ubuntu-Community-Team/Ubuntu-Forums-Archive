---
title: "Quad Boot &gt; Grub2 Configuration Tool / Burg  Help - Win7/ML/Ubuntu/SteamOS"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by Sidus_Solutions on 2015-07-21
Hi I'm looking for some help if possible. I'm new to Ubuntu and Linux in general but I like to tinker and I learn relatively quickly. 

So I decided to build a quad boot system using separate drives for each OS and I plan to maybe add Windows 10 into the mix to make a [COLOR=#000000][FONT=Helvetica Neue]penta?? boot system, why you ask? Well, why not :-)

So my setup is as follows:

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Intel i7 3770k, Asus P8Z68-v Pro/Gen3, 16GB Ram, PNY GeForce GTX660[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Drive 1 : Samsung SSD 840 EVO 250GB (Windows 7)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Drive 2 : SK hynix HFS 256GG (Mountain Lion)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Drive 3 : [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]WD Green 1TB HDD (Ubuntu 15.4)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Drive 4: [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Seagate 2TB SHDD (Steam OS)[/FONT][/COLOR]

[FONT=Verdana, Helvetica, Arial, sans-serif][COLOR=#000000]So far everything is working great and I can choose the drive to start from bios and everything boots perfectly. I used Chameleon bootloader for the hackintosh but it only see's the mac & win 7 drives so this is no good. I installed grub2 on ubuntu and also installed Burg so I can theme the boot screen how I like and I actually got a great boot screen showing all 4 drives / OS'es which I setup using [/COLOR][/FONT]Grub2 Configuration Tool and a bit of theme editing..

The problem now is the Mac and SteamOS do not load from the boot menu either, they show but hitting return on them does nothing. I have tried using Grub2 Configuration Tool and it detects all the drives and Mac 32bit & 64bit but they are not bootable and manually trying to configure it with chainloading +1 to go to Chameleon has not worked for me either. 

So can someone please please give me a straight forward clear answer, is what I'm trying to do possible and is there some easy config guide for burg / grub2 or some other solution. 

Should I back track and try configure everything using Clover on the Mac side???

Any help is greatly appreciated...I have scoured the web looking for a answer and although there is lots of answers most of them are either out of date or do not work. I should state I'm willing to reinstall all drives except the windows which seems to be fine on both sides anyway.

---

### Post by dino99 on 2015-07-21
burg was used some years ago, and i does not know its status nowadays (maybe start keeping things simple first)

grub2 can load all the OS if the path is found (uuid); check them with that command: > sudo blkid , they need to match /etc/default/grub , then > sudo update-grub done from the drive where it is installed (something like /dev/sda) actualize the latest change made

---

### Post by oldfred on 2015-07-21
We do not support Hackintosh, please see Ubuntu code of conduct.
       [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)
Ubuntu Forums Code of Conduct
[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

But you have a new UEFI system and it sounds like you installed most system in BIOS mode. 


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

      
 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

