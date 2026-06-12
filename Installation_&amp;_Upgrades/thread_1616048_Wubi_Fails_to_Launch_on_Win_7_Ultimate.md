---
title: "Wubi Fails to Launch on Win 7 Ultimate"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by DonLand on 2010-11-07
I have downloaded wubi.exe to my hard drive. After double clicking the exe and OKing the security dialog, I get a error message box titled: "pyrun.exe - No Disk"
 
The error message reads:
"There is no disk in the drive. Please insert a disk into the drive \Device\Harddisk3\DR5.
 
There are three buttons: Cancel, Try Again, Continue
 
Clicking any of these buttons simply causes the same message box to pop up over and over. I cannot cancel this message or the process unless I reboot my computer. I guess the latest version of Wubi does not run on Windows 7 Ultimate.
 
My computer:
Intel Pentium I7
6GB RAM
1TB Hard Disk
 
Any ideas on how to get around this problem?
 
Thanks,
 
Donald

---

### Post by garvinrick4 on 2010-11-07
Insert disk and tray and choose wub.exe and double click answer few questions and install.
No downloading involved if you have install disk. If not download a ubuntu .iso file and burn disk. Nice to have around it being a Live Cd.
 I guess you could download wubi straight into HDD from Ubuntu, sure would be time consuming I imagine.

---

### Post by bcbc on 2010-11-07
> **DonLand said:**
> I have downloaded wubi.exe to my hard drive. After double clicking the exe and OKing the security dialog, I get a error message box titled: "pyrun.exe - No Disk"
 
The error message reads:
"There is no disk in the drive. Please insert a disk into the drive \Device\Harddisk3\DR5.
 
There are three buttons: Cancel, Try Again, Continue
 
Clicking any of these buttons simply causes the same message box to pop up over and over. I cannot cancel this message or the process unless I reboot my computer. I guess the latest version of Wubi does not run on Windows 7 Ultimate.
 
My computer:
Intel Pentium I7
6GB RAM
1TB Hard Disk
 
Any ideas on how to get around this problem?
 
Thanks,
 
Donald

this problem is caused by having peripheral devices plugged in such as a multimedia card reader/phone/etc. It's not an infinite loop but apparently the wubi code iterates through the drives a lot so it appears that way - clicking continue will eventually work. Best to just unplug everything you don't need before running wubi.

---

### Post by DonLand on 2010-11-11
Thanks.  I simply burned a CD and installed Ubuntu on another computer I had sitting around.  It too was a Win 7 CPU but I shrank the main partition by 70GB and installed Ubuntu in the new partition.  If I decide to install on the original machine, I'll try removing my iPhone as you suggested.

BTW, I wasn't able to get the Ubuntu to install on my second machine on the first pass.  Ubuntu's setup found the raw partition that I allocated but was not able to create a swap partition.  Once that failed I had to go back into Win 7 and carve a third small partition out of the raw partition I created earlier.  Ubuntu's setup still failed.

So I launched Ubuntu to run straight from the CD.  Once there, I was able to go into System-Administration-Disk Utility and format the now 60GB partition as Ext4 and the third 1-GB partition as swap space.  Upon reboot I was able to run the setup utility and install Ubuntu (where I am writing this note from now) :-)

Thanks again for your help.

Donald

---

### Post by DonLand on 2010-11-11
See my response below for what I ended up doing.  Thanks for your reply.

Best, Donald

---

