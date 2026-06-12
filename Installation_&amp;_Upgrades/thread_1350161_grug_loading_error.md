---
title: "grug loading error??"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2009-12-09
Ok so here's my set-up:
I have an Acer AS 1410 Aspire One netbook with the hard drive in 4 partitions: The first one is the eRecovery partition that has all the OEM Vista install files to reformat or install Vista. It was there when I bought the machine.
The rest was divided in 3 different 80 Gb partitions: B is the Ubuntu partition, C is the Vista partition and D is the win-doze 7 partition.

So far, I have been unable to delete the C (Vista) partition so I  to use PartitionMagic to shrink C (vista) from 80 Gb down to 20 Gb.

PartitionMagic prompted me to restart to execute the partition changes, so I did. The C part was shrunk down to 20 Gb but when I try to booth up all I get is this following error message:

Grub loading.
error: unknown filesystem
grub rescue>

I tried changing to booth sequence and I even reinstalled the Vista from the eRecovery partition but I still get the same error message.

I don't care if I wipe out the entire drive and install win-doze and/or Ubuntu from scratch because all my files are already backed up.

How do I get past this Grub error message and booth from any of the drives or wipe the HDD and start from scratch?


Thanx for your help, this is posted from my PDA because that's all I have right now.

Cheers,
PepeLapiu

---

### Post by PepeLapiu on 2009-12-09
And BTW, I haven't been able to get anything to booth up, none of the 3 OS's on the HDD, none of the DVD's I have and not the Ubuntu USB stick I made either.

It just keeps coming back to the same GRUB error message.

---

### Post by darkod on 2009-12-09
> **PepeLapiu said:**
> And BTW, I haven't been able to get anything to booth up, none of the 3 OS's on the HDD, none of the DVD's I have and not the Ubuntu USB stick I made either.

It just keeps coming back to the same GRUB error message.

I would make sure I can boot from the usb stick first. Probably you need to go into the netbook BIOS (you have to be fast when it's booting up and see if you needs to press F2, F10, F12 or similar). So, have the usb stick plugged in, go into BIOS and in Boot Options or what ever it's called on your netbook, set the stick before the internal hdd. Note, the stick option might be called USB HDD, on my Samsung NC10 that's how it's called for example. Yes, a stick in not usb hdd but it works with that option.
Once you can boot with the stick with Try Ubuntu option, that should give you internet access, wired or wireless, post back here how exactly you want the setup because even if you don' mind doing fresh installs of windows and ubuntu, you still have to plan so you don't need to resize partitions later. That's always a hassle and risking losing your data/OS.
You can also post a screenshot of Gparted (in System-Administration) to take a look at your drive setup, it will help you visualise it too. You can take screenshots in Applications-Accessories but set up the delay to 3 seconds for example so that the make screenshot window goes away and is not insluded in the screenshot too.
Post here from the LiveUSB. :)

---

### Post by PepeLapiu on 2009-12-09
OK, I'm on the USB Ubuntu as you suggested. And here is the GParted screen as you requested. 

[IMG]http://s189.photobucket.com/albums/z136/PepeLapiu1968/?action=view&current=Screenshot.png[/IMG]
Direct link to the picture:
[http://i189.photobucket.com/albums/z136/PepeLapiu1968/Screenshot.png](http://i189.photobucket.com/albums/z136/PepeLapiu1968/Screenshot.png)

It's really cool how Ubuntu doesn't treat me like an idiot and gives me an application that allows me to delete/shrink/expand/move partitions.

Power over stuff I own ...... how primitive in a communist world such as this one!!!

Anyway, now what I would like to do is erase the entire HDD, all partitions except the first one on the left which is the eRecovery for the OEM Vista.I hate all those bloated applications that get bundled with it from Acer but that is the ONLY legal win-doze I have so I'd like to keep it for a little while.

Once it's all erased, I'd like to reinstall the vista on a 30 Gb partition and install Ubuntu on the rest of the HDD.

Where should we start, Skipper?

---

### Post by Rohan Kapoor on 2009-12-09
Hey, first delete the partitions that you want gone. Right click and hit delete or remove partition.

Then you need to hit the apply button and then wait while it deletes the partitions. Next you should create a partition at the end of drive formatted to ext4 for ubuntu. Leave the 30gb you want free in between.

---

### Post by darkod on 2009-12-10
> **PepeLapiu said:**
> 
Anyway, now what I would like to do is erase the entire HDD, all partitions except the first one on the left which is the eRecovery for the OEM Vista.I hate all those bloated applications that get bundled with it from Acer but that is the ONLY legal win-doze I have so I'd like to keep it for a little while.

Once it's all erased, I'd like to reinstall the vista on a 30 Gb partition and install Ubuntu on the rest of the HDD.

Where should we start, Skipper?

The only problem with this plan is that usually the recovery partition restore of vista would delete the whole drive and set it up like from factory, when you bought it. In that case, any plan that you make before is useless. If you don't mind losing your ubuntu and win7 install, don't delete any of the partition from Gparted right now, no need. Start your computer from the recovery partition and do the vista recovery. I can't be 100% but I think it will delete all of this for you anyway. NOTE: it will also delete the current vista, any data you need from the hdd must be copied to external hdd, or similar.

After vista has finished its job, boot it few times to check if it's working fine. Then boot again with the usb stick as now, open Gparted and shrink the vista partition to the 30GB you want for it.
IMPORTANT: After the shrink process is done, boot vista few times because windows needs to finish disk checks after it has been resized. Boot if few times to see that it works fine after the shrink.

Post another screenshot after the restore if you're not sure and have questions. Shrinking vista to 30GB should leave the rest of the drive free for ubuntu.
Then you just boot with the stick again, this time select Install Ubuntu, and tell it to use Largest Continous Free space which would be the unallocated space created by shrinking vista.

Booting with the stick and Try Ubuntu, and opening Gparted will show you how your partitions look at any moment, if unsure about anything, check and ask questions.

---

### Post by PepeLapiu on 2009-12-12
Never mind guys, I wiped out the entire HDD and installed Ubuntu on the whole thing, destroying the Vista eRecovery partition in the process.

It's just as well, now I just forced myself to learn Linux no matter what .... F##k Bill Gates !!!

---

