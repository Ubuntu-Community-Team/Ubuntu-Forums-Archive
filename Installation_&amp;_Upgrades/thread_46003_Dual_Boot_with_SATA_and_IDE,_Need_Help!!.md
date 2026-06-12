---
title: "Dual Boot with SATA and IDE, Need Help!!"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by snapmando on 2005-07-02
This is what I wanna do....

Install Win XP on the SATA drive and install Ubuntu 64Bit on the IDE Drive.

Can someone give me instructions on how I could do this, Please!!

Are there any issue's with this distro and SATA drives?

I would like to accomplish this on a Dual-Boot.



I am a Noob, so Please speak NooBish!! O:)

---

### Post by mingus on 2005-07-03
[QUOTE=snapmando]
Install Win XP on the SATA drive and install Ubuntu 64Bit on the IDE Drive.

Can someone give me instructions on how I could do this, Please!!

Are there any issue's with this distro and SATA drives?

I would like to accomplish this on a Dual-Boot.
[/QUOTE]

1.  Set BIOS to boot from SATA
2.  Install XP on SATA
3.  Boot from Ubuntu install CD, follow directions and at partition menu, use "guided partitioning" on the IDE drive (hda) or use "manual" to control more closely how the partitions are done
4.  At the boot loader menu, do *NOT* take the default.  Instead instruct the installer to put grub on the Master Boot Record of the IDE drive (/dev/hda) - *NOT* on the SATA drive (sda)
5.  Ubuntu will finish phase one of install and ask you to reboot.  *Immediately*  enter BIOS setup and change sequence to boot from IDE drive.  Let Ubuntu finish installation.  If you do not yet have your network connection set up, be sure to tell installer to get packages from CD only
6.  In Ubuntu go to Applications/System Tools/Terminal.  You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
savedefault
chainloader        +1

and change it to this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
map                    (hd1,hd0)
map                    (hd0,hd1)
chainloader        +1

7.  save the file
8.  reboot and test boot into XP

---

### Post by dahabreh on 2006-05-18
but when i run the unbuntu installation with SATA and IDE HD connected the setup doesn't see the IDE drive!!! ](*,) 

help help help

---

### Post by Sasquatch2000 on 2006-07-07
I am interested in this as well. 

Can't there be an easier way?

---

### Post by stv453 on 2006-07-22
"enter BIOS setup and change sequence to boot from IDE drive"

is there a way to do it if the bios doesn't let you choose which hard disk to boot from (just 'cd/harddisk/floppy')... ?

---

### Post by Sasquatch2000 on 2006-08-15
Passing along some more info:
[Boot Ubuntu using NTLDR](http://www.ubuntuforums.org/showthread.php?t=236846)

---

### Post by thedivvyman on 2006-08-24
Hi - I found this post whilst enquiring about dual booting with 2 HDD's  SATA & IDE. Could I ask mingus (if you are still around) if I followed the instructions given,  what  would be seen on screen on a cold boot  after setting the pc up  this way.
Thanks
Brian

---

### Post by Moozacman on 2006-09-21
I followed this method of install as I too have a SATA as my main drive and then a IDE backup.  When I was installing Ubuntu though, I didn't get an option for where to put grub, it automatically went ...well I guess onto the SATA drive.  Now when I start my computer it will WinXP will automatically start up. I have to go into my boot menu to get grub to come up.  Anyone know how I can fix this?  If it wasn't for gaming, I would just ditch winbloze all together, but I need my RCT3!!!!!!

---

### Post by angdis-bb on 2006-09-24
I just did a dual boot install. My machine has windows XP on the sata drive, and I installed linux on an IDE drive.

I didn't know anything about this issue and just installed by "clicking through" using the desktop CD.

Immediately after install was complete, the machine rebooted into windows instead of grub, so I googled for answers and found this thread.

I looked at mingus' posting but remembered that I did not get any menu asking where to put grub. I so I skipped that and just went into the PC bios. All I had to do was to change the order of booting so that the IDE drive was before the SATA drive. 

Now everything works fine (boots into grub).

---

### Post by Sasquatch2000 on 2006-11-27
Still no definitive answers, it seems. I thought it would be easier to install Ubuntu than this. I don't want to botch or even touch my Windows XP Professional installation on the SATA drive, but would prefer a menu at startup offering me which OS to boot from, the XP on SATA or the Ubuntu on IDE. Just not happening to date. Thanks.

---

### Post by bulldog on 2006-11-27
It 's very simple really,just disconnect your sata from the motherboard,install Ubuntu on the IDE disk.
GRUB has no choice and will be installed on the IDE drive.

Make this drive the master boot device so if you start your computer you will see GRUB.

Now connect the sata again and this disk will be untouched by ubuntu.

To get windows into your GRUB you have to alter your menu.lst and add the windows entry to it with mapping hd0 to hd1,because windows likes to be on the first boot device,so you have to fool windows.

Now you can boot ubuntu and windows from GRUB but in case of disaster you can boot the sata disik with windows own bootloader.

I have helped many users with this problem and if you do a search you should find a topic about it.

But if you have questions about it,feel free to ask.

---

### Post by Sasquatch2000 on 2006-11-27
> **bulldog said:**
> ...To get windows into your GRUB you have to alter your menu.lst and add the windows entry to it with mapping hd0 to hd1,because windows likes to be on the first boot device,so you have to fool windows....

I followed all of what you said except this part. Where does one find this "menu.lst", and what should this "windows entry" look like?

Thanks, it sounds like we're heading in the right direction.

---

### Post by bulldog on 2006-11-27
If you're in Ubuntu open a terminal.
```
gksudo gedit /boot/grub/menu.lst
```
Add the following to the bottom of the list,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

This will work if your IDE [ubuntu] drive is your boot device and your sata [windows] is the second.

To see your windows partitions in Ubuntu you have to list them in fstab.
Here's a tutorial to do so.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by willcox on 2006-12-18
Hi bulldog!
 I'll really aprecciate if you could help me:
1.-sata with Ubuntu 6.10.
2.-IDE  hd with an intact XP.
I write "intact", because I have installed Ubuntu 6.10 with the IDE drive unpowered as I understood here:
 [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728).

sudo fdisk -l:
/dev/sda1               1          65      522081   83  Linux
/dev/sda2              66         326     2096482+  82  Linux swap / Solaris
/dev/sda3             327       13075   102406342+  83  Linux
/dev/sda4           13076       30401   139171095   83  Linux

Do I have to run the IDE drive as master or slave? 
And finally,  please,  how do I set /boot/grub/menu.lst with these HD's?
Thx!

---

### Post by confused57 on 2006-12-18
> **willcox said:**
> Hi bulldog!
 I'll really aprecciate if you could help me:
1.-sata with Ubuntu 6.10.
2.-IDE  hd with an intact XP.
I write "intact", because I have installed Ubuntu 6.10 with the IDE drive unpowered as I understood here:
 [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728).

sudo fdisk -l:
/dev/sda1               1          65      522081   83  Linux
/dev/sda2              66         326     2096482+  82  Linux swap / Solaris
/dev/sda3             327       13075   102406342+  83  Linux
/dev/sda4           13076       30401   139171095   83  Linux

Do I have to run the IDE drive as master or slave? 
And finally,  please,  how do I set /boot/grub/menu.lst with these HD's?
Thx!
Until bulldog sees your post...you could try setting your bios to boot first to the SATA drive with Linux installed and add a Windows entry similar to the one listed by bulldog to boot your Windows IDE drive.
There's some instructions on how to edit your /boot/grub/menu.lst here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Grub is installed to your SATA drive, so it would need to be set to boot first.

---

### Post by bulldog on 2006-12-18
> **willcox said:**
> Hi bulldog!
 I'll really aprecciate if you could help me:
1.-sata with Ubuntu 6.10.
2.-IDE  hd with an intact XP.
I write "intact", because I have installed Ubuntu 6.10 with the IDE drive unpowered as I understood here:
 [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728).

sudo fdisk -l:
/dev/sda1               1          65      522081   83  Linux
/dev/sda2              66         326     2096482+  82  Linux swap / Solaris
/dev/sda3             327       13075   102406342+  83  Linux
/dev/sda4           13076       30401   139171095   83  Linux

Do I have to run the IDE drive as master or slave? 
And finally,  please,  how do I set /boot/grub/menu.lst with these HD's?
Thx!

No,you have GRUB on the Sata drive because you disconnected the other one,so just let the Sata be boot device.
You should being able to boot your Ubuntu without any problem I guess,but the windows entry should be set in your menu.lst.
If you can give me the outcome of```
fdisk -l
``` with both drives connected?
Put it on the forum and I will make an entry for your windows so you can boot windows from GRUB as well.

**EDIT:**
Thanks  confused57 :-)

---

### Post by willcox on 2006-12-18
Hi!
ok, with both drives connected, I am only able to boot XP (slave).

Look:

I have this BIOS config/options:
IDE CONFIGURATION:
1.- Onboard IDE Operate Mode:
a).-Compatible Mode 
b).-Enhanced Mode(actually)
2.-Combined Mode Option:
a).-Pri IDE + SATA
b).-SATA + Sec IDE(actually)
Boot:
Boot Device Priority:
1st boot device (SATA)
2nd boot device (disabled)

I have read that XP wants to be the king always,  and I'm seeing. 
Even yet, I'm writing you from XP!

So, should I change the BIOS' options mentioned above, to get Ubuntu running?
 It seems that the only way is to connect the drive that will be in use.

---

### Post by confused57 on 2006-12-18
> **willcox said:**
> Hi!
ok, with both drives connected, I am only able to boot XP (slave).

Look:

I have this BIOS config/options:
IDE CONFIGURATION:
1.- Onboard IDE Operate Mode:
a).-Compatible Mode 
b).-Enhanced Mode(actually)
2.-Combined Mode Option:
a).-Pri IDE + SATA
b).-SATA + Sec IDE(actually)
Boot:
Boot Device Priority:
1st boot device (SATA)
2nd boot device (disabled)

I have read that XP wants to be the king always,  and I'm seeing. 
Even yet, I'm writing you from XP!

So, should I change the BIOS' options mentioned above, to get Ubuntu running?
 It seems that the only way is to connect the drive that will be in use.

bulldog, didn't know you'd be available to respond at the time or I wouldn't have intruded...

willcox,  first of all I wouldn't make but one or two changes at a time & be sure to write down what you changed, so you can change it back if you have problems...I'm not familiar with your bios options, but can you try highlighting the "2nd boot device" and enabling your IDE drive as the drive to boot 2nd...I guess you've selected the options that you've marked with "(actually)"...as I mentioned, write down whatever changes you make so you can change it back & try another option if it doesn't work...I'm not an expert, so you might want to wait for someone else who may be familiar with your specific bios options.

---

### Post by willcox on 2006-12-18
Thank you confused57!
The fact is,  that no matter how I change the BIOS options.
Being the two drives connected,  XP runs.
XP unplugged,  Ubuntu runs.
Well,  I'd better be patient,  besides,  Linux is my favorite OS.

---

### Post by confused57 on 2006-12-18
Until you get your bios configured correctly, hopefully, you might try the Super Grub Disk(see the Super Grub Disk section):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It's only a 500 kb download, and the Super Grub Disk might enable you to boot to either drive with both drives connected...you may or may not want this as a permanent solution, but it's worth a try.

---

### Post by Sasquatch2000 on 2006-12-19
How come there are no free partition software programs like "Partition Magic"?  This one pops into my head, having seen it maybe 7 years ago working quite nicely.

It seems the "Ubuntu experience" needs help in the "Transitioning Department".

---

### Post by bulldog on 2006-12-19
> **Sasquatch2000 said:**
> How come there are no free partition software programs like "Partition Magic"?  This one pops into my head, having seen it maybe 7 years ago working quite nicely.

It seems the "Ubuntu experience" needs help in the "Transitioning Department".

There certainly is a very good graphical partitioner called Gparted live cd.
Download it [30MB],burn it on a disk and boot from it,you'll be surprised.

 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by bulldog on 2006-12-19
> **willcox said:**
> Hi!
ok, with both drives connected, I am only able to boot XP (slave).

Look:

I have this BIOS config/options:
IDE CONFIGURATION:
1.- Onboard IDE Operate Mode:
a).-Compatible Mode 
b).-Enhanced Mode(actually)
2.-Combined Mode Option:
a).-Pri IDE + SATA
b).-SATA + Sec IDE(actually)
Boot:
Boot Device Priority:
1st boot device (SATA)
2nd boot device (disabled)

I have read that XP wants to be the king always,  and I'm seeing. 
Even yet, I'm writing you from XP!

So, should I change the BIOS' options mentioned above, to get Ubuntu running?
 It seems that the only way is to connect the drive that will be in use.

As I look at this options,I would choose 2)Combined mode with option b,Sata + Sec IDE.
If you connect the IDE disk in present situation,it will be master,which we don't want.
In the combined mode is the Sata the first boot device and this is what we want to have.
It's possible though,you have to connect the IDE disk to the secondary IDE port to be seen as a secondary master.

Edit:
No problems confused57,if you can solve it before I can it's alright with me.
The bottom line is to help users with problems.:-)

---

### Post by willcox on 2006-12-19
Hi my friends!
Don't know exactly, what's happening:
Instead of connect the XP drive, I have plugged a FAT32 (IDE slave) partition and SATA (ubuntu) running:

I.- sudo fdisk -l:
/dev/sda1 1 65 522081 83 Linux
/dev/sda2 66 326 2096482+ 82 Linux swap / Solaris
/dev/sda3 327 13075 102406342+ 83 Linux
/dev/sda4 13076 30401 139171095 83 Linux

II.-sudo mount /media/hdb &#8594; nothing!

III.-sudo mount /media/hdb1 &#8594; nothing!

IV.-Aplications &#8594; system tools &#8594; sysinfo &#8594; IDE = nothing!

The question is, why Ubuntu doesn't recognize the FAT32 Partition?

-Do I have to write 1 or 2 scripts in /etc/fstab?  for example:
 /dev/hdb	/mnt/SCRATCHDISK	vfat	rw,defaults,umask=0000	0 0.....
  BTW, this partition runs smoothly with this script in FC5. (SCRATCHDISK is the name/label's partition) and stores only music, some videos and personal data.

-Is it a kernel problem?

-BIOS detects the drive as is, 2nd IDE drive (slave). Ubuntu doesn't.

-I'm deeply considering the motherboard that I recently bought could be my big disgrace..(Intel CPU too). I used to install linux & XP with AMD and compatible motherboards with any problem.

---

### Post by confused57 on 2006-12-19
willcox,   Ubuntu usually has no problems detecting IDE controllers, but it "appears" that yours is  not...what mobo are you using?   You might want to start another thread with the title mentioning your "mobo type & IDE problem" & someone using the same mobo may be able to help you(maybe start the thread in the hardware section)...a google search may help. 
Have you tried the Super Grub Disk?

---

### Post by kheyz on 2007-01-09
Hello, I am a fresh user of Ubuntu and loving it.  Zero filled my drive and dropped an Edgy install to help force my learning experiance of the Ubuntu ways.  So far so good :) Many forums later and countless hours in the terminal (at least it seemed) I had support for my Nostromo N52 pad and able to run WoW through wine at a very acceptable framerate, with only a slight difference in performance.  But alas, the slight performace difference is enough to want to run WoW through winbloze, or at least have the option to do so.
 I have an extra IDE hard drive lying around with windows already on it.  Ubuntu is currently on my on a single SATA drive with no other hard drives installed.  Anyone forsee any issues with me just popping in the IDE (with winbloze) as a secondary and editing the GRUB as many have suggested?  Or will GRUB auto recognize the new drive and OS?  Any suggestions or other routes I should take?  Thanks in advance.  Great community, and a fine piece of open source I have gathered so far :)

---

### Post by oedenfield on 2007-02-09
I am trying to do the same thing.  I have a SATA drive with Windows that I normally boot right into and I have an IDE drive setup with two partitions (I'm hoping to put SLES 10 on one and Ubuntu desktop on the other, but at this point I'm just concerned with ubuntu).

I get to the last part of the install where it is asking about GRUB and the default setting is hd0.  I don't know if hd0 is my IDE or my SATA.  I am fine if it is IDE because I can always hit F8 during POST and I can choose my drive to boot into there if I had to.  And if hd0 is my SATA drive then I would want GRUB to be smart enough to see that I have a Windows install on that drive and have a boot option for it.

I don't want hd0 to be my SATA and GRUB to just know about the ubuntu install and just give me the option to boot to ubuntu.

I can't find anything that explains what hd0 actually is.  Thank you everyone for your responses above, there has got to be a best way to do it.

---

### Post by confused57 on 2007-02-09
> **oedenfield said:**
> I am trying to do the same thing.  I have a SATA drive with Windows that I normally boot right into and I have an IDE drive setup with two partitions (I'm hoping to put SLES 10 on one and Ubuntu desktop on the other, but at this point I'm just concerned with ubuntu).

I get to the last part of the install where it is asking about GRUB and the default setting is hd0.  I don't know if hd0 is my IDE or my SATA.  I am fine if it is IDE because I can always hit F8 during POST and I can choose my drive to boot into there if I had to.  And if hd0 is my SATA drive then I would want GRUB to be smart enough to see that I have a Windows install on that drive and have a boot option for it.

I don't want hd0 to be my SATA and GRUB to just know about the ubuntu install and just give me the option to boot to ubuntu.

I can't find anything that explains what hd0 actually is.  Thank you everyone for your responses above, there has got to be a best way to do it.
Whichever hard drive is set up in bios to boot to first "should"  be recognized as hd0 by grub.  I always install with the alternate cd, when the installer offers to install grub to (hd0), I select "no", then it offers an option of where or if...I usually enter /dev/hda(or /dev/hdb,/dev/sda,etc), just to be on the safe side, rather than (hd0).

---

### Post by v8YKxgHe on 2007-03-02
Nope! that didn't work. I get 

```
Error 23 - Error while parsing number
```

Pah, ignore me! Wrong thread :P hehe

---

### Post by oedenfield on 2007-04-25
I finally addressed this issue by just disconnecting my XP drive (I knew for sure that Ubuntu wasn't going to touch it.. and then installed.

Now my BIOS decides what is going to boot (I press F8 when I see the ASUS logo) and then I can choose.  One day I'll think about configuring GRUB on my IDE to see the Windows XP install on SATA and that will be nice, until then I am happy with just automatically booting into ubuntu unless I press F8 (BIOS configuration).

---

### Post by Kattumaram on 2007-05-02
> **mingus said:**
> 1.  Set BIOS to boot from SATA
2.  Install XP on SATA
3.  Boot from Ubuntu install CD, follow directions and at partition menu, use "guided partitioning" on the IDE drive (hda) or use "manual" to control more closely how the partitions are done
4.  At the boot loader menu, do *NOT* take the default.  Instead instruct the installer to put grub on the Master Boot Record of the IDE drive (/dev/hda) - *NOT* on the SATA drive (sda)
5.  Ubuntu will finish phase one of install and ask you to reboot.  *Immediately*  enter BIOS setup and change sequence to boot from IDE drive.  Let Ubuntu finish installation.  If you do not yet have your network connection set up, be sure to tell installer to get packages from CD only
6.  In Ubuntu go to Applications/System Tools/Terminal.  You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
savedefault
chainloader        +1

and change it to this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
map                    (hd1,hd0)
map                    (hd0,hd1)
chainloader        +1

7.  save the file
8.  reboot and test boot into XP

Thanks, Mingus:

Your scheme finally bailed me out of the snarl produced by my three HDDs, all SATA, when I attempted to dual- boot, XP and Ubuntu, each on a different drive..  XP Pro is on HD2 (sdc), Ubuntu on HD1(sdb) and two NTFS primary partitions are on HD0 (sda).  The MBR is on HD0 (sda). I installed GRUB to (sda) during the installation of Ubuntu on HD1(sdb)  per the above instructions and then made changes in the /BOOT/GRUB menu.lst to get XP onto the menu....works like a charm.....took me only two days to get it all configured.

---

### Post by Sasquatch2000 on 2007-05-20
> **angdis-bb said:**
> I just did a dual boot install. My machine has windows XP on the sata drive, and I installed linux on an IDE drive.

I didn't know anything about this issue and just installed by "clicking through" using the desktop CD.

Immediately after install was complete, the machine rebooted into windows instead of grub, so I googled for answers and found this thread.

I looked at mingus' posting but remembered that I did not get any menu asking where to put grub. I so I skipped that and just went into the PC bios. All I had to do was to change the order of booting so that the IDE drive was before the SATA drive. 

Now everything works fine (boots into grub).

So, what you are saying is that you are using hardware (BIOS), not software (OS or boot program) to choose the boot drive? I suppose I could also do that, but was looking for something more elegant (easy).

---

### Post by 4WoofGrrrr on 2007-05-29
Please help me if you can.


I just installed Ubuntu 7.04 on my existing Win XP system in an attempt to make dual-boot system.
Strangely, I just assumed the install could handle this situation and do the right thing.

The system has two hard drives, one is SATA and the other is EIDE.

The SATA drive has two FAT32 and one NTFS partition. Win XP is installed on the NTFS partition.
The EIDE drive had one NTFS partition and lots of free space

I wanted to install Ubuntu from the Live CD into the free space on the EIDE drive.

When it was time to assign partitions, I create a SWAP and several REISERFS partitions:
               /    /var    /usr    /opt    /home
The install completed and Ubuntu booted from the hard drive with no problems.
I was never asked where to write the Master Boot Record (mbr.)



When I tried to reboot, however, I got booted directly into Win XP!!! No option to boot Ubuntu.
No menu. Just directly to Win XP.

I figured out that the Ubuntu install put the MBR on the EIDE drive, NOT the SATA drive,
and my BIOS was setup to boot the SATA drive. So I used GRUB from the SuperGrub
CD to write the MBR on the SATA drive. It worked. (I know I could have just changed
the boot disk in the BIOS, but I didn't think of it until later...)  The boot menu showed up!
(I have since discovered several threads that discuss this problem, including this thread,
my notions were confirmed as to what the problem was and how to fix it .. thanks)

(I sure wish the INSTALL CD had been more helpful with these issues.  I mean, I have
read and read and read about how wonderful Ubuntu is and how easy it is to install.
I linux newb like me should really not have to deal with all this!)




So everything was fine.

That is, until I noticed one of my Win XP drive letters was missing!!! An NTFS parition
on the same EIDE drive onto which I installed Ubuntu is missing.   When I installed, I
did NOT change any partition sizes.  I merely created NEW partitions in the free space
that I had saved just for linux.



I bring up Win XP Disk Manager, and the EIDE drive is not even listed. The whole drive
has just vanished, along with the NTFS partition on it. No linux partitions. No free space.
Nothing.

I bring up the Win XP Device Manager, and the EIDE drive is there. I display its properties
and click the "Volumes" tab, no partitons are displayed. When I click the "populate" button
NOTHING IS DISPLAYED.

When I boot Ubuntu, the NTFS filesystem is there. I can read files from it. All the paritions
I created during the Ubuntu install are there as well!



So what happened? Did "parted" during the Ubuntu install write a Partition Table that
Win XP doesn't understand??? If so, can I make it write a Partition Table that Win XP
DOES understand? How? Is there any way to fix this?



Thanks for any help you can provide.

---

### Post by 4WoofGrrrr on 2007-05-31
**Never Mind.**

I re-partitioned the drive and re-installed everything.

How the Disk Label and Partition Table got screwed up
so XP could no longer read it I will never know.

---

### Post by Sasquatch2000 on 2007-06-11
Wow, I just found this: [Wubi](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

I don't know if it will help here or not, but it sure sounds good. Why can't Ubuntu incorporate this into their code?

If my system were more expendable, I'd try it; but I have some photos and other stuff on there I don't want to blow away.


I tried again over the weekend, and installed the Ubuntu 7.04 on the IDE drive while the SATA drive was also hooked up. 

Now I get a grub menu with several choices, but when I try the Window (last choice) XP one, it just sits there trying to start up. It never gets to the Windows stuff.

I still have to pull the plug on the IDE for the system to see the SATA. BIOS is of no help.

---

### Post by adamskixp on 2007-06-24
Hi, well i have a different matter, seem to have just installed ubuntu onto my spare hd, but is there anything i can do as to when pc starts up it defaults to starting ubuntu and i cant use my keyboard to select usb emulation as then it comes up with a grub error 17, also when i do load ubuntu it has issues with the display and doesnt load any further, the screen goes bright and flasing with vertical lines, d,oh

Any help would be much appreciated

Thanks in advance

Adamski

---

### Post by ferronica on 2007-06-24
i have SATA windows XP installed and IDE ubuntu Fiesty Fawn  GNOME installed, what settings do i need ?

---

### Post by Max Headroom on 2007-09-16
Dell Dimension 5100;

WinXP on SATA, need to install Ubuntu on Trigem 60gb IDE drive.

Progress so far...

[INDENT]Downloaded .iso, unwrapped it and copied that image to a cd.

Added IDE drive on the same ribbon cable as the cd drive, cd drive is on the end connector.
[LIST]
[*]Disconnected SATA
[*]Set jumpers on IDE to master
[*]Edited to boot from cd
[*]Boot up, says no drive present
[*]Changed jumpers to various options of three shown, still no go.
[*]Disconnected IDE and SATA, boot from cd, says no drive present.
[/LIST][/INDENT]


I'm wondering if this is a Dell thing?

If anyone has the same machine and successfully installed Ubuntu on a second drive, I'd appreciate hearing your setup.  Thanks in advance.

---

### Post by Max Headroom on 2007-09-24
Bump

Any tips or advice really would be appreciated, thanks in advance.

---

### Post by The_Shady_1 on 2007-10-18
I'm trying to do the same thing here, any tips? WinXp on SATA      Ubuntu 7.10 on IDE. I unplugged my SATA when I installed Ubuntu and all is fine with that but I do I get it to promt to ask which OS to boot from. My BIOS only lets me select floppy,cdrom,Hard disk.

---

### Post by RubberSoul on 2007-11-03
> **mingus said:**
> 1.  Set BIOS to boot from SATA
2.  Install XP on SATA
3.  Boot from Ubuntu install CD, follow directions and at partition menu, use "guided partitioning" on the IDE drive (hda) or use "manual" to control more closely how the partitions are done
4.  At the boot loader menu, do *NOT* take the default.  Instead instruct the installer to put grub on the Master Boot Record of the IDE drive (/dev/hda) - *NOT* on the SATA drive (sda)
5.  Ubuntu will finish phase one of install and ask you to reboot.  *Immediately*  enter BIOS setup and change sequence to boot from IDE drive.  Let Ubuntu finish installation.  If you do not yet have your network connection set up, be sure to tell installer to get packages from CD only
6.  In Ubuntu go to Applications/System Tools/Terminal.  You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
savedefault
chainloader        +1

and change it to this:

title                     Microsoft Windows XP Professional
root                    (hd1,0)
map                    (hd1,hd0)
map                    (hd0,hd1)
chainloader        +1

7.  save the file
8.  reboot and test boot into XP

Ok, in the first time i`ve done it, it worked fine, but now (fresh installl of windows and ubuntu) in the ubuntu instalation, he dont give me the boot loader menu option to choose what hard drive comes first. What should i do?? if i cant choose he erases windows mbr and it wont work any more...

---

### Post by RubberSoul on 2007-11-04
upz

---

### Post by bulldog on 2007-11-05
I think you can find all you need at this places,

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by shakyone on 2008-01-18
Max Headroom, try putting your HDD on the IDE cable into the Master position and the CD Rom in the slave position, and set their jumpers accordingly.

---

### Post by smo0th on 2008-03-15
> **dahabreh said:**
> but when i run the unbuntu installation with SATA and IDE HD connected the setup doesn't see the IDE drive!!! ](*,) 

help help help

I have ubuntu in my 500GB SATA and trying to install xp in my 15GB IDE only for gaming, I just ran thru the problem you have, you need to go to the BIOS and look for a hard disk drive setting which sets hard disk drive #1, originally I could not boot because the blank IDE drive was there as #1, so I changed it to be the SATA drive as #1.

So you should find this parameter and set your IDE drive as #1 because the BIOS only takes this drive for boot purposes.

Please let me know if this was any help to you or you need more details.

Regards,

---

### Post by Sasquatch2000 on 2008-04-09
How does Ubuntu 8.04 "Hardy Heron" change any of this?


What I am really looking for is a way to install Ubuntu Linux onto either the same partition or another partition on either the same and/or another hard drive. I want a choice of which OS to boot on when I start up. 

Any ideas?

Thanks.

---

