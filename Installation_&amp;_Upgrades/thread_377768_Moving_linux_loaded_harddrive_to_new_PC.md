---
title: "Moving linux loaded harddrive to new PC"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2007-03-06
Funny thing - I burned up my motherboard, video card and power supply last night. The harddrive, with my beautiful Ubuntu Fiesty setup is salvageable. (I had it checked and the data is intact)

I went to Wally Mart and bought a new HP PC - just the box - with Vista preloaded. (boy what a piece of junk Vista is ... but that's another story.)

I want to move the Linux harddrive to my new PC. There is a good bit of data there I would like to save and I want the ability to dual boot Vista and Ubuntu from the two harddrives. 

The differences between the two PCs are significant. The old one (that I burned up - shorted out) with Linux was booting an AMD XP processor with an nVidia video card. The chipset was Via on the old mobo.

The new PC has an Intel CPU 3.0 ghz and a built-in ATI video card. A different chipset as well, but I don't know how different. Audio will be different though both are built in. Ethernet is also different, though I don't know exactly how.

My plan is this: (in steps)

1) install the Linux harddrive as is to new PC on IDE1 as slave. (the CDrom may already be on IDE1 as slave in which case I will install as master on IDE2 - 

...... any comments on that part by anyone? Is there another way I have not thought of or problems I may run into?

2) setup bios to see both harddrives and the CDrom

3) boot the linux rescue disk and install Grub on the mbr and chainload Vista.

4) reboot into linux recovery mode and edit xorg.conf to remove the nVidia driver and replace with VESA (I could disable the ATI video on the new PC and install the nVidia card - )

...... comments on this? should I run reconfigure xserver-xorg and let it detect my setup instead of editing it manually?

5) reboot and pray that Grub starts and has the proper entries to dual boot to either Ubuntu or Vista.

..... anything else I can do besides pray?

Thanks in advance.

---

### Post by Herman on 2007-03-06
Hello ,
>  5) reboot and pray that Grub starts and has the proper entries to dual boot to either Ubuntu or Vista.

..... anything else I can do besides pray?
 Get yourself a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")
> 4) reboot into linux recovery mode and edit xorg.conf to remove the nVidia driver and replace with VESA (I could disable the ATI video on the new PC and install the nVidia card - )

...... comments on this? should I run reconfigure xserver-xorg and let it detect my setup instead of editing it manually?I would run             [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") but that's only my opinion. 
>  3) boot the linux rescue disk and install Grub on the mbr and chainload Vista.That would probably be okay.
There is always, [EasyBCD]("http://neosmart.net/dl.php?id=1")
>   EasyBCD is NeoSmart Technologies' multiple award-winning answer to tweaking the new Windows Vista bootloader. With EasyBCD, almost anything is possible. Setting up and configuring Windows boot entries is simple, and there is no easier way to quickly boot right into Linux, Mac OS X, or BSD straight from the Windows Vista bootloader - on the fly, no expert knowledge needed!
I have not yet read one single complaint from any Vista users running EasyBCD. That would leave your Vista MBR untouched, and you already have grub in your second hard disk's MBR. Why not give EasyBCD a try?

Regards, Herman :)

---

### Post by Psquared on 2007-03-06
EasyBCD - never heard of that one. I'll check into it.

Would you recommend that I use the nVidia card and disable the onboard ATI? For booting Ubuntu it would make it easier - OTOH, Vista is setup to play with ATI. That should be easy to fix though simply by uninstalling the ATI drivers and disabling the onboard video in the BIOS and then let Vista boot up with the nVidia card and load the drivers. I think I would do this prior to installing the linux harddrive. Seems like it would go easier on xorg if I did this. Not as much to change.

Are there kernel specific drivers for AMD vs Intel CPUs? both are 32 bit x86 so I am guessing not and Fiesty uses the generic kernel. I have not compiled anything except Picasa (uses "Wine") so the kernel is pretty much pure.

HP/Compaqs are funny. You know HP puts a lot of stuff that is proprietary on their machines and I noticed during setup that I had to do the Vista setup and then the Compaq/HP setup. (which is it anyway - it says Compaq one place and HP another?????). It also stores stuff on a separate partition "d:/" so if "c:/" gets wiped out you can do an complete reinstall without using a CD.

I just wonder if that extra partition on the primary would cause Grub, or even SuperGrub, any problems.

---

### Post by Psquared on 2007-03-06
If I use EasyBCD why do I need Grub or SuperGrub?? Don't they serve the same purpose?

---

### Post by Herman on 2007-03-07
>  Would you recommend that I use the nVidia card and disable the onboard ATI? I don't know exactly which ATI you have, but my wife and I both have Acers with ATI radeon 9200 graphics cards and we don't do anything special when we install Ubuntu in them. They get the generic ATI driver in xorg, by default, and we can change to a more specific one later if we decide to.
> Are there kernel specific drivers for AMD vs Intel CPUs? both are 32 bit x86 so I am guessing not and Fiesty uses the generic kernel. I have not compiled anything except Picasa (uses "Wine") so the kernel is pretty much pure.
We have a couple of PCs in the house with AMD processors and we just install the same ubuntu in them exactly the same as the intel ones. I'm not aware of anything special we are supposed to do. They work great!

> HP/Compaqs are funny. You know HP puts a lot of stuff that is proprietary on their machines and I noticed during setup that I had to do the Vista setup and then the Compaq/HP setup. (which is it anyway - it says Compaq one place and HP another?????). It also stores stuff on a separate partition "d:/" so if "c:/" gets wiped out you can do an complete reinstall without using a CD.

I just wonder if that extra partition on the primary would cause Grub, or even SuperGrub, any problems.
I have installed Ubuntu for freinds who have compaq presario PCs and I just installed Ubuntu in them as per normal, I can't remember having any problems.

---

### Post by Herman on 2007-03-07
> If I use EasyBCD why do I need Grub or SuperGrub?? Don't they serve the same purpose?Grub is the world's best bootloader for Linux. 
EasyBCD is an application for Windows Vista that works well with Grub. You can have Grub installed to the first sector of your Ubuntu partition or to MBR on a non-first hard disk and EasyBCD will load grub via the Vista bootloader. You still need grub to do the actual booting of Ubuntu.

If you would prefer to write grub to MBR in your first hard disk, that would be fine too. I just though I should mention EasyBCD in case you didn't know about it, but do as you prefer, use you own best judgement. I'm just making you aware of the extra choice that is available, that's all.

Super Grub Disk is a handy thing to have around in case you ever do have any booting problems. (Unlikely). You can use that in an emergency, and also it can help you do a lot of other work to do with booting and bootloaders. It's a good tool to have whatever you are doing.

Well you were asking for thoughts and comments.

Regards, Herman :)

---

### Post by Psquared on 2007-03-07
Thanks Herman. I took the cover off my shiny new HPCompaq and found that it uses a SATA harddrive. The one I salvaged from the french fried computer is EIDE. Will a sata drive coexist with an eide drive?

This sounds tricky, but I'm going to have to edit the grub menu file to point to the right partitions.  There is an eide controller on the mobo because the DVD/CD is connected to it. I may end up with the old drive as slave on the controller with the DVD drive.

Lets see ....

Drive/Controller 1 is sata so it will be sda1 & 2 in /dev right?
Drive/Controller 2 is plain old eide so it will be hda1 & 2 in /dev?? 

Grub will see them as sd0,0 and hd0,0. Am I on the right track here?

sda will only have the one drive (containing Vista) with two partitions 
hda will have hda1 and hda2 - the latter being the harddrive with Ubuntu.

Grub will install on sda1 (Vista c:/) The question is, will Grub scan both harddives, find all the partitions and setup the menu entries properly without any intervention on my part?

BTW - just food for thought. I don't know if you messed with Vista at all, but IE7 is just the slowest browser I have ever seen. I can't even believe that M$ would put out something like this. I downloaded and installed FF 2.0.2 and it runs friggin blazes around IE7. I could not even type an email in Yahoo Mail because IE was so sluggish I was typing faster than characters were put on the screen. I ended up with partial words and spaces where there were supposed to be words.

No problem in Yahoo Mail with FF at all. Just a mystery to me and shows the kind of cr@appy software M$ is putting out there. The whole system (Vista - Home Basic Version) is slower and more buggy than Ubuntu Fiesty and Fiesty is beta software. :)

---

### Post by Herman on 2007-03-09
> Grub will install on sda1 (Vista c:/) The question is, will Grub scan both harddives, find all the partitions and setup the menu entries properly without any intervention on my part? Hello Psquared, 
No, _you should not_ install grub to your Windows bootsector, which in your case will be sda1.

Instead, grub should be installed to sda, which will be the MBR in your first hard disk.

If you installed grub to sda1, you need to use some Vista program like XP's FIXBOOT in the xp [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") to repair your Windows boot sector. I don't know how they do it in Vista yet, I only know about the Windows XP method. I imagine it's probably the same or similar.

There is no guarantee that grub will get the order of your hard disks the way we would expect when IDE and SCSI disk drives are mixed. If you are lucky it will all go as normal. Be prepared to have to do a little editing in your /boot/grub/menu.lst or your /boot/grub/device.map if you need to.

Regards, Herman :)

---

### Post by Psquared on 2007-03-09
Thanks for the help Herman. I have not done this yet because Vista has crashed twice since the install. APCI is not working properly and for some reason Vista lost my CDRom. I read some reports of this and the fix was to remover upper and lower filters in a section of the Registry.

Well poo on that. I think I'll just jerk this Sata out and put my Fiesty back in by it's lonesome. Maybe I'll give the Vista drive to someone ... no ... wait, I wouldn't want to do that to ANYONE.

---

### Post by Herman on 2007-03-09
:lol: He-he-he, now you have the right idea! :)   

That will solve all your problems very easily and well.  I approve!

Regards, Herman

---

### Post by adrian15 on 2007-03-14
> **Psquared said:**
> 
Grub will see them as sd0,0 and hd0,0. Am I on the right track here?


No, that's not right all. Ask Herman if you want more details.

In my opinnion you should do a fresh install of ubuntu or whatever linux you want to the new pc. You should make a /home partition because it's the best thing and copy on it data from the other computer's /home folder.

This way Ubuntu will recognise and setup the new hardware and also configure grub. Once you will have copied into /home the old data from the old computer all your settings (documents, bookmarks, mail) will be restored.

adrian15

---

### Post by Psquared on 2007-03-15
Here's a new twist. I've got Vista running ok now - it still gives me an error that it shut down unexpectedly when I leave it running and it logs off automatically. I tried logging off before I leave it, but when I come back and logon, I still get an error saying that Windows (Vista) quit running unexpectedly. I have to reboot at that point.

So here's what I'm wondering. The harddrive with Fiesty is EIDE. If I install it as master or slave on the EIDE controller (mobo supports both SATA and PATA - or EIDE) can I use the bios boot select to choose to boot the EIDE drive with Fiesty instead of the SATA drive with Vista? If I can, will it ignore the existence of Vista on the SATA drive and go directly to the mbr of the EIDE drive and start Grub? I guess I can just try it, but I don't want either drive contaminated by the other so I'm concerned that if I use the bios setting/selector during boot to pick the EIDE that it might peek at the SATA drive and take something off there since it is primary. Likewise, if I boot the SATA/Vista drive will it peek at the EIDE on the other controller and try to take something from there?

Ultimately I'm trying to dual boot the two drives, but I think I need to get the Fiesty/EIDE drive to boot up first and then reinstall Grub to find the other drive and partitions?

Big question for me is will the boot selector during post allow me to boot the Eide drive with Fiesty and ignore the Sata drive?

Thanks,

---

### Post by Herman on 2007-03-16
You should be able to press a key during boot-up like 'F8' or 'F12' or some other key and get a menu to pick which device or disk you want to boot.
It would get tiresome if you had to boot that way every time, but it would mean that you can boot from the MBR of the non-first hard drive.
I don't believe one drive can 'contaminate' another, not without the user doing something. 

I agree with you that it would be slightly better to make the hard disk with Fiesty on it Primary Master, (hd0). Then you can just add a Windows boot entry with a pair of  'map' commands to boot your Vista, or, you could just chainload your other hard disk's MBR with Grub. Try adding a command like this to your menu.lst and see what happens,
```
title   Chainload my Second Hard Disk
root (hd1)
chainloader +1
```Regards, Herman :)

---

### Post by Psquared on 2007-03-16
> **Herman said:**
> You should be able to press a key during boot-up like 'F8' or 'F12' or some other key and get a menu to pick which device or disk you want to boot.
It would get tiresome if you had to boot that way every time, but it would mean that you can boot from the MBR of the non-first hard drive.
I don't believe one drive can 'contaminate' another, not without the user doing something. 

I agree with you that it would be slightly better to make the hard disk with Fiesty on it Primary Master, (hd0). Then you can just add a Windows boot entry with a pair of  'map' commands to boot your Vista, or, you could just chainload your other hard disk's MBR with Grub. Try adding a command like this to your menu.lst and see what happens,
```
title   Chainload my Second Hard Disk
root (hd1)
chainloader +1
```Regards, Herman :)


Thanks. I feel better about trying that now. I actually don't mind switching drives using the BIOS boot selector because I won't boot that often. I just have so much stuff on the Fiesty drive that I don't want to lose.

I'm going to give this a try tonight and see how it goes.

Thanks again for your help.

Peyre.

---

### Post by adrian15 on 2007-03-19
> **Herman said:**
> Try adding a command like this to your menu.lst and see what happens,
```
title   Chainload my Second Hard Disk
root (hd1)
chainloader +1
```Regards, Herman :)

Now Vista does not need the map commands trick to boot? :confused: 

adrian15

---

### Post by dannyboy79 on 2007-03-28
windows in general only ever needs the map commands within grub when you are trying to boot windows from a non-first hard disk. it states this within grub manual. check it out: [http://www.gnu.org/software/grub/manual/grub.html#makeactive](http://www.gnu.org/software/grub/manual/grub.html#makeactive)
it is number 13.3.23 map. So many people don't really know what they are telling people they just tell them to use the map command and they really don't need to, they only tell them that because that's "what worked" for them. People really need to learn  more about grub before just telling them to do anything. Herman is very knowledgable and I am sure he is aware of when to use the map command.

---

### Post by Herman on 2007-04-03
I'm sorry but I'm not perfect. I made a mistake this time. I thought the map commands wouldn't be needed since I was talking about booting the second hard disk's MBR, and not the bootsector of the partition. (hd1) and not (hd1,0).
I had Grub on my second hard disk's MBR, and of course, grub boots fine when I chainload the second MBR from Grub in (hd0). 

But what about when Windows is installed in MBR2? I was not sure, so I re-installed my Windows98SE bootloader to (hd1) with [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to test this.
When I boot up from the BIOS by pressing my F12 key for a list of bootable devices, Windows 98SE on hard disk 2 boots up from the second, (hd1) MBR no problem. No map commands needed.
I can also switch the [hard disk boot priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in BIOS and Windows 98SE will boot up fine from hard disk 2 's MBR.

But when I tried again with the disks boot priority back to normal and booting with grub from the first hard disk, my Windows XP boots up every time instead. That's on my frist hard disk. Why does the second hard disk's MBR boot Windows on the first hard disk? I even tried to hide it with grub's 'hide' command, but Windows Xp still kept booting instead of Windows 98SE,

Finally I used the map commands and Windows 98SE booted correctly from MBR of the second hard  disk. I don't know if Vista would be different from booting Windows98SE or not, I 'm guessing it would be the same probably, as far as the map commands go. Someday I will find out for sure when I can get a legal copy of Vista for free somehow, but I don't know when that will be.

So, I was wrong and adrian 15 is correct. 

Sorry Psquared, adrian15, dannyboy79 and  everyone, bit I did get it wrong that time. I'll try not to make any more mistakes but sooner or later I'm bound to, that's fairly certain, but I hope it won't be for a while. (Or if I do, I hope I can correct it before anyone notices) :)

Regards, Herman :)

---

### Post by dannyboy79 on 2007-04-03
don't even sweat it Herman!!! you have helped so many with grub, dual-booting w/ 1 and 2 hard drives etc etc. We are all only human, if you didn't make a mistake sooner or later I would start to wonder if you were an Alien or Siborg. ha ha
anyway, that's pretty cool that vista can boot from a NON-first disk from grub.

---

