---
title: "[SOLVED] Totally desparate.."
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by togo59 on 2008-06-27
I installed ubuntu (Hardy) on a separate disk to windows but managed to overwrite the windows boot sector. Symptom is the same as bamboo BUT Ubuntu can only see my (let's call it the C: drive but it's actually /dev/sda: ) from the command as follows:
```
roger@roger-ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d930d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000660ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   224829674   112414806   83  Linux
/dev/sdb2       224829675   234436544     4803435    5  Extended
/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbe423ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

```

If I go to Places/Computer -- the drive is missing.

When I install the Windows CD for recovery, what was previously a D: drive is now called C: and there's no OS there. It can't see my original C: drive.

In the bios,  have tried swapping the Boot Priority and the Disk Order (or whatever it's called -- I'm sure you know what I mean :)) and it makes no difference, what was a D; drive is now a C:.

Here is the menu.lst, should it prove interesting.
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

```

I have tried using the Windows install disk but it doesn't see my SATA drives at all. I've tried Super Grub Disk to no avail.

Please help me someone!

---

### Post by jimv on 2008-06-27
Was Windows on the 500 gig drive?

---

### Post by togo59 on 2008-06-27
Sorry: This is embarrassing, I've got two identical threads now (I tagged onto somebody else's thread [http://ubuntuforums.org/showthread.php?t=840310]("http://ubuntuforums.org/showthread.php?t=840310"), then, with no answers, started this one :oops:

Perhaps any other replies could go to the other thread.

But no, I have three hard disks, one IDE and two SATA, as follows:
[LIST=1]
[*]Windows was (is) on the 80Gb SATA disk (but it's invisible except in the BIOS, or when I type fdisk -l)
[*]The 500Gb IDE disk is windows stuff (my personal data, but no OS) Visible from Ubuntu and from the Windows recovery disk
[*]Ubunto is on the 120GB (SATA disk)
[/LIST]

Thanks for replying to this thread. Please could you reply to the other thread and then I'll delete this one.

---

### Post by jimv on 2008-06-27
OOps, I'm dumb.  I didn't see the 80 gig drive.  Well, here's a test: unplug the 120 and 500 gb drives and see what happens.  If it says invalid system disk, then at least it's seeing the drive and you can try mbrfix from your Windows disk.

---

### Post by togo59 on 2008-06-27
Hi,

I tried unplugging the 500Gb. The Windows install disk (running the repair) said I had no disks at all. Even though the BIOS can see both. (All three when they're all connected.)

:( :confused: :(

[Is there something funny with the forum software? I have had to retype two replies after hitting Submit.]

P.S. I am hitting the sack now (it's late and I've been up for a while) thank you for your help, I log in tomorrow.

---

### Post by jimv on 2008-06-28
Perhaps try the steps in the thread:

[http://forums.techguy.org/hardware/715089-solved-xp-setup-not-seeing.html](http://forums.techguy.org/hardware/715089-solved-xp-setup-not-seeing.html)

Apparently the XP setup needs SATA drivers or there's an option in yoru BIOS that you may be able to change.

---

### Post by togo59 on 2008-06-28
Many thanks Jim, I'll give it a go. :cool:

---

### Post by togo59 on 2008-07-01
:(

This is driving me crazy. I followed [[COLOR="DeepSkyBlue"]these[/COLOR] ]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml")steps ([ [COLOR="DeepSkyBlue"]nLite[/COLOR]]("http://www.nliteos.com/index.html") is an amazing free program) but to no avail. I slipstreamed the SATA drivers but the problem is that I already have a Windows disk that I'm trying to rescue - so I go for the repair option with the Windows recovery disk and it just doesn't detect the drive (even though it is visible in the BIOS).

I have also tried BootMaster (which recovers an MBR) -- it could see the disk OK and I wrote a new MBR to it, but no change!!

I tried SuperGrub but again no effect.

This is my menu.lst (the bit with the reference to windows):
```
title		Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify		(hd1,0)
chainloader	+1
boot
```

I can't mount the drive from Ubuntu (despite following several tutorials about mounting). The drive thats playing up is sda1. NOte the difference between fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff56ff56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000660ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbe423ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```
and blkid
```
/dev/sdb1: UUID="89d635d1-d2ea-44a7-8095-70e4fd64b242" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="aaba6a7e-ff32-42c4-a0a3-acdf982c839d" 
/dev/sdc1: UUID="F628D3F928D3B739" LABEL="Big" TYPE="ntfs" 

```
/dev/sda1 isn't present. My fstab file is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=aaba6a7e-ff32-42c4-a0a3-acdf982c839d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /media/windows ntfs defaults,umask=007,gid=46 0 1 
```
I manually added the last line in response to advice from another thread.

I really need my Windows disk back, so if anyone can help I would be very appreciative.

[Edit: If I try to boot to Windows from the Grub menu it says: "Error 13: Invalid or unsupported executable format."]

---

### Post by togo59 on 2008-07-01
](*,)
And now, with the aid of Super Grub, I have reduced my system to a complete pile of junk.

No Windows, no ubuntu and seemingly, no BIOS.

The screen just stays blank on reboot. Rescue disks don't help, there's nothing. No messages of any sort.

Users of Super Grub be warned!

And all this because I followed standard Ubuntu install directions.

:mad:

---

### Post by Rallg on 2008-07-01
No BIOS?

Put in a useful system CD (live Ubuntu, RescueCD, or a Windows installer).

Turn off your computer (use the switch, dude). Wait a minute. Turn it on. Do you see the manufacturer's splash screen? (It would say "IBM" or "Dell" or "Fujitsu" or whatever.)

If no manufacturer's splash, then either you REALLY fried your system, or you inadvertently disconnected the monitor.

If manufacturer's splash, that is the time at which you press a function key to get the BIOS boot menu. On my laptop, the key is F12 (yours may differ). Can you get to BIOS that way? If so, then select to boot from CD. Does that work?

If you cannot get a BIOS screen with any function key, or you cannot boot from CD, then you indeed have a problem. But it is quite rare to fry your BIOS.

If you can boot from a CD, then the next time you boot the computer, at the manufacturer's screen press the function key that gets you to the master BIOS menu (on mine, it is F2). Change the boot order so that CD is the top priority. Note that if you don't have a bootable CD, then the system will fall back to the next in priority, usually the hard drive.

Can your computer boot from USB memory stick? There are ways to make a blank USB bootable, install DOS, and GRUB4DOS. That gives you a GRUB boot method that doesn't use whatever GRUB you have on the hard drive, and doesn't care about the MBR, either (unless you ruined the partition record).

If you can get something useful to boot, then you are probably most of the way towards fixing the problem. Ultimately, you might be better off just retaining Windows and removing Linux. However, it is not as simple as trashing the Linux partition(s) since you still have to deal with the boot process. That's where a bootable USB can come in handy.

---

### Post by togo59 on 2008-07-01
> **Rallg said:**
> No BIOS?

Put in a useful system CD (live Ubuntu, RescueCD, or a Windows installer).No BIOS screen.

> Turn off your computer (use the switch, dude). Wait a minute. Turn it on. Do you see the manufacturer's splash screen? (It would say "IBM" or "Dell" or "Fujitsu" or whatever.) I used the switch.

>  If no manufacturer's splash, then either you REALLY fried your system,  :(

> or you inadvertently disconnected the monitor. 
I checked the monitor.

>  Can your computer boot from USB memory stick? 
I doubt it, without a BIOS.

>  Ultimately, you might be better off just retaining Windows and removing Linux. However, it is not as simple as trashing the Linux partition(s) since you still have to deal with the boot process. That's where a bootable USB can come in handy. That's what I was trying to do.

:cry:

---

### Post by jimv on 2008-07-01
Holy crap, I can't imagine how a supergrub disk could toast a bios.

Be afraid...SuperGrub has become self aware and destroyed your computer!

I think it's time to open the case and disconnect the drives to see if you can get it to boot.

---

### Post by togo59 on 2008-07-01
The only thing I can think of is (maybe) with so many reboots it had some sort of hardware failure. Like you, I didn't expect Super Grub to toast the BIOS (but then I didn't expect the standard Hardy install utility to toast my Windows boot sector).

Judging by the number of similar sounding threads, the Ubuntu installer should carry a health warning. :mad:

I will have to physically remove my drives and put them in another machine to see if I can recover the data.

What a waste of time.

---

### Post by jazziam on 2008-07-05
Just a quick check, have you cleared your CMOS i.e. used the jumped on the mobo to clear your CMOS and return it to its default?

---

### Post by StormPCs on 2008-07-05
It seems like you are blaming Linux for your issues.  That is not possible, unless you mean that your computer would be running fine today had you not attempted the installation in the first place.  That may or may not be the case, but it seems to me that you could use a better understanding of computers in general.  This is needed if you wish to use Linux successfully.  That's because people are not perfect, so even if you follow all of the instructions perfectly you may not get the desired result.  You need to know enough to recognize when a mistake of some kind has been made.

I mean no disrespect but you really need to hook up with someone locally who can help you out with this.  Many of your observations do not seem to make sense.  It seems your setup is a little more complicated than many.  You may have hardware, software or virus issues, perhaps even all three.

You spoke about not wanting to wast time.  That tells me you don't want 
to tinker.  In this case you should get it clear in your mind how you want to use your system and the functionality you need, and then find a professional who can make that happen for you.

In my experience Linux is not a good OS for people who are not extremely well-versed in several computer disciplines, especially those who like to play.  In Linux you really need to get your system the way you want it and leave it alone once you are good,  If you play, even if you are somewhat of a guru compared to your neighbors you can still get into trouble.  Only you can decide if Linux it is for you.

There is a reason why Vista and Win XP are so idiot-proof.  Linux will never be as good in that regard, for the same reason Linux has no antivirus software.  Both are simply not necessary.

Good luck to you.:guitar:

---

### Post by misterbk on 2008-07-05
> **togo59 said:**
> The only thing I can think of is (maybe) with so many reboots it had some sort of hardware failure. Like you, I didn't expect Super Grub to toast the BIOS (but then I didn't expect the standard Hardy install utility to toast my Windows boot sector).

Judging by the number of similar sounding threads, the Ubuntu installer should carry a health warning. :mad:

I will have to physically remove my drives and put them in another machine to see if I can recover the data.

What a waste of time.


Just a suggestion, don't discount the idea that a hardware failure that was going to happen anyway just happened to occur while you were tinkering.  It has happened to me before and I went around blaming the wrong piece of hardware for a while before I figured out it was something else.

My recommendation would be to try that cmos reset jumper.  If there is none try removing the battery and the power cable to the computer for a while, making sure there's time for the capacitors to slowly discharge.  Don't forget to write down which way the battery goes in the socket, you may have to leave it for a few hours.  (part of the purpose of the cmos reset jumper is to discharge any voltage stored in capacitors.)

If the 80GB drive is functioning correctly and just has had its partitions scrambled, here's how to get your data back:

1:  Locate a computer that works that you can use.
2:  Locate and obtain hard drive recovery software that supports NTFS **and isn't just a simple undelete tool.**  I have been using R-Studio with good success but there may be freeware as that costs money.  (I have found it quite worth it actually.)
3:  Install the recovery software.
4:  NOW attach the drive to the computer. (if it's failing you want it spinning as little time as possible.)

At this point you have a choice.  If you have at least 120-ish gigs of available storage to use that is on a different drive (not the 80gb one), you should **create an image** of the 80GB drive, storing the image somewhere else, on some other drive's free space.

(The idea here is you do not save anything back to the 80gb drive.)

If you do not have 120-ish gigs of space, but do have some free space (say at least 60 gigs), then you can try to scan and recover directly.  But, in this situation, if new bad sectors happen while you're recovering you may lose more files.

In either situation, your recovery software will probably need to scan the drive.  Save the scan info if you can so you don't have to scan it again.  Crawl through the folders located by your recovery software picking ones that look like your files, and tell the recovery software to save them to your alternate location.  If the 80GB drive is in good shape, it should be a slow but manageable process.  If it's not, this could take a long time, like days, so plan for that.

If you're using R-Studio, it will problem-solve and attempt to figure out what the folder structure was and present as much of the drive in that structure as it can.  But it will also find unrooted folders that may or may not be duplicates of the files it did organize correctly...  So if you had 30GB of actual files your recovery might take up over 60GB until you remove the duplicates.  The recovery process there is to just go down the list and mark checkboxes, then when you're done hit Recover Marked and wait for it to finish.

Then you can reinstall windows and your software and get back up and running.


P.S. I'm in agreement here, I'm 90% sure nothing in any of the linux software you used could actually have hosed your bios.  It -could- have damaged your windows partition though.  I'm gradually learning that the best way to install linux is to remove any hard drives you don't want to be modified, just so it's impossible for you or the software to change them.

(Also for me, linux got confused when writing the bootloader when I had two hard drives in the system, and linux wouldn't boot.  This is a linux-only system though.)

---

### Post by falcon61102 on 2008-07-05
> **jazziam said:**
> Just a quick check, have you cleared your CMOS i.e. used the jumped on the mobo to clear your CMOS and return it to its default?

If you've tried this and still no luck.  I would download the latest BIOS for my mobo and start there.  Follow your motherboard instructions for flashing the CMOS to get a new BIOS if indeed it is fried and then start working with your other hardware issues.  

misterbk had some good suggestions to image your drive, which will allow you to start the process of extracting your data without touching the actual physical drive.  Once you get that backup image, repartition and format that drive so that you have a clean drive and then start re-installing your OS of choice from there.  Once you actually have a system up and running, then you can go back to that backup image and pull out all of your personal files.  Not the most efficient way to restore your system but it works.

---

### Post by bilijoe on 2008-07-06
> **StormPCs said:**
> In my experience Linux is not a good OS for people who are not extremely well-versed in several computer disciplines, ... [SIZE=2]***I totally disagree!***[/SIZE]  This may have been true a few versions back, but by 7.10, I find Linux to be completely as usable, user friendly, robust, and stable as any Windows system.

:arrow:Uninformed people shy away from Linux because of horror stories about the command line interface, and complex installation issues.  My experience is that, with Ubuntu version 7.10, came as intelligent, robust, and (unless you use some less-than-common hardware) foolproof an installer as any Windows installer (not to mention faster and easier).  I have had zero problems installing 7.10 on many different desktop and laptop systems.  As for the command line, by 7.10 its use became almost completely unnecessary (unless you wanted to use it for the tremendous extra power and versatility it provides).  Pretty much everything you need to do to set up and run a system for an average user, can be done through the GUI.  And power users rejoice at, rather than fear the command line.  Also, let's not overlook that Windows has a command line interface too, and there are occasions when it must be used, (just as there are in Linux); to run "ipconfig", for example.  As far as tinkering goes, you can break any system via uninformed tinkering.  Linux, because of its unequaled accessibility, may encourage tinkering more than other OSs, but it is, by no means, more susceptible to damage by tinkering than any other OS.  It is simply easier to get at its critical components (which, if you do your homework, and behave yourself [**and backup your system before you start tinkering**], is a distinct advantage, rather than any kind of flaw or weakness).

I have been a Linux fan for many, many years, yet I too have refrained from recommending it to regular users (as opposed to computer hobbyists, computer science students, or other more experienced users).  Since the release of 7.10, however, I have been up on my soapbox, 24 hours a day:lol:, trying to convert everyone I know, away from the disaster that is Windows, to the magical world of Linux (specifically, Ubuntu 7.10 [I haven't had the time to check out 8.04 yet to the point where I am recommending that version, but I suspect I soon will be--I just know, from lots of experience that 7.10 is "safe" for the most computer illiterate of users]).

\\:D/Linux has come of age, my friends, and it is time to preach the word to the masses.  Myself, I have informed all my friends and associates, for whom I represent an informal IT department, that I will soon cease working on Windows-based systems; the problems are too messy, and take too long to fix (when that's even possible).  I will, however, be willing to help them with any problems they may have (if they have any), on Linux-based systems.

:!:Linux is a far more well conceived OS than Windows ever was.  Simply put, it is a fundamentally superior design.  Only because of the many paid programmers[-( (remember, Linux programmers donate their time), and the often highly questionable marketing practices of Microsoft:evil:, did Windows get the huge head start that it did.  But, that is all it was--a head start.  Linux is so fundamentally superior that, now that it has [slowly] come of age, through the efforts of hundreds (if not thousands) of volunteer programmers, and users willing to work with a [sometimes] flawed, and immature system, in order to foster the development of proper OS, for the benefit of us all, the head start Windows has enjoyed for so long has begun to dwindle.  Soon the faster, better, cheaper (read that "free") contender will catch, and pass the bloated, lumbering monstrosity that is Windows.

This is, of course, all, no more than my humble, personal opinion.  But as more and more hardware and software providers jump on the Linux bandwagon, look for the race to become quite interesting, and look forward to the day when, upon poking your head into someone's office or den, you see a Linux screen, shining brightly on their monitor.

I just had to get all that off my chest; sorry if I bored any of you.

:arrow: P.S.  ***This is very important!***  If you download a CD image, with which to create an install CD, you **MUST** perform the MD5 checksum test on the file, and (I recommend) also on the resulting CD.  [SIZE=2]*Failure to do this may very well result in an installation that will live up to all the horror stories you have ever heard, and one that may be impossible to repair or ever get running correctly!*[SIZE=1]  [SIZE=2]Linux, like any OS, is a highly complex piece of software (actually, many pieces of software).[/SIZE]  [SIZE=2]One incorrectly downloaded or copied bit, in all those Megabytes of program code and data, can result in the most hideous and insidious of "bugs".  Such "bugs" are absolutely NOT attributable to any flaw or error in Linux, but will inevitably be attributed to it, reinforcing the negative publicity Linux has long been subject to.  I[/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=1][SIZE=2]n the interest of avoiding spreading false information about the quality of the Linux OS[/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=1][SIZE=2], PLEASE!  _Do_ _NOT_ over look this step (the MD5 checksum validation of your downloaded file, and your install CD).  In downloading CD images for Linux install disks, I have experienced a 20% rate of downloaded files that were shown (by the checksum test) to contain errors, and about a 2% rate of CDs that also failed the test, due to copying errors.  The validation procedure is quick and easy, and well documented and supported in the download instructions provided by Ubuntu.  With the error rates I have experienced, my guess is that roughly 10% of the seriously disgruntled would-be Ubuntu Linux users, who submit critical posts to the Ubuntu Forums, result from download/copying errors that **would have been caught, and the ensuing disaster avoided**, had the user simply validated his or her install disk, prior to attempting installation.  Please, do not consider this step of validating the accuracy of the .iso file, and the CD as "optional"; it is not!


:arrow: P.P.S.  I mentioned the Ubuntu Forums above.  I would like to thank all those who contribute their time and expertise to making the forums positively the best form of technical support I have ever encountered.  I have had every question answered, and every problem solved that I have posted to the forums.  And in record time, compared to even the best technical support I have received from any other source.  These forums also reinforce the "community" nature of the Ubuntu experience, an aspect of Ubuntu that I cannot praise highly enough.  When you choose Ubuntu as your flavor of Linux, you not only get a powerful, professional quality operating system, you also get the best of the best technical support, and membership in a world-wide family of Ubuntu users, which carries more benefits, both obvious (like the forums) and subtle (like the feeling of never being alone, when wrestling with a difficult problem), than I can enumerate.  Linux is clearly the best!  And Ubuntu, the best of the best!  Don't take my word for it.  Try it, and see for yourself!  You won't regret it.

Sincerely, [/SIZE][/SIZE][/SIZE]

---

### Post by falcon61102 on 2008-07-06
Nice post... I have to agree with many of the things you said.  While I'm really just getting into Linux, I remember tinkering with it about 6 or 7 years ago and I am amazed at how much has changed and am constantly amazed at the amount of people that are now using it.  This forum is proof of that alone.  While I am definitely enjoying my new-found freedom from windows, I can still see where many people are leary about jumping in.  Fortunately with all the Live CDs out there, people can get there feet wet and really see how easy it really is.  I recently set up my system which is a dual boot Vista/Ubuntu on a XPS 1530. I had fewer problems and it took less time and effort to get my system up and running than it would if I was trying to do a dual Vista/Xp boot system to include resizing my partitions.  I look forward to continuing learning everything Ubuntu and Linux has to offer.

---

### Post by togo59 on 2008-07-10
Guys -- I'm soo grateful for your kind observations.

Let me state: I use Ubuntu at work having switched from SUSE and I just love it. The 8.04 upgrade went onto my dual-booted Toshiba laptop with no worries. Wireless worked straight out of the box.

I installed Ubuntu on my daughter's PC last year and it went on with no problems other than I have failed to convince the Broadcom wireless hardware, the nDis wrapped drivers and the wireless network to have anything to do with each other (and don't worry - I've spent more hours trawling through threads, stickies, blogs etc than is safe for my fragile sanity).

The fatal problem I had with my own PC (just put yourself in my shoes..) was that I was dealing with some sensitive Super Grub steps, reading the instructions oh-so-carefully, and gently clicked 'yes' on the 'OK to reboot' option when (unknown to me) a two-year old memory card failed. Just went pop. :confused:

I'm sorry, the reason I couldn't see my BIOS was that my PC had a hardware fault. It was nothing to do with Linux, Ubuntu, or SGD. But it was a bit like you're doing open heart surgery when the large marble the patient had secretly placed in his mouth before the op suddenly gets stuck in his wind pipe. :(

I did take all your excellent advice and I agree with pretty much all that's been said. The main thing is that I realised I was out of my depth and contacted the technicians at work (although this is my private, home PC). The battery was removed from the CMOS and the BIOS reset. Technicians cleverly spotted the faulty memory and, with that removed, at least it got as far as the BIOS screen. One technician, who has been working with SUSE and Scientific Linux systems for many years told me that Super Grub Disk had caused him problems as well. I won't say what he thought of SGD but here's my bit of advice: If you've got MBR problems or similar, be an expert *before* you use SGD. I've developed tons of stuff on Linux systems, I've spent much of my life programming, but I've never needed to know how boot loaders, boot sectors, MBRs etc need to be configured. SGD is written by an extremely competent enthusiast but even s/he is not able to anticipate every situation (and the wiki page is FULL of blanks!) so users like me are short on info. I like risks, took one and if the memory card hadn't failed all that would have happened was that I would have had an unbootable PC that could have booted from a recovery disk.

My friendly technical support guys were able to recover all my files (though even they said it was a struggle as Grub had installed itself on all three drives and each one was inaccessible - I didn't do this explicitly - there's no way I wanted the 500Gb disk to be anything other than a data disk). The disk drives were removed and installed on a computer set up for this type of recovery. I forgot to ask the recovery software they used. All three drives were re-formatted and windoze and my data files were re-installed. :redface:

So I'm back to a working windoze system (well, almost, there was some residual damage -- some recent data files got corrupted but I had backups; I haven't yet come across an unbacked-up corrupted file yet but I'm sure I will). I had backed up my data disk but as all my software on the C: drive is sitting in my cupboard on CDs or is downloadable I didn't do an image backup but I should have done.

Whatever happens (and thanks to the Ubuntu support) I know my PC's destiny is to be dual-booted, with Ubuntu on one of the SATAs, windoze on the other. But, as per your good advice, I will create an image backup of my system drive before I go any further.

FYI: When I could only boot Ubuntu I didn't really miss windoze, now I've only got windoze I _really_ miss Ubuntu. :cry:

Thanks for all your help and advice!!

):P

---

### Post by falcon61102 on 2008-07-10
Wow... glad you got everything working again.  Talk about an untimely hardware fault.

---

