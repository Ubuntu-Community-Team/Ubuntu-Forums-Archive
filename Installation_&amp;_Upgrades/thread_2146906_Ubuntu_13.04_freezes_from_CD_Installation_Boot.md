---
title: "Ubuntu 13.04 freezes from CD Installation Boot"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by AfrikaDietmar on 2013-05-20
Hello,

i have been having troubles with 12.04 which didn't work out. Am still running on 10.04 which works fine with my PC specs below. 13.04 installed well on a numerous PCs but on my more powerful PC mentioned below it just won't let itself even boot/install from CD.
I have tried a weaker graphic card, pressed F6 and set a "X" on noapic, nolapic, nomodeset, or just on nomodeset and also edited the line and added vga=771. Still it will just come to the blinking cursor and freeze there. I have also set SATA in Bios on AHCI, IDE or Disabled. That didn't help either. If 10.04 managed to be installed, it should be possible with 13.04 right ? Is there anything else you can suggest to make it work ?

PC Configuration:
[COLOR=#000000]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333, 500 GB Hard Drive SATA[/COLOR]
[COLOR=#000000]Power: Cooler Master 625W Extreme2[/COLOR]
[COLOR=#000000]Graphic Card: ASUS GT620 (Connected 2x 24" LED LCD Viewsonics, one on HDMI one on the blue connector)


[/COLOR]

---

### Post by fantab on 2013-05-20
I am sure you are selecting from your BIOS to boot from LiveCD after inserting the CD. Otherwise it sounds like a bad burn. I suggest you do a[ MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on your downloaded .iso, if the sums don't match then re-download the ISO image and burn it again, and try to burn it at lower speed than the maximum offered by your Burner.

---

### Post by AfrikaDietmar on 2013-05-20
> [COLOR=#000000]Asus m4a87td core unlocker feature on usb3 was causing the problem[/COLOR]
[COLOR=#000000]Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! [/COLOR]
[COLOR=#000000]In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.[/COLOR]
[COLOR=#000000]Changed IDE Mode to AHCI Mode[/COLOR]

There is no Sercurity > I/O Access on my mainboard in BIOS settings ([COLOR=#000000]ASUS P8H61-PRO (Intel H61 Chipset))[/COLOR] so couldn't try that nor a possibility to set anything on locked.


[HR][/HR][COLOR=#000000]PC Configuration:[/COLOR]
[COLOR=#000000][COLOR=#000000]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333, 500 GB Hard Drive SATA[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Power: Cooler Master 625W Extreme2[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Graphic Card: ASUS GT620 (Connected 2x 24" LED LCD Viewsonics, one on HDMI one on the blue connector)[/COLOR][/COLOR]

---

### Post by AfrikaDietmar on 2013-05-20
> [COLOR=#000000]I am sure you are selecting from your BIOS to boot from LiveCD after inserting the CD. Otherwise it sounds like a bad burn. I suggest you do a[/COLOR][ MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM")[COLOR=#000000] on your downloaded .iso, if the sums don't match then re-download the ISO image and burn it again, and try to burn it at lower speed than the maximum offered by your Burner.[/COLOR]

Same CD worked on several PCs. I can't be the CD. I also have an original 12.04 CD from England that i ordered and same issue with that CD to. It's definitely not the CD. Did some of those checks before, no errors there. So its not the CD. :(

---

### Post by fantab on 2013-05-20
Can you confirm that your CD Drive is working fine? Try Burning the .iso to USB pendrive, you can use 'Unetbootin' to do so.

---

### Post by AfrikaDietmar on 2013-05-22
Its for sure working fine as I installed Ubuntu 10.04 from it.

> [COLOR=#000000]Try Burning the .iso to USB pendrive, you can use 'Unetbootin' to do so.[/COLOR]
Just did that. It's the same. Freezes when it needs to load the Kernel I suppose.
It gets till the Grub part, then there it freezes.

Gee I really don't know what to do now. Been trying to much... Looks like Ubuntu 12.04, 13.04 don't like Asus mainboards!?

---

### Post by fantab on 2013-05-22
Are you dual-booting with Windows. Is there a Windows8 in the picture.

you can boot 10.04 from LiveCD then post the output of: 
```
sudo parted -l
```

---

### Post by AfrikaDietmar on 2013-05-23
Hi fantab!

no windows on this machine, only ubuntu 10.04 
I use it to work as well and am logged in right now, this is the result I get in terminal with command:

> [COLOR=#000000][FONT=Ubuntu Mono]sudo parted -l[/FONT][/COLOR]

ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  25.0GB  25.0GB  primary   ext4            boot
 2      25.0GB  500GB   475GB   extended
 5      25.0GB  41.0GB  16.0GB  logical   linux-swap(v1)
 6      41.0GB  500GB   459GB   logical   ext4


Does it help to advise me or you really need to have it from the LiveCD ?

---

### Post by fantab on 2013-05-23
Your partitions look fine, as far as I can tell. Your situation beats me and reminds me of a similar situation where 11.04 would not install on my machine. Every Ubuntu edition before that worked and every edition since have worked but not 11.04 Natty. 

Try Ubuntu [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

OR you can install 12.10, and then, perhaps you can upgrade from 12.10 to 13.04. Don't tweak 12.10 in anyway, keep everything default. Update it to the latest and run Upgrade.

Good luck...

---

### Post by AfrikaDietmar on 2013-05-24
It's kind of dissapointing that nearly on all my new PCs there is so much trouble getting 13.04 to work. I will try your suggested solution. A lot is just hardware related. Is there a list where you can check with which hardware components ubuntu works best ? For example MSI Mainboards instead of ASUS and which graphic cards it prefers. I would then buy hardware in this way...

---

### Post by fantab on 2013-05-24
> **AfrikaDietmar said:**
> It's kind of dissapointing that nearly on all my new PCs there is so much trouble getting 13.04 to work. I will try your suggested solution. A lot is just hardware related. Is there a list where you can check with which hardware components ubuntu works best ? For example MSI Mainboards instead of ASUS and which graphic cards it prefers. I would then buy hardware in this way...

You can check this out: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/) (It is not a comprehensive list but can offer help).

---

### Post by AfrikaDietmar on 2014-04-22
I just tried the Ubuntu 14.04 Minimal CD, i did get a little further this time on the same PC but at the point "Detecting disks and other hardware" there it just hangs/freezes and stops.
Any ideas what I can do? At least with the minimal CD i get a few more options running than with the normal installation CD.
 
Since Ubuntu 10.10 is working fine and was able to install is there no way to get 14.04 working!?

Same PC Configuration as beginning of this thread:
[COLOR=#000000][COLOR=#000000]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333, 500 GB Hard Drive SATA[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Power: Cooler Master 625W Extreme2[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Graphic Card: ASUS GT620 (Connected 2x 24" LED LCD Viewsonics, one on HDMI one on the blue connector)

Seems like I'm not the only one with this issue > [/COLOR][/COLOR][http://superuser.com/questions/324921/cant-install-ubuntu-64-bit-on-my-asus-destop](http://superuser.com/questions/324921/cant-install-ubuntu-64-bit-on-my-asus-destop)

---

### Post by Ingotian on 2014-04-22
This probably isn't going to help but the safest thing is to buy a machine with Ubuntu pre-installed. I did this with a Dell XPS 13.3. Expensive but a very nice computer and it is guaranteed to work. I also feel that since DELL has made the effort to support Ubuntu I should make the effort to support them. I have recently installed 14.04 on an Asus VivoBook S200E-CT216H 11.6-inch LED Notebook (Intel Core i3-2365M 1.40GHz Processor,4GB DDR3 RAM, 500GB HDD, Touchscreen, HD 3000, USB 3.0, HDMI, HD Web Camera, Windows 8). This appears to work directly, touch screen and everything out of the box. Just over £300 for a refurbished one in new condition on Amazon. Not as nice as the XPS but about a third of the cost!

Usually I try some searches with the machine name and Ubuntu to see if it pulls up any known problems or better a "definitely works" or "works but you need to tweak the sound" or something. The real pains are the ones that blank the screen because then you can't easily fix anything :-(.  What we probably need is a better selection of low to hi-spec machines we know definitely work. Being able to buy any laptop without Windows on it would also be better. Why can't we just choose and install our favourite OS from the internet?

---

### Post by AfrikaDietmar on 2014-04-23
That will be one of the steps to consider when acquiring new devices but usually I just put the parts together myself.

Ubuntu 10.10 is working on my system. The newer ones aren't. I cannot explain why!? Shouldn't the newer OS versions be able to cope :confused:

---

### Post by jan22 on 2014-05-21
I've the same problem here, also an Asus Board. Ubuntu boots to the screen with the dots and then freezes. I also tried nomodeset, xforcevega etc. but it didn't help.

---

### Post by AfrikaDietmar on 2014-05-22
Hi jan22,

welcome to the club of that Asus Mainboard with the unfortunate position of not being able to run those latest awesome Ubuntu versions. I think we are doomed! Am thinking of turning that PC into a simple Windows Game Machine :/ Right now the only OS I have on it running is Ubuntu 10.04. BUT unfortunately more and more progams are not supported. Yesterday I killed Chrome and can't install the newest ones anymore :( ...so bad for the sync.
Read in here on my other thread where we chat a bit about this from a stand point of what could it be... -> [http://ubuntuforums.org/showthread.php?t=2222545](http://ubuntuforums.org/showthread.php?t=2222545)
Maybe we can get to ask Ubuntu to include the drivers required in their next update!

---

