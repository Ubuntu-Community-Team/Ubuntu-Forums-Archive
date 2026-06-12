---
title: "Get Me Started - Desktop &amp; Nautilus"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by OceanBitz on 2011-05-21
Have Ubuntu booting from an external HD attached via USB.  The basic tutorial is awesome but could use a push to get moving a bit quicker. I am comfortable with the DOS Dir and Windows Explorer and prefer finding files and running programs that way.  Do you think I can fine Nautilus, no<g>.  My new desktop shows an Example folder (icon) which I found did permit me to view files, but this seems like a peculiar route and the other icon is to Install Ubuntu.  That I do not understand either because it appear installed<g>.  Appreciate somebody explaining these two icons on the my new desktop and explaining how to find/activate Nautilus.
Ed

---

### Post by Bucky Ball on 2011-05-21
Nautilus is a window manager. Is that what you are after? If you have an 'install Ubuntu' icon on your desktop you are running from the CD or you are running a Wubi install inside Windows. 

When you boot your computer, do you get a list of the operating systems on you machine that you can choose from (this should include a Ubuntu entry, under that the Ubuntu recovery entry, and after that any other OSs you have installed)?

---

### Post by OceanBitz on 2011-05-21
I am booting directly from the external HD which in my CMOS has has been specified to be first in the boot sequence - so no, there are no choices.  On that HD only one OS resides, Ubuntu, and on completion of the boot sequence the Ubuntu desktop that I described displays. So I am questioning the content of that desktop and how to get to Nautilus which to me in fundamental to getting around in an OS.

---

### Post by Hedgehog1 on 2011-05-22
This is Nautilus:

[IMG]http://imageshack.us/m/546/5255/screenshotnatu.png[/IMG]

For your purposes, it is to Ubuntu what 'Windows Explorer' is to Windows.


***The Hedge***

:KS

---

### Post by OceanBitz on 2011-05-22
That is what I want.  I suspect I am not "full" installed. Remember I created a bootlable external drive which then plugged into a USB port gets all input from that MRB and drive.  The initial screen which drops through quickly unless I hold with space bar is an Installer boot menu with the first choice and obvious default mentioned "Run Ubundu from this USB"  The second choice is Install Ubuntu on my HD" and then several more such as T"Test Memory" and "Advanced Options"  Letting it fall through I get a desktop that has two icons, Examples and Install Ubuntu 11.04.  Under a top menu choice of System | Administration there is an option to Install Ubuntu 11.04 with a note "Install this system permanently to your hard drive"

I suspect I have not completed the installation on my external USB connected drive an am looking at some sort of a temporary installation.  I would really appreciate some newbee help here.  I am a Windows programmer, not too dumb, but this is not making me look good<g>.

---

### Post by Hedgehog1 on 2011-05-22
> **OceanBitz said:**
> **I suspect I have not completed the installation on my external USB connected drive** an am looking at some sort of a temporary installation.  I would really appreciate some newbee help here.  I am a Windows programmer, not too dumb, but this is not making me look good<g>.

Based on the what you have described, I agree that you do not have appeared to have installed Ubuntu yet. However, there are a few other possibilities:

If the USB drive and USB port are both USB 3.0, at this time Ubuntu will not boot from a USB 3.0 port with a 3.0 device.  You will need to move the drive to a 2.0 port.

If you are running USB 3.0, it may have indeed installed onto the drive, but you will not be able to boot from it until you move the drive to a USB 2.0 port.

If that is not the issue, then please do this so we can guide you on the installation to the external USB drive:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by OceanBitz on 2011-05-22
Hedge, mine are USB 2.0 - but clearly I am booting from the external drive.  There is no boot problem.  The question is what have I booted into.  I have described the initial which is obviously a Ubunto setup screen which then drops through automatically to displaying a Ubunto desktop.  It is that desktop that I need to understand and the peculiar options for installing Ubunto.  Am I in some form of a demo?

Ed

---

### Post by Hedgehog1 on 2011-05-22
> **OceanBitz said:**
> Hedge, mine are USB 2.0 - but clearly I am booting from the external drive.  There is no boot problem.  The question is what have I booted into.  I have described the initial which is obviously a Ubunto setup screen which then drops through automatically to displaying a Ubunto desktop.  It is that desktop that I need to understand and the peculiar options for installing Ubunto.  Am I in some form of a demo?

Ed

We call the 'Demo' the LiveCD/LiveUSB.  It allows you to try Ubuntu, install Ubuntu and also fix a damaged system.

If you are seeing this:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

and/or this:

[IMG]http://img202.imageshack.us/img202/5771/small07trygui.png[/IMG]

That is the LiveCD/LiveUSB image you are running from.

But the only way I can tell you more is if you run the boot info script.

***The Hedge***

:KS

---

### Post by OceanBitz on 2011-05-22
Hedge, we are now speaking the same language - that is exactly the screen I see.  Now that runs directly off my external from which my BIOS/CMOS has been configured to try first.  So that "live CD/liveUSB really is not an installed copy, yet it boots, I think, first displaying an Installer Boot Menu as I indicated - not just a program I ran from Windows.  Now if I elect to install can I place the installation right back on the external - I sure do not want to wipe out my Windows 7 on my internal hard drive just yet.  I am very interested but not yet a convert<g>.    

Ed

---

### Post by Hedgehog1 on 2011-05-22
So, what you really want to do is boot off the LiveCD (not the external hard drive), make sure that your external is called '/dev/sdb' (typically your internal is '/dev/sda').

One you know your external drive, then  begin your Ubuntu install by using gparted and do this:

**[SIZE="3"]NOTE THAT ALL THESE PICTURES SHOW /dev/sda, BUT YOU EXTERNAL IS LIKELY /dev/sdb, SO CHANGE THE DEVICE ACCORDINGLY[/SIZE]**.

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-22
**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

**Now when you install, select this method:**

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

**And tell the install to use the three partitions this way (Your Drive is likely /dev/sdb, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

**[SIZE="3"]PLEASE INSTALL THE BOOT LOADER ON YOUR EXTERNAL DRIVE: /dev/sdb[/SIZE]**


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-22
This install method completely isolates UBuntu on the External drive.

To boot Ubuntu, you will need to use the BIOS boot selector and choose the USB drive, otherwise Windows will boot off the internal drive (which is OK).

***The Hedge***

:KS

---

### Post by OceanBitz on 2011-05-22
Hedge, you are going to fast for me, a programming and troubleshooting computers from DOS to Windows 7 .

I would answer your first statement  "So, what you really want to do is boot off the LiveCD (not the external  hard drive), make sure that your external is called '/dev/sdb'  (typically your internal is '/dev/sda')"  NO!  I want to boot off my external.  I do not want to mess with my present computer's hard drive, only install a copy of Ubuntu on an external hard dirve that when attached via USB will boot into the Ubunto OS.  Let's start there.  I really thought I was heading in that direction becuase I do have a bootable external but unfortunately it is what you describe as "Live"  or what I am starting to think is "Dead."   What I apparently need to do is convert that "Live" or demo to the real thing on my external.  If I click on that Ubuntu 10.10 on the desktop do your screen shots then illustrate how to convert this "Live" demo to the "real thing."

Ed

---

### Post by Hedgehog1 on 2011-05-22
OK - I gave you info overload.  I do that - sorry (I work with 200 nerds in R&D - it is a hard habit to break).

The idea is to not touch your internal hard drive in any way.

The install is to be only on your external hard drive, and completely separate from your internal hard drive.

Here is how Linux 'sees' hard drives:

/dev/sda  dev means 'device', sd means 'SCSI Device' (I know, your drives are not SCSI, but that is the name convention), and follow by the letters a,b,c,d and so on.

Your two drives are:
/dev/sda (your internal drive)
/dev/sdb (your external drive when it is connected to your PC).

On a hard drive, we have partitions.  The are numbered.

/dev/sdb1 is the first partition on the external drive.
/dev/sdb2 is the second partition on the external drive.

The intent here is to install Ubuntu on your external drive only, and not write anything Ubuntu to you internal hard drive.

Is this less nerdy?  I can never really tell.

***The Hedge***

p.s. My wife often says to me: "Me- Human. You- Nerd" when I geek out.

---

### Post by OceanBitz on 2011-05-22
You did good, backed off sufficiently.  The syntax is all new.  I am now comfortable with sda and sdb and of course I want to work on my external which is sdb which eventually will display sb1,2 and 3. Now your first note instructing the details of the install stated "Once you know your external drive, then  begin your Ubuntu install by using gparted and do this:"  Is this something I do from with the Live?  Is not the icon on my Live desktop have this purpose - it states "Install."  Again back to fundamentals,  if this install repartitions, I assume it wipes out the "Live" code that now resides on the external and just where did the new code come from?   

Ed
P.S.  I am pretty bad myself - have had a problem all my life at cocktail parties when I get off on one of my favorite computer topics or physical metallurgy (how I earned my food and supported my "normal" wife)   - everybody walks off.

---

### Post by Hedgehog1 on 2011-05-22
OH - you are the 'physical metallurgy' guy we try not to make eye contact with at parties?  Yes, I see...

If you used something like **unetbootin** [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") to convert the ISO into a LiveUSB, but used your whole external drive rather than a little USB stick, that would do have put the LiveCD image on the external USB drive.

You will find gparted (**G**nome **PART**ion **ED**itor) on the system administration menu of the LiveCD/LiveUSB.

It is a powerful tool - be sure you are only changing the external drive. :D

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-22
OH - one other thought to make the install goof-resistant.

If you are not on a laptop, you can pull the data cable of the windows drive (when powered off) so you ONLY have the external drive attached during install.

That makes it's hardest to mess up.

***The Hedge***

:KS

p.s. Ubuntu (well, all Linux distros) can be moved from PC to PC without much muss-and-fuss.  In many cases, you will only need to change video driver after the relocate.  I use the genieric driver on the 'Ubuntu On A Stick' (Natty on a 32 gig fast USB stick) and can boot any machine at home or at work from it.  That is a true pocket-PC.

---

### Post by OceanBitz on 2011-05-22
Like that suggestion - will pull the data cable, boot from my external, hit the install and see if I cannot follow your thorough directions.  

I am off to a grandchilds baseball game and will not be able to get back to this until tomorrow - will let you know of my success.  Appreciate your wasting you Sunday with me.

---

### Post by Hedgehog1 on 2011-05-22
Have fun at the Game! (**Time with grand kids is always well spent)**

***The Hedge***

:KS

---

### Post by OceanBitz on 2011-05-22
Hedge -- Did not stay for the balance of the bouble header - enough and it was cold.

So pulled the data cable from my internal SATA HD, pluged in my external to the USB and brought up the desktop for the "LiveCD/LiveUSB image" as you identify.  Double clicked on the "Install Ubuntu 10.10" icon.  A dialog box displayed to "Allocate drive space" but slightly different than your illustration.  Across the top was a grayed out button bar with Drives  Type Mount Point Format? Size....a empty box in the middle and another grayed out button bar at the buttom indicating New Partition Table  Add  etc....... A textbox at the bottom showd /dev/sda   - NOT sdb and no way to change.  So assuming maybe since my SATA or sda was unavailable, it decided to call my external sda. There was no way of changing or entering anything.  Hit Continue and of course with no entries absolutely nothing happened.   

I think when it comes to Ubuntu I am a loser and should be happy in my DOS and Windows world.  I saw two advantages of this project, a better backup than my 1.5 Seagate TB external, better because I could still get to it if my internal HD crashed. I also saw the opportunity to explore and learn first hand the value of Liux.  Actually I am backed-up up to the extreme with my primary computer backing up at night using DOS's XCOPY with a switch to only copy if an older date is found on my second computer, and weekly manual backups using a variety of batch files sending information to my Seagate External.  I also have several images of the C partition of both computers in various places.  Unless the house burns down I am fairly well protected.  Yes, most everything I know is on HD's, very little in my brain.

I do thank you for sticking with me but I think you took on to great a challenge.

Ed

---

### Post by Hedgehog1 on 2011-05-22
Fair Enough!

Dual booting is not for everyone.

Thanks for giving it a try.

Also - Remember you can use an Ubuntu LiveCD/LiveUSB to boot up and rescue data from a crashed Windows machine.  So that is an 'Ace' in your back pocket.


***The Hedge***

:KS

---

### Post by arpanaut on 2011-05-22
Let me venture a guess here,

Because you are operating the Ubuntu OS/live demo from the external drive and it is mounted and it is probably FAT 32: you cannot alter the external drive, to prepare it for a proper installation.

If you were to prepare a CD or USB stick with the iso and boot from that then you would be able to alter and prepare/partition the USB HDD for a proper installation.  Then what Hedgehog1 gave you with the illustrated instructions will work.

I don't think that you can be booted from and install to the same disk, especially if the partitioning scheme was not already ready for linux.

I may be wrong here but I think this is the issue that is preventing you from getting Ubuntu properly installed on your external.

---

### Post by linuxinstalledfromhdd on 2011-05-23
It would be better to turn that external drive into a NAS box and then install over your LAN network.

---

### Post by OceanBitz on 2011-05-23
Hedge - will definitely keep the "Ace" for awhile.  Have filed away all the good information you provided

arpanaut - sounds logical, had to wonder how I could repartition the drive where all my information as sitting - sounded a little like pulling up with your boot straps.  Will have to pick up a larger flash drive, only have a 1GB.
Hope you guys noted that my external was an old internal connected with a  $25 SATA/IDE to USB cable with an external power transformer built in.  There has to be a lot of trashed computers out there with good hard drives and there is some value security in having multiple HD's for backup and special projects over having every thing on a a single terabyte HD (which I have too<g>).

Ed

---

