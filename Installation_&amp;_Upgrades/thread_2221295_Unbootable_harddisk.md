---
title: "Unbootable harddisk"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by prismaled on 2014-05-01
Following the recommendation in  YannBuntu's answer on May 30th 2011 "Re: [Boot-Repair] Graphical tool to repair the PC boot in 1 clic !" I hope it´s OK to present my problem here.

Due to power failure during a system back-up, one of my older computers is now unbootable. I was mostly using the XP partition, but had also (without success!) tried different linux distros on other partitions. Now, when XP no longer is supported, my intention was to replace it with Linux on this computer.  In order to fix the boot problems I tried to install Ubuntu 32-bit 14.04 LTS, expecting that the installation would correct the start-up process. As the computer still didn´t boot I tried the Boot-Repair program, which unfortunately didn´t work.

My computer: ACER Aspire T160, Base Board ACER FC51GM, Bios Phoenix ver R02-B1, memory 1GB. Harddisk 298 GB, partitioner sda 1-6, sda5 =swap. CD-rom (sdb1).

Boot-Info: [http://paste.ubuntu.com/7346722/](http://paste.ubuntu.com/7346722/). That information is far beyond my level of knowledge so I hope someone out there would kindly tell me how to proceed. Does the file reveal signs of uncurable damage to the system?

---

### Post by Bashing-om on 2014-05-01
prismaled; Hi ! My welcome to the forum.

OK, I do not claim to be the sharpest tack in this box of tacks that is the ubuntuforums as I too have my difficulties reading the boot-repair info output.
However, this is what I see, that Windows boot code is still installed onto the MBR in sda, and it do appear to be corrupt.
ubuntu release 14.04 is installed to the sda6 partition.

I propose that grub be installed manually to the MBR, and once installed and booted to ubunu we chainload Windows onto grub.

To that end:
Boot the ubuntu 14.04 liveDVD to terminal, and to install grub to the MBR of sda, do:
Terminal commands:
```

sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot to bios setup, and reset the booting priority to boot the 1st hard drive -> boot into ubuntu !

Ok now once booted into ubuntu -> let's pick up Windows for the ubuntu boot menu:
terminal command:
```

sudo update-grub

```

Reboot again, and let's see what we have ... the option to boot ubuntu ( several entries ) as well as the option to boot Windows.

[INDENT][INDENT]looks to me like totally doable
[/INDENT][/INDENT]

---

### Post by prismaled on 2014-05-01
Hi Bashing-om, thanks for your greetings and answer!

I tried your first code without any problems:
sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

However, on starting up again I still can´t reach the harddisk, instead the next choice, the CD. Even after disabling any other start-up probilities than the first harddisk, the computer still ends up trying to boot from CD!
I will give it another try later this evening and will come back later, thanks until then!

---

### Post by Bashing-om on 2014-05-01
prismaled; Well !

To be honest, that makes no sense.
If bios could not recognize the hard drive in order to change the boot priority, then ubuntu would have screamed and hollered about trying to install grub to the MBR of the hard drive.

All I can presently suggest is to keep looking at the boot options in bios - remember that one must "save the changes to cmos" for the change to take effect.

[INDENT][INDENT]there has to be a way
[/INDENT][/INDENT]

---

### Post by prismaled on 2014-05-01
Bashing-om, could this be a bios problem? After the power failure, which caused the damage to the  harddisk, I put it into another computer with a MB I knew was OK. It was OK then, but is it still functioning? Does the paste-file tell you anything about that?

---

### Post by Bashing-om on 2014-05-01
prismaled;

From my reading and understanding of the boot-repair text file, the Windows boot code (was) installed to the MBR of sda, and to my inexperienced eye in this particular - that file (was) corrupted.
OK ya ran the code from the ubuntu liveDVD environment and that code (RE-)installed ubuntu's boot manager to that sector.

Now one MUST reset the bios' boot priority to the 1st hard drive in order to boot ubuntu ( only system known at this time - Windows to be picked up later).

Now if and I stress IF you are unable to readjust bios booting priority - you have looked and you have tried and you have "saved changes to cmos" and still can not boot to that hard disk because bios will not comply -> then try this - again try this IF you have not made extensive changes to bios  - :

A desk top machine; fairly easy, open the case and remove the battery from the mother board for 5 minutes, replace the battery. This will revert bios back to all default settings. Better yet, if this is a 4 year old or older  box, replace that battery with a new one - life expectancy of those batteries is 5 years.

A lap top; do your home work ! Some lap tops are difficult - to say the least - to open up. Same procedure applies for the desk top. But do your home work ! Some lap tops have "clips" that are easily broken and no way to get replacement clips.

[INDENT][INDENT]that is just
[INDENT][INDENT][INDENT]what I think
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by prismaled on 2014-05-02
Thankyou again, Bashing-om, you have condensed hours of search during the last weeks into understandable sentences, I really appreciate that!
After all my Internet searching I had a few days ago done just what you are proposing - I replaced the battery with a new one in my desktop to get the default bios settings back. I believe that the date of the original bios was 2006 so perhaps there are reasons for an update?!
Here is a link to a boot-repair-infofile from today ([http://paste.ubuntu.com/7377928/](http://paste.ubuntu.com/7377928/)) - theGrub2 has now been installed in the MBR of /dev/sda, as you intended. So far, so good!
The boot sector info of sda1 is the same in the 2 files, saying that 13328 sectors are missing. Is that information of importance? Something destroyed even if he disk passed the scanning of Boot-Repair?
I am considering to test the harddisk in another computer, if it boots there the problem would most likely emanate from bios .... or wouldn´t it?

---

### Post by Bashing-om on 2014-05-02
prismaled; Humm,

Mind you I am no longer Windows literate.
But, Here are my observations.
1)I appears to me that in bios Windows "fast boot" is enabled. Try and disable that function from within bios.
Reboot, soon as the bios screen clears, depress and hold the right **** key. -> what results ?

2) "sda1 has 
                       88132526 sectors, but according to the info from 
                       fdisk, it has 88145854 sectors." -> Windows partition, I would not place a whole lot of emphasis on what an ubuntu tool reports. But do take it under advisement, as soon as we can boot Windows, run a file system check with Windows check disk utility.

3) [s]In my in-experience, I had expected to see a check sum validation in those last 2 bytes of the boot code in MBR. I will see what I can do to validate my suspicion ![/s] EDIT: Your check sum is valid. 

Keeping in mind the aboves, if from within bios you can not find a means to  boot the 1st hard drive, well, ya got a Windows repair disk handy ? .. let us (re-)install Windows boot code to the MBR of sda. Boot into Windows ; disable "fast boot", run Windows check disk.

Now if all works from Windows perspective, we will again install ubuntu's boot code to the MBR.

As there is no problem with the hard disk installed to another box, we know that the problem lies in bios/boot management within the desired box.
Let's get Windows back booting, cleaned up, and then do the ubuntu thing.
---------
Off Topic:
Other things have come up that I must attend to, I will return asap.

[INDENT][INDENT][INDENT]solutions, where are you
[/INDENT][/INDENT][/INDENT]

---

### Post by prismaled on 2014-05-02
Bashing-om,
Changing "fast boot" doesn´t change anything as the start-up still stops at "Verifying DMMI poool data.......... Disk boot failure"

In bios there are 4 options: first, second and third boot device (all of them checked as 1st harddisk) and "boot from other device" which leads to the CD if enabled, to "Disk boot failure" if disabled. So if "boot from other device" is disabled no harddisk can be found on start-up.

Perhaps I have misled you to believe that the harddisk already has been checked on another computer, but that is not the case. I intend to hand it over to a friend on Monday and hope to have it back after a couple of days. 

So until then - thank you for now - I am coming back next week. I am glad that you still seems to have hope for the old machine!

---

### Post by oldfred on 2014-05-02
Boot info says Vista PBR - partition boot sector but you have XP boot files.

I once ran a Windows 7 chkdsk on my XP and it actually worked better than the XP chkdsk, but it also converted PBR to Windows 7 type.

The PBR calls out which boot loader to use ntldr for XP and bootmgr for Vista or later. So you may have wrong boot loader in Windows part 2 or PBR boot.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I restored my XP boot sector with my Windows 7 repair flash drive using bootsect.exe


 Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by prismaled on 2014-05-03
Hi oldfred, thanks for your help! 
As I  have never been in the neigborhood of Win7 or Vista the information in the boot-repair-file confused me. However, it didn´t cause much of concern - my primary goal was to get Ubuntu running. With that in order there will be another challenge diving into the Win-booting problems. My knowledge is on a much lower level, it would be overwhelming to try to attack these problems today.  
I can mention that I earlier tried the XP recovery console, if that could possibly have mixed up the PBR. For now I will test the harddisk on another computer, keeping your comments and instructions in mind.

---

### Post by Bashing-om on 2014-05-03
prismaled; Yeah .

It is your thought process we try to aid, guide and assist.

We will get ya up on ubuntu. Just a matter of isolating that bottle neck.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by prismaled on 2014-05-03
Thank you, Bashing-om, thank you for trying!  I am willing to learn - will be back after the test of the harddisk.

---

### Post by prismaled on 2014-05-07
Back again - to go on or to give up?

On testing on another machine I got this message:

Error `file/grub/i386-pc/normal/mod` not found
Entering rescue mode ....
grub rescue > -		

Then the system was locked with a blinking cursor. 
After loading the Boot-Repair program I got this infofile:
[http://paste/ubuntu.com/7408866](http://paste/ubuntu.com/7408866)
Then I tried a repair ([http://paste/ubuntu.com/7408894](http://paste/ubuntu.com/7408894)) which was successful!

On booting up this screen was displayed:

Grub v. 2.02
Ubuntu
Advanced options for Ubuntu
Memory test
Memory test
Windows 2000/Vista/XP on /dev/sda1

Launching Ubuntu first resulted in a freeze, on another try it worked. Booting into Windows couldn´t be done.

Now I put the harddisk into the other machine (with the suspected MB-fault). After changing bios to accept booting from the available options (all = harddisk), and to unable other booting devices, I am back to the original:

Verifying DMI Pool Data ....
Disk boot failure

I suppose I have to give up trying to use that machine  ..? The most probable reason for the failure is a MB-fault, isn´t it?

---

### Post by prismaled on 2014-05-07
Sorry - correction!

"After loading the Boot-Repair program I got this infofile:
[http://paste.ubuntu.com/7408866](http://paste.ubuntu.com/7408866)
Then I tried a repair ([http://paste.ubuntu.com/7408894](http://paste.ubuntu.com/7408894)) which was successful!"

---

### Post by oldfred on 2014-05-07
Glad that worked. 
Not sure what it did though.

Your Windows looks like it may need repairs. The PBR partition boot sector must have info in it that say it is the same size as what partition table sees. Report says that is not the same. Chkdsk from an XP disk should fix that.
Also boot.ini is different than what others have posted and what I have. I have not seen signature entries. They may be correct with your version, but I would also run the fix for boot.ini.

But understand XP is not supported and you should not be using it on Internet anymore.

---

### Post by prismaled on 2014-05-07
Oldfred, 
It would be fine if it was possible to wake up XP again, the main reason is to retrieve some important information. I would then delete most of the programs and keep the system as rudimentary as possible.  Some of my important files can only run in Windows, two of them must have Internet connection. Later on I hope to replace those programs with alternatives from Linux. 
So under a period of a couple of months I intend to use Ubuntu most of the time, but must have entrance to XP now and then.

But before anything else I have to examine the status of the MB, as that computer is better equipped than the one I am using now.   If it can´t be used, I have to work with this one, placing the problematic harddisk in it as a slave. 

The Chkdsk from the XP disk could not write any changes to the harddisk, when I tried it earlier, perhaps it works better in this machine. 

With both disks in place I suppose it would be possible to rescue some of the unreachable data in XP and, perhaps, make it bootable again.

Coming back when I know more ....

---

### Post by prismaled on 2014-05-26
I have to confess ... I finally gave it up! 
Bought a new computer (Win 8.1) as the old one needed too much repair. A back-up of the XP on this computer will have a partition on the Win8.1 machine and this old XP will lodge a new Ubuntu installation. This solution fits my needs best for the moment.
Thank you Bashing-om and oldfred for all your help! It should have worked if the hardware had been working correctly!

---

### Post by oldfred on 2014-05-26
New Windows 8 system will be UEFI with gpt partitioning. 
While UEFI systems have a CSM mode which boots in BIOS, your XP will not boot on a gpt drive.
If you can plug in another internal drive then you could boot XP.
Ubuntu can install to gpt drives and boot in either UEFI or BIOS boot mode. Bit more complex, because you have to change settings in Windows & UEFI before installing. How you boot installer either UEFI or CSM is then how it installs.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by prismaled on 2014-05-27
Thank you for this extremely important info! Apparently I have to plan this better! Thanks again!

---

