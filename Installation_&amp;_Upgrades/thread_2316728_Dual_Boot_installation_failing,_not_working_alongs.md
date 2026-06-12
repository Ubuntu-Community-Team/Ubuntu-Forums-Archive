---
title: "Dual Boot installation failing, not working alongside Win10 on Laptop"
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by greentea2 on 2016-03-10
Since several days I am failing to install Ubuntu 14.04 with alongside Windows 10 on my laptop. I could install it from my USB stick, but after installation is finished I still cannot boot into it. Currently I have a Thinkpad T440 with Win10 running in UEFI mode. 
 
I have tried to install Ubuntu according to following instructions: 
_[https://forums.linuxmint.com/viewtopic.php?f=42&t=163126](https://forums.linuxmint.com/viewtopic.php?f=42&t=163126)_
[U][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[/U]..I also have used the option to install it automatically which did not work out neither. 
 
Last month I have installed Linux Mint in dual boot with Win10 exactly this way on my Desktop without any issues, but on my laptop for some reasons there is working something wrong. I am sure that I have followed strictly all instruction.
 
To recap again: 
- I am 100% sure that I have disabled secure boot in the BIOS and in my Windows settings. 
- excluded the windows boot loader
- I have tried to install Ubuntu in UEFI only mode and both: UEFI first option
 
Please see following the pics. I really hope there is someone who can help me out, for sure I made a mistake somewhere.

---

### Post by greentea2 on 2016-03-10
Sorry, I forgot to attach the pics :)

---

### Post by oldfred on 2016-03-10
You had pending new partitions, but you have to tick the green check mark icon to get the changes to take place.
Then you have to use Something Else to choose/change the partition you created to use as / (root) and format as ext4. It will find & include an existing swap automatically.

Make sure Windows fast start up is off.

       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme
[/URL]
 UEFI install,windows 8 with Something Else screen shots
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) 

[URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]
[/URL]

---

### Post by greentea2 on 2016-03-10
Hi @oldfred, thanks for your answer! For sure the fast startup in Windows is switched off. I also deactivated secure boot and SRT in the BIOS.


Besides, I am not sure what you mean with pending new partitions. The picture above were from Gparted. 100% I checked the mark and later, when installing I used the New Partition#2 as root and not home! 


Exactly like here:
[IMG]https://forums.linuxmint.com/download/file.php?id=20156&mode=view[/IMG]


Later I will try to get through your links!

---

### Post by greentea2 on 2016-03-11
I've just once again installedUbuntu, but it was still not booting. Then I run again the live install USB on top and installed boot-repair according to following tutorial: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Afterwards regretfully nothing boots, except if I include the windows boot loader again in first place of the boot order in the BIOS I get Windows running.

The Boot-Repair URL was [COLOR=#0000ff][B]paste.ubuntu.com/15346010

[/B][/COLOR]Really would be glad if someone could help me out! :confused:

---

### Post by oldfred on 2016-03-11
Usually these two entries are similar, as difference is which path and file to boot.
 ```
Boot0013* ubuntu	HD(1,800,100000,85d436f0-93e4-4c71-863a-1cd4aa37be12)File(EFIubuntushimx64.efi)
Boot0014  Windows Boot Manager	HD(2,96800,32000,93e1148e-1138-4c10-a463-90fc9e068070)File(EFIMicrosoftBootbootmgfw.efi)
```
Also * should mean active.
Boot-Repair copied shimx64.efi to the fallback, or hard drive boot of /EFI/Boot/Bootx64.efi. Some UEFI auto add that entry. 
If not you may need to add an entry:
sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  
OR in your case where drive is sda and ESP partition is sda2 or 2:
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is ESP - efi system partition

Then see if UEFI hard drive boot entry works.

---

### Post by greentea2 on 2016-03-13
Hi @oldfred, 

Finally I found the solution. I've just enabled Secure Boot and it worked !!! 
According to the tutorial [on this link]("https://stephen.rees-carter.net/geek/thinkpad-t440s-ubuntu") 

Probably it will affect most **Dual Boot** of the **ThinkPad T series - **so would be good to keep it in mind for the Ubuntu-team.

---

### Post by oldfred on 2016-03-13
That is different. 
Normally most have to turn secure boot off?

---

