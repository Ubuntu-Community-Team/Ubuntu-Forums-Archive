---
title: "Grub Error 21 after install"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Sups- on 2008-11-10
I decided to install Ubuntu on one of my computers, I used the live CD and pretty much only clicked continue so no manual settings there. Everything seemed fine untill my computer rebooted and gives me Error 21. Reinstalling also gives me the same problem.

I've searched the forums and read through most of the threads about error 21 I could find but I either can't follow the instructions well enough or the method doesn't fix the error. Most threads also include a problem of dual booting, which I'm not trying to do I only have one hardrive and would simply like Ubuntu on it.

 The BIOS doesn't seem to be recognizing my Hardrive anymore, So i tried auto detecting in BIOS and nothing comes up, setting it to manual didn't do anything after the reboot either. So I'm left thinking that something hardware wise isn't supported? I tried loading supergrub but all the options there also don't work. Also the Grub errors at loading stage 1.5.

Heres my Fdisk when booting from the CD. I'm guessing somethings missing there since everyone elses seems longer.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb27852ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38158   306504103+  83  Linux
/dev/sda2           38159       38913     6064537+   5  Extended
/dev/sda5           38159       38913     6064506   82  Linux swap / Solaris

As you can see I have little to no knowledge about Linux, so if you have any solutions/advice it would help if you laid it out step by step :P.

Thanks in advance. 

PS(It'll be awhile before I reply need to catch up on sleep)
PSS (Sorry if theres any bad english in there)

---

### Post by sirebral on 2008-11-10
You need to fix your grub loader.  It sounds like your grub loader is broken.

I've had that error after I installed and hen removed Windows.  The grub loader was looking for the Vista partition and couldn't find it so it returned an error.

I think I also removed an old linux partition.  That was messy.  I'm glad I have an external HD now.

---

### Post by caljohnsmith on 2008-11-10
OK, just to make sure your Grub is properly installed to your HDD, how about booting your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of those commands, reboot, and let me know if anything changes. We can work from there.

---

### Post by psusi on 2008-11-10
Is this a really old computer?  Like a Pentium 1?  If so the bios may not be able to understand hard drives larger than 8 GB.  If that is the case, then you need to make a /boot partition as the first partition on the disk, below the 8 GB mark.  It only needs to be maybe 100 or 200 mb, but try what the above poster said first.

---

### Post by Sups- on 2008-11-10
> Is this a really old computer?
Its a core 2 duo, around 2 years old.

> Please post the output of those commands
grub> root (hd0,0)



grub> setup (hd0)

 Checking if "/boot/grub/stage1" exists... yes

 Checking if "/boot/grub/stage2" exists... yes

 Checking if "/boot/grub/e2fs_stage1_5" exists... yes

 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.

succeeded

 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2

/boot/grub/menu.lst"... succeeded

Done.


I rebooted afterwards and I still get the same error.

Edit: I've just tried those commands again after grub>quit  which gives me the "Probing devices to guess BIOS drives. This may take a long time." I don't think I waited for that the first time and rebooted. Roughly how long should this take?, i've left it up for about 2 hours now and the computer doesnt seem to be loading anything.

> You need to fix your grub loader.
Is there a step by step guide out there on how to do this, everything I've found asks me to edit my grub menu, without telling me what to actually edit.

Thanks, keep the help coming guys.

---

### Post by caljohnsmith on 2008-11-10
OK, how about doing:
```
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
That command should return "ff00". If it does, try this:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
Reboot, and let me know what happens.

EDIT: Based on some of the comments you've added, it sounds like you might have a hardware problem or possibly a problem with how your HDD is setup in BIOS. I would go ahead an try the above commands though to see if it makes any difference, but unfortunately I'm doubtful they will help.

---

### Post by Sups- on 2008-11-10
I seem to be doing something wrong, I've gone through the command to check any spelling/space mistakes but it all seems allright.

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}

> sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}

awk: line 2: syntax error at or near if

awk: line 3: missing } near end of file

EDIT: Ah, how should I go about fixing a hardware problem? Like I said before my BIOS was not picking up my HDD on auto or manual after the Ubuntu installation. At bootup it does show me a line saying my current drives. 
"HDD0: XXXXXXXXXX 320GB etc"

However going into bios and checking Primary has no drive at 0GB.

EDIT2: My Hardrive appeared on the LIVECD Desktop as 316GB Media so I decided to reboot and see if anything changed. Now instead of getting Grub Error 21, it automatically Loads the Grub Command line. I've tried typing root (hd0,0) but that gives me error 21. So I guess I'm still stuck at what I was at before.

EDIT3: Booting up with the livecd again, my hardrive is not shown on the desktop anymore.

---

### Post by Sups- on 2008-11-11
Bump, Any help would be great

EDIT: I tried this again,

sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit 

because I was confused at how I was able to see this 

"Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2

/boot/grub/menu.lst"... succeeded"

When my HDD is not being picked up, 

Alas, I seem to be getting error 21 now when I try to grub> root (hd0,0)

By the looks of it the majority of this board seems to be from different time zones I'll give reinstalling Ubuntu another go while everyone's off-line, though doubtful that it'll do anything. Keep the help coming :P

EDIT2: Well reinstalling does nothing.

---

### Post by caljohnsmith on 2008-11-11
If your HDD is not even show up any more, it sounds to me like you most likely have a hardware problem since the behavior keeps changing and is not even consistent. Can you at least check the the HDD's connections? I would reseat the cable connectors just to make sure they aren't loose or something. Let us know how it goes.

---

### Post by Sups- on 2008-11-11
Just checked, and pushed the cables in abit tighter, still get the GRUB 21 ERROR. And just to confirm before installing Ubuntu, Vista worked fine without any hardware errors.

---

### Post by psusi on 2008-11-11
You need to straighten out your bios so it properly recognizes the disk or there is no way it will boot.  Look for a large disk access option and make sure the controller is in AHCI mode if this is SATA.

Also on the other command you went wrong because you left out the closing ' after the }.

---

### Post by bwallum on 2008-11-24
I'm getting this error.

I installed a second hard drive to my friends machine. I used 'cable select' for the jumper in each drive. The primary (existing) drive has a Windows XP Pro os installed. I tried to install Intrepid on the secondary (newly fitted drive). Everything appeared to be going fine using the live CD install method. I chose guided install for the whole secondary drive. Both drives were fully identified by the partition editor. There were no error messages in the install. 

However upon reboot as advised, I got the Ubuntu horizontal bar for a while then a terminal screen (full) advising exit, some numbers and text I did not understand and then the message to remove the CD and press Enter.

The CD did not respond to pressing the tray button. After a while I pressed enter and the machine started to reboot. At that stage I pressed the cd tray button and removed the CD. I then got the grub screen and error 21.

This is a production machine (the Windows part) and I cannot access the Windows drive. The machine currently stops at error 21 message.

Please help.

---

### Post by caljohnsmith on 2008-11-24
Bwallum, can you set your BIOS to boot the secondary drive? If so, then you can install Grub to the MBR (Master Boot Record) of your secondary drive and boot it directly. That way you can keep your drives independent of each other, and if you restore a Windows MBR to the Windows drive, you should be able to boot the Windows drive regardless of whether you have problems with the Ubuntu drive. 

If that sounds good to you, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of all the following commands:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above find commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also, if you want to go ahead and restore a Windows MBR to your Windows drive so you can immediately get into Windows again, just do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
If none of the above commands give you any errors, reboot, set your BIOS to boot the Ubuntu drive, and you should at least get a Grub menu on start up if all goes well. Let me know if you can get that far or if you run into problems. :)

---

### Post by bwallum on 2008-11-26
> **caljohnsmith said:**
> .....Let me know if you can get that far or if you run into problems. :)

Thanks for the help. The main issue was the BIOS. The machine is an old Dell Optiplex GX260. The bios setup page is a single screen. Some items have options which are accessed by highlighting an item and pressing the return or right arrow key. It seems to operate oddly in that a keyboard error is thrown if accessing the cmos setup screen (F2 key) after completely powering down the machine, i.e. turning off or unplugging at the power socket. The machine was also using a wireless keyboard which seemed to add to the irrational behaviour.

Anyway, I took out the 160Gb drive and put in a 20Gb drive known to work. I forced the primary drive to master with the jumper pin on the drive and connected up to the primary end of the cable, The 20Gb drive was forced to slave and connected to the secondary connector on the cable.

Hey presto the cmos picked up the drive as unknown. Right arrow allowed me to detect 'auto', I rebooted and checked the cmos. It now showed a secondary drive with the correct capacity. I took out the 20Gb drive, inserted the 160Gb drive, again forced to slave and then rebooted to setup. The drive was correctly shown.

I installed Intrepid on the 160Gb drive. All appeared well until right at the end it says to remove the CD and press enter. It would not let me have the install cd, The button on the cd drive would not open it. I pressed enter anyway and as the reboot started removed the cd with the button on the cd drive.

I got grub! Enthused by my success I tested the Windows boot, all ok. I then rebooted and tested the Intrepid install. It displayed the Ubuntu splash page and the horizontal bar filled. The screen then displayed an 'X' and then the mouse pointer icon....and that is all it displayed. I left it for a couple of hours, waggled the mouse about, saw the pointer icon move as expected on the screen.

The Intrepid i386 live cd IS DEFECTIVE! This is the second occassion that I have had trouble with it (md5sum matches published).

So, I installed Hardy i386 and install was clean. I then updated Hardy, then upgraded to Intrepid, then updated Intrepid. 

Now my previous nonsense with Intrepid occurred when changing monitors. I asked my friend what resolution he normally worked with. I then changed the resolution to his desired 1024x768. I went to restart and got a mess on the screen. At reboot the normal Ubuntu splash and bar had disappeared and was replaced with a blank scree. Within a normal amount of time the desktop appeared in the desired resolution. 

I'm a Ubuntu fan so please hear me when I say Intrepid has serious issues for new installs from the live i386 cd and when changing monitors. The previous blow up was on an AMD64 rig, nvidia and a 22" widescreen monitor (still unresolved by the way, it insists on using a 4:3 proportioned view, very ugly on a wide screen)

I'm now about to take the i386 machine back to my friend and plug in his monitor. Fingers crossed....

---

### Post by bwallum on 2008-11-26
Very happy to report, that if changing monitors, presetting a resolution on the current monitor to one that the new monitor can use ensures a clean change of monitors.

---

