---
title: "Trouble Booting After Edgy Install"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by Viper_Maniac on 2007-03-21
Ok. I figured I would go ahead and install Edgy on my computer after getting everything in XP sorted out on my new hardware. I had to use the safe graphics mode to boot up the live cd because the regular mode wouldn't show anything on the screen. I hate having to boot up just to install the damn OS. Takes forever to boot up to where I can do something. Kinda annoying. Sorry about that. Anyways I install it onto about a 50GB free space on my main drive. It installs and it tells me to restart now or continue using the live cd. I restart and it gets to the point where it asks me to remove the disk and press enter. I remove the disk and press enter but nothing. It locked up right there. I pressed enter many times and tried to move the mouse because there was still a mouse pointer on the screen and still nothing. I figure it must be ok to just hit the reset button. It boots up past the POST and then stops with an error "Error booting Operating System" or something similar to that. I'm posting from the live cd as its the only way to post this right now. Help would be greatly appreciated. 

My hardware is: Athlon64 3500, 512MB Dual Channel PC3200, ASUS A8N-SLI Premium, Geforce 7600GT, Western Digital 250GB SATA(Main), Western Digital 80GB IDE(Sec.)

---

### Post by ssican on 2007-03-21
There is a case similar. See is Thread: [http://www.ubuntuforums.org/showthread.php?t=389243&highlight=how+to+install+grub](http://www.ubuntuforums.org/showthread.php?t=389243&highlight=how+to+install+grub)   In this thread trere is 1 HD SATA and 1 HD IDE , and was used Ubuntu Live CD.  For INSTALL GRUB was used the method that is on post 5 in this thread: [http://www.ubuntuforums.org/showpost.php?p=2328754&postcount=5](http://www.ubuntuforums.org/showpost.php?p=2328754&postcount=5)

---

### Post by Viper_Maniac on 2007-03-21
Well that fixed Grub and I got the menu but then I get new errors. No matter what I pick I get some sort of an error. If I pick Ubuntu it gives me this error: "Error 22: No Such Partition". If I pick Windows it gives me this error: "Error 12: Invalid device requested". Ideas?

---

### Post by Viper_Maniac on 2007-03-21
Well I reinstalled Edgy and restarted after it was finished. Then after POST it stops with a message of "Invalid boot device" or something similar to that. I swore. ;) Then I put the disk back in to boot up to the live cd. Once I got to the menu where it asks if you want to run a memtest or start/install Ubuntu, I picked the option of Boot from first drive. Then I get the Grub menu. I pick the first one(Linux) and it starts up Ubuntu(Not the cd one). I'm now in it(the one installed on the drive) but I know what happened. Windows and Linux are both installed on the SATA but the installer must have installed Grub on my IDE drive because for some reason it thinks thats the first drive(primary) when it isn't. I just have that drive for storage of music, vids, and other stuff.

Now my question is how do I find out which drive it really is installed on and get it sorted out the way it should be?

---

### Post by bulldog on 2007-03-21
> **Viper_Maniac said:**
> Well I reinstalled Edgy and restarted after it was finished. Then after POST it stops with a message of "Invalid boot device" or something similar to that. I swore. ;) Then I put the disk back in to boot up to the live cd. Once I got to the menu where it asks if you want to run a memtest or start/install Ubuntu, I picked the option of Boot from first drive. Then I get the Grub menu. I pick the first one(Linux) and it starts up Ubuntu(Not the cd one). I'm now in it(the one installed on the drive) but I know what happened. Windows and Linux are both installed on the SATA but the installer must have installed Grub on my IDE drive because for some reason it thinks thats the first drive(primary) when it isn't. I just have that drive for storage of music, vids, and other stuff.

Now my question is how do I find out which drive it really is installed on and get it sorted out the way it should be?

You can find out how ubuntu sees your disks ```
cat /boot/grub/device.map
```
But it's really simple.
IDE goes before Sata so your IDE disk is (hd0) and the Sata is (hd1) now it's a normal behavior that ubuntu install GRUB on (hd0) unless you have the alternate cd,that gives you an option to install Grub on another hdd.
Even if your Sata disk is set as first boot device,it will install Grub on the IDE disk.

---

### Post by Viper_Maniac on 2007-03-21
Thanks for your response. It does see the IDE as hd0 and the SATA as hd1. How do I remove grub from the IDE and install in onto the SATA so I can boot normally without the cd(not alternative)?

---

### Post by bulldog on 2007-03-21
> **Viper_Maniac said:**
> Thanks for your response. It does see the IDE as hd0 and the SATA as hd1. How do I remove grub from the IDE and install in onto the SATA so I can boot normally without the cd(not alternative)?

The simplest way is to set the IDE disk as master boot device.
The hard way is to reinstall GRUB with the live cd,and recover your windows MBR with the windows install cd.
To reinstall GRUB with the live cd onto the Sata disk will disable the windows boot in your menu.lst.
You have to map your hdd's to boot into windows.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Make your windows entry looking like this and you'll be able to boot windows from the GRUB menu
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1

```

Use the setup command for the disk which will be given with the find command!!

---

### Post by Viper_Maniac on 2007-03-21
I replaced the MBR on the IDE drive which allowed me to boot up normally but only directly into Windows. I tried redoing the grub from the live cd to put it on the SATA but didn't work. Still booted up right in Windows. So I figured I'd try and reinstall Ubuntu but this time right before it started to install, it shows that screen that tells you what its going to do. It showed that Grub would be installed to (hd0). I changed it to (hd1) in the hopes that it would install it on the SATA. It installed and restarted. Then it presented me with the Grub menu. I was starting to feel alittle excited until I picked something. Anything I picked related to Linux came back with that Error 22 message and if I tried Windows it said "Starting Up" but would go no farther. I swear I've never had so much damn trouble with Linux up til now.

---

### Post by Viper_Maniac on 2007-03-22
I figured it out. I just needed to disconnect the IDE drive and have the SATA drive be the  only HDD connected. Thats the same way I used to install XP because I was having almost the same problems when trying to install it last week. Then I proceeded to install Edgy. The installation encountered no problems. Everything seems to be working just fine. I just hope no problems will arise when I go to hook up the IDE drive. ;) Thanks much for the help ssican and bulldog. :)

---

