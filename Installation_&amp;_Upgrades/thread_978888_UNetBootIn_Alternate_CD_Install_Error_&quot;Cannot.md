---
title: "UNetBootIn Alternate CD Install Error: &quot;Cannot find CD&quot;"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by thelastfarmkid on 2008-11-11
Howdy folks, as the title says, I've got a problem.

I tried to install Ubuntu Studio 8.04 using the UNetBootIN method, and when I get to the install process, it tells me that it could not find the CD.  I think: well, duh... because it's USB. 

I also tried the unetbootin method with UbuStu 8.10, no dice.  Went on to try normal Ubuntu alt, (8.04 and 8.10) neither worked.  As a control, I tested the Ubuntu livecd installer, worked like a charm. So, am I doing something wrong in setting the ISO within unetbootin and going from there, or are there some magical options that I have yet to discover that will make this work?

Any help?

---

### Post by Steve1961 on 2008-11-11
Not all computers are capable of booting from usb.  When your pc boots up is there an option to press a key to bring up a boot menu?  If so, insert the usb stick before switching on, boot up and bring up the boot menu.  If the usb key shows up on the menu you're in business, if not your hardware probably doesn't support usb booting

---

### Post by thelastfarmkid on 2008-11-12
Sorry, I was unclear.  My computer supports booting from usb.  I installed Intrepid using the unetbootin live usb installer.

Just the Alternate ISOs don't want to work with Unetbootin, I get a "cannot find CD" error.

Am I doing something wrong?

---

### Post by Steve1961 on 2008-11-12
> **thelastfarmkid said:**
> Sorry, I was unclear.  My computer supports booting from usb.  I installed Intrepid using the unetbootin live usb installer.

Just the Alternate ISOs don't want to work with Unetbootin, I get a "cannot find CD" error.

Am I doing something wrong?

can't see a reason why it wouldn't work with the alternative cd.  I know unetbootin failed on me last week when trying to put the dektop iso of intrepid on a usb stick.  I used dd to zero out the partition table on the usb stick, repartitioned it, and then and tried again.  Then it worked  fine.  Worth a try.

---

### Post by billdoor on 2008-11-12
I have the same problem. Installing Kubuntu 8.10 from UNetBootIn, selecting 8.10_x86_Live from the dropdown. Setup gets just past setting up the keyboard and network interface then bails as it can't find the CD. Standard install ISO has no such problem, but unfortunately I need to set up encrypted LVM.

Any wany to force it forward or mount it manually from the busybox console in a way that the install script can find?

---

### Post by thelastfarmkid on 2008-11-12
I think I zero'd it out, not sure. I used the HP format tool. How can I be sure?  

Maybe could somebody try to duplicate the error on purpose so I'm sure it's not just me?

I'm open to all ideas.

---

### Post by Steve1961 on 2008-11-13
> **thelastfarmkid said:**
> I think I zero'd it out, not sure. I used the HP format tool. How can I be sure?  

Maybe could somebody try to duplicate the error on purpose so I'm sure it's not just me?

I'm open to all ideas.


To zero out the partition table you just need to know what your usb stick is called (e.g. /dev/sdb,sdc.....).  You can find this by doing sudo fdisk -l.  Once you know what it is make sure it's unmounted.  Then, if, for example, it was /dev/sdb, you would do the following:

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1

Takes about a second.  Pull out the stick and then reinsert it and partition it with gparted.

Warning:  if you get the device number wrong you could cause serious damage to your system, so make sure you are certain off the details first.

---

### Post by AndEat on 2008-11-28
i get this also

- the usb key DOES boot
- in the first stage of the install, there is a cd detection process...and the installer will not continue.

from what I understand, the installer isn't aware of where it installing from and wants to detect a cd before moving on.

is very frustrating, because I can't get an adequate usb install from ubuntu in the way I need to install (alternate install from usb)

---

### Post by ankara on 2008-12-30
im trying to get the UbuntuStudio AMD64, which is only available as an alternate install cd, working with Unetbootin. no joy.
so far ive managed to get a tiny bit further than everbody else but nowhere near close to finishing. FYI ive not got a dvd burner so cant just burn a copy. would be nice. but a technical challenge is always good fun :D

from the installer, while choosing language, i Ctrl-Alt-F2 to a busybox terminal and ```
mount -t vfat /dev/sdc1 /cdrom
``` there are times that this can be temperamental, giving me device not found and illegal string blah blah. but when it works, this gets me past the "detect and mount cdrom" section but fails on me at the installing base system, due to something about not having the genuine install cd inserted.

there is obviously a flag or some kind which tests the installation media for something. it would just be nice if one of the DEVs could tell us how to disable it or workaround.
regards

---

### Post by rodrigocsm on 2009-03-05
Did anyone find the solution for this problem? I'm facing the exactly same thing. It boots fine but stucks the installation trying to find the cd.

---

### Post by ankara on 2009-03-05
no, what i ended up doing was installing the desktop version and then searching for, and installing the ubuntustudio-* meta-packages through aptitude.
HTH

---

### Post by avtolle on 2009-03-05
From memory, unetbootin needs a Live CD image to work (it doesn't really make sense for the alternate cd image to be used, when one thinks about it, if the creation of the USB is to act as a "Live CD"); I recognize that installation was the goal here, but that is, in and of itself, not the purpose of unetbootin, or at least as I understand its purpose.

---

### Post by ankara on 2009-03-05
This isnt so much a Unetbootin issue, once the kernel is loaded, Unetbootin should have absolutely no control over what is run or how it is run, its purpose is to be a portable media bootloader. the issue is that the alternate cd has a flag set that disallows installation from any other media except CD. this means that you cannot install any other version of ubuntu from USB, such as the server or studio versions.

---

### Post by lloydandj on 2009-03-06
I have pretty much the same thing.  When I go into the bios it says usb "not present."  Even with usb stick in, and even after I set usb option to number one on the list in the bios boot sequence.  There*s not much on google about "not present usb."

---

### Post by Rofko on 2009-03-09
I think a lot of people are having this problem. Can someone think of a workaround?? I spent my entire Sunday trying to work this out. This surely just requires a simple hack, telling the alternate install to get the data off the partition instead of the cd.

Anyone???

Just to reiterate, the problem is: Although unetbootin will allow you to boot (from usb or hdd, launching the installation procedure, it is unable to 'find' the cd drive to install from. This is obviously going to be the case, as the whole point of this procedure is to install without a cd drive.

The fact is that the Live CD (run through unetbootin or not) simply does not work with a lot of older machines, even if the installed version works fine. IF you can manage to install it.

---

### Post by ankara on 2009-03-09
the really annoying thing about this issue is that there is no reason what-so-ever, that i can see at least, why the Ubuntu developers should cripple their own product in this way. for a distro that tries to be true to GNU principles, it flies in the face of that convention. dare i say it even smells like a M$ policy [-X

---

### Post by maybeway36 on 2009-03-09
Just use UNetbootin with regular Ubuntu as the option. It should download a 9MB text-mode installer. This installer will actually let you install Ubuntu Studio, it's one of the options in the task list in the "Select and install software" step.

The options you will want to check are:
Audio creation and editing suite
Ubuntu Studio desktop
2D/3D creation and editing suite
Video creation and editing suite

---

### Post by ankara on 2009-03-09
@maybeway36: forgive me for being blunt. i think your post is more than a little unclear, how is this txt installer downloaded and at what point in the process, how is it accessed from the alternate cd ISO when that has its own installer. please give steps or cite references and links for us non-mindreaders :P
one more thing, when the existing alternate txt installer is used (without clarification ive no idea how these two are different) the install fails well before the installer ever gets to the "Select and install software" choice for software installation. it fails before doing the "apt-get update" step to check the mirrors before giving the software choices. right after partitioning step if i remember correctly.

---

### Post by maybeway36 on 2009-03-11
I've used the 9MB netboot installer before, but never throguh UNetbootin, so I really don't have any idea how to do that. I know it's just two files, linux and initrd.gz, and you can get them from the [mini.iso for Intrepid](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso) or [this folder.](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/) Once you get them running, it's fairly straightforward - the only real installation media is the Internet.
If you already have UNetbootin installed on the USB drive, just put linux and initrd.gz in the root folder of the USB drive and add an entry to syslinux.cfg:
```
label ubuntu810
menu label Ubuntu 8.10 netboot installer
kernel /linux
append initrd=/initrd.gz vga=normal
```

---

### Post by ankara on 2009-03-11
ah yes, the old net-install option, i used to do this with debian over ftp. forgotten all about that. now ***surely*** that will work. ive no idea if the installer will show the ubuntustudio options (i doubt it but really hope your right and it does), if not then it could be no different to just installing the standard desktop version then apt-get'ing the meta-packages. 
however, its another workaround at least. 
thanks.
when using Unetbootin its simply a case of selecting the drive you wish to install to and selecting the ISO to load onto that drive. the rest is pie or cake, depending if your sweet or savory :D

---

### Post by t0mppa on 2009-03-11
I just did this yesterday as a matter of fact. Dropped the alternate install files through Unetbootin to a USB stick and it successfully installed Ubuntu 8.10 on my laptop. So, just wanted to say that it IS possible to do just that.

However, there was no way to install the studio parts. Whenever I tried checking them, the installer said that it couldn't find the packages online, but when I left them out, it didn't have any problems proceeding with the installation.

---

### Post by paulctan on 2009-03-13
> **thelastfarmkid said:**
> Sorry, I was unclear.  My computer supports booting from usb.  I installed Intrepid using the unetbootin live usb installer.

Just the Alternate ISOs don't want to work with Unetbootin, I get a "cannot find CD" error.

Am I doing something wrong?

No, you are not doing something wrong.  I have found exactly the same problem, and so has some other people:
[INDENT][B]
[https://bugs.launchpad.net/unetbootin/+bug/237867]("https://bugs.launchpad.net/unetbootin/+bug/237867")
[/B][/INDENT]
I managed to fix the problem by downloading the network install (mini.iso) from:
[INDENT][B]
[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")
[/B][/INDENT]
I used the 8.04 LTS Server Amd64 iso:
[B][INDENT]
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-amd64/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-amd64/current/images/netboot/mini.iso")
[/INDENT][/B]
and am now past the cdrom not found problem.  (use the mini.iso as the ISO image for unetbootin)

Hope this helps you and other people that have been googling for days on the problem.

Paul Tan.

---

### Post by ankara on 2009-03-13
there are some interesting workarounds in that bug report, thanks for sharing. loop mounting the .iso to /cdrom is one i wish i'd thought of.
:doh: :D

---

### Post by Vasilisgr on 2009-05-03
Hi guys 

I am pretty new with ubuntu i have one old laptop HP pavilion PIII 850mhz 256 ram 18GB hd, this laptop dosent have the option of USB boot and dose not have a cd drive either... :-( what i did was downloading unetbootin and installing the hole thing on my c: drive i restart my system and i had the option to boot XP on UNet so i choose unet,  it booted up as a live cd normally i did 2 partitions one ext4 4gb and one swap 2 gb, and i start the installation process i give a user name and pass i click forward and i get the no cd found message :-( any help?? :confused::confused:

thank you

---

### Post by IgnorantGuru on 2009-08-13
The results of an (un- but almost-successful) experiment with this FWIW...

[http://kubuntuforums.net/forums/index.php?topic=3105737.msg192616#msg192616](http://kubuntuforums.net/forums/index.php?topic=3105737.msg192616#msg192616)

---

### Post by hengst on 2009-12-06
[B]Looks like problem has been solved ; 

[/B]Secondly, as of Ubuntu 8.10, unetbootin should be changed to pass cdrom-detect/try-usb=true as a kernel command line option if it wants the installer to try to probe USB devices. (Sorry, this won't work with 8.04.)


( from the bug report , [https://bugs.launchpad.net/unetbootin/+bug/237867](https://bugs.launchpad.net/unetbootin/+bug/237867) )


i can confirm that it worked for my USB- 9.10 Studio installation on a desktop.

---

### Post by agreenbhm on 2010-02-02
Just so it is clearly written for all my fellow n00bs out there, load the alternate cd up onto a USB drive using UNetBootin, then when at the boot screen, hit tab to edit the first entry, then write "cdrom-detect/try-usb=true" before the "--".  Then hit enter, and you're good to go.  Thanks for all those that posted before I did.

---

### Post by geekoid on 2010-04-06
> **agreenbhm said:**
> Just so it is clearly written for all my fellow n00bs out there, load the alternate cd up onto a USB drive using UNetBootin, then when at the boot screen, hit tab to edit the first entry, then write "cdrom-detect/try-usb=true" before the "--".  Then hit enter, and you're good to go.  Thanks for all those that posted before I did.

I can confirm this little solution still works perfectly for 10.04 beta 1 Alternate.  Thanks for sharing it with us.

---

### Post by geekoid on 2010-04-06
Another method of doing this so the parameters are permanently set is to edit the syslinux.cfg file in the root directory of your flash drive once you've created the UNetBootin install.

Just open this file in a reasonable notepad app (I use **notepad++** under Windows and **gedit **or **vim **under Ubuntu), look for the entry or entries you wish to modify and add in the following text before the "--" part of the "append" parameter for that entry.

```
cdrom-detect/try-usb=true
```

Once done, save, eject and then boot your box with the now fixed installer :KS

---

### Post by rusti06 on 2010-04-12
> **geekoid said:**
> Another method of doing this so the parameters are permanently set is to edit the syslinux.cfg file in the root directory of your flash drive once you've created the UNetBootin install.

Just open this file in a reasonable notepad app (I use **notepad++** under Windows and **gedit **or **vim **under Ubuntu), look for the entry or entries you wish to modify and add in the following text before the "--" part of the "append" parameter for that entry.

```
cdrom-detect/try-usb=true
```

Once done, save, eject and then boot your box with the now fixed installer :KS
sorry..can you tell me specific about the code??i'm newbie

---

### Post by setsuna on 2010-05-02
> **rusti06 said:**
> sorry..can you tell me specific about the code??i'm newbie

as geekoid said..
just add the "cdrom-detect/try-usb=true" after the "--" sign

i.e, i want to customizing my default line on alternate usb install, so i open the syslinux.cfg and find the "menu label default" and edit, the line goes like this :

```
label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit vga=normal -- quiet cdrom-detect/try-usb=true 
```

do the same action if want to fix the other option on our alternate usb install ;)

---

### Post by aNt1X on 2010-09-16
After many CD burned, i was still getting the "corrupted CD" error, no matter i used internal and external drives...

Just wanted to report that this trick worked for me too, with Ubuntu Alternate 10.04.1 64bit and UNetBootIn 471, on a HP ML115 with SATA RAID1.

Start UnetBootin, Select Ubuntu and "HDMedia_64", then create the pendrive.

Boot your machine with the USB pendrive.

Select the menu item "Install", DON'T press ENTER, just press TAB and add the "cdrom-detect/try-usb=true" before the "--", press ENTER and sit down.

Thank you.

---

### Post by scoz on 2010-10-22
Hi,

The method with "cdrom-detect/try-usb=true" didn't work for me. Here is what I do when I want to install Ubuntu (or Debian) with UNetBootIn. It requires two USB sticks.

1. Download the iso image of Ubuntu.

2. Use UNetBootIn to make a bootable USB stick from the iso image.

3. Create a partition on your **other** USB stick, which must be big enough to put the iso image on it (I usually make it a few MB bigger).

4. Overwrite this partition with the iso image. Let's say the partition is named /dev/sdc1. Then run this shell command:
```
dd if=/tmp/ubuntu-10.04.1-server-i386.iso of=/dev/sdc1
```
Of course, replace /tmp/ubuntu-10.04.1-server-i386.iso with the path of your iso image, and /dev/sdc1 with the path to the partition you created on the USB stick. Remember the number of this partition (number 1 if the partition is /dev/sdc1, number 2 if the partition is /dev/sdc2, etc).

5. boot on the USB stick you created with UNetBootIn.

6. Run the installer normally until it says "No common CD-ROM drive was detected" and asks "Load CD-ROM drivers from removable media?"
Chose "NO".
Then it asks "Manually select a CD-ROM module and device?"
Chose "YES".
Then it asks to chose a module from a list, chose "none".
Then it asks for the device file for accessing the CD-ROM.
Here you must plug the second USB stick. You can press alt+F2 to switch to a console that you can use to find out the name of the partition that contains the iso image (that you wrote with the dd command).
Type this:
```
cat /proc/partitions
```
To list all partitions
Or you can type this:
```
tail /var/log/syslog
```
to see what the kernel did with the USB stick you just inserted (it should say what device name it gave to it).

Let's say the device name is /dev/sde. Then the partition is /dev/sde followed by the number I told you to remember at step 4, so it's /dev/sde1.
So come back to the previous screen by pressing alt+F1 and type /dev/sde1 in the dialog box. Press enter and you're done.

---

### Post by jakeo25 on 2011-03-04
Hello All,

This seems to have worked for the "Cannot find CD" error when I tried to install version 10.10:

[LIST=1]
[*]Boot your machine with the USB stick.
[*]Select the menu item "Install Ubuntu Studio"
[*]Press TAB (don't press enter)
[*]Add "cdrom-detect/try-usb=true" before the "--" (excluding the quotes) 
[*]Press ENTER
[/LIST]

This worked on my Toshiba Satellite laptop.

The radio (wifi) wasn't detected during install, so I needed to hook up directly during install -- I may have more questions for all of you for how to configure it. :P

Jake

---

