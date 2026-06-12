---
title: "Grub Rescue"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by sewbiz on 2014-06-14
I need an expert. I removed .mod files in GRUB...I know....very bad move...now I have
a crash to deal with. Grub rescue please help!

continuing to get unknown command messages...don't know what to ask for....
need to reinstall grub2 but how to? can't install disc with distribution either...please help.
will do more hours of research...benefits of being a Linux user. NOT!

---

### Post by sammiev on 2014-06-14
Hi,

You gave us really no info like what OS are on your computer and what type of boot system you had or have? ( like Win8 )
What type of computer you have with specs?

Here's a good [link]("https://help.ubuntu.com/community/Boot-Repair") to get you going. You can make a boot able USB so you can  repair your problems.

If you only have one HDD and it's a older computer you can usually just boot from a live version of the Install OS you used and install the grub over again.

```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by sewbiz on 2014-06-15
The command you suggested did not work...it says...unknown command 'sudo' on my screen.

I have a Linux OS version bethe....32 bit...my son built it so msdos compatible 
Ubuntu 12.04 LTS bethe

Desktop

The system boots with the disc but I only now get a black screen with
grub rescue>                       It does respond when I type in ls     but other commands I type
are not successful....I get....unknown command....or file not found. I think the boot is in hd0,msdos  because
when I type (hd0,msdos3)/boot it tells me   ./   ../      which now worries me. What does that mean?

---

### Post by sewbiz on 2014-06-15
> **sewbiz said:**
> The command you suggested did not work...it says...unknown command 'sudo' on my screen.

I have a Linux OS version bethe....32 bit...my son built it so msdos compatible 
Ubuntu 12.04 LTS bethe

Desktop

The system boots with the disc but I only now get a black screen with
grub rescue>                       It does respond when I type in ls     but other commands I type
are not successful....I get....unknown command....or file not found. I think the boot is in hd0,msdos  because
when I type (hd0,msdos3)/boot it tells me   ./   ../      which now worries me. What does that mean?

Once I download the boot repair kit disc and the grub2 disc to my usb drive. What are the next steps. I put it in the usb port for my desktop (which is broken being in grub rescue mode).....I shut off and restarted the computer.....then what? Do I need to first config any files on the discs themselves? What is the command I type into the screen? All I have on the screen is a prompt that says......grub rescue>        nothing like the terminal where it has my name on the screen. How do I talk to this? It seems the typical commands it does not recognize. Should I put in '   in front of my words. I am fairly new at this.

---

### Post by oldfred on 2014-06-15
If you have a working Ubuntu live/installer DVD or flash drive you can just add Boot-Repair as suggested by sammiev above. If you download the full ISO you do not copy the ISO to a flash drive, but have to install it just like you do any ISO. Otherwise is it not bootable.

Once you have a bootable flash drive you just restart PC and use one time boot key (often f12 but varies by vendor) or in BIOS choose to boot flash drive.  If you still get grub rescue then DVD or flash drive is not bootable and BIOS is defaulting back to hard drive with broken grub.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by sewbiz on 2014-06-15
Aren't all flashdrives the same? Please dumb down your comment

---

### Post by sewbiz on 2014-06-15
> **oldfred said:**
> If you have a working Ubuntu live/installer DVD or flash drive you can just add Boot-Repair as suggested by sammiev above. If you download the full ISO you do not copy the ISO to a flash drive, but have to install it just like you do any ISO. Otherwise is it not bootable.

Once you have a bootable flash drive you just restart PC and use one time boot key (often f12 but varies by vendor) or in BIOS choose to boot flash drive.  If you still get grub rescue then DVD or flash drive is not bootable and BIOS is defaulting back to hard drive with broken grub.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

How do I get a bootable flash drive? How do I use F12 key.....shift then F12 (holding down at the same time)?

---

### Post by sewbiz on 2014-06-15
> **sammiev said:**
> Hi,

You gave us really no info like what OS are on your computer and what type of boot system you had or have? ( like Win8 )
What type of computer you have with specs?

Here's a good [link]("https://help.ubuntu.com/community/Boot-Repair") to get you going. You can make a boot able USB so you can  repair your problems.

If you only have one HDD and it's a older computer you can usually just boot from a live version of the Install OS you used and install the grub over again.

```
sudo grub-install /dev/sda
sudo update-grub
```

The command you suggested did not work...it says...unknown command 'sudo' on my screen.

I have a Linux OS version bethe....32 bit...my son built it so msdos compatible 
Ubuntu 12.04 LTS bethe

Desktop

The system boots with the disc but I only now get a black screen with
grub rescue>                       It does respond when I type in ls     but other commands I type
are not successful....I get....unknown command....or file not found. I think the boot is in hd0,msdos  because
when I type (hd0,msdos3)/boot it tells me   ./   ../      which now worries me. What does that mean?

---

### Post by sammiev on 2014-06-15
Here is a how to using [UNetbootin]("http://unetbootin.sourceforge.net/") and there is many other programs that do the same.

---

### Post by oldfred on 2014-06-15
These are the keys often used by brand of computer whether older BIOS or newer UEFI.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Unless your keyboard shows multiple key assignments, usually you just press f12 immediately on power up, well before grub or Windows boot loader has a chance to take over boot process.

---

### Post by sewbiz on 2014-06-23
I am back from vacation and back at working for a "fix" for my computer. 
I am currently reinstalling 11.04 alongside Ubuntu 12.04.4 LTS (which I have on my computer) using a live CD of my old system version (11.04 Ubuntu).
My boot volume was 100% full and while
trying to correct the problem I was having, by removing files manually (following the risky advice of a user with not enough beans to know
fully what he/she was recommending), I stupidly deleted some .mod files in grub I thought were media/music files. YIKES!!! CRASH!
So ..... two weeks into this, and back from a few days away on vacation (while gone I did some "reading" up to have a better understanding
of how this Ubuntu works for my scenario)...I need some recommendations. I am awaiting for the install to complete....it has been 3 hours...still 
says "resizing partition". I have a BIOS utility. It told me it takes a long time...but how long is that? Would love to hear from other users who have had to do this.

Also....what next steps would I take to correct the errors (reinstall missing files-.mod) in Grub2 on my Ubuntu 12.04.4 LTS. 
I have a desktop (Samsung)...any other info you need? Should I start a new thread? This is unrelated to the initial title on this post. : (
One thing has led to another.

---

### Post by Bashing-om on 2014-06-23
sewbiz; OH Boy.

Allow me to step in here and try and assist.

1st, 11.04 is a no no ! .. Release 11.04 is End-Of-Life, the software repository has been turned down and that release is no longer supported.
2nd, We must have a liveDVD/USB to work from to (RE-)install grub .. as /boot is full we may have to jump through several hoops to do this.
Download the 12.04.4 .iso file release from:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Burn the .iso as an image NOT data at a slow rate:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

And finally check the liveDISK for defects:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

3rd, Now we are ready to go to work.
Boot the liveDVD to a terminal and execute terminal commands:
# represents a comment not to be executed. If you have more than 1 hard disk installed and ubuntu is NOT installed onto that 1st partition, then adjustements to these commands will have to be made.
```

sudo fdisk -lu ##to make sure the hard drive we are working with is indeed 'sda' else STOP and re-evaluate.##
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

We can hope there is "room" for grub to re-install // else ... well there are ways to jump over that too. We cross that bridge when we get to it.

Press on !

[INDENT][INDENT]ain't no step for a stepper[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-23
Can I download to a USB drive? But you say I need a LIVE DVD. I am confused. How will my computer be able to "read" the program that is uploaded to a USB?
Baby steps please. I am not all that familiar with all things UBUNTU. Ubuntu 12.04.4LTS is currently on my computer that has the FULL BOOT volume.  : (

---

### Post by oldfred on 2014-06-23
This has instructions for both Windows and Ubuntu on install to flash drive or DVD. And a one button to download, choose the 64 bit version unless system is real old.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)



You download the ISO and use the tool for either Windows or Ubuntu to install from ISO to flash drive or DVD. More details in each of the links by Bashing-om with screen shots so you can follow along to know exactly what to do.

---

### Post by sewbiz on 2014-06-23
If to a flash drive....how will my system "read" the USB? It is in grub rescue mode. No terminal to get to...no desktop.

---

### Post by Bashing-om on 2014-06-23
sewbiz; A thought;

Boot up that 11.04 EOL liveCD and download the .iso file and
burn the .iso to a usb-stick:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

we keep on
[INDENT][INDENT]'til this is a done deal
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-23
> **Bashing-om said:**
> sewbiz; OH Boy.

Allow me to step in here and try and assist.

1st, 11.04 is a no no ! .. Release 11.04 is End-Of-Life, the software repository has been turned down and that release is no longer supported.
2nd, We must have a liveDVD/USB to work from to (RE-)install grub .. as /boot is full we may have to jump through several hoops to do this.
Download the 12.04.4 .iso file release from:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Burn the .iso as an image NOT data at a slow rate:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

And finally check the liveDISK for defects:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

3rd, Now we are ready to go to work.
Boot the liveDVD to a terminal and execute terminal commands:
# represents a comment not to be executed. If you have more than 1 hard disk installed and ubuntu is NOT installed onto that 1st partition, then adjustements to these commands will have to be made.
```

sudo fdisk -lu ##to make sure the hard drive we are working with is indeed 'sda' else STOP and re-evaluate.##
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

We can hope there is "room" for grub to re-install // else ... well there are ways to jump over that too. We cross that bridge when we get to it.

Press on !
[INDENT][INDENT]ain't no step for a stepper[/INDENT]
[/INDENT]


I can't open a terminal to check anything. How to get to a terminal when the system won't boot to get me to desktop?

---

### Post by sewbiz on 2014-06-23
> **Bashing-om said:**
> sewbiz; A thought;

Boot up that 11.04 EOL liveCD and download the .iso file and
burn the .iso to a usb-stick:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

we keep on[INDENT][INDENT]'til this is a done deal
[/INDENT]
[/INDENT]


Was told this was a bad idea....ooops...too late...did what you suggested here...now on to other advice.
But....do appreciate all help...good or bad, trial and error with Linux. Still no fix in sight....holding back the tears!

---

### Post by Bashing-om on 2014-06-23
sewbiz; Making good progress.

Admittedly 11.04 not the best tool to use, but get 12.04.4 burned to the usb thumb drive ..will be all done with 11.04 and we can then move on.

[INDENT]it ain't nothing but a thing
[/INDENT]

---

### Post by sewbiz on 2014-06-23
I burned the image file to DVD. I put the DVD into my computer (the broken one in grub rescue mode. Black screen on 
computer says   grub rescue>  _      (the dash is blinking)     now what?

Is the sudo command "SAFE"....I read somewhere it wasn't at the point I am at. Also...when I have typed it before
my computer told me " unknown command 'sudo'
Do I have to use certain types of commands it will understand. I will try what you suggest and get back to you.

I tried both with and without 'sudo' and the command 'fdisk -lu'
Using one I get..... unknown command 'sudo'    the other I get .....    unknown command 'fdisk'
Should I be using     different symbols?  It does not understand my language.

---

### Post by Bashing-om on 2014-06-23
sewbiz; Hummm....

That is not supposed to happen !
OK, what pops to mind is that you are booting to the install rather then the liveDVD.

Verify that in bios you have reset the boot priority to boot from the CD drive;
Verify once more that the md5sum of the .iso matches
verify once more that the liveDVD passes "check disk for defects"
Now boot the liveDVD 12.04.4 -> "try ubuntu" -> terminal

"sudo" should be good in that liveDVD.
In that liveDVD terminal what returns now from terminal command:
```

sudo fdisk -lu

```

Presently I have no clue why the command " sudo fdisk -lu " is not accepted:
reference from my system that command:
```

sysop@1310mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1310mini:~$ 

```
note that with the use of "sudo" in the live environment a password is not required but in that install you must supply your pass word and when the pass word is entered there is no response to the screen ( security reasons).

If you are booting into a "grub >" prompt, only a limited amount of terminal commands are available, and yes 'sudo and fdisk' are not available.

[INDENT][INDENT]we keep hammering away
[INDENT][INDENT][INDENT]'till something gives
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-23
I turn on the computer. I open drawer for my live DVD with the burned image file. Close drawer. Only get a black screen after the computer comes on...flashes the screen quickly at the start...then all goes black except the black and white screen with the words.....error: file not found.      grub rescue> _    (dash is flashing)

I did not......

Verify that in bios you have reset the boot priority to boot from the CD drive;
Verify once more that the md5sum of the .iso matches
verify once more that the liveDVD passes "check disk for defects"
Now boot the liveDVD 12.04.4 -> "try ubuntu" -> terminal

because it is all too complicated as to how to (trying things on my own when I am waiting for replies from people).

I got as far as the DVD burn...not even sure I burned the correct one...but only the one suggested on the website
that told me to...."if I was not sure".  Things have to be really DUMBED down for me. My son got me into this LINUX world.
But I do love it being of an analytical mindset.

---

### Post by oldfred on 2014-06-23
There are two terminals, if you will.
Grub rescue> is a very limited terminal where you can put in a few commands to help booting. 
It is not the standard Ubuntu terminal where you can run many commands.

At grub rescue, type these commands. If you have flash unplugged I would expect grub to be (hd0,1), but if plugged in then it may be (hd1,1).

       ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd1,1), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

If that does not work, again if above shows (hd1,1) use that and change sda1 to sdb1 on linux line:
ls (hd0,1)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,1)/boot # Do you see the kernel and initrd image files ?
set prefix=(hd0,1)/boot/grub
      set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro nomodeset
initrd /initrd.img

---

### Post by Bashing-om on 2014-06-23
sewbiz; OK,

You must direct the computer what to boot up, in this instance we want to boot the DVD. To boot the DVD the boot priority must be changed in bios settings.

How one enters bios differs with each and every manufacturer and version of bios.
Most prevalent in "older" systems is to hit the delete key as soon as the bios screen appears, or maybe the F12 key or similar. Many times there is an advisory when the bios screen appears as to which key will access the bios set up utility. In the bios there are several screens accessable from the primary screen, arrow keys, enter key and escape key applies. All I can suggest is to look around in the bios and determine where the option is to change the boot priority to the CD drive.

Else if you still can  not figure out how to change the boot priority, post back the bios manufacurer and version as depicted on the bios boot screen, when you are booting up; and I will see what I can find out to direct your efforts.

There is no magic pill, one just has to roll up the sleeves and do it themselves.

It's ubuntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-23
> **oldfred said:**
> There are two terminals, if you will.
Grub rescue> is a very limited terminal where you can put in a few commands to help booting. 
It is not the standard Ubuntu terminal where you can run many commands.

At grub rescue, type these commands. If you have flash unplugged I would expect grub to be (hd0,1), but if plugged in then it may be (hd1,1).

       ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd1,1), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

If that does not work, again if above shows (hd1,1) use that and change sda1 to sdb1 on linux line:
ls (hd0,1)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,1)/boot # Do you see the kernel and initrd image files ?
set prefix=(hd0,1)/boot/grub
      set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro nomodeset
initrd /initrd.img

When I type ls    i only see this:     (hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos7) (hd1,msdos6)  (hd1,msdos5)

I get no other information. When I do ....  hd1/boot      ls     I get     ./  ../       (commands you will see explained in previous comments on this thread).
That is the furthest I ever get in this grub rescue command  text screen (not a terminal!)  : (

---

### Post by sewbiz on 2014-06-23
> **Bashing-om said:**
> sewbiz; OK,

You must direct the computer what to boot up, in this instance we want to boot the DVD. To boot the DVD the boot priority must be changed in bios settings.

How one enters bios differs with each and every manufacturer and version of bios.
Most prevalent in "older" systems is to hit the delete key as soon as the bios screen appears, or maybe the F12 key or similar. Many times there is an advisory when the bios screen appears as to which key will access the bios set up utility. In the bios there are several screens accessable from the primary screen, arrow keys, enter key and escape key applies. All I can suggest is to look around in the bios and determine where the option is to change the boot priority to the CD drive.

Else if you still can  not figure out how to change the boot priority, post back the bios manufacurer and version as depicted on the bios boot screen, when you are booting up; and I will see what I can find out to direct your efforts.

There is no magic pill, one just has to roll up the sleeves and do it themselves.

It's ubuntu[INDENT][INDENT][INDENT]it is fixable
[/INDENT]
[/INDENT]
[/INDENT]


Manufacturer.... Intel     Bios (F2)  
I have the box the motherboard came in......Intel Desktop Board....DG41TX Classic Series....for the Intel Core 2 Quad   and Intel Core 2 Duo Processors.

My son made my machine to be compatible with Microsoft Windows should I ever want to use my program. I do have my Compaq (old laptop) Live Operating System CD for Windows XP.

---

### Post by oldfred on 2014-06-23
I am confused.
Is system giving grub rescue or DVD and which DVD is this, the 11.04 or 12.04?

If from hard drive do any of these show the kernel and initrd image files ?

ls (hd0,msdos4)/
 ls (hd0,msdos3)/
 ls (hd0,msdos2)/
 ls (hd0,msdos1)/
ls (hd1,msdos7)/
 ls (hd1,msdos6)/
  ls (hd1,msdos5)/

And if trying to boot DVD and just getting grub rescue means you are not booting DVD. Either not selected as first to boot from one time boot key or in BIOS or not a valid bootable DVD.
And at DVD you should get tiny icons (asscessiblity) of a stick figure and keyboard. Press any key immediately and then f6 so you can add nomodeset.

---

### Post by Bashing-om on 2014-06-23
sewbiz; Hey ;

See oldfred's last message.

See if this is not your bios and the included instructions.
[http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v13.pdf](http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v13.pdf)

Insure you are set to boot the DVD.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-23
MORE info about computer....Intel Celeron Processor ......Intel 64 Architecture (First page title)

---

### Post by sewbiz on 2014-06-23
I am not using the live 11.04 DVD....I have in the drawer thing on the computer my newly burned only image file. Thinking about downloading from the internet and  burning a live 12.04.4.4 LTS but no safe way to do that.

---

### Post by sewbiz on 2014-06-23
> **oldfred said:**
> I am confused.
Is system giving grub rescue or DVD and which DVD is this, the 11.04 or 12.04?

If from hard drive do any of these show the kernel and initrd image files ?

ls (hd0,msdos4)/
 ls (hd0,msdos3)/
 ls (hd0,msdos2)/
 ls (hd0,msdos1)/
ls (hd1,msdos7)/
 ls (hd1,msdos6)/
  ls (hd1,msdos5)/

And if trying to boot DVD and just getting grub rescue means you are not booting DVD. Either not selected as first to boot from one time boot key or in BIOS or not a valid bootable DVD.
And at DVD you should get tiny icons (asscessiblity) of a stick figure and keyboard. Press any key immediately and then f6 so you can add nomodeset.

Oh...wow....I am now super excited.....I did not add  / at the end of my lines....getting somewhere!!!
I will try all these instructions and let you know.  SEE I need to know step by step the smallest little detail! BRB

I am so excited....found BOOT!!!   Found vmlinuz....selinux....vmlinuz.old run/.....others

These are in (hd0,msdos3).....what is next?

---

### Post by sewbiz on 2014-06-23
> **Bashing-om said:**
> sewbiz; Hummm....

That is not supposed to happen !
OK, what pops to mind is that you are booting to the install rather then the liveDVD.

Verify that in bios you have reset the boot priority to boot from the CD drive;
Verify once more that the md5sum of the .iso matches
verify once more that the liveDVD passes "check disk for defects"
Now boot the liveDVD 12.04.4 -> "try ubuntu" -> terminal

"sudo" should be good in that liveDVD.
In that liveDVD terminal what returns now from terminal command:
```

sudo fdisk -lu

```

Presently I have no clue why the command " sudo fdisk -lu " is not accepted:
reference from my system that command:
```

sysop@1310mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1310mini:~$ 

```
note that with the use of "sudo" in the live environment a password is not required but in that install you must supply your pass word and when the pass word is entered there is no response to the screen ( security reasons).

If you are booting into a "grub >" prompt, only a limited amount of terminal commands are available, and yes 'sudo and fdisk' are not available.
[INDENT][INDENT]we keep hammering away[INDENT][INDENT][INDENT]'till something gives
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I am told it is because I am in grub rescue mode....this is not the terminal but only a text screen....with limited command potential. Something to that effect...would have to look back on these messages in this thread.

---

### Post by sewbiz on 2014-06-23
Found BOOT....Found vmlinuz....selinux....vmlinuz.old run/.....others

These are in (hd0,msdos3).....what is next?

---

### Post by oldfred on 2014-06-23
go back to post #23 and  use (hd0,3) and sda3 instead in examples posted.

---

### Post by sewbiz on 2014-06-23
> **oldfred said:**
> go back to post #23 and  use (hd0,3) and sda3 instead in examples posted.

Did you mean replace with (hd0,msdos3) and sda3?

Also...my image files initrd are non-existent. Will these commands work without them???
I think these may be some of the files I stupidly removed.
I suppose we can spend a few extra weeks in training how to recover them.....later. Always hopeful!

INSTRUCTIONS in post #23:

ls (hd0,1)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,1)/boot # Do you see the kernel and initrd image files ?
set prefix=(hd0,1)/boot/grub
      set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro nomodeset
initrd /initrd.img 				

SO I WOULD DO THIS????   Is this all on the same line....do I need to do some peculiar marks so computer knows to do this then this then this.... like && or ||
Been doing some reading about this stuff so just want to be sure I have all the steps correct. 

ls (hd0,msdos3)/
ls (hd0,msdos3)/boot
set prefix=(hd0,msdos3)/boot/grub
set root=(hd0,msdos3)
linux /vmlinuz root=/dev/sda3 ro nomodeset
initrd /initrd.img

---

### Post by sewbiz on 2014-06-23
> **sewbiz said:**
> Did you mean replace with (hd0,msdos3) and sda3?

Also...my image files initrd are non-existent. Will these commands work without them???
I think these may be some of the files I stupidly removed.
I suppose we can spend a few extra weeks in training how to recover them.....later. Always hopeful!

INSTRUCTIONS in post #23:

ls (hd0,1)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,1)/boot # Do you see the kernel and initrd image files ?
set prefix=(hd0,1)/boot/grub
      set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro nomodeset
initrd /initrd.img                 

SO I WOULD DO THIS????   Is this all on the same line....do I need to do some peculiar marks so computer knows to do this then this then this.... like && or ||
Been doing some reading about this stuff so just want to be sure I have all the steps correct. 

ls (hd0,msdos3)/
ls (hd0,msdos3)/boot
set prefix=(hd0,msdos3)/boot/grub
set root=(hd0,msdos3)
linux /vmlinuz root=/dev/sda3 ro nomodeset
initrd /initrd.img

While waiting....I typed in the second set of commands I had questions about. I got stumped )when the computer stopped giving me a prompt
without an error message... at this point:

linux /vmlinuz root=/dev/sda3 ro nomodeset    #computer said....Unknown command 'linux/vmlinuz'   (was I suppose to have a "space" between the two words?)
initrd /initrd.img     				#computer said....Unknown command...again...'initrd/initrd.img'     (maybe need spaces again?)

I will try retyping......NOPE...still....unknown command....'linux'     :(

---

### Post by Bashing-om on 2014-06-23
sewbiz; Well,

I am accustomed to a different structure.
Let me get from you a bit of info and I will structure up the command syntax that I am familiar with.
at that grub > prompt what returns from:
```

search -f /vmlinuz
search -f /sbin/init
ls -la (hd0,msdos3)

```
and then we can set some paths and attempt to boot the operating system from that grub > prompt.

[INDENT]more than one path
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-23
Did  you say you deleted the essential boot files?

Then you have to either reinstall or perhaps chroot into your system from a working live DVD or flash drive that is preferably the same version.
Then you have to update system, reinstall kernel & rebuild initrd files from inside the chroot.

Chroot requires you to exactly type in many commands and spaces are also vital.

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once you correctly chroot, all text after a # is a comment, do not type:

      
 #houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

update-initramfs

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Well,

I am accustomed to a different structure.
Let me get from you a bit of info and I will structure up the command syntax that I am familiar with.
at that grub > prompt what returns from:
```

search -f /vmlinuz
search -f /sbin/init
ls -la (hd0,msdos3)

```
and then we can set some paths and attempt to boot the operating system from that grub > prompt.[INDENT]more than one path[INDENT][INDENT][INDENT]to an end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om; did you read that I deleted some essential files in GRUB?  Do I have to do the chroot thing instead? Read message #38 from oldfred. I don't want to do anything that is 
a waste of my time and already yours.

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Well,

I am accustomed to a different structure.
Let me get from you a bit of info and I will structure up the command syntax that I am familiar with.
at that grub > prompt what returns from:
```

search -f /vmlinuz
search -f /sbin/init
ls -la (hd0,msdos3)

```
and then we can set some paths and attempt to boot the operating system from that grub > prompt.
[INDENT]more than one path[INDENT][INDENT][INDENT]to an end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


This is what I get: (in the order of commands typed)
Unknown command 'search'
Unknown command 'search'
error: bad filename.

Seems the only command this screen (NOT TERMINAL) knows is 'ls'.   : (

---

### Post by Bashing-om on 2014-06-26
sewbiz; Hello.

Troubleshooting a problem is never a waste of our time. Finding a solution is our goal. I try to do so in the simplest terms possible.

We are now at the stage of doing as oldfred advises. A full CHange Root and (RE-)install of grub in that environment.

I have posted that procedure in another thread:
[http://ubuntuforums.org/showthread.php?t=2230969&page=2&p=13059170#post13059170](http://ubuntuforums.org/showthread.php?t=2230969&page=2&p=13059170#post13059170)
My post#13 in that other thread, rather than repeating, please use it as the guide.

I am thinking that your ubuntu install is the same as in that other thread - ubuntu installed onto that 1st hard drive (sda) and the operating system at large is on the 1st partition ( hd0 in grub speak). Else adjust to the partition that "/" is installed to. Any doubts and we will clarify, one way or another.

Just goes to show
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Hello.

Troubleshooting a problem is never a waste of our time. Finding a solution is our goal. I try to do so in the simplest terms possible.

We are now at the stage of doing as oldfred advises. A full CHange Root and (RE-)install of grub in that environment.

I have posted that procedure in another thread:
[http://ubuntuforums.org/showthread.php?t=2230969&page=2&p=13059170#post13059170](http://ubuntuforums.org/showthread.php?t=2230969&page=2&p=13059170#post13059170)
My post#13 in that other thread, rather than repeating, please use it as the guide.

I am thinking that your ubuntu install is the same as in that other thread - ubuntu installed onto that 1st hard drive (sda) and the operating system at large is on the 1st partition ( hd0 in grub speak). Else adjust to the partition that "/" is installed to. Any doubts and we will clarify, one way or another.

Just goes to show[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


The problem is I have no terminal. I only have a black screen with a flashing (-) dash thingy.  Just says grub rescue>  _     the dash is flashing. I will try and do as you say.

---

### Post by sewbiz on 2014-06-26
It does not recognize sudo......UNKNOWN COMMAND.

---

### Post by Bashing-om on 2014-06-26
sewbiz; Hey,

Excuse me for not being clear.

Work from the liveDVD to do the CHange Root and install grub "dpkg-reconfigure grub-pc".

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Hey,

Excuse me for not being clear.

Work from the liveDVD to do the CHange Root and install grub "dpkg-reconfigure grub-pc".
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


Do you mean my live DVD that has Ubuntu 11.04 on it? Or the Live DVD that my computer does not seem to find. It does not read it. I must not have done it right. Seems I have to backtrack.....which live DVD? From the USB? From an actual disc drive?  : (  Dumb everything down for me...can you see I only have less than 100 beans.  : (

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Hey,

Excuse me for not being clear.

Work from the liveDVD to do the CHange Root and install grub "dpkg-reconfigure grub-pc".[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


I am typing to you from a laptop that has windows. Ubuntu is not installed on this computer although I seem to have downloaded the file but don't know how to now install the Ubuntu 14.04 to the computer. I am clueless about most things Ubuntu. Do I make the changes and installs by putting a live DVD into my broken computer that is in grub rescue mode or are we formatting or changing something on the live DVD first in my computer with windows? I am so lost as frustration does that to me!

---

### Post by sewbiz on 2014-06-26
I found this quote from someone who had the same problem I was  having....found this on askUbuntu.com......CAN I DO THIS? Can someone  show me how to enable Boot from USB in BIOS?

Quote:
[Thank you very much for your  thorough assistance.  Though I initially  couldn't get any of your  suggestions to boot of a USB either, I, by a  complete guess, found out  how I could:  I had Boot from USB enabled in  BIOS and placed above the  hard drive in the boot order, but when I  DISABLED booting form the hard  drive, all became peaches.  Thanks  again!                 –                      [user165793]("http://askubuntu.com/users/165793/user165793")                 [Aug 2 '13 at 0:50]("http://askubuntu.com/questions/327323/grub-rescue-limbo-with-a-twist?rq=1#comment416854_327547")                                                                                                  ] end Quote

---

### Post by Bashing-om on 2014-06-26
sewbiz; Hello,

1st we do need a liveDVD or USB of 14.04. Release 14.04 is the target, right, to get installed ? - We must have the same version/release DVD as what is installed or is to be installed in order to install grub from that liveDVD.
a) you may download that .iso file from the 11.04 liveCD and make up the 14.04 liveDVD/USB.
b) you may use the Windows machine to download and burn the image: 
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

------------------
As to advising you how to reset the boot order in your bios, I can not advise. Each and every bios is different, even to differences in versions from the same manufacturer. My post #28 refers, is that not the manual for the bios screen as you see it when you boot up and press the key to access the bios setup utility ? There is a screen from that set up utility to control the booting process - to set what the machine boots up.
-------------
So the 1st step here is to get you knowing how to boot the DVD.
Check and see if the link provided matches your bios. And I will try and muddle through getting you able to boot the DVD.

Once you can boot up the liveDVD, then we can go back to work.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-26
> **Bashing-om said:**
> sewbiz; Hello,

1st we do need a liveDVD or USB of 14.04. Release 14.04 is the target, right, to get installed ? - We must have the same version/release DVD as what is installed or is to be installed in order to install grub from that liveDVD.
a) you may download that .iso file from the 11.04 liveCD and make up the 14.04 liveDVD/USB.
b) you may use the Windows machine to download and burn the image: 
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

------------------
As to advising you how to reset the boot order in your bios, I can not advise. Each and every bios is different, even to differences in versions from the same manufacturer. My post #28 refers, is that not the manual for the bios screen as you see it when you boot up and press the key to access the bios setup utility ? There is a screen from that set up utility to control the booting process - to set what the machine boots up.
-------------
So the 1st step here is to get you knowing how to boot the DVD.
Check and see if the link provided matches your bios. And I will try and muddle through getting you able to boot the DVD.

Once you can boot up the liveDVD, then we can go back to work.
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


OK...the 11.04 version was initially installed when I first started using my computer....I have updated since to 12.04 so do I need to download/upload a 12.04 version to disc and then find the files I need from "it"? Instead of the 11.04?

---

### Post by Bashing-om on 2014-06-26
sewbiz; Wheal .. Short answer;

If there is a good install of 12.04 on the hard disk, and it is 12.04 that we want to repair grub. Then, Yes, we want a 12.04 liveDVD/USB from which to obtain the required files.

[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-26
I burned my downloads to disc. Not sure I even did that right though because when I put the burned disc in the drive and see the files....I only see an adobe acrobat doc icon by the name of the download. Gee whiz.....are you tired of me yet? Same thing on the USB......no folders or file names to see only the large document. DUMB. Where do I go to download the LIVE PROGRAM so I can put it to disc or usb?  Baby steps....I am not totally illiterate when it comes to all things with the computer but I don't seem to be able to get the basics right to even get me started on a fix! Will check in tomorrow....going to rest on this. Need sleep. Thank you for your patience with me and help on this.

---

### Post by Bashing-om on 2014-06-26
sewbiz; Hey !

Not a problem at all with baby steps, once upon a time I also knew nothing.
Download the iso image from:
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)
I suggest as you do not know your hardware and it is Intel based that you choose " ubuntu-12.04.4-dvd-i386.iso" from the list: from your webrowser. It will by default ( unless it has been changed) download that .iso to the Downloads directory in your /home.
ok you have the .iso file now you need to verify that it has not been corrupted in that transfer process ( or no one else has messed with that .iso !)
That is where the md5sum come in:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
OK, the .iso is verified so next is to burn it to disk as an image - NOT as a "data" file as we are going to make it a bootable disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
IF you are going to burn in Windows use this guide:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

OK, now you have a liveDVD, next is to make sure the burn is good,:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

To verify that the burn is good, you must reset in bios to boot from the CD, follow the guide and at the boot options screen in the liveDVD choose " check disk for defects".

Now That we have a known good liveDVD, we can go to work.

[INDENT][INDENT]1st step done
[INDENT][INDENT][INDENT]next when ready is to look and see what we are working with, in the terminal of the liveDVD
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-27
> **Bashing-om said:**
> sewbiz; Hey !

Not a problem at all with baby steps, once upon a time I also knew nothing.
Download the iso image from:
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)
I suggest as you do not know your hardware and it is Intel based that you choose " ubuntu-12.04.4-dvd-i386.iso" from the list: from your webrowser. It will by default ( unless it has been changed) download that .iso to the Downloads directory in your /home.
ok you have the .iso file now you need to verify that it has not been corrupted in that transfer process ( or no one else has messed with that .iso !)
That is where the md5sum come in:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
OK, the .iso is verified so next is to burn it to disk as an image - NOT as a "data" file as we are going to make it a bootable disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
IF you are going to burn in Windows use this guide:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

OK, now you have a liveDVD, next is to make sure the burn is good,:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

To verify that the burn is good, you must reset in bios to boot from the CD, follow the guide and at the boot options screen in the liveDVD choose " check disk for defects".

Now That we have a known good liveDVD, we can go to work.[INDENT][INDENT]1st step done[INDENT][INDENT][INDENT]next when ready is to look and see what we are working with, in the terminal of the liveDVD
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

#26 comment shows this:

Manufacturer.... Intel     Bios (F2)  
I have the box the motherboard came in......Intel Desktop  Board....DG41TX Classic Series....for the Intel Core 2 Quad   and Intel  Core 2 Duo Processors.

My son made my machine to be compatible with Microsoft Windows should I  ever want to use my program. I do have my Compaq (old laptop) Live  Operating System CD for Windows XP.                 

You gave me a link to a page with many options to download....do I do the first link? Do I download to computer and put on USB or DVD or both. Can I erase the one I already burned to or buy a brand new one? I am in kindergarden at this point. I have done this step several times already but not successful.

Is this the one on the list (it is EASY to make a mistake)
that I download?      [64-bit Mac (AMD64) desktop CD]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04.4-desktop-amd64+mac.iso")    ?   Or this choice from the list further down on the page:   [URL="http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04.4-dvd-amd64.iso"]ubuntu-12.04.4-dvd-amd64.iso


[/URL]

---

### Post by sewbiz on 2014-06-27
> **Bashing-om said:**
> sewbiz; Hey !

Not a problem at all with baby steps, once upon a time I also knew nothing.
Download the iso image from:
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)
I suggest as you do not know your hardware and it is Intel based that you choose " ubuntu-12.04.4-dvd-i386.iso" from the list: from your webrowser. It will by default ( unless it has been changed) download that .iso to the Downloads directory in your /home.
ok you have the .iso file now you need to verify that it has not been corrupted in that transfer process ( or no one else has messed with that .iso !)
That is where the md5sum come in:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
OK, the .iso is verified so next is to burn it to disk as an image - NOT as a "data" file as we are going to make it a bootable disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
IF you are going to burn in Windows use this guide:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

OK, now you have a liveDVD, next is to make sure the burn is good,:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

To verify that the burn is good, you must reset in bios to boot from the CD, follow the guide and at the boot options screen in the liveDVD choose " check disk for defects".

Now That we have a known good liveDVD, we can go to work.[INDENT][INDENT]1st step done[INDENT][INDENT][INDENT]next when ready is to look and see what we are working with, in the terminal of the liveDVD
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Or is this the file:   ubuntu 12.04.4-dvd-amd-64.iso     (this is the one I am downloading now and will burn to Live DVD)

---

### Post by oldfred on 2014-06-27
Intel motherboards seem to have a BIOS that requires a boot flag on a primary partition. That is really a Windows requirement as grub does not use a boot flag to find the rest of grub to boot with.

So make sure you have a boot flag on one and only one of sda1 thru  sda4. It does not have to be your Linux boot partition.

---

### Post by sewbiz on 2014-06-27
> **oldfred said:**
> Intel motherboards seem to have a BIOS that requires a boot flag on a primary partition. That is really a Windows requirement as grub does not use a boot flag to find the rest of grub to boot with.

So make sure you have a boot flag on one and only one of sda1 thru  sda4. It does not have to be your Linux boot partition.

I do appreciate all your help oldfred, but what you just told me is GREEK to me. I did not understand one word of it or what I am to do next or how to do what I need to find it. Boot flag....clueless. So...does this mean my system may be unbootable? The black screen does not understand any of the commands other than ls.

I can't seem to even be able to do a download correctly. Does my Windows OS need to have Office to do this. I have a basic system....Windows 8.1 that I am using to find solutions.

---

### Post by oldfred on 2014-06-27
You do not need office as that is just applications for word processing or spreadsheet. LibreOffice in Ubuntu is almost the same thing from a functional standpoint. 

If you get install working an get error from BIOS that you cannot boot then boot flag is an issue. If you want to understand a little about how computers boot, just look at pictures in this. Article is more complex but explains it in detail. Discusses Vista but applies to all BIOS/MBR systems, but Windows uses a Partition boot sector where grub does not.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

But none of that should be related to your download an install issues. Many have posted that various flash drives or different installer software work better. So you sometimes have to experiment.


If you have downloaded this, it should be fine if you have 2GB or more of RAM and decent video card or chip.

12.04.4-dvd-amd-64.iso

---

### Post by sewbiz on 2014-06-27
> **oldfred said:**
> You do not need office as that is just applications for word processing or spreadsheet. LibreOffice in Ubuntu is almost the same thing from a functional standpoint. 

If you get install working an get error from BIOS that you cannot boot then boot flag is an issue. If you want to understand a little about how computers boot, just look at pictures in this. Article is more complex but explains it in detail. Discusses Vista but applies to all BIOS/MBR systems, but Windows uses a Partition boot sector where grub does not.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

But none of that should be related to your download an install issues. Many have posted that various flash drives or different installer software work better. So you sometimes have to experiment.


If you have downloaded this, it should be fine if you have 2GB or more of RAM and decent video card or chip.

 12.04.4-dvd-amd-64.iso

I have an Intel (R) HD Graphics Family, DAC type: Internal,  Adapter String: Intel (R) HD Graphics 4400, Intel Video BIOS
               Driver Version 10.18.10.3412     on the computer I am downloading to. I  do have enough space on the DVD I want to BURN to or my USB.
Maybe it will be something as simple as a double click that I am not doing....or choosing the wrong .iso.
I am amazed you have not given up on me oldfred.

---

### Post by sewbiz on 2014-06-27
Should I download to Windows Media Player? Or just save the file....then find it in my download folder...etc. I saved it to the folder before...then from the folder I clicked on it and clicked....send to the drive....should maybe I have "copied" it to the drive. Maybe it is a SIMPLE thing like that which I am doing wrong. : (    I cried last night so won't waste tears today.

---

### Post by oldfred on 2014-06-27
You cannot copy or send to drive, you have to install it using one of the installer apps that both extracts the files in the ISO and converts drive or DVD to a bootable device. Just copying it does not make it bootable.

Follow instructions for ISO, unetbootin, pendrive, or rufus which all are installers. Links to each posted above.

---

### Post by sewbiz on 2014-06-27
I have Windows 8.1.....when I do the download from the website it puts it in a folder that calls it an Adobe Acrobat Document and not even to my download folder. I am not going anywhere if I can't even get this first step right. I click on the link on the website that has the Live Cd....it downloads....taking about an hour or so...then I just get the Adobe thing. Maybe my settings are off for downloads. It never stays the .iso file although once I thought it did. I will try again.

---

### Post by sewbiz on 2014-06-27
1.6 GB is downloading and in the download folder as I see it downloading with the correct file extension .iso    Maybe I am worrying about trivial things. Maybe it does not matter that when it is finished it calls itself something else and is smaller too in size. Maybe not a complete download. I will let you know.

---

### Post by yancek on 2014-06-27
> 1.6 GB is downloading and in the download folder 

I'm not sure what you are downloading.  I thought it was Ubuntu 14.04.  When I go to their page, both the 32bit and 64bit versions show as 970MB,  When you get it downloaded, it should show as "ubuntu-14.04-desktop-i386.iso or "ubuntu-14.04-desktop-amd64.iso.  If you downloaded the latter, you must have 64bit capable hardware on the machine you want to install it to or it will fail.

What software do you use to burn a CD/DVD?  You need something like Nero or Imgburn, something that is capable of "burning and iso file as an image" and don't confuse image in this sense with image in the sense of a picture or photo.  It means a "bootable image".  You can use software with this option to burn the iso to a DVD, selecting probably from the Tools tab to "burn as an image".  If you don't have that option with your burning software, don't bother it won't work.  

You can also use the windows software universal usb installer (also referred to as pendrivelinux) which only works on windows.  You can also use unetbootin which has Linux, windows and mac versions.  You can use either to create a bootable flash drive.  Instructions are simple and are on their respective pages.  If you use either, understand that any data on the flash drive before you use them will be TOTALLY overwritten.  If you use a DVD, use a blank one.

Once you have your medium, put it in the computer you want to install to.  Set it to boot from DVD or usb, whatever the case is and save the changes in the BIOS and boot.  You should get the option to try or to install so make your choice.

You might take your Ubuntu 11.04 CD and put it in a jewel case and then put that in your bookcase where you store collectibles.  It is unsupported and outdated and is not really secure to use.

You might review the following tutorial on installing Ubuntu 14.04.  It is pretty detailed and also gives some background information on preparation prior to install.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Good luck.

---

### Post by sewbiz on 2014-06-27
I am looking for the links to the installers. I do not see it. ok...I am preparing to install Unebutin and they ask what distribution....UBUNTU.....12.04....then not sure...a lot of choices...NetInstall....Net Install_x64....HD Media....HD Media_x64.....Live Install....Live_x64.   If I were to guess I would say Live_x64 only because I am wanting to burn a Live DVD and my processor has an x64 in it.  Not sure...I could take another week of research and find the answer but appreciate any help more than you know!

---

### Post by oldfred on 2014-06-27
If you select the top part it downloads again (Distribution). But you have already downloaded it:

You want to select the bottom as shown (DiskImage) and find the correct path where the ISO was saved and choose that ISO. Then you should select your flash drive.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sewbiz on 2014-06-27
OK....that was not the linked page I used...I just did a Google search for unebootin....never saw that page...will try again. Thank you very much. BRB.....

I was here and clicked the download:

[http://sourceforge.net/projects/unetbootin/?source=dlp](http://sourceforge.net/projects/unetbootin/?source=dlp)

We will see what happens....So do I download for Windows since I am using a Windows OS? See how easily confused I can get.
Still a beginner.

---

### Post by sewbiz on 2014-06-30
I am stuck on the first step....download ....I download it and it goes into my download folder on C: drive yet it is not 1.6GB (downloading Ubuntu-12.04.4-dvd=amd64.iso to Windows 8.1 OS). It becomes an Acrobat Reader document but the Adobe Reader could not open it. Not supported file type. Can I get some help with this...truly appreciative...will do search on internet to find the answer in the manual.  LOL!

---

### Post by sewbiz on 2014-06-30
Summary: NO SOLUTION YET!  I have a Ubuntu 12.04.4 Desktop that is in Grub Resuce mode. It does not recognize any commands I type other than 'ls'. I am trying to download an .iso file ( Ubuntu-12.04.4-dve-amd64.iso ) and upload to disc or usb that is bootable. The download should be 1.6GB but when the download is complete it is much smaller (even thought the download takes over an hour). I want to burn it to a DVD on a windows 8.1 laptop while keeping it bootable for my Linux OS. Can anyone help me find a solution as to why my Windows 8.1 can't read my .iso file? Thank you in advance.

---

### Post by sewbiz on 2014-06-30
UNetbootin gave me the answer I was looking for earlier about "Distributions" to choose ...gee whiz...take the time to study. I am off to buy a new USB that I can format so it will be bootable...don't want to erase all my backed up files, which formatting will do. So I will format my USB...then I think let UNetbootin do most of the rest. I did get the .iso file downloaded as 1.6GB...still the Acrobat Adobe thing confuses me. I don't see any folders or anything.WEIRD! Afraid it will just be one big TEXT file. See you in a couple days.

---

### Post by oldfred on 2014-06-30
Windows likes to hide extensions, because it knows better. 
But if you have somewhere changed the default for .iso to be an Acrobat file and not an install image then that could be the issue.
Somewhere is a setting to turn on the showing of extensions. I always did that in XP but do not know how with the newer Windows.

---

### Post by sewbiz on 2014-07-03
I purchased a new USB (8GB) so will I burn the image to it or a DVD-RW (4.7GB) that I also now have on hand? 
Went to my download folder and found the .iso file but it tells me it is 1,716,960KB....not 1.6GB. Is that the same size?
Also...when I go to the UNetBootin program it asks me to enter the distribution. Do I select Ubuntu......then 12.04_Live or....Ubuntu....12.04_Live_x64?
I have Ubuntu 12.04 on the desktop computer that is in Grub Rescue mode that I want to boot and make all the fixes to missing files I deleted.

---

### Post by yancek on 2014-07-03
> Went to my download folder and found the .iso file but it tells me it is 1,716,960KB....not 1.6GB. Is that the same size?

I wouldn't worry about that as the sizes are rounded off, the 1.5GB.

> Also...when I go to the UNetBootin program it asks me to enter the  distribution. Do I select Ubuntu......then 12.04_Live  or....Ubuntu....12.04_Live_x64?

The select distribution item at the top of the unetbootin window is if you want to download it.  Since you have previously indicated that you have already downloaded the Ubuntu iso file, you need to navigate to your /home/user/Downloads directory if that is where you have it.  To do that, click on the tab with three dots [  ...  ] in the center.  It is to the right of the entry box which is to the right of ISO in the lower right of the window.  The Type tab should show USB and the drive/partition should be showing in the tab  to the right of Drive.  If it is not showing, close unetbootin, insert the flash drive and open unetbootin again.  You should not have any other usb drives attached to save possible confusion.  When you have this set, click OK to begin.

---

### Post by sammiev on 2014-07-03
> **sewbiz said:**
> I purchased a new USB (8GB) so will I burn the image to it or a DVD-RW (4.7GB) that I also now have on hand? 
Went to my download folder and found the .iso file but it tells me it is 1,716,960KB....not 1.6GB. Is that the same size?
Also...when I go to the UNetBootin program it asks me to enter the distribution. Do I select Ubuntu......then 12.04_Live or....Ubuntu....12.04_Live_x64?
I have Ubuntu 12.04 on the desktop computer that is in Grub Rescue mode that I want to boot and make all the fixes to missing files I deleted.

I usually check out the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") after a download.

---

### Post by sewbiz on 2014-07-04
THANK YOU yancek for your instructions. Very helpful. Sammiev, I  appreciate your input too. I need everything dumbed down though. Still a  newbie at this. Oldfred you have spent a lot of time working with me  and appreciate too your loyalty! : )

The download (upload...install?) to my E drive was a success using UNetBootin. Next step is now to check out the MD5SUM.
OK...I read the manual about MD5SUM....however....they keep saying "CD"  ....check to make sure the "CD" is not corrupt...etc. Was I suppose to use
a Live DVD rather than a USB drive to transfer the file onto? Before I move on, can someone tell me if this makes a difference.

Also....I am using a laptop Windows OS so how do I check the MD5SUM using Windows....maybe that info is further down on the page I was reading.
I will research further.

---

### Post by sewbiz on 2014-07-04
Yes...further down on the page....HOW TO with WINDOWS...BRB.

---

### Post by sewbiz on 2014-07-04
I installed the MD5SUM for Windows...entered all the info (my .iso file/ the corresponding hash from UbuntuHashes) compared and all is good. Still have the question though about DVD verses USB. Does it matter that the file says "DVD"? (Ubuntu-12.04.4-dvd-amd64). I am annalytical so look at all the "details" of a thing and need to know the "WHY" for everything.
Maybe this is the reason this is taking me so long to understand and go through each step. Thank you for all the help I have been getting so far. My question is should I have had the file on the DVD...maybe that is the next step. Maybe we will now be burning it to the DVD. ??????

---

### Post by yancek on 2014-07-04
It should not make any difference that it says DVD in the iso filename as long as your flash drive is large enough to hold the DVD iso contents.  It should be because the DVD iso is less than 2GB.  What unetbootin does is to put a "Live CD" or "Live DVD" on a flash drive and make it bootable.  Live CD/DVD's can be used as an operating system to try the system out and most also have an installer which can then be used to install that particular operating system.

Putting an iso file of a Linux operating system on a CD or DVD is usually a little easier and has been used much longer than putting it on a flash drive.

---

### Post by sewbiz on 2014-07-05
I am going to try to burn this to a DVD as well. I am first compressing the file to a zipped folder....then I extract it and send it to the DVD? Or do I need a program installed to do this for me? Seems I never get this right. Is there a difference between copying a file to a DVD or burning one to it...or sending one to it? This is where I am stumped. I will do some more research.

---

### Post by sewbiz on 2014-07-05
Not finding anywhere to "burn" my file to DVD in Windows 8.1.....any help out there? When I double click on the file in explorer from the download folder I get a message that reads:

"Acrobat Reader could not open 'ubuntu-12.04.4-dvd-amd64.iso' because it does not support file type or because file is damaged (example sent via email and file not properly decoded). File was not sent email but from website (see messages above with link)". I am frustrated but have not given up hope. Will check in tomorrow. Please dumb down any info you can give me as I am not that bright when it comes to all this tech stuff. Thank you in advance....also, if using the USB with the file instead, can I just plug it into the port on the "broken...GRUB RESCUE MODE" machine and see if it will boot? I am just thinking that it may not be able to read the port itself so this is why I am trying to burn to the DVD.

RECAP:  My goal is to be able to reboot my Desktop which has files missing in GRUB (that I mistakenly and stupidly deleted) so I can reinstall these. It has Ubuntu-12.04.4LTS on it currently. The .iso file is the same distribution and version. It has the same MD5SUM config. 

Again...any help appreciated.  : (

---

### Post by yancek on 2014-07-05
> I am going to try to burn this to a DVD as well. I am first compressing  the file to a zipped folder....then I extract it and send it to the DVD?  

I can't image that would work at all.

> Not finding anywhere to "burn" my file to DVD in Windows 8.1

Had the same problem with windows 7.  I don't know if there is any software with a default windows install to do the job.  You download a program called Imgburn, once that is downloaded you can open it and check the options on the tabs in its window and find an option to "burn as image".  That is what you need to do.  If you can't get any software to "burn the iso as an image", it won't boot.

You need to use something like unetbootin or pendrivelinus to put the iso of Ubuntu on the flash drive or it will not be bootable also.  You need to have the flash in the port when you boot the computer.  You need to change the boot priority in the BIOS to set the flash drive to boot first.  The methods for doing this vary with computer manufacturers.  If it fails in one usb port try another.  I have an Acer notebook which will boot a flash drive but only the first port so you need to check that if it fails.

---

### Post by sewbiz on 2014-07-05
> **yancek said:**
> 

You need to use something like unetbootin or pendrivelinus to put the iso of Ubuntu on the flash drive or it will not be bootable also.  You need to have the flash in the port when you boot the computer.  You need to change the boot priority in the BIOS to set the flash drive to boot first.  The methods for doing this vary with computer manufacturers.  If it fails in one usb port try another.  I have an Acer notebook which will boot a flash drive but only the first port so you need to check that if it fails.

OK....I have UNetBootin installed on my Windows laptop. I also do have the .iso file on my flash drive which I did from UNetBootin. I just thought the DVD was to be the simpler way of doing things. I will check to see if the flash drive will boot it. OK....tried all 7 ports...none work to boot my computer with the USB in it (this has the Ubuntu-12.4.4 .iso file on it).

---

### Post by sewbiz on 2014-07-05
I will try to change the boot priority in BIOS on my USB...maybe that is the trouble...skipped that step. My USB still won't boot my computer (desktop). Off to do more research...but another day. TIRED.....zzzzz this is pretty taxing.
Wish I were smarter. Thank you for the help so far everyone. In the meantime I am downloading boot-repair-disk....I am desperate here! I will use UNetBootin then to move the download to my USB drive....the same one that I used for the .iso file. There is room on it (6GB approx more space).

---

### Post by yancek on 2014-07-05
>  I will use UNetBootin then to move the download to my USB drive....the  same one that I used for the .iso file. There is room on it (6GB approx  more space). 		

If you have anything on the usb you want to save, move it as unetbootin installing a system to a flash drive will overwrite it.  That is mentioned on their web site.  You don't need the iso file on the flash drive, just use unetbootin to take the iso file and put it on the flash and make it bootable.  I explained this process in an earlier post.

---

### Post by sewbiz on 2014-07-07
> **yancek said:**
> If you have anything on the usb you want to save, move it as unetbootin installing a system to a flash drive will overwrite it.  That is mentioned on their web site.  You don't need the iso file on the flash drive, just use unetbootin to take the iso file and put it on the flash and make it bootable.  I explained this process in an earlier post.

Thank you yancek. I did use UNetBootin to move the file to my flashdrive. I am now talking about adding Boot Repair to the same flashdrive....using UNetBootin as the tool to do this. Will my .iso file then be overwritten? The USB...with the .iso file did not work to boot my computer. I tried 7 ports. I thought maybe I should just install Boot Repair instead.

---

### Post by sewbiz on 2014-07-07
When I select the distribution on UNetBootin.....I have several extensions to choose from for my version (12.04)....Live, Live_64, HD Media, HD Media_64, Net Install, NetInstall_64.
How do I know which one to choose. Research on this topic isn't clear. Can someone answer this part for me? I need step by step instructions. This process is slow for me because once I get to a certain step, there are options I have to choose and I don't understand which one is the correct one or why. Confusing.

---

### Post by sewbiz on 2014-07-07
Here is where I am at..(I am a grandma and can only work on this when baby is sleeping)...please don't assume I know much of anything. I need everything carefully explained to me but I am doing my own research too in between people responding. I am "reading the manual" so to speak. I have begun the process of burning the boot repair disc to my USB (New one with no other information on it...64GB). I used
UNetBootin to do this....I selected distribution=Ubuntu....version=12.04_Live.....all went well but then it asks me...."Installation complete, reboot (current)...after rebooting, select the USB boot option in the BIOS boot menu. Reboot now."

I have many questions:
REBOOT what? Do I keep the USB in the port that it is in on the computer currently working? Is that what it means by '(current)'? This is what I did...I left the USB in and "rebooted now" as they said to.....now I am looking for WHERE THE BIOS BOOT MENU is on Windows 8.1. Or....do I put the USB in the port leading to my "broken" machine (Ubuntu 12.04 installed but missing files in grub....Desktop)? Please help....I keep getting stuck because directions are never explicit but I am wondering if the authors assume we are all more advanced Linux users. I am sure you are sick of me by now. : (

---

### Post by waterlubber on 2014-07-07
when you boot the computer, it shows a screen with your motherboard's logo on it, and usually text describing various keys, like
F12 for boot menu. Sometimse, to use the F# keys, you may need to hit FN+F# or SHIFT+F# or a combination of the two.

---

### Post by sewbiz on 2014-07-08
> **waterlubber said:**
> when you boot the computer, it shows a screen with your motherboard's logo on it, and usually text describing various keys, like
F12 for boot menu. Sometimes, to use the F# keys, you may need to hit FN+F# or SHIFT+F# or a combination of the two.

When I do shift+F10 (which is my boot menu) I get a screen that says "enter password"....I don't know what it is and have tried several simple passwords I may have used.
: (   Password check failed...went to product guide at support.intel.com with no help. Is my case hopeless?

---

### Post by yancek on 2014-07-08
>  I am now talking about adding Boot Repair to the same  flashdrive....using UNetBootin as the tool to do this. Will my .iso file  then be overwritten?

Yes, it absolutely will and you will no longer have the Ubuntu you created with unetbootin on that flash drive!

> When I select the distribution on UNetBootin.

There is no need to do that.  That is only necessary if you do not have any version of Ubuntu.  You have indicated that you already have a downloaded Ubuntu iso on your computer.  To access that, I explained in detail how in post #72 above.  


> REBOOT what? Do I keep the USB in the port that it is in on the computer currently working? 

You can reboot the windows 8 computer to test the usb you created but since you want to use it on the other machine, take the usb out and put it in your other machine and boot it.  When you see the first screen, you should see an option at the bottom of the screen indicating which key you need to repeatedly tap to enter setup.  Common keys are F2, F10 but there are others and it should show but only for a few seconds.  If you are able to access your BIOS, you should see a Boot tab at the top.  Use the arrow key on your keyboard to highlight it and look for Boor Priority and highlight it with the keyboard keys and look for options.

---

### Post by sewbiz on 2014-07-09
> **yancek said:**
> Yes, it absolutely will and you will no longer have the Ubuntu you created with unetbootin on that flash drive!



There is no need to do that.  That is only necessary if you do not have any version of Ubuntu.  You have indicated that you already have a downloaded Ubuntu iso on your computer.  To access that, I explained in detail how in post #72 above.  




You can reboot the windows 8 computer to test the usb you created but since you want to use it on the other machine, take the usb out and put it in your other machine and boot it.  When you see the first screen, you should see an option at the bottom of the screen indicating which key you need to repeatedly tap to enter setup.  Common keys are F2, F10 but there are others and it should show but only for a few seconds.  If you are able to access your BIOS, you should see a Boot tab at the top.  Use the arrow key on your keyboard to highlight it and look for Boor Priority and highlight it with the keyboard keys and look for options.

Thank Yancek...but my GRUB is broken...missing files that I stupidly deleted. Too many posts here now...maybe I should start over...I seem to be repeating myself. I can't get past the Boot Priority page...I highlight....click enter and they ask for a password....I never get to the "options" after that. I did the arrow thing. I didn't download .iso on my "broken" computer....only from the website and installed to my USB using UNetBootin.

What should I do admin of this forum? Start a new thread?

RECAP: (In case someone is just joining this conversation and wants to help.)

My desktop computer has Ubuntu-12.04 LTS installed on it. (I am using windows 8.1 laptop to help find a fix) My boot disc volume was full...needed to delete some old kernals. Stupidly...I went into my grub folder as I was having success with this and thought I would delete more things. I saw folders with music notes on them (.mod files) thinking they were some music downloads I did unknowingly and started "deleting" them as well. YIKES...then my screen went BLACK and had the words "GRUB RESCUE _" on it. This is now all I get. It does not recognize any commands I type in other than 'ls'. Everything comes up..."unknown file", "bad file name","unknown command", error messages continually. It can't seem to read my USB if I put it into any port with a new .iso file to boot it in it.  I am learning that I have to change the BIOS so it boots the USB first. Can't seem to be able to do that because it needs a password when I get to a certain point. 

Is this a lost cause. I am very new at Ubuntu/Linux so talk plainly to me and really dumb it all down. I am doing my own research so can read a manual but there are so many extra details I come across before I need to ask yet another question. Thank you for your help.

---

### Post by oldfred on 2014-07-09
Boot-Repair does have an Advanced option to totally uninstall grub and reinstall it. That may be the best choice to try now?

But you have to be able to correctly make a bootable live installer version of Ubuntu or make the Boot-Repair liveCD version with unetbootin, pendrivelinux or rufus using your Windows.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2014-07-09
From your last post, it seems you have a BIOS password.  If that is the case and you don't know it I'm not sure how that could be changed although it should be possible.  Usually when you select the Boot tab there will be an option to set the priority to CD/DVD/USB/HD etc.  The method for selecting them or moving them up/down in priority varies with manufacturer.  You should see the name of the manufacturer of the computer (HP, Dell, Toshiba, etc) or the motherboard when booting.

The only commands that will work at the prompt you see are Grub commands which are much more limited than the commands you have access to when fully booted to the system.

If you deleted just the .mod files from your grub directory, all those files are in the /usr/lib/grub/i386-pc directory and could be copied from there.  If you deleted other files that could be an additional problem.

If you are unable to change the boot priority, you might consider starting a new thread to deal with that as your first priority as this one is getting a little cumbersome and not many people are going to go back and read over 90 posts

---

### Post by sewbiz on 2014-07-09
> **yancek said:**
> From your last post, it seems you have a BIOS password.  If that is the case and you don't know it I'm not sure how that could be changed although it should be possible.  Usually when you select the Boot tab there will be an option to set the priority to CD/DVD/USB/HD etc.  The method for selecting them or moving them up/down in priority varies with manufacturer.  You should see the name of the manufacturer of the computer (HP, Dell, Toshiba, etc) or the motherboard when booting.

The only commands that will work at the prompt you see are Grub commands which are much more limited than the commands you have access to when fully booted to the system.

If you deleted just the .mod files from your grub directory, all those files are in the /usr/lib/grub/i386-pc directory and could be copied from there.  If you deleted other files that could be an additional problem.

If you are unable to change the boot priority, you might consider starting a new thread to deal with that as your first priority as this one is getting a little cumbersome and not many people are going to go back and read over 90 posts  

Thank you yancek...I will look what you have written here over more closely this weekend, decide what to do... and maybe start a new post.

---

