---
title: "Problem Installing Ubuntu side by side with win7"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by JohnReimer on 2011-05-19
Hello,

I currently have an HP laptop dm4 1060us.  It has Windows 7 Home Premium x64 installed.

I want to install Ubuntu 11.04 side by side with Windows 7, but there is no option in the Ubuntu installation menu to do so.  I am installing Ubuntu by CD.  

I tried clicking the "Custom Option" but it wont let me format the new hard drive area that I freed up by shrinking my main C: drive down.

Here is a screenshot:

[IMG]http://img35.imageshack.us/img35/5846/20110519113525.jpg[/IMG]

The /dev/sda1 is the SYSTEM partition.
The /dev/sda2 is my C:\ drive for Windows 7.  The original size was around 480 GB.
The "unusable" device is the result of the shrinking of the /dev/sda2 device.
When I click the format box on that device, it doesn't do anything.
The /dev/sda3 device is my system recovery device.
sda4 is for HP tools

When I try to manually set up a partition in the computer management tool in windows 7, here is what shows up:

[IMG]http://gyazo.com/ab131cecb0a8d233e41af65696084765.png[/IMG]

and then I click finish...

[IMG]http://gyazo.com/e00b66c6ae8ba546a1ba3027ad99c79c.png[/IMG]

I do not want to click Yes on this box, because the last time I did it, it stopped me from doing future "System Recovery."  This was bad in the end.

Any help would be greatly appreciated.
Thanks!

---

### Post by Quackers on 2011-05-19
Welcome to UF :-)

You don't want to click on that option - definitely not.
Your problem is that you already have 4 primary partitions. This is the maximum number of primary partitions on an MBR partitioned disc.
The only way out is to delete a partition. You can do that with the Windows Disk Management console that you are already using.
Other people in your position have deleted the HP TOOLS partition. This contains some diagnostic tools, which are, I believe, available separately via the HP website.
Once that partition is deleted the install alongside option should appear in the Ubuntu installer.

---

### Post by JohnReimer on 2011-05-19
> **Quackers said:**
> Welcome to UF :-)

You don't want to click on that option - definitely not.
Your problem is that you already have 4 primary partitions. This is the maximum number of primary partitions on an MBR partitioned disc.
The only way out is to delete a partition. You can do that with the Windows Disk Management console that you are already using.
Other people in your position have deleted the HP TOOLS partition. This contains some diagnostic tools, which are, I believe, available separately via the HP website.
Once that partition is deleted the install alongside option should appear in the Ubuntu installer.

I will try that out, once I create the Recovery Disc just in case.

Thank you for your help!

---

### Post by Quackers on 2011-05-19
You're welcome.
It is wise to have a means to recover the system.
By recovery disc are you referring to the disc commonly known as a Windows repair disc ( made in Control Panel > Backup & Restore Centre) or a set of recovery dvd's used to recover your system to the state it was bought in?
Both are advisable :-)

---

### Post by JohnReimer on 2011-05-20
> **Quackers said:**
> You're welcome.
It is wise to have a means to recover the system.
By recovery disc are you referring to the disc commonly known as a Windows repair disc ( made in Control Panel > Backup & Restore Centre) or a set of recovery dvd's used to recover your system to the state it was bought in?
Both are advisable :-)

I was referring to the HP Recovery DVD's (5 Needed) by CyberLink for the Recovery.

I ended up not doing that method, but instead backing up and deleting the HP_TOOLS partition, creating a new volume using the leftover 80GB that was sitting there, and creating an extended partition with 4GB swap, 75GB Ubuntu, and 200MB HP_TOOLS (FAT32 formatted).  Turns out everything works!

---

### Post by Dutch70 on 2011-05-20
> **JohnReimer said:**
> I was referring to the HP Recovery DVD's (5 Needed) by CyberLink for the Recovery.

I ended up not doing that method, but instead backing up and deleting the HP_TOOLS partition, creating a new volume using the leftover 80GB that was sitting there, and creating an extended partition with 4GB swap, 75GB Ubuntu, and 200MB HP_TOOLS (FAT32 formatted).  Turns out everything works!

Hi and welcome to UF.

I was going to suggest you create a logical partition and put HP_TOOLS back on your hdd, but I see you did that. Nice work!

Please mark the thread solved with "Thread Tools" at the top of the page when you're satisfied. That helps people with the same problem find it easier & prevents people from continuing to try & help you when you don't need it any longer. :)

---

### Post by Cammy253 on 2011-10-20
Hello, I am having the exact same problem but I am confused on how to delete the HP tools patroon and install it on my main hdd..I would really like to still keep my HP tools but if I have to delete it to get Ubuntu installed with a dual boot them I will and I am looking for some advice exactly how I should do this...sry about this but I am a beginner and help would be greatly appreciated

---

