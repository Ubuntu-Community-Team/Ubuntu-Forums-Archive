---
title: "I can't Use Windows XP After Installing Ubuntu 7.04"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by elektr10 on 2007-05-01
I've just instaled ubuntu 7.04.
Grub menu appears on system startup but there is not the choice "windows xp" although it is installed.I'm sure that there is no problem with windows xp but after installing ubuntu I can't reach xp.How can I solve the problem?

---

### Post by mysticrider92 on 2007-05-01
Weird, I have never had problems with Ubuntu stopping XP from booting. First try 'sudo gedit /boot/grub/menu.lst' and check for a line towards the bottom that says anything about Windows. Copy that section and post it if you can and we will go from there.

Also, this part of the forums is for problems with ubuntuforums.org, this should be in 'General Help' or 'Absolute Beginner Talk'. ;)  A mod can move it for you.

---

### Post by elektr10 on 2007-05-01
Windows is mentioned only in an example:
[B][I]editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		[COLOR="Red"]Windows[/COLOR] 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1[/I][/B]

Sorry for my fault.I'm a beginner at this forum. :(

---

### Post by bulldog on 2007-05-01
Can you boot ubuntu?
If so,perform in a terminal ```
sudo fdisk -l
``` it's a lowercase L not a one.
Post the output on the forum please.

---

### Post by elektr10 on 2007-05-01
> **bulldog said:**
> Can you boot ubuntu?
If so,perform in a terminal ```
sudo fdisk -l
```
Yes I can.This is the output:
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         233     1871541   1b  Hidden W95 FAT32
/dev/sda2             234         243       80325    7  HPFS/NTFS
/dev/sda3             244        7402    57504667+  83  Linux
/dev/sda4            7403       12161    38226667+   f  W95 Ext'd (LBA)
/dev/sda5            7403       10875    27896841    7  HPFS/NTFS
/dev/sda6   *       10876       12100     9839781   83  Linux
/dev/sda7           12101       12161      489951   82  Linux swap / Solaris

---

### Post by bulldog on 2007-05-01
Is windows on the sda2 partition?

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1
```

If yes,add this entry to your menu.lst.
```
gksudo gedit /boot/grub/menu.lst
```
This opens the menu.lst in a text editor.
Just copy and paste the part you need,I copied some extra lines,so you better understand where to put it [at the bottom]

---

### Post by elektr10 on 2007-05-01
> **bulldog said:**
> Is windows on the sda2 partition?

No.On sda5.

---

### Post by bulldog on 2007-05-01
Well in that case you have a problem.:( 
Windows should be installed on the first primary partition,**but never in a logical partition**
You can't boot from a logical partition.

---

### Post by jml on 2007-05-01
I don't use Vista but I have read on several sites that your problem is not uncommon.  Vista interacts with the boot loader in a way that is different from all previous versions of Windows.  Here are a few sites that offers solutions.  Hope that they help.

[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

[http://www.desktoplinux.com/articles/AT2094892904.html](http://www.desktoplinux.com/articles/AT2094892904.html)

Hope this is of help.

Joe

---

### Post by elektr10 on 2007-05-01
> **bulldog said:**
> Well in that case you have a problem.:( 
Windows should be installed on the first primary partition,**but never in a logical partition**
You can't boot from a logical partition.
Isn't there any solution hope :(

> **jml said:**
> I don't use Vista but I have read on several sites that your problem is not uncommon.  Vista interacts with the boot loader in a way that is different from all previous versions of Windows.  Here are a few sites that offers solutions.  Hope that they help.

[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

[http://www.desktoplinux.com/articles/AT2094892904.html](http://www.desktoplinux.com/articles/AT2094892904.html)

Hope this is of help.

Joe
Thanks for your interest but I use xp, not vista.

---

### Post by bulldog on 2007-05-01
Not one I know of.

Ubuntu can be installed anywhere,but windows is a little picky about that.
I certainly have never heard of booting windows from a logical partition.

But you can wait if someone else have a better idea.

---

### Post by TennTux on 2007-05-01
I have installed Ubuntu 6.06 on both a Win2000 and a Win XP system and in both cases I had to tell GRUB how to dual boot. I might not have all the details but the process involved editing 2 files. */boot/grub/device.map* and */boot/grub/menu.lst*.

The device.map has a mapping of the drives needed during boot. One of mine looks like the following after editing.
```
(hd0)      /dev/hde
(hd1)      /dev/hdf

```

While I needed to add the following to the end of my menu.lst file. At least make sure it's not in the middle of the *BEGIN AUTOMATIC KERNELS LIST* ... [I]END AUTOMATIC KERNELS LIST
[/I]```

title      Windows 2000
map     (hd0) (hd1)
map     (hd1) (hd0)
root     (hd1,0)
makeactive
chainloader     +1

```

As I understand it the mapping is needed to fool the system into thinking the windows disk is the first one on the system before invoking the window bootloader. The entries in your map file will vary according to you system. Be sure to check out the man pages on these files and the map command.

Best of luck.

---

### Post by elektr10 on 2007-05-02
I would apply the way that showed bu there is no ***_(hd1)_*** in device.map.
There are both (hd0) and (hd1)in the second code.

Can I create new (hd1) or what should I do?

---

### Post by dannyboy79 on 2007-05-02
> **elektr10 said:**
> I would apply the way that showed bu there is no ***_(hd1)_*** in device.map.
There are both (hd0) and (hd1)in the second code.

Can I create new (hd1) or what should I do?


could you clarify what you are saying? please post the output from 

cat /boot/grub/device.map

and also

sudo fdisk -l

(NOTE: tell us which os's are where when you show us the output from the fdisk command)

---

### Post by elektr10 on 2007-05-02
The output of "cat /boot/grub/device.map" is:
```
(hd0)   /dev/sda
```

Output of "sudo fdisk -l" is:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         233     1871541   1b  Hidden W95 FAT32
/dev/sda2             234         243       80325    7  HPFS/NTFS
/dev/sda3             244        7402    57504667+  83  Linux
/dev/sda4            7403       12161    38226667+   f  W95 Ext'd (LBA)
/dev/sda5            7403       10875    27896841    7  HPFS/NTFS
/dev/sda6   *       10876       12100     9839781   83  Linux
/dev/sda7           12101       12161      489951   82  Linux swap / Solaris

```

There are 3 os's on my computer.
*Windows is on sda5
*Ubuntu is on sda6
*Pardus(another linux version) is probably on sda3 because one linux version is ubuntu, the other is pardus.

I hope I'm clear enough ;-)

Please also have llok at that photo.Maybe it helps to examine the problem.
[[IMG]http://img369.imageshack.us/img369/6255/screenshotkv8.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshotkv8.png)

---

### Post by dannyboy79 on 2007-05-02
> **elektr10 said:**
>  The output of "cat /boot/grub/device.map" is:
```
(hd0)   /dev/sda
```

Output of "sudo fdisk -l" is:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         233     1871541   1b  Hidden W95 FAT32
/dev/sda2             234         243       80325    7  HPFS/NTFS
/dev/sda3             244        7402    57504667+  83  Linux
/dev/sda4            7403       12161    38226667+   f  W95 Ext'd (LBA)
/dev/sda5            7403       10875    27896841    7  HPFS/NTFS
/dev/sda6   *       10876       12100     9839781   83  Linux
/dev/sda7           12101       12161      489951   82  Linux swap / Solaris

```

There are 3 os's on my computer.
*Windows is on sda5
*Ubuntu is on sda6
*Pardus(another linux version) is probably on sda3 because one linux version is ubuntu, the other is pardus.

I hope I'm clear enough ;-)

Please also have llok at that photo.Maybe it helps to examine the problem. 

ok, well whats the problem? you can't boot into windows? i have to ask, what is on sda2? so looking at the picture, when you look inside the /media/ folder, do you see ntldr and all your normal windows os stuff? if that's the case, all you need to do is add an entry like this to be able to boot into windows.


title      Windows XP (NOTE TO YOU: this exactly what you'll see within grub so you can put whatever)
root     (hd0,4)
makeactive
chainloader     +1

that should do it.

---

### Post by elektr10 on 2007-05-02
> **dannyboy79 said:**
> ok, well whats the problem? you can't boot into windows? i have to ask, what is on sda2? so looking at the picture, when you look inside the /media/ folder, do you see ntldr and all your normal windows os stuff? if that's the case, all you need to do is add an entry like this to be able to boot into windows.


title      Windows XP (NOTE TO YOU: this exactly what you'll see within grub so you can put whatever)
root     (hd0,4)
makeactive
chainloader     +1

that should do it.
Your prediction  is completely true.I mean i can't boot into windows.I'm not sure but probably there is nothing on sda2 because i had some problems with partition magic and there is an extra partition(about 78 mb) that i made it by misake.
I can use all the data inside the /media/ folder  including windows system files.

You didn't say but i firstly typed [I][B]"sudo gedit /boot/grub/menu.lst"
[/B][/I] and added the code that to the end of the page and saved.When i pressed "enter" on "windows xp" on system startup, an error message appeared:
[B][I]Error 12:Invalid device requested.
Press any key to continue[/I][/B]
When i press a key, it returns to the OS menu. :(

---

### Post by bulldog on 2007-05-02
To save you a lot of trouble,you better reinstall windows.
Don't use Partition Magic to partition your hdd,use the gparted live cd instead.
PM has some issues with making Linux partitions.
Gparted has a GUI so it shouldn't be to difficult.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can mount your windows partition if needed,so you can copy any data from it.

---

### Post by dannyboy79 on 2007-05-02
NO, don't reinstall windows, you've barely troublshot anything!!!!

before anything, lets make sure that windows is where he says it is and if it's missing boot files that's easy to fix!!

just start here:

you're certain that windows is installed on sda5? I asked if that when you had /dev/sda5 mounted to /media/  what was inside the folder? if /dev/sda5 has ntldr and all the other windows boot files than there should be no reason you would get grub error 12. are you saying that grub menu isn't even appearing? or are you saying that this error appeared before it even made it to the grub menu? 

just as a double top secret verify, let's reinstall grub into the mbr of sda (hd0) and point the setup to (hd0,5) IF in fact you're saying that your /boot/grub/  folder and files are located on /dev/sda6. so you would boot into a live cd, then type in at a terminal

sudo grub

root (hd0,5)
setup (hd0)

exit

and that will install grub to your mbr of your sda disk. then when you boot into your ubuitnu install, add the info I gave you at the top and it should boot into windows UNLESS of course you're giving me the wrong info (it's possible that you're giving me incorrect info on accident. just find out where windows is installed by mounting all of the NTFS partitions and seeing what's on each one. the one with windows installed obviously has ntldr, ntdetect.com and other boot required files. and also the system32 folder, the windows folder etc etc.

---

### Post by bulldog on 2007-05-02
> **dannyboy79 said:**
> and you're certain that windows is installed on sda5? I asked if that when you had /dev/sda5 mounted to /media/  what was inside the folder? if /dev/sda5 has ntldr and all the other windows boot files than there should be no reason you would get grub error 12. are you saying that grub menu isn't even appearing? or are you saying that this error appeared before it even made it to the grub menu? 

just as a double top secret verify, let's reinstall grub into the mbr of sda (hd0) and point the setup to (hd0,5) IF in fact you're saying that your /boot/grub/  folder and files are located on /dev/sda6. so you would boot into a live cd, then type in at a terminal

sudo grub

root (hd0,5)
setup (hd0)

exit

and that will install grub to your mbr of your sda disk. then when you boot into your ubuitnu install, add the info I gave you at the top and it should boot into windows UNLESS of course you're giving me the wrong info (it's possible that you're giving me incorrect info on accident. just find out where windows is installed by mounting all of the NTFS partitions and seeing what's on each one. the one with windows installed obviously has ntldr, ntdetect.com and other boot required files. and also the system32 folder, the windows folder etc etc.

Windows is installed on a logical partition instead of a primary.
In my understanding you can't boot windows from a logical partition.
It has nothing to do with GRUB as far as I know.

---

### Post by elektr10 on 2007-05-02
You(dannyboy79) emphasized whether i'm sure that my windows is on hda5.Unfortunately i become hesitant about it.I said that windows is on sda5 because two os's are shown on system monitor.One is hda5 and the other is hda6.hda6 is formatted as ntsf.So i think windows is on that partition. 
I can access windows system files and folders with no problem but how can i understand whether ntldr is on that partition?

I reinstalled grub but no change on system startup.Grub menu appears with no problem but i can't choose windows.

Also "bulldog" says something logical.What do you think about that?

---

### Post by dannyboy79 on 2007-05-03
well Bulldog is right on the money, that an oversight on my part. There is a way to boot windows from a logical partition!

this is a guide ([http://www.goodells.net/multiboot/ptedit.htm](http://www.goodells.net/multiboot/ptedit.htm)) that uses a $50.00 software title called PowerQuest's Partition Table Editor 

but you can download a free partition editor called DFSee which looks to be WAY more versatile than Powerquests's product, you can download it and get familar with  it here: [http://www.dfsee.com/dfsee/download.php](http://www.dfsee.com/dfsee/download.php)

It does cost money BUT there is a short evaluation period and after that you are required to register and pay for the program. Unregistered versions remind you of this at startup and termination of the program and it is not possible to use batch-mode for unattended operation. Otherwise the program is fully functional.


So it is certainly possible to booot windows from a logical drive!!!! Now whether or not you want to do this is another story. If you can simply save all your data off onto other drives and reinstall windows onto a primary partition that sounds like the easiest but NOT the funnest or most challenging. 

Good luck in whatever you decide and make sure you let us know.

---

### Post by elektr10 on 2007-05-03
I like challenging so will try your first solution offer. I'm already challenging because although i've nearly no information about linux, &#304; don't give up trying. :)

I'll prefer second program because it's free to try :)
However i've some questions:
I understand that it'll make an image of my windows and write it to the same partition and can make it first primary partition so my problem will be solved.Am i right?If no, could you explain for me?

I have a look at the site but there is no information how to use the program.The site explains only its features and how to download it.I'm afraid i can commit an irrecoverable mistake. :(

There are 2 options to install.One is "Latest 8.xx version, Linux files only (560 Kb ZIP)", the other is "Latest 8.xx version, Linux TARBAL (550 Kb .tgz)".Which one should i install?

---

### Post by dannyboy79 on 2007-05-03
> **elektr10 said:**
> I like challenging so will try your first solution offer. I'm already challenging because although i've nearly no information about linux, &#304; don't give up trying. :)

I'll prefer second program because it's free to try :)
However i've some questions:
I understand that it'll make an image of my windows and write it to the same partition and can make it first primary partition so my problem will be solved.Am i right?If no, could you explain for me?

I have a look at the site but there is no information how to use the program.The site explains only its features and how to download it.I'm afraid i can commit an irrecoverable mistake. :(

There are 2 options to install.One is "Latest 8.xx version, Linux files only (560 Kb ZIP)", the other is "Latest 8.xx version, Linux TARBAL (550 Kb .tgz)".Which one should i install?


ok, the second option. sounds like a great challange and I am glad to see some1 with some ba__s. you can just download the zip UNLESS you don't have anything to open a zip within Ubuntu, if you don't then download the tarball, both contain hte same stuff but they have are within different compression packages (zip versus tar). Instead of installing it into linux, let's just burn the iso to a disk and then boot the computer to it, that way we won't have any system files in use if we want to clone linux with it. the instructions for burning it onto a cd are with the readme file within the .zip. 

The best instructions and help you'll get are within the yahoo group for DFSee, i just joined it myself, so I suppose I can help ya but I am not familar with it either, i merely found it as a solution to your problem. 

Well the easiest thing to do would be to clone it then put it within a Primary partition instead of trying to edit the hidden sectors with the partition table. the guide for editing the hidden sectors within the partition table was that other link, that guide uses ptedit.exe and that's exactly what is contained within DFSee according to the website. Let me know how it goes.

ANYTIME YOU'RE MOVING AROUND PARTITIONS OR EDITING PARTITION TABLES I WOULD ALWAYS RECOMMEND YOU BACKUP THE INFO THAT YOU CAN'T AFFORD TO LOSE, THEN CONTINUE. I can tell you a first hand experience which saved my but. I work on computers on the side, long story short, prior to me attempting a dual boot setup with Win2000 and Xubuntu Edgy, I chose to not only use Partimage to backup his Win2000 image onto a fat32 partition but I also used a tar command to backup everything at the file level. Well it turned out that when I tried to restore the Win2000 image back onto the NTFS Partition crreated by Gparted, I got a Disk Read Failure, I tried everything to get it to work but it wouldn't. So I ended up wiping the partition by writing zero's to it, then I started up the windows installer, formatted the drive then during the install I hit Escape, it asked if I really wanted to stop the install, I said yes. Ok, now I had a NTFS partition created by Win2000. Next I connected the drive to my Ubuntu setup and extracted the tar file of his Win2000 setup onto this drive. Then I poped in the Win2000 cd again and chose to do a Automatic Repair of the OS using the Recovery Console, then when I rebooted there was the Lovely WIn2000 logo. 

So, moral of the story, back it up back it up, back it up, maybe not just at the partition level, but the file level as well. Good luck

---

### Post by elektr10 on 2007-05-05
Thank you so much but for your long explanation but i couldn't commit what you said.The program is so complicated and works with commands so i didn't want to use it to prevent critical mistakes.I thought to have an image on virtual pc with acronis true image but when i get in touch with someone who tried it, i got bad news.He said it had problems while restoring the image.
So my only cure is to reinstall both ubuntu and windows :(
However i have still some hesitations:
I'm planning to install ubuntu on C,windows on D.When i apply my plan do you think windows will be installed on "first primary partition" and i'll have no problem?I mean should i do anything else to make windows installed on "first primary partition".

---

### Post by dannyboy79 on 2007-05-07
> **elektr10 said:**
> Thank you so much but for your long explanation but i couldn't commit what you said.The program is so complicated and works with commands so i didn't want to use it to prevent critical mistakes.I thought to have an image on virtual pc with acronis true image but when i get in touch with someone who tried it, i got bad news.He said it had problems while restoring the image.
So my only cure is to reinstall both ubuntu and windows :(
However i have still some hesitations:
I'm planning to install ubuntu on C,windows on D.When i apply my plan do you think windows will be installed on "first primary partition" and i'll have no problem?I mean should i do anything else to make windows installed on "first primary partition".


i don't agree with reinstalling both os's but if that's what you want to do than I can help. ALWAYS INSTALL WINDOWS FIRST. you can isntall ubuntu first but then you'll have to fix grub after windows overwrites it. 

So simply use windows xp cd installer and when it gets to the point of partitioning and preparing the disk just delete ALL the existing partitions, simply one by one click on the one that you don't want and hit D (for delete) if I remember right, then it'll ask again if you're sure you want to delete that partition. then simply create a new one for winxp but make it at a minimum 10gb, that should be enough for basic programs and the os. and leave all the remaining space UNALLOCATED, don't do anything with it. then simply install ubuntu using the installer and your'e set. If you're not using the alt cd, then it'll automagically install grub to the mbr of the drive you're installing it on and will also pick your existing win install and youll be set. that's it. your're done.

---

### Post by elektr10 on 2007-05-13
Thank you (dannyboy79 and bulldog) for your help.I have successfull installed both ubuntu and windows xp :)
It's time to enjoy :)

---

### Post by heartbeat on 2007-05-17
I already have windows xp installed.
when i want to install ubuntu, should i install ubuntu on a logical partition?

---

### Post by bulldog on 2007-05-17
> **heartbeat said:**
> I already have windows xp installed.
when i want to install ubuntu, should i install ubuntu on a logical partition?

It doesn't matter where you install ubuntu,primary or logical,just be sure your windows is on the first primary partition.

---

