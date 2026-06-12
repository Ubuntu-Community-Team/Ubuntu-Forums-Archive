---
title: "Ubuntu install saying i don't have storage"
date: 2017-03-25
forum: Installation &amp; Upgrades
---

### Post by droplo on 2017-03-25
So, I have ran into a problem with my brand new pc build. It is my first build, and also my first time using ubuntu. I burned a dvd with the ubuntu installer and booted my computer from the disk. I got into the installer where i can select live mode, install, ect ect.. When i click install it does its thing, i did notice a lot of failed outputs being sent in the command window. But when it brings up the installer window it says i must have "__" gb of disk space to install(I don't remember the exact number) and that my computer has 0.0 bytes. I have two Samsung 850 evos installed on my computer, one 120gb and the other a 500gb. They are not in raid mode and they do show up in my bios.

My system specs are:
Intel I7-7700k processor
Asrock Killer SLI/AC Z270 motherboard
MSI GTX 1070 Gaming X 8gb graphics card
NZXT Kraken x52 water cooler
16gb(8x2) Corsair Vengeance LPX DDR4 3000mhz ram
Samsung 850 EVO 120gb SSD
Samsung 850 EVO 500gb SSD
Corsair RM750x power supply
[ASUS DRW-24B1ST/BLK/B/AS Black SATA 24X DVD Burner]("https://www.newegg.com/Product/Product.aspx?Item=N82E16827135204")


I have updated my motherboard bios to the most recent version. 
I bought the SSD's used, and have honestly no idea if anything is on them or any actions he took before selling them to me.
I have the SSD's plugged into two of my SATA 6gb ports on my motherboard.

I have had a ton of issues trying to install an OS on this brand new build pc. I first tried installing windows 10 using microsoft's media creation tool and a brand new 32GB USB 3.0 flash drive i purchased from walmart. It would boot from it, bring up the windows logo and a spinning circle underneath it, and nothing else would happen. I also noticed it turned off my keyboard and mouse when the spinning circle popped up, as my RGB lights turned off on them. I then bought an OEM windows 10 installation disk and tried using that, and to no avail, the same thing happened. Windows splash screen and a spinning circle.

I then resorted to trying to install ubuntu first then going back to install windows 10 after i got my pc working. After trying to install ubuntu and it saying i have 0.0 bytes of disk space and cannot install, I have concluded that it has something to do with my SSD's.

I am unsure exactly where to go from here. I can boot into ubuntu live perfectly fine but I don't know what to do from here. 

My motherboard only supports AHCI and RAID and is currently set to AHCI. I also don't know if my SSD's are supposed to show up as a bootable device, but they don't. 

I have tried unplugging everything but the bare minimum and running from my integrated graphics with only 1 SSD plugged in, but nothing changed.

I'm very new to all of this so any solutions or fixes please be in depth on how to do them.. This is really frustrating as I've put a lot of money into this PC and really want to use it.

---

### Post by Bucky Ball on 2017-03-25
Welcome. So there is nothing you want to keep on these drives? Sounds like they already have partitions on them and perhaps no free, unallocated space to install Ubuntu to. 

Perhaps try this. Boot to a live session ('Try Ubuntu from the install media) and open Gparted. In there, you will see both disks, probably sda and sdb (use the drop down menu top right to switch). On each drive, click 'Device> Create new partition table' on the toolbar in Gparted. That will wipe all partitions and leave you with blank drives ready for partitions.

When you are looking at two drives with nothing on them, try installing again and see how you go (use the install button on the desktop).

PS: Installing Ubuntu first and Windows second is definitely the wrong way of going about this. You would save yourself some headaches if you work out how to get Windows installed first. You are going to have to do it eventually anyway, and when you do, you will probably break the Ubuntu bootloader and have to figure  that out as well.

Rule of thumb: Win first, Ubuntu second. It can be done the other way, but save yourself some time and hair pulling. ;)

---

### Post by droplo on 2017-03-25
Thanks for your reply!

I will follow your steps when i get home from work today, you are correct in assuming there is nothing I want to keep on these drives. 

As for installing Ubuntu first, I am only installing it so i can access the SSD's and fix them. Since Ubuntu has the live feature, and seems to give more feedback as to what's going wrong in its installer, I figured if i could get Ubuntu to install then Windows should be able to as well.

I'm assuming windows is seeing the 0 drive space also, which is causing it to freeze up, so if I can clear the SSD's in Ubuntu live mode and then go back and install, I'm hoping it will fix it. 

I'm not planning on keeping Ubuntu once I can get windows to install, but as i have NO operating system on the computer right now, Ubuntu seems to be the best for debugging and has a more technical community to help me through my problem. But who knows, maybe I'll like Ubuntu more and keep it anyways :)

---

### Post by Bucky Ball on 2017-03-25
You should be able to fix them without installing Ubuntu using the live session and Gparted. :) 

See how you go. The instructions I gave previously will wipe the drives clean and remove all partitions.

If you get a message that it can not create a partition table, you may need to right click and unmount any mounted partitions.

---

### Post by droplo on 2017-03-25
Thanks Bucky :)

I'll reply tonight with my results

---

### Post by droplo on 2017-03-25
Update:

I have used my installation media to boot Ubuntu live.. I have one 120 gb ssd plugged in, but it doesn't look like it is being recognized. The only device available in Gparted is sr0(my disk drive running the media). I tried switching the cables with my disk drive and ssd then rebooted and tried again but it still only shows the dvd reader. In my bios it shows a list of my 6 data ports and it says "Samsung 850 Evo 120gb" so it's clearly seeing its there. I can click on it and it brings up info on it, says it's size is 120 gb.

In my bios storage configuration I see it defaults to seeing my ssd as a hard disk drive, so I switched the type to solid state. Ubuntu isn't seeing that I have any ssd plugged in at all according to Gparted. Any ideas?

---

### Post by droplo on 2017-03-25
[http://i.imgur.com/o92wGZp.jpg](http://i.imgur.com/o92wGZp.jpg)
[http://i.imgur.com/5OZ0pgp.jpg](http://i.imgur.com/5OZ0pgp.jpg)
[http://i.imgur.com/ozwGm4n.jpg](http://i.imgur.com/ozwGm4n.jpg)

As far as I'm aware my bios is picking up my SSD just fine

---

### Post by droplo on 2017-03-25
Here's the code that shows up directly after running Ubuntu without installing
[http://i.imgur.com/kJCsfsB.jpg](http://i.imgur.com/kJCsfsB.jpg)

---

