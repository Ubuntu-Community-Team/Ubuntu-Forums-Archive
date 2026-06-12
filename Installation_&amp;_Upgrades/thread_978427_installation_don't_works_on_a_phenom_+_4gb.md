---
title: "installation don't works on a phenom + 4gb"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by mattcav on 2008-11-11
Hi here

i'm matteo from italy and i'm tryng to install ubuntu 8.10 for AMD64 on my pc.

Here machine's hardware:
- AMD - 9550 PHENOM QUAD AM2 2,2GHZ 
- ASUS - M3A 
- WEST.DIG. 640GB SATA
- 4GB (2+2) DDR2 800MHZ
- Nvidia 8400gs and a wireless pci

now. my first way to install ubuntu was install directly from live cd. 
copying files, about at 20%, the installation manager give me this error:
[B]
The following file did not match its source copy on the CD/DVD:

[namefile]
  	
This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
[/B]


ok...now some solution i've tried. nothing works:

1) test cd/dvd hardware. i've installed a copy of win xp pro. all ok, all works. windows boot and load normally.

2)burn another cd. done, don't work, same problem.

3)skip all error messages. after completing instalation, ubuntu don't boot and load, freezing the pc on system initialization

4)i've heard that ubuntu installer run some ubuntu32bit components, and this can't manage so much ram memory. ok, i've pull off a memory bank and reboot pc as 2gb ram. same problem, don't work

5)install from wubi. windows part works fine, but ubuntu installation, at copying files give same error.

6)install ubuntu from an old 8.04 hardy live cd. same error again

ok...i need an help.

i can understand where's problem: my girlfriend have the same pc (motherb,ram,hd) but different processor (amd64 5200+) and there all works fine. is the processor the problem? but i've read about many people who have a phenom 9550 and live well with ubuntu.

other solution i've NOT tried, but i think can be:

1) install ubuntu on another machine. then put hd with operative system on my machine and let ubuntu upgrade hd configuration

2)install a new processor (amd 5200+?), install ubuntu and after re put-in phenom.

can be good? other solutions? 

well, thank you in advance, and keep ubuntu great.


Matteo.

---

### Post by tommcd on 2008-11-11
I don't think the CPU is the problem. My first thought is that the install CD you burned, or your downloaded iso, are corrupted. Did you check the md5sums of the Ubuntu .iso file you downloaded? You should also burn the disc at the slowest possible speed, and check the md5sum of the disc after you burn it. See this to learn how to check the md5sum. It shows how to do it from Windows also:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)
Rule out a bad CD before proceeding further.
What program did you use to burn the CD? Two good free programs to burn a .iso from Windows are INfra Recorder and Iso Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29%7C%28burn%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29%7C%28burn%29)
Are you installing Ubuntu onto a separate partition on your hard drive, or are you installing inside Windows using Wubi?

And welcome to the Ubuntu forums!

---

### Post by mattcav on 2008-11-11
thanks a lot tom, but i've burned 2 cds from 2 different .iso on my mac with roxio toast. to build up my girlfriend's computer (amd 5200) i've used the one of this cds, and there works well.

when i've read for the first time this problem, i've make a 'check cd for defects' from livecd's panel.

no error was found on the cd...

for the installation, i've tried all possibilities: first, i've tried to install ubuntu using the entire disk. then, after win xp pro installation, i've tried to install ubuntu in a partition with guided installation. then i've tried to install form win xp with wubi. and then i've tried to install an old 8.04 livecd. 

same problem for all.

---

### Post by mattcav on 2008-11-11
nothing more? someone have a 9550 phenom able to install 8.10?

sorry for upping, but i can't understand where the problem is...

---

### Post by kebin071 on 2008-11-11
I doupt it's because you have an AMD quad, a lot of folks have been using those for a while.

I myself upgraded to 8.10 from 8.04 then downgraded back to 8.04 after an upgrade install, clean upgrade install, and clean install w/formatting of all partitions.

Like you, I'm using x64, but with an AMD dual-core 5000+, not quad.

With 8.10, I was getting two different boot errors, one of which was multiple I/O errors.

-- -

At first, I thought you problem may be with a faulty CD drive, but if you can boot from Ubuntu live CD and boot/install windows, that is not likely the case.

Personally, I would suggest downloading and installing ubuntu-8.04-x64-alternate install ISO [not the exact file name].

I'd suggest getting the 8.04 x64 alternate install to install ubuntu out of the live CD environment. I'd even get the LTS version CD [long-term support].

When ubuntu install asks about where to install, I would choose manual, and pick clean partitions that are not in use by windows.

I'd suggest using ext3 or xfs for file system, and be sure to format.

-- -

I suspect the problem may be with ubuntu 8.10. If that is not the case, it's possibly with your hardware.

If it is with your hardware, it's likely the HDD or motherboard.

Try a clean install of 8.04 x64 LTS Alternate install CD, and be SURE to check the md5sum of downloaded ISO before you burn it; at I suggest, not more than 12x speed.

Just to be sure, try testing the CD at ubuntu install boot first, just to be sure. Once you're installing, see if it produces the same error...

-- -  Additional info that could be helpful for folks to know...

It sounds like your system is home-built; correct?

Is your WD HDD SATA I or II?

This is the correct MB? [http://www.asus.com/products.aspx?l1=3&l2=149&l3=592&l4=0&model=1934&modelmenu=1]("http://www.asus.com/products.aspx?l1=3&l2=149&l3=592&l4=0&model=1934&modelmenu=1")

During windows install and/or during operation, have you received any error messages in regards to reading/writing to/from your CD or HDD or other I/O error messages?

During windows install or during operation after a clean install of windows, have you got any BSOD's? if so, what's the 1st code not in brackets? "0x0000004E" for example.

Any other error messages that could be a concern, like from BIOS, or boot error messages with I/O, USB or PCI-E?

What is the arrangement of partitions on your WD HDD?

---

### Post by mattcav on 2008-11-11
[better will follow]

---

### Post by mattcav on 2008-11-11
[B]
At first, I thought you problem may be with a faulty CD drive, but if you can boot from Ubuntu live CD and boot/install windows, that is not likely the case.[/B]

yes it's true, and was my first problem discover if there is a bad hardware. but this cd drive have installed a win xp pro without any problems.


**Personally, I would suggest downloading and installing ubuntu-8.04-x64-alternate install ISO [not the exact file name].**

yes, tonight i'll try on this way. this is the only solution not experimented, without use a 32bit version.

**I suspect the problem may be with ubuntu 8.10. **

i'm not so sure. i've tried to install with an old 8.04 live cd. same problem, at same place.


[B]
If it is with your hardware, it's likely the HDD or motherboard.[/B]

the same motherboard and hdd are inside my girlfriend's computer, and works very well with a dual boot xp/ubuntu 8.10. we have bought our 2 computer at same day, from same shop.the only difference is a phenom for me and an amd 5200+ for her.


[B]
It sounds like your system is home-built; correct?
[/B]
yes, it is homebuild, but is not my first homebuild pc.


**Is your WD HDD SATA I or II?**


sata2. it's a Western Digital - 3,5" 640GB SATA2, this:
[http://www.microfox3000.it/descrizione_modello.php?modello_ricerca=3828](http://www.microfox3000.it/descrizione_modello.php?modello_ricerca=3828)

[B]

This is the correct MB? [http://www.asus.com/products.aspx?l1=3&l2=149&l3=592&l4=0&model=1934&modelmenu=1]("http://www.asus.com/products.aspx?l1=3&l2=149&l3=592&l4=0&model=1934&modelmenu=1")[/B]

yes, it is. the same for me and my girfriend's 5200+


**During windows install and/or during operation, have you received any error messages in regards to reading/writing to/from your CD or HDD or other I/O error messages?**

no, nothing. all works fine, and in win xp all works very good.


**During windows install or during operation after a clean install of windows, have you got any BSOD's? if so, what's the 1st code not in brackets? "0x0000004E" for example.**

i don't know what is a BSOD, but nothing strange from other win installation i've made.

[B]
Any other error messages that could be a concern, like from BIOS, or boot error messages with I/O, USB or PCI-E?[/B]

no, never.

[B]

What is the arrangement of partitions on your WD HDD?[/B]

i've tried for first time install ubuntu in a empity hd, let ubuntu take all empity space(guided installation). not worked, and to try cd/hd i've made a win install, formattinf hdd in ntfs. afer, i've installed ubuntu in a partition of 70%, ext3.


many thanks for your help, mr kevin.
what you think about an installer (wubi?) from an usb pen?
and install the system in an other pc, and then bring back hdd on my pc?

have a nice day,
M.

---

### Post by mattcav on 2008-11-11
don't works. 

don't work ubuntu-8.04-x64-alternate install ISO, don't work kubuntu same iso.

said: file corrupted during the installation process.

i'm thinking it's a bad hardware, but i don't know what...cd? hdd? motherboard? 

but with xp-pro all works very well!

last one: try to install ubuntu in my hd trough another pc. it's a good idea? can it works fine also if i make installation on an intel pc?)

ok, i'm desperate.

M.

---

### Post by tommcd on 2008-11-12
Try the regular 32 bit Ubuntu install CD. You can use either the desktop CD or the alternate CD. You can install 32 bit linux on a AMD 64 bit CPU. If the 64 bit Ubuntu isn't working you may as well try it.

---

### Post by mattcav on 2008-11-14
well, the situation seems a little bit more hard to solve.

i've tried to install 32bit version. nothing, don't works, same problem (file did not match its source copy on the CD/DVD)

i've tried to change sata socket on motherboard. don't works

i've bought a brand new cd drive. not the solution, same problem.

so, i was thinking about a cd interface not recognize under ubuntu installation, and i've tried another approach to the problem.

i've downloaded mini.iso from ubuntu archive, mount it on a cd and try to install via netinstallation.

cd works, connect and begin installation. during installing the base system from server (it.archive.ubuntu.com, but, i've tried another..) system says to me: 

[B]
debootstrap warning
the file [path/filename]was corrupt  
go back    continue[/B]

i don't think that files from us and it repository can be corrupted, and now i've no more solution for install ubuntu on my system.

please, someone help me!

(during this installations, i've re-installed windows. it works well...)

:confused:

---

### Post by kebin071 on 2008-11-15
Man, I just can't figure out why you've been having so many problems. I still have a concern with your hardware.

I mean, if you checked the md5sum of the ISO file, and it's ok, you should be good to go. So I am not too concerned about the CD at this point.

Worst case scenario, I'd go ahead and order a FREE CD from Ubuntu for Ubuntu 8.04 x64 LTS or Ubuntu 8.10 x64; if they send'em to Italy.

But, I'll take a stab at it again, see what we can come up with.


First, a few questions...

**Hardware:**

Is your CD/DVD drive SATA or PATA [IDE]?

Are you using the on-board sound controller built into your motherboard, or are you using an add-on sound card [ie: creative labs or ASUS sound card, either PCI or PCI-E 1x slot]?

**BIOS:**

1st - Have you made any changes to your BIOS?

2nd - Have you over-clocked your system using the BIOS?

if yes, to either question, I'd suggest clearing your BIOS, or rather, CMOS memory. It basically resets your BIOS settings to it's factory defaults, and it's more effective than simply restoring the factory defaults in side the BIOS.

Even if you haven't made any changes, I would go ahead and proceed with the next step to clear the RTC RAM on your motherboard. Make sure you have your ASUS M3A manual handy.

For info on how to do that, power down your system, unplug the power, and refer to your manual, the one I downloaded from ASUS, says:

"Clear RTC RAM (3-pin CLRTC) - Page 2-19" - fr: asus.com english manual for M3A.

I didn't actually read that part, since I know how to do it, but there should be a 3pin jumper on your motherboard marked CLRTC.

**-- *Before you touch anything on the inside of your case, be sure to discharge any static electricity off your body by touching an unpainted metal area on your case. I'd personally suggest unplugging the main power cable from your box/tower before doing so.***

Check further down for more info on BIOS settings BEFORE you boot back up...

------------------------------------------------------------------------------

**Hardware:**

**Once you reset the BIOS factory defaults by clearing the RTC RAM (*from ASUS manual*), leave the system powered off!**

1st - Verify your WD SATAII HDD is plugged into the SATA1 [or HDD1] port on your motherboard.

2nd - Verify your CD/DVD is plugged into SATA2 [or HDD2] port on your motherboard. If you are using a IDE CD/DVD, check to make sure it's jumper is set to master, that it's plugged into the correct 'master' port on cable [i think it's the 1st one from motherboard port]; the M3A manual says your board only has 1 IDE [PATA] port on it.

** Side note:  Most motherboard manufactures list on the motherboard the first HDD port has HDD0 or SATA0; some of them stopped doing that due to inexperienced computer folks would get confused on what's first. Zero is always first, but some didn't know that. Your manual says the first hard drive port is SATA1. Double check that in your manual you got with board.

ASUS says you have 4 HDD ports, SATA 1 - 4. And 1 PATA [IDE] port, which it lists as PRI_IDE.

Consult your manual and BIOS settings to verify the info i'm talking about above.


****** *See the 4 star note at bottom of page if you feel you may have a problem with your WD hard drive's integrity*...**

------------------------------------------------------------------------------


**Other Hardware:** (*check the following before your first boot after you cleared the RTC RAM on your board*).

Once you have verified the ALL ports and cables, and the drives they are plugged into, check the following.

- Just to be sure; power off, then disconnect any non-critical hardware like printers, usb devices like media players, phones, joysticks, or anything like that.

Really, the only thing you need plugged in is your LCD, mouse, keyboard, internet and speakers if you wish.

- Do you have any non-critical add-on cards installed, like sound card, parallel port card, or other PCI &/or PCI-E device (*excluding your PCI-E video card)*?

If you do, you may wish to remove them temporarily before proceeding.

Double check ALL power & data cables to make sure they are correctly seated and connected correctly.

------------------------------------------------------------------------------


**!! BIOS !! - You may want to take notes of settings you change; &/or make a note of the default setting before you change it.**

Assuming you already reset factory defaults in your BIOS by clearing the RTC RAM on your motherboard, change the following settings (*if present*) in your BIOS when you power on the first time; before you go into windows or Linux install.

1 - Verify that your HDD & CD drives are displayed correctly and seem to be detected correctly and in the correct order.

2 - Change the boot order so the system boots to CD first, then HDD. Once Linux install is done, and it reboots for the first time after setup, you'll have to change the boot order again in BIOS to HDD first, then CD.

3 - While in BIOS, disable any settings for AMD Cool & Quite &/or for ASUS Quiet Thermal Solution, and for ASUS Crystal Sound Noise Filtering settings.

You can turn these back on later if you wish.

The ASUS Quiet Thermal Solution is just a BIOS setting that will allow the system to adjust the CPU and voltage to save power when it's not under load. The Noise filtering is for the on-board sound controller and is supposed to help with VOIP calls and other audio software from the OS.

Those settings may not effect the problem, but it's possible. It's best to turn them off for now for troubleshooting purposes.

If there are other settings you are unsure about, ask here or check on the ASUS support forums.

-- Be sure any over-clocking settings are **NOT** turned on, and they shouldn't be once the BIOS settings have been reset to defaults. The memory, CPU, voltage and system timings could effect I/O performance and a host of other things.

Anyway, continue on... **Try to install Ubuntu now.**

Let us know what happens.

***If you are concerned about your hard drive, continue reading below***...

------------------------------------------------------------------------------


**** **Concerns with your Hard Drive's integrity?**

-- Step One: Integrity check from windows... (*If windows is NOT currently installed on the question system, do NOT install it for this test, skip to next test*). I assume windows is installed on partition C: ? Since the partition(s) you tried to install Ubuntu on aren't recognizable by windows, delete ALL non-windows [NTFS] partitions on the system. Ubuntu install likely would have made two (2) partitions during install, one partition for the / "root", and the other for swap space. Delete both of those in windows, using the 'computer management' program file Administrator Tools, under 'disk management'.

Once both or ALL Linux partitions have been deleted, create a single windows [NTFS] partition [max size] and format it. Once it's been formatted, from 'my computer', right click on drive X: (*which ever drive letter is the one you just formatted*) and hit properties. From there, click on 'tools' tab, under error checking, click 'check now'. There will be two boxes, one to 'auto fix errors' and one to 'scan for bad sectors'; Make sure BOTH boxes have a check mark in them. Once the scan starts, it may take a bit, anywhere from 10-40 mins, pending errors found. When it's done, it should tell you if there were NO errors found; if no errors found, the data integrity on HDD is ok.

-- Step two:  If Windows is NOT installed on the question system, and Linux doesn't boot, you'll want to connect your HDD to your girlfriend's/wife's system. If her system has a single SATA CD/DVD drive, the HDD from your system would be plugged into SATA3 on her motherboard. That's if her board has HER HDD plugged into SATA1, her CD plugged into SATA2, and YOUR HDD plugged into SATA3. In other words, plug YOUR HDD into the next SATA port that's open in order.

Anyway, once YOUR HDD is plugged into HER motherboard, boot the system and log into your OS. If her system has Windows on it, go back up to step one above. If HER system doesn't have windows installed, or you'd prefer to use Ubuntu, continue...

In Ubuntu, install GParted (GNOME Partition Editor].

Once installed, run System > Administration > "Partition Editor". HER HDD should be listed has /dev/sda. You HDD should be /dev/sdb. VERIFY THAT. Use the drop down to change the targeted drive to the one from your system.

If your windows files are already backed up, delete ALL partitions on the suspect HDD from YOUR system. Create a new single partition in ext2. DO NOT MOUNT THE HDD!

The integrity check can't be performed once the drive is mounted. If you mounted it, unmount it.

- Anyway, from the drop-down menu in the partition editor program, select > Partition > then click on 'check'.

It should report no errors. If so, let us know. Or, contact the seller or manufacturer for a replacement if either step is not able to repair any errors found. If it has bad sectors, and under warranty, it needs to be replaced.

------------------------------------------------------------------------------


Any other questions, or info, post a reply.


BTW: In regards to one of your earlier questions, about installing Ubuntu on your girl's system, with your HDD, then put your HDD back into your system with Ubuntu installed on it; I'd be glad to tell you how to try that if you want.

I'd suggest doing that as a worst case sarnario; simply based on that information you have provided, I am not conviced it's a software problem with the CD. If it's not a software problem, the only other thing it could be is hardware.

If it really is some type of hardware problem, imho, you'll want to find out what it is at some point, before it causes more problems down the road.


The wubi install shouldn't fail, since it downloads the files from the net while it installs Ubuntu into the virtual HDD file in the windows file system; so that's an odd concern.

The wubi installer I downloaded, from my memory, was just a few MB's in size, and it downloaded the files on-demand.

Hope my info is helpful.

------------------------------------------------------------------------------



***DISCLAIMER:  The information and suggestions above are provided without any warranty of any kind and are not guaranteed to be accurate. Consult your motherboard's manual before and during the process of any of the suggestions I've described.***

---

### Post by kebin071 on 2008-11-15
oh, a final note... your manual says:

[quote=ASUS]2.6       Jumper
   1.   Clear RTC RAM (3-pin CLRTC)
   This jumper allows you to clear the Real Time Clock (RTC) RAM in
   CMOS. You can clear the CMOS memory of date, time, and system setup
   parameters by erasing the CMOS RTC RAM data. The onboard button
   cell battery powers the RAM data in CMOS, which include system setup
   information such as system passwords.
   To erase the RTC RAM:
   1. Turn OFF the computer and unplug the power cord.
   2. Remove the onboard battery.
   3. Move the jumper cap from pins 1-2 (default) to pins 2-3. Keep the cap on
        pins 2-3 for about 5~10 seconds, then move the cap back to pins 1-2.
   4. Reinstall the battery.
   5. Plug the power cord and turn ON the computer.
   6. Hold down the <Del> key during the boot process and enter BIOS setup
        to re-enter data.
          Except when clearing the RTC RAM, never remove the cap on CLRTC jumper
          default position. Removing the cap will cause system boot failure!
                                                       M3A
                 ®
                                              CLRTC
                                         1 2           2 3
                                         Normal    Clear RTC
    M3A Clear RTC RAM                   (Default)
          &#8226;    You do not need to clear the RTC when the system hangs due to
               overclocking. For system failure due to overclocking, use the C.P.R. (CPU
               Parameter Recall) feature. Shut down and reboot the system so the BIOS
               can automatically reset parameter settings to default values.
          &#8226;    Due to the chipset limitation, AC power off is required prior using C.P.R.
               function. You must turn off and on the power supply or unplug and plug the
               power cord before reboot the system.
[/quote]

that's off of page 2-19.

---

### Post by kebin071 on 2008-11-15
oh dang. i forgot...

if you do have windows up and running, you may as well update your BIOS before you do all the other stuff i was talking about.

i would update the bios first if you can actually.

i've read a lot of reviews about ASUS motherboards where poeple would update the BIOS first thing.

I'd check your version against the downloadable verion on the ASUS web site.

PS: Read the ASUS M3A Manual.

---

### Post by mattcav on 2008-11-18
well,

first of all, thank you mr. kevin: i've read all your posts and they're very good to understand better some advanced settings of these motherboard.

after, a news from my phenom:

i've do, like kevid wrote, a udpgrade of my mb bios. now running a 13/11/2008 bios, downloaded directly form asus website.

then, i've tried to install a ubuntu 8.04 LTS 32bit from livecd, and there was a little step forward. the computer don't give an error about 22%, but it give me same error arond 40%, during a openoffice's library installation.

ok, i've hit 'retry' and the installation gone forward. 

other 5-8 errors, always 'retry' always forward.

when the installation finished, and it did a reboot, ubuntu appears.

all seems ok, and i've tried to install some as 149 upgrades.

all works good, but not all.

when i try to install:
**linux-image-2.6.24-19-generic**

sistem give me an error. same error (in italian)

 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: il file tar è rovinato - l'archivio del pacchetto è rovinato

in english, is something like:
[B] /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb:  tar file corrupted 
[/B]

ok...a step forward, but i don't understand what problem is on my computer again.

 i think is the same(but i don't know what...) 
can i try some solution from here?


have a nice day,

M.

---

### Post by mattcav on 2008-11-18
installing some programs on this ubuntu to try limit and stability, i found another package that system says 'corrupted'

it is:
**listdc++6-4.2-dev**

there's a reason why both packages are recognized as 'corrupted'?

for now, only this two give error.

i've installed so many programs like amarok, or eclipse.

M.

---

### Post by ccheath on 2008-12-20
i found this thread via google "The following file did not match its source copy"

i have a feeling the hard drive is the problem
the pc i'm on is an [emachines t5226]("http://emachines.com/products/products.html?prod=T5226")

previously it had vista home premium 32bit on it and was doing all kinds of funky stuff that i at first thought was malware

so i did restore from the hdd restore partition 
that had problems but still booted into vista after the install
but, it had funky errors still (wmi host stopped working a lot and the sp1 update just would not install)

so i decided to reinstall from the disc
that was much better of an install, but defender wouldn't start
and i had a lot of problems getting updated again (finally got to sp1 and it won't install again)

so we're going to ubuntu now

first tried the 64bit disc (since the t5226 is x64)
got "The following file did not match its source copy" errors around 60% copying and from there on kind of randomly

ubuntu just won't install (the livecd runs fine)

so my next thing i'm going to try is to put a known good hard drive into the box and try to install to that

any other ideas on salvaging the current drive?

Cheers,
Chris Heath

---

### Post by tommcd on 2008-12-20
I'm not sure why you posted to this thread, since the title of the thread is about AMD Phenom CPUs. The e-machines PC you linked to has an Intel Pentium D CPU and Intel 945G chipset.

Anyway, Ubuntu should install just fine on that computer of yours.
Some suggestions:
Download the Ubuntu 32 bit live CD. You don't need to use 64bit. 
Make sure you burn the CD at a very slow speed. Use Iso Recorder of Infra Recorder. Also verify the md5sums of the downloaded iso file and the disk you burn:
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you suspect the hard drive is bad:
Does Vista have a utility for checking the hard drive for errors? Windows XP did, so Vista probably does also. Run that if you can to check the drive.
Also, can you open up the computer to see who made the hard drive? All hard drive manufacturers have utilities that you can download from the manufacturer's website that you can run to check the drive for errors or bad sectors. If the computer is still under warranty you may not want to open it up since that would likely void the warranty. Then again, if the computer is under warranty, perhaps you can get the drive replaced.

And welcome to the Ubuntu forums!

---

### Post by ccheath on 2009-01-05
tommcd,

thanks for the suggestions
i did eventually get to install (and so far run okay)

i did the md5 check from the boot screen on both the 32 and 64 bit install discs and they checked out okay but kept getting these same error messages as mattcav 

i did initially suspect the hard drive as the culprit and ran my copy of steve gibson's SpinRite on it and there were not reported errors so i gave the 32bit disc another try and after getting some of these error messages again and clicking retry it eventually copied the install over to the hard drive

so like i said it's running okay for now
thanks for the suggestions,
chris heath


> **tommcd said:**
> Some suggestions:
Download the Ubuntu 32 bit live CD. You don't need to use 64bit. 
Make sure you burn the CD at a very slow speed. Use Iso Recorder of Infra Recorder. Also verify the md5sums of the downloaded iso file and the disk you burn:
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you suspect the hard drive is bad:
Does Vista have a utility for checking the hard drive for errors? Windows XP did, so Vista probably does also. Run that if you can to check the drive.
Also, can you open up the computer to see who made the hard drive? All hard drive manufacturers have utilities that you can download from the manufacturer's website that you can run to check the drive for errors or bad sectors. If the computer is still under warranty you may not want to open it up since that would likely void the warranty. Then again, if the computer is under warranty, perhaps you can get the drive replaced.

And welcome to the Ubuntu forums!

---

### Post by jpppdk on 2009-06-01
I reached this page after searching for "the following file did not match its source copy on the cd/dvd".

I have  an ASUS M2N68-AM mainboard, AMD X2 5200+ processor, WesternDigital WD1600 x 4 and Corsair XMS 6400 2GB x 2. I had the exact same issue with Linux installation (Ubuntu 32/64, Kubuntu 32/64). Windows XP SP2 also showed  the same problem UNLESS I turned on RAID in the BIOS and then provide RAID drivers (in a floppy) at the begening of Windows install. That way Windows install worked for 32/64 bit vesions.

After trying everything including different ISO, burning softare/speed, single SATA disk, an old PATA disk... the same error persisted.

I was directed towards the disks and BIOS because of the error message and the fact that Windows worked with drivers. BUT the answer was in  the RAM. I finally ran Memtest from ubuntu live CD and figured one of  the 2 DDR2 modules showed errors (I counted upto 2400 errors before aborting the test). I removed the one with errors ran memtest with the other module without errors for around 30minutes. With only that one module installed I installed Ubuntu 9.04 64bit on  the first try :D.

I have seen posts from other who had the same problem BUT ith memtest NOT returning any errors in RAM. But it looks like RAM is a primary candidate for this error even though the meesage points to HDD and DVD. Hope this helps someone.

EDIT: just to add that I downloaded the ISO 5 times, bought a new DVD drive, a new SATA disk drive, burned around 8 CDs and 7 DVDs.... I didnt think my brand new Corsairs would be faulty...
JPPP.

---

### Post by VastOne on 2009-06-01
> **jpppdk said:**
> I reached this page after searching for "the following file did not match its source copy on the cd/dvd".

I have  an ASUS M2N68-AM mainboard, AMD X2 5200+ processor, WesternDigital WD1600 x 4 and Corsair XMS 6400 2GB x 2. I had the exact same issue with Linux installation (Ubuntu 32/64, Kubuntu 32/64). Windows XP SP2 also showed  the same problem UNLESS I turned on RAID in the BIOS and then provide RAID drivers (in a floppy) at the begening of Windows install. That way Windows install worked for 32/64 bit vesions.

After trying everything including different ISO, burning softare/speed, single SATA disk, an old PATA disk... the same error persisted.

I was directed towards the disks and BIOS because of the error message and the fact that Windows worked with drivers. BUT the answer was in  the RAM. I finally ran Memtest from ubuntu live CD and figured one of  the 2 DDR2 modules showed errors (I counted upto 2400 errors before aborting the test). I removed the one with errors ran memtest with the other module without errors for around 30minutes. With only that one module installed I installed Ubuntu 9.04 64bit on  the first try :D.

I have seen posts from other who had the same problem BUT ith memtest NOT returning any errors in RAM. But it looks like RAM is a primary candidate for this error even though the meesage points to HDD and DVD. Hope this helps someone.

EDIT: just to add that I downloaded the ISO 5 times, bought a new DVD drive, a new SATA disk drive, burned around 8 CDs and 7 DVDs.... I didnt think my brand new Corsairs would be faulty...
JPPP.

Good catch JPPP.  

Just remembering the good old days when a memory problem would cause the ear ringing, gut wrenching beeps at boot up that gave a code that something was wrong. 

Of course most home built pc'ers, including me, do not bother to even connect the internal speaker anymore...

:redface:

---

### Post by jimbobstan on 2010-05-16
Hi,
 
I know this doesn't belong technically in this area of the forum, but I had a very similar issue to you, but with different HW.
 
No matter which Ubuntu version I downlaoded and burnt, I still had errors during the installation saying "the following file did not match it's source copy...blah blah".
 
Then I saw your post about the ram and i did a ram test. The computer just rebooted directly at the beginning. Knowing something was wrong, I went into the BIOS to check my ram settings. Sure enough, my ram timings were set to "manual" and the ram speed was also manually adjusted (i have no idea why... i proabably was experimenting with some wacky idea in the past). I returned all these settings to "Auto".
 
I then tried Ubuntu 9.10 (because I know i burnt this disc at 4x, and 10.04 I burnt at full speed, so i wanted to take no chances) and it installed without a single error.
 
So please try that if you have this error. Maybe an admin can copy this post to a more generic thread for this error? I just wanted to share my solution in case this works for anyone else.
 
Thanks guys!
 
James

---

