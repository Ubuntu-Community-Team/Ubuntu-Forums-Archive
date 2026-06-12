---
title: "Dual Boot Install&gt; XP on SATA, Ubuntu on IDE"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by BrokenDynasty on 2005-06-03
I currently have an Athlon 64 system running Windows XP from a S-ATA 160GB HD.  I have an IDE 80GB HD that I would like to install Ubuntu on.  Before I start, I want to say that I did search the forums and read some of the troubles people have had with GRUB and dual boot installations, and the howto, but I still have some questions.

I downloaded the .iso, burned it properly, ran Ubuntu live and it ran well with all my hardware as far as I could tell (took some PPPOE tweaking to get my DSL working, but only because my router isn't hooked up right now).  I tried a SuSE distro once and liked it but thought I'd give some other distros a shot (I'm a linux noob) but had a terrible time uninstalling SuSE and getting windows to boot again, so this time I want to be more careful.

**QUESTION:** What is the safest way to go about installing Ubuntu onto my secondary IDE drive?  Should the drive be set to Master or Slave?  Should I use GRUB?  Is there an option to put GRUB on the IDE drive?  Basically how should I go about keeping the two OS's as seperate as possible so if I decide to try out another distro or to scrap Ubuntu, my Windows isn't doomed?  Thanks for reading.

Edit: I am using Ubuntu 5.04 (Install/Live CD)

---

### Post by BrokenDynasty on 2005-06-04
Bump to keep on the first page.  Anyone have any advice?

---

### Post by op3studios on 2005-06-04
I'm young at this but
Since this is my exact set up, here's what worked for me:  It may not work for you, and others will know more.

Print install guide.
Install Ubuntu to the 80ide.  When you get to the partitioning display, you will see your sata, probably as scsi but the size will be right so you'll know what that one is.  You will also see your ide, probably as ide hd 0.

Anyway, select your 80, make sure never to touch your SATA in any of this.

Free and format the 80 into several partitions.
At least one FAT 32 part mounted as dos, to share files between windows and Ubuntu.  (I keep all my media files there!)
Everything else as ext3, unless you need a swap file   < 1gig ram.
There are many partitioning schemes.   Search.

There can be up to 4 primary partitions.
There can be many logical partitions created and seen within one of the primarys.

There should be 1 partition for root, Several gig for me.
The rest can be home or what ever you want via your info search.
If you have one g ram, you probably don't need a swap file.
Format everything here, install and mount your partitions, Make sure; then say go.
Don't Touch your SATA, put grub on your Ubuntu ide!  (hdd0 i think....)  make sure.

Eat chips.

Fill in the blanks.

Log in, let everything be like mist on morning lake, 
then reboot.

During reboot, hit delete and go to your bios.
Choose Boot from your choices, and go to hard drive priority or whatever yours says, make your 80 your top drive.
Make sure in Boot devices that the change has been made then save and exit .
So you switch from SATA to IDE boot in bios whenever you want to run XP or Linux.
I think this is the safest way to migrate as you can isolate and therefore prevent mbr issues with your system.
From here, as you learn, you can modify the configuration into a common dual boot or whatever.
You can spend time figuring your final setup, but this is the fastest, and you may well want to change parameters of your first setup easily by reinstalling.

So choose the ide in bios and boot...note; grub can take a long time to load.  The deadly blinking blank screen cursor is ok in Linux, just eat more chips.  Soon Grub will introduce itself and later it will give you a boot list.  On my system, XP is listed, but doesn't boot....see wiki when you want to fix this by editing your boot files.
Ubuntu is default and auto boots after boot screen timeout.
Log in and start doin stuff like surfing addons and the sort.
Anything you want from windows can be placed in your Fat32 partition from Windows, Unbuntu stuff can be written to the Fat 32 from Ubuntu.
They like each other.

Enjoy!
You can search google for anything you need, use the word Ubuntu in the search string.  the guides here are good, as well as the how to stuff.
This is the most friendly helpful forum I've seen.  

Mist rising sunlight
Sparkling comes the newday.
Ubuntu; Here  --Now.

jz

---

### Post by mingus on 2005-06-04
[QUOTE=BrokenDynasty]

**QUESTION:** What is the safest way to go about installing Ubuntu onto my secondary IDE drive?  Should the drive be set to Master or Slave?  Should I use GRUB?  Is there an option to put GRUB on the IDE drive?  Basically how should I go about keeping the two OS's as seperate as possible so if I decide to try out another distro or to scrap Ubuntu, my Windows isn't doomed?  Thanks for reading.

Edit: I am using Ubuntu 5.04 (Install/Live CD)[/QUOTE]

* Just point the installatioin to use hda.  Plan in advance your desired partitioning scheme.
* Master/Slave:  The IDE drive is on a separate controller than the SATA.  If it is the only HDD on the channel, it is a Master and should be jumped and cabled accordingly.
* Grub vs LILO is a personal choice.  Most find GRUB to be a bit more powerful and flexible than LILO.  Unless this has changed in the past year, there were commands in LILO to handle difficult drive size issues, that did not have an equivalent in GRUB.  This does not appear to be your case, so GRUB should do fine.
* I don't see any danger in Windows being "doomed."  However, setting up the dual-boot can get very mystical and if hosed, getting the boot process back right can be a royal pain (although always doable).  If you *really* want to keep the two separate and Windows "safe", then (1) setup Ubuntu to boot from the Windows loader; in this case grub needs to be installed on the whichever hda1 partition your /boot directory is located on, or (2) install grub to a floppy and boot from it whenever you want to get into Ubuntu.  This 2nd method is not flashy, but I have used it extensively because I have multiple OS's and am installing/removing distros frequently and don't want to fiddle with the MBR.

Hope this helps.

---

### Post by BrokenDynasty on 2005-06-04
Thanks for all your help thus far.  I am going to print out this thread, and the other installation guides online, and give it a shot.  I have confidence now that it wont be too daunting, and that if I majorly botch it up, that this forum will get me through it.  Thanks again.

---

