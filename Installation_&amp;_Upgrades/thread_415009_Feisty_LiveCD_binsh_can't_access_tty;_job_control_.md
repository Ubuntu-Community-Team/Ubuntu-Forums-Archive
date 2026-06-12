---
title: "Feisty LiveCD /bin/sh: can't access tty; job control turned off - Weird Workaround"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by klytu on 2007-04-20
Not sure if this is the correct forum to post this ...

Downloaded the new Feisty LiveCD yesterday, but the CD wouldn't boot on one of my computers. md5sum matched, CD was burned nice and slow and appears to be good - same CD boots all my other machines without difficulty. The approximate specs of the one it wouldn't boot:

Compaq Desktop, 700Mhz Celeron Processor, 300MB RAM, ESS ES1988 Allegro Sound Card, Integrated Intel 82810E DC-133 Graphics,
Accton EN-1207D Fast Ethernet Adapter, PCTel Inc HSP MicroModem 56

LiveCD boot would fail with the commonly posted error:>  /bin/sh: can't access tty; job control turned off This Compaq machine appears to be decidely hostile to Linux in general, but I was able to boot other live CDs on it including Knoppix, Damn Small Linux, and Dapper live. Tried many boot options I saw posted in the forums for the Fiesty Live CD - all failed with the same error. (Minor rant: At first it was not at all clear to me exactly WHERE or HOW  to give the boot options with this live CD.  I am no expert but I'm also far from being a NOOB with Linux/Ubuntu. If I got confused, I would bet heavily that a beginner would be also.) I removed the quiet splash boot options so I could watch and maybe see exactly where the boot process was failing. I noticed a repeated attempt to access my floppy drive just before the failed boots. There was no floppy in the drive and this seemed odd. I put in a read-only floppy containing some text files and re-booted from the Fiesty LiveCD, again removing the quiet splash boot options. Throughout the (looong) boot process, I continued to note periodic activity trying to access the floppy drive. But eventually the boot completed to the Ubuntu desktop. Confirmed I can boot the live CD on the Compaq every time this way, but fails all other ways tried. 

I'll play around with it more and post back if I figure anything else out. I think this indicates a bug somewhere in the Fiesty live CD's boot up process.

[COLOR="RoyalBlue"]**04/26/2007**[/COLOR] **After reading the MANY replies and posts in this thread so far, it's clear that the error message in the subject line can occur for MANY different specific reasons. What all of these reasons seem to have in common is that the new 2.6.20-15 kernel used by Fiesty chokes when it encounters hardware or combinations of hardware that its boot-up routines aren't coded to handle properly.  When it chokes, it almost always spits out that error message at the end. Solving your particular issue or finding a workaround for it may require a lot of time and patience, if you ever solve it all.  Many have posted solutions that worked for them and many haven't found an answer. It's probably a good idea to post your hardware and how it's connected when you add to the thread. That way if you find an answer for yourself, someone else with a similar set-up can try your solution. (I plan to edit this post with more specific hardware info later as well.) **

---

### Post by elect on 2007-04-20
me too

---

### Post by klytu on 2007-04-20
> **elect said:**
> me too

Do you mean that you also can boot by inserting a floppy?  Or do you mean that you can't boot with Feisty LiveCD and get the error below? > /bin/sh: can't access tty; job control turned off 

---

### Post by elect on 2007-04-20
> **klytu said:**
> Do you mean that you also can boot by inserting a floppy?  Or do you mean that you can't boot with Feisty LiveCD and get the error below?

Same problem, unable to boot with both versions (live&alternate) and it search in the floppy.

I think its a Controller problem..


after spoken with my friend, I will try to install ubuntu in the same hd by another computer, after that patching the kernel with some Alan cox patches then put it back and try,I will let u know

prey for me:mrgreen:

---

### Post by cogadh on 2007-04-20
Didn't work for me, all I get is a repeating error:
```
Buffer I/O error on device fd0, logical block 336
```

Followed by the standard:
```
/bin/sh: can't access tty; job control turned off
```

I've checked the floppy and it is readable from Windows and it doesn't report any sector errors. I still think we are seeing the ongoing SATA/PATA controller issues inherent to the new kernel.

---

### Post by klytu on 2007-04-20
> **elect said:**
> Same problem, unable to boot with both versions (live&alternate) and it search in the floppy.

I think its a Controller problem..


after spoken with my friend, I will try to install ubuntu in the same hd by another computer, after that patching the kernel with some Alan cox patches then put it back and try,I will let u know

prey for me:mrgreen:

If you think the floppy controller is bad, you might try disconnecting the floppy drive altogether and then try booting. In my case, I don't think there are any particular hardware problems - other LiveCDs boot without any particular difficulty, just the recent Feisty LiveCD has problems.

---

### Post by edmondt on 2007-04-20
I had to remove all removable drives connected via usb... bad stuff....

---

### Post by cogadh on 2007-04-20
> **klytu said:**
> If you think the floppy controller is bad, you might try disconnecting the floppy drive altogether and then try booting. 

Don't bother, I already did that, it doesn't change a thing. The install still looks for the floppy and throws a new error when it can't find it.

The controller problem is a known issue with the current kernel. The whole method of handling SATA/PATA/IDE controllers was changed and it is aparently still a little buggy.

---

### Post by Narf on 2007-04-20
I get the same error message ... BUT I get it after my computer decided to completely freeze in the middle of the distribution upgrade to Feisty(while generating the locales) and now it doesn't even boot!
If any of you guys can help me, I'd be very thankful.

---

### Post by elect on 2007-04-20
I get it work properly in an unfair way.... 


But that wasnt the right solution, u should search for Alan Cox kernel (-ac)

---

### Post by elect on 2007-04-20
> **klytu said:**
> If you think the floppy controller is bad, you might try disconnecting the floppy drive altogether and then try booting. .


DOne done, with no solution (i had disabled it by bios)

---

### Post by elect on 2007-04-20
> **cogadh said:**
> Didn't work for me, all I get is a repeating error:
l.

Have u already tried so? :(

---

### Post by cogadh on 2007-04-20
I'm sorry, I don't understand what you are asking.

---

### Post by elect on 2007-04-20
> **cogadh said:**
> I'm sorry, I don't understand what you are asking.

I know, sry for my english, it's not the best :D

---

### Post by cogadh on 2007-04-20
That's okay, I'm sure I don't speak/write your native language very well, so you're already better off than me.

Could you try to explain your question a little more?

---

### Post by b8zs on 2007-04-20
> **elect said:**
> DOne done, with no solution (i had disabled it by bios)

I'm at the same point as you.  I saw the FDD activity light, so I disabled it in the BIOS.  Still receiving the same error as others have posted.  However....I also see "(initramfs)" as the last output before the system locksup.

What is (initramfs)?  Is this is point where the file system is initialized into memory?

---

### Post by elect on 2007-04-20
> **cogadh said:**
> That's okay, I'm sure I don't speak/write your native language very well, so you're already better off than me.

Could you try to explain your question a little more?



It works (for me) with the beta version of 7.04,,,,,, but it shouldnt be so... I wanna get it works properly with the stable release

---

### Post by cogadh on 2007-04-20
> **b8zs said:**
> What is (initramfs)?  Is this is point where the file system is initialized into memory?

The "initramfs" is a reference to the virtual filesystem that the live CD runs in. Basically it is a virtual hard drive the runs totally in your system RAM.

---

### Post by cogadh on 2007-04-20
> **elect said:**
> It works (for me) with the beta version of 7.04,,,,,, but it shouldnt be so... I wanna get it works properly with the stable release
 If you were able to run the beta and you have been updating it all along, then you are already running the stable release.

---

### Post by nkp_20 on 2007-04-20
Quick solution to try guys:

When booting with livecd (Feisty 7.04) you could just try the option that says "Boot with Driver CD", but just keep the regular livecd in the drive and press enter both times when prompted to do so. This worked for me, so you guys may as well try it.

---

### Post by elect on 2007-04-20
> **cogadh said:**
> If you were able to run the beta and you have been updating it all along, then you are already running the stable release.

That was the problem, stil as i use 2.6.20-12 it works, but if i choose at the boot the new updated kernel 2.6.20-15 it hangs up

---

### Post by Datalanche on 2007-04-20
Fascinating. I just did a search for this tty error, and I had the opposite problem as you guys. I got the error a few times, but realized I still had a floppy in the drive. Took it out and now the Kubuntu LiveCD appears to be working. Hopefully now I can re-install (the upgrade bombed bigtime).

---

### Post by petermck on 2007-04-21
Hi
I just tried to do the upgrade asn suggested using update-manager online and it got as far as asking me if I wanted to keep my 'php.ini' file, which I chose to, and now it won't boot and I get the came error as yoy guys.
bin/sh: can't access tty; job control turned off and it drops me to a some kind of initramfs shell.
I am loathed to reinstall from scratch. Has anyone got any suggestions on what I can do to fix this?

---

### Post by elect on 2007-04-21
> **Datalanche said:**
> Fascinating. I just did a search for this tty error, and I had the opposite problem as you guys. I got the error a few times, but realized I still had a floppy in the drive. Took it out and now the Kubuntu LiveCD appears to be working. Hopefully now I can re-install (the upgrade bombed bigtime).



Kubuntu Live 7.04?

With the normal Ubuntu no success?:( 


With Ubuntu dvd version maeby it can works, some1 has already tried?

---

### Post by karellen on 2007-04-21
I get the same message, but not when I try to boot the livecd (which worked fine for me) but after I just upgraded to feisty and I select to boot the new 2.6.20 kernel. No problems whatsoever with the old 2.6.17 kernel, feisty boots ok with the latter...
:confused: pretty annoying stuff, even though it is not a critical one as I have other kernel images to rely on

---

### Post by klytu on 2007-04-21
> **nkp_20 said:**
> Quick solution to try guys:

When booting with livecd (Feisty 7.04) you could just try the option that says "Boot with Driver CD", but just keep the regular livecd in the drive and press enter both times when prompted to do so. This worked for me, so you guys may as well try it.

This also worked for me. Thanks for posting it!

---

### Post by elect on 2007-04-21
> **klytu said:**
> This also worked for me. Thanks for posting it!

It doenst work for me, i get this error

floppy0: probe failed

---

### Post by mbmccormick on 2007-04-21
Thank you so much! I've been looking everywhere for a workaround to this problem and I finally found one that worked!

I placed a floppy disk I had laying around in the floppy drive, rebooted (to CDROM first), and I was able to get to the desktop environment...

---

### Post by strikeback03 on 2007-04-21
my computer has never had a floppy drive.  no IDE drives either.  Still get the error.

---

### Post by cogadh on 2007-04-21
I just found a solution for my version of this problem. I disconnected my CD-ROM drive (it was extra anyway) and booted from my Lightscribe DVD-RW drive. It never even looked at the floppy drive and booted right into the desktop. I'm actually typing this from the live CD while Feisty is installing!

---

### Post by bucaneer on 2007-04-21
Same problem here. No floppy drive, no extra CD-ROM or anything (using PATA DVD-RW), no USB devices, single SATA HDD. MoBo: MSI P965,  CPU: C2D E6300, 2x512 RAM, video: X1950pro, audio: SB Audigy, if any of these matter. 'Driver CD' thing didn't work.
Help?

---

### Post by joehack on 2007-04-21
For a brief moment, I thought that booting with VGA console works. But the problem keeps coming and going.:mad: 

Jochen

---

### Post by elect on 2007-04-21
> **cogadh said:**
> I just found a solution for my version of this problem.  booted from my Lightscribe DVD-RW drive.

What is it? An external unit?

---

### Post by strikeback03 on 2007-04-21
I only have one optical drive, so I can't unplug it.

---

### Post by cogadh on 2007-04-22
> **elect said:**
> What is it? An external unit?
 It was an internal secondary drive, now since it works so well, it's become my primary drive (I completely removed the other drive that was the source of the problem). It is a Samsung SH-S182M DVD-RW Lightscribe drive.

Based on my experience and what I have read of others, I believe the problem is some type of conflict/incompatibility with certain CD/DVD drives and the SATA/PATA "drivers" in the current kernel. If you can swap out the drive, I recommend trying it.

---

### Post by elect on 2007-04-22
> **cogadh said:**
> It was an internal secondary drive, now since it works so well, it's become my primary drive (I completely removed the other drive that was the source of the problem). It is a Samsung SH-S182M DVD-RW Lightscribe drive.

Based on my experience and what I have read of others, I believe the problem is some type of conflict/incompatibility with certain CD/DVD drives and the SATA/PATA "drivers" in the current kernel. If you can swap out the drive, I recommend trying it.



I can use other CD/DVD drivers, but I think the problem is the HD, Ubuntu cant find it, i suppost some problems with the controller IDE

---

### Post by khalil on 2007-04-22
i had this problem then i swapped my iomega CD burner for my NEC DVD burner and it installed fine.

so it might be a prolem with some optical drives.

---

### Post by shockuk on 2007-04-22
Same error...

All my drives are IDE, and my motherboard doesn't have SATA/PATA support.

I don't have a floppy drive (probably haven't used one since 1999 :)), and floppy drive support is turned off in BIOS.

 I "upgraded" from Edgy using the upgrade manager and received this error. Couldn't be bothered to faff about looking for ways to fix it, and my computer could do with a fresh install, so I popped in my Feisty live CD which booted fine. Performed a fresh install, and when booting off hard disk I still received this error.

Computer has been liking Ubuntu sofar, and has run Dapper and Edgy just fine.

I hope a proper fix comes very soon as obviously I can't use Feisty.

For now I've got a *gulp* Windows XP cd sat looking at me on my desk which I can see entering a DVD drive soon...

---

### Post by maffoo on 2007-04-22
I get this same error. I have a Via Epia-EX mobo with no floppy controller, so I can't try a floppy. I'm booting from a SATA DVD writer, the only other drive is the internal SATA hard drive. At first I also had a CF card on the IDE port, I've removed this but still get the same error. The driver CD option doesn't work either.

I'm currently trying to boot the Xubuntu Live CD, I haven't tried the standard Ubuntu CD, but I will once I'm finished downloading it.

---

### Post by jpyanowski on 2007-04-22
After reading and rereading this thread I'll now add my note. I'm getting the same error message when I try to boot the live cd. I used the workaround and it worked!! \\:D/ \\:D/ Happy dance. I went and tried to install and it said my IDE hard drive was a SATA. :shock:  Not good and no install. So I will sit on the sidelines watching and reading and waiting for an answer.:popcorn:

---

### Post by shockuk on 2007-04-22
I found out that aswell as my machine, the same thing has happened on a mates' computer AND my brother's computer.

This seems to be a VERY common occurrence in my eyes, and looking at launchpad there are quite a few bugs filed with the same symptoms but different causes (and different workarounds). Iv'e spent about 2 hours trying different workarounds to no avail, and have finally given up.

I'm probably going to go back to Edgy. 

I feel that Feisty shouldn't of been released because it's clearly got major problems, although I do realise that it is important to stick to the strict release schedule.

---

### Post by bucaneer on 2007-04-22
I guess Linux hates my PC. I get this error in both 6.06 and 7.04; 5.04 and Knoppix 3.8 also refuse to boot (I didn't expect them to work anyway). I guess that my DVD-RW is causing the problem, since the solutions are optical drive related (and 5.04 couldn't recognize it).

---

### Post by cogadh on 2007-04-22
> **jpyanowski said:**
> After reading and rereading this thread I'll now add my note. I'm getting the same error message when I try to boot the live cd. I used the workaround and it worked!! \\:D/ \\:D/ Happy dance. I went and tried to install and it said my IDE hard drive was a SATA. :shock:  Not good and no install. So I will sit on the sidelines watching and reading and waiting for an answer.:popcorn:

If you drive was detected as "sda" instead of "hda", that is not a problem. SDD's are not SATA drives, they are SCSI drives, however, the new kernel also views IDE/PATA drives as SCSI now, so instead of the usual hda, hdb, etc., everything will be sda, sdb, etc. The drives will still work fine, it's just a change in the naming convention.

Side note to **shockuk**:
If you have IDE drives, then your mobo has PATA support. PATA stands for Parallel Advanced Technology Attachment, as opposed to SATA, which means Serial Advanced Technology Attachment. PATA is the new/current standard acronym for IDE (Integrated Drive Electronics) devices.

---

### Post by rcbrush99 on 2007-04-22
I am experiencing the same problem on a relatively new Intel Core2Duo system built from scratch.  I am writing this via the Ubuntu Live CD right now though.  The fix for me was to place a blank, formatted floppy disk in the system.

BTW... Installed first try on my 5 year old system.

---

### Post by Mr.Clark on 2007-04-22
> **rcbrush99 said:**
> I am experiencing the same problem on a relatively new Intel Core2Duo system built from scratch.  I am writing this via the Ubuntu Live CD right now though.  The fix for me was to place a blank, formatted floppy disk in the system.

BTW... Installed first try on my 5 year old system.

So it's not likely to have SATA support then? ;)

I think that Feisty does seem to have problems installing onto SATA. It went onto my Tablet PC with no issues, but my father has a Shuttle SD32G2 and it gives the error 

```
/bin/sh: can't access tty: job control turned off
``` every time he installs and tries to boot (the live CD works fine).

I suspect all we need to do is tweak the installer so that it puts the SATA drivers on at the same time, but damned if I know how to do that...

---

### Post by rcbrush99 on 2007-04-22
> **Mr.Clark said:**
> So it's not likely to have SATA support then? ;)



Correct, older system is not SATA.

---

### Post by ijn on 2007-04-22
hey guys here this... this is insane..
I had feisty beta for some 2 weeks. to me it was the most adorable os. yesterday I thought to get the final release 7.04. download the cd, burned it with nero, and reboot. after the logo screen and some noises into the cd+rw it stops on a black screen and the only thing u can do is ctrl+alt+canc. that's all. hi hi hi Smiley I spend the whole Sunday tried to install kubuntu without success. and believe me,,, I burned some other ubuntu /kubuntu different versions but none of them worked out. this is ridiculous because I did the install thing... some 30 times with the old feisty beta. at this point please someone tell me that it's me who goes wrong or my laptop config that wont work, but don't tell me that canonical is delivering a cd/dvd without a boot session...please help:(

ok it's me again..
I have a dell inspiron 6400/1505. 2ghz 2duo, 1gb ram ati x1300, dell wireless draft 802.11n and bluetooth. bios version A14 updated today.

when I was beautifully in feisty beta I followed the guide posted above for ati+glx+beryl and ect... and I was interested making beryl work. from all the guides and howto's this one was the one that worked. didn't tried wireless though... but if you have probs with ati Xseries just follow the wiki howto install fglrx ati proprietary driver. it should work on almost every dell 6400.

---

### Post by Narf on 2007-04-23
> **Narf said:**
> I get the same error message ... BUT I get it after my computer decided to completely freeze in the middle of the distribution upgrade to Feisty(while generating the locales) and now it doesn't even boot!
If any of you guys can help me, I'd be very thankful.

Thanks to some guy from the IRC channel on freenode I finished the upgrade:

1. Boot from a live cd.
2. mount /dev/hda1 /mnt/
3. chroot /mnt/ bash
4. dpkg --configure -a

Though, the machine crashed a few more times while generating locales - there's probably something wrong with them.

---

### Post by elect on 2007-04-23
> **ijn said:**
> hey guys here this... this is insane..
I had feisty beta for some 2 weeks. to me it was the most adorable os. yesterday I thought to get the final release 7.04. download the cd, burned it with nero, and reboot. after the logo screen and some noises into the cd+rw it stops on a black screen and the only thing u can do is ctrl+alt+canc. that's all. hi hi hi Smiley I spend the whole Sunday tried to install kubuntu without success. and believe me,,, I burned some other ubuntu /kubuntu different versions but none of them worked out. this is ridiculous because I did the install thing... some 30 times with the old feisty beta. at this point please someone tell me that it's me who goes wrong or my laptop config that wont work, but don't tell me that canonical is delivering a cd/dvd without a boot session...please 

I had the same story, but i have a Asus P4GD1, i suppost problems with controller IDE, Ubuntu doesnt see the hd and then go to floppy....

But with the beta version it worked, i wondered....:confused:

---

### Post by silverbullet007 on 2007-04-23
I'll add myself to this ever-growing list of folks with the tty error.

I'm ran 6.10 perfectly fine on an HP e-pc 42 Small form factor.  No floppy and PATA.

I've read ever post I could find on this error and I get the feeling it's all with that change in how Feisty detects the IDE controller.  Am I wrong?

DEVS---- Any guesstimate on a fix?

*EDIT*  I was able to successfully upgrade this same machine via Update Manager.  But I've done so much with regards to ndiswrapper and wpa supplicant trying to get WPA support to recognize the Belkin USB adapter I have that I decided to try the cd....so I KNOW it's a problem with the ISO image.

---

### Post by hal8000 on 2007-04-23
After a permanent install of Feisty 7.04 on reboot my system halts at "waiting for root file system"... after about 7 minutes booting continues and eventually halts at /bin/sh: cant acces tty;job control turned off.

The feisty live cd works ok, and as has been mentioned already I believe that kernel 2.6.20 bug is the problem here.

One solution (only to those who have multi boot linux systems) is to boot into an alternate linux system and copy another systems kernel and /lib/modules into the Feisty system. I have booted Feisty using 2.6.18 from Pardus Linux and the system works. On first boot it is necessart to run depmod -aev to recreate the kernel modules, but I am currently going to try a 2.6.20.7 kernel from kernel.org

My system is Asus  P4P800, Maxtor 160G UDMA,  , 1 floppy drive, 1 LS120,  Sony CDRW and Philips DVDW.
Booting with a blank disk in the FD or the live feisty CD does not resolve the problem for me, I have not tried Alan Cox's kernel patch, but as I cant boot with 2.6.20 , I will not be able to patch anyway.

If the Feisty beta disk was ok, why make kernel changes on the final release version?

---

### Post by dannyboy79 on 2007-04-23
is your maxtor a sata disk? i can almost guarentee they didn't make changes to the kernel. why would think this is a kernel issue. I am sure it has to do with the system not being able to read your system files stored on your sata disk. please tell me what kind of hard drive your system is installed on.

---

### Post by dannyboy79 on 2007-04-23
add libata to /etc/modules. also if you have a sata disk, add the appropriate sata module to this file as well. these modules will be loaded upon boot and hopefully fix the issue.

---

### Post by dannyboy79 on 2007-04-23
> **shockuk said:**
> Same error...

All my drives are IDE, and my motherboard doesn't have SATA/PATA support.

I don't have a floppy drive (probably haven't used one since 1999 :)), and floppy drive support is turned off in BIOS.

 I "upgraded" from Edgy using the upgrade manager and received this error. Couldn't be bothered to faff about looking for ways to fix it, and my computer could do with a fresh install, so I popped in my Feisty live CD which booted fine. Performed a fresh install, and when booting off hard disk I still received this error.

Computer has been liking Ubuntu sofar, and has run Dapper and Edgy just fine.

I hope a proper fix comes very soon as obviously I can't use Feisty.

For now I've got a *gulp* Windows XP cd sat looking at me on my desk which I can see entering a DVD drive soon...


you guys can all try to install from an iso image instead if you'd like to try that. check it out, this is the only way I could get Xubuntu Edgy installed on an ancient box that had a 24x cdrom which I thought was the issue.  


[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by gschuck on 2007-04-24
I am a Linux newbie and figured that Ubuntu 7.04 would be a good choice to start with.  I am having the same BusyBox "/bin/sh: can't access tty; job control turned off" message, but I am getting it when booting from the Desktop install CD, as the install process is getting started.  Nothing has even started to install yet.

I did try the Server CD, and that one will install without any problem.  Of course, when it finished and the system rebooted I had no idea what to do, but it was up and running.  I then used a program called KillDisk to wipe the drive clean before trying the Desktop version install again.  Still got the same message.

The system I am using is an old Dell Precision Workstation 410 with a PIII 450Mhz processor, 384MB RAM, a 9.5GB SCSI drive, and a SCSI CD ROM.  The hard drive and CD ROM are on separate Apaptec AIC-78xx controllers.  The floppy that is in the system is not functional, so I disabled it in the BIOS, which did not make any difference on the BusyBix error message.

Is the consensus that the problem is related to the way the CD is set up?  If not, can anyone throw a newbie a bone on what to try to get around this issue?  I would truly appreciate it.

Thanks.

---

### Post by markoloka on 2007-04-24
No feisty, no fun.
I'm also part of growing members who get: can't access tty;...

Here's my home pc specs: Abit IB9, Sata2 WD 250gb, D915, Kingston Dual 667 1gb, Samsung Dvdr...

Tried: Desktop & Alternate... both md5 checked burnt slow as my laptop can burn (4x and this is my work pc). 
Desktop: tries to access floppy as much as possible and gives crc error and freezes pc...tried also several options suggested here. Not working.
Alternate: Either: can't access tty or error in irq 19 and then pc totally freeze. Keyboard stops working etc. Not working.

I wanna do clean install. No upgrading. 
Beta is only thing i got to boot and install...then it gives error in Software install part and stops. 
I have xp in my hdd already and it works fine. I have used 6.06 & 6.10 on my old pc along w/ xp so dual boot is no problem but installing feisty.

---

### Post by boneymaloney on 2007-04-24
> **gschuck said:**
> I am a Linux newbie and figured that Ubuntu 7.04 would be a good choice to start with.  I am having the same BusyBox "/bin/sh: can't access tty; job control turned off" message, but I am getting it when booting from the Desktop install CD, as the install process is getting started.  Nothing has even started to install yet.

ditto on all points, I even get the message when I try the 'check install CD for defects' option. I'm trying this on an old P3 laptop with a PCMCIA-connected external cdrom drive, no floppy. I'm very keen to get this answered, seems to be a fairly common issue...  experts?

cheers.

---

### Post by dannyboy79 on 2007-04-24
ah, try to read the 3 previous posts I made. if you've already tried that then disregard but by your post, it appears as though you haven't tried them yet. As far as installing from an iso, that works no matter what cause I've done it.

---

### Post by boneymaloney on 2007-04-24
jesus, I tried reading your .iso solution via the link provided - try to get in your head that Feisty has been heavily promoted as new and sexy and just right for linux noobs. That trainwreck of a post is, while well-intentioned and doubtless technically accurate, the reason the vast majority are too scared to tackle linux.

Good luck for this one, I'll try again in six months.

cheers.

---

### Post by buzzbeebara on 2007-04-24
> **mbmccormick said:**
> Thank you so much! I've been looking everywhere for a workaround to this problem and I finally found one that worked!


I placed a floppy disk I had laying around in the floppy drive, rebooted (to CDROM first), and I was able to get to the desktop environment...

Having same issues as everyone here. Thank you for this post.

I did this and it worked. I put Feisty Fawn live cd in tray, powered on pc. when it got to the install menu, i put a blank floppy in floppy slot, then chose to "start or install" ubuntu. after awhile i got the live CD desktop. I then started the install to HD, utilizing the entire HD. so far installation going well.

Now, why did this work, any guesses?

---

### Post by silverbullet007 on 2007-04-24
Somebody tell me why you need a floppy in the first place?  You didnt with 6.10...WTH could be the purpose?  I ask because many of us do not have floppy drives.

---

### Post by dannyboy79 on 2007-04-24
> **boneymaloney said:**
> jesus, I tried reading your .iso solution via the link provided - try to get in your head that Feisty has been heavily promoted as new and sexy and just right for linux noobs. That trainwreck of a post is, while well-intentioned and doubtless technically accurate, the reason the vast majority are too scared to tackle linux.

Good luck for this one, I'll try again in six months.

cheers.

what does the big man have to do with installing ubuntu from an iso? you want to convert to linux from windows but want it given it to ya on a silve platter. Yes, linux has been trying to make it easier and easier for windows converts to come to this side and as hard as the developers try to make it easy, there is just so many different hardware configurations and so many variables that it is a HUGE task. you asked for a solution to get Feisty installed on your computer and I have provided you one. You don't want to do that, then by all means that is your proagative. We'll see ya in 6 months then, as I am sure you'll be back asking questions.

---

### Post by Niomi on 2007-04-24
I'm experiencing a simular problem, the details of my situation I posted in my own thread:
[http://ubuntuforums.org/showthread.php?t=421246](http://ubuntuforums.org/showthread.php?t=421246)

I apologize if I stepped on any toes by starting this thread. Originally I thought the posters in this thread were talking about just the LiveCD, but I'm not sure. There was at least one person who described their PC locking up in the middle of an upgrade which resembles what happened to me (X crashed in the middle of upgrade, I did a dist-upgrade in TTY)

---

### Post by words1 on 2007-04-24
I just did a clean install of 7.04 on an elderly Dell 2300 with IDE drives.  No problem whatsoever.  On a Dell 4700 with Sata drives, I get the "can't access tty" business, can't even run the live CD.  There is no exotic hardware involved.  Target drive is a Western Digital 80gb.

It is clearly something to do with SATA drives, judging from my experience and the preceding thread(s).

My question is -- how is this going to be fixed?  It can't be fixed with an update if people can't install the system in the first place.  Will they release/post a corrected version of 7.04 on the net?  How can they let that version be downloaded when it's clear that thousands of people will not be able to install it?

I guess what I'm asking is:  Is anyone listening?  I know bug reports have been filed, but this is not a little bug -- it's a huge screw-up.  I don't want a "work-around" -- I want it to "work," period.

---

### Post by klytu on 2007-04-24
FYI, there is another thread about this in the beginners forum [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=415041"). Probably many more will surface until the issue is resolved.

---

### Post by silverbullet007 on 2007-04-24
No Words1, this is no just a bug against SATA drives... my HP SFF uses plain old PATA.  Same problem.

It sure would be nice for some dev or mod to post in these long threads that obviously involve alot of people to say their working on it, or the problem is acknowledged...something so we all dont feel like we're just spinning our wheels.

---

### Post by markoloka on 2007-04-24
BTW...
I tried Knoppix 5.1 (2007-01-04)
and it works fine so problem is somewhere in new ubuntu. or kernel. 
I have 1 sata2 hdd and it seems to look for Pata drives. Is that correct?

---

### Post by wlamia on 2007-04-24
I used the recommended procedure using the Upgrade Manager as documented here: 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

but it restarts into BusyBox as others have noted. This also happened when I tried the Dapper -> Edgy upgrade. Re-installing from the CD works.

Upgrading really must be improved for Ubuntu to be acceptable over the long run. I am just experimenting now. It is not just a matter of preserving /home. People have different optional software installed, and keeping track of what needs re-installing is a major headache. If the best way is to re-install from scratch, there has to be a better way to restore the configuration than doing it manually.

---

### Post by dannyboy79 on 2007-04-24
OK, to narrow this down for the developers, we really need to start understanding why this is happening and what is the same between everyone's hardware. Can people start posting main parts of their systems, ie:
lspci output
32bit or 64bit CPU (also which version of Feisty)
Sata or Pata (all hard drives not just the one you're installing to. it could be choking on a hard drive in your system)
Video Card
Devices plugged in during install (ie, usb, extra pci card, etc etc)
DVD/CD-ROM's (maybe speeds?)
ANything else that can be pertinent which could affect the install and or LiveCD.

This way the developers can troubleshoot this with some knowledge. I am really shocked that people don't remember this happening with Edgy and or Dapper. This is how I solved it for Edgy.  

[http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688)

post number 5.

---

### Post by dannyboy79 on 2007-04-24
> **wlamia said:**
> I used the recommended procedure using the Upgrade Manager as documented here: 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

but it restarts into BusyBox as others have noted. This also happened when I tried the Dapper -> Edgy upgrade. Re-installing from the CD works.

Upgrading really must be improved for Ubuntu to be acceptable over the long run. I am just experimenting now. It is not just a matter of preserving /home. People have different optional software installed, and keeping track of what needs re-installing is a major headache. If the best way is to re-install from scratch, there has to be a better way to restore the configuration than doing it manually.

there is, you simply extract all your installed pacakges before you do a fresh install, then when you get your new system running, you use aptitude to install all the packages from that list.

here ya go

dpkg --get-selections | grep -v deinstall > ubuntu-files; cat ubuntu-files| mailx -s &#8220;ubuntu-files&#8221; [email]my.mail@my.addr[/email]ess

and then, after you install the new system fresh!!! you would always do this first

sudo aptitude update && sudo aptitude upgrade

to restore all those packages:

dpkg --set-selections < ubuntu-files

Now you&#8217;ve told your system what it needs to install, so let&#8217;s install it all.

sudo dselect

This will open up a dselect session. Type &#8216;I&#8216; and allow dselect to install of the the packages listed in your ubuntu-files document. When it&#8217;s finished, type &#8216;Q&#8216; and hit the ENTER key to exit dselect.

(I give full credit to arsgeek.com)

---

### Post by Niomi on 2007-04-24
What is the difference between SATA and other drives, and how can I find out if my HDD is either?
I haven't paid much attention to what HDD I buy, I just try to get the most space for the cheapest price. In addition I haven't bought a new drive in a couple of years. So I probably have the sort of drive which is known for being slow, cheap and common.

Seeing as the cables of my hard drive look like this: [http://en.wikipedia.org/wiki/Image:Ata_20070127_002.jpg](http://en.wikipedia.org/wiki/Image:Ata_20070127_002.jpg)
I'm guessing that it's a PATA drive.

---

### Post by dannyboy79 on 2007-04-24
it's most likely a pata drive. Which is Parellel-ATA. This kind has a very large wide connector. The newer hard drives are SATA, which is Serial-ATA. This has a very small data connector and even a different looking power connector although some sata drives have both a sata power connector port as well as the old molex style power connector along with the data connection port.

SATA drives have a theoretical transfer rate of 1.5gb/sec (that was the orinigal Sata standard)

Newer SATA Drives have a theoretical transfer rate of 3.0gb/sec (this is also known as SATA II)

PATA drives transfer way slower depending whether they are 133, 100 or 66 ATA. (these are all megabytes per second? check this out [http://www.webopedia.com/TERM/A/ATA.html](http://www.webopedia.com/TERM/A/ATA.html))

---

### Post by medya on 2007-04-24
check out [this post]("http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html")

---

### Post by dannyboy79 on 2007-04-24
why link to it, just post it man!!!

HERE YA GO EVERYONE, THIS SOLUTION HAS WORKED FOR A FEW PEOPLE AND LOOKS PROMISING:

many people like me have faced a "can't acess tty" error in Feisty Fawn Live CD while trying to boot from live CD , the exact error is :


/bin/sh: can't access tty; job control turned off
I fixed the problem , I was inspired by Ben Colin's comment but I didnt do what he said , as it didnt work for many others , I fixed it in my Shewdiz-ish way .

it seems this problem is happening to those who have more than one hard disk ,
I have two Hard Disks and two disk drives (a CD-RW and a DVD-ROM) ,
I unplugged one of the hard disks and unplugged the CD-RW ,so I had one device on each IDE .
then I put the live CD in and installed the Feisty Fawn Linux .

but the problem is not fixed yet, after you are in ubuntu you should , type this in terminal :
sudo gedit /etc/initramfs-tools/modules
and then add this to the end of the file
piix
and then save the file , and now do this :
sudo update-initramfs -u

now turn off your PC , and then connect your Other Drives cables again and start ubuntu , it should work fine !

---

### Post by Mr.Clark on 2007-04-24
> **dannyboy79 said:**
> why link to it, just post it man!!!

HERE YA GO EVERYONE, THIS SOLUTION HAS WORKED FOR A FEW PEOPLE AND LOOKS PROMISING:

many people like me have faced a "can't acess tty" error in Feisty Fawn Live CD while trying to boot from live CD , the exact error is :


/bin/sh: can't access tty; job control turned off
I fixed the problem , I was inspired by Ben Colin's comment but I didnt do what he said , as it didnt work for many others , I fixed it in my Shewdiz-ish way .

it seems this problem is happening to those who have more than one hard disk ,
I have two Hard Disks and two disk drives (a CD-RW and a DVD-ROM) ,
I unplugged one of the hard disks and unplugged the CD-RW ,so I had one device on each IDE .
then I put the live CD in and installed the Feisty Fawn Linux .

but the problem is not fixed yet, after you are in ubuntu you should , type this in terminal :
sudo gedit /etc/initramfs-tools/modules
and then add this to the end of the file
piix
and then save the file , and now do this :
sudo update-initramfs -u

now turn off your PC , and then connect your Other Drives cables again and start ubuntu , it should work fine !

What does the "piix" command do?

I'm trying to get it installed on a Shuttle with one SATA hard drive and one IDE optical drive. That error comes up after booting successfully from Live CD and then installing.

Cheers :)

---

### Post by markprice81 on 2007-04-24
I found that adding pci=noapci to the boot prompt solved the problem.

Mark

---

### Post by dannyboy79 on 2007-04-24
> **Mr.Clark said:**
> What does the "piix" command do?

I'm trying to get it installed on a Shuttle with one SATA hard drive and one IDE optical drive. That error comes up after booting successfully from Live CD and then installing.

Cheers :)

are you saying that you installed successfully but then after you reboot this is what happens? if so, just mount your installed system within the liveCD, then change the file like it suggests, save the file, then umount your the partition which you mounted to access your installed system, then reboot without the liveCD in place. 


this solution can also work from the initramfs prompt I think, just edit that same file by chrooting into it just like when we had to fix the xorg.conf file when using the liveCD with ATI cards. so it would be this a the initramfs prompt:

chroot /root nano /etc/initramfs-tools/modules

and then add the

piix

to the end of the file, then save this. then exit nano using control x, then it'll ask if you want to save, type "y", then it'll ask if you want to save it as the same name, hit enter. you should now be back at the initramfs prompt.

then type in 

sudo update-initramfs -u


and then continue booting with

control d

---

### Post by dannyboy79 on 2007-04-24
there's a little bit longer of a way but you could give it a try if you really want to use feisty. you could perform the fix by creating your own liveCD with the change already implemented if the chroot doesn't work.

mount the ISO image as part of a liveCD
copy the ISO contents into a temporary directory 
the stock feisty  live CD comes with Windows installers for various free software packages like Firefox and Thunderbird; if you don't need these on your live CD, you can save over 30 MB by deleting the programs/ directory 
mount casper/filesystem.squashfs as part of the filesystem 
use Squashfs and compile the kernel stuff 
alternatively, Gentoo kernels seem to already have the squashfs stuff patched in 
copy the contents into a temporary directory; do this as root and with -a option for a correct copy 
make any necessary modifications to the root filesystem, in this case, add piix to that one file 
rebuild root filesystem; run as root: 'mksquashfs squashfs-root filesystem.squashfs' 
overwrite the old casper/filesystem.squashfs file with the newly created one 
build burnable, bootable ISO: 'mkisofs -o ubuntu-6.06.1-desktop-i386-custom.iso -b "isolinux/isolinux.bin" -c "isolinux/boot.cat" -no-emul-boot -boot-load-size 4 -boot-info-table -cache-inodes -r -J -l ubuntu-6.06.1-desktop-i386' 

I am guessing this would work but haven't tried it yet. I got the idea from here: [http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html](http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html)

---

### Post by dannyboy79 on 2007-04-24
Last but not least, the my last idea to get Feisty Installed if all else has failed.

You could install Feisty using debootstrap after you install it into the ramfs of a liveCD. Follow this guide but DON'T DO THE ENCRYPTION of the /root partition unless you want to of course.

[http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install](http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install)

---

### Post by silverbullet007 on 2007-04-24
I can atest that this problem is not limited to only those folks with multiple IDE devices or HDD's.  I have 1 hdd and 1 cdrom device and still get the error.  I actually stumbled across the above post last night and tried the "piix" command after entering the CLI via F1.  It's just a different way to get the same results.

But to be fair has anyone tried that "fix" and actually have it work where nothing else did?

---

### Post by jerrylamos on 2007-04-24
A bunch of us have had similar problems with Feisty.  For some detail and workarounds see:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)

In my case, trying several things, I wound up putting the CD R/W on IDE1, and the IDE hard drive on IDE2.  That requires opening the case and having 2 cables.  Presently I've got a CD ROM, CD R/W on IDE1, and two IDE hard drives on IDE2.

With a 1 gHz Celeron, 512 mb memory, and a 1280x1024 LCD performance is sparkling fast.

Not knowing the internals it seems to me the problem(s) came from the Ubuntu developers trying to handle both IDE and SATA drives with the same code.  Sure messes a lot of things up having hda1 show up as sda1 instead.  sda1 is the USB pen drive on every other Linux I've tried except Feisty.  Also the UUID reliance can be a real mess.  

I'm still running Feisty mostly though, in part because if I find problems the developers might be more interested.

Cheers, Jerry

---

### Post by elect on 2007-04-24
> **hal8000 said:**
> 
If the Feisty beta disk was ok, why make kernel changes on the final release version?

I have the same question..

---

### Post by scripted on 2007-04-24
> **dannyboy79 said:**
> why link to it, just post it man!!!

HERE YA GO EVERYONE, THIS SOLUTION HAS WORKED FOR A FEW PEOPLE AND LOOKS PROMISING:

many people like me have faced a "can't acess tty" error in Feisty Fawn Live CD while trying to boot from live CD , the exact error is :


/bin/sh: can't access tty; job control turned off
I fixed the problem , I was inspired by Ben Colin's comment but I didnt do what he said , as it didnt work for many others , I fixed it in my Shewdiz-ish way .

it seems this problem is happening to those who have more than one hard disk ,
I have two Hard Disks and two disk drives (a CD-RW and a DVD-ROM) ,
I unplugged one of the hard disks and unplugged the CD-RW ,so I had one device on each IDE .
then I put the live CD in and installed the Feisty Fawn Linux .

but the problem is not fixed yet, after you are in ubuntu you should , type this in terminal :
sudo gedit /etc/initramfs-tools/modules
and then add this to the end of the file
piix
and then save the file , and now do this :
sudo update-initramfs -u

now turn off your PC , and then connect your Other Drives cables again and start ubuntu , it should work fine !


Didnt work for me at first, but after i swap out my dvd writer with a cd writer and reinstalled, its boots fine now.

---

### Post by silverbullet007 on 2007-04-24
I guess tonight I will try swapping my 40gb hdd and regular cdrom device over to each others channels and see if that helps.  Worth a try I guess.

---

### Post by dannyboy79 on 2007-04-24
> **silverbullet007 said:**
> I can atest that this problem is not limited to only those folks with multiple IDE devices or HDD's.  I have 1 hdd and 1 cdrom device and still get the error.  I actually stumbled across the above post last night and tried the "piix" command after entering the CLI via F1.  It's just a different way to get the same results.

But to be fair has anyone tried that "fix" and actually have it work where nothing else did?
are you saying that you can get to the command line from initramfs by hitting alt-f1? if not, than what are you saying? Also, are you using a sata drive or an ide drive? also, are you using master/slave or cable select? are you using the same ide channel for both the devices? when you say you tried the piix command, it's not a command, could you clarify what you're saying? are you making sure you have all other devices out of your machine like pci cards, usb devices etc etc, making sure you only have monitor, mouse, and keyboard during install? have you tried the irq=route or irqpoll or noapic or nolapic? these options often work for people. have you tried turning on or off legacy usb device support in the bios? have you tried disconnecting any extra usb ports that may be connected to the motherboard usb headers? all these things need to be tried. I know it sucks but if you want to install feisty you'll try it as they won't be releasing another distro for 6 months.

---

### Post by ormandj on 2007-04-24
So - when will this be fixed and a new set of ISOs produced? It's affecting my Toshiba R100 laptop w/ a PCMCIA CDROM drive. I'm not interested in doing workarounds that may/may not work, in the meantime. This is very obviously a nasty bug (plenty of reports across multiple threads) with various solutions. I'm not sure why this wasn't caught before release - way to turn off potential new users.

Cheers,
David

---

### Post by jerrylamos on 2007-04-24
In my case the weird workaround was to put the CD R/W on IDE1, and use a separate cable to the IDE hard drive on IDE2.  What that's got to do with the price of eggs in China I don't know, but it works.  It even still works with two CD drives on IDE1 and two hard drives on IDE2.

Where the whole trouble came from is when Ubuntu development tried to use the same code to support both IDE and SATA.  Suddenly hda1 was now sda1, wild code UUID's show up, and crazy things fell off the wagon.  In particular USB pen drives aren't sda1 any more which is a major fowlup.

As far as I can tell from the forums any number of people running other Linux's can't run Feisty because of this.

There's some more info here with some leads to workarounds:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)

Cheers, Jerry:confused:

---

### Post by oubou68 on 2007-04-24
the only thing i had to do was to deactivate all bios boot-entries which were set to "automatic"

---

### Post by silverbullet007 on 2007-04-24
> **dannyboy79 said:**
> are you saying that you can get to the command line from initramfs by hitting alt-f1? if not, than what are you saying? Also, are you using a sata drive or an ide drive? also, are you using master/slave or cable select? are you using the same ide channel for both the devices? when you say you tried the piix command, it's not a command, could you clarify what you're saying? are you making sure you have all other devices out of your machine like pci cards, usb devices etc etc, making sure you only have monitor, mouse, and keyboard during install? have you tried the irq=route or irqpoll or noapic or nolapic? these options often work for people. have you tried turning on or off legacy usb device support in the bios? have you tried disconnecting any extra usb ports that may be connected to the motherboard usb headers? all these things need to be tried. I know it sucks but if you want to install feisty you'll try it as they won't be releasing another distro for 6 months.

Yes I can get to the CLI by hitting alt-f1 (sry I left out the alt before)

In my previous posts I indicated that I did not have SATA...only PATA, 1 hdd and 1 cdrom (not even a burner)

Most likely the same ide channel as in my previous posts I indicated this was a SFF. (Small Form Factor)

Yes I realize piix is not a command per say, but while I cannot recall the exact syntax at this time, I did try it via CLI.

Again, its a SFF, so I have no PCI slots, no usb devices other than a mouse and only 1 lcd thru the onboard video.

I havent seen the irq-related ideas until today so I havent had a chance to try yet.  Same with the legacy device support in the BIOS.  Explain how having extra USB ports plugged into the mobo headers could make a difference when they're just "physical layer" extensions of the headers themselves basically.  Since the actuala "usb hub" device is on the mobo have the small ribbon cable plugged in could make no difference whatsoever.

And lastly a fix or resolved ISO's could in no way be considered a distro release... it would not be an upgrade but rather a fix.

---

### Post by silverbullet007 on 2007-04-24
Also I posted in the beginning how the "upgrade" worked perfectly...still does in fact.  Boots correctly each time.  However this BusyBox sh1t or whatever in the h377 is actually initiating these tty errors is the real culprit...IMHO it's not Fiesty itself.

---

### Post by mpscoggins on 2007-04-24
Thanks Guys.  after a frustrating night trying to install Feisty,  reading your replys, i moved my second hard drive to secondary master and the dvd back to primary slave and it installed with no problems:) 



Thank All

---

### Post by Chamelion on 2007-04-24
Sorry I previously have posted this into the wrong threat.:oops: 

I tried to update my daughter's computer to Edubuntu Feisty from Edgy and was not able to boot anymore. Just to be on the safe side I previously had downloaded the Edubuntu Feisty Live CD.
Then I tried to do the clean install and got what a lot of you are getting.
[HTML]/bin/sh: can't access tty; job control turned off[/HTML]
That basically means that Feisty is not available for her and for a lot of other people.
I already have re installed Ubuntu Feisty twice on my computer. Both times it broke after a few hours. Different problem.
[http://ubuntuforums.org/showthread.php?p=2527806#post2527806](http://ubuntuforums.org/showthread.php?p=2527806#post2527806)
I know that I am being sneaky here, but I really would like an answer. I do love Ubuntu, but I think Feisty might have been released a bit early. 
I am new to Linux and Feisty dangles quiet a few carrots in font of people. I would have been happy to wait a bit longer for a **stable** system but as Linux is free there are other distros that might deliver what they promise.
i might install Ubuntu Feisty a third time onto my computer if I do not get any help and then possibly look towards Sabayon etc. :sad: Thank you for your help.

---

### Post by elect on 2007-04-25
> **silverbullet007 said:**
> No Words1, this is no just a bug against SATA drives... my HP SFF uses plain old PATA.  Same problem.
.

Its a problem with controllers IDE..

---

### Post by boneymaloney on 2007-04-25
> **dannyboy79 said:**
> you want to convert to linux from windows but want it given it to ya on a silve platter. Yes, linux has been trying to make it easier and easier for windows converts to come to this side and as hard as the developers try to make it easy, there is just so many different hardware configurations and so many variables that it is a HUGE task. you asked for a solution to get Feisty installed on your computer and I have provided you one. You don't want to do that, then by all means that is your proagative. We'll see ya in 6 months then, as I am sure you'll be back asking questions.

No sh!t, I want it easy as possible, just like the majority of potential switchers. If linux is going to get out of its hobbybox and into the mainstream (desktop, not server) it needs to at least install without crapping out. Is that your definition of a silver platter? Things working as they should?

---

### Post by Mr.Clark on 2007-04-25
To be fair, it's not really asking too much for someone to be able to stick a disk in, hit "Install", answer a few questions and then get to a working system, is it?

There may be some playing with Console commands afterwards, but yes, if that's what you want to call it, I'd like my installation on a silver platter.

---

### Post by elect on 2007-04-25
I get this before the same error: ATA Abnormal Status

---

### Post by dannyboy79 on 2007-04-25
> **boneymaloney said:**
> No sh!t, I want it easy as possible, just like the majority of potential switchers. If linux is going to get out of its hobbybox and into the mainstream (desktop, not server) it needs to at least install without crapping out. Is that your definition of a silver platter? Things working as they should?

My computer has no problem installing, so obviously you guys have some kind of hardware that isn't allowing the Ubuntu Live CD to work properly. If you want Feisty, I listed SEVERAL ways to get it installed. As I said, the developers have a GIGANTIC task in trying to accomodate everyone's hardware and sometimes things like this happen. IT'S FREE, tons of developers don't get paid (i'll take your word of choice) ****, they work very hard and as I said sometimes there are problems. If you don't want to try the other solutions and if you've already tried ALL the suggestions (boot options irqpoll, irq=route, noapic, nolapic) have read my thread about the issues I had with booting Ubuntu Dapper on my other machine and it still doesn't work for ya, then like I have already said. I guess you'll either have to chose another distro or wait 6 months as I don't see them releasing all new images for Fesity.

Also, there's no need to get nasty. Some hardware is more compatible with Linux that others. I haven't posted over 20 times in here because I have nothing better to do, I am trying to help you and then you get all nasty which doesn't go far when you're looking for help.

---

### Post by dannyboy79 on 2007-04-25
> **silverbullet007 said:**
> Also I posted in the beginning how the "upgrade" worked perfectly...still does in fact.  Boots correctly each time.  However this BusyBox sh1t or whatever in the h377 is actually initiating these tty errors is the real culprit...IMHO it's not Fiesty itself.

so did you try this:

type this at the busybox prompt
chroot nano /etc/initramfs-tools/modules
and then add this to the end of the file
piix
and then save the file , and now do this :
sudo update-initramfs -u
type in control d

and that should continue the install.

---

### Post by markoloka on 2007-04-25
I tried that busybox prompt...no working. My keyboard gets frozen (after 20sec) and all i can do is push reset button. 

One thing i noticed, beta works on my pc better than official release. Beta unfortunately fails on software installation part around 6%. So what changed between beta and official release concerning this topic???

---

### Post by dannyboy79 on 2007-04-25
> **markoloka said:**
> I tried that busybox prompt...no working. My keyboard gets frozen (after 20sec) and all i can do is push reset button. 

One thing i noticed, beta works on my pc better than official release. Beta unfortunately fails on software installation part around 6%. So what changed between beta and official release concerning this topic???

huh, when I had my ati issue, busybox initramfs prompt worked fine. I could chroot into the /etc/X11/xorg.conf file, edit it, save it, and continue booting. do you have any other hardware hooked up that Fesity could be choking on? Have you removed all hard drives except install one and made sure that cd-rom or dvd-rom and hard drive are on seperate ide channels and or on the same channel? have you tried all the boot options I suggested? have you tried some bios modifications? like, don't try to overclock and try to disable or enable legacy usb support etc etc.

---

### Post by ormandj on 2007-04-25
> **dannyboy79 said:**
> My computer has no problem installing, so obviously you guys have some kind of hardware that isn't allowing the Ubuntu Live CD to work properly. If you want Feisty, I listed SEVERAL ways to get it installed. As I said, the developers have a GIGANTIC task in trying to accomodate everyone's hardware and sometimes things like this happen. IT'S FREE, tons of developers don't get paid (i'll take your word of choice) ****, they work very hard and as I said sometimes there are problems. If you don't want to try the other solutions and if you've already tried ALL the suggestions (boot options irqpoll, irq=route, noapic, nolapic) have read my thread about the issues I had with booting Ubuntu Dapper on my other machine and it still doesn't work for ya, then like I have already said. I guess you'll either have to chose another distro or wait 6 months as I don't see them releasing all new images for Fesity.

Also, there's no need to get nasty. Some hardware is more compatible with Linux that others. I haven't posted over 20 times in here because I have nothing better to do, I am trying to help you and then you get all nasty which doesn't go far when you're looking for help.

Stop the rant. It's not wise. Ubuntu (previous versions) work absolutely fine for most people. This one has issues. Don't defend it blindly, that's silly.

None of your suggestions work, none at all - not for me and apparently many others. I don't have many options, either - I've got a Toshiba R100 w/ PCMCIA cd-rom drive. I can't swap drives inside my laptop - it's only got one. No, the PIIX fix didn't work, either.

Somebody goofed up somewhere, and I'm sure it will be rectified - it's just rather lacking in wisdom to release a "final" release that has this many problems for a large portion of people. For everybody posting on the forum, there's probably another dozen who don't. It's enough to spawn multiple threads, so it's a serious issue. Telling us how hard everybody works (we know) and so forth doesn't accomplish anything.

I'm sure I speak for everyone when I saw we all VERY much appreciate the effort and time the volunteer members put into Ubuntu. We just want to be able to use the fruit of their labor.

---

### Post by shockuk on 2007-04-25
> **boneymaloney said:**
> jesus, I tried reading your .iso solution via the link provided - try to get in your head that Feisty has been heavily promoted as new and sexy and just right for linux noobs. That trainwreck of a post is, while well-intentioned and doubtless technically accurate, the reason the vast majority are too scared to tackle linux.

Good luck for this one, I'll try again in six months.

cheers.

Very good point to be honest.

I have spent countless hours trying countless workarounds, and still keep receiving this error message - I think Feisty is simply not capable to run on my main (most important) system (unless I heavily modified some components of the OS).

Iv'e been using Ubuntu (Dapper and Edgy) on my desktop for around 9 months now, have had a few problems but Iv'e normally been able to fix them. This Feisty installation problem takes the biscuit. I only just today realised that I was actually more productive using Windows XP (heavily protected with a good AV and Firewall), so I'm going back. Installing XP as we speak.

I will be keeping Debian on all of my servers, it's fantastic and obviously much more economical than the M$ equivalent. Linux is definately the best choice when it comes to servers (in my eyes).

If Canonical really want to target the "average Joe's" Desktop they're gonna have to do much better than this...

---

### Post by veliro on 2007-04-25
Feisty live is working here if I only use hd's on my promise controller, when i put some disks on the onboard jmicron controller the tty message pops up. Fortunately edgy works like a charm.

It's a good point that the people working with linux distros work for free, so it would be silly to judge them too hard... But still...
I have some friends that got the same problem with Edgy too after an upgrade and a reboot. After what I have heared and read he problem is with the new kernel (2.6.20-9), and not ubuntu's fault at all... My machine's are still running on 2.6.17-11, and still working...

The good thing is that many people have this problem, so it will probably be fixed soon.

---

### Post by dannyboy79 on 2007-04-25
people could compile a new kernel using edgy or dapper or with a  patch and then remake the live cd installer per the instructions that I gave earlier if it's merely a kernel issue.

---

### Post by elect on 2007-04-25
> **ormandj said:**
>  No, the PIIX fix didn't work, either.
.

How about that way?

---

### Post by quique1hn on 2007-04-25
I have the same problem an old hp omnibook express, so it`s not new hardware... kubuntu herd 4 work without isues, y tried ubuntu and kubuntu and they fail.. It´s only have 1 hd, an 1 cdrom, and it`s not cd I have install feisty in a desktop just finr.. today a have install linux mint in the laptop. I sill want feisty.:(

---

### Post by cookiesmakemehappy on 2007-04-25
Well, I'll just jump on this bandwagon and say it won't work for me either.
I was running Edgy on my Thinkpad since I got it in February and it worked fairly well. I'd hoped Feisty would fix a few issues but so far it's been nothing but trouble. 
I've tried some of the workarounds posted here but sofar nothing has worked.  At this point I just want to be able to USE my laptop again, as all of my schoolwork is on it.  Is there a way I can go back to Edgy without losing my data?

---

### Post by Jason Weiss on 2007-04-26
I was trying to read this thread late last night. 

Can anyone tell me is someone has actually come up with a solution to this problem?

I do not want to have to reinstall everything and loose my data.

and this tread is so messy that if someone has come up with a solution you wold not be able to find it.

---

### Post by Sef on 2007-04-26
> Can anyone tell me is someone has actually come up with a solution to this problem?

Check out this post from [LinuxQuestions]("http://www.linuxquestions.org/questions/showthread.php?t=474493&page=2").  It has some solutions.

---

### Post by megadesign on 2007-04-26
Same problem here with old laptop Acer TravelMate 529. It has only one HDD, one CD and one FDD.

Workarounds failed. I tried diskette, break=top + modprobe piix, boot update CD. Nothing helps.
Last thing I'll try is alternate CD.

Ubuntu Team should fix it pretty quickly, if they want to keep users on their side... :(

---

### Post by zvacet on 2007-04-26
**megadesign** try to upgrade from alternate.
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by dannyboy79 on 2007-04-26
> **megadesign said:**
> Same problem here with old laptop Acer TravelMate 529. It has only one HDD, one CD and one FDD.

Workarounds failed. I tried diskette, break=top + modprobe piix, boot update CD. Nothing helps.
Last thing I'll try is alternate CD.

Ubuntu Team should fix it pretty quickly, if they want to keep users on their side... :(

just because you only have 1 hard drive doesn't mean that possibly the drive is being labeled incorrectly, try to use the chroot and make sure that the menu.lst kernel boot line is correct.

---

### Post by silverbullet007 on 2007-04-26
I think that is exactly one of the problems danny... we shouldnt [COLOR="Red"]have[/COLOR] to check or change that file since Edgy (and for others dapper) installed perfectly.  But those of us who like Ubu and/or hate Microshaft will try alot of different things to get it going.. this kind of problem, and the many others since Fiesty's debute will halt alot of the switchers.  It might be asking for too much but I sure wish we could find out from the dev team, the exact changes in either the ISO image, busybox, or whatever that could be a possible candidate for this issue to be happening.

---

### Post by dannyboy79 on 2007-04-26
I don't think we're asking to much for an installer that works! I have touted over and over that the developers work very hard and a lot of time for free and that it has to be a GIGANTIC task trying to accomodate ALL the different hardware but you're absolutely correct, what did they change from Edgy to Fesity that has caused this. I know they changed it so that ALL drives are recognized as sdx (x being a letter) so it's possible that's the issue? I don't have a clue what the reason is but it's rather disappointing that ALL the suggestions that I have provided are still not helping some users but then again I am sure that not everyone has been attempted. installing from debootstrap? recreate iso image? I agree that these methods shouldn't have to be done to enjoy feisty but the fact is that if you want to run feisty and the normal intstaller isn't working than there's no other way. I haven't see one comment from 1 developer yet. I know I have been informed in the past that the developers don't hang out here, I believe they only hang out in the launchpad where the bug is posted so I think I am going to go check out the bug and see what the developers have to say.

---

### Post by hoagies on 2007-04-26
Hey you guys!!!!

You must notice and be aware that Ubuntu 7.04 is coming out in the form of SCSI, or serial drives, "/sdx".  This is causing "huge" problems on my systems, which all consist of IDE drives, "/hdx".

My advice to anybody having IDE drives:  Do NOT use Ubuntu vs 7.04!!:

1.  The problems appear, because the distro believes it is designed for "serial drives".  Then all of a sudden it encounters the "40 strand ribbon cables" of the IDE drives, which is leading to problems, because it seems to have problems with interpreting "UDMA", which it can not resolve by itself, or fix

2.  The Portuguese/Brazilian Ubuntu Forums have posted a quick solution for those who have managed to install vs 7.04 on IDE drives, to convert the erroneous drives, and erroneous operations back to "/hdx".  The proposed, very quick and easy solution came from Suse, YOU ->  Some Portuguese/Brazilians are reverting back to Ubuntu vs 6.10, by overloading that distro, in order to save their "data"

3.  In my own case, on top of everything else, when investigating "can't access tty", it gives me the answer:  /dev/Console.....  I use HP Pavilion "mx50 and mx70" consoles.....  Pure Debian has always had problems with these monitors, to the point of not being able to install Debian based distros.....  And this time Ubuntu vs 7.04  claims to have a new form of Debian installer

4.  I do have a "bug report" in, but I do not know whether it will be accepted!!  For those with connections:  Please contact the Ubuntu vs  7.04 people

How Ubuntu is going to get out of this "pickle", is a "mystery" to me, Charlie Brown!!  :lolflag: 

:guitar:   signed ->  hoagies

---

### Post by dannyboy79 on 2007-04-26
> **hoagies said:**
> Hey you guys!!!!

You must notice and be aware that Ubuntu 7.04 is coming out in the form of SCSI, or serial drives, "/sdx".  This is causing "huge" problems on my systems, which all consist of IDE drives, "/hdx".

My advice to anybody having IDE drives:  Do NOT use Ubuntu vs 7.04!!:

1.  The problems appear, because the distro believes it is designed for "serial drives".  Then all of a sudden it encounters the "40 strand ribbon cables" of the IDE drives, which is leading to problems, because it seems to have problems with interpreting "UDMA", which it can not resolve by itself, or fix

2.  The Portuguese/Brazilian Ubuntu Forums have posted a quick solution for those who have managed to install vs 7.04 on IDE drives, to convert the erroneous drives, and erroneous operations back to "/hdx".  The proposed, very quick and easy solution came from Suse, YOU ->  Some Portuguese/Brazilians are reverting back to Ubuntu vs 6.10, by overloading that distro, in order to save their "data"

3.  In my own case, on top of everything else, when investigating "can't access tty", it gives me the answer:  /dev/Console.....  I use HP Pavilion "mx50 and mx70" consoles.....  Pure Debian has always had problems with these monitors, to the point of not being able to install Debian based distros.....  And this time Ubuntu vs 7.04  claims to have a new form of Debian installer

4.  I do have a "bug report" in, but I do not know whether it will be accepted!!  For those with connections:  Please contact the Ubuntu vs  7.04 people

How Ubuntu is going to get out of this "pickle", is a "mystery" to me, Charlie Brown!!  :lolflag: 

:guitar:   signed ->  hoagies

What is Ubuntu vs 7.04???? Do you mean to put "version" 7.04? Also, you start talking about a fix but don't mention how to perform the fix, this isn't very accomodating to the tons of people following this thread. Can you either post the link to the solution or the solution itself?
Also, I wonder if a 80 wire cable would be better, 40wire is so old and I can't believe people still use 40 wire. Another thing is that I don't entirely agree with your hypothesis as I ran the live cd fine on my P4P800-E Deluxe which has 2 ide cd-rom and 3 sata drives. Shouldn't I have gotten the same error as you guys due to my "ide" drives? I think it's more involved than what you say.

---

### Post by silverbullet007 on 2007-04-26
> **dannyboy79 said:**
> What is Ubuntu vs 7.04???? Do you mean to put "version" 7.04? Also, you start talking about a fix but don't mention how to perform the fix, this isn't very accomodating to the tons of people following this thread. Can you either post the link to the solution or the solution itself?
Also, I wonder if a 80 wire cable would be better, 40wire is so old and I can't believe people still use 40 wire. Another thing is that I don't entirely agree with your hypothesis as I ran the live cd fine on my P4P800-E Deluxe which has 2 ide cd-rom and 3 sata drives. Shouldn't I have gotten the same error as you guys due to my "ide" drives? I think it's more involved than what you say.

Unless by "IDE drives" he was only referring to IDE Hard Drives as opposed to cdroms.  but I agree, if the Portuguese have determined a fix please by all means post it up here.

---

### Post by silverbullet007 on 2007-04-26
I just checked my menu.lst file in /boot/grub and didnt see a line specifically called "kernel boot".  Is this the file that I could modify in the ISO to alter the hdd labels?

---

### Post by megadesign on 2007-04-27
Hi,
tomorow I wrote about INSTALLATION Ubuntu 7.04 on Acer TravelMate 529. It was not pretty clear, that
I talked about clean&first instalation, not about upgrade from 6.10 or something else ...

So, good message, installation from alternate CD passed ...
Ubuntu 7.04 is running on that laptop without problems, all hardware is right recognized.

But as I told, I think, newbies could be deterred by that problem with live/install CD.
Remember Ubuntu Bug #1  ;)

Have a nice day!

---

### Post by markoloka on 2007-04-27
On slashdot site there was on news that new kernel is released: 2.6.21
When ever this will arrive to x/k/ubuntu could someone check if this would fix this problem. 

Someone mentioned launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864) this is topic concerning our problem(s) but there's still no fix or so. 

What bothers me is information...what's going on with progress to fix this problem.

---

### Post by arcik on 2007-04-27
> **hoagies said:**
> 
You must notice and be aware that Ubuntu 7.04 is coming out in the form of SCSI, or serial drives, "/sdx".  This is causing "huge" problems on my systems, which all consist of IDE drives, "/hdx".


This really might be the problem.

However, I can boot Feisty using the Super Grub Disk ([http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)) and its option to boot Linux directly and then the SCSI sub-option.

Unfortunately, I have very little knowledge about Linux, so I don't know how to find out which settings is the Super Grub Disk using to boot Ubuntu and where to correct the standard settings coming with Feisty.

Can someone help?

---

### Post by dannyboy79 on 2007-04-27
> **arcik said:**
> This really might be the problem.

However, I can boot Feisty using the Super Grub Disk ([http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)) and its option to boot Linux directly and then the SCSI sub-option.

Unfortunately, I have very little knowledge about Linux, so I don't know how to find out which settings is the Super Grub Disk using to boot Ubuntu and where to correct the standard settings coming with Feisty.

Can someone help?

well, I am currently reviewing the sgd iso image after I mounted it to see what boot options is passed to it and I don't recall there being a specific menu option within grub that stated "boot scsi" drive. If so, can you please let me know which sub menus it's in, for example is it under advanced, is it under boot  linux, is it under misc? let me know and I see what I find and let you know. currently I am within the misc menu  and then linux option, this is what the menu.lst withint the sgd iso image looks like:

title Boot Gnu/Linux Directly
call $(grub_device)/boot/grub/choose/bus.lst
set aux_bus=$(out_bus)
set choose_title="Root filesystem"
selectfile /etc/fstab
set root_fs=/dev/$(aux_bus)$(out_linux_end)
set choose_title="Choose vmlinuz"
selectfile /boot/vmlinuz /vmlinuz
set kernel_device=$(out_device)
set kernel_file=$(out_file)
set kernel_bus=$(out_bus)
set kernel_end=$(out_linux_end)
set choose_title="Choose initrd"
selectfile /boot/initrd.img /initrd.img
# set initrd_device=$(out_device)
# set initrd_file=$(out_file)
root $(kernel_device)
kernel $(kernel_file) root=$(root_fs)
initrd $(out_device)$(out_file)
boot

So it appears that a dgs is merely parsing various files on your computer already to be able to boot into linux directly. At least for using the Misc, Linux, option within the sgd.

---

### Post by silverbullet007 on 2007-04-27
Correct me if Im wrong here but I dont see anyhting in that file that directly points to using SATA/SCSI hdd's.  bus.lst perhaps?

---

### Post by dannyboy79 on 2007-04-27
YEAP, you got it. I just figured out what the previous poster was talking about when he said that he used the scsi option. There really isn't a scsi option but I know what he was talking about because this is what the grub help tip states:

This option lets you boot Gnu/Linux.

Auto option lets you boot Gnu/Linux.
You only have to decide if your main hard disk is treated
by Linux Kernel as an ide disk (/dev/hda) or as an scsi disk
(/dev/sda). If one does not work... please try the other one.

In this part SGD makes some assumptions as the disk that
Grub/Bios calls (hd0) is the same as hda or sda.
This assumption may not be true if your disk is a primary slave
and the primary master is a cdrom. If so you will have to make do
with one of the the manual options.

You can also try manual options if Auto option doesn't work for
you for any other reason.


So it's funny that I actually posted the exact one that I needed to. That's the menu.lst that was used which was able to boot that previous posters Fesity Install. Since I am not a programmer and only been on linux for last 1 year and 3 months, I can't tell you would he would have to do in his own menu.lst to get it to boot his system without having to use sgd. Maybe just copy and paste all of it, I don't know so don't listen to me. Maybe ask the developer of SGD?

Anyway, after looking at the menu.lst files that are within the area of the disk that displays the above help text I have pasted them both below.

**This is the AUTO menu.lst**

title |====================> Automatically Boot Gnu/Linux (Help) <====================|
catis on
configfile $(grub_device)/boot/sgd/S10en/S60_advanced/S70_misc/S25_linux/auto/menu.lst
# Try to find root of the filesystem
# If vmlinuz is on: /boot/vmlinuz that means it is also the root of the filesystem
# If vmlinuz is not on: /boot/vmlinuz but in /vmlinuz we should search for /etc/fstab as the root of the filesystem.

title Boot Gnu/Linux Directly
call $(grub_device)/boot/grub/choose/bus.lst
set aux_bus=$(out_bus)
set choose_title="Root filesystem"
selectfile /etc/fstab
set root_fs=/dev/$(aux_bus)$(out_linux_end)
set choose_title="Choose vmlinuz"
selectfile /boot/vmlinuz /vmlinuz
set kernel_device=$(out_device)
set kernel_file=$(out_file)
set kernel_bus=$(out_bus)
set kernel_end=$(out_linux_end)
set choose_title="Choose initrd"
selectfile /boot/initrd.img /initrd.img
# set initrd_device=$(out_device)
# set initrd_file=$(out_file)
root $(kernel_device)
kernel $(kernel_file) root=$(root_fs)
initrd $(out_device)$(out_file)
boot


**This is the menu.lst located within the option where the root and boot are within the same partition:**
title |====================> same Root and Boot Partition (Manual) (Help) <====================|
catis on
configfile $(grub_device)/boot/sgd/S10en/S60_advanced/S70_misc/S25_linux/manualsame/menu.lst
title same Root and Boot Partition
set choose_title="Partition of Boot and Root"
call $(grub_device)/boot/grub/choose/lpartition.lst
set aux_part_boot=$(out_part)
set aux_linux_part=$(out_linux_part)

root $(aux_part_boot)
kernel /vmlinuz root=/dev/$(aux_linux_part)
initrd /initrd.img
boot

**This is the menu.lst located within the option where the root and boot are on different parititions:**
title |====================> different Root and Boot Partition (Manual) (Help) <====================|
catis on
configfile $(grub_device)/boot/sgd/S10en/S60_advanced/S70_misc/S25_linux/manualdifferent/menu.lst
title different Root and Boot Partition
set choose_title="Partition of Boot"
call $(grub_device)/boot/grub/choose/partition.lst
set aux_part_boot=$(out_part)

set choose_title="Partition of Root"
call $(grub_device)/boot/grub/choose/lpartition.lst
set aux_linux_part=$(out_linux_part)

root $(aux_part_boot)
kernel /boot/vmlinuz root=/dev/$(aux_linux_part)
initrd /boot/initrd.img
boot

GOOD LUCK. Based on a person merely entering /dev/sda instead of /dev/hda, I would say that this guy should just edit his own menu.lst and change any place that he sees hda and change it to sda cause that's all the above help  tip is stating. I wish I could be of more help. As you can see below, all his bus.lst file has in it is this:

title $(choose_title)
pause
title  IDE
set out_bus=hd
back
title SCSI
set out_bus=sd
back

---

### Post by silverbullet007 on 2007-04-27
> GOOD LUCK. Based on a person merely entering /dev/sda instead of /dev/hda, I would say that this guy should just edit his own menu.lst and change any place that he sees hda and change it to sda cause that's all the above help tip is stating. I wish I could be of more help. As you can see below, all his bus.lst file has in it is this

Maybe Im just being dense here.. I fail to see any references to either sda nor hda in the menu.lst file.  Also where on the cd is that file?  I'd like to checkout or alter my own ISO..

---

### Post by rollingcircle on 2007-04-27
I had this same error message doing a clean install of Feisty on a Shuttle SD32G2.  I solved the problem by flashing the BIOS with the latest from Shuttle.  The documentation for the latest BIOS update is "Fixed can't install Linux with Dual Core CPU".  I have no clue how this would affect the IDE controller but it worked.

---

### Post by Ipsissimus on 2007-04-27
After finding the 'modprobe piix' solution, and it not working I Finally found how to fix my Edgy to Feisty upgrade!

[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=2547102&postcount=2[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2547102&postcount=2")

Which is from this thread: [http://ubuntuforums.org/showthread.php?p=2547102#post2547102]("http://ubuntuforums.org/showthread.php?p=2547102#post2547102")

If you're still having issues, try this perhaps?

--Ipsissimus

---

### Post by dannyboy79 on 2007-04-27
> **Ipsissimus said:**
> After finding the 'modprobe piix' solution, and it not working I Finally found how to fix my Edgy to Feisty upgrade!

[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=2547102&postcount=2[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2547102&postcount=2")

Which is from this thread: [http://ubuntuforums.org/showthread.php?p=2547102#post2547102]("http://ubuntuforums.org/showthread.php?p=2547102#post2547102")

If you're still having issues, try this perhaps?

--Ipsissimus

so that's a fix for the people who did upgrades and then couldn't boot into feisty, what about people installing Feisty for the first time. This is very bad for potential new users, this could result in very bad press from people who tried converting from windows and they find they can't even get it installed. I have provided serveral different suggestions for fixes that I have read in tons of different forums but there still doesn't seem to be one that is EASY for people who are trying to install Feisty from the cd.

---

### Post by arcik on 2007-04-27
> **dannyboy79 said:**
> 
Since I am not a programmer and only been on linux for last 1 year and 3 months, I can't tell you would he would have to do in his own menu.lst to get it to boot his system without having to use sgd. Maybe just copy and paste all of it, I don't know so don't listen to me. Maybe ask the developer of SGD?

[...]

GOOD LUCK. Based on a person merely entering /dev/sda instead of /dev/hda, I would say that this guy should just edit his own menu.lst and change any place that he sees hda and change it to sda cause that's all the above help  tip is stating. I wish I could be of more help.

Thank you, dannyboy. I tried to modify the menu.lst, but it didn't work. I think this isn't the weak place (but maybe I only misunderstood what you meant). There are, in my opinion, only two possibly relevant places in the menu.lst file:

FIRST:
```

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
```I don't understand what this does.

SECOND:
```

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ff23e9a8-f55e-43e0-8847-97fdee4d3fd4
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```I quote this, because it is the only part of the file where there is an uncommented reference to a disk. I tried changing (hd0,0) to (sd0,0). It didn't help. And no wonder, because Ubuntu starts booting and only then it halts.
The last information I get from the system is the following:
```

kinit: no resume image, doing normal boot ... done
mount: mounting /dev/disk/by-uuid/ff23e9a8-f55e-43e0-8847-97fdee4d3fd4 on /root
failed: no such device
begin: running /scripts/local-bottom ...
done.
done.
begin: running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
done.
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init
```
and then the BusyBox v1.1.3 comes up telling me this:
```
/bin/sh: can't access tty; job control turned off (initramfs)
```

There must be some difference in what sgd does. What is this difference? Is there a way to find out? And what can I change and where to be able to boot just as I did with Edgy.

Hope the information I've just provided will help the more experienced Ubuntu-users to give me a tip, how to solve this problem. Thanks beforehand!

---

### Post by dannyboy79 on 2007-04-27
try changing the kernel line from a UUID to the device location if you just want to try other stuff.

**FROM:**
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ff23e9a8-f55e-43e0-8847-97fdee4d3fd4
**TO:**
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda1



also, did you see this post, it worked for him. [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

OR

from the initramfs, you could find out what devices are being found by feisty, i notice the error states, mount: mounting /dev/disk/by-uuid/ff23e9a8-f55e-43e0-8847-97fdee4d3fd4 on /root failed: no such device
which to me means that it didn't find anything at /dev/disk/by-uuid/blah blagh blah

so what if you tried to chroot into the live cd and listed the items within /dev/disks?

chroot ls -la /dev/disks/

and see wjhat happens if anything? I have only been on linux for 1.4 years and I am merely trying to use logic to solve this as I have no idea how the livecd works so if my idea sounds stupid or isn't even possible than just disregard.

---

### Post by elect on 2007-04-27
> **megadesign said:**
>  break=top + modprobe piix, 

What is it? Can u describe better this way?

---

### Post by jerrylamos on 2007-04-27
Do a search on my post "Workarounds".  "can't access tty" is launchpad bug 106864:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)
which says in part:

" Ben Collins  said on 2007-04-18:  (permalink)

The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"

For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed.

We are working on an update to fix this."

In my  case, not quite understanding Ben's instructions, I put the CD drive on IDE1 and the IDE hard drive on IDE2.  Voila.

Cheers, Jerry

---

### Post by hbjason on 2007-04-28
If you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
  o Select [COLOR=Blue]F6[/COLOR] for more options
  o Add the following option to the beginning of the options list:
        [COLOR=Blue]break=top
[/COLOR]   o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
        [COLOR=Blue]modprobe piix
        exit

[/COLOR] You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
  o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
    -- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
  o When the install is complete do not reboot -- stay in the LiveCD
  o Open a terminal ([COLOR=Blue]Applications->Accessories->Terminal[/COLOR])
     o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

        [COLOR=Blue]mkdir target
        sudo mount /dev/hda1 target[/COLOR]

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: [COLOR=Blue]
sudo mount /dev/hda2 target/boot

[/COLOR]         [COLOR=Blue]sudo chroot target

[/COLOR]   o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
  o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
    -- you should do this with your favorite unix editor; or simply type the command:
        [COLOR=Blue]echo piix >> /etc/initramfs-tools/modules[/COLOR]
  o After modifying the file you must update the system with the command
              [COLOR=Blue]update-initramfs -u[/COLOR]
  o When complete, type '[COLOR=Blue]exit[/COLOR]' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by strikeback03 on 2007-04-29
So I finally had some time to try a few of the suggestions.  For me adding "all_generic_ide" to the line before booting from the LiveCD allowed me to boot.  Don't remember if that tip was in this thread or not.  Guessing from what scrolled by with quiet and splash turned off, the system was complaining about my built in card reader.

Unfortunately, Feisty (from the LiveCD) does not recognize my wireless card (Realtek RTL 8185 chipset).  Anywhere to find out if support for this got removed between Edgy and Feisty?

---

### Post by arcik on 2007-04-29
> **dannyboy79 said:**
> try changing the kernel line from a UUID to the device location if you just want to try other stuff.

Oh no! It really was THIS simple for me!! I couldn't believe my eyes. Thanks for your help, dannyboy. This is the relevant section of my current menu.lst (note that I put sda1 and not hda1):

```

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Hope this works for others, too!

---

### Post by pinoytechie on 2007-04-29
I've had the same error when I tried to load LiveCD files from a NTFS partition.

[http://noyph.phpnet.us/]("http://noyph.phpnet.us/")

---

### Post by dannyboy79 on 2007-04-30
> **arcik said:**
> Oh no! It really was THIS simple for me!! I couldn't believe my eyes. Thanks for your help, dannyboy. This is the relevant section of my current menu.lst (note that I put sda1 and not hda1):

```

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Hope this works for others, too!

I love it when a suggestion works. I am very new to linux (1.3 years) and I most of the time just try to use my logic based on what the errors are. 

Glad I was able to help!

---

### Post by dannyboy79 on 2007-04-30
> **pinoytechie said:**
> I've had the same error when I tried to load LiveCD files from a NTFS partition.

[http://noyph.phpnet.us/]("http://noyph.phpnet.us/")


didn't you notice that the instructions state that you need a fat32 partition? anyway, did you try the fixes stated above? if so, did they work?

---

### Post by scubastevegk on 2007-04-30
What's interesting/irritating to me is that the 32-bit Feisty Desktop LiveCD works perfectly on my hardware, but the 64-bit is giving me the tty error.  Before I got on the forums, I assumed I was going to discover that this was only an AMD64 issue, but I was surprised to learn that it wasn't.  Anyway - here's my full system specs in case anybody wants to try to draw any commonalities from them.

Pentium Extreme Edition 955 CPU (3.46 GHz Dual Core w/ Hyper-Threading)
4 GB DDR2 PC2-5300 RAM
Asus P5N32-SLI Deluxe Motherboard
Two 256 MB NVIDIA GeForce 7600GT PCI-Express Video Cards in SLi configuration
400 GB Western Digital SATAII Hard Drive
Samsung SATA DVD+/-RW w/ LightScribe

I added 2 GB of RAM today to get the 4 GB, which is why I want to move to the AMD64 build of Feisty - can't leverage the RAM without it.  Just to be safe, I went back and double checked and the x86 LiveCD still boots without a hitch - so in my case, at least, this is only an AMD64 issue.

---

### Post by dannyboy79 on 2007-05-01
> **scubastevegk said:**
> What's interesting/irritating to me is that the 32-bit Feisty Desktop LiveCD works perfectly on my hardware, but the 64-bit is giving me the tty error.  Before I got on the forums, I assumed I was going to discover that this was only an AMD64 issue, but I was surprised to learn that it wasn't.  Anyway - here's my full system specs in case anybody wants to try to draw any commonalities from them.

Pentium Extreme Edition 955 CPU (3.46 GHz Dual Core w/ Hyper-Threading)
4 GB DDR2 PC2-5300 RAM
Asus P5N32-SLI Deluxe Motherboard
Two 256 MB NVIDIA GeForce 7600GT PCI-Express Video Cards in SLi configuration
400 GB Western Digital SATAII Hard Drive
Samsung SATA DVD+/-RW w/ LightScribe

I added 2 GB of RAM today to get the 4 GB, which is why I want to move to the AMD64 build of Feisty - can't leverage the RAM without it.  Just to be safe, I went back and double checked and the x86 LiveCD still boots without a hitch - so in my case, at least, this is only an AMD64 issue.

i don't think you need to go to 64bit to use all your 4gb of ram. according to here ([http://discuss.extremetech.com/forums/1004377255/ShowPost.aspx](http://discuss.extremetech.com/forums/1004377255/ShowPost.aspx))

*The stock 32-bit Ubuntu kernel is built with support for 4GB. *

**UPDATE:** After further reading, I believe the above statement may or may not be true. I guess the saying, "Don't believe what you read in the papers is also true for the internet. hehe hehe. ([http://www.extremetech.com/article2/0,1697,2114123,00.asp](http://www.extremetech.com/article2/0,1697,2114123,00.asp))

[I]There is a limit to the amount of usable RAM. A 32-bit PC architecture like the Intel Pentium i686 family can only access 4 GB of RAM. This is a hardware limitation. Assuming you can insert 16 GB of RAM into the computer, only the first 4 GB will be addressable. The second limitation comes from the Linux 2.6 kernel used by Ubuntu's Dapper Drake (as well as other Linux variants). The kernel can only access 1 GB of RAM. Any remaining RAM is unused. For this reason, it is currently not worth investing in more than 1 GB of RAM. Also, since the total virtual memory (RAM + swap) is limited to 4 GB, you should not need to allocate more than 3 GB of swap on a 1 GB RAM system.

Note: If you compile the kernel from scratch, there is a HIGHMEM flag that can be set to access up to 4 GB of RAM on a 32-bit architecture. Unfortunately, there is a reported performance hit since most hardware drivers cannot access the high memory. If you set this flag, then do not bother with any swap space&#8212;the total amount of memory (RAM + swap) cannot be larger than 4 GB.[/I]


Even if the stock kernel wasn't, you may have less issues compiling your own kernel than going with the 64bit version of Ubuntu. Have you tried ALL the suggestions? adding irqpoll, or noapic, or nolapic. have you tried piix suggestion as I see that you're using a sata dvd-writer. if you have edgy install already, you could always try to use the Alternate CD and perform an Upgrade?

---

### Post by scubastevegk on 2007-05-01
In my 32bit installation, only 3 GB of RAM is available for use.  It's my understanding that this is due to the system needed to leave space to address the memory on the video cards and the PCI bus, but I could be wrong there.  I've tried a few of the option on the AMD64 disc, but have not been able to go through them all yet - I'll be taking another shot at it when I get a chance.  I just wanted to throw my two cents into the discussion to offer up a little more information and see if possibly anybody had the same experiences I did.

---

### Post by dannyboy79 on 2007-05-01
> **scubastevegk said:**
> In my 32bit installation, only 3 GB of RAM is available for use.  It's my understanding that this is due to the system needed to leave space to address the memory on the video cards and the PCI bus, but I could be wrong there.  I've tried a few of the option on the AMD64 disc, but have not been able to go through them all yet - I'll be taking another shot at it when I get a chance.  I just wanted to throw my two cents into the discussion to offer up a little more information and see if possibly anybody had the same experiences I did.

and have you enabled the HIGHMEM option when compiling the kernel?

---

### Post by pinoytechie on 2007-05-01
> **dannyboy79 said:**
> didn't you notice that the instructions state that you need a fat32 partition? anyway, did you try the fixes stated above? if so, did they work?

I already installed Feisty when I found this thread.

---

### Post by elect on 2007-05-01
It works :mrgreen: ....wow :lolflag: 


I played a lot with my drives-disposition.
All I say is to install with minimal number of hd and cd/dvd player, in this case with a dvd player and the hd target. Then play with settings: master, slave, primary ide, secondary ide...

I got it works with hd in master on pri ide and dvd in sec ide always master

---

### Post by markoloka on 2007-05-02
Does anyone know if it's possible to make my own Kubuntu installation cdr? I thought since there's no official fix to  this and modprobe piix doesn't work for me. I've been wondering if i could put newer kernel to installation disc or so. 

Are there alternative methods to install??? I'm not meaning alternative disc as i've tried that allready but something like net install or so. Any suggestions are welcome since i'm stuck w/ xp and i want to do fresh install on feisty. Maybe i try my beta again... it's only one that works until it fails on software installation.

---

### Post by dannyboy79 on 2007-05-02
> **markoloka said:**
> Does anyone know if it's possible to make my own Kubuntu installation cdr? I thought since there's no official fix to  this and modprobe piix doesn't work for me. I've been wondering if i could put newer kernel to installation disc or so. 

Are there alternative methods to install??? I'm not meaning alternative disc as i've tried that allready but something like net install or so. Any suggestions are welcome since i'm stuck w/ xp and i want to do fresh install on feisty. Maybe i try my beta again... it's only one that works until it fails on software installation.


i ahve provided several alt means to install feisty, they are all listed within this thread. they include installing from an iso stored on a seperate fat32 parititon (using alt install cd iso image), OR recreating the iso with a new kernel and or other new files. OR you could also try to do a network install. have you seen the windows installer, I forget what's it's called, something like Wubi. found here: [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

### Post by markoloka on 2007-05-02
I'm interested first to try that compiling new iso w/ another kernel (which one, any ideas???). Network install would be ok too...but then i take my pc to my work as we have millions time faster net there than at my home. 
I'll give look for that "wubi". If i succeed then i'll spread my info how i got things work. I hate it when when people don't how they fixed their problems/errors after they ask for help in forums.
Damn i thought i missed something. Maybe i need to start reading this topic :roll:

---

### Post by dannyboy79 on 2007-05-02
> **pinoytechie said:**
> I already installed Feisty when I found this thread.

i was merely pointing out that the guide you linked to that you stated you followed and then got this error specifically stated, "Using your favorite ISO image extractor, extract Feisty Fawn's iso image to a VFAT/FAT32 (or ext2/ext3/reiserfs) drive/partition of your choice" so it's possible that there are other issues besides with the Feisty Installer due to you trying to run it from a NTFS partition.

---

### Post by mr_manny on 2007-05-03
Tried both the 7.04 standard, and alternate images :(

Simply can't get past the tty errors I receive shortly after the ubuntu logo.
Guess I'll try pulling everything accept for one dvd and one hard drive...

currently installed opensuse didn't have any issues w/my hardware :(

---

### Post by sk8dork on 2007-05-03
> **mr_manny said:**
> currently installed opensuse didn't have any issues w/my hardware :(
they're using an older kernel with their latest release.

---

### Post by mr_manny on 2007-05-03
kernel 2.6.18.2 is the default for opensuse 10.2

We are running 6.04 on a Laptop, and am looking forward to trying 7.04 on this box...one day :P

---

### Post by strikeback03 on 2007-05-04
> **hbjason said:**
> If you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
  o Select [COLOR=Blue]F6[/COLOR] for more options
  o Add the following option to the beginning of the options list:
        [COLOR=Blue]break=top
[/COLOR]   o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
        [COLOR=Blue]modprobe piix
        exit

[/COLOR] You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
  o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
    -- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
  o When the install is complete do not reboot -- stay in the LiveCD
  o Open a terminal ([COLOR=Blue]Applications->Accessories->Terminal[/COLOR])
     o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

        [COLOR=Blue]mkdir target
        sudo mount /dev/hda1 target[/COLOR]

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: [COLOR=Blue]
sudo mount /dev/hda2 target/boot

[/COLOR]         [COLOR=Blue]sudo chroot target

[/COLOR]   o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
  o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
    -- you should do this with your favorite unix editor; or simply type the command:
        [COLOR=Blue]echo piix >> /etc/initramfs-tools/modules[/COLOR]
  o After modifying the file you must update the system with the command
              [COLOR=Blue]update-initramfs -u[/COLOR]
  o When complete, type '[COLOR=Blue]exit[/COLOR]' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

the above does not allow me to boot the LiveCD.  If I use "all_generic_ide" in the options the LiveCD boots, that is how I installed Feisty.  However once installed Feisty will often not boot, says it cannot find the hard drive.  How do I make the install boot reliably?

---

### Post by mr_manny on 2007-05-05
found the following online:

Your /boot/grub/menu.lst uses uuid and your fstab doesn't. Since uuid is not required, 
try this change to the first Ubuntu entry in your your menu.lst. and see what happens...

change Code:

kernel /boot/vmlinuz-2.6.20-12-generic root=UUID=2788b51c-0f80-4201-8303-88f66218ec1f ro quiet splash

to Code:

kernel /boot/vmlinuz-2.6.20-12-generic root=/dev/hdb7 ro quiet splash


There is a way to get the uuid by using the following command:

ls -l /dev/disk/by-uuid/





contrats on being able to boot the live...I think I tried the all_generic_ide, or was it all-generic-ide?

will try again.

---

### Post by strikeback03 on 2007-05-05
all_generic_ide is what worked for me.  Anytime I have been able to boot (from LiveCd or install) the UUID of the drive is the same number as in the kernel boot line.  Whenever it has thrown the error I can't seem to do anything to check and see what it thinks the UUID is.

---

### Post by evslin on 2007-05-05
Good morning,

I have a test laptop that I use to screw around with, and I encountered this error trying to even just load the newest Ubuntu live CD after previously having FreeBSD 6.2 installed.  Long story short, I ended up pulling my Windows XP install CD back out and using it to blow away all the partitions on the hard drive.  The Ubuntu live CD worked just fine after that.

Hope that helps somebody who's trying to install this!

---

### Post by klytu on 2007-05-05
> **strikeback03 said:**
> all_generic_ide is what worked for me.  Anytime I have been able to boot (from LiveCd or install) the UUID of the drive is the same number as in the kernel boot line.  Whenever it has thrown the error I can't seem to do anything to check and see what it thinks the UUID is.

all_generic_ide also works for me on my problem computer. 

So, if I understand you, sometimes you boot with no errors and sometimes you don't? Or is that you can boot from LiveCD or install but can't boot from the harddrive at all? Could you post the contents of your /etc/fstab and your /boot/grub/menu.lst files?

---

### Post by markoloka on 2007-05-07
Strange thing happened to me...
I got my feisty installed. Not from desktop or alternate cd's but from BETA. Althought grub is nowhere to boot so i need to fix that. Gparted live cd helped me to boot on new feisty. After it i did update/grade and about 250 files were updated. What i realised... beta handles my sata2 hd much better than official release. They changed something how it handles hd's but what?

Hopefully this topic get's solved soon.

---

### Post by Cannaregio on 2007-05-07
Happened to me too once.
Sorry if this solution has already been proposed, but it worked for me, so I'll bump it.

This error "BusyBox /bin/sh can't access tty" and so on is mostly due to the fact that you have a XP partition and dual boot and you just pulled off a USB stick without due ejecting either in your XP partition or in Ubuntu itself.

Solution is to live boot from a feisty live cd, and then terminal, and then (not really necessary) check with system --> administration --> gnome partition editor, if you want to see what happens, but the important life-saving command is:

```
sudo e2fsck -y /dev/sda1
```

the corrupted drive will be checked and healed.

It worked for me, your mileage may vary.

---

### Post by dannyboy79 on 2007-05-07
> **Cannaregio said:**
> Happened to me too once.
Sorry if this solution has already been proposed, but it worked for me, so I'll bump it.

This error "BusyBox /bin/sh can't access tty" and so on is mostly due to the fact that you have a XP partition and dual boot and you just pulled off a USB stick without due ejecting either in your XP partition or in Ubuntu itself.

Solution is to live boot from a feisty live cd, and then terminal, and then (not really necessary) check with system --> administration --> gnome partition editor, if you want to see what happens, but the important life-saving command is:

```
sudo e2fsck -y /dev/sda1
```

the corrupted drive will be checked and healed.

It worked for me, your mileage may vary.

maybe you didn't read most people's posts but this is the error they are getting when they try to boot the Live CD. You're one of the lucky ones that could actually boot the live cd.

---

### Post by Cannaregio on 2007-05-07
Sorry about that, indeed I only read diagonally, because this is a common problem for people that have already installed Feisty and that suddendly get this error because they removed a USB stick. And I thought the solution I found could help.

Maybe these circumstances are correlated?

---

### Post by markoloka on 2007-05-08
I had on one ext3 partition bad blocks. My hd is brand new. I did check on system rescue cd cos that thing can boot correctly. Now bad blocks are gone... i did that test several times until all was fine. Some days after it beta worked. I did try desktop & alternate cd's but still they won't work.

---

### Post by strikeback03 on 2007-05-08
> **klytu said:**
> all_generic_ide also works for me on my problem computer. 

So, if I understand you, sometimes you boot with no errors and sometimes you don't? Or is that you can boot from LiveCD or install but can't boot from the harddrive at all? Could you post the contents of your /etc/fstab and your /boot/grub/menu.lst files?

here is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a531c6c6-3243-4364-bbaf-50d1452bef42 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=b5cd1dd6-738d-47d8-bf80-0fee9604dee4 /home           ext3    defaults        0       2
# /dev/sda1
UUID=3A18D43918D3F1BD /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=094C9CAC118AB52B /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=B044F23244F1FAC4 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=c8295546-1578-47c1-8dcc-1859bc894064 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0 
```

and menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a531c6c6-3243-4364-bbaf-50d1452bef42 ro all_generic_ide noapic nolapic

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a531c6c6-3243-4364-bbaf-50d1452bef42 ro all_generic_ide noapic nolapic quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a531c6c6-3243-4364-bbaf-50d1452bef42 ro all_generic_ide noapic nolapic single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I have edited menu.lst to add all_generic_ide for now, as well as noapic and nolapic which seem to fix random freezing issues.

I was never able to boot the LiveCD without all_generic_ide.  IIRC I was able to boot the install without it once or twice right after install, before I realized how much of a problem it was.

---

### Post by Gang_Star on 2007-05-10
Sorry I didn't have time to read this whole thread, so I don't know where most of you are up to, but I thought I would add my own personal experience and resolution:

So a week or so ago I decided to install Ubuntu to a spare wiped sata drive. Got the same old error despite my best efforts. I rewrote the cd etc and tried all the different options in the menu. No successs. In the end I installed dapper instead, which went flawlessly. I then upgraded to edgy, then to feisty.

A week later I have decided I would rather start fresh on Kubuntu instead - same cdlive error shinnanigans. And I would rather not use the time and bandwidth doing the same thing. I read this thread and decided to try a few of the ideas. I unplugged all my drives except the main sata drive and a cd drive. My samsung CDRW didn't work, but my samsung DVDRW did. Booted into the live enviromnent with only a couple of odd graphical glitches. Install went fine.

My Hardware:
Core2 Duo, Asus Mobo, SATA drive, Samsung CD drives, floppy

[B]Conclusions:
*I personally don't think most of the hardware is a big factor, except for possibly the CD drive you use
*This effects both Ubuntu and Kubuntu
*Detatch all drives you don't need (floppy, extra cd drives, hdds etc)
*If one cd drive doesn't work try another[/B]

My ten cents... :)

---

### Post by StylusPilot on 2007-05-10
I am yet another person to have this same issue when booting the Live CD

My specs are

AMD Athlon 2500+
Shuttle SN45G (nForce2 Motherboard)
SATA Hard Drive
External USB Samsung DVD Burner

Has anyone tried compiling the Live CD with a different Kernel? How do you do that?

I also can't use the Alternate CD, as it can't find my USB DVD even though it booted of it... weird

Any suggestions?

---

### Post by justinblack on 2007-05-11
i dont know if this is of any help to you guys but i had this problem as well
I have 3 hard disks in my pc 2 connected to a sata controller and 1 connected to a IDE controller
when i have all my disks connected the ubuntu 7.04 install disk works fine when i disconnected the 2 sata disks and tried the install disk i got the same error everyone is reporting here.
the reason i disconnected the other disks was to make the installation process easier for me, maybe some of you are also doing the same?
anyway thats my tuppence worth.
cheers
justin

---

### Post by hoagies on 2007-05-11
Hey you guys:

It's about time Mr. Ubuntu himself does something about this!!  One can't expect "noobs", "average housewives",  etc., etc., to start plugging and unplugging hard drives, optical drives, floppies, or whatever else in the hope to achieve some magic "Linux Voodoo", (somewhere), in order to make this OS work!!  An Os is supposed to work "out of the box"; easy man, easy!!

Worst yet, many "average users" start believing that there is something "wrong" with their "own" Computer System, which is not necessarily "true"!!  Does one want to saddle those people with these "eternal doubts"??

I personally believe there is a big problem with the 2.6.20-x kernel.  It was probably written or compiled on somebody's "fan dangled" laptop, ignoring the millions of "permutations and combinations" of computing devices and components out there; which really IS a serious challenge, and problem!!

To arrive at this conclusion:

1.  I run four computers:  One SATA system, and three PATA systems.  The SATA system is the only one accepting 7.04
2.  I have the three versions of ubuntu 7.04:  "live cd", dvd, and "alternate cd".  All of those have manifestations of the same problem
3.  I tried the newly forged Linux Mint 3.0 "Cassandra", BETA.  It uses the new 2.6.20-x kernel.  It also hangs up, at the same point that (k)ubuntu 7.04 hangs up ->  Linux Mint is 98% Ubuntu based
4.  I used the newly forged Zenwalk, which also uses the new 2.6.20-x kernel.  Zenwalk tries to "repair" one's own system.  With the result that it converts my all "/hdx" system to "/sdx", screwing up everything else on the drives, or BIOS??!!


My opinion:  Only Mr. Ubuntu, with the assistance of the Good Lord, can lead us out of our quandaries and miseries, into the "Promised Land".  Really!!  Because remember people, we are now on page 17 of this topic, with no real effective solution, yet!! A solution which satisfies everybody:  Prince or Pauper, Husband or Wife!!

We have arrived at the point where there are people with Computer Systems, who "can", and there are people with Computer Systems who "can not"!!

Notes:  
1. I have NO problems with (k)ubuntu 6.06 LTS  and 6.10, and/or  Linux Mint 2.2 "Bianca", (which is 98% ubuntu based).  And Knoppix, as always, works fine everywhere!!
2.  I have noticed that:  When the older (k)ubuntus and Linux Mint 2.2 install themselves, the installer at one point halts, to announce it is "loading modules for the IDE Chipset", and there are about 5 or 6 of them!!  Are those missing in the 2.6.20-x kernel??

---

### Post by z33k3r on 2007-05-11
I have had the same experiences on two different machines. The one that I know specs for is a Dell OptiPlex GX110... P3 733mhz, 513mb PC100, Dell Slim CD-Rom, 20gig IDE HDD... just the basics... Tried two different instances of 7.04 from two different downloads using the Live disc... will be downloading the alt disc to see if anything changes.

I agree with the last post that the Uby Dev's need to pay attention to this. :mad:

---

### Post by z33k3r on 2007-05-11
I have now tried the Ubuntu Server disc and it installed just fine...:confused:

---

### Post by bazant on 2007-05-12
Hello people!
My case  indicates that Feisty CD  doesn't like  partitions with "unused space". 
I had 3 partitions on my SATA drive. On 1st part - 1 logical disk, on 2nd 1 logical disk and free space and on 3rd 1 logical disk.
With this setup Feisty CD failed.
I changed 2nd part - I added in WinXP a logical drive covering whole free space. I didn't apply any filesystem to it, nor formated it under Win. I just added a logical disk.
After such operation Feisty CD booted correctly!

Hope it helps someone.
Best regards,
Bazant

---

### Post by strikeback03 on 2007-05-12
> **hoagies said:**
> Hey you guys:

It's about time Mr. Ubuntu himself does something about this!!  One can't expect "noobs", "average housewives",  etc., etc., to start plugging and unplugging hard drives, optical drives, floppies, or whatever else in the hope to achieve some magic "Linux Voodoo", (somewhere), in order to make this OS work!!  An Os is supposed to work "out of the box"; easy man, easy!!

Worst yet, many "average users" start believing that there is something "wrong" with their "own" Computer System, which is not necessarily "true"!!  Does one want to saddle those people with these "eternal doubts"??

I personally believe there is a big problem with the 2.6.20-x kernel.  It was probably written or compiled on somebody's "fan dangled" laptop, ignoring the millions of "permutations and combinations" of computing devices and components out there; which really IS a serious challenge, and problem!!

To arrive at this conclusion:

1.  I run four computers:  One SATA system, and three PATA systems.  The SATA system is the only one accepting 7.04
2.  I have the three versions of ubuntu 7.04:  "live cd", dvd, and "alternate cd".  All of those have manifestations of the same problem
3.  I tried the newly forged Linux Mint 3.0 "Cassandra", BETA.  It uses the new 2.6.20-x kernel.  It also hangs up, at the same point that (k)ubuntu 7.04 hangs up ->  Linux Mint is 98% Ubuntu based
4.  I used the newly forged Zenwalk, which also uses the new 2.6.20-x kernel.  Zenwalk tries to "repair" one's own system.  With the result that it converts my all "/hdx" system to "/sdx", screwing up everything else on the drives, or BIOS??!!


My opinion:  Only Mr. Ubuntu, with the assistance of the Good Lord, can lead us out of our quandaries and miseries, into the "Promised Land".  Really!!  Because remember people, we are now on page 17 of this topic, with no real effective solution, yet!! A solution which satisfies everybody:  Prince or Pauper, Husband or Wife!!

We have arrived at the point where there are people with Computer Systems, who "can", and there are people with Computer Systems who "can not"!!

Notes:  
1. I have NO problems with (k)ubuntu 6.06 LTS  and 6.10, and/or  Linux Mint 2.2 "Bianca", (which is 98% ubuntu based).  And Knoppix, as always, works fine everywhere!!
2.  I have noticed that:  When the older (k)ubuntus and Linux Mint 2.2 install themselves, the installer at one point halts, to announce it is "loading modules for the IDE Chipset", and there are about 5 or 6 of them!!  Are those missing in the 2.6.20-x kernel??

while I agree it is a big problem, not everyone has the same problem.  as I understand it, the "can't access tty:job control turned off" is the result of any error on boot - to find out what caused a particular system to hang you need to look at what occurs before the error.  In my case the kernel has issues with my hard drive, "all_generic_ide" fixes it.  other people have different problems, so different solutions are needed.  Maybe they should have had the system print the real error before the generic TTY error.

Testing is done on plenty of different systems, however apparently some change made between one of the last beta releases and the final release caused problems for some testers.  Other than the need to use all_generic_ide, Feisty has been more stable for me than Edgy - Edgy would occasionally refuse to start.

I built another computer for work which is very similar to mine, but only has one HD instead of two.  So with only 2 drives connected (one SATA HD, one SATA DVD burner) it behaved the same as my system - no boot on the liveCD unless "all_generic_ide is used.

---

### Post by phoenixankit on 2007-05-15
I tried one thing, I disabled quicksplash(i think that ws the name) and then some huge list of errors came afer 10-15 mins:

[IMG]http://img91.imageshack.us/img91/5683/15052007001tv1.jpg[/IMG]

[IMG]http://www.imagefilez.com/out.php/i104532_15052007002.jpg[/IMG]

[IMG]http://www.imagefilez.com/out.php/i104533_15052007003.jpg[/IMG]

---

### Post by kirksteadman on 2007-05-15
As a novice to Linux, anew member to the forum I hesitate to offer the following information. I have tried many distros in an attempt to get my wireless PCI cards recognised and installed. I've used two PC and four different wireless cards. Every installation has worked fine except none have recognised the wireless cards and therefore
I have been unable to get on the Internet. Every previous version of Ubuntu has installed OK but not recognised wireless PCI card. Today, Ubuntu and Kubuntu 7.04 arrived, but would not install "message - tty, job control turned off". I have removed the wireless PCI card and bingo Kubuntu installed without any problem. It's a beautiful OS, however I am still left with the inability to get a wireless PCI card to work and therefore caanot get on the Internet. Anyone got a solution to that?

---

### Post by sk8dork on 2007-05-15
i ended up installing edgy on my dad's machine. everything works, even his pci wireless card (it's a desktop box). for some reason he decided to click the 'upgrade to feisty' button in the update manager and after that was unable to get any progress on the ubuntu loading splash. i loaded a previous kernel, uninstalled the feisty kernels, changed all repos from feisty to edgy, and told him not to upgrade to feisty until a new kernel comes out. that's been my fix for getting him to try ubuntu. it's sad, really. 

i tried most of the suggestions in this thread. all_generic_ide made little progress, but didn't completely boot. i am sure it's the combination of 2 sata hdds and 1 ide hdd and 1 ide cdrom, but he just can't be without his xp install on the ide drive (vista is on the other sata drive).

---

### Post by gtippitt on 2007-05-16
The "can't access tty" problems with new kernel are not limited to the SATA/PATA quirks discussed here.  I have 2 Compaq Ipaq Desktop (thin-clients) running Ubuntu with this problem.  These PCs have a removable CD drives that has not been installed since I installed 5.10.  After I upgraded from 6.10 to 7.04 using Upgrade-Manager from the Internet, both are not getting the "can't access tty" error.  I changed the /boot/grub/menu.lst default line from 0 to 2 to load the previous kernel, and the machines booted.  

They are still not quite rite however.  Using the 6.10 version, I cannot remember either of the PCs hanging up so that it hand to be rebooted.  Since I loaded 7.04, one or the other will hang every 48 to 72 hours, so that it will not respond to the mouse or keyboard and I must power it down.  

This PC are about as vanilla as you can get.  They have Celeron 500, 256MB RAM, 4 GB IDE HD and and 1 GB USB Flash drive,  They have the Intel 82801 chipset with video, 100mb Ethernet, audio, and everything built onto the motherboard.  They boot and mount root from the 4 GB IDE HD, and the USB flash is mounted to /usr/lib (ext2 noatime).

With 6.04 and 6.10 they were stable as a rock.  With /usr/lib on the flash drive, it is almost never written, except when software is installed or updated.  Programs load from the flash in a flash.   

I worked for 20 years as a programmer on systems ranging from Control Data super computers to Commodore 64's and  IBM PCjr's and programmed in 9 different languages.  I have never heard of a software package (not from Microsoft) that had been as poorly tested as this 7.04 release.  How did these bugs get into the code without anybody noticing?  

It does not seem to matter if you are upgrading or fresh install.  It does not matter if you are booting from CD or HD.  It does not matter if your PC is fast or slow, old or new.  I realize that everyone for whom 7.04 worked fine has not posted in the thread, but this bug is hitting lots of people.

My 2 PC are not some obscure configuration of devices that just happen to not work together.  These are COMPAQ brand hardware.  The USB flash drive is the only thing hardware that is not original as they came out of their boxes.

On a side note,  if you have problems trying to install Ubuntu on an small PC with limited hard disk space, having the install put /usr/lib on a 1 GB USB flash is a great, cheap, fast  way to give you an extra GB of head room on the hard disk.  With only the 4 GB HD, I have plenty of space for the entire UBUNTU desktop and RhythmBox. I keep my email files on the local hard disk, but I keep all of my other documents on my multimedia server.  You can buy these IPAQs on Ebay for about $25 including shipping.

---

### Post by klytu on 2007-05-16
> **kirksteadman said:**
> As a novice to Linux, anew member to the forum I hesitate to offer the following information. I have tried many distros in an attempt to get my wireless PCI cards recognised and installed. I've used two PC and four different wireless cards. Every installation has worked fine except none have recognised the wireless cards and therefore
I have been unable to get on the Internet. Every previous version of Ubuntu has installed OK but not recognised wireless PCI card. Today, Ubuntu and Kubuntu 7.04 arrived, but would not install "message - tty, job control turned off". I have removed the wireless PCI card and bingo Kubuntu installed without any problem. It's a beautiful OS, however I am still left with the inability to get a wireless PCI card to work and therefore caanot get on the Internet. Anyone got a solution to that?

You might want to research and try out ndiswrapper. Also you´ll probably get better assistance getting your wireless card working by starting a new thread for your problem in the ¨Networking and Wireless¨ forum. Your question will probably get buried and largely ignored within this thread. Also take a look at this page: [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by sparrowhawk on 2007-05-16
This problem was solved for me by disconnecting my floppy drive, installing Feisty and then reconnecting the floppy.

---

### Post by jerrylamos on 2007-05-16
I don't know if some of you have seen my post "Workarounds" in "Installation & Upgrades" which gives a couple ways that "might" get you around the problem(s).  Looking at the situation as a "black box" it appears to me that the very complex SCSI simulation of everything from IDE hard drives, SATA, CD-R/W, and I don't know what else is running head on into the effort to speed up boot by doing things in parallel.  One piece of code has a dependency that hasn't been done yet.  

This is all very time dependent so that any change in configuration or gosh knows what can upset or fix the problem(s).  Basically it looks to me like things are getting out of sequence in the effort to speed up boot.  Now I'm not a developer so I don't know, it just behaves that way to me.

I had hit a problem "can't access tty" which if I turned "quiet" off and looked very closely was an fsck failure because fsck was trying to check a drive that hadn't been mounted yet.  In Edgy & Dapper I think the mounts get done then the fsck, while in Feisty it seems fsck got started before the mounts completed.  

The same thing happens to Feisty CD Live "persistent" mode where the "persistent" code gets started before the USB pen drive volume "casper-rw" is mounted.  In Edgy & Dapper, the mounts get done, then "persistent" can find "casper-rw".  "persistent" worked on Feisty until some experimental Debian scripts were put into Feisty somewhere between 7 February and 10 February.  In this case there is no workaround other than going to Edgy or Dapper.

Another case from my "Workarounds" post:
"Feisty does not recognise CD burner"
"The workaround mentioned in the previous thread (break=top + modprobe piix) fixed the xfermode error problems described in bug #96826 for me on a Dell OptiPlex GX100 system. The two problems seems to be connected. "

Cheers, Jerry

---

### Post by phoenixankit on 2007-05-18
I tried one thing, I disabled quicksplash(i think that ws the name) and then some huge list of errors came afer 10-15 mins:

[IMG]http://img91.imageshack.us/img91/5683/15052007001tv1.jpg[/IMG]

[IMG]http://www.imagefilez.com/out.php/i104532_15052007002.jpg[/IMG]

[IMG]http://www.imagefilez.com/out.php/i104533_15052007003.jpg[/IMG]

SOMEONE!!

---

### Post by Aldebran on 2007-05-20
I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

---

### Post by rockallite on 2007-05-21
> **Aldebran said:**
> I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

Same problem (/bin/sh: can't access tty; job control turned off), and the second solution worked for me.

I found it rather slow when booting into GNOME desktop. Is it some kind of Safe Mode?;)

---

### Post by scubastevegk on 2007-05-21
Maybe this will help somebody, maybe not - but this problem went away for me when I changed my SATA optical drive out for an IDE one.  Now I'm happily running Feisty AMD64 with no issues at all! :)

---

### Post by Osamabingandhi on 2007-05-21
i had the same problem. My solution was to format my disc without any fat32 partition and with no other strange partitions, just the filesystem, home and swap. Anything different gave the tty problem.

---

### Post by bluegray on 2007-05-21
I solved the problem with adding break=top to the boot options and modprobing piix. But now I get a lot of 'Spurious ACK' errors, and the keyboard's leds are flashing - something is not right.

I'm using a 7.04 Live CD that just arrived.

Oh, and I had to disable the floppy drive as well

---

### Post by ^KrS^ on 2007-05-21
Here's my solution, tis a weird one. I have two machines hooked up to a KVM switch, one running ubuntu server 7.04 and one that i was installing ubuntu 7.04 Alt cd on two WD 120G IDE but with sata converters on them.  So i was getting the same error everyone else has been getting, (never got the error on the 64bit alt cd, this is an athlon64 2800+) so when i was messing around chroot'ing around i figured, hey why not try to start X and see what happens.  Well it started, but no mouse.. i thought that's weird...  So i remembered the can't access tty, and thought, just for the heck of it i'll try something.

   So i powered down both the server and the new installed machine, unhooked the mouse and keyboard from the kvm, as well as the cabels to the machines so i had a complete power cycle on the kvm.  Hooked everythign back up , and here i am typing to you from my new install. ;) i dunno why, but resetting the keyboard and mouse at every link from key/mouse to motherboard cleared up my issues.  It almost seems like it's the kernel freakin out cause it can't find, or has a bad signal from the keyboard or mouse.

    Just for reference, i never had any floppy issues with it trying to read it constantly and my hardware that's relevant is below:

Athlon64 2800+
MSI K8N Neo MS-7030 v1
1.5G ddr400
ati 9800 pro 128M
2 x 120G WD IDE with ide -> sata converters on them.

using Ubuntu 7.04 alternative cd
/ is /dev/md0
/boot is /dev/sda1 1G (i know way too much but it matches the swap size)
swap is /dev/sdb1 1G
alt cd boots fine and install went without a hitch, till first reboot then i got the tty issue.

i'll post back if anything else weird happens, as i haven't tested much yet, just thought i'd post this when it was fresh in my brain :)

oh! and i possibly may have edited my fstab and got rid of the UUID's in there as well, and replaced with proper /dev names.  So the key/mouse thing may be completely unrelated hahah sry i just remembered

---

### Post by TrendyDark on 2007-05-22
> **Aldebran said:**
> I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

Doh! I had installed Edgy a long time ago on my Gigabyte board that has the Jmicron SATA controller and used the all_generic_ide trick with success. I knew about it, but when I went to install feisty today I entered "all-generic-ide" hahaha.

---

### Post by atowell on 2007-05-24
> **Aldebran said:**
> I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

the first one worked for me! thanks for the tip!!

---

### Post by The Fold on 2007-05-25
Nice to know I'm not alone with my pain on this problem.

I had read in a couple of places that the problem could be due to the JMicron PATA controller on my ABit IB9 motherboard, as this controller just wasn't supported fully until 2.6.20(?).

Anyway, I've been reading through this thread today and I'll be trying the 3 main suggestions when I get home from work. I'll post back with my results (hopefully from a Ubuntu system ;)).

My hardware:

ABit IB9 965 motherboard
Intel Pentium D 2.6Ghz
1GB Corsair Value DDR2
1x 500GB SATA-II Western Digital
1x 200GB IDE Western Digital
1x 160GB IDE Maxtor
1x 150GB SATA Maxtor
1x 120GB IDE Maxtor (not currently connected due to lack of PATA space :P)
1x NEC 3500 DVD+/-RW
XFX GeForce 7600 GS 256MB

Yeah, I have a lot of drives. I'll be yanking them in turn if the regular suggestions don't help though. My aim is to get Ubuntu on the 160GB and have the system dual-booting with XP which is on the 500GB.

---

### Post by sk8dork on 2007-05-25
> **The Fold said:**
> Nice to know I'm not alone with my pain on this problem.

I had read in a couple of places that the problem could be due to the JMicron PATA controller on my ABit IB9 motherboard, as this controller just wasn't supported fully until 2.6.20(?).

Anyway, I've been reading through this thread today and I'll be trying the 3 main suggestions when I get home from work. I'll post back with my results (hopefully from a Ubuntu system ;)).

My hardware:

ABit IB9 965 motherboard
Intel Pentium D 2.6Ghz
1GB Corsair Value DDR2
1x 500GB SATA-II Western Digital
1x 200GB IDE Western Digital
1x 160GB IDE Maxtor
1x 150GB SATA Maxtor
1x 120GB IDE Maxtor (not currently connected due to lack of PATA space :P)
1x NEC 3500 DVD+/-RW
XFX GeForce 7600 GS 256MB

Yeah, I have a lot of drives. I'll be yanking them in turn if the regular suggestions don't help though. My aim is to get Ubuntu on the 160GB and have the system dual-booting with XP which is on the 500GB.

your problem is likely related to the combination of sata and pata devices connected and your pata controller as you mentioned. you may have little success trying to install ubuntu on the 160gb pata drive while having the 500gb sata drive connected so it will detect the os and offer a line in the grub menu. if one of the suggestions here works for you, like all_generic_ide, then great, but if you get stuck you may want to try installing ubuntu on the 150GB sata drive, only having the 150GB sata and the 500GB sata connected (with the cdrom too of course). that even may not work, but it could be worth a last resort effort. if nothing works, you might want to try to install edgy instead, but that may not work if your hardware really isn't supported prior to 2.6.20, since edgy uses a 2.6.17 kernel i think.

---

### Post by HuskyDev on 2007-05-25
> **nkp_20 said:**
> Quick solution to try guys:

When booting with livecd (Feisty 7.04) you could just try the option that says "Boot with Driver CD", but just keep the regular livecd in the drive and press enter both times when prompted to do so. This worked for me, so you guys may as well try it.

Also worked for me.  Weirdness...  I wonder what the "Boot with Driver CD" does different from the straight install option.

Thanks for the tip!

---

### Post by Zizo on 2007-05-25
Hi all,
 
I was using dapper and decided to upgrade. I did that in 2 steps, from dapper to edgy then to feisty. I didn't use any live CD. I upgraded using the internet.
 
First I got a problem with the X server which couldn't start properly. So I was on text only. 
 
Second I also got /bin/sh: can't access tty; job control turned off .
 
I tried many things but the system is locked in that second error. Any suggestion?
 
Thanks

---

### Post by jerrylamos on 2007-05-25
Sorry, we don't know what "tried many things" are.  Can you list them?  Also, what are the last few lines on the screen before the "can't access tty"?

---

### Post by upchucky on 2007-05-25
I too am getting an error , but i did not do upgrade to Feisty

I let my Edgy do a security update, and when it requested my sys to reboot when done it came up with the following error after the ubuntu splash screen

/bin/sh: can't access tty; job control turned off
(initramfs) [17179576.876000] usb 1-1: device not accepting address 2, error -71

this is a laptop install that was running edgy just fine and it never choked on updates before.

I am booting a usb install and intended to do this untill i have replaced all my windows software with Linux software.

it is obvious that the edgy update broke a file that the usb needs to boot. i do have some commands available to try to get to the problem. since grub is booting the problem is not there.

any ideas?

---

### Post by doctoss on 2007-05-25
I was getting the same error messages probably referring to my floppy, and my hard drive was not recognized. I solved the problem by removing the jumper that was in the master position on a single hard drive. I guess when there is only one drive the jumper confuses feisty.

---

### Post by Zizo on 2007-05-26
I tried the many things that are listed in here and also by googling. Don't forget that my linux has limited services now. I am not able to do much. Limited commands. So I am left with nothing.
 
I am so frsutrated how come this can happen? I mean just an upgrade messed up my computer. What if I rely on ubuntu only? What if I had no Windows partition on it? I thought we can completely get rid of Windows but it seems no. And that is a shame.
 
One upgrade messed up my X server then my boot thing. At least put a warning that there is a bug for a certain type of PCs.
 
This will negatively influence ubuntu.....

---

### Post by The Fold on 2007-05-26
> **sk8dork said:**
> your problem is likely related to the combination of sata and pata devices connected and your pata controller as you mentioned. you may have little success trying to install ubuntu on the 160gb pata drive while having the 500gb sata drive connected so it will detect the os and offer a line in the grub menu. if one of the suggestions here works for you, like all_generic_ide, then great, but if you get stuck you may want to try installing ubuntu on the 150GB sata drive, only having the 150GB sata and the 500GB sata connected (with the cdrom too of course). that even may not work, but it could be worth a last resort effort. if nothing works, you might want to try to install edgy instead, but that may not work if your hardware really isn't supported prior to 2.6.20, since edgy uses a 2.6.17 kernel i think.

Well, I tried all 3 solutions that other people have tried, that is, the Install using Driver CD option, the break=top option and the all_generic_ide option, none of them worked for me.

I tried pulling all drives except the DVD-RW (IDE) and 1 IDE drive, no joy.
I then tried 1 SATA drive and the DVD-RW, no joy.

A further problem I found is that the whole thing was freezing during USB detection for some strange reason. I'd get the busybox prompt but then while typing the machine would freeze completely. It was only when I took the --quiet and splash options out that I could see this happening when loading USB drivers.

So, my next idea (thanks to my boss) was to try booting Knoppix. It boots and detected everything although it did complain that I had a broken bios(?) for some reason. Also with this it would start loading X and as far as the system was concerned, it had, however I got no display. I'll blame that on drivers though I think. I could move into a console session but response from the keyboard was incredibly slow.

I went back to the ubuntu disc and tried running acpi=off noapic as boot parameters without any joy, it still froze. One last try with the Knoppix disc, this time without any boot options and I have a console that isn't slow. 

Any thoughts on bootstrapping/install ubuntu from here a'la Gentoo style?

---

### Post by mdvalley on 2007-05-26
I might be able to give the developers some insight into this problem. I have a situation where the Fiesty LiveCD booted correctly, and later failed to boot with the same CD and the same hardware in the same configuration.

Background:

My initial Ubuntu install was with Dapper. Later on, I decided to upgrade to Edgy through the update manager. Through the upgrade process, I got errors and warnings about incomplete installations and unstable operating systems. However, the system still rebooted and runs fine to this day, seeming running Edgy. But I'm still concerned about it, so I wanted to make a fresh Feisty install from the CD.

I had my home folder on the same partition as my operating system, so I wanted to change that before I installed. I booted from the Feisty LiveCD without incident. I followed the guide at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to move my home folder to its own partition. In short, I used GParted to resize my linux partition, make a new one, copy some files, and fstab it as my home. Feisty kept re-mounting my volumes, which was annoying, but it otherwise went well. I restarted the computer and booted into my hard drive to verify that the change was successful, and it was. Firefox (and some other programs) forgot all my settings, but the system booted.

I then restarted back into the LiveCD to install Feisty and got the error:

/bin/sh: can't access tty: job control turned off

with no other information or error messages. My system is still running Edgy at the moment.

Motherboard: ASUS P5GD1 (Intel 915P northbridge, Intel ICH6R southbridge)
CPU: Pentium 4 3.2Ghz HT
Hard Drive: Western Digital 250GB SATA (Primary master)
CD-ROM: Plextor PX-755SA SATA DVD-RW (Secondary master)
Video: EVGA 7600GT KO
Sound: SB Audigy2 ZS
Onboard network card
Keyboard wired, PS/2
Mouse wired, USB
Kernel 2.6.17-11-386

Partitions before:
/dev/sda1: NTFS, Windows, 149.94GiB
/dev/sda2: ext3, Ubuntu, 80.05GiB
/dev/sda3: extended
/dev/sda5: linux-swap, 2.90GiB

Partitions after:
/dev/sda1: NTFS, Windows, 149.94GiB
/dev/sda2: ext3, Ubuntu, 14.65GiB
/dev/sda4: ext3, /home, 65.40GiB
/dev/sda3: extended
/dev/sda5: linux-swap, 2.90GiB


If there's anything you'd like me to try on this system to help discover the cause of this bug (short of destroying data), I'd be happy to help.

---

### Post by upchucky on 2007-05-27
I just wanted to update my post on this,
I got my edgy working again, it turned out that the automatic security update from a few days ago re-wrote or moved my Grub/menu.lst.
My bootable usb drive is sdb1
the update changed it to sda1.
I had to boot with my edgy live cd and edit all drive entries in "menu.lst" to again say sdb1, reboot and all is ok.
the google post that clued me in said something about a command to see which drive is the usb drive and comparing the info there to the info in menu.lst, and fstab.

it was very late last night and I'm just a linux beginner, sorry i cant remember the command and did not save the link to the clue.

Anyway I hope my fix helps others.

---

### Post by DarkStarAeon on 2007-05-28
Well, I went out of town for the weekend, came back, fired up my computer and my wifes computers, both run Ubuntu, and both said there are updates available.

Mine upgraded with no issues, my wifes computer is having the same error message you are all getting, and I have no clue how to fix it or even what is wrong.

This is not good, not good at all.

---

### Post by DarkStarAeon on 2007-05-28
Ok this is weird.

My wifes computer which dual boots Ubuntu and Windows, which is experiencing the problem described in this thread, is now working.
I logged into the Windows side and all sorts of minor things were buggy in there, especially internet connection wise. So I tweaked and peaked all that with ipconfig and reentering my wep key etc. etc. etc.
(why much of the windows stuff was buggy at the same time I have no idea)

Then I restarted and logged into the previous version of Ubuntu 2-6-20-15 and all was fine there, so I decided to try the new 2-6-20-16 again.

It took a minute or two to load, but then 2-6-20-16 finally did load.

I have restarted a few times now, and switched back and forth a few times now between Windows and Ubuntu and all seems to be working.

Like I said, no idea if it's related, but my wifes Ubuntu/Windows computer is working now, maybe there was a problem on both sides that conflicts?

---

### Post by Foaming Draught on 2007-05-28
hbjason, thank you very much for the fix which you posted 4 weeks ago (#133).  It worked perfectly for me.  Mind you, I had the forum open on a second machine so that I could see what commands to type.  In the absence of an adjacent machine, one would have to print out your post.

But now my belovèd Ubuntu is installed on desktop and laptop, and I'm very grateful.

FD

---

### Post by sk8dork on 2007-05-28
the new kernel version is available, as pointed out in DSA's last post, 2.6.20-16. does anyone know if this kernel update fixes the problem in this thread?

---

### Post by DarkStarAeon on 2007-05-28
That's the one that created the problem for me. 

But somehow it's all working now.

---

### Post by The Fold on 2007-05-29
An update on my progress over the weekend:

As I said before, booting from Feisty is a no-go. I tried booting off the alternate Feisty iso which got me a little further, complaining that I needed to boot with the irqpoll option as it was having issues with my USB on IRQ19. Doing this, I could see that it was detecting hard disks but then hung whilst detecting my USB mouse/keyboard.

As I don't have a PS/2 keyboard or mouse to test, I couldn't exactly turn off USB, although I did try setting it in the boot command line then yanking the keyboard straight after hitting return. This then resulted in the system freezing up shortly before where it was previously, which was the HDD detection.

I also tried booting from an Edgy disc, which got pretty much nowhere, hanging during boot when saying there was no PS/2 controller found.

I managed to get a bare Gentoo install onto the drive I wanted although even that's giving me a VFS error on boot, suggesting I don't have ext3 support in the kernel even though I have it all compiled in.

I did some more searching about the JMicron controller and it seems other people have had issues with this (although frustratingly not with my motherboard) and it seems a patch was applied to the kernel fairly recently. The question is, how do I get said kernel booting on my system and get an install kicked off?

EDIT: 

A guess I suppose would be to try this suggestion from dannyboy79. I've performed an operation similar to this once before with Knoppix. I'm guessing if I could mount the squashfs then chroot into it I could re-compile the kernel with the latest updates to try it?

> **dannyboy79 said:**
> there's a little bit longer of a way but you could give it a try if you really want to use feisty. you could perform the fix by creating your own liveCD with the change already implemented if the chroot doesn't work.

mount the ISO image as part of a liveCD
copy the ISO contents into a temporary directory 
the stock feisty  live CD comes with Windows installers for various free software packages like Firefox and Thunderbird; if you don't need these on your live CD, you can save over 30 MB by deleting the programs/ directory 
mount casper/filesystem.squashfs as part of the filesystem 
use Squashfs and compile the kernel stuff 
alternatively, Gentoo kernels seem to already have the squashfs stuff patched in 
copy the contents into a temporary directory; do this as root and with -a option for a correct copy 
make any necessary modifications to the root filesystem, in this case, add piix to that one file 
rebuild root filesystem; run as root: 'mksquashfs squashfs-root filesystem.squashfs' 
overwrite the old casper/filesystem.squashfs file with the newly created one 
build burnable, bootable ISO: 'mkisofs -o ubuntu-6.06.1-desktop-i386-custom.iso -b "isolinux/isolinux.bin" -c "isolinux/boot.cat" -no-emul-boot -boot-load-size 4 -boot-info-table -cache-inodes -r -J -l ubuntu-6.06.1-desktop-i386' 

I am guessing this would work but haven't tried it yet. I got the idea from here: [http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html](http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html)

EDIT2:

I'll be trying this tonight [[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)]

---

### Post by -Soul_Reaper- on 2007-05-29
I get the same freaking message! It really sux cause i have to use this old pc till i get ubuntu on it.
My specs:
-pt.4 2.8ghz
-1gb of RAM
-150gb HD
-It is a compaq >:[

Can someone help me i am really new to linux and my HD pretty much crashed, so i am trying to install linux.

---

### Post by -Soul_Reaper- on 2007-05-29
> **Osamabingandhi said:**
> i had the same problem. My solution was to format my disc without any fat32 partition and with no other strange partitions, just the filesystem, home and swap. Anything different gave the tty problem.

So do i just format it? I got another machine i can hook it up to do that.

---

### Post by Lamel on 2007-05-29
Ok, im new to this all but this is what i did and i got my system up and running. It may help it may not.
 Ok after I booted the live cd and did the install and befor i did the reboot (i was installing ubuntu 7.04 desktop for 32 bit) I was looking around system and found synapic package. Under base system I found a list of different things that where installed and where not installed. I went through and added some of the system (i forget all that i added) that i rember seeing in the forum while i was looking for answers. After i added them and let them install then i did the reboot and so far everything workes. I hope this helps someone anyway, have fun and ill check back later.:D

---

### Post by Imashinu on 2007-05-29
I unfortunatly have this problem and it is becoming aa big problem. I tried disconnecting all of my diffrent                  hardware with no help. This is  a serious problem because i need a new OS because windows is grabage.

---

### Post by havrelm1 on 2007-05-30
Having the same problems too. ata2.0 failed to set xfermode after selecting install ubuntu studio 7.04, (then when i tried regular ubuntu 7.04, I got the can't access tty error message (which didn't list when trying to install ubuntu studio) and the ata2.0 failed to set xfermode error message, then when I go through the installer it doesn't detect my 2nd sata hdd, but all drives work perfectly in xp pro and ubuntu edgy 6.10). I haven't tried any of the fixes yet, and really dont want to go through all that.

AMD Athlon 64 X2 3800+(65W) Windsor 2.0GHz Socket AM2 Processor, 1GB DDR2 800 RAM
MSI K9N SLI Platinum Socket AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard
XFX PVT73GUGD3 GeForce 7600GT 256MB GDDR3 PCI Express x16 Video Card
Sony NEC Optiarc 18X DVD±R DVD Burner Black E-IDE/ATAPI
Western Digital 80GB SATA
Samsung spn160GB IDE (with SATA adapter)

---

### Post by The Fold on 2007-05-31
Right, well I re-mastered the 7.04 LiveCD with the 2.6.20-16 kernel and instead of getting the /bin/sh: can't access tty error, it seemed to find my hard disks but was coming up with some kind of ext3/journal error (the disk in question does have an ext3 partition on it).

After having the error come up 20 or so times it did finally go to a busybox prompt, where I'm still getting an issue with my USB keyboard freezing up. I tried disabling USB2.0 in my BIOS which did give it a little extra life but not much.

One thing I did find is if I booted from the 7.04 minimal disc, the system worked absolutely fine up until it performed hardware detection, at which point the system hung again, a tail -f on /var/log/messages showed it was during hard disk detection.

I'm now working on re-mastering the LiveCD with a stock 2.6.21 kernel which I've almost got working except for some reason it's saying /lib/modules/2.6.21 doesn't exist, despite me running a 'make && modules_install'. I copied over the config from the 2.6.20-16 kernel headers and added in some extra support for PATA controllers as I noticed some JMicron and IT* controllers in the list.

I've been told the problem with the modules not showing may be down to not having a correct initrd? If anyone can shed some light on this it'd be much appreciated. I know I have to run something along the lines of 'mkinitramfs -o /boot/initrd-2.6.21 2.6.21'.

---

### Post by Lamel on 2007-05-31
Ok, this is what I did to get mine to work for 7.04 ubuntu. 

1.booted from live cd
2.I did a install
3.After the install and befor the reboot I went to system, administration, synaptic package manager.
4.Clicked on serch
5.typed in grub
6.after it did the search and found all the different package I clicked on all that where there and let them download and install.
7.rebooted and it worked
Now i dont know if this will work for everyone so just give it a try and post if it worked. If not Ill try again to see what might work.:D

---

### Post by sk8dork on 2007-05-31
> **Lamel said:**
> Ok, this is what I did to get mine to work for 7.04 ubuntu. 

1.booted from live cd
2.I did a install
3.After the install and befor the reboot I went to system, administration, synaptic package manager.
4.Clicked on serch
5.typed in grub
6.after it did the search and found all the different package I clicked on all that where there and let them download and install.
7.rebooted and it worked
Now i dont know if this will work for everyone so just give it a try and post if it worked. If not Ill try again to see what might work.:D

did you ever actually come across the problem(s) brought up in this thread? or did you just have success in installing and posted what you did that was against the norm? (sorry if you posted previously in this thread with your problem, i can't remember and can't be bothered to look through each page right now). when you say 'booted from live cd', it makes me think you don't have the same problem most people in this thread had, which was not being able to boot to the live cd...  i know on my particular home machine i never had any problems installing feisty or booting the live cd, so anything i did on that machine would be of no help to anyone in this thread.

---

### Post by Lamel on 2007-05-31
Yes i did have the same prob as in getting the error. When i said i booted from live cd i mean just that(a complet new install) How ever i did not seem to have any other prob after that. Please understand that im just tryen to help out and dont mean to come off as a know it all.

---

### Post by The Fold on 2007-05-31
Well, I sorted out the modules issue I was having with the re-mastered LiveCD, but it's still not working. I now get a busybox prompt even in qemu.

I tried the latest Gentoo LiveCD as well and it hung detecting in piix. As much as I want this to work I'm really out of ideas now :(

---

### Post by serlex on 2007-05-31
This problem is scaring people off from trying out Ubuntu, get it sorted.

---

### Post by dragon slayer on 2007-06-01
Nice work nkp-20,:D that worked thanks

---

### Post by Essence on 2007-06-01
I was able to get around the problem pretty quickly myself... On my desktop I have disc drives, a NEC DVD burner, and a Sony CDRW Burner. When I booted from the disc in the NEC drive it produced this problem, so I switched the boot order of the two drives in the bios, and put the disc in the sony drive, which worked fine. Just thought I would post incase it helps someone else.

---

### Post by dragon slayer on 2007-06-01
ok i posted to soon my screen went black oh well 
I haven't been able to lode Ubuntu since 5.04 probably hard ware
freespire and fedora lode. (this is on a compaq)
I tried it out on my dell it loads with out a glich
Thanks any way Good work Ill try 8 when it comes out.:)

---

### Post by mnhtapu on 2007-06-01
A person known to me tried to install Ubuntu 7.04 using its live CD in his pc but he failed as it gives an error 
“/bin/sh: can't access tty; job control turned off”.

His PC’s configuration is Amd Athlon XP1400, Motherboard MSI MS6382,Ram 256MB DDR1. Again, he tried in another machine which has Pentium D 3.0GHz,Motherbord 
Gigabyte 945 DS2, Ram 512MB with HD Audio. In that PC Ubuntu runs without any problem. Would anyone give me a solution so that I can help that hapless poor guy?

---

### Post by rcdeacon on 2007-06-01
This is apparently a common problem with many of us. I wish I knew if this was an ACTIVE issue that is being worked on or since it doesn't affect the whole community it is merely considered an annoyance and is not getting any premier treatment. I was very anxious to give Untuntu 7.04 a serious try since I cannot use my ipod or my pda with my current distro (Mepis 6.5). Sadly I cannot even live boot with Ubuntu or Kubuntu 7.04.

---

### Post by paraplier on 2007-06-03
I solved the same problem by installing Ubuntu Studio instead of just the OS alone. maybe something to do with the way the ISO was packaged.

My install background:

ubuntu-7.04-desktop-i386.iso couldn't install because the image on disk "cant access tty; job control turned off"

ubuntu-6.06.1-desktop-i386.iso hung at "uncompressing linux ... okay, booting the kernel"

Studio-7.04-alternate-i386.iso both verified dvd integrity and installed without problem although now I'm trying to resolve "failed to start xserver" problem likley due to my ATI x300 graphics card.

With the Studio install you get the option to decline to install the extra multimedia apps but you'll get open office whether you want it or not. Easy enough to unistall later I'd guess.

Luck,
Paraplier

---

### Post by matt johnston on 2007-06-03
I had the same error message, but I replaced the cd rom with a spare one we had here in the shop and it worked fine.

---

### Post by Cannaregio on 2007-06-04
> **paraplier said:**
> I solved the same problem by installing Ubuntu Studio instead of just the OS alone. maybe something to do with the way the ISO was packaged.

My install background:

ubuntu-7.04-desktop-i386.iso couldn't install because the image on disk "cant access tty; job control turned off"

ubuntu-6.06.1-desktop-i386.iso hung at "uncompressing linux ... okay, booting the kernel"

Studio-7.04-alternate-i386.iso both verified dvd integrity and installed without problem although now I'm trying to resolve "failed to start xserver" problem likley due to my ATI x300 graphics card.

With the Studio install you get the option to decline to install the extra multimedia apps but you'll get open office whether you want it or not. Easy enough to unistall later I'd guess.

Luck,
Paraplier

Indeed I think that that **verifying** part you'r speaking about could be tied to the solution. 

But I'm no developer, I just underline the following for those with real kernel and boot sequence knowledge, that might be able to find a solution to this mess.

As I said,  **/bin/sh: can't access tty; job control turned off ** still appears  (once you have managed to boot) for other USB related problems (maybe a more telling error message could result more useful, he?) but in many cases can be solved with the command
```
sudo e2fsck -y /dev/sda1
```
where you of course substitute **sda1** with your own ext2 or ext3 drive(s)
the corrupted drive will then be automatically (**-y ** for non interactive mode) checked and healed and everything might (might) work again.

Just a desperate 0.0002 cents.

---

### Post by teskiwk on 2007-06-05
/bin/sh: can't access tty; job control turned off

I m new in ubuntu ....but meet this problem when installing it...but finally i solve the problem...i think for those who hav floppy disk in computer will seldom/never meet this problem..cause my computer don't hav floppy disk...and my solution is:-
1. Get a pendrive atleast 1gb and copy all the ubuntu cd's content to the pendrive.
2. Then boot ubuntu cd with the pendrive plug in
3. Then install ubuntu.

[COLOR="Red"]P/s :[/COLOR] I think this problem relate to the dev0 and dev1(don't know correct or not about the letter dev0) it seems like the ubuntu boot will put the cd-rom as dev0 if dun hav floppy disk in that computer, if there is floppy there it will be dev0 for floppy and dev1 for cd-rom and i think the booting will only read the data from  dev1 hence if there is no floppy disk there the cd-rom will be dev0 then the system can't read data from a null dev1...but if we add a pendrive or cd-rom into computer then the path dev1 will be the pendrive or extra cd-rom(if we add cd-rom to it then better we direct boot from that extra cd-rom.

---

### Post by rcdeacon on 2007-06-05
I happen to have a floppy in a computer that is not state of the art and I get the same problem. My own personal opinion is that this is something that really needs to be addressed. There appears to be a sizeable number of people with this particular issue and quite frankly it is a showstopper. How many people desiring to migrate into the linux world are going to persevere through this trying to find a work around? Few!

---

### Post by serlex on 2007-06-05
people with this problem should try Linux Mint 2.2, it should install fine.

---

### Post by dperalesit on 2007-06-05
Hopefully this helps. I was receiving the TTY error as well.
I had 3 80gb Maxtor Drives and 1 60gb WD drive, all SATA.
1 DVD-ROM and 1 DVD-RW, both IDE.
Had to unplug all but 1 80gb SATA and my DVD-ROM drive to install.

Beforehand I tried every solution except hardware. In the end I was desperate and opened up the case.
So any of you holding off opening the case, save yourself the heartache and just try it, it worked for me :)

---

### Post by markoloka on 2007-06-06
Does someone know... if i add that piix etc to initramfs modules does it affect on all kernels?
I mean i updated yesterday and now it won't boot w/ latest kernel. ....12 kernel will boot just fine. 
I had this busybox...tty problem but was able to install via BETA.

---

### Post by domer on 2007-06-06
Ubuntu 7.04 (Fiesty) installed fine in my case (i.e. THE LIVE CD WORKED FINE), but when I restarted my computer after the install I got the error "/bin/sh: can't access tty; job control turned off". I got the same error with Kubuntu. I think I should mention this, I am doing this installation on a new 250 GB WD harddrive and I have XP Pro on a separate partition on the same harddrive.

---

### Post by domer on 2007-06-06
> **domer said:**
> Ubuntu 7.04 (Fiesty) installed fine in my case (i.e. THE LIVE CD WORKED FINE), but when I restarted my computer after the install I got the error "/bin/sh: can't access tty; job control turned off". I got the same error with Kubuntu. I think I should mention this, I am doing this installation on a new 250 GB WD harddrive and I have XP Pro on a separate partition on the same harddrive.

Just as a follow up of my immediately previous post, when I installed Ubuntu Dapper, it worked FINE (the live cd as well as booting up after installation). Which hints that both Fiesty and Kubuntu are buggy. :(

---

### Post by sk8dork on 2007-06-06
> **domer said:**
> Just as a follow up of my immediately previous post, when I installed Ubuntu Dapper, it worked FINE (the live cd as well as booting up after installation). Which hints that both Fiesty and Kubuntu are buggy. :(

it's the latest kernel that ships with feisty. somewhere between the beta release of feisty and the final release a kernel update caused this problem. so any release prior to and including the beta release of feisty should be exempt from this problem. the resolution for my dad's system was to just install edgy, and it's working great. i'm going to wait until a kernel update comes out that has confirmed results that this issue is fixed before advising him to upgrade.

---

### Post by dreamspy on 2007-06-06
I had this problem to, but the cause seemed to be that I had a diskette with some drivers in the floppy drive. Removed the diskette and everything went smooth after that.

---

### Post by magisbladius on 2007-06-07
I've been having this problem ever since Dapper (never tried before it) with an ASUS PW5-DH Deluxe and PATA drives.

---

### Post by JackRnl on 2007-06-08
One thing is sure about that tty problem: installation of Ubuntu is NOT ok and something should be done about it by the people who are responsible for the distribution version. The way it is right now is just not good enough to be able to talk about a "distributionversion" .
One thing that might help would be adding an identification WHY the problem occurs so all those people (including me) who want to install Ubuntu but fail can provide USEFUL info to the developers and testers. Without it solving the problems will be very hard I believe and people will lose interest in Ubuntu.
So PLS generate a version that will allow to locate and identify problems SOON !

I gave it another and another try  and read several similar threads about the tty problem on other fora.
It seems it has been there for quite some time but no solution has been found and from Ubuntu nothing has come for several months now.
So for me it's over, I decided to NOT install Ubuntu but instead using Knoppix because that DOES boot and install normal. The reason I switch is the lack of support for this CRITICAL bug. I'm a software developer for over 25 years, but if i would deliver a product and it would show such behaviour I would either go back to the previous version ASAP and/or solve the bug within a VERY short period of time. I've had that kind of experiences and it's just not acceptable keeping people for a long time struggling with such a crucial thing like failing installation on MANY systems : the 7.04  version should have been removed from download or AT LEAST it should have bene told CLEAR it won't work on many occasions.

Hopefully Ubuntu will learn something from this bug

---

### Post by Iteo on 2007-06-10
Ok i need serious help. Im not sure if this is related but here i go. So I tried this disc(feisty livecd) on one computer with two harddrives and it gave me the error "can't access tty; job control turned off" with some other errors too. But then i tried this disc on a computer with 1 harddrive and it seemed to work perfectly. But back to the first computer, I reset and went into windows to make sure the disc was OK and it seemed to be so i restarted and then i received the BLUE SCREEN OF DEATH after windows' startup screen(it had not reached desktop). It said something about an Unmountable_Boot_Volume. I have tried everything i can and windows will only startup in safe mode. Did i corrupt the partition while messing around in busybox, did linux itself do it, or is my computer confused. Thank you for any help. Please this is _**URGENT**_ as I am about to delete my windows partition. Thank you.

~I'm a geek with a continuously broken computer....ironic isnt it?

---

### Post by kyrhash on 2007-06-12
Just thought i would post my exp.  I tried to install feisty from the live CD, since i have a Core 2 Duo processor i tried both the 64 bit version and the 32 bit version.  After burning the 32 bit CD i got this error so i went to the 64 bit and got the same error.  I then burned a third copy (32 bit) and that copy finally booted.  So i did some tests and found that between 1 in 5 to 1 in 10 times i booted the live CD booted fine.  I think at least some of the issues come from Jmicron SATA controllers.  I am a complete newb at linux (going on 3 months) so i may just be talking away.

---

### Post by garion on 2007-06-13
Linux Mint copies pretty much everything from Ubuntu as its core, including bugs naturally.  Linux Mint 3.0 does the exact same thing as Feisty Live CD on my Dell 4600 desktop, which is even worse because I realized that Mint doesn't even have an alternative cd that I could use.

I agree with JackRnl above that such error should be addressed in a timely fashion.  I've had other odd issues with Feisty such as suspending worked well with Feisty beta and got broken in the final version two weeks later and never got fixed.  Another example, Feisty beta cd booted fine on my laptop with ATI graphics, while the final cd just throws an error on starting X to many many ATI users.  There are a handful of bugs I am aware of like this on launchpad that keep sitting there as unconfirmed or confirmed but not acted upon.  This really starts to get a bit annoying, and make me question the model of releasing on a hard 6 month schedule.  It seems like that they rush to get one release out on time at all costs (of bugs), and then just forget about it and move on to the next release.  I can sort of understand why they couldn't afford correcting all these bugs, because they are so busy with Gusty now!  And is Gusty going to have similarly annoying bugs without being corrected?  Very likely.  Is that what we users really want?




> **serlex said:**
> people with this problem should try Linux Mint 2.2, it should install fine.

---

### Post by Skneepa on 2007-06-14
Hi everyone! I'm just trying to make my first steps in Linux and English is not my native language so please forgive any mistakes ;) ...I had the same problem booting from live CD and I managed to fix it by using the all_generic_ide command posted in the forum (sorry, I can't recall by whom exactly). However I did not install the OS yet, just booted and tried it for a while. I' ll install the next days and I ll post a reply of what happened. But I have to say some things that may help you with more experience go through a solution...First, I'm running on a C2Duo on MSI P965Neo-F. Guess what, Jmicron controller. I tried to install Ubuntu 6.10 and it stops after loading telling me something about JBR or something (means the Jmicron as I know) as headline and something about PCI and can't find something. I also had issues with this controller in Windows XP (BSOD leading to disk errors and NTFS.sys). MSI suggested removing all my drives from this controller and connecting them to Intel's native chip. No BSOD since then till now. Several fora are pointing Jmicron as Linux unfriendly. The problem in my case was that the only IDE port on mobo was Jmicron's. So I had to crap my old IDE HDD and DVD-RW and get new SATA ones. I connected both at Intel's SATA ports and had no problems. I can't even now get Ubuntu 6.10 working ( I'll try the all_generic_ide command there too) but 7.04 at least booted. So Intel CPU users try removing your drives from Jmicron and give a try. I would suggest disabling it from BIOS but I can't find the exact entry. If someone knows how to do so please post so we can try! Also try not using mixed SATA-IDE configurations, stick with just one of them. Sorry for the long post!

---

### Post by sangos on 2007-07-10
Relevant system Specs:
Processor: Intel P4
Hards Drives: 2 IDE-40 GBs each(slave and master)
OS: windows XP Pro (originally installed)

Tip:
Made sure that Windows was booting up normally and then booted from the Ubuntu Live CD to get Ubuntu desktop from the CD

Issue:
Got the error message after installing Ubuntu and restarting computer...freezes up at the Ubuntu splash/Progress Bar screen

Resolution:
1] Used Linux System rescue disk to invoke GParted: Edited Partitions
      a) Made the Ubuntu partition( ) a PRIMARY partition-did NOT make it BOOTABLE by the "manage flag" in GParted
          i} The partition was earlier "LOGICAL" which DOES not work
         ii} The BOOTABLE partition right now in GParted window is still set at MS Windows XP Pro
2] Used Ubuntu Live CD to install on to the Hard drive
      a) chose the manual option to partition the Hard Drive
          i} Set the Ubuntu Partition (mount point= /;file system= ext3)
      b) chose to install GRUB in the Ubuntu partition
          i} GRUB installs by default to the C:/ partition used by Windows and imposes itself on the MBR so it shows up on restart before the Windows bootloader
3] Used GParted again to make the Ubuntu partition bootable instead of the Windows XP partion
       a) Both the Ubuntu and Windows XP partions reside on the same Hard Drive ( IDE Master)
4] Restarted the computer
      a) Edited GRUB to select the default Operating system
          i} In my case I chose Windows XP as my default Operating System in GRUB

---

### Post by sangos on 2007-07-10
Sorry about the numbering above(the editor here does not work)

The Order of lines is 
 main comment  <Number> ]
 Sub comment                                        <Letter> )
 More Sub comment                        <Roman number> }

---

### Post by wpshooter on 2007-07-10
> **kyrhash said:**
> Just thought i would post my exp.  I tried to install feisty from the live CD, since i have a Core 2 Duo processor i tried both the 64 bit version and the 32 bit version.  After burning the 32 bit CD i got this error so i went to the 64 bit and got the same error.  I then burned a third copy (32 bit) and that copy finally booted.  So i did some tests and found that between 1 in 5 to 1 in 10 times i booted the live CD booted fine.  I think at least some of the issues come from Jmicron SATA controllers.  I am a complete newb at linux (going on 3 months) so i may just be talking away.

I don't think this problem is related to the "Jmicron SATA controllers (or at least not exclusively) because I have gotten this error on a system that I am very certain that does NOT have this Jmicron controller.

---

### Post by wpshooter on 2007-07-10
> **JackRnl said:**
> One thing is sure about that tty problem: installation of Ubuntu is NOT ok and something should be done about it by the people who are responsible for the distribution version. The way it is right now is just not good enough to be able to talk about a "distributionversion" .
One thing that might help would be adding an identification WHY the problem occurs so all those people (including me) who want to install Ubuntu but fail can provide USEFUL info to the developers and testers. Without it solving the problems will be very hard I believe and people will lose interest in Ubuntu.
So PLS generate a version that will allow to locate and identify problems SOON !

I gave it another and another try  and read several similar threads about the tty problem on other fora.
It seems it has been there for quite some time but no solution has been found and from Ubuntu nothing has come for several months now.
So for me it's over, I decided to NOT install Ubuntu but instead using Knoppix because that DOES boot and install normal. The reason I switch is the lack of support for this CRITICAL bug. I'm a software developer for over 25 years, but if i would deliver a product and it would show such behaviour I would either go back to the previous version ASAP and/or solve the bug within a VERY short period of time. I've had that kind of experiences and it's just not acceptable keeping people for a long time struggling with such a crucial thing like failing installation on MANY systems : the 7.04  version should have been removed from download or AT LEAST it should have bene told CLEAR it won't work on many occasions.

Hopefully Ubuntu will learn something from this bug

Boy, did you say a mouth full.  I agree completely !!!  They need to fix this PRONTO !!!

---

### Post by rbmorse on 2007-07-10
> **wpshooter said:**
> I don't think this problem is related to the "Jmicron SATA controllers (or at least not exclusively) because I have gotten this error on a system that I am very certain that does NOT have this Jmicron controller.

And it's not just Ubuntu, either. I have an Intel 965G chipset-based machine that installs Feisty just fine, but manifests the TTY job control error trying to boot the gParted LiveCD.

---

### Post by rcdeacon on 2007-07-11
I have personally posted on this issue also and for some reason not only has this problem not been fixed but it has not even been adequately addressed an any form. I am very, very disappointed in Ubuntu, a distro that is supposed to be on the "top of the heap" so to speak. I have not installed it and do not recommend it either.

---

### Post by Proleter on 2007-07-18
Same problem here. 
I have IDE hard drive(160GB WD), no floppy and Optiarc DVD RW.
I haven't been able to even boot the LiveCD. Tried also the Alternative CD and all recomendations in this topic. Every time the booting stops with ATA: Abnormal Status... except with  all_generic_ide and break=top tips,wich finishes with some failiure when trying to install Realtek Lan Card....
I'm using Ubuntu as my desktop operating system since Breezy and I'm not trying to bee linux guru... I just want simple operating system that does the job. But on this computer it can't even install...

---

### Post by r3r3 on 2007-07-19
This is so lame, it s been months! And nothing changed, UBUNTU will pay this big time and is already gathering bad feedback all arround the world.. well done!

---

### Post by splintercellguy on 2007-07-19
Excellent input, I suppose you have encountered this error before? I suggest reburning, or trying the tricks covered in the previous 24 pages.

---

### Post by bluknight on 2007-07-19
I copied vanilla kernel from Edgy 2.6.17-11-generic, initrd.img,   as well as the /lib/modules/kernel, /lib/linux-restricted-modules/kernel and the /lib/firmware/kernel folders onto Feisty /boot and  /lib file system, pointed grub to it and have been using Feisty over a month with no problems.

Now please can any developer tell me why *that works?* :confused: Could it be the initramfs which Edgy doesnt use??

---

### Post by r3r3 on 2007-07-19
The tricks in the previous 24 page? Are you kidding? What we need is a real fix not some ****** up work arround, seriousely this is messed up, do you really think that standard computer peoples will open their computer and trying to unplug hardware to be able to install ubuntu? Very funny...

---

### Post by Shaun Olsen on 2007-07-19
Thought I would finally give Ubuntu a try after all the good things I've heard about 7.04 and the many many digg posts about how Linux in general isn't actually as difficult to install as people think and how Ubuntu has come a long way in user-friendliness.

Tried to install this on my 975X chipset using the Intel ICH7R SATA Controller and get this error. Unplug my Raptor and just use an IDE drive on the JMicron controller and still the exact same thing.

That's it, I just wanted to try something new, not interested in jumping through hoops spending a lot of time just to get this running. Guess I will be waiting for the next major revision to be released. :popcorn:

Rant over, seeya guys in a couple of months I guess.

---

### Post by sk8dork on 2007-07-19
can anyone that has the problem with 7.04 try booting with the latest gutsy tribe 3 live cd? i downloaded it and burned it and it booted fine on a dell latitude d620, but that's not really saying a lot since the machine never had the problem in this thread. i plan on having another person test this out, but perhaps some of you could try the same. just because this thread get's no 'fix is in the works' posts doesn't mean that they aren't actually working on fixing it.

---

### Post by Bossieman on 2007-07-19
> **sk8dork said:**
> can anyone that has the problem with 7.04 try booting with the latest gutsy tribe 3 live cd? i downloaded it and burned it and it booted fine on a dell latitude d620, but that's not really saying a lot since the machine never had the problem in this thread. i plan on having another person test this out, but perhaps some of you could try the same. just because this thread get's no 'fix is in the works' posts doesn't mean that they aren't actually working on fixing it.

Still the same problem for me with Tribe 3. I have a Zepto Znote 6324W

---

### Post by r3r3 on 2007-07-20
okay, downloading gusty tribe 3, i sincerly hope it'll works

Edit: still the same deal :_(

---

### Post by sk8dork on 2007-07-20
hmm. it's bad now, but if it's not fixed by gutsy final then it'll be a bigger and lamer problem than ever.

---

### Post by Bossieman on 2007-07-20
> **sk8dork said:**
> hmm. it's bad now, but if it's not fixed by gutsy final then it'll be a bigger and lamer problem than ever.

That would be a disaster imo. Does anyone know what is done to fix this?

---

### Post by errenay on 2007-07-21
I have encountered the same problem.

System: Acer Aspire 5920G (Centrino 2 Duo 7300, 2 GB RAM, chipset Intel 965G, GeForce 8600 M GT with 256 MB, 160 GB SATA), system: Vista Premium 32 bit, trying to install: Kubuntu 7.04 LiveCD 64 bit.

Without kernel options ```
quiet splash --
``` I could see the messages. First ```
/bin/sh: can't access...
``` was without any previous warning. I have used
```
modprobe ata_piix
exit
```
It has helped a little. However, there was another error:
```
cp unable to open '/root/var/log' no such file or directory
Begin: Running /scripts/init-boyyom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```
And that's all... :( I have tried
```
modprobe piix
modprobe ide_generic
```
but it doesn't help. I'm too green to know what I should do next. But I hope it helps somebody to understand this problem. Thank you in advance for your help.

---

### Post by Shootfast on 2007-07-21
Hi guys, not sure If you have the exact same problem as I did, however on my system, I was able to boot to live cd, and it would crash to busybox after I ran native.

I narrowed it down to the initrd image created by the installer, turns out the one included in feisty wasn't too great at detecting some motherboards / system hardware.

I had to download the alternate cd, choose repair installation, get to a command line and download yaird (Yet-Another-Initial-Ram-Disk) (sudo apt-get install yaird) then use yaird to replace your initrd image.

Hope that works for someone

---

### Post by Proleter on 2007-07-21
Well I give up.
Tried:
Breezy - Can't recognize the CD
Dapper - Can't access tty
Feisty - Can't access tty.

I run:
Abid IB9 mother board
160 GB IDE hardisk
1024 MB Ram
Optiarc DVD RW
No floppy

I had to install windows with some kind driver created through ITE IDE Controller Driver Disk Maker ...

I give up for now better...

---

### Post by Pumalite on 2007-07-21
This is a mix of fixes I have collected from different places. See if one fits you and apply it. ( I hope they haven't been mentioned in this thread before; I didn't have time to read the whole thread):

when I boot, the screen shows

Starting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by tredegar on 2007-07-22
Pumalite,

I have been meaning to thank you for your post at [http://ubuntuforums.org/showpost.php?p=2553305&postcount=133](http://ubuntuforums.org/showpost.php?p=2553305&postcount=133) (in this thread, and improved-reposted again, above)

My hardware: Sony Vaio VGN-FZ11L, 120GB SATA drive, 2MB RAM, 
It would not boot 6.06.1 at all and 7.04 froze at "configuring pcmcia". Not surprising as this laptop doesn't have pcmcia! 
Interestingly, knoppix 5.1.0 booted up just fine, so I knew linux was possible on this hardware.

So I tried booting 7.04 with **nopcmcia** as a kernel option. This was better, but then I was dumped at the "can't access tty; job control turned off" screen.

After a couple of hours of googling and getting nowhere, I found your post, which I followed  to the letter (adding **nopcmcia** as well as **break=top** to to the kernel options ) and 7.04 finally booted OK, except that I had to use knoppix's xorg.conf to get X to run (using the vesa driver).

Once I had 7.04 installed and running I was able to fix up xorg.conf, and install NVIDIAs driver (driver 100.14.11 is needed for this laptop).
Wireless worked "out of the box" so long as I had the kubuntu "restricted-modules" loaded, but these included the xorg nvidia driver which conflicted with NVIDIA's own driver. The solution:

Make sure the files **/etc/init.d/nvidia-glx** and **/etc/init.d/nvidia-kernel** do not exist (delete them)
Edit** /etc/default/linux-restricted-modules-common** so it contains this line:
**DISABLED_MODULES="nv nvidia_new"**
If the file **/lib/linux-restricted-modules/.nvidia_new_installed **exists, delete it (note that it's a "hidden" dot file. Then install the NVIDIA driver.

Much happiness,:)  it was worth a day's experimenting & googling. Everything works perfectly after I had instaled livdvdcss, flash, sun's java etc. etc. Your post saved me!
Many, many thanks!

---

### Post by Pumalite on 2007-07-22
You are very welcome. Glad to be able to help you. Enjoy!

---

### Post by Sir Funk on 2007-07-22
After trying both the LiveCDs and the Alternate CDs for Ubuntu 7.04 & 6.06, Kubuntu 7.04, and Xubuntu 7.04, I've finally been able to install using the Alternate CDs by adding "irqpoll" to the command line when installing.  Using this, I can get a LiveCD to boot (although it is EXTREMELY slow and will freeze at the same point every time if I try installing using the LiveCD).  Once installed when I try to boot up I will be (eventually) thrown to the initramfs prompt and none of the proposed solutions in this thread will work (yes I *have* read all 26 pages).  

I've been trying to get Ubuntu to work for about a week now to no avail.  One final solution I'd like to try is one that I found on the Super GRUB Disk website.  It says that the UUID assigned to root on the line that begins with Kernal when Ubuntu boots is not correct.  Does anyone know how I can find out the UUID to see if it is correct or not?  I've tried ls /dev/disk/by-uuid/ -alh at the (initramfs) prompt, but it does not find this because as far as my understanding goes, that I am only at a virtual filesystem that's stored in RAM and not the one on my hard drive, where this information might be found.

If I'm able to boot from the LiveCD without it freezing (questionable), is there some way to determine my disk's UUID?

I'm beginning to agree with others--this is getting ridiculous.

-Funk

---

### Post by r3r3 on 2007-07-23
ok booting into a decent system (debian) and unlinke this crappy ubuntu, it works!
à bon entendeur...

---

### Post by vacation on 2007-07-25
1st time user. 
downloaded alternate of kubuntu ,installed it but it didn't boot.Grub was not installing.
So downloaded xubuntu live, and was getting 
"/bin/sh:can't access tty;job control turned off"
Plugging in my FDD from my old P3 worked like a charm.
Just put in a useless floppy,don't even know what's in it.
Thank You!!

---

### Post by bluknight on 2007-07-25
> **Sir Funk said:**
> 
If I'm able to boot from the LiveCD without it freezing (questionable), is there some way to determine my disk's UUID?
-Funk

root>blkid
OR
root>vol_id /dev/sd? | grep UUID

---

### Post by errenay on 2007-07-27
OK. At last I have managed to boot from LiveCD (Kubuntu 7.04, 64 bit, Acer Aspire 5920). I have used additional option
```
all_generic_ide
```
for kernel during booting LiveCD and "safe graphics mode" to start KDE.

---

### Post by aftertaf on 2007-07-30
I just killed my system by going gutsy too early :) and so i reinstaled fresh with feistylive cd

To get live cd to boot, i had to F6 and add break=top , then boot
once booted, ran install... then mounted new install chrooted and added piix to /etc/initramfs-tools/modules
then ran update-initramfs -u,
exit and reboot
On reboot still doesnt work: drops to busybox with same error:
i type modprobe piix, exit
then it boots to a maintenance (ctl+D) prompt. I press Ctl+D and it boots ok.

I have also added piix to /etc/modules to make it load this ok, no joy
Since then i have dist-upgraded (2.6.20.16 tested, same problem)

I have a SATA controller, and  IDE controllers.
I have IDE primary disks (hda, hdb) and a dvdrw (hdc)
i dont have any sata drives, but i cant deactivate sata completely in BIOS.

but when it blocks to begin with, all I do is modprobe piix, exit then I can reboot.
Any way I can get it to use piix instead of other modules that are making it hang?


I will try redoing the same steps in these 2 modules files, with the ata_piix module too and report any success i get.

---

### Post by ncwalker on 2007-08-04
I had the same problem on a Compaq Presario 5000.  Using the Feisty LiveCD I inserted a floppy and selected install and it worked!

Thanks!

---

### Post by ronc55 on 2007-08-05
As you can see there seems to be several fixes becoming available.  Some work some don't.  In frustration I went to a different distribution and attempted an installation.  It too aborted with the standard tty error message.  I booted it again and pressed F6 at the opening screen and erased the quiet splash option at the end of that line.  This makes the installation viewable on the screen as you go along.  Just before it aborted with the tty message it complained of an irq conflict on my machine and suggested using "irqpoll" .  Being a newbie to Linux I wasn't sure where to put that but ..

I rebooted, selected F6, erased the quiet splash and the dashes.  I then added irqpoll and it installed or at least gave me a running version of it.  I didn't install it.  Made me wonder if it was possible to do the same thing with Fiesty Fawn - Yep it worked.  I have the desktop on my machine as we speak - I have not hit the install button but I got this far - yeah!!

So erase "quiet splash --"  quotes are mine after pressing F6 at boot.  Add "irqpoll" and running it.  Just let it run, there are several pauses along the way, but they are just that.

Hope this helps.  I have an IBM Laptop, R30 with 30 gig and 384 mem.  Pentium III @ 900 mhz.  Stock except for the added memory.

---

### Post by StylusPilot on 2007-08-07
Hi,

I would just like to note my experiences.

I too had this "can't access tty" error.

Firstly I will note my configuration incase anyone has a similar setup.

AMD Athlon XP 2500+
Nvidia nForce 2 Chipset
ATI X1600 Video Card
0x IDE Devices Connected (All IDE ports disabled in BIOS)
1x  SATA Hard Disk (320GB Seagate)
1GB RAM
USB Keyboard and Mouse

I wasn't able to simply use the Alternate CD, as I have a USB DVD ROM, and the Alternate CD doesn't have the driver integrated. Rather than mess about with putting a driver on the Alternate CD I tried to get the Live CD working.

After reading this long thread, I tried the following.

the "all_generic_ide" method
the "modprobe piix" method
the "irqpoll" method
and all 3 method togethor

I was still not able to boot. I tried all of these on the following distributions.

Fiesty Fawn
Gusty Tribe 1
Gusty Tribe 2
Gusty Tribe 3

In the end for me, it turned out to be USB related.

All I did was go into the BIOS, and manually set the USB ports to 1.1 mode instead of the default USB 2.0/1.1

I was then able to boot into the Live CD no worries.

Just thought I would share In case its something people havn't tried yet.

Cheers.

EDIT: For me, I can now confirm the install works fine from the Gusty Tribes 3 CD, after I made my BIOS Change. I will now change it back to USB 2.0 and see if the problem start again.....

EDIT 2: Problem doesn't come back when I enable USB 2.0 Support. So this was the fix for me. Install once the BIOS has ben changed, then change back. Anyone else having problems wanna try this method?

---

### Post by ralic on 2007-08-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also spent the better part of a day trying to resolve this. I just couldn't get anything to start successfully from the Feisty 7.04 live cd (Including the scan for defects option!). In the end I managed to succeed by getting the piix module loaded at the start of installation.

I followed this advice:
> 
Here are steps to workaround the problem during the installation process:

  1. Add break=top to the kernel cmdline
  2. At the prompt, run: modprobe piix
  3. Then exit

And, here steps to make the workaround permanent after an installation:

  echo blacklist ata_piix | sudo tee -a /etc/modprobe.d/blacklist-ata
  echo piix | sudo tee -a /etc/initramfs-tools/modules
  sudo update-initramfs -u
  sudo reboot

The problem should be fixed for the first SRU release of Feisty.


From here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/30]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/30")

There is similar advice already in this thread, however I believe that the advice on making it a permanent feature is quite useful.

I followed the advice to make it permanent and that allows the system to boot without manual intervention, however it is necessary to follow the first 3 steps each time I need to boot from the live cd.

**One very important thing to note.**
After the initial installation, my default grub boot up item included the option "disable=top" on the *kernel* line. This caused the automatic boot to fail and drop immediately into initramfs just as in step 1 above. I removed it (hint: edit /boot/grub/menu.lst) and then boot up was automatic as expected.

Hope this helps someone else.

---

### Post by jtrent on 2007-08-09
I too found that the workaround of placing a floppy in the drive worked just fine.

This is on an old HP Pavilion XT846 with a 800 celeron and 256 mb ram.

I even went so far as to disable the floppy controller in the bios and physically disconnect the drive but to no avail.  It seems that it requires the floppy to boot the live cd.

---

### Post by logos34 on 2007-08-10
Strange...I didn't have this problem using the 7.04 .iso I dl'd and burned to cd-rw.  But I ran into it using the ShipIt CD.  My solution was different than everyone else's: I had left a floppy in the drive and had to take it OUT...Seems it tries to access the floppy drive right when the Ubuntu splash logo with loading bar appears.

---

### Post by de_valentin on 2007-08-12
I have the same problem with my new pc, thelive cd works on every other computer in the house but not on the new one. For me the "all_generic_ide" seems to work. But somehow the nice experience I had with Ubuntu is now almost gone since it fail to recognize any part of my new pc (or at least so it seems)

Reading through the forums I did notice people with the same machine setup so that shouldn't be the problem....

I hate to say it but for now this new pc will become an all xp pc with some unpartitioned space left unused untill Ubuntu figures this out.

my setup:
MSI P35 NEO
Intel core 2 Quad 6600
Asus EN8600 GTS
Western Digital 500 Gb SATAII

---

### Post by Prey2God3 on 2007-08-12
Its 7 in the morning... I've been up all ...nite trying to get this F..ing thing to werk...
I didnt go through all the 200+ bulletins so i donno if anybody else got this...
All i did was get pissed off and walk away  for about 10 mins and... YEAH THATS IT... ALL YOU GOTTA DO!

I do not have a floppy drive and i had it disabled in bios...

If your box hangs completely disable it in bios...
That brings you to the /bin/sh: can't access tty...
then your in inittramfs...
then you get some floppy errors...

DONT TOUCH ANYTHING... JUST WALK AWAY!

THERES LIKE A 5-10 minute delay where it seems hopeless... But then it skips the floppy and boots normally...

...It took me like 8 hours to figure that sh!t out... i hope this helps somebody...

Windows at least has an hour glass...

---

### Post by todak on 2007-08-12
7.04 works perfectly for me, but when I tried to boot up 7.10 livecd, error appeared. I tried the "all_generic_ide" boot command and lo! and behold, it booted to a desktop! =D>

7.10 herd5 desktop reverts back to busybox on booting. With alternate cd boot takes about 5 minutes, then goes straight into the install gui!?!

---

### Post by de_valentin on 2007-08-14
the "all_generic_ide" made it work but the grafics were almost vga, and that is not pretty on an 19" screen.

But today I came across this one "generic.all_generic_ide=1" and that made it look like it should.:)

---

### Post by JG6_oddball on 2007-08-19
for 2 hours i have been trying all (almost) workarounds to no avail :( feisty installed fine on my HP 7955 but this old gx100 optiplex  is a nightmare...i got suse10.2 on there right now but i want ubuntu...anyonre have a GX100 that found a solution?

S!

---

### Post by geraschenko on 2007-08-23
For what it's worth, here is my experience installing 64-bit Kubuntu 7.04 on the following system.
Dell Vostro 1500
video card: nVidia GeForce 8400M GS
processor: Intel T7300
lspci output:```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```
(Let me know if there is anything else about my system I should add here.)

The problems:
(1) The livecd wouldn't boot.
(2) Once (1) was solved and Feisty was installed, it would break when I updated the kernel from 2.6.20-15 to 2.6.20-16. Updating the kernel would change my /boot/grub/menu.lst (to include the "break=top" option), and no amount of messing with it would allow me to boot either kernel.

What worked for me:
(1) dannyboy79's approach here:
[http://ubuntuforums.org/showpost.php?p=2525421&postcount=1](http://ubuntuforums.org/showpost.php?p=2525421&postcount=1)
but I had to boot in safe graphics mode (in addition to the "break=top" and "modprobe piix" business).
I don't know what the piix module does; could somebody please tell me or tell me how to find out?
After the install, my /boot/grub/menu.lst had the "break=top" option, so I removed it and everything worked (until the kernel upgrade).

(2) After I got the new kernel through adept-updater, but BEFORE rebooting (this wasn't my first attempted installation), I installed
[http://people.ubuntu.com/~scott/packages/initramfs-tools_0.85eubuntu10_all.deb](http://people.ubuntu.com/~scott/packages/initramfs-tools_0.85eubuntu10_all.deb)
Then I removed the "break=top" options from /boot/grub/menu.lst and I could reboot.

This is more or less Ipsissimus' approach here:
[http://ubuntuforums.org/showpost.php?p=2547102&postcount=2](http://ubuntuforums.org/showpost.php?p=2547102&postcount=2)
I'm sure it would have worked if I booted from a CD, mounted my hard drive, and chrooted, or if I'd booted in recovery mode after the kernel upgrade, but that's not how I did it.

---

### Post by jim.hitch on 2007-08-25
Thanks klytu. Weird perhaps, but it worked.

I was trying to boot and then install from the Xubuntu Live CD on an Acer C100 (external CD/DVD 1394 firewire) and getting the install error which this thread refers to.

Simply plugging in the USB 3.5" with a random diskette in it worked. :KS

Jim

---

### Post by veliro on 2007-08-26
Can anybody tell me if the problem is solved?
I want to install feisty on my computer here now, last time i tryed i got the tty error. This happend a long long time ago, so i want to try again.

Is it fixed, or is Edgy the way to go?

---

### Post by EliWCoyote on 2007-08-26
Thank you for your help!  If you're installing Feisty to a PC that has a floppy drive in it, I strongly recommend inserting any floppy and trying the install again; it worked for me, thanks to you guys.  :-)  Any old floppy, including unformatted floppies, seems to work.

---

### Post by veliro on 2007-08-27
I simply moved one PATA disk from the controller on the main board too a Promise controller. The Promise controller made the disk look like an SATA disk.

Now everyting works :)

---

### Post by Thunderck on 2007-08-27
So I'm in the mix on this too.  One thing I have not seen or seen explained is...

I cannot boot OS from any grub config line.  

I can boot from LiveCD 7.04, 6.10, 6.04.

When I try installing from LiveCD I only see 1 disk hda1.

From fdisk I see 7 disk, hda1-hda7. (which is my ntfs XP, and linux partitions)


In conjuction with this tty issue does anyone know why I cannot see my drives from LiveCD but I can from fdisk????   :mad:

---

### Post by mbetti on 2007-08-27
I found a workaround for this problem trying install ubuntu on Travelmate.

Simply add "noapic irqpoll" to kernel option (f6 on boot from live cd).

You have to specify these kernel option also on the next boots.

Regards,
Maurizio Betti

---

### Post by mentholphetamine on 2007-08-29
I'm a newbie here and also to Linux / Ubuntu.Thanks for all who have posted their workarounds. Especially for: maudalo 

After two weeks, I finally got my Feisty to work.
I'm using an old Acer TravelMate 529TX (I saw someone posted the same model somewhere with the same problem, I hope you fix it at last!) comes with a PIII 850MHz / 256MB / 20GB / CDROM / FDD.
I got the 'searching to floppy drive' problem and finally can't access tty.
This is my workaround:
1. Boot the liveCD and press F6 for options
2. At the beginning add break=top pci=noacpi
3. I delete the quiet spash so I can see the process
4. At the break type: 
modprobe ide_cd
modprobe isofs
modprobe piix
exit 
(inspired from: [http://ubuntuforums.org/showthread.php?t=1625&highlight=hdc%3A+lost+interrupt](http://ubuntuforums.org/showthread.php?t=1625&highlight=hdc%3A+lost+interrupt))
but I delete the modprobe ide_generic (I think it's causing some problem)
5. I got it to run into liveCD

Hip Hip Hoorayyyyy. Hope this work for you guys!

Greetings from Indonesia!

---

### Post by Swarms on 2007-08-29
> **mentholphetamine said:**
> I'm a newbie here and also to Linux / Ubuntu.Thanks for all who have posted their workarounds. Especially for: maudalo 

After two weeks, I finally got my Feisty to work.
I'm using an old Acer TravelMate 529TX (I saw someone posted the same model somewhere with the same problem, I hope you fix it at last!) comes with a PIII 850MHz / 256MB / 20GB / CDROM / FDD.
I got the 'searching to floppy drive' problem and finally can't access tty.
This is my workaround:
1. Boot the liveCD and press F6 for options
2. At the beginning add break=top pci=noacpi
3. I delete the quiet spash so I can see the process
4. At the break type: 
modprobe ide_cd
modprobe isofs
modprobe piix
exit 
(inspired from: [http://ubuntuforums.org/showthread.php?t=1625&highlight=hdc%3A+lost+interrupt](http://ubuntuforums.org/showthread.php?t=1625&highlight=hdc%3A+lost+interrupt))
but I delete the modprobe ide_generic (I think it's causing some problem)
5. I got it to run into liveCD

Hip Hip Hoorayyyyy. Hope this work for you guys!

Greetings from Indonesia!

My Znote 3414W went working with that procedure!
Thanks alot!

---

### Post by mentholphetamine on 2007-08-30
additional info:

for my acer, if I add modprobe ide_generic it will caused this problem:

**hdc: lost interrupt**

---

### Post by Swarms on 2007-08-31
> **Swarms said:**
> My Znote 3414W went working with that procedure!
Thanks alot!

Ok a little addition, tried Gutsy tribe 5, didn't work without the commands, and neither with.

---

### Post by mentholphetamine on 2007-09-01
another problem, maybe i should buy a new laptop *sigh*

I've installed my FF all the way through. But after I press Restart Now, my laptop indicated there was a problem and the system freeze. So I reset the laptop but during the bootup (the Ubuntu logo with the moving bar, the system freeze). Anybody have any idea what happen and how to fix it?

Much appreciated!

---

### Post by shaolintl on 2007-09-03
I had similar problem with tty and an additional one about intel_rng something when trying to install Kubuntu Feisty from live cd. I also tried upgrading (dapper - edgy - feisty) which had the same results. I tried to install Ubuntu (without the k) from the live cd and got a different error message there is some problem with identifying my graphics card.
I tried the upgrade again and this time I have installed the proprietary driver for the ATI graphic card before the upgrade to Feisty and it worked this time.

---

### Post by Dukaso on 2007-09-13
I posted this in its own thread but I might as well post it here as well

I've recently decided to give Ubuntu a shot and I'm having an issue installing it.

HP Laptop with
2gb ram
Nvidia 8600m gs
Intel centrino duo 2.0ghz processor
150gb hdd with a 130ntfs windows partition, 8.34gb recovery partition, and 10gb (to be)Linux partition in Fat32
Windows Vista Home Premium
Ubuntu 7.04 CD
WUBI with a Kubuntu virtual disk on both my windows partition and linux partition. I could probably install it from that but I'm more interested in solving this problem.

My Problem:
Everything works fine up until the part where I select the option to run and install Ubuntu after booting from the CD. A memory allocation error flashes for roughly half a second and a command line saying "/bin/sh: Can't access tty; Job control turned off" comes up.

What I know thus far:
The CD I burned works. My roommate installed Ubuntu to his laptop without any problems.
I've tried five different Ubuntu and Kubuntu CDs so far and they've all produced the same error.

What others have suggested:
Vista is being obstinate
I did something wrong with my partitioning

---

### Post by CaptainCool on 2007-09-20
I'm also having problems installing ubuntu form the live CD.

Starting and installing ubuntu gets past the loading bar screen (where it has ubuntu and a loading bar) and then stops with "can't access tty...etc", same with graphics safe mode and CD check.

Computer specs:

E6750 C2D processor
Asus P5K SE motherboard
8800gts graphics
onboard realtek HD sound
onboard Attansic L1 Ethernet controller
2x 500gb samsung spinpoint HDs
pioneer dvd rw

First hard disk has windows xp installed on it

Hope you get round to fixing this, I'm downloading the alternative iso atm.

---

### Post by danensis on 2007-09-21
I get the error message on a brand new novatech Rasor:
Santa Rosa T7100 15.4" - Intel Core Duo T7100 1.8 2048mb Ddr2 160gb Sata Hdd

Screen 		15.4" WXGA X-Brite 1280 x 800 TFT Screen
Processor 		Intel Core 2 Duo T7100 1.8Ghz 2Mb Cache Processor
Processor Speed 		2x 1.8Ghz
Memory 		2048MB DDR2 667MHz Memory
Hard Drive 		160GB SATA Hard Drive
Drive 		DVD/RW Multi Burner
Modem 		56K Internal Modem
AGP Graphics 		Intel GMA X3100 Graphics
Sound 		7.1 Azalia High Definition Audio
Speakers 		2 x 1 Watt
Memory Slots 		2 x DIMMs
Memory Capacity 		4GB
Audio In Port 		1 x Mic-in
Audio Out Port 		1 x H'phone/Speakers
Networking Port 		10/100 LAN & 54G Wireless LAN
Ext Monitor Port 		1 x External Monitor Port
RJ11 Modem Port 		1 x RJ11 Modem Port
Power Socket 		AC Power Adapter
TV Port 		1 x S-Video Out
USB Ports 		3 x USB 2.0
PCMCIA Port 		1 x Express Card Slot
Bluetooth 		Yes
AC Adaptor 		AC Adapter Supplied
Internal Battery 		6 Cell Lithium Ion Battery
Touchpad 		Glidepad with 2 buttons
Scroll Button 		1 x scroll button
Notes 		4 in 1 Card Reader

Feisty Fawn live CD - goes through boot-up process, get oscillating progress bar, then the 
" /bin/sh: can't access tty; job control turned off"  error message.

I thought it might be because the hard disk wasn't partitioned, but the live CD doesn't seem to cope with this, so I installed Mandriva and that works fine.

---

### Post by frychiko on 2007-09-22
I finally gave up on this problem and bought a new motherboard. Gparted was also giving me the same problem. I had another big issue with the motherboard anyway, it had to go.

---

### Post by fca_neo on 2007-09-25
I had the same problem and solved it by putting a diskette in.

My setup:
AMD Athlon 1GHz
640 MB sdra
two ATA HDs
a CD-RW
a DVD
GForce 3 64 MB
and some other misc hardware

I hope this helps

---

### Post by Prymalfury on 2007-10-01
I have a Toshiba Qosmio, HD DVD RW, Centrino Core 2 duo 1.8, 250 gig hard drive, Intel graphics x3100, 2 gigs of ram, and I got that same result. 

I have not had the time to play with the installation error yet, but I will have time tonight when I get out of class.

---

### Post by UbuntuKhan on 2007-10-02
Wubi install on a Windows Xp mahine. I have the boot screen with the options Win and Ubuntu but when I choose Ubuntu it stops after a little while (I can see the splash screen with the bar only a little bit orange) and then it spits: /bin/sh: can't access tty; job control turned off    initramfs). The Hard Disks (2 on this machine) are in a raid0 configuration. I don't know if that has something to do with anything. Also the video card is Ati based.

---

### Post by roaldz on 2007-10-02
I'm having the same problem when booting Feisty livecd: /bin/sh: can't access tty; job control turned off - And then the floppy errors and so on. I Can't fix it with putting a floppy in. Don't have a cd burner around, so can't try alternate cd.
I've also tried wubi, that worked, but ntfs-3g is soooo slow, it's no good for a decent workstation, not even an impression of what it could be.
Could there be a way to port the wubi installation over to the main disk partition? That would solve my problem. Is this done before?

Greetz

Roald

---

### Post by digger82 on 2007-10-03
I have had Edgy working for a long time without issue

Downloaded Feisty and cannot boot - i also get the tty issue

This gives me the shits, since there was clearly not enough pre release testing for so many people to have this problem

Is it possible to re-install Edgy without losing what's on the hard drive?

---

### Post by andrewnroth on 2007-10-04
hi i dont know if i am asking in the right place, i am completely new to linux,  i am installling ubuntu 7.04 on my new computer,  

after the installation menu occurs and iclck install ubuntu i get some message saying something about ram but the screen changes before i can read it, the it goes into a program called busy box and i get the error:

can't access tty; job control is turned off.

can anyone help me with this?

i have seen other people have posted their specs so i gather this ay help:

Sony Vaio
Intel Core2 Duo CPU @ 1.8GHZ
2046MB RAM
32-bit operating system

Thanks

Andrew

---

### Post by r3r3 on 2007-10-05
hello, just downloaded the last gusty beta, it's getting better, but still aint booting into the live cd, when i boot with default parameters, it's almost booting to the live cd's desktop, but block just before i can see the mouse cursor, but the rest is black, when i add break=top pci=noapci to the boot command, then i m getting tty error directly... :/

my specs are
Asus p5b deluxe wifi
C2D 6320
8800 gts 320
Audigy ZS
promise fasttrack s150 sx4 with raid 5
2GB ocz platinum pc2-6400

---

### Post by r3r3 on 2007-10-05
edit: double post

---

### Post by Her Ghost on 2007-10-07
Getting the same error, but a bit confused as to why:

I have been running Kubuntu 7.04 (64bit) for about 6months now and the installation on that went fine.

I decided to go for Kubuntu 7.04 (32bit) but when I try to install I get the "can't access tty" error.  This is exactly the same when I try for Ubuntu 7.04 (32bit).

Seems odd that I can have the 64bit version working perfectly, but not the 32bit version?

---

### Post by merado on 2007-10-14
I literally tried every workaround in this thread. Nothing worked. 64 bit didn't even give me an error, just a black screen.  Though my Intel Core 2 Quad q6600 should do the trick. However I'm so glad I finally got it working!
I used Ubuntu 7.10 RC 32 bit and it started up without a hassle. No boot parameters were necessary.
I hope we can say "Problem Solved".
I was already near giving up and installing an other distro, but now there is nothing speaking against using the best one :)

---

### Post by silvercliff on 2007-10-18
problem not solved.  i am using the 7.10 release and i am still getting this crap.  i am getting the i386 alternate cd now.

---

### Post by PakSiw on 2007-10-18
Linux in general is quite consistent on this kind of weirdness. Have you ever encountered a new release of Windows will not work properly while the previous one does?

---

### Post by Swarms on 2007-10-18
7.10 solved it for me, now everything works except Intel HDA sound.

---

### Post by Maassive on 2007-10-20
I am trying to install Ubuntu 7.04 off the live CD (that just came in the mail) onto my Toshiba (currently running on Ubuntu 5.10) and get error message:

/bin/sh: can't access tty; job control turned off 

I am highly illiterate when it comes to Linux, but seeing that a number of problems may be the cause of the problem, I hope that someone may have figured out how to deal with this problem on an 1998 Toshiba portege CTe series running on a pentium III.

When I prompt for "help" after the error message,  I get:

Built-in commands:
-----------------------

. : alias bg break cd chdir command continue echo eval exec exit 
export false fg getopts hash help jobs kill let local pwd read
readonly retrn set shift times trap true type ulimit umask unalias 
unset wait [ [[ashbasename busyboxcat chmod chroot chvt clear
cmpcpcut deallocvt dumpkmap echo egrep env expr false fbset
fdflush fgrep grep hostname ifconfig ip kill ln loadfont loakmap
lsmkdir mkfifo mknodmkswap mktemp more mount mv openvt printf
ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort
stat sync tail tee test touch tr true tty umount uname uniq yes

---

### Post by aymanmaharek on 2007-10-22
Welcome to all of you fine 
Now, the site of the ISO file and Hrgueth and Stabth and worked well, and I happened to you want produced hard again on the same organ after I separated the hardware that was my hand a letter written by male Books Group mistakes and worked all attempts ISO and burned again but again I Mrdic Itstab benefit soon soon as possible, and thank you very much 
Note 
What message are as follows aged 
Busy Box v1.1.3 (Debian 1:1.1.3 - 3ubuntu3) Built-in Shel (ash) 
Enter help for a list of built-in command.s 
Thank you:guitar::guitar:

---

### Post by xyphur on 2007-10-29
I can confirm this is still happening under Gutsy (7.10) FINAL. System is an IBM eServer xSeries 232 (type 8668-27X)

Based on a ServerWorks chipset, with integrated Adaptec u160 SCSI and 6 x IBM 10k 18.2GB SCSI drives, and a single IDE DVD-ROM drive (only IDE device in the system - in fact it's only got one IDE bus for a supported total of 2 devices max.)

None of the workarounds posted anywhere have worked. The only way I will likely end up with Gutsy on this machine is by installing Edgy, then doing a dist-upgrade like I did when I went from Edgy to Feisty.

This is a major issue, and must be fixed. Too many users with highly varying hardware configurations are experiencing the same crap.

---

### Post by defZA on 2007-11-02
I get this error when I have two SATA's and 2 PATA HDD's plugged in.
Two SATAs work fine.
1 SATA and 1 PATA work fine.
Motherboard: Asus PK5-VM

[SIZE="4"]A work around is to press CTRL-ALT-F1 when Ubuntu is booting.[/SIZE] It only seems to happen when the boot screen (GUI loading screen) is showing, pressing Ctrl-Alt-F1 switches to a terminal till Ubuntu is finished booting up and this error doesn't occur.
Any of the Function keys (left Alt-Ctrl-F1-F6) will work, not just F1.

I use Ubuntu 7.04 (aka Feisty)

---

### Post by strikeback03 on 2007-11-04
I downloaded 7.10 64bit and installed on my work computer, went flawlessly.  That is a P35 chipset (MSI P35 Platinum board) and a Q6600.  Brought same CD home to install on my home system (P965 chipset, E6600), and it throws the same error as the Feisty CD did.  all_generic_ide let it at least boot, but it hung shortly thereafter.

---

### Post by gwhlevy on 2007-11-18
I just helped a friend build a new PC from the ground up.  Intel dual core processor, an all Intel motherboard, a WD 250 GB harddrive, no floppy, DVD+/- CD combo drive, 2 GB RAM.

I tried to run Gutsy Live DVD on his machine and I get that same thing:

Busybox v1.1.3 (Debian 1:1.1.3-3 Ubuntu 3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

I feel ***very*** embarassed by this.  My friend spend a good bit of money to build this PC to be faster and better, and he was looking forward to trying Ubuntu.  Right now it's just a WinXP machine (what he had before.)

 I've built many PC for people (and myself) and this is the first time I've run into this.  I sure would like an answer on this.  I wanted to introduce my friend to the "joys of Linux", instead of seeing him just load WinXP all over again on a new machine!

---

### Post by rleon on 2007-11-18
Linux has problems to boot from  IDE DVD drives used with modern mainboards along with SATA HDs under the same hood. If you have an IDE DVD drive like me you have to options: either upgrade to a new SATA unit or, like me, buy a cheap serial ATA to IDE converter card that plugs to the IDE drive (it also requires power) and connects to a Serial ATA port. You have to enable SATA AHCI mode in BIOS setup  (generally this is not the default option). Linux will be happy now and boot from the DVD as the latest kernels have the required drivers for SATA drives. You could also boot from a USB DVD drive.
As for the all_generic_ide kernel parameter, I think that I also tried this before and somehow it worked but access to the drive was very slow.
 I have an Intel 965 mobo and as I wanted to dual boot, besides this I  had to sliptream Windows XP to integrate SP2 and the Windows SATA drives for the mainboard. This is the only solution to run both OS on the same PC. This particular chipset, and other newers also, does not support paralell ATA devices natively but when Intel made the boards it used a third party IDE controller made by JMicron or Marvell. This is not well supported by Linux and  Linux generally cannot even boot from a parallel ata drive (a DVD) along with a SATA drive (a HD) and Bios SATA default setup. You have to avoid the use of parallel ATA devices and enable AHCI mode in BIOS setup to run SATA drives.

Ramon

---

### Post by xyphur on 2007-11-19
rleon, and anyone else who has posted anything regarding SATA: Thanks for the insight, and your info may just help a few people out around here regarding this issue, but... None of the machines that I've received this error on have had SATA drives, much less SATA controllers of any kind. It's something completely unrelated, at least in my experience.

Regardless of what I attempt to boot from, be it an IDE CDROM, CD-RW/DVD combo, or straight DVDROM, and whether the machine has a SCSI controller (my IBM eServer xSeries 232, with 2 built-in Adaptec u160 controllers), or none at all and just regular IDE (like a plain P3 733 box built on a basic Asus CUSI-FX mainboard with two plain IDE controllers), it doesn't seem to matter... something's wrong somewhere with the way the kernel was compiled on certain releases, and it's showing itself on select systems for yet unknown reasons. SATA may be one possibility on certain systems, and yet on others, such as my IBM server, it has nothing to do with SATA. Maybe SCSI? who knows, because my P3 box doesn't have anything except IDE, and it happens on there just the same. Like I've stated before, this is a very large issue that needs immediate attention and quick resolution, because with so many differing scenarios for this error to occur in, there remains a large possibility of people attempting to try out Linux for the first time, and then being completely let down even before they get it booted off the CD.... or, worse yet, it works off the CD, they install it, and then it fails to boot.... imagine the frustration!

---

### Post by yogeshmk on 2007-11-19
"initramfs" is the BusyBox shell (ash) that is displayed at the end of boot process (when something go wrong). I too am getiing it. See my thread "Disappointed with 7.10" (But I don't hve solution yet!)
--
~yogesh

---

### Post by rleon on 2007-11-19
Sorry. It has to be some hardware incompatibility problem. I remember that I also got  a similar message trying to install one of the 6.X versions on a Pentium III and I quit.

---

### Post by sk8dork on 2007-11-27
this problem is so annoying. before 7.10 was released i tried to boot to the tribe 3 cd, and got this problem. each CD release after that has been the same it seems. i decided to just go for it and do an upgrade from 7.04 to 7.10. of course the upgrade process is fine, but upon reboot i got the error and couldn't boot into the OS. actually i first get an apic error and kernel panic. if i boot using noapic it will then proceed to have issues that seem to be regarding accessing drives, then it drops down to initramfs. now here is the weird part, i started throwing commands at initramfs that essentially didn't do anything. i tried "modprobe piix" which fails because piix is not available. i try it a few more times, same result, i just type "modprobe" and get the little message about how to use modprobe, then i eventually just typed exit, and it dropped to the next line and proceeded to boot into the OS.... wtf? so i've tested this each reboot. it drops to initramfs, i hit exit a few times and it will just go right back to initramfs, and after a minute it will finally just proceed on. my system always worked fine between 6.04 and 7.04, but at 7.10 it's having these issues. booting with a 7.04 live cd works flawlessly, so it's not as though my hardware has gone bad or anything. it's really annoying. part of me wants to go out and buy a new mobo cpu combo just so it will work with the new linux kernels (i would be in fedora 8 right now if it behaved any differently than ubuntu 7.10), but i can't help but feel like it's stupid that the new version doesn't act right with my existing stuff the way the older version did.

---

### Post by asprakash on 2008-02-13
I was also faced the same problem in puppy linux .
I got solved this problem by using the boot option with "acpi=off"
try this steps,
   1. Boot your computer so that GRUB is displayed.
   2. Press the "e" key to go into edit mode.
   3. Press "o" to add a new line to the script.
   4. Type the following: acpi=off irqpoll
   Now boot it.
For more, ref this link, [http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page4.html#post3055649]("http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page4.html#post3055649")

---

### Post by hitokiri82 on 2008-03-08
I dont know if a anyone else is still having this problem. I had the same problem with a Thinkpad T61p. I managed to solve it by setting up the SATA driver in the BIOS to "Conpatibility" instead of the default.

I hope this helps someone out there.

Cheers, 

Francisco

---

### Post by bprof on 2008-03-13
I had the same problem with Debian 4 rc3. It was solved in a way similar to what asprakash described.
1. Boot your computer so that GRUB is displayed.
2. Press the "e" key to go into edit mode.

Sometimes for some reason (I don't know why) grub points to a different location than what it was installed on.

For example in my case /dev/sdb1 instead of /dev/sda1

All I did was changing this to the correct location, and then hit enter to get back to the menu then 'b' to boot using the new settings.

You will be asked for root password enter the password and change 

/etc/fstab    
/boot/grub/menu.list

To reflect the new settings, and then reboot.

---

