---
title: "[Errno 5] Input/output error"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by dheerajsp on 2007-11-01
i get this error during installation at about 29%. this is the error i get in the dialog box:

```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```

i checked the CD when i burnt it and it was OK. i even verified the MD5 of the ISO after downloading and the CD doesnt have any scratches. so i dont think it's an issue with the CD.


im trying to install Ubuntu into an already existing ext3 drive that i've used before to install many distros. so i tried formatting the drive using Gparted from the System Menu. but gparted crashed after saying it finished formatting. so i tried the same with the Fiesty cd i had, and it formatted it and didnt crash.

then i put the Gutsy CD back in and opened gparted and it showed that my ext3 drive has 300+ mb of used space?!?!?! isnt is supposed to be 0mb? i just formatted it!!!

so i tried deleting the partition, but then it says that i need to unmount all partitions below the logical number 6(my ext3 partition is hd6, so...). but after i unmount them, it still doesnt delete!


i simply dont know what to do now! definitely my MBR will be overwritten, so ill need to 'fixmbr' from my XP cd. but before that, does anyone know what i can do to install Gutsy right now?

thanx!

---

### Post by dheerajsp on 2007-11-02
Anyone??

---

### Post by udayshanbhag on 2007-11-02
Even i have the same problem.
Did you get solution to this problem??

Thanks in advance
Uday

---

### Post by dheerajsp on 2007-11-02
not really. but i installed Kubuntu 7.04 into the same drive and it worked ok. so there definitely is sumtin wrong with teh Ubuntu live cd itself. i even tried installing Xubuntu 7.10 that i accidentally downloaded, but even that agev the same error message at a different stage of the setup!

---

### Post by MrFSL on 2007-11-02
To start could you boot from the Feisty disk, open a terminal and post the output of:

```
cat /proc/partitions 
```

---

### Post by dheerajsp on 2007-11-02
> **MrFSL said:**
> To start could you boot from the Feisty disk, open a terminal and post the output of:

```
cat /proc/partitions 
```
im at work now, so i cant do that now.

but i WAS able install Kubuntu Fiesty. lemme go home and try installing Gutsy on this drive after i run the 'cat' command u gave,


thanx.

---

### Post by MrFSL on 2007-11-02
This command won't allow you to install. It will just let us know what your hardrive looks like in terms of partitions.

Post the output so we can better determine what we are dealing with.

---

### Post by dheerajsp on 2007-11-02
> **MrFSL said:**
> This command won't allow you to install. It will just let us know what your hardrive looks like in terms of partitions.

Post the output so we can better determine what we are dealing with.
yea, i had an idea of what that would do... will post in a few mins...

---

### Post by dheerajsp on 2007-11-02
[PHP]ubuntu@ubuntu:~$ cat /proc/partitions 
major minor  #blocks  name

   3     0   78184008 hda
   3     1    6296970 hda1
   3     2          1 hda2
   3     5   11671191 hda5
   3     6   12552977 hda6
   3     7     938068 hda7
   3     8    6289416 hda8
   3     9   20972826 hda9
   3    10   19454683 hda10
   7     0     646072 loop0
[/PHP]

im tryin to install into hda6. and hda7 is my swap drive.

---

### Post by Shadak on 2007-11-02
im getting the same problem at 28% installation.  I have gotten 7.04 to install with my set up but not the 64 bit 7.10.  I am using raided drives with a 100MB boot partiotion, and 20GB root, i have 2GB of ram so i dont have a swap. If anyone knows how to fix this i would love to know what i can do to fix it.

Also i do have a 64-bit processor and the main reason y im doing this is just so i can get the 64-bit os only soundblaster drivers

---

### Post by dheerajsp on 2007-11-02
umm.. anyone else wanna try troubleshooting?

---

### Post by Shadak on 2007-11-03
Okay this is what i did, it was a random guess but it worked.  I copied the terminal command line from the install icon on the desktop and placed sudo infrint of it, then finally ran it all in the terminal.
So all you need to do is run thse following line in the terminal and it should work

sudo ubiquity --desktop %k gtk_ui

dont ask my y this works cause i dont know

---

### Post by bozieu on 2007-11-03
I also have the same problem. The CD is good the hard drive is good and older ubuntu is installing properly.

I tried to run sudo ubiquity --desktop %k gtk_ui in a terminal but the installation is still aborting with the same message.

---

### Post by MrFSL on 2007-11-03
>  installer encountered an error copying files to the hard disk:

Well, if we assume that the CD is working fine and it is not a burn issue, then lets look at the other possibilities.

If you have a previous installed version of ubuntu and you are trying to install Gutsy from scratch to the same partition, are you sure the partition has been formated?

Perhaps there is a problem with the hard-drive, you could try a:```
sudo fsck /dev/device
```
...replacing "/dev/device" with the location that you wish to install. (See **cat /etc/partitions** above).

If there is nothing wrong with the disk and the partition you want to install in, and it has been formatted correctly, then i am back to suspecting the CD. I would make an md5sum of the image you downloaded and compare it. I would burn it to disk (non-rw disk) at the slowest speed possible. Then, if I still had an issue I might try a different disk from the daily builds.

Found at [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com)

Cheers!

---

### Post by dheerajsp on 2007-11-04
> **MrFSL said:**
> Well, if we assume that the CD is working fine and it is not a burn issue, then lets look at the other possibilities.

If you have a previous installed version of ubuntu and you are trying to install Gutsy from scratch to the same partition, are you sure the partition has been formated?

Perhaps there is a problem with the hard-drive, you could try a:```
sudo fsck /dev/device
```
...replacing "/dev/device" with the location that you wish to install. (See **cat /etc/partitions** above).

If there is nothing wrong with the disk and the partition you want to install in, and it has been formatted correctly, then i am back to suspecting the CD. I would make an md5sum of the image you downloaded and compare it. I would burn it to disk (non-rw disk) at the slowest speed possible. Then, if I still had an issue I might try a different disk from the daily builds.

Found at [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com)

Cheers!
well i did check mark the Format? option in gparted during installation, never failed to do that!

i tried the fsck command and it said that my read, write and check time were in teh future. so corrected that. executed the command again and it was ok. ill try installing again!

---

### Post by qozmiq on 2007-11-07
Same issue here.  Am doing a dual boot with XtraProblems.  But is Ubuntu that is giving me headaches.  First cd made, error 5.  made another, with different burning ware, and at slowest speed.  Same problem.  Downloaded completely distro from different location.  Still got Error 5.  Tried using the sudo fix mentioned above, still failed.  I tested every cd I made, and each one is telling me there is a error with one file.  No info on what file.  I have tried distro's burned from three different computers.  All have issues.  XtraProblems loaded fine, so I do not think the issue is with the burners, the drive in the laptop, or the disks.  My theory is that the distro has an issue.  

I am making one more attempt, taking XP out completely, and see what happens.   So damn frustrated right now....

Surprise, surprise.  It failed again.   I am going back to the Feisty.  Gusty is broken.

---

### Post by brumsky on 2007-11-11
Had this problem on an older notebook, as did a friend. We installed Ubuntu server, then later installed desktop files, and it worked, both ended up with a working install of 7.10 Desktop. 

Am now having this problem on a new Dell notebook. Have gone thru all of the CD checks and multiple burns, so agree, sounds like a problem with the distro? 

Don't remember the commands we used to install the desktop, and I'm a total newb and many miles away from my notes. Anyone know what the shell commands are from Server to install Desktop?

Thx.

---

### Post by brumsky on 2007-11-12
Found a thread on installing desktop to server: [http://ubuntuforums.org/archive/index.php/t-186298.html](http://ubuntuforums.org/archive/index.php/t-186298.html)

---

### Post by Pas3n7 on 2007-11-15
I'm having the exact same problem, but I have a few more details

gparted and fsck both give the same error

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.40.2 (12-Jul-2007)
fsck.ext2: error while loading shared libraries: /lib/libext2fs.so.2: cannot read file data: Input/output error

The md5sum of the iso comes out correct, and the cd check (from the live cd boot menu) comes out clean.

d2334dbba7313e9abc8c7c072d2af09c
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso

I just fsck'ed the disk before I installed, so it doesn't seem to be a problem with the disk.

I guess I'll try the server CD next

---

### Post by chriskanan on 2007-12-03
I'm encountering this same problem. I burned the disk on two different computers, and prior to wiping it to install Ubuntu everything worked fine.  Did any of you figure out what the problem was?

Thanks.

---

### Post by fulcrumbg on 2007-12-22
I have the same problem , but what is weird : I manage to install it the first time , then I messed up my sound card drivers , and deleted the partition , tried to reinstall, and since then getting this Errno 5 message :( 

Let's hope someone will find solution soon ! :)

p.s. Did someone managed to install it with the alternate desktop CD ???
I think I'm gonna try now ! 

will post a.s.a.p. !

---

### Post by seabrawk on 2007-12-22
Yeah let us know, cuz there are more than a few of us curious about this one.  I have tried the manual repartitioning a few times to no avail (vs the guided...).

It definitely seems related to a previous install, as I am installing over a previous install of server.

---

### Post by seabrawk on 2007-12-22
Something wrong in the Live CD code, as the alternate version worked great for me.

In fact, you can google "Errno 5" and "bug" and get a couple hits i think..

---

### Post by fulcrumbg on 2007-12-23
I did managed to install it from the alternate cd as well ! Worked as a charm ! :) 
Very happy with my Gutsy so far P) =D>

---

### Post by shawn.mnb on 2008-01-02
hey i'm really new to this as well, and I was trying to install ubuntu but I keep getting the same 'errno 5' message. Ive tried different cd burners, the lowest speeds and all that. Ive even tried downloading the iso from different mirrors but always the same. Id like to try the alternate cd but Im a little scared of the text based installer.
Id like to dual boot XP and Ubuntu, - ive partitioned my drive with XP using about 40 gigs and XP is working fine - Ive never had problems with my HD or dvd/cd rom drive before either. Ubuntu loads from the live cd but when I try to actually install it is when I get my problems. should I try the alternate CD? even though im a complete newbie? any help?

---

### Post by k-naeckebrot on 2008-01-06
Sorry. Solution did not work.

Yesterday I thought I solved the problem by installing to a smaller JFS partition. After it did install nicely on that attempt I thought I had solved the problem and posted my suggestion here. Wrong!

Today I tried again (because the adept-updater was behaving strangely) and installation failed. I repeated it about seven times and then, without changing the procedure, it worked out.

So maybe the troublemaker is really the LG-DVD-ROM and my burned DVD-ROM.

Is it somehow possible to mount the iso after booting the Live-CD and use then the ubiquity button to install without using the CD-ROM? Does it solve the problem?
I will only try if I have to but maybe someone else with that problem could try.

Cheers
knaecke

---

### Post by sandclock on 2008-01-16
Hi
I am having same problem i have tried every solution given here i have also tried diffrent cdrom its still same. i checked hard drive for errors-- NONE. i am stuck here i dont know what to do only option for me at the moment is to fall back on win xp again i hope this is solved soon
thanks and regards
nik

---

### Post by dtgolder on 2008-02-06
Agreed. Problem here as well with no solution.

---

### Post by runes on 2008-02-12
Add me to that list.
 
Hardware config:
 
Asus M2N-E 2 gigs ram
2 WD 500 gig drives (aaks model SATA II)
one on SATA 1 and one on SATA 2 - non-raided
LG 18x SATA DVD-RW (on SATA 3)
ATI Mach 64 pci video card (ya ya ancient but hey it was kicking around)
Antec Sonata III (power supply sufficient for hardware)
Generic 17 inch lcd display set up as analogue
 
On boot with the live (7.10) disc I get to the partitioning and allow it to perform guided on 0,0,0 Sata 1 drive the process will run up to 30% then error out with the above title error message.
 
I tried several low level tools to blow away the partitions and boot manager that Ubuntu installs but the error persists.
 
I ran western digital tools and drives are ok - tried utils to test dvdrw...working fine.
 
I redownloaded the live cd and still get the same error. 
This is not a dual boot system I was planning to sw raid the second drive but first I have to get the os installed! I recall there were ongoing issues with the partitioning tools in Ubuntu..maybe this is part of it? Or if all of you are trying to install the os on a SATA drive it may be the live cd has issues with SATA support or Nforce drivers-or both?

---

### Post by Akovia on 2008-02-17
Add one more to the list. Been running same distro via Virtualbox for a couple weeks now and decided to go permanent since I could never get any help with the network setup I wanted.

[http://ubuntuforums.org/showthread.php?t=690415](http://ubuntuforums.org/showthread.php?t=690415)

Most of my hardware is listed in that post. 

The only thing I did non-standard was go the manual partitioning route so I could set up a seperate /home partition. I know this isn't the correct forum for feedback, but the partitioning part of the installation is horrible and took quite a while to figure out for the results I wanted.

Disks

WD SATA 75GB (sda) XP install
WD SATA 300GB (sdb) NTFS Storage
WD SATA 160GB (sdc) Planned ubuntu

First try I made the following partitions from manual partition manager. 

/ = 10GB (Primary, Begining)
/home = 145GB (Primary, Begining)
swap = 5GB (Logical, End)

After failed install and retry, manual part mgr looked like this. 

/dev/sdc
  /dev/sdc1  ext 3  /media/sdc1    10001MB   408MB
  /dev/sdc3  ext 3  /media/sdc3  145036MB  2500MB
  /dev/sdc5  swap                         5000MB       0MB

Set them back up as / & /home and had it reformat again

Details page before install initialization shows..
The following partitions are going to be formatted:
 partition #1 of SCSI3 (0,0,0) (sdc) as ext3
 partition #3 of SCSI3 (0,0,0) (sdc) as ext3
 partition #5 of SCSI3 (0,0,0) (sdc) as swap

Failed again around 28%. I did notice that it seemed to hit a brick wall. It was copying files and was climbing fast when the error hit. It didn't hang like the first try. Tried again with guided entire disk partitioning.

The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sdc)

The following partitions are going to be formatted:
 partition #1 of SCSI3 (0,0,0) (sdc) as ext3
 partition #5 of SCSI3 (0,0,0) (sdc) as swap

This time I didn't get any error message but it just quit leaving a /target icon on the desktop.


Not sure if any of this is relevant for troubleshooting, but I really hope someone can help shed some light on this. It seems to be more than just an obscure problem and if it can't be fixed head-on, can someone help figure out an alternative way to install this? 

Is there a way to copy files to a hard disk or usb drive and install from there, or get some more verbose information on the error? I really really hope someone can help as this seems pretty important when you can't even get the base system installed.

Best Regards,
Akovia

---

### Post by Akovia on 2008-02-17
UPDATE:
Install at 82% right now and still going.

I opened my machine and disconnected my other SATA drives, leaving only the drive I'm installing to. I did also use my other CDRom drive but doubt that was the key. I did start this time with the default partition option, sliding the slider to 100% to try as many different options as I could. When I got to the details screen before starting the install, I noticed it left the old partitions intact from the last failed attempt but I continued anyway. When I realized it was working (got to 70%), I stopped it and reconfigured using my initial manual partition choices, deleting the extra partitions.

It just asked me to reboot so it looks like that may have fixed it. Not sure why disconnecting my other drives worked, but I hope it might help others with the same problem. The only other difference was using my CDRom instead of my DVD-RW drive which I've never had a problem with before. Both are Sony.

Will report back if I have any other problems or insight as to what happened.

Akovia

---

### Post by KetLock on 2008-02-27
I'm completely stuck on this as well. I've tried every combination of things to do but no success. :confused:

---

### Post by dagyrox on 2008-03-28
Hi.  I have been using 7.10 for a few months now on my laptop.  i have just put together a new pc from scratch.

sata HD
sata DVD
2g memory
256 evga video card

i have never had problems with ubuntu, as a matter of fact, ubuntu was a ton better than suse(i used to be a suse fan).  I'm getting the errno5 at 61%.

is it possible that this might have to do with our sata drives?  i noticed a few posts back that someone disconnected one of his sata drives.

thanks
jason

---

### Post by Echo35 on 2008-04-04
Ditto, ditto, and more ditto. I keep getting errorno 5. I've even tried using different variants of Ubuntu (Mint, gOS, etc.) and they all do the same thing. I've even gone as far as iso busting them and booting off a USB Jump Drive and its still giving me the same error (Which is rather amusing, Ubuntu telling me to check the CD when its on a jump drive :)). Of course the same Jump Drive installed it fine onto my laptop. However, the Linux install on my PC is NOT on a sata, its on an IDE, and I also had similar problems with the beta of 8.04.

---

### Post by Moorgeist on 2008-04-04
[Errno 5] Input/output error

I got this error at 66% of the Ubuntu 8.04 installation on my Asus A6JE notebook. The same error occured while installing on my desktop PC.

I solved this problem by changing the brand of the CD, which i used to burn the installation image:

1. Used a no-name CD-RW: Ubuntu installation aborted at 66% with the "Errno 5" (notebook and desktop PC)

2. Used a Taiyo Yuden CD-R: The CD didn't boot at all (notebook and desktop PC). Tried several blank CDs.

3. Used a Verbatim DVD-R (Nothing else left...): Problem solved. Installation completed. A new happy Ubuntu user.

---

### Post by Psyphre on 2008-04-17
Me too. I have installed ubuntu edgy, feisty, gutsy and hardy on my desktop many times. Never any problems. However now, (after wanting to reinstall gutys after problems in hardy's wifi) I cant get gutsy to install. Ive even tried hardy again and that wont work anymore either. So its not just confined to Gutsy.

It defintely isnt the cds as i have 3 different cds which i know for a fact work, as I have installed off them in the past with no issues. 

This makes no sense to me. What is causing it?

---

### Post by bb12489 on 2008-04-21
still no fix for this?

---

### Post by Maintech on 2008-04-21
In the boot up options add: --nomsi
Try that and see what happens.

---

### Post by dwhsix on 2008-04-26
I was having the same problem (for 8.04), but got past it.

I got the livecd and alternate install ISOs off torrent, burned to CD and verified the livecd.  I initially tried an upgrade of 7.04 using the alternate CD, something botched that (not sure what), so decided to do a fresh install and deal with getting my stuff re-installed, etc.

Installing from livecd failed with the errno 5 about 3 times, consistently.  I then ran diagnostics on my disks, both of which passed (although the disk I was /not/ installing to was running hot).

I noticed in [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) that they recommend to burn the livecd at the slowest speed.  Not sure why this would make a difference, given the first livecd I had passed verification, but I tried it (and actually burned the CD on a different CD burner on another machine).  The install from that CD completed.

So it may have been writing the CD slowly, or it may have been the different CD burner.  Don't really know.

---

### Post by dwhsix on 2008-04-26
I was having the same problem (for 8.04), but got past it.

I got the livecd and alternate install ISOs off torrent, burned to CD and verified the livecd.  I initially tried an upgrade of 7.04 using the alternate CD, something botched that (not sure what), so decided to do a fresh install and deal with getting my stuff re-installed, etc.

Installing from livecd failed with the errno 5 about 3 times, consistently.  I then ran diagnostics on my disks, both of which passed (although the disk I was /not/ installing to was running hot).

I noticed in [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) that they recommend to burn the livecd at the slowest speed.  Not sure why this would make a difference, given the first livecd I had passed verification, but I tried it (and actually burned the CD on a different CD burner on another machine).  The install from that CD completed.

So it may have been writing the CD slowly, or it may have been the different CD burner.  Don't really know.

---

### Post by Beretta_NZ on 2008-04-28
Still the same problem in the ISO currently being downloaded from Ubuntu.

With so many people having exactly the same problem, this is a pretty colossal screw up.

---

### Post by toddedw on 2008-04-28
This problem is driving me bonkers. I can't seem to fix it. 

I had a 60gb pata drive in my Dell Inspiron 6000 erroring with errno 5 at about 60%. I switched the hard drive to a 40gb pata drive and I'm still getting the same issue. 

I'm trying the --nomsi option now. Next I will download a new .iso and burn it to a different brand of CD.

Any other suggestions would be appreciated. I have been an Ubuntu users for a very long time and I have never experienced this problem, but it looks like it goes back to 7.04?

EDIT 12:09pm:
--nomsi switch at boot has no effect.

Downloading a new ISO now.

EDIT 4:10pm:
I was originally using Durabrand CD-R's for my install CD. After downloading a new ISO, checking the md5, switching to Memorex CDs, burning it at a slow speed, and verifying the CD it worked great. *shrug*

---

### Post by ishkur88 on 2008-04-28
I seem to be having this issue as well. I've done everything suggested in the previous replies, but to no avail. 

I've run disk checks on my Ubuntu disks (all 7 of them :\ ), I've run checks on the file system, and nothing really tells me that the disks are bad, or that my drive is dead/dying.

I run a Dell XPS M140 with a 80GB HDD. If anyone can shed some light on the situation, that would really be appreciated... (right now, I cant use this machine at all except for when in a LiveCD session).

---

### Post by x0d on 2008-04-28
I also fell victim to the errno 5 error trying to install.  I swapped the CD/DVD drive with another one that I had and everything installs fine now.

---

### Post by xproject on 2008-04-29
I had the same problem. I highly doubted that the problem stemmed from the manufacturer of the CD-R. But, I tried a different manufacturer's DVD-R (yes, a DVD-R as someone earlier mentioned). My original CD-Rs manufacturer was Maxell and did not work. The DVD-Rs manufacturer was Verbatim and worked without any problems.

My suggestion: Switch your speed to the lowest one, if that doesn't work, switch to a DVD-R.

---

### Post by HybridZero on 2008-04-29
Add another user to the list. ErrNo 5 on every attempt to install so far (tried slow burn, different CD manufacturer, dvd-r, fsck, etc with no luck). I'm downloading the alternate install CD now to see if I can get things going through that approach.

---

### Post by fuzzbuzz85 on 2008-04-30
Hi all,

this is now driving me crazy too! Couldn't get the update manager to work on gutsy so downloaded the hardy iso, burned it onto cd and tried to install, several times, each failing after errno 5. Tried installing into my 2nd hard drive, errno 5 again. Then downloaded the iso from another mirror, MD5'd it (the number matched the one provided by the ubuntu hash page), checked the CD integrity, which failed on one file, even though I burned it at the slowest possible speed on nero on a housemate's machine (8x). 

Before my most recent attempt I followed the advice which someone posted earlier:

cat /proc/partitions, which brought up a list of sda partitions (sda1,5-11; sda1,5,6;loop0).

Then I decided to try and re-install gutsy (from the same CD I originally installed it from)... errno 5 again! Now running live, did the cat /proc/partitions thing again and got:
major minor  #blocks  name

   3     0  156290904 hda
   3     1    1526143 hda1
   3     5    1510078 hda5
   3     6    2996059 hda6
   3     7    1510078 hda7
   3     8  129234861 hda8
   3     9    1510078 hda9
   3    10    3534268 hda10
   3    11     224878 hda11
   3    12    4851598 hda12
   3    13     281106 hda13
   3    14    8667036 hda14
   3    15     441756 hda15
   3    64   20016348 hdb
   3    65   19133383 hdb1
   3    69     875511 hdb5
   7     0     657224 loop0

What I'm now thinking is that once this problem happens once, each consecutive installation attempt makes more and more mess - I now have even more partitions, which is madness!! Anyone have any ideas? I'm a total newbie as well, and the frustration is compounded by an impending dissertation hand-in.... :confused: :(

UPDATE: Tried manually repartitioning my two hard drives (one is 140G, the other 20G. On the 20G made a 19G / and a 1 G swap, and the 140G was made as a /home), then reinstalling... errno 5. Always at a different place. I'm close to throwing my computer out the window!!

UPDATE: Tried to install with the alternate cd (MD5'd and integrity-checked, burned at slow speed etc), made it to 85% and then it failed again. Will try burning on a different machine.

UPDATE: Burned an alternate cd at 4x, just didn't work. Tried live CD install (for the hell of it), the screen turned giant during the username/password set-up. Back to original alternate CD, got to 85% before failing again at the same file - 'preparing to configure notification-daemon'. Could this be our culprit? Ran 'Select and install software' again, failed at 85%. Hm.

UPDATE: Burned the liveCD at x1 speed onto a DVD-r... made it to 22%. I'm just going to have to do the dissertation work on my live CD and give up for a while - I think I've exhausted all options suggested here!

UPDATE: Had one last bash - burned alternate CD at x1 speed onto DVD-r. Failed at 85% again, same file - 'notification-daemon'. If anyone knows more than I do about these things (not difficult!) is there any way that you can skip out that file during the installation process? Cheers

---

### Post by electronic spark on 2008-04-30
Same errno 5 input/output error!  Tried ububtu amd64 kubuntu amd64 mint 4.0 ubuntu i386.. all with same DVD+R's.  Live runs fine.

Before that I ran 7.04 with all the upgrades.  Upgraded to 8.04 and nautilus failed, I tried fixing it by removing, reinstalling desktop, different file manager dolphin works, nut bunch of things don't work because nautilus is default like burner etc.

What is wrong with ubuntu?  I had same problem upgrading/installing 7.10, could do just upgrade on line.  
Is there a way to do internet install?  other distro's have it.

I downloaded and burned several iso's, checked fine, cd check passed.!

I ,ay have to switch to another distro.

I can only run live mode.

Somebody has to be able figure it out?  ubuntu virus?

How do I install from HD?  I don't enjoy burning cd's anymore (100 so far since mandrake ver?? (1997)

Not even some good old linux cd's work anymore.

Downloading kiwi linux and ubuntu alternate cd - I'm desperate.

It's funny, I can't install xp on this pc anymore, is ubuntu planting a bug like ms?

---

### Post by Psyphre on 2008-05-01
right i dont understand why but every attempt i make at installing gutsy fails. ive burnt so many cd's with no luck. Yet, for some reason hardy (not the beta i used before, but the released hardy) WILL install fine. But guess wat?? my wifi wont work anymore in hardy, so i HAVE to use gutsy. This makes no sense, why will hardy work everytime (ive tried 3 times) i install, but gutsy will not??

---

### Post by electronic spark on 2008-05-01
I'vr tried alternate no luck, reinstalled good ol' 7.04, was upgrading to 7.10 and restarted, thinking it was frozen, now it's messed up again.  Going to try install 8.04 right now amd64.  Wish me luck.  I want the 8.04 because it seems wine is running better (used tax software) and it's supposed to be a better os.

Nope, didn't work :-(

..and the internet stopped working..

The attempt to install 8.04 wiped out the grub loader again - it stopped at grub loading stage 1.5

---

### Post by fuzzbuzz85 on 2008-05-02
Hi all,

had another scout around google for ideas, found this which is interesting. Although doesn't offer much in the way of solutions, maybe it'll be relevant to one of you! Good luck, and please post up here if you find a way around it 'cos I think it's driving us all round the bend! 

[https://bugs.launchpad.net/ubuntu/+bug/205359](https://bugs.launchpad.net/ubuntu/+bug/205359)

---

### Post by Psyphre on 2008-05-02
Great news!!! 

I got it working!!!! I must have burnt so many cds, all in vain.
In the end i had one last idea, i had a feeling that the partitions are obviously messed up, and every attempt i tried to make using the live cd's just couldnt fix it. So I burnt myself a copy of windows xp, booted it up and used it to delete the partitions completely. Then installed ubuntu without a problem at all.

I hope it works for you guys as well, its definitely worth a try.

---

### Post by fuzzbuzz85 on 2008-05-02
The good news: I think I've installed it....
I burned *another* alternate CD, and it failed again at 85%. Accidentally asked it to try installing again... and it got further, and started asking me millions of questions. Failed again. Tried again, got even further, then I got a scary red screen then it went back to the menu again.

The bad news: it wouldn't install grub... grrr! So now I'm back on the live CD faffing around trying to make that work. Will post again with results.

---

### Post by dmarquard on 2008-05-02
I had tremendous problems installing Kubuntu 8.04 LTS on Abit KN9 SLI Mb w MCP55P Chipset.

I Continually got the I/O errors from the CD/DVD and locked up.

After checking hard drives, clearing CMOS, reburning on DVD vs CD, trying the alternate CD etc. I found the following to be the case.

I removed the SATA drive from my KN9 and put it into an older computer ASUS A8V w Athlon 64 w VIA VT8237 Chipset on the same SATA Drive mb connector then ran the install disk on that computer.

It installed w no problems. I then moved the SATA Drive back to my KN9 box and it ran great.

I put same monitor on both computers so install was correct and I plugged the SATA Drive into the same SATA connector.

I later noticed a setting on my KN9 board bios:
MCP55 HT Speed and MCP55 HT Width
My suspicion is that an adjustment may have been able to be made here for the install to slow down the CD/DVD to prevent I/O errors. Someone may want to try this.

After install and moving the HD back to my KN9 the CD/DVD could be used for burning etc w no further problems.

I suspect that the Hardy boot disk uses a  different CD access than the final installed but Im only guessing.

Turns out the CD's were not faulty the drive was not faulty but install program is buggy.

Kubuntu needs to address this in the install disk.

---

### Post by naggis on 2008-05-03
Hi 
I have been having the same problem whilst trying to install Hardy. It seems, that many folk reburned the disk without success - so did I. I tried deleting the partitions using the Windows disk but again no joy.
When I read that burning at the slowest speed may possibly sort things out, this seemed to be in line with the comment which came with the error message. This said that the disk may be dirty etc.
Anyway, burning at x4 sorted the problem out for me. 
But there seem to be a number of questions still. Is there a problem in writing the original .iso file at the server? Surely the installation should not be so sensitive to burning speed or maybe disk manufacturer.
Lets hope the problem is quickly fixed as it would be a shame to put folks of using such a great os.

---

### Post by electronic spark on 2008-05-03
Finally, I got 8.04 working.  I reinstalled 7.04, did all updates, did an upgrade to 7.10 , did all updates and then upgrade to 8.04.  It was wort it.  It runs great.

---

### Post by x0d on 2008-05-04
This error may be related to a hardware problem.  On my myth box I was getting the Errno 5 on various burned media when I tried an install so I tried switching out the optical drive with a spare.  It did the trick and mythbuntu installed fine.  I then wiped the harddrive and hooked up the original optical drive to do a re-install...Errno 5, no dice.  I then switched out the original optical drive with a third spare optical drive just to make sure that the first optical drive was causing the Errno 5 error and it installed fine.  It may very well be a hardware-related issue.

---

### Post by putrid on 2008-05-25
[SIZE="1"]I'm sorry i had to post in this old thread, but I maybe got one solution.[/SIZE]



**Finaly! its alive!**

I got the same error when trying to install Ubuntu 8.4 with the live CD. I just installed it on my laptop with no errors, so it couldn't be the CD. I tried 5-6 times before i tried to install it from my **CD-ROM** instead of my **DVD-ROM**, **[COLOR="Red"]and it worked  flawlessly[/COLOR]**

I hope any of you guys could solve your problems too with this info.

__________________________
The error code:
[COLOR="Green"][I]**The installer encountered an error copying files to the hard disk:**

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/I][/COLOR]

[SIZE="1"](I'm sorry for the bad English)[/SIZE]

---

### Post by LeeU on 2008-06-10
Anybody find the exact problem here? I have burned 6 CDs (Live and alternate), verified the CD, changed hard drives and RAM memory, and changed the CD unit and nothing changes. I get to 85% of loading the software and it produces the above error. The computer ran Ubuntu fine before. I have tried it with Heron and Gutsy. This seems to be a problem that no one is paying attention to.

---

### Post by ADloser on 2008-06-11
After a couple of failed attempts with the same error, I changed my partition format from ReiserFS to ext3 and the next attempt installed successfully. (Also I'm installing 64 bit version.)

---

### Post by LeeU on 2008-06-11
Yep. I had mine set at ext3 also. Strange ...

---

### Post by promix89 on 2008-06-15
I installed Ubuntu 8.04 and this mistake when I want to give children on a cd dvd or the pc. ubuntu 7.10 with the so called problem arise. who knows how to solve this problem? :(

---

### Post by runes on 2008-06-27
> **promix89 said:**
> I installed Ubuntu 8.04 and this mistake when I want to give children on a cd dvd or the pc. ubuntu 7.10 with the so called problem arise. who knows how to solve this problem? :(

I was struggling with this for a bit..I tried updating the firmware on my motherboard and dvd drive. Tested the memory, hard drive, dvd drive and all seemed fine.  After looking around on the web I found someone who had major problems installing another distribution with the same motherboard.  It turns out that the memory I have will not work when installed in the two banks that are considered DUAL CHANNEL but the installs now work fine when installed on the two other banks.  Try checking your ram and moving it to the other banks if you have the space for it.  If you are not sure, have someone do it for you.  It worked for me when everything else didn't.

---

### Post by tithonus on 2008-07-05
I have the same error over and over again.

here's a bug report for this: [https://bugs.launchpad.net/ubuntu/+bug/245794](https://bugs.launchpad.net/ubuntu/+bug/245794)

---

### Post by hairshirt on 2008-07-05
I solved this for myself here.  Worked out quite simple for me really.  Just took three days of pulling my hair out.

[http://ubuntuforums.org/showthread.php?p=5324413#post5324413](http://ubuntuforums.org/showthread.php?p=5324413#post5324413)

---

### Post by AriLex on 2008-07-12
I did the following (intuitively, so don't ask me why) and it worked:
1. With the boot-options I pressed F6 twice and marked the first 3 options that came in a pop-up window (noapci nolapic noapic if I remember well). That made it to 85% instead of 51%. 
2. I burned the .iso on a CD (Kodak CD-R 52x 700MB) instead of on a DVD, and also set the boot options as above.
Maybe just luck, but worth the try.

---

### Post by Hoora on 2008-07-21
Anyone got the solution on this? Struggling here to get a replacement for the Chinese XP that I have to use at work... Frustration grew intolerable yesterday because of the MS and Chinese characters... Nope, I can't any Chinese! 

Anyways, I get the same Errno5 at 40 (or something) percent with my kubuntu-kde4-i386-desktop cd. I've checked the md5 sum of the image and the disk that I burned. The disk quality is not probably the best but I really can't believe on it. I'll try the alternate cd tomorrow when I get back. I got only one DVD-ROM drive so I cant swap them. 

Anyone know if it is possible to mount the iso image and install from there while booting from the live-cd. It sounds to me like there is a hardware (or something) problem with the dvd-player or something...

---

### Post by Hoora on 2008-07-21
Ok, got it working by installing Ubuntu from the alternate cd. I suggest that anyone with weird [Errno5] problems should try alternate cd if all else fails.

---

### Post by seabrawk on 2008-07-24
Haha, I posted that same thing December 22nd...I am surprised more people didn't immediately try that.

I can't imagine it worked for everyone, but it did work for a few people.

---

