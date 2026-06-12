---
title: "Can somebody PLEASE help me with Ubuntu Installation?"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by nemesis93 on 2008-06-12
I have been trying to install Ubuntu Hardy Heron onto my computer for a week now. I have tryed from searching google.com, asking questions in yahoo! ask, to now here the Ubuntu Forums. Nothing has worked for me ,i ultimatly came here to see if i can FINALLY solve this problem.

Ok into the root of my problem everytime i try to run the installer on bootup i select the option to install Ubuntu and then Ubuntu loads for around 15-20 seconds after that it stays on almost the third bar of loading. So I leave my computer alone after knowing it will not do anything and now everytime i leave it for around 10 minutes it says:
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
init: Unable to execute "/bin/sh" for rc-default: No such file 
init: rc-default main process (7486) terminated with status 255

I do not know what to do anymore i really REALLY need help.
I've been trying and trying for a whole week now.

Please and Thanks to anyone who helps me!

---

### Post by wootah on 2008-06-12
> **nemesis93 said:**
> I have been trying to install Ubuntu Hardy Heron onto my computer for a week now. I have tryed from searching google.com, asking questions in yahoo! ask, to now here the Ubuntu Forums. Nothing has worked for me ,i ultimatly came here to see if i can FINALLY solve this problem.

Ok into the root of my problem everytime i try to run the installer on bootup i select the option to install Ubuntu and then Ubuntu loads for around 15-20 seconds after that it stays on almost the third bar of loading. So I leave my computer alone after knowing it will not do anything and now everytime i leave it for around 10 minutes it says:
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
init: Unable to execute "/bin/sh" for rc-default: No such file 
init: rc-default main process (7486) terminated with status 255

I do not know what to do anymore i really REALLY need help.
I've been trying and trying for a whole week now.

Please and Thanks to anyone who helps me!
When you downloaded the ISO, did you check the md5 sum of the file?

Try checking the cd for problems (one of the options on the menu). Also, perhaps run the memtest86 for an hour or so and see if anything comes up.

Let us know if that helps :)

---

### Post by Vivaldi Gloria on 2008-06-12
Yeah, it looks like a corrupt cd.

---

### Post by nemesis93 on 2008-06-12
Ok so i ran the Disk Check and when it was all done it said no errors were detected on my CD.
After that i ran the Memory test and i did not get any errors on that either

Oh and by the way how do I check the md5 sum of the .iso image file?

---

### Post by wootah on 2008-06-12
> **nemesis93 said:**
> Ok so i ran the Disk Check and when it was all done it said no errors were detected on my CD.
After that i ran the Memory test and i did not get any errors on that either

Oh and by the way how do I check the md5 sum of the .iso image file?

Hopefully you still have the ISO available for the cd. Try this program [http://md5-checker.tsoft.qarchive.org/](http://md5-checker.tsoft.qarchive.org/) and then load the ISO and compare the md5 sum to the list [here ]("http://releases.ubuntu.com/8.04/MD5SUMS")for there iso that you downloaded. If you are having a lazy day, here is the list:

```

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

```

---

### Post by abn91c on 2008-06-12
check th cd itself for scratches, fingerprints, that will give you that error also

---

### Post by wpshooter on 2008-06-12
Are you sure that you are downloading, burning and trying to install the correct (final release) version of Hardy and not the release candidate ?  Where are you going to download the ISO ?

Try  [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by nemesis93 on 2008-06-12
Alright so i ran the md5 check utility and it gave me this response:
The Codes Match!

So, so far there's nothing wrong with the CD itself.

What should i do :confused:

---

### Post by steppedup on 2008-06-12
I had some problems with Hardy Heron as well.  But we have to cut it some slack - it's still a very new release.

Do what I did - download the **alternate installation **of Ubuntu 7.10 (Gutsy Gibbon).  Not the full-on graphic install - the text only install.

The benefits of doing so is the Ubuntu 7.10 has been around much longer - therefore the open source community has been working on all of those drivers/ hardware issues you might be banging your head against with 8.04 - and solved for 7.10.

Make sure to check the checksum, then burn it at 1X speed.

Go have a beer and watch The Daily Show all the way through.

Come back and the CD should be burned.  Run the CD check.

If ok, you should be good to go.  

[Here's a link to an A to Z I wrote for the Dell Inspiron 1100]("http://ubuntuforums.org/showthread.php?t=822192") - but you can just look at the installation part (definitely skip the BIOS part!).  Added bonus - you'll end up with box that will look like a Mac OS X.

---

### Post by vivekrocks on 2008-06-13
Can u briefly describe the architecture of your sys?
Have u tried any of earlier ubuntu distributions like gutsy-7.10?
I think knowing the architecture I might be able to help you!

---

### Post by nemesis93 on 2008-06-13
Ok so i am currently downloading Ubuntu 7.10 alternate CD x86. The download is pretty slow at 180-220 kb/sec (around 90 minutes). But ill wait. about my PC

System Specs:
Intel Pentium 4 3.20 Ghz HT
1 GB DDR PC3200 RAM
ATI Radeon X1550 PCI (not PCI-Express)
Internal 200 GB HDD
External 250 GB HDD
My exact PC (really old): [http://h10025.www1.hp.com/ewfrf/wc/product?product=443070&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=443070&lc=en&cc=us&dlc=en&lang=en&cc=us)

There is specific information including my bios and everything.

Note: I have not updated the firmware of my bios nor my CD, DVD, and hard drive.

---

### Post by nemesis93 on 2008-06-13
Ok so now that i have finally finished downloading 7.10 alternate install. I have to burn this to a CD at 4x speed? How do i do that because the only program i have for burning iso files is Sonic RecordNow!This program comes MS XP and has no options for the speed to burn it on.

---

### Post by avtolle on 2008-06-13
Go here and download infrarecorder, a free (as in beer) utility you can use, which does have options for speed, etc.
[http://infrarecorder.sourceforge.net/?page_id=5](http://infrarecorder.sourceforge.net/?page_id=5)

---

### Post by nemesis93 on 2008-06-13
Alright so im in this part of the 7.10 alternate Ubuntu install:

-------------------------| [!!] Partition disks--------------------

The minimum size you can use is 75.6 GB or 30% and the maximum size is 247.7 GB.

Hint: Use "20%" (or "30%", etc.) for 20% (resp. 30%, etc.) of the available free space for this partition. Use "max" as a shortcut for the maximum allowed size.

New partion size:

___________________________________________________________________

[INDENT]<Go Back>[/INDENT]                                      <Continue>

I thought that Ubuntu only used around 10 GB not 75 GB? 

Note: That the partioner is pointing to my Seagate 250 GB External HDD


I need an answer ASAP cause I'm staying on this step of the installation guide until i get some advice?

Thanks!

---

### Post by nemesis93 on 2008-06-13
Can i please get some help im still on the hard disk partion step in the Ubuntu 7.10 alternate install CD.

I need help ASAP! Please!

Thank You.

---

### Post by avtolle on 2008-06-13
Tell it how much to use. It will use, if you tell it to do so, all the available space on the drive. BTW, I'd allocate 15 Gb for the Ubuntu installation (at a minimum), but that's just me.

---

### Post by snowpine on 2008-06-13
> **nemesis93 said:**
> Alright so im in this part of the 7.10 alternate Ubuntu install:

-------------------------| [!!] Partition disks--------------------

The minimum size you can use is 75.6 GB or 30% and the maximum size is 247.7 GB.

Hint: Use "20%" (or "30%", etc.) for 20% (resp. 30%, etc.) of the available free space for this partition. Use "max" as a shortcut for the maximum allowed size.

New partion size:

___________________________________________________________________

[INDENT]<Go Back>[/INDENT]                                      <Continue>

I thought that Ubuntu only used around 10 GB not 75 GB? 

Note: That the partioner is pointing to my Seagate 250 GB External HDD


I need an answer ASAP cause I'm staying on this step of the installation guide until i get some advice?

Thanks!

Hi, it sounds like there is already 75.6 GB of data on that hard disk, so that is the smallest the partition can be. Two questions though before you go any further:

1. Do you really want to install Ubuntu on your *external* hard drive? 

2. Are you trying to set up a dual boot with another operating system (Windows, Mac, another Linux) and keep your existing data, or are you trying to wipe the computer clean and do a fresh Ubuntu install?

---

### Post by nemesis93 on 2008-06-13
Yes i really do want to install Ubuntu on my external as i do not have enough free space on my internal hard disk only have about 15% free space. Most of the files i have in their are important so i wouldnt delete many of them.

So do you think i should type in 25 GB for the section that asks me New Partition size?
> 
New Partition Size:

_25 GB?_______________________________________________

<Go Back>                                               <Continue>

---

### Post by shailendra on 2008-06-13
Are you able to run Ubuntu from the live CD you have made? There might be the problem with the CD or the ISO may not be matching with your system architecture. So if Ubuntu is running from the live CD then there should be no problem with the CD.

---

### Post by snowpine on 2008-06-13
> **nemesis93 said:**
> Yes i really do want to install Ubuntu on my external as i do not have enough free space on my internal hard disk only have about 15% free space. Most of the files i have in their are important so i wouldnt delete many of them.

So do you think i should type in 25 GB for the section that asks me New Partition size?

Cool, just checking! :)
25 GB should be plenty of space. 

Is there any important data on the external hard drive that you need to back up before proceeding, just in case?

---

### Post by shailendra on 2008-06-13
You can refer to the "HOW TO" at the following link.
"http://ubuntuforums.org/showthread.php?t=822264"

It might be helpful for you to install Ubuntu on external hard drive.

---

### Post by nemesis93 on 2008-06-13
When i write in 25 GB it tells me too small size for partition??!

When i come back i think it recommends 161.7 GB because thats what comes up on the partition size line.

161.7 GB is just WAY to much!

---

### Post by wootah on 2008-06-13
> **nemesis93 said:**
> When i write in 25 GB it tells me too small size for partition??!

When i come back i think it recommends 161.7 GB because thats what comes up on the partition size line.

161.7 GB is just WAY to much!

It's never too much!!! :biggrin:

---

### Post by snowpine on 2008-06-13
> **nemesis93 said:**
> When i write in 25 GB it tells me too small size for partition??!

When i come back i think it recommends 161.7 GB because thats what comes up on the partition size line.

161.7 GB is just WAY to much!

I *think* it is asking you how much to shrink down the existing partition. Then in the next step, you can use however much space you freed up to create a new Ubuntu partition. 

Does that make sense? You already have 76GB of data on the external hard drive that you want to keep, yes?

---

### Post by nemesis93 on 2008-06-13
Alright so to my understanding i have to create a new partition manually.
So i will create a new partition on my external hard drive.
Now i have to backup all my data to create a new partition right?
Creating a new partition does include deleting all excisting dadt right?

---

### Post by nemesis93 on 2008-06-13
Alright so i just finished installing Ubuntu 7.10 using the alternate CD install. So it looked like everything went well so when the installation was completed to my EXTERNAL HDD it open the cd drive and told me to remove it and reboot so i did. As soon as it prompted me to pick which os to boot into:

Microsoft Windows XP Home Edition
Microsoft Windows Recovery Console
Ubuntu

I selected Ubuntu and i just got a blank (black) screen with a blinking cursor (underscore= _).

So then i just tryed out going to the bios and setting my computer to boot up from my first drive which i switched to my EXTERNAL and then i rebooted...

After that i got a black screen saying EXACTLY:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

_     (blinking underscore)

What should i do now?

---

### Post by nemesis93 on 2008-06-13
> **nemesis93 said:**
> Alright so i just finished installing Ubuntu 7.10 using the alternate CD install. So it looked like everything went well so when the installation was completed to my EXTERNAL HDD it open the cd drive and told me to remove it and reboot so i did. As soon as it prompted me to pick which os to boot into:

Microsoft Windows XP Home Edition
Microsoft Windows Recovery Console
Ubuntu

I selected Ubuntu and i just got a blank (black) screen with a blinking cursor (underscore= _).

So then i just tryed out going to the bios and setting my computer to boot up from my first drive which i switched to my EXTERNAL and then i rebooted...

After that i got a black screen saying EXACTLY:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

_     (blinking underscore)

What should i do now?


No responses?!? Please help me i think i am finally about to boot into Ubuntu after 1.5 weeks of pulling my hair!

---

### Post by shailendra on 2008-06-16
Error 17 means GRUB is not found. 

Try the following steps:

1) Return to the boot menu of Ubuntu and press "E" button to edit the command line. 

2) Change the "root(hdX,Y)" command and try to boot Ubuntu. Change the value of "X" and "Y". Start with "0". Note down the command which worked for you.

In my case the original command was "root(hd0,1)", which gave me Error 17. But the command "root(hd0,0)" worked for me.

3) Now you have to update the "menu.lst" file to make this change permanent, otherwise you will have to change it every time you boot.

4) First take backup of the "menu.lst" file. On the terminal type the command;
"sudo cp /boot/grub/menu.lst /boot/grub/menu_copy.lst"

5) Now update the "menu.lst" file. On the terminal type the command;
"gksudo gedit /boot/grub/menu.lst

The menu.list file will be opened. 

6) Go to the section for "Ubuntu" and update the root command which worked for you and save the file.

In my case, I had to replace "root(hd0,1)" with "root(hd0,0)" at three places in the menu.lst file.

Note: Make sure that you do not update any other section.

7) Reboot your PC. You should now be able to run ubuntu.

Refer: [http://ubuntuforums.org/showthread.php?t=822264](http://ubuntuforums.org/showthread.php?t=822264)

---

### Post by Somekindofsuperhacker? on 2008-10-23
Does it still tell you "Too small size" if, on the Guided partitioning, you click and drag the area between the Windows partition and the proposed Ubuntu area, and give Windows a bit more size?

I was getting that error because by default the Guided partitioner wanted to make Windows have 0% free disk space.  I had to give it some free space and then it worked.

---

