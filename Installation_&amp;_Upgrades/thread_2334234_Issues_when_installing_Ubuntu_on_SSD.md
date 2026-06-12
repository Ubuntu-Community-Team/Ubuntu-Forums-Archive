---
title: "Issues when installing Ubuntu on SSD"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by gia-alexa on 2016-08-17
So I'm having issues installing a clean copy of Ubuntu with a bootable USB on Asus laptop, a K50ID. I've been running Ubuntu on the included 500GB HDD for a couple of weeks now without any issues and decided I wanted to upgrade the computer to an SSD, an ADATA SP550 120GB. My issues start after I select the hard drive to install, when it tells me I've got Error 30, disk is read only. 

I've tried a couple of times without any success. I've also tried to check the hard drive on gdrive while in the Try Ubuntu mode and there are one big partition, one small on 4gb and 4gb of empty space. disk say I can't remove the small portion of 4gb of empty space because I am not the owner of the drive, and I can't change the permissions of the drive either.

I've tried to install Windows 7 with a bootable USB too and it freezes without any error messages at around 60%.

Meanwhile I've plugged in the SSD into another laptop (Asus eee 1005ha) and been able to install Ubuntu without any problems what so ever. Any ideas what the issue could be?

edit: I was able to boot up the K50ID when I moved the SSD back from the 1005ha, but since I want a 64x install I still need to resolve the issue.

---

### Post by oldfred on 2016-08-17
In BIOS do you have drive set as AHCI?
And some BIOS have settings to turn or or allow use of a drive.

Post these, change example with sdd to your drive:
 udisksctl status
Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
Use hdparm to unfreeze
[http://ubuntuforums.org/showthread.php?t=2317805](http://ubuntuforums.org/showthread.php?t=2317805)
Info on freeze
[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

---

### Post by gia-alexa on 2016-08-17
Okay, so tried the commands and I booted from a Parted Magic-usb, I did a health check on the drive without issues, and I erased the entire drive and tried to install Ubuntu again, with the same error.So I'm in BIOS right now, but I can't figure out how to set my drive as AHCI? I'm assuming it should be done in IDE Configuration?


[ATTACH=CONFIG]270721[/ATTACH][ATTACH=CONFIG]270722[/ATTACH][ATTACH=CONFIG]270723[/ATTACH][ATTACH=CONFIG]270724[/ATTACH]

Does my BIOS not allow for AHCI, and so is there anything I can do to fix this, or will I not be able to install Ubuntu to the SSD directly from the computer?

---

### Post by oldfred on 2016-08-17
Please attach screen shots, not every one has high speed Internet.
Easy to attach with paperclip icon in Forum's advanced Editor.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    
Settings look ok.
Just not sure what in your BIOS compatible vs enhanced means?

Do you have newest BIOS from vendor for your model system?

---

### Post by gia-alexa on 2016-08-17
Sorry, fixed it now.

It says compatible is for older systems like Window 2000 and XP, it was also needed when I tried to install netBSD.

---

### Post by oldfred on 2016-08-17
Glad you resolved it.

I then wonder if compatible is really the old IDE setting. 
Most newer BIOS have AHCI, IDE or RAID as alternative settings.

---

### Post by gia-alexa on 2016-08-17
Yeah I think it's the old IDE setting.

---

### Post by gia-alexa on 2016-08-17
Okay so I think I have resolved it. I removed the internal HHD/SSD all together and booted up the Ubuntu USB and plugged in the SSD as an external HDD via cables. Then installed it on the external SSD, without any problems. Then put the SSD back inside the computer and was able to boot it up. So still not sure why I couldn't install, but now it works at least!

Thanks for a good frist time experience on the forums!

---

### Post by gia-alexa on 2016-08-17
So okay, no it does still not work fine, don't have any write permissions when it's set up internally.

---

### Post by oldfred on 2016-08-17
You can add this to installer.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yancek on 2016-08-17
Write permissions to what?  On pretty much any Linux, an ordinary user will not have write access outside their /home/user directory.  You need to use  root/admin for that and that means sudo.  You can also create other partitions and other directories outside your /home/user and modify the ownership and permissions.  You would need to give more details on what exactly you are trying to do and the error(s) you are getting.

---

### Post by gia-alexa on 2016-08-17
Here is the link: [http://paste2.org/MwcEcUxy](http://paste2.org/MwcEcUxy)

---

### Post by gia-alexa on 2016-08-17
I can't write anything anywhere, the SSD is mountable externally and in other computers but I can't install Ubuntu on it when it is mounted inside computer and while I'm able to boot ubuntu up when it's been installed from another system I still can't write anything anywhere. If I try to create an empty file it says the disk is read-only. I know I don't have permissions everywhere but I can't write to my home folder, or even open any application without an error message.

---

### Post by oldfred on 2016-08-17
Install looks normal to me.

To yancek's point, what is not working?

Since you only have Ubuntu installed, it should just directly boot without grub in BIOS boot mode.

Report says Secure Boot may be on, But to boot in BIOS mode it has to be off.

---

### Post by gia-alexa on 2016-08-17
The install was able to boot but I was not able to do anything that would write on the disk. Tried to do clean install again, but still the same error messages. I took a printscreen on how it looks.
 
[ATTACH=CONFIG]270726[/ATTACH]

---

### Post by oldfred on 2016-08-17
If it worked as an external drive, then it still is some BIOS incompatibility.
I did not notice any settings in screen shots you posted, but some are often hidden in sub-menus.

Is it the newest BIOS for your computer?

---

### Post by gia-alexa on 2016-08-17
Yes, the BIOS are the latest, I can't find any menus for SATA/AHCI in the bios.

---

### Post by gia-alexa on 2016-08-17
Update: I was finally able to install Windows 10 after the same error I described in my first post, and after it was installed it worked without any issues (as it seems at least). Still not able to install Ubuntu though. I saw this on my boot up now, and if I read it right this means the computer is handling the AHCI-part right. 

[ATTACH=CONFIG]270729[/ATTACH]

So now I'm even more clueless what the error is...

---

### Post by oldfred on 2016-08-17
It does say it is an IDE device. It may say that on all devices or it may be wrong?

My newer Asus UEFI specifically says SATA and AHCI, but it will not relate to an older BIOS system. My older Gigabyte board with similar CPU also called drives IDE, but I had AHCI on.

---

### Post by gia-alexa on 2016-08-18
Okay, so now I've solved it 100% as far as I can see.

I installed Ubuntu on the SSD while it mounted externally, without any problems. Then I booted the system up while still having the SSD externally, checked that all permissions were right (they were), and downloaded gksu in case I would have to change them later. Turned off the computer, mounted it inside the laptop and booted up, no problems no far. Ubuntu is running fine, permissions seems to be working. Whatever the issue was I have seemed to been able to pass by it!

Thanks for all the help!

---

