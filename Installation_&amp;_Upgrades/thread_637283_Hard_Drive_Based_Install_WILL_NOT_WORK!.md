---
title: "Hard Drive Based Install WILL NOT WORK!"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by MerlinX420 on 2007-12-10
I have an old sony laptop that I'm trying to put ubuntu on. The CD-ROM is defective. I can't boot from USB. It doesn't have a on board wired network card. I was able to get windows xp on it after retry to copy files over and over again untill it read them. I then proceeded with this install method posted at :[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I used the CD image method described here.

The CD image approach

Note: This method only works with the Alternate Ubuntu install CD.

If for some reason you can not (do not want to) write the CD it is possible to use the ISO image to do the installation form hard disk.

    *

      Create a directory called hd-media in the root directory of the first primary partition of your hard drive (usually drive c:\, which it will be referred to as from now on).
    *

      Download vmlinuz and initrd.gz from [WWW] [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/) and save them to hd-media
    *

      Download the ALTERNATE ubuntu-installer CD from [WWW] [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) and save the .iso file in the root directory of first partition of your hard drive.
    *

      Download Grub For Dos from [WWW] [http://sarovar.org/download.php/1138/grub_for_dos-0.4.2.zip](http://sarovar.org/download.php/1138/grub_for_dos-0.4.2.zip)
    *

      Extract grldr from the archive to c:\grldr. The rest of the files in the archive are unnecessary.
    *

      Append c:\grldr="Install Ubuntu" to c:\boot.ini.

To view and edit the Boot.ini file on WindowsXP:
1. Right-click on My Computer, and then click Properties.
2. On the Advanced tab, click Settings under Startup and Recovery.
3. Under System Startup, click Edit.

Note: Eventhough c:\boot.ini is not shown by the explorer, this file exists and can be also opened in the notepad. Just write the path c:\Boot.ini at the open dialog.

    *

      Create a new text file called menu.lst and save it to the first primary partition of your hard drive.
    *

      Open menu.lst in a text editor and paste the following text in the file:

      title Install Ubuntu
      kernel   (hd0,0)/hd-media/vmlinuz root=/dev/ram0 ramdisk_size=128000
      initrd   (hd0,0)/hd-media/initrd.gz

    *

      Save menu.lst, reboot, select "Install Ubuntu" twice. You now have a CD image installation of Ubuntu going.



     I am able to get the text based install to run.    HOWEVER!!!

 When I partition the disk I get an error    "the ext3 file system creation in partion #1 of SCSI1 (0,0,0) (sda) failed."

Now I'm sitting here in a contunioues loop. It just willn't create the partion. I don't understand. Is it becuse the install is running from that postion and it willn't overwrite it's self? I really don't see why this dosn't work. Has any1 else tried this install meathod? I'm so pissed off right now I'm cussing a blue streak. It's taken me a whole day to get winxp on this system just so I can install ubuntu.  Why is this install meathod posted if it dosn't work!!!  I can't stand to run windows anymore. (I switched back in 7.04 and have to say I'm very pleased with the OS except the current release.)  Am I just wasteing my time with this install meathod? It's not like I can just go buy a laptop CD-ROM from the store so I need to know if this even worked for anyone else.

Thanks,

Merlin X.420

---

### Post by logos34 on 2007-12-10
That's a tried and true howto--a lot of people have used it successfully.  I've used it myself, but on new hardware.  

I feel your pain...But could you provide some more info, like did you use the guided or manual partitioning? How much space did you allocate for root?  etc.  Hardware specs too (Hdd size?),

---

### Post by MerlinX420 on 2007-12-10
I used the guided method. It's a P3 450 with 128 mb ram and a 4.6 gb hd. I'm not sure how to set up manual partions. (I did it once back in the day with slackware 3.3)  So this how-to is tried and tested?? I've re attempted it and still get the same error.

I've now tried it AGAIN and this time it can't find the menu.lst file. it must be lost. winxp setup re-started. the hd was in 2 parts when I looked. I'm getting ready to try this again then. I still don't see how this could work. THE ISO is on a win part. that needs to be destred yet still read the iso??? I don't understand how it COULD work. Is it the computer or PEBKAC? Thanks for any help you can give me.

---

### Post by logos34 on 2007-12-11
> **MerlinX420 said:**
> ...4.6 gb hd. 


You're at the low end of the [system requirement]("https://help.ubuntu.com/community/Installation/SystemRequirements")s, especially that drive...windows base install normally uses ~2 gb or so, if memory serves me correctly, that doesn't leave much--perhaps the installer is having trouble getting all the files in such a tight space.  You might also check the bios hard disk settings, try different ones (auto, user, chs, etc.) 

My advice to you would be to download the [Xubuntu alternate install cd]("http://www.xubuntu.org/get")...it's smaller and lighter and hopefully will install without a hassle.  It's more suited to older hardware/low end specs.

ADD: just saw your edit after I posted

---

### Post by logos34 on 2007-12-11
> **MerlinX420 said:**
> I've now tried it AGAIN and this time it can't find the menu.lst file. it must be lost. winxp setup re-started. the hd was in 2 parts when I looked. I'm getting ready to try this again then. I still don't see how this could work. THE ISO is on a win part. that needs to be destred yet still read the iso??? I don't understand how it COULD work. Is it the computer or PEBKAC? Thanks for any help you can give me.

this supports my initial assumption, there's just not enough disk space left to install ubuntu.  It won't delete the windows part because obviously that's where the installer/iso is running--the partition is mounted.  You do that later.  Not sure what the deal is with it not finding the menu.lst.  

Again, you really should forget ubuntu and get Xubuntu.  Take a break and try it again in a day or so.

---

### Post by MerlinX420 on 2007-12-11
My desktop is also a p3 450 but with 256 MB of ram and 13.4 GB HD.  I was actually able to do a live CD install.  I'm downloading the xubuntu alt install ISO now. It's 688 MB. It's not MUCH smaller then the Ubuntu install.  I have to re-install win xp and then attempt it again. (This faultily CD-ROM is SLOW!) How can the ISO stay intact when the partition it's on needs to be destroyed and made into an ext3 file system? 
How can it keep the ISO when the drive is one whole partition? Could I split off the drive and keep a 700 MB or so part that would allow me to use the rest of the drive without affecting the ISO?
I don't have to wait. I'm laid off from work broke and have nothing better to do then TRY, TRY, Again!!!! Jezzz the D/L stalled!! I don't know if I can get the file! Thanks thou.
I guess I'll HAVE to breakdown and BUY a cd-rom drive for this thing.

---

### Post by techgeek40 on 2007-12-11
I have three hard drives (dev listed below)
Partition the drives just fine - no problems
When I install Ubuntu I see the sda1 (which is my Vista) sda2 (which is my XP)
I then use Ubuntu's partition on the "third" partition to make a swap file - that goes fine.
Then I use the remaining partition (listed as free in Ubuntu) to install the O/S

It goes through the install fine - IF i don't change to the ReiserFS (/) and keep it as ext3

If I use the ReiserFS and on "7 of 7" use the Grub on (sda,4) that is when I get the error

BUT - if I use the ext3 (/) then I would like a way for EasyBCD to set up so I can see all three (Vista/XP/UBuntu) during boot up and select from there - 

Here is the screen I get for Step 7 of 7 
Language: English
Keyboard layout: U.S. English
Name: techgeek
Login name: techgeek
Location: America/New_York
Migration Assistant:

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
partition #3 of SCSI1 (0,0,0) (sda) as swap
partition #4 of SCSI1 (0,0,0) (sda) as ext3

That's where I am running into a problem.

Addendum:

Okay,
Here is how I have things laid out

DEVICE TYPE MOUNT POINT FORMAT? SIZE USED
/dev/hda
/dev/hda1 ntfs /media/hda1 (76720 MB) 7600 MB
/dev/hda2 ntfs /media/hda2 (5241 MB) 1100 MB
/dev/hdc
dev/hdc1 ntfs /media/hdc1 (80023 MB) UNKNOWN
/dev/sda
/dev/sda1 ntfs /media/sda1 (59290 MB) 17800 MB
/dev/sda5 ntfs /media/sda5 (24594 MB) 6000 MB
/dev/sda3 swap (1998 MB) 0 MB
/dev/sda4 ext3 / (74150 MB) 3500 MB
/dev/sdb
/dev/sdb1 ntfs /media/sdb1 (80077 MB) 24800 MB
/dev/sdb2 ntfs /media/sdb2 (79961 MB) 63500


As you can see I am using sda4 for the Ubuntu install - so my question is how do I get EasyBCD to see that and us it?

Addendum:

This is the error I get when I install

This is what I am getting when it gets to the end
Unable to install GRUB in (sda4)
Executing 'grub-install (sda4)' failed.
This is a fatal error

Now I did get a post from another forum that I should use it as (hd0,3)
But why that? I know I'm not understanding this but the hd0,3 - the 3 would be my swap file?

---

### Post by logos34 on 2007-12-11
yeah, the actual iso is not much smaller, but in the end it takes up less space on the disk...not sure exactly how much less (it's been a while since I did a test install).  At any rate, xubuntu is your best bet because you can't run ubuntu on that amount of ram even if you managed to install it (you might be able to but it would be really slow).  The guided install cleared a second space on the drive by shrinking the windows partition--that's where your root goes (it obviously can't delete the windows part because that would pull the carpet out from under it).  It's hard top say what the problem is exactly, could be any number of things, but I think it's just to tight a squeeze...think about it, the iso alone takes up 700 mb of space on the windows partition.

---

### Post by logos34 on 2007-12-11
techgeek40,

It might be best to start a new thread.

---

### Post by MerlinX420 on 2007-12-11
I guess that makes sense. I could see were the install could take less room with xubuntu then Ubuntu. So it does resize it and then attempts to use the remaining to install to. I plan on re-building this laptop. Once I get a Optical Drive that will work, another 128 mb of ram a faster CPU (P3 850-m for 17.00!), AND THEN I guess I also need a bigger HD. Thanks for the help. I was starting to think I was a dummy for not understanding it. 
It's so hard being a noob when your use to being an expert.  I'll see if it works. (If all else fails I could just re-install XP every 30 days!)
Win xp is about 2 gb + 700 mb ISO leaves about 1.9 gb left. Yhea thats to small.

---

### Post by MerlinX420 on 2007-12-11
NOPE!!!  Tried it. Same Error Message. I guess it can't be done at all.

The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.
<go back>     <continue>

Partition Overview

SCSI1 (0,0,0) (sda) - 4.9 GB ATA IBM-DBCA-204860
     #1 primary        4.6 gb b f ext3    /
     #5 logical 271.4 MB     f  swap   swap


Once again I am defeated. Yet another PAINFUL windows XP install AGAIN!!
I guess I just have to wait untill i get some better hardware/or a CD-ROM Drive that will work.
I might even look for another distro.
Thanks for your help thou. I don't think it's possiable on this machine. Shame too. I could have used this install method on many OLD machines. 

Is it possiable to do a network install with a wireless USB adaptor?

---

### Post by Rhubarb on 2007-12-11
I have had great success installing ubuntu on my old laptop server.  It has no optical disc drives, it has no floppy disc drives, it can't boot from USB, and I can't be bothered doing a network install.

So here's how I did it:
Pull the hard drive out and put it into a much more modern PC.
Install ubuntu onto it (make sure none of the modern PC's hard drives are attached).
Reboot, get the linux-generic package from synaptic (Because I noticed the latest ubuntu doesn't like old CPUs)
Edit /boot/grub/menu.lst   - make sure the generic kernel is the default one to boot.

Put the hard drive back into your old PC, and watch your old machine come alive again :)

For more details see my post number 15 here:
[http://ubuntuforums.org/showthread.php?t=635532&page=2](http://ubuntuforums.org/showthread.php?t=635532&page=2)

Please note: You may not have to get the linux-generic package (and hence edit your grub menu.lst) as it may work fine anyway.
Another note: This will work for ubuntu server and any other flavour of ubuntu.

---

### Post by logos34 on 2007-12-11
> **MerlinX420 said:**
> SCSI1 (0,0,0) (sda) - 4.9 GB ATA IBM-DBCA-204860
 **    #1 primary        4.6 gb b f ext3    /**
     #5 logical 271.4 MB     f  swap   swap

no wonder it's failing--you can't give root the whole disk yet, it's formatting the windows partition with the iso installer files!  You need to SHRINK the windows partition down as small as it will go, then use the remaining space for root and swap. But like I said there might not be enough space.  Try '**manual'** partition option and resize it down.

---

### Post by MerlinX420 on 2007-12-12
Thank you for your help. i used my sister's laptop dvd-r/rw drive to install ubuntu and I'm running it now. It's doses run quite well in fact with only 128 mb ram.  That hard drive swap would be a good idea except 2 things. I don't have the adaptor for a 2.5 44 pin IDE to 40 pin 3.5 IDE. I don't have a modern computer. (My DESKTOP is a p3 450!) The most modern computer components  I have are a 21" CRT I found in the garbage with a GF4MX AGP card.  AHHHHHH!!!! NO MORE WINDOWS!!!! Chalk up another victory for ubuntu!

---

### Post by logos34 on 2007-12-12
> **MerlinX420 said:**
> ... to install ubuntu and I'm running it now. It's doses run quite well in fact with only 128 mb ram. 

you mean Xubuntu, right?


Glad you figured out a way to get it installed.  Doing it from the cd is so much easier.

---

