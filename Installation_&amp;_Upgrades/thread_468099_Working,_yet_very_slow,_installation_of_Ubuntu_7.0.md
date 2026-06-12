---
title: "Working, yet very slow, installation of Ubuntu 7.04 from extracted ISO in Hard disk"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by londolozi on 2007-06-08
I finally have a working installation of Ubuntu 7.04 from an extracted ISO (standard one, not the alternative) in my hard drive FAT32 partition lettered c: (containing a windows XP). 

It booted OK (relatively fast) as a Live-Ubuntu, but when I initiated the "Install to Harddisk" process from the desktop Icon, things went very very slow, so I haven't even begun the installation process yet (it took about 10 minutes just to load the installation "window", and the system is not responsive, in other words, huge delay in mouse movement etc)

Anybody has any idea of how to fix this ? in other words, to speed things up ? Does it has anything to do with "ramdisk_size" below ? I'm a newbie in command-line Linux.

Here are the steps I used in doing it so far, summed up from two sources below:
1) "Installation/FromWindows - Community Ubuntu Documentation" at 
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")
2) "Alternative Installation Methods for Feisty - How to install Ubuntu Feisty over network or from a hard-disk. By: Mihai Marinof, Linux Editor" at 
[http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml]("http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml")

[INDENT]1. Download the ubuntu-installer CD from  [http://www.ubuntulinux.org/download/]("http://www.ubuntulinux.org/download/") and burn the CD, then copy the contents of the CD to c:/ (location of windows installation. Because file and folder names in the Ubuntu CD is different from Windows, no file or folder will be overwritten)

2. Download Grub For Dos from [http://sarovar.org/download.php/672/grub_for_dos-0.4.1pre22.tar.gz]("http://sarovar.org/download.php/672/grub_for_dos-0.4.1pre22.tar.gz") or Get the newest version from [http://sarovar.org/projects/grub4dos/]("http://sarovar.org/projects/grub4dos/")

3. Extract grldr from the archive to c:\grldr. The rest of the files in the archive are unnecessary. (If your default compression/archive program doesn't like *.gz files, try 7-Zip from [www.7-zip.org]("www.7-zip.org").)

4. Append c:\grldr="Install Ubuntu From c:\" to c:\boot.ini and change "timeout=0" to "timeout=15" (this will give you a 15 second boot-delay to choose wether to boot default windows installation or to install ubuntu).
      To view and edit the Boot.ini file on WindowsXP:
      1. Right-click on My Computer, and then click Properties.
      2. On the Advanced tab, click Settings under Startup and Recovery.
      3. Under System Startup, click Edit.

5. Create a new text file called menu.lst and save it to the first primary partition of your hard drive

6. Open menu.lst in a text editor and paste the following text in the file:
   title Install Ubuntu from c:\
   root (hd0,0)
   kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
   initrd /casper/initrd.gz

7. Save menu.lst, reboot with the Ubuntu installer CD in the drive, and select "Install Ubuntu From c:\" twice. You now have a CD installation of Ubuntu going.[/INDENT]

---

### Post by merlinus on 2007-06-08
Is there some reason why you chose to go this route rather than booting from the ubuntu live cd (or alternate desktop cd) and installing from there?

-merlin

---

### Post by londolozi on 2007-06-08
Why I had to take the road less traveled :)

1. I'm installing it on a laptop without a cd rom, without BIOS capable of booting from usb cd rom/usb flashdisk. I have a usb cd-rom drive and usb flashdisk, but I've googled everywhere and can not find a workable method to perform installation from those routes. From what I've learned, even SBM (smart boot manager) can not boot from usb cd-rom (haven't tried this option yet though). By the way, my laptop is a rather old Toshiba Dynabook SS2000 DS80P/2 with Pentium III 800Mhz, 256MB of RAM (shared 16MB of video memory on a Trydent Video Accelerator XP Ai 1), and 20GB Drive.

2. I don't have the bandwidth to download the full alternative ISO file (flat rate internet is still too costly down here, I currently use a limited 250 MB/month GPRS-on-GSM data plan). Consequently, network install is also not an option. fyi, I currently have the standard live-cd through Ubuntu ShipIt (the free delivery service from ubuntu). 

3. My laptop can boot from a usb floppy drive, but I can't get any workable solution yet to use this and my usb cd-rom to install ubuntu from the standard live-cd.

4. I don't know any other options there are.


By the way, I just tried setting the "ramdisk_size=6000000" (yes with 6 zeros) still no improvements.

Will "xforcevesa" or "Start Ubuntu in safe graphics mode" help ? (just learned about this from [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2") Gonna give it a try in a moment.

Thanks for your response.

---

### Post by merlinus on 2007-06-08
I figured there was a good reason, but had to ask.

;)

When you get it installed, I think xubuntu will be better, given your hardware.  It is very easy to install over ubuntu.  

I am using it on a 5-year-old Compaq Evo N600C with 20G hard drive, 1.06GHz Pentium III M and 256M RAM.

Good luck!

-merlin

---

### Post by londolozi on 2007-06-08
:) Thanks for the xubuntu tips, that was the origional plan after I get ubuntu on my lappie. 

Any other tips on making ubuntu or xubuntu lighter, like those tips on making WindowsXP lighter ? (stopping unnecessary services, uninstalling unnecessary apps, etc)

---

### Post by merlinus on 2007-06-08
> Any other tips on making ubuntu or xubuntu lighter, like those tips on making WindowsXP lighter ? (stopping unnecessary services, uninstalling unnecessary apps, etc)


Same same, for the most part.  

I gave 10G to win2000, 4.5 to /, 1 to swap, and the rest to /home.

So far I have not had to uninstall anything, but did kill a few unnecessary services.

-merlin

---

### Post by londolozi on 2007-06-11
I'm givin' up for the moment.The installation went unbeliavably slow, and freezed on step 3 of 7 (on starting up the partitioning).Is there a possibility to install without booting in a Live-Ubuntu mode ? i.e. installing right from boot up ? I figured, maybe it's because running the live session and the installer at once maybe a little hard for my old machine. (I once read about this possibility in "launchpad" as one of the homework needed to be done to "ubiquity", Ubuntu's current installer system)Anybodey know any workaround for this yet ?Many thanks in advance# I once installed windows xp from the command line (without the cd), and it took me one full day to finish the installation process (finished and working though, unlike ubuntu). Is this some sort of hardware limitation problem ?

---

### Post by conticreative on 2007-06-15
I have been having the same problem, with the difference that I was trying to install from the CD-ROM and not from the disk. Basically, all the problems the OP had I am having to the point where I had to stop the installation. Every mouse movement seemed to take at least 30 seconds to register, if at all and I was ultimately unable to enter the user name in screen 6.

If anyone has had similar problems and if there is a fix, please post it here. Thank you

---

### Post by jellyini on 2007-07-03
I have two laptops with different variations on the same theme: running criminally slow.  

Two HP laptops one AMD 475mHz K6-2, 256MB RAM, 6GB HDD, CD-R/DVD, and 
one Intel 500mHz Celeron, 256MB RAM, 10GB HDD, CD/DVD.  I have the Ubuntu official CDs, and several copies of the downloadable (all worthless, never could get a good burn of it. At ANY speed) I can boot and load any flavor of linux or microsoft os on either lappy.  The first time I installed Ubuntu on the Athalon laptop (by far the older crappier one), it worked better than any os I ever ran (distro: 6.06, or maybe 6.04.)  I was hooked.  But EVRY distro of Ubuntu I have tried since has driven me back to windows until i can find a fix.  Which never happens. 

The Athalon will take the LiveCD and boot it reasonably quickly, about ten minutes to boot all the way up.  The install works, but restarting results in a boot time that still hasen't gotten past the login, say about 45 mins to an hour...

The Intel will boot from the LiveCD, run a few programs very slowly, but completely stops responding whichever flavor of installer (ubiquity) I use.  Still haven't gotten a install to get to the first step with that one.

I am at wit's end with this.  I really want to support this, but I find my faith slipping.  LOL

Any help here...

Jelly

I ave the Athalon machine up nd wokin. "Iif thine devce offends thee, pluck it."  I  had the USB Belkin 54G Wireless card plugged inn.  ONCE I removed it, it ran smoothly...until  I plugged it back in.  Lag city.  Gotta be something with the network or wireless drivers.   Workin on it.

The Intel machine shoewd some performance increase when the install was tried from LiveCD w/o the Belkin wireless device plugged in.  But still hung at opening step 1 of 7; never loaded the language list.  The CD-ROM acts like it is being conflicted with.  It never really "hangs" so much as it gets so busy reading data from the CD it forgets to do anythig else, even update the time, move the mouse or display the data it's readin!!.  One other note: the CD-ROM in this is not OEM (HP Pavilion 5200 series) but from an external CD/DVD-ROM that I cannibalized because the OEM optical drive won't read the Ubuntu LiveCD.  Instead, shows an error that  says "Unable to boot from CD" and has a button reading, "Reboot".  The fdd is old and non-functioning so other alternate methods to boot using OEM CD-ROM weren't available.

---

### Post by kbman on 2007-07-19
I see this post is more than 2 weeks old, but I had the same issue, and found the post 

Issue: The install of Ubuntu is very slow.
I have an old laptop (Pentuim 3, 256mb ram, 20Gig HDD) on which I tried to install Ubuntu, and it would take 30min's before loading the first step, and each step in between would also take forever - and sometimes it would hang


I effectively used this method to install it via a HDD
[http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml](http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml)

But I changed it a bii, and this solved my issue.

On the destination PC, I created 3 partitions 
- /dev/hda1  - ext3   (type 83)
- /dev/hda2   -Swap Drive (type 82) (This is what fixed it for me - having a swap drive x2 the amount of mem you have)
- /dev/hda3   - ext3 the (Extracted intall iso )

Once this is created you need to to 

mkswap /dev/hda2
swapon /dev/hda2

You then boot up with a Grub disk, and do the root,kernel,initrd and boot steps.

When booting up, it should auto mount the swap drive, and when installing it should go much quicker.

Ciao
Gerard

---

### Post by londolozi on 2007-07-20
kbman, you're my hero !!!

I am a proud owner of a fresh ubuntu 7.04 installation now !!!

I did it without resorting to the "command line" though. 

I simply created a 512 MB "linux swap" partition (twice the size of my RAM, 256MB) from windows using partition magic 8. And redo the origional setup process I wrote at the beginning of this article, and sure enough, things went much much faster. Installation went smoothly without a hickup.

Yeehaaa !!! Now, I can get my hands dirty in the ubuntu linux laboratory.

Many thanks kbman !

---

### Post by bford16 on 2007-07-21
I can't get this to work.  I get "Error 17: file not found."  Can you help?

---

### Post by logos34 on 2007-07-22
> **bford16 said:**
> I can't get this to work.  I get "Error 17: file not found."  Can you help?

If you're trying the first method (network install), one thing you might check is that the 'linux' file you copied to C: \boot\grub does not have a .html extension.  Or if trying the second method (starting up a cdrom install) check that the paths are correct...initrd.gz and vmlinuz are located in '/casper' on the Feisty Live CD, but in '/install' on the text-mode Feisty Alternate CD

---

### Post by bitt on 2007-09-06
> I have been having the same problem, with the difference that I was trying to install from the CD-ROM and not from the disk. Basically, all the problems the OP had I am having to the point where I had to stop the installation. Every mouse movement seemed to take at least 30 seconds to register, if at all and I was ultimately unable to enter the user name in screen 6.

If anyone has had similar problems and if there is a fix, please post it here. Thank you

I had this problem, I had tried just about everything else including, irqpoll, ide_all_generic, break=top to dump to console then  'modprobe piix' and exit back to install script the list goes on.... im a complete newbie to linux but my error was OS independent.... first the original disk i burned jittered, and would hang;

**after **i had an MD5 verified iso 
**and** did the disk verification
i was able to install in under an hour instead of 6 (just to crash and fail)
selecting the safemode video option from the boot menu.


Hope this helps other new users, this was an install on an Averatec 3250hx laptop.

Edit: I have been out of the digital loop for 7 years for some things i did when i was 16, so I'm way behind the current times in technology, but if i had to venture a guess to developers i would say this is an issue with laptops that use ram as shared video memory, intuitively i would say that the driver ubuntu tried to use for video took way more than its share of the ram or all of it leaving only basic system ram allocation for the install.

---

