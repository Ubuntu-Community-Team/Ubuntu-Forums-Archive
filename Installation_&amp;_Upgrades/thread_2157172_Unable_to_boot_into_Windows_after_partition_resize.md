---
title: "Unable to boot into Windows after partition resize - help!"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by photoabhi on 2013-06-24
Greetings,

This is my first time posting here so I'm sorry if i break any rules regarding the same  :)

This all began a few days ago. My dual-boot laptop with Ubuntu 12.04 and Winodws 7 was running fine, i was doing regular work on it, when i suddenly saw to my horror that i hardly had any free space on my C: drive. (p.s, i was using Windows 7.). So i decided to resize it and give it some more space. I used Easeus Partition manager, selected the C:drive and resized it to the amount i wanted(around 5GB). I was supposed to restart my laptop, and i did. And that's when it all went haywire.The laptop just refused to go to GRUB, rebooting endlessly on it's own. I was in a dilemma; this had not happened before! So i used Linux Mint to recover GRUB with Boot-repair. Well, it worked, but only to an extent. I could only boot into my Ubuntu installation. The windows boot option was not even visible. I could only boot into Ubuntu. I tried using Boot-repair again, purging GRUB and re-installing it, but nothing worked,which has led me to ask for help here. Could anyone tell me what is going on, and whether it can be fixed?   :(

Regards,

Photo-abhi.

---

### Post by photoabhi on 2013-06-24
Oh, and here's the boot-summary made by Boot-repair for reference - 

[http://paste.ubuntu.com/5795899/](http://paste.ubuntu.com/5795899/)

---

### Post by oldfred on 2013-06-24
After any resize of a NTFS partition, Windows has to run chkdsk. NTFS partitions have internal data on partition size that must match partition table. Chkdsk fixes that. But you can only run chkdsk from Windows.
Generally best to change Windows size from inside Windows using its Disk tools. I thought Easeus was one of the better tools for Windows. 

You need to use a Windows repairCD or flash drive to run chkdsk. It cannot be run from Linux.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Some have reported that Hiren's boot CD can run chkdsk.
Some have also said f8 works to get to Windows repair console. But the time from grub to Windows is very short compared to time from Windows in MBR to boot. So you have to be quick. They reported they had to try several times and it still may not work.

---

### Post by photoabhi on 2013-06-25
Thanks! Unfortunately, both the links regarding system recovery require that i log into Windows, but i cannot use Winodws as of now! I'l try the F8 option and let you know...

---

### Post by photoabhi on 2013-06-25
The F8 option does not work either. And i don't have a copy of Windows either! I'm in a real fix now! what other options do i have? (if i need to remove Windows, so be it! :D ) 

Thanks a lot, anyways!  :)

---

### Post by oldfred on 2013-06-25
If you know someone, friend from work or school with the same 32 bit or 64 bit Windows (any version) you can make the repair disks.

You can also purchase them, they used to be free but now are expensive.
       
 Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

    EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

 Also has chkdsk and some other Windows repairs in free version:
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

     May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

More info from those who know Windows.
[       ]("http://neosmart.net/blog/") [http://www.sevenforums.com/](http://www.sevenforums.com/)
    [ ]("http://neosmart.net/blog/")

---

### Post by photoabhi on 2013-06-26
Unfortunately, i don't  :(  anyways, thanks a lot! i think I'l just delete Windows and use Ubuntu for now. Or maybe format the whole drive and install Linux Mint.. :)

---

