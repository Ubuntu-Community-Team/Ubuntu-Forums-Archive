---
title: "Not booting after install of 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by fenriwolf on 2010-04-30
I have installed 10.04 Netbook remix, installation went find and rebooted..Now all i get is a black screen after bios finished loading. I guess it is something with the bootloader.

Anyone have a suggestion on what to do?


Many thanks for the help

Model: Acer Aspire One 250

---

### Post by brynhildur on 2010-04-30
Have the same problem! Just finished upgrading Ubuntu 9.10 to 10.4 (not a clean install) and now I just get the black screen of death after the bios has loaded up. Do I need to do a clean install?

---

### Post by wilee-nilee on 2010-04-30
Does the live cd run without install on a USB or CD? I have the same model but we may have different hardware, I am typing from Lucid regular download not the UNR.

---

### Post by fenriwolf on 2010-04-30
I did a clean install, erased everything on the disk.
I am booting from a USB drive working perfectly to load Ubuntu and see how it looks and works. Only error i get under installation is for the Wireless card, but dont think that would cause it to not boot up. I did try to install Ubuntu Netbook remix 3 times and all 3 times i had the same result when trying to boot from the harddrive.

Will have another go when i get home from work.

---

### Post by Motjida on 2010-04-30
I had the same problem, Ubuntu 10.04 LTS was booting up fine as a LiveCD (on my USB stick), installation went fine, but after the reboot and removing the USB stick it just stood there.

I found out that I made a mistake during the install, I didn't notice that it actually installed onto the USB stick and not the local HDD.

Maybe that'll help solve your issues :)

---

### Post by Motjida on 2010-04-30
Above post is only somewhat correct. It actually installs onto the HDD just fine, but it writes the bootloader to the USB stick and thus you cannot boot unless the USB stick is there.

So when you get to step 7 of the install, click Advanced and change the bootloader install to the drive you're installing to.

---

### Post by Jonners59 on 2010-04-30
I have similar.  I installed on two machines, and not had any joy.  Am now worried about loosing everything on one.

Machine 1: was a new install on a Vista 64-bit machine.  Loaded fine, but after it will not boot into Ubuntu.  I get an error message saying Windows is not shut down properly???

This machine is not such an issue, but machine 2 is.

Machine 2 I was using Ubuntu 9.10 on a Vista 64-bit.  I used the Update Manager to do this upgrade.  It took hours to download, but then as the install started it died.  I now can not get into Vista or Ubuntu.  It gives a message  something like /obin/init/ error and can't find libnib.dbus.iso.1[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

---

### Post by Jonners59 on 2010-04-30
I have been having a bad time of it too.  I attempeted on 2 machines, both running Vista 64-bit.

1 is a PC where the install is new.  After install and I re-boot to complete the installation I get told that Windows has not been shut down completly and to run various commands - which I can't do as I am in limbo land.  One such is "mount -t ntfs-3g -0 remove_hiberfile /dev/sda1 iso/device"

Machine 2 is far more worrying, as I stand to loose data and can't get it tom start in either Ubuntu or Vista.  I used the Update Manager (as instructed) to do the update.  It downloaded the iso, which took hours, it then just started to install and all died.  On re-boot, when I select Ubuntu it freezes on a black screen, but if I press enter I get some text, with comments: "sbin/init/error" and can't find "libnib -dbus.so.1"

Does anyone know where Evolution mail stores all the folders (eMails) and settings, and Firefox stores it's, and where desktop is stored?

Can I run another copy of Ubuntu on another partition to retrieve these and rebuild my install?

I have been playing with the Ubuntu 9.4 DVD, the trial install to see if I can do anything.  I get the feeliing it is close.
Very worrying!!!

---

### Post by fenriwolf on 2010-04-30
> **Motjida said:**
> I had the same problem, Ubuntu 10.04 LTS was booting up fine as a LiveCD (on my USB stick), installation went fine, but after the reboot and removing the USB stick it just stood there.

I found out that I made a mistake during the install, I didn't notice that it actually installed onto the USB stick and not the local HDD.

Maybe that'll help solve your issues :)

As i remember during the installation of my last attempt i went in there but what i could see it showed to install the boot loader on the HD, "/SDA"

But will double check when i can attempt another try later this evening..

Thanks for the info

---

### Post by djwkd on 2010-04-30
For those with the netbook problems - put your model on there - could be a hardware problem (or could be the bootloader installed on the USB stick, as someone above said - which is more likely). Also try using XChat to connect to FreeNode, then join #ubuntu, and ask in there.
 
Also - the two people above with 2 machines - are these netbooks or desktops/laptops? And are they 64bit or 32bit?

---

### Post by Motjida on 2010-04-30
> **fenriwolf said:**
> As i remember during the installation of my last attempt i went in there but what i could see it showed to install the boot loader on the HD, "/SDA"

But will double check when i can attempt another try later this evening..

Thanks for the info

It said the same to me, only the USB stick was /dev/sda/ and the actual HDD was assigned /dev/sdb/ :)

---

### Post by Christof999 on 2010-05-01
Hi, 

Running a Toshiba NB305-00F netbook.

Downloaded 10.04 Ubuntu netbook remix. Installed it on a flash drive with UNETINBOOT.

Installed fine. 

Partitioned fine. Hit advanced, made sure install was to the physical hard drive. 

Rebooted. Nothing, just hangs after bios. I can however get it to boot by reinserting my USB stick, boots then. 

Next tried changing the bootloader install location to /dev/sdb during install.

Still not booting unless usb stick inserted.

Tried running sudo update-grub (which I highly resent since I think in this day and age OS companies cannot expect end users to be fiddling with hacker or computer hobbyist stuff.)

Seriously, I gotta be honest, this is completely unacceptable. Its 2010, and if linux ever does expect to break into the mainstream, it cant have stuff like no wifi, no boot or blank screens after install. Thats the truth, no more excuses. 

I just spent the last two weeks telling people how great Ubuntu is, and signing its praises. Now I wish I hadnt. Sorry if this is harsh or offends, but the truth hurts. If the top linux distro can't even make their LTS release install and boot properly, you guys don't have a chance in hades of gaining market share. Two wasted afternoons is what I got. 

The real kicker? Worked PERFECTLY FINE in Mint 8. So I know its possible to get it working. However, it should just work. This aint the days of slackware, 1992 and old school red hat. 2010 people, computing is the future, and end users simply cannot afford the downtime major mistakes like this cost. 7 installs and nothing yet? Only a complete fanboy could defend that. And trust me, I love linux, and ubuntu.

Get it working ubuntu, just do it. Thats what you do when you screw up, you acdept it, fix it and try to prevent problems like this in the future. I Love your philosophy, love your software, but the cost in time to get it working makes those payoffs not worth it whatsoever. Youve heard it from the holy grail average end user, the type you are always trying to attract away from windows.

Cheers
Chris

---

### Post by Christof999 on 2010-05-01
Also, bluetooth is not working. 

Not that it matters much if the system wont even boot though.

---

### Post by sobolosrios on 2010-05-01
I'm running 10.04 on an nb305 with everything working except the brightness keys.  My version doesn't have bluetooth so I don't know about that.  

I'd be happy to help you try and sort through it if you have specific questions.

P.S. A few nb305 types are hanging out here:

[http://ubuntuforums.org/showthread.php?t=1382481&highlight=nb305](http://ubuntuforums.org/showthread.php?t=1382481&highlight=nb305)

We'd be happy to have you join us.

---

### Post by duver299 on 2010-05-01
I just installed 10.04 desktop. It went through the install without any problems. After the install, it reboots and just doesn't start. My pc goes though post and just stops. I have a list of devices on my screen, "Verifying DMI Pool Data ........." and a blinking cursor. I guess its a grub issue. Any advise on solving this. I actually had the same problem when I first installed 9.10.

---

### Post by jiex on 2010-05-01
Hi there. 
I tried to upgrade through the manager and after it was finished (it took hours) my computer booted to the log in screen. I entered my name and P/W - then the screen went black.  I could not get to the recovering page or anything, apart from the terminal.

I lot of searching revealed that it was likely a problem with my ATI display (its a 4200 onboard the motherboard). I read somewhere that the drivers that come with Ubuntu do not like the ATI / Radeon / Catalyst drivers AND then I recalled some advice I saw in my frenzy of searching: totally remove the ATI / Radeon/  Catalyst drivers and package. 

This I then tried. Easier said than done. 

Most removal approaches leave artefacts and the system finds those, becomes confused and chucks a wobbly. This was happening. I did a listing of software in yhr terminal - I think the command was:
<<dpkg -l '*fglrx*'>> and secondly <<locate fglrx>> - without the << and >>
Yup - fglrx was still there.
Finally, I found this page:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
It recommended an "aggressive" complete removal and this is achieved by:
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon

I also found this page, which has similar advice. 

[http://swiss.ubuntuforums.org/showthread.php?p=9202028](http://swiss.ubuntuforums.org/showthread.php?p=9202028)

However, remember: a standard uninstall won't remove enough of the ATI/Radeon/Catalyst drivers and you really have to go the whole hog - the "aggressive uninstall. When I did that, the machine booted OK and seems to work. The display is a bit odd - a little distorted, like 4:3 TV on 16:9. 

Were I doing the upgrade again (and when I have recovered my composure, I will do this:) I would cut Lucid to CD, back up all data then reformat disk and do a complete clean install. It would have been quicker. 

I have not tried reinstalling the latest ATI drvers, but will do that with the new install to see what happens.

On that, last time (for Karmic) they would not install properly through synaptic but I had to download the packege and install through the command line. I think for the most recent drivers they install via the ATI site somehow.

Given that the ATI drivers are known to cause problems, I do think that the Lucid installer should containn a sub-routine that removes totally the ATI drivers before installation upgrade commences and then it could give you the option to reinstall the latest ATI drivers. 

Tags for this post might be: ATI drivers black screen boot failure complete remove

---

### Post by duver299 on 2010-05-01
Well, I'm not sure if this will help anyone here but I got mine to work. I have two hard drives on my system. I installed 10.04 to to my larger hard drive but it seems that grub had been placed on the second (smaller) drive. When reinstalling, I checked on the advanced option on the "install' page/screen and noticed that my while my OS was being installed on sdb, grub was being installed on sda. Anyway, I changed it to sdb and it works fine for now. I only just completed the install so time will tell how long it works for. If you have any other drive on your system, even if its a flash drive, make sure that grub isn't being installed there as opposed to the drive where your OS is being installed. You should also check your boot priority in bios to ensure that your first boot device is the drive where your OS is installed.

---

### Post by Jonners59 on 2010-05-02
> **djwkd said:**
> For those with the netbook problems - put your model on there - could be a hardware problem (or could be the bootloader installed on the USB stick, as someone above said - which is more likely). Also try using XChat to connect to FreeNode, then join #ubuntu, and ask in there.
 
Also - the two people above with 2 machines - are these netbooks or desktops/laptops? And are they 64bit or 32bit?


Sorry for the slow reply I did not get a notification:

They are both 64-bit and PCs...  I am hoping I have solved one.  I am currently completing the install after god knows how many attempts and having to re-install Windows too.  What I did is remove other hard drives from the PC, and Just have the one.

I still have an issue with the other machine.  I do not have an issue reinstalling from scratch, but my concern is loosing my desktop (I had saved about 10 docs that I need and are not backed up), my Evolution emial info and my Firefox settings and bookmarks......  I am concerned that an install would wipe out existing folders and hence these files.

Does anyone know how to find them.  I can then copy them via the Vista install, re install 9.10 and then copy them back in to the new install...

---

### Post by fenriwolf on 2010-05-03
> **Motjida said:**
> It said the same to me, only the USB stick was /dev/sda/ and the actual HDD was assigned /dev/sdb/ :)

Diden't have much time to do some more testing this weekend..but i have only one HD and could see that HD is assigned to SDA, so it places the Bootloader int he correct place.

Had a chat with a collegue of mine and he suspected it to be that the HD partition is not set as active and there for i get a black screen with a blinking cursor, will have a chack later on tonight to see..

---

### Post by Jonners59 on 2010-05-03
> **fenriwolf said:**
> 
Had a chat with a collegue of mine and he suspected it to be that the HD partition is not set as active and there for i get a black screen with a blinking cursor, will have a chack later on tonight to see..

I have had this too on another PC I have been upgrading to 10.4 and having troubles...

I found after a zillion rebuilds and play that:
1. try an earlier image.  I managed to get mine to boot by doing so..  I then found that it would boot in the current version

2.  I noticed that error messages, when I managed to get in to the logs were all related to graphics card config file...  I changed the resolution by loading in recovery and choosing the option to load in basic mode...  That said the screen was unreadable.  I have had one or two graphics errors on both machines.

There also seems to be a general issue of where and how the grub is saved and stored.  If I look at my own experiences and compare with all those I have seen on the forum, they are all strikingly similar.

I now have one machine that can only use Vista, but all my docs and apps are in Ubuntu... and it won't install or fix and another that will not let me open Vista!  Getting very "upset" with this.  Going off Ubuntu fast.  Especially as noted NO ONE is helping.

---

### Post by thf on 2010-05-05
i seemed to be having the same problem: blank screen with blinking cursor after grub.  i was installing over a windows7/unr9.10 dual boot, and decided i'd try partitioning the hd to have another linux partition.  after banging my head on the desk for a couple hours i decided to give up that idea, install to a single linux partition, and now it boots fine.  

doubtful that this is the root of the problem for anyone but me, but on the off chance it is...  it sounds like maybe the crux of this issue is the same for a lot of people.

---

### Post by sobolosrios on 2010-05-06
> **thf said:**
> i seemed to be having the same problem: blank screen with blinking cursor after grub.  i was installing over a windows7/unr9.10 dual boot, and decided i'd try partitioning the hd to have another linux partition.  after banging my head on the desk for a couple hours i decided to give up that idea, install to a single linux partition, and now it boots fine.  

doubtful that this is the root of the problem for anyone but me, but on the off chance it is...  it sounds like maybe the crux of this issue is the same for a lot of people.

I had almost identically the same experience.

---

### Post by uutnubu on 2010-05-06
Did an upgrade on an HP Laptop.  Boots to black screen with kernel 2.6.32-22, however if I boot with 2.6.32.21, it will boot OK.  Maybe this will help someone else.

---

### Post by Jonners59 on 2010-05-07
> **uutnubu said:**
> Did an upgrade on an HP Laptop.  Boots to black screen with kernel 2.6.32-22, however if I boot with 2.6.32.21, it will boot OK.  Maybe this will help someone else.
Had all, that and none working.  What I in my nieve way have discovered is that it has:

Trouble with multi Hard Drives installed
Trouble with resolution
Trouble with GRUB

Once in it becomes temperamental.  It will work fine, then on a reboot certain apps do not work, Privileges may be lost, it won't boot until several retries or a recovery or re-install.  I have on one occasion found that it could not see any hard drives on the system......

I would like to see better recovery tools, for normal people, not geeks, especially for the GRUB or boot, and MUST include fixing Windows Boot Manager as we are striving to encourage users away from Windows...  I have had to reinstall Vista countless times because U10.4 corrupted the Vista install (boot) and the Windows recovery, as good as it is, could not gain access because the U10.4 had in some way blocked it.  All this takes times, is frustrating, and made for geeks who this is their life - not mine.

Why rebuild the whole system, including configs, documents/folders and fikles when there is only an error in the OS.  Just fix that.  Have a tick box to allow the Ring fencing of the rest.  (.10 is easier and was a doddle to install.

Gone back a step and released, just like Windows, too soon without a fully functioning OS.  Sad day.

---

### Post by Jonners59 on 2010-05-07
There you go....  My 10.4 was working last night when I finished at 1AM, now I have just rebooted and I get a black screen after a brief view of the ubuntu logo...
 F useless.

---

### Post by thf on 2010-05-07
it seems i spoke too soon.  it was booting fine and now i have the same problem as before.

---

### Post by thf on 2010-05-17
in case anyone is still reading out this thread: try recreating your installation usb drive using the ubuntu program "make startup disk" and check the "discard settings on shutdown" option.  also don't use the b43 wireless drivers as they seem to not play well.

seems to be working again, but you can see what happened last time i said that..

possibly helpful:
[http://ubuntuforums.org/showthread.php?t=1477453](http://ubuntuforums.org/showthread.php?t=1477453)
a thread i can't find again, and
[http://ubuntuforums.org/showthread.php?t=1477490](http://ubuntuforums.org/showthread.php?t=1477490)

---

### Post by Jonners59 on 2010-05-18
> **thf said:**
> in case anyone is still reading out this thread: try recreating your installation usb drive using the ubuntu program "make startup disk" and check the "discard settings on shutdown" option.  also don't use the b43 wireless drivers as they seem to not play well.

seems to be working again, but you can see what happened last time i said that..

possibly helpful:
[http://ubuntuforums.org/showthread.php?t=1477453](http://ubuntuforums.org/showthread.php?t=1477453)
a thread i can't find again, and
[http://ubuntuforums.org/showthread.php?t=1477490](http://ubuntuforums.org/showthread.php?t=1477490)

Not the issue I have.

I seem to have ended up with some odd boot menus, not sure if they are in GRUB or some other, and I can not open 10.4  I get the black screen, which when I run in Recovery mode and play with options allows me to open in default resolution (this time only), so I think in my case the issue is that the install does not recognise my monitor.  An old IBM 19" CRT, which gives a great picture...

I wish I could get rid of these menus!!!!!!!!!!!!!!!!!

---

