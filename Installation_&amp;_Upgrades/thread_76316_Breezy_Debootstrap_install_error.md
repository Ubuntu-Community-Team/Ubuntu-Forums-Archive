---
title: "Breezy Debootstrap install error"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by dickohead on 2005-10-14
I'm currently trying to install Breezy on my laptop, I successfully installed hoary, and was running it for months, but after a kernel problem i decided to format and start again.
I am getting returned with this error in Breezy's base system installation:
```

Base System Installation error The debootstrap program exited with an error (return value 1). Check /target/var/log/bootstrap.log for details.

```

But the file bootstrap.log does not exist, i tried changing my root partitions file system from Reiser to Ext3, as per some suggestions in another thread, but still have the same error, i have attempted skipping the base install only to run into more problems. I also burnt the CD at 2x speed but the exact same problem is still occuring.

---

### Post by paperwings on 2005-10-15
[QUOTE=dickohead]I'm currently trying to install Breezy on my laptop, I successfully installed hoary, and was running it for months, but after a kernel problem i decided to format and start again.
I am getting returned with this error in Breezy's base system installation:
```

Base System Installation error The debootstrap program exited with an error (return value 1). Check /target/var/log/bootstrap.log for details.

```

But the file bootstrap.log does not exist, i tried changing my root partitions file system from Reiser to Ext3, as per some suggestions in another thread, but still have the same error, i have attempted skipping the base install only to run into more problems. I also burnt the CD at 2x speed but the exact same problem is still occuring.[/QUOTE]

Got the same problem here. I've gone through 3 different cd's, and have the same problem.

---

### Post by odie5533 on 2005-10-15
Me too :(
Just wondering: Are you guys using the ADM64 Install?

---

### Post by paperwings on 2005-10-15
no, i used the standard X86 iso. (verified with checksum)

---

### Post by odie5533 on 2005-10-15
Hmm what motherboard/cpu do you have paperwings?

---

### Post by taygan on 2005-10-15
Ah, yes, I have the same problem.

I've tried installing about a dozen times.  (MD5Sum on ISO image is fine, burned two different install CDs)  Usually it fails about 33% through the base install, although I have gotten it to base-install twice.

After reboot it always fails before everyting installs with nearly the same error:
(this is from my notes so it may not be exactly right)

```
ata1: translated ata stat/err 0x35/00 to scsi k/asc/ascq 0x4-/00/00
buffer i/o error on device sda, logical block (and the blocks change each time)
```

Ah ha! it's having a read/write failure on my SATA hard drive.  I reinstalled Warty, everything works, hoary was working (but I don't have a hoary install CD)

I've run full drive diagnostics, drive checks out okay.  Memory checks out.  Hardware seems fine.

Many other folks are having this error on USB or DVD drives.  Looks like there's a bunch of us that are failing on the HDD.  Are these all SATA drives?  

(ASUS A7V600-X motherboard, Hitachi SATA drive, Plextor CD-RW.)

I'm going to try reinstalling hoary, then upgrading to Breezy while keeping an old kernel to see if that could be the problem.

In other words, it seems that for many of us, BREEZY IS BROKE?!  (possible bugs 15552, 16901, 17496)

---

### Post by odie5533 on 2005-10-15
I don't use SATA :S
Gigabyte K8U Triton Mobo, 3200+ AMD 64 Newcastle, 120gb WD and 160gb Maxtor, AOpen DVD+R/RW drive

No similarities at all, but the same problem.

---

### Post by taygan on 2005-10-15
Has anyone with these problems on clean install tried upgrading from hoary rather than the clean install??

I'll try it, but I've got to get a Hoary install disk from a buddy, so won't be able to try it today.

---

### Post by odie5533 on 2005-10-15
Hi, I found the problem to the debootstrap error. It actually is a bad CD burn. After reading so many people with the same problem I didn't believe it, but it truely is because after burning on different media at 1x (yes, 1x. Takes a while, but its worth it :D) I am successfully running Breezy Badger.

Steps to Take to Fix the Debootstrap install error:
1. Burn at 1x
2. Try a different brand of cd media

---

### Post by dickohead on 2005-10-16
I re-downloaded the iso file due to a bad MD5, and I am using 64bit on a laptop, now i have some bad packages and modules when loading up for the system configuration... but eh - it all installed quite well!

---

### Post by dickohead on 2005-10-16
I am now successfully typing this reply to you all from my fresh install of breezy on my 64bit laptop! WOOHOO!!!

---

### Post by taygan on 2005-10-17
Umm,  it seems to be more than a bad cd..  I re-burned with varirec 0, 4x on a Plextor drive.  My CD is reading just fine.  I've got errors on the write side of things.

I reinstalled Hoary, tried a dist-upgrade, had a few problems (couldn't download the security updates and things got screwy.)  Tried it again (fresh Hoary to Breezy upgrade) got it all installed, lots of locales errors, but it installed and booted, looks pretty.


Things went well until I installed updates.  ooops..  Buffer i/o error again, on the dpkg  end of things.  So it seems that dpkg or apt-get or synaptic or something is not allowing breezy to write to my SATA hard drive.  ugh!

Tried hdparm -d1 /dev/sda, but SATA doesn't accept that.

ANY OTHER WORK-AROUND??

Is the new version of dpkg or something buggy or is it just happening then by chance?

I've downgraded back to HOARY, I'll try breezy again, but I need to try something new, other than buying a different drive (Hitachi SATA 120 gig (Deskstar??))

Is this a VIA chipset problem??  The CD seems okay..

---

### Post by bugmenot on 2005-10-18
For me the error was that my browser (firefox, gcc4) was not downloading the whole .iso image.  It was stopping at 2g due to some math error, when the dvd is actually 2.8g large.  This gave the same error.  So moral is do the md5sum.

---

### Post by dickohead on 2005-10-18
there was a DVD? Man now i feel stupid! But yes, do the MD5 and if you have errors after that, try disabling things like:
```

acpi=off nolapic noapic

```
 I'm running a 64 bit laptop, that's widescreen, so i had to type the following when booting:
```

linux vga=771 acpi=off noapic nolapic

```

---

### Post by jtuthehizzo on 2005-10-24
I'm having the SAME problem on my Athlon XP 2800 comp.  The cd was suspect but it worked fin on my roomie's laptop!  I think it might be that my hard drive had a partition burned into it-help!?

---

### Post by Samuli on 2005-10-24
I had the same debootstrap problem with Kubuntu Breezy when I used finnish language options and keyboard layout.. I got over base-install by using english language and keyboard.

---

### Post by woody7 on 2005-12-19
I have the same problem.  However, after running the CD Integrity check on the disk, I found that my CD was indeed not valid.  I burned the CD using Roxio 5 on a Win 2000 Pro box with an old 8x burner.  I burnt the ISO at the max rate, but, like an idiot, I did not check the MD5 checksum after download and after burning.

Time to waste another CD.

<sigh>

... Woody (another one)

---

### Post by Felix21685 on 2006-03-08
i was getting the same error..
for me it was that i was trying to use fat32 instead of ext3.

once i switched to ext3 and gave it some swap space..it worked flawlessly.
try that..

---

### Post by negatron on 2006-03-15
I'm getting the same error now that I'm trying to install Breezy. I've succesfully installed Warty and Debian, but Breezy just keeps complaining about the debootstrap and sometimes it complains that it can't read from the cd (although the cds pass the integrity check).

I've tried to burn the image on to a two different CD-R and three different CD-RW discs with differents speeds, I've tried to redownload the image and the md5sum has always been correct. But still Breezy won't install.

I'm getting rather frustrated on this, and I wouldn't want to change the distribution.

I even tried the solution that Samuli suggested, still with no luck. :(

---

### Post by KansasJoe on 2006-03-15
I ended up having to dl mine from a different mirror and burn to cd-r instead of cd-rw and it worked while i was previously getting the debootstrap error

---

### Post by Ran13 on 2006-04-08
I keep getting the same error as well.

I used a Plextor 12/10/32A on a Win2k Pro box and Adaptec DirectCD to burn the CD @ 1x. The downloaded ISO passed the MD5 checksum test using wxChecksums.

The install has gotten as far as selecting the kernel when it fails with this error (/blah..blah.../bootstrap.log...same as above), but no further.

The CD Integrity check passes about 1/2 the time, and, when it fails, fails on a different file almost every time, but most often in one of the kernel install .deb files.

Could it be a bad CD drive? (It doesn't seem bad when I boot from a DOS/Win bootdisk w/ generic CD drivers...I can access all directories and open files on a normal CD.???) Also, I had this machine up & running with the Live CD (using the same CD burning software/method noted above), which is another reason why this has me completely stumped. :P

The machine is an old HP Pavilion 6630 w/ a 500MHz Celeron. If I can't get this installed, I haven't decided whether to convert it to a doorstop or a boat anchor. ;)

I've got 15 years of experience with DOS/Win, but I'm a complete Linux noob. Can anyone help an ol' dog learn a new trick 'r two?

UPDATE:
Well, turns out this was caused by a bad CD_ROM drive. I replaced the Samsung SC-140 40x that came in the machine with an old Mitsumi CRMC-FX240S 24x I had layin' around and the install went perfect! :)

Back to figurin' out this new Linux thing ....  ;)

---

### Post by 999.michael on 2006-04-11
[QUOTE=odie5533]
Steps to Take to Fix the Debootstrap install error:
1. Burn at 1x
2. Try a different brand of cd media[/QUOTE]

yeah i had the same problem with the i386 installer but ill try that. however, with the cd integrity check it always works. so ill try a different cd drive aswell, that might work.

---

### Post by jfreak on 2006-04-15
yeah i have the same problem and i am using an ordered disk
i can work around some of it my checking the integrity of the cd and picking up kindof near where i left off

but,i guess the real problem then is that we all have corupt cd drives

do you think i could just clean my drive, or do i need to do something worse

also, how come i have no problem installing windows???](*,) ](*,) ](*,)

---

### Post by kchukchukchu on 2006-04-15
I have the same problem too,  with the debootstrap problem coming up either during base system install or even before then (for the same CD) even though  I checked the sum AFTER I burned the CD and the sum was correct. 

I 'm quite frustrated at the moment. Mine was an HP Pavillion 6535. 

hope you are installing successfully by now,
K

---

### Post by jfreak on 2006-04-16
yeah sometimes i get the bootstrap error before the base system.

1 possible workaround
when you get to an error, you can go back to the menu and check the cd integrity, then it will re-recognize the cd and you can restart from the last step you were on. (it this was the base system, it doesn&#8217;t save you a lot of time) but it is guaranteed that you will get at least as far as you did the previous time (i have no clue why, maybe because the files are already written)

I spent about 2 days and successfully did it with the hedgehog version, but i haven&#8217;t been able to do it with breezy yet.  I can get as far as installing the image (part of the base system) but once it fails at that, the integrity check wont re-recognize the cd.

when answering keep in mind that i am using a ordered disk (although i have tried a burned one a couple of times)

hope this information helps

---

### Post by jfreak on 2006-04-16
i think it's a hard drive problem

---

### Post by kchukchukchu on 2006-04-17
hello, jfreak,

how's it going with the install?   How did you figure out if it's a harddrive problem?

for me, I am thinking if it is a CD drive problem.  I read the ctrl-alt-f3 screen and at different places, it has cp: read error: input/output error.
(it caused "dependency problems afterwards saying that the needed packages are not installed.  somehow it got through the read error after a while.)

hope you have success with yours.. I don't know what to do with mine at the moment,
Kay

---

### Post by jfreak on 2006-04-17
yeah sometimes (on breezy only) it will make it through the "read errors"

So my theory is that they are really write errors and since  breezy extracts them right after they are copied, it looks like a read error.  So when it checks it it's messing up.

This could be easily be caused by some unexpected property of the hard drive.

I think this isnt a cd drive error becuase i can install all windows operating systems (including mistake edition) using the same cd drive; and it's not a bad burn because half of us are using pressed disks or disks burned at 1x on a TDK.

Just a theory

The only pressed copy i've tried is the hedghog version (2.01 or something) and i of course has the same error, but i just ordered the new ones so i will be interested to do some tests with them.
I'm also gona try some tests with different hard drives.

I'm gona find the awnser to this of it takes all summer.

---

### Post by microthorne on 2006-04-25
Hi,

For me the issue was having a second CD-ROM drive on the same IDE cable which is possibly dead (not showing up in auto detection after POST.)  I unplugged the second CD-ROM drive and made it past the debootstrap error.

HTH someone.
-Thorne

---

### Post by jfreak on 2006-04-27
guess what,
every computer i've tried with this problem, has the same problem with suse
](*,) :-k ...](*,)

---

### Post by GDeadHead on 2006-04-29
I had this problem untill I realized I was trying to installing Ubuntu on a fat 32 formatted hard drive.  Make sure your hard drive is formatted as ext.

---

### Post by jfreak on 2006-04-29
how do i format with ext

---

### Post by patC on 2006-05-04
same prob as everyone hear it seems.
but mine started a little different.
I burn an iso of ubunto to install onto a mac, and preformed the install perfectly with no problems. it previously had mac os9 on it. a day later some kid from work gave me a copy of mac osx and i put that os on it for a day or so, but when i tried to but ubuntu back on i got the message unable to install initrd-tools
an error was returned while trying to install the initrd-tools package onto the target system.
check /target/var/bootstrap.log

i know its not the cd because i had installed it perfectly a week ago.
its also gives some message about not being able to partition right?
No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS file system.

no solutions found on my end. all i can think is its in some kinda wrong format, but im a noob to the linux world

---

### Post by damianubuntu on 2006-05-08
I have the same debootstrap error on install on BB 5.10.  I have three machines all now coming across to ubuntu.  Two have installed fine and one remains impossible.  Following the earlier comments about Suse, I found that this machine would not install on any Debian deriv (I tried about 6 or 7), but I could get a mandriva install to go on easily.  I know the DVD is OK, and I'm using the same dvd drive on each machine, taking it around as I go :-)  I'm now going to try swapping oen of the HDDs to see if that makes any difference.

Interested to hear any more suggestions, because I've been at this for some weeks now, and I'm determined to get all three machines into Ubuntu, and not have one of them sitting in mandriva or some other distro!

---

### Post by damianubuntu on 2006-05-08
I have the same debootstrap error on install on BB 5.10.  I have three machines all now coming across to ubuntu.  Two have installed fine and one remains impossible.  Following the earlier comments about Suse, I found that this machine would not install on any Debian deriv (I tried about 6 or 7), but I could get a mandriva install to go on easily.  I know the DVD is OK, and I'm using the same dvd drive on each machine, taking it around as I go :-)  I'm now going to try swapping oen of the HDDs to see if that makes any difference.

Interested to hear any more suggestions, because I've been at this for some weeks now, and I'm determined to get all three machines into Ubuntu, and not have one of them sitting in mandriva or some other distro!

---

### Post by damianubuntu on 2006-05-08
I have the same debootstrap error on install on BB 5.10.  I have three machines all now coming across to ubuntu.  Two have installed fine and one remains impossible.  Following the earlier comments about Suse, I found that this machine would not install on any Debian deriv (I tried about 6 or 7), but I could get a mandriva install to go on easily.  I know the DVD is OK, and I'm using the same dvd drive on each machine, taking it around as I go :-)  I'm now going to try swapping oen of the HDDs to see if that makes any difference.

Interested to hear any more suggestions, because I've been at this for some weeks now, and I'm determined to get all three machines into Ubuntu, and not have one of them sitting in mandriva or some other distro!

---

### Post by damianubuntu on 2006-05-08
I have the same debootstrap error on install on BB 5.10.  I have three machines all now coming across to ubuntu.  Two have installed fine and one remains impossible.  Following the earlier comments about Suse, I found that this machine would not install on any Debian deriv (I tried about 6 or 7), but I could get a mandriva install to go on easily.  I know the DVD is OK, and I'm using the same dvd drive on each machine, taking it around as I go :-)  I'm now going to try swapping oen of the HDDs to see if that makes any difference.

Interested to hear any more suggestions, because I've been at this for some weeks now, and I'm determined to get all three machines into Ubuntu, and not have one of them sitting in mandriva or some other distro!

---

### Post by damianubuntu on 2006-05-08
whoa!!! how did that happen, I promise I clicked the post button just once, and then up came an error message from the forum.  Sorry for filling up space everyone.

how do you delete these messages?

SOMEONE DELETE ALL THESE FOR ME PLEASE!!

---

### Post by oli888 on 2006-05-19
I think I've found the solution!!!

I found that I had problems when I did not have a working OS installed, so I tried the following:

1. Download latest Knoppix CD.

2. Type "sudo knoppix-installer" (without quotation marks) into the command line, which should load an installer to install Knoppix to your hard disk.

3. After it has successfully installed, download the BB CD

4. Use the MD5 Checksum

5. Burn at 1x on a CD-R (not CD-RW)

6. Boot and try to install!

Normally I got sutck at 33% with the debootstrap error, but sometimes I didn't even get this far because my laptop crashed. It crashes a lot but this happened on every OS I've tried (Knoppix, Win 98, and XP). This time, however, I got to 80% and it crashed. I assume that it would work if it hadn't crashed, but now I have to install knoppix again....... Good luck to you and I hope it works!

When the final version is released (June 1), I will try that and see if I still get the installation error, as I have not tried the beta versions.

---

### Post by rtobyr on 2006-05-24
Has anyone checked their BIOS to see if antivirus protection is turned on? Having antivirus on in the BIOS prevents you from making changes to the boot sector.

---

### Post by jfreak on 2006-06-19
why would there be antivirus when installing an os?

---

### Post by petrus66 on 2006-06-25
I used the same installation CD on my old ide harddisk with succes.
No visual flaws seen on CD surface, media should be fine..

The only thing that has been changed on my rig is upgrading from IDE to SataII drive.

Ubuntu, or at least Grub, was losted on the fly, as I used Norton Ghost to clone the partitions from the old harddrive. Against to my all my expentations the Windows partitions cloned perfectly and are running well.

I entirely formatted old linux partitions with Partition Magic and rebooted for a fresh install...

I strongly suspect a compatibly issue with native motherboard (Lanparty nf-4) sataII support.

any suggestions?

I will try with newest Suse and maybe Solaris.

Suse did recognize my Radeon X800 at the first handshake, as with Ubuntu I had to struggle for two days as an absolute beginner to get the graphical interface up..

Second try to Ubu, as it is still feeling so "warm hearted" and fresh...

---

### Post by jfreak on 2006-07-10
ladies and gentlemen,
from further testing i have concluded that this is indeed a cd-drive error, occuring commonly on older hp and compaq cd drives

---

### Post by starpause on 2006-07-31
> **dickohead said:**
> 
I am getting returned with this error in Breezy's base system installation:
```

Base System Installation error The debootstrap program exited with an error (return value 1). Check /target/var/log/bootstrap.log for details.

```



i got this error several times trying to install kubuntu 5.10 on a thinkpad 600. my problem was a bad copy of the install cd so i followed the following steps for a sucessful install :cool: 

i re-downloaded the .iso image for the install cd on my desktop and opened it with k3b. **the download passed the k3b md5 check.** then i burned it at regular speed on the same writer, but **was sure to check the box for verifying the write**. the disc verified after burning and then smoothly installed after that.

thanks for all the advice on this thread! :KS

---

### Post by missmoondog on 2006-08-26
> **jfreak said:**
> ladies and gentlemen,
from further testing i have concluded that this is indeed a cd-drive error, occuring commonly on older hp and compaq cd drives

hmm? i'm almost tending to lean towards this thinking also.

---

### Post by skurtzberg on 2006-09-14
After experiencing this problem with dapper (oem install from dapper alternate cd) it was necessary to delete all the files that had been written to the hard drive before the error occurred.  (Obviously I'm using an existing file system without reformatting.)  Before erasing these files, the exact same error occurred even with a validated CD.  After erasing, the install proceeded normally.

I would have expected the error indications to change using a corrected CD.  It's not surprising that erasing the files is required (although it is sloppy on the part of the install program).  I was mislead for a time, thinking that the problem might not have been caused by the bad CD.

The bottom line is:  the CD was the cause, and if you are installing without creating the file system on the install root partition, delete all files (written by the installer; obviously don't delete the files that motivate the install onto an existing file system.

---

### Post by skibler on 2006-10-23
I am trying to install xubuntu-6.10-beta-alternate-i386.iso.

I am getting stuck at the same place during the Base System install:

```

Bask system Installation error
The debootstrap program exited with an error (return value 1).

Check /var/log/syslog or see virtual console 4 for the details.

```

I verified the md5 sum of the iso, and also verified the burned media using the guide here:
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

But on the machine I am trying to install on (an IBM Thinkpad R31) it fails the media check.

Is there a boot option I can enable/disable to get past this? Thanks!

---

### Post by jfreak on 2006-11-10
IT'S NOT A CD ERROR ](*,) ](*,) ](*,) 
I AM USING ORDERED PROFESSIONALLY PRESSED CDs

---

### Post by RichDoe on 2006-12-21
I was getting that error until I followed some advice given in this forum to change the file system to ext 3. Then everything worked fine. Except for my windows ubuntu dual boot, but that's not what this thread is talking about.

I'm using ordered CD's as well, but just to be safe have them do an Integrity test.
To do that, hit ESC until you reach the installation menu. Then select "check CD for integrity" or something of that nature.

---

