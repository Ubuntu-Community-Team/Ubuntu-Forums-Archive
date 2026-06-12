---
title: "Cannot Install Ubuntu On Acer Aspire One"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by &lt;(*v*)&gt;itsAPenguin on 2008-07-10
Recently (by recently i mean today) i purchased a brand new Acer Aspire One netbook:). I tried installing ubuntu hardy heron 8.04 using both an external CD Drive (with the ubuntu install disk of course) and from a bootable USB key and both times i run into the same problem:mad:: It starts off normally, gets to the ubuntu loading screen (the one with te ubuntu logo and the bar moving back and forth) and then it stops all of a sudden and the following comes up:

udevd-event[1411]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

(initramfs)

with a blinking cursor. I can type commands that seem to work fine.

CAN SOMEONE PLEASE HELP!?

---

### Post by rabidphage on 2008-07-11
Hi, try the alternate install CD.

---

### Post by &lt;(*v*)&gt;itsAPenguin on 2008-07-11
I tryed the alternate install but i ran into new problems: the aspire one does not have a cd-rom so i had to use a USB key and the 3rd installation step fails: it can't detect a cd-rom drive (cause it doesn't have one!).

And I cannot skip this step casue then it can't load the debconf preconfiguration file (it tries to load it from file:///cdrom/preseed/ubuntu.seed) and it also won't be able to load the installer components from the CD.

I am trying to get my hands on a external cd-rom drive to see if this solves the problem but in the meantime do you have any ideas?

---

### Post by Pumalite on 2008-07-11
If you have an OS installed; try unetbootin:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by b3n3 on 2008-07-12
check out this:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
it worked fine!

---

### Post by &lt;(*v*)&gt;itsAPenguin on 2008-07-12
> **b3n3 said:**
> check out this:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
it worked fine!
I tried following those instrcutions and it didn't work!!! :(
it gave me the same message as before: udevd-event[1408]: run_program: '/sbin/modprobe' abnormal exit

and Pumalite, no I don't have another OS installed :S.

Anyways i guess i'll try and get my hands on a external CD-ROM drive and try the alternate cd again :)

---

### Post by monino on 2008-07-13
> **<(*v*)>itsAPenguin said:**
> I tried following those instrcutions and it didn't work!!! :(
it gave me the same message as before: udevd-event[1408]: run_program: '/sbin/modprobe' abnormal exit

and Pumalite, no I don't have another OS installed :S.

Anyways i guess i'll try and get my hands on a external CD-ROM drive and try the alternate cd again :)

Hi i have the same problem with Medion Akoya mini.
I try:
-ubuntu
-ubuntu alternate
-ubuntu minimal cd
-kubuntu
-xubuntu

and i have the same problem!!! when i try with alternate the install menu dont leave me because stop at detecting cd roms... i try to install with pendrive, in other pcs run ok but in this laptop no. :(
sorry for my english

---

### Post by monino on 2008-07-13
i try with xubuntu and run ok, why run and ubuntu not run?

---

### Post by &lt;(*v*)&gt;itsAPenguin on 2008-07-13
So it worked ok when you used xubuntu?
alright i'll give it a try

---

### Post by tiltus on 2008-07-13
I installed Heron on my Aspire One today, using unetbootin.

Create the Live USB through unetbootin on your main computer, I just opened it up in windows. On your netbook press f12 when it is booting, and put "USB HDD" to the top of your boot list. Restart your netbook with your usb plugged in, and it should boot off your USB, it'll have an option on your desktop to install, and that takes forever.

The really hard part is trying to get the wifi card working.
That said, does anybody know what Atheros chipset is in the aspire one?

---

### Post by issih on 2008-07-13
if you can get xubuntu installed you could always do that, then simply install the package ubuntu-desktop from there. You could even remove the xubuntu packages if you wanted...Rather a roundabout solution, but it is a possibility.

Hope that helps

---

### Post by Tux Aubrey on 2008-07-13
Try the 32 bit 8.04.1 build of Ubuntu (or Xubuntu).  I think the later kernel has built-in support for the Atom processor that is lacking in the earlier builds.

For WIFI, the chip is a new Atheros (AR5007) that works with the LATEST madwifi drivers - not the version shipped with Ubuntu.

Follow this guide to compiling them - 

[http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html](http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html)

Don't forget to disable the drivers that the Hardware Drivers wizard thing uses by default before you start.

Once you get the drivers working, you can add them to /etc/modules to make them load at boot time.  Do it manually (sudo nano /etc/modules) or just

```
$ sudo echo ath_pci >> /etc/modules
```

You will have to repeat the make-install process whenever there is a kernel update so keep the tar ball (unless they get built-in, which is promised "soon")

---

### Post by Tux Aubrey on 2008-07-13
Another thing you may want to do with a newly installed X/ubuntu on the Acer Aspire One is to edit your fstab (sudo nano /etc/fstab) and comment (#) out the line for /dev/sdb1 which begins /media/cdrom0......

Otherwise you may have problems with USB devices that are not CDROMs.

USB devices automounted fine for me after editing that line.  Before that I was getting errors about wrong filesystems and bad blocks.

This issue does not affect booting from a USB device (which you can select during boot with F12.

Also, watch out for NumLock!  It is on by default and you will have fun trying to enter a password if you are not used to it (Fn+F11 turns it off).

Have fun - I'm loving mine!

---

### Post by tiltus on 2008-07-15
[QUOTE=Tux Aubrey;5380552For WIFI, the chip is a new Atheros (AR5007) that works with the LATEST madwifi drivers - not the version shipped with Ubuntu.[/QUOTE]

I found that the chipset did not work with the lastest MAdwifi drivers, rather their latest special drivers in snapshot:
[http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

---

### Post by Tux Aubrey on 2008-07-15
> **tiltus said:**
> I found that the chipset did not work with the lastest MAdwifi drivers, rather their latest special drivers in snapshot:
[http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

You are right.  I just followed Bruno Abinader's How-To and got those drivers.

---

### Post by 2fast4u288 on 2008-07-15
I have successfully gotten Ubuntu 8.04 Hardy running on my new acer aspire one in only 2 days after receiving it from my boss to experiment with Linux on it. I have also gotten the wireless to work. I was able to get hardy on it by first installing 7.10 gutsy gibbons and using the distro upgrade. Yes, I know that that's not the best way to go about things, but it works. The way i got the wireless to work is with nDiswrapper. I first got the windows drivers from [HTML]http://www.liliputing.com/2008/07/windows-drivers-for-acer-aspire-one.html[/HTML] then using ndiswrapper the way you always do. BTW, sry this post is so long, but its 3:30 in the morning and im typing this on my aspire one, which for some reason makes me babble on about nothing, sry bout that too. Anyways, if what i said helps anyone out, well...i guess i helped u out...:) :lolflag: This is also my first post on this site, so please dont bash me too much :lolflag: and do u guys think its weird to be a Linux "semi-expert" at the age of 15? (im not calling myself an expert-expert because just cuz i know more about linux than anyone i know, dosn't mean i know more than most of the ppl who help the people out on this site)...OMG...STFU ME!!...sry guys...really sry...im gonna finish now...bye...

---

### Post by kunixos on 2008-07-15
itsapenguin: have you tried modifying your boot parameters to disable some of the card managers (noapci, etc.)? that was a problem for me with my Acer Aspire 9410Z with a couple other distros. Not with Ubuntu, but I'm not sure how the Aspire One works similarly/differently.

Hope this helps!

---

### Post by 2fast4u288 on 2008-07-15
I also 4got to ask u guys where u got your aspire ones from...cuz i got mine from my bosses spetial contact who got a surprise shipment of them b4 the actual stated release day..so...ya..any responce would be appretiated....im totally gone now..lol

---

### Post by dandesigns on 2008-07-15
thanks for the instructions. :) it worked.

---

### Post by dcwckd on 2008-07-15
Installed with unetbootin and live 8.04.  Wifi is great, thanks. 

Reduced swappiness and changed fstab to tmpfs (cause were using SSD).

Any idea how to get it to suspend when I close the lid?

Thanks

---

### Post by baseline on 2008-07-17
Big bump!

I hope someone from Canonical are keeping an eye on this thread...
There are literally thousands of users struggling to get Ubuntu to work on the Aspire one. Linpus lite is soooo bad  :\
As anyone been able to solve the mic problem and the suspend one?
Any help would be greatly appreciated.

tkx

---

### Post by mattylight on 2008-07-17
[http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164]("http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164")

Try that link to the aspire one user forum, this guy says all his stuff works properly. I haven't done it myself, my aspire one hasn't arrived yet, but I plan on using this when I go to do it. I'm a total noob, but I hope this helps. 
Matt

---

### Post by dandesigns on 2008-07-18
still, the mic is not working after all the steps on that link though. 

here are my problems using ubuntu on aspire one:
1. wifi led not working even if the wifi works
2. mic not working
3. the SD expansion slot would only be treated as an SD card reader and not as a real expansion to the SSD's like on linpus.(minor issue)
4. boot time is around 40 secs
5. touchpad don't work properly, eg. horzontal and vertical scrolling and double-tap drag


if any of the issues i listed are incorrect please let me now. i could have done something wrong in the process.

also, if anyone could help me make the linpus connect to windows network as flawless as ubuntu, please message me. thanks.

---

### Post by baseline on 2008-07-18
> **mattylight said:**
> [http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164]("http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164")

Try that link to the aspire one user forum, this guy says all his stuff works properly. I haven't done it myself, my aspire one hasn't arrived yet, but I plan on using this when I go to do it. I'm a total noob, but I hope this helps. 
Matt

Hi Matt,

Thanks for the info, I'm actually also posting on that thread.
Let's hope that between all of us we can reach a point where Ubuntu works just as well as on a regular computer.

cheers

---

### Post by WanderingStar on 2008-07-19
> **dandesigns said:**
> still, the mic is not working after all the steps on that link though. 

here are my problems using ubuntu on aspire one:
1. wifi led not working even if the wifi works
2. mic not working
3. the SD expansion slot would only be treated as an SD card reader and not as a real expansion to the SSD's like on linpus.(minor issue)
4. boot time is around 40 secs
5. touchpad don't work properly, eg. horzontal and vertical scrolling and double-tap drag


if any of the issues i listed are incorrect please let me now. i could have done something wrong in the process.

also, if anyone could help me make the linpus connect to windows network as flawless as ubuntu, please message me. thanks.

Indeed, those are some issues, I started that thread, so thanks for the heads up on some issues.  

1. Correct, does not work - I never even noticed.
2. Also not working.
3. I expect this is something custom from Linpus, and not a hardware feature I belive.  I doubt it will ever function.
4. Correct
5. My touchpad is functional, including scrolling out of the box.  I've never tried the double-tap drag.

All in all, its not too bad to get it working.  The no sound after resume is the killer for me. 

Jeff

---

### Post by dandesigns on 2008-07-19
I would really want to have ubuntu on the aspire one as i do have even bigger issues with linpus lite (samba, available apps, limited bash, and annoying screen saver). I actually had the netbook remix installed right after i bought the notebook but then reverted back and just wait for the next release.

I'm very much happy with how debs work (i have hardy on my desktop), and too sad for red hats. no offense to red hat users but if only Acer and other laptop makers would open their drivers, ubuntu could get the upper hand on the umpc market.

---

### Post by ted616 on 2008-07-19
> **dandesigns said:**
> still, the mic is not working after all the steps on that link though. 

here are my problems using ubuntu on aspire one:
1. wifi led not working even if the wifi works
2. mic not working
3. the SD expansion slot would only be treated as an SD card reader and not as a real expansion to the SSD's like on linpus.(minor issue)
4. boot time is around 40 secs
5. touchpad don't work properly, eg. horzontal and vertical scrolling and double-tap drag


if any of the issues i listed are incorrect please let me now. i could have done something wrong in the process.

also, if anyone could help me make the linpus connect to windows network as flawless as ubuntu, please message me. thanks.

I got same problems on my ubuntu-aspireone. Anyone can solve mic-not-working problem? Thank you.

---

### Post by baseline on 2008-07-21
The guys at puppy linux are also keeping an eye on this one:
[http://www.murga-linux.com/puppy/viewtopic.php?search_id=507643914&t=31298]("http://www.murga-linux.com/puppy/viewtopic.php?search_id=507643914&t=31298")

Now that would be a really fast boot up process  :)

cheers

---

### Post by leo_ietres on 2008-07-23
I read in a forum from germany, that teh UBUNTU 8.04 version does not boot, and you have to try booting from the 8.04.1 new release (remember that 8.04 is a LTS version of ubuntu, and the 8.04.1 release has solvented many bugs from previous version)

I still not try this solution on my aspire one... hope this works !!!

---

### Post by Tux Aubrey on 2008-07-23
> **leo_ietres said:**
> I read in a forum from germany, that teh UBUNTU 8.04 version does not boot, and you have to try booting from the 8.04.1 new release (remember that 8.04 is a LTS version of ubuntu, and the 8.04.1 release has solvented many bugs from previous version)

I still not try this solution on my aspire one... hope this works !!!

That was true for me.  8.04.1 has the 2.6.26 kernel and therefore support for the Atom processor.

---

### Post by doomslagen on 2008-07-23
Have similar problem...please visit my thread and help me with my problem...

---

### Post by ind on 2008-07-26
I followed this guide and Ubuntu works Perfectly with my Aspire One
[http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&p=1233#p1233](http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&p=1233#p1233)

<3 ubuntu!


PS - I don't really know how to use linux, so you can rest assured the guide is easy to follow.

---

### Post by gnuisnotunix on 2008-07-28
these drivers work:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3816-20080724.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3816-20080724.tar.gz)

are the card readers working for all of you? I inserted a SD Card in both readers and none of them got automatically mounted.. do  I have to mount them manually? in case I have to, does anyone knows which devices (/dev/) the readers use?

---

### Post by mtonnies on 2008-07-28
Is anyone else having problem with the trackpad not working. I have no functionality, what so ever. Any help would be greatly appreciated. Is there possible a wrapper for the windows driver, or an actual linux driver for the trackpad. I have looked around but can't seem to find anything. Thanks in advance.


Acer Aspire One - 8G SDD, 512 RAM

---

### Post by gnuisnotunix on 2008-07-28
the touchpad works for me... and I just realized that the card reader works after rebooting.

---

### Post by zzats on 2008-07-29
> **gnuisnotunix said:**
> 
are the card readers working for all of you? I inserted a SD Card in both readers and none of them got automatically mounted.. do  I have to mount them manually? in case I have to, does anyone knows which devices (/dev/) the readers use?

the SD-card reader is a JMicron reader, and assigns devics starting from /dev/mmcblk0, first partition being /dev/mmcblk0p1.

The card reader works straight away after fresh install, although I haven't tried booting the machine without the card inserted.

---

### Post by gnuisnotunix on 2008-07-30
Thanks for the info... the problem with the SD cards seem to be a known one in Ubuntu since Feisty... there's a bug report about a similar problem with other laptops...

---

### Post by Thomas8675309 on 2008-07-31
The more-or-less official instructions for installing Ubuntu on the Acer Aspire One can be found [[FONT="Arial Black"][SIZE="2"]here[/SIZE][/FONT]]("https://help.ubuntu.com/community/AspireOne").

---

### Post by geraldbrandt on 2008-08-20
I just installed Ubuntu (Kubuntu, actually), and the wireless doesn't show up when I do an lspci.  Any ideas?

---

### Post by kamereon on 2008-08-21
I've had some trouble with the mousepad, too. 
Until i installed and ran 'gsynaptics'. It let's you set and unset all the touchpad parameters you need.

I followed [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne") to get the wireless working.

Strange: the left card reader will automount, the right one only works, if the card is inserted before boot.

---

### Post by GnarusLeo on 2008-08-25
This happens to me as well. The left card reader automounts just fine, but the right one needs to be booted with to work.

This is a huge issue for me, as I am going to have a 16g SD card permanently in the left to use as a "HDD", and the right one to use as a "disk station". Please enlightn us with some sollution to this :popcorn:

---

### Post by MadEgg on 2008-09-22
> **mtonnies said:**
> Is anyone else having problem with the trackpad not working. I have no functionality, what so ever. Any help would be greatly appreciated. Is there possible a wrapper for the windows driver, or an actual linux driver for the trackpad. I have looked around but can't seem to find anything. Thanks in advance.


Acer Aspire One - 8G SDD, 512 RAM

Yep, here the touchpad doesn't work either. It did on the install USB stick but after reboot it doesn't. I tried installing gsynaptics and changing xorg configuration to include shmconfig but it doesnt help.

This is on an Acer Aspire One 150B, 120 GB HDD, 512 MB RAM. I'm using an USB mouse now but that's not a real solution.

---

### Post by stephan0h on 2008-09-22
A minor thing here: i've tried to set up a bigger virtual display (xorg.conf: virtual 1024 1024). Unfortunately this does not work. Has anybody got this running?

Despite this everything is working fine out of the box (xubuntu, 8.04.1) - except sound, cardreader and wifi, which i had no time setting up and testing yet.

reg,
stephan

---

### Post by kamereon on 2008-09-23
stupid question, maybe, but did you run gsynaptics and set the sensitivity to a higher level, MadEgg?

---

### Post by MadEgg on 2008-09-23
Yup, I did.

The strange thing is that none of the device files in /dev/input responds to touching the touchpad or pressing the buttons. So apparently something is wrong at kernel/driver-level. 

Is there any way to install the kernel the install ISO is using, as the touchpad did work with the live USB-stick?

---

### Post by richardh9936 on 2008-09-24
The Acer Aspire One has the Atom chip like the eee-pc, doesn't it?  If so, then you MUST look at [http://www.ubuntu-eee.com/]("http://www.ubuntu-eee.com/") because they have re-compiled it for that chip.  I've used their procedures on an eee-pc, and it worked wonderfully.  8.04.1 installs the easiest.

Please look at ubuntu-eee.

---

### Post by MadEgg on 2008-09-24
The chip is not the problem, it works fine, except for the mouse.

I have actually not installed ubuntu but onelinux, Ubuntu for AAOs. The wiki suggested to use this kernel, specifically optimized for the AAOs but that doesn't activate the touchpad either... This is the kernel found at [http://www.splra.org/oneLinux/](http://www.splra.org/oneLinux/)

It works, boots much faster than the normal kernel, but no touchpad...

---

### Post by MadEgg on 2008-09-26
> **MadEgg said:**
> 
Is there any way to install the kernel the install ISO is using, as the touchpad did work with the live USB-stick?

Anyone?

---

### Post by thinkpadx60 on 2008-09-26
Last Night I downloaded Ubuntu 8.10.1 alpha 6 and used Unetbootin to create a Bootable Flash drive. I installed it on My Aspire one then hooked up a network cable to the unit and did ALL the Updates (Over 300 MB worth) after finishing all the Updates I unpluged the network cable and rebooted..  WiFi Works Great , Touchpad works Great , Screen resolution Looks great.. I will try the Mike & Camera This evening (Those are VERY Low on My priority list). Tonight I'm going to install a 60 GB Toshiba PATA Drive to replace the Solid state HDD & Reinstall 8.10.1..

---

### Post by MadEgg on 2008-09-28
Right, I have found the cause of the problem with the touchpad.

It seems that I pressed Fn+F7 which apparently disables the touchpad. Pressing it again fixed it. Yippee.

---

### Post by siblog on 2008-10-09
Has anyone tried to install the 8.10 beta on the AA1 yet? I am looking try it out tonight and thought I would check to see if anyone has had any luck. Also another question....Do you recommend using the regular live desktop ISO or the alternate ISO when creating the USB via UNetbootin?

---

### Post by Jitz0722 on 2008-10-10
Check Out ubuntu Documentation

install 8.10 Beta or
eeebuntu 8.04.1 ==> with upgrade to 8.10 ( Netbook Remix )

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by kaffeboy on 2008-11-28
I recently purchased my Aspire One (still waiting for the mailman). However, I see that this thread is rather old and I wanted to know what things are supported out of the box in Ubuntu 8.10?

Specifically Wifi & Webcam...

I´m also thinking of doing a hardware mod...isntalling a 20GB 1.8¨ PATA drive to replace the puny and delicate SSD.

---

### Post by anon4321 on 2008-11-28
I've noticed (also on other forums) people not being able to boot or install Ubuntu ( 8.4 and 8.10 ) on Acer Aspire ( M3640 ). The live CD boot will hang at [ initializing bluetooth ]. A workaround is booting Ubuntu (F6) with acpi=off. To permanently fix this issue is to go in the PC's BIOS (hold del key during boot), then goto [Advanced BIOS Features], then goto [Installer OS Select], then change the value from AUTO to OTHERS. Then Save and exit Setup. Ubuntu will now boot with full ACPI support.

---

### Post by sefs on 2008-12-29
I just bought one of these baby's (aspire one) with windows xp home pre-installed,  They don't seem to come with Linux installed.  It will be fun to test these tips to get Ubunutu on there.  Hopefully it will not be too much hair pulling.

---

### Post by Buce on 2010-01-10
Has anyone had any success installing Ubuntu minimal? That's the version I use, and I can't get it to install off the alternate CD.

---

