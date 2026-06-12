---
title: "Partition Help On Feisty Fawn (7.04) Installation"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by Magneticgravity on 2007-08-27
Hello all, I recently installed Dapper Drake (6.06) on my Dell PC, partitioning it with Win. XP. I gave Ubuntu 100GB and Xp 45GB (mainly for games on Xp).

Anyway, I found out it would be better if i upgraded to Feisty Fawn. I downloaded the Live CD from the website and using K3P or some ISO CD burner i put the Feisty ISO onto a CD.

Pretty confident that i knew what to do, i put the CD in the drive and rebooted my PC. The splash screen came up, i hit enter on the first option and the desktop came up. 

I clicked 'Install' on the desktop, and went through the first few options (language, location etc.).
I got to the Partition step, and there was three options:

 1) *Guided - resize SCS13 (0,0,0), partition #5 (sda) and use freed space*

*New Partition size* (and then a slider dial showing the amount of GB, it went up to 100GB).

2) *Guided - use entire disk*

(with my full HDD GB available).

3) * Manual*

Anyway I clicked Manual, knowing that i wanted to format the 100GB of Ubuntu 6.06 I currently have now and put 7.04 onto it. 
It scanned the disks, and then came up with the ''Prepare Partitions.'
It showed my Xp partition and my Ubuntu one, along with swap etc.

Now, here i got a little confused. I clicked on the Ubuntu partition:

Device: */dev/sda/5*
Type: *ext3*
Mount point: */media/sda5*

That was the partition i wanted to format, and then install Feisty on. I checked the 'Format' box, then clicked 'Forward.'
A pop box came up saying:

*No root file system is defined, please correct this from the partition menu.*

Now, at this point I didn't really know what to do, so i went back to the first partition options.

The first option (Guided etc, see above) sound promising, because the available space shown was 100GB, the same size as my Ubuntu Partition. I made it 100GB maximum, then clicked 'Forward.'

A box popped up saying:

[I]Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.

Please note that the resize operation may take a long time.[/I]

Now i didn't click 'Continue' and so exited and knew straight away that I would call the great techs at Ubuntu Forums ;)

So, if you haven't realized yet, I want to format my Ubuntu HDD and install Feisty on it, without touching the Xp side of things. So, just need a little advice on whats best to do here.

Sorry for the epic post, just making sure you know everything.

Thx in advance.

---

### Post by forestpixie on 2007-08-27
when you get to the partitioning I think you'll need to edit the existing partition - then you can specify root file system -

[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

maybe it would be better to delete the old partition and build from there with a /, /home and swap - at least that's what I did the first time I reinstalled (although after that I dealt with the partitions separately with a [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") livecd)


so I would in your position get to the partitioning screen - choose manual then making sure I was doing the right drive 

delete partition 

create root partition - 7-8Gb and use as ext3, use / as mount point
create home - remaining space, use as ext3, use /home as mount point
create swap partition - 2 times RAM

Hope that helps and makes some sense :)

---

### Post by abhilash82 on 2007-08-27
There is a screencast available for Live CD install of Ubuntu 7.04 @ [http://www.youtube.com/watch?v=mduooMLIUl8](http://www.youtube.com/watch?v=mduooMLIUl8). 

This must answer most of your queries and if you are planning to upgrade it directly from your current version then read these threads.
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by Magneticgravity on 2007-08-27
Yeh, I used that youtube video the frst time to help me.

But im just a bit stuck on what exactly to do. Theres a few partitions, Win. Xp and Ubuntu, aswell as Swap and stuff :S

What would you guys recommend doing, the simpliest and easiest way would be great.

---

### Post by Pumalite on 2007-08-27
Take a good look at this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Magneticgravity on 2007-08-27
> **forestpixie said:**
> when you get to the partitioning I think you'll need to edit the existing partition - then you can specify root file system -

[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

maybe it would be better to delete the old partition and build from there with a /, /home and swap - at least that's what I did the first time I reinstalled (although after that I dealt with the partitions separately with a [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") livecd)


so I would in your position get to the partitioning screen - choose manual then making sure I was doing the right drive 

delete partition 

create root partition - 7-8Gb and use as ext3, use / as mount point
create home - remaining space, use as ext3, use /home as mount point
create swap partition - 2 times RAM

Hope that helps and makes some sense :)

I sort of understand what you mean. So if I edited the partition, Feisty would simply install on that HDD space or...

---

### Post by forestpixie on 2007-08-27
if you edit the partition with those three partitions - feisty would install to the / partition - once it's told to do so - OR you could just mount that 100Gb partition as / in the same way if you feel safer doing that and the install creates a /home and swap automatically  :D

the problem you had was about not specifying the /root so the install couldn't continue.

I made a seperate home partition so upgrades or reinstalls on root wouldn't affect my /home data

---

### Post by Magneticgravity on 2007-08-27
OK, thx, that mount option sounds best, so what would happen exactly? Would it wipe my 100GB partition and then start new or...?

And how would I do that?

---

### Post by forestpixie on 2007-08-27
go back to my first post look at the image grom psychocats site that basically is what you need to do - then it will do it's thing on your 100Gb partition.

Start the install again carry on as you did before then do the edit partition in manual partitioning.

Check out psychocats installing to a desktop - in my sig.

Edit - if you're really panicking - once you've got to the partitioning part and have made you're choices - move the edit partition/mount as box away from the rest - do a screenshot of whole desktop and post it here - I'm sure someone will look and give you a heads up if you're going to bork your xp

---

### Post by notwen on 2007-08-27
How about you give us a idea of what your current partition is, while in Ubuntu open up a terminal and type 
```
sudo fdisk -l
```

Enter your pass and then copy & paste the output back here, from the info you paste we will know exactly what you're working w/ and which partitions need to go and/or be created when you install Feisty. =]

---

### Post by Magneticgravity on 2007-08-27
will@Will-Desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        5882    47182905    7  HPFS/NTFS
/dev/sda3           19094       19452     2883667+  db  CP/M / CTOS / ...
/dev/sda4            5883       19093   106117357+   5  Extended
/dev/sda5   *        5883       18716   103089073+  83  Linux
/dev/sda6           18717       19093     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
will@Will-Desktop:~$

---

### Post by forestpixie on 2007-08-27
install to /dev/sda5 - tick the format box and make sure you edit it's mount point as /, format /dev/sda6 and make sure to use swap as mount point

that should be fine - good luck :)

Edit - I'm assuming that the install will let you do those things anyway as the sda5 & 6 are logical (I think) partitions inside an extended partition

---

### Post by Magneticgravity on 2007-08-27
OK, im currently doing it now. Ive changed the mount point of /dev/sda5 to / like you said usng edit partition.

If I edit /dev/sda6 the mount point is greyed out...

---

### Post by notwen on 2007-08-27
```

Device Boot Start End Blocks Id System
/dev/sda1 1 8 64228+ de Dell Utility
/dev/sda2 * 9 5882 47182905 7 HPFS/NTFS
/dev/sda3 19094 19452 2883667+ db CP/M / CTOS / ...
/dev/sda4 5883 19093 106117357+ 5 Extended
/dev/sda5 * 5883 18716 103089073+ 83 Linux
/dev/sda6 18717 19093 3028221 82 Linux swap / Solaris

```

From this we can tell 
---
sda1 is your dell restore partition
sda2 is your Windows partition
sda3 is a cocnurrent dos partiton(could be multiple things)
sda4 is an ext partition housing both linux and your swap
  sd4-|
         |-sda5 is your / partition for linux
         |-sda6 is your swap

Ok form here would you like to create a seperate partition for you /home folder?  Lots of people do this to salvage their files in case of the linux system itself goes bad.  I'll try and describe what you'll want to do within gParted for both instances.

If you're wanting to do a simple install with your /home folder within your / partition; simply select the sda4 partition and delete it, apply changes.  You now have unallocated space where your previous sda4 partition was.  After you verify that you do have unallocated space, simply click back and get to the partition selection screen in the Ubuntu install.  Look for the option to install using the largest continuous free space.  Complete the remaining install steps and you should be good to go.

If you're wanting to do the slightly more complex install giving the /home folder it's very own partition.
If you're wanting to do a simple install with your /home folder within your / partition; simply select the sda4 partition and delete it, apply changes.  You now have unallocated space where your previous sda4 partition was.  Select the unallocated space and create a ext3 partition anywhere from 10-15GB and give it / for a mounting point, apply changes.  Now w/ the remaining unallocated space you will need to determine how much swap space you want(general rule of thumb is double your system's RAM, never over 2GB) so create a new ext3 partition and resize it leaving the amount of space for your swap partition in unallocated space, let's give this new partition the /home mounting point, apply changes.  Now w/ the remaining space create a swap partition, apply changes.  Now you should have sda4 as the / partition, sda5 as the /home partition and sda6 as your swap partition.  Be sure right click on the / partition(sda4) and give it the boot flag. Proceed w/ the install. 

Hope this isn't too overwhelming, maybe you can use bits and pieces to accomplish whatever you decide on. Be sure to back up any data you don;t want to lose, because you are indeed wiping all of your Linux partition. Good luck ! =]

---

### Post by Magneticgravity on 2007-08-27
To Notwen:

Thanks alot! Your clear explanations make me understand it a whole lot more (yes im a slight noob when it comes to this).

Anyway, if i install 7.04 using the GUI installer, and i click 'Manual' a list of my Partitions appear, apart from sda4, but if im right thats just a combination of sda5 and sda6?

I would like to perform your first option where i delete the partition, then go back and use guided space so 7.04 can simply install over the new space, however, theres no sda4 in the partition table.

---

### Post by notwen on 2007-08-27
> Anyway, if i install 7.04 using the GUI installer, and i click 'Manual' a list of my Partitions appear, apart from sda4, but if im right thats just a combination of sda5 and sda6?

Correct, if you're using the GUI gParted then an extended partition which houses 2 or more logical partitions is generally outline din a light blue color. Look to see if your sda5 and sda6 are outlined in a light blue box.  This would indicate that they are.

---

### Post by Magneticgravity on 2007-08-27
They are there, but are highlighted in the same colour as every other partition.

Would it be easier to install using the more text based installer, and how?

---

### Post by forestpixie on 2007-08-27
post a screenshot of the partition editor -

---

### Post by Magneticgravity on 2007-08-27
Sure...

---

### Post by notwen on 2007-08-27
This is purely an example screenshot taken from the gParted website.  Notice how hda5 is housed inside of a light blue box and also at the bottom how it's coming up under hda4 from the drop-down arrow?  In your situation sda4 should be housing sda5 and sda6. =]

[IMG]http://gparted.sourceforge.net/screens/gparted_1_big.jpg[/IMG]

---

### Post by Magneticgravity on 2007-08-27
I have GParted as its on the CD, though can i still install Feisty or could i delete the Dapper partition on GParted, then install Feisty?

---

### Post by notwen on 2007-08-27
By your screenshot it appears you have a Feisty cd w/o gParted.

---

### Post by forestpixie on 2007-08-27
ok that's not gparted - to use gparted
open a terminal and enter

gksudo gparted

and it'll look like notwen has described

edit - slow again

---

### Post by notwen on 2007-08-27
> **Magneticgravity said:**
> I have GParted as its on the CD, though can i still install Feisty or could i delete the Dapper partition on GParted, then install Feisty?

Both of these options are do-able.  If you do not need to back up anything I'd simply delete your old / and swap partitions and then install using the "install using the largest continuous free space" option. and save you from having to swap out cds so much. =]

---

### Post by Magneticgravity on 2007-08-27
I knew it wasnt GParted though now I think I know what to do...brb.

---

### Post by Magneticgravity on 2007-08-27
OK, look at this screenshot:

Everything appears where it should be, although sda4 is locked and so if the Linux Swap.

I can however delete sda5, should i do this?

(sorry if im dragging this on, im just making sure i do this right).

---

### Post by forestpixie on 2007-08-27
You might need to unmount them before you delete them - can't remember

> (sorry if im dragging this on, im just making sure i do this right)

been there done that :)

---

### Post by Magneticgravity on 2007-08-27
Yes, though i can only unmount sda5 :confused:

sda4 has its 'unmount' greyed out, and sda6 hasnt even got an 'unmount' option.

---

### Post by notwen on 2007-08-27
sda4 is locked because your swap(sda6) is currently being used by the system.  As for your partition table, all looks correct.  Assign the correct mount points sda5( / ) and sda6(swap) and double check to make sure sda5 has boot flags, after verifying al fo that, proceed w/ your install and let us know how everything turns out. =]

---

### Post by forestpixie on 2007-08-27
That's exactly why I now use the live gparted so i can do all this before I start the install :)

I would go back to [here]("http://ubuntuforums.org/attachment.php?attachmentid=41805&d=1188226294")

delete both sda5 and 6, then create a partition in the empty space you get using that partition editor

Edit - or that :)

---

### Post by Magneticgravity on 2007-08-27
OK, on the installer, ive deleted sda5 and sda6, I now click forward yes? Everything should be alright?

---

### Post by Magneticgravity on 2007-08-27
OK, ive deleted them, now i have free space, I click new partition on the free space?
Shall i make Mount Point "/" ?

---

### Post by notwen on 2007-08-27
Use the slider to leave the appropriate amount of space for your swap and then create your current partition and yes mount point / .  After that select the remaining unallocated space and create your swap partition.

---

### Post by Magneticgravity on 2007-08-27
> **notwen said:**
> Use the slider to leave the appropriate amount of space for your swap and then create your current partition and yes mount point / .  After that select the remaining unallocated space and create your swap partition.

Ahh sorry, im confused again!!

I delete the sda5 and sda6 partitions, yes?

And then go back, use the slider to create a new partition, leaving enough space for a swap?

---

### Post by notwen on 2007-08-27
Yup, you got it.

---

### Post by Magneticgravity on 2007-08-27
Umm this is the final window:

[I] Language: English
 Keyboard layout: United Kingdom
 Name: Will XXXXXXXXXX
 Login name: will
 Location: Europe/London
 Migration Assistant:
 Microsoft Windows XP Home Edition (/dev/sda2):


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #7 of SCSI3 (0,0,0) (sda) as ext3
 partition #8 of SCSI3 (0,0,0) (sda) as swap[/I]

Eek! Is this right?

---

### Post by notwen on 2007-08-27
The partition #7 and #8 kinda puzzle me, but give it a try and then check your output from the "sudo fdisk -l" command again. =]  Hope all turns out right, I'll keep my fingers crossed.

---

### Post by Magneticgravity on 2007-08-27
OK, it didnt work, when i rebooted, i had 3 OS - XP, Ubuntu and then Ubuntu Generic or something. I clicked on the new one, and it failed, something to do with root file.

Im now back on Dapper, and i got this from the terminal:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        5882    47182905    7  HPFS/NTFS
/dev/sda3           19094       19452     2883667+  db  CP/M / CTOS / ...
/dev/sda4            5883       19093   106117357+   5  Extended
/dev/sda5            5883       18303    99771651   83  Linux
/dev/sda6           18717       19093     3028221   82  Linux swap / Solaris
/dev/sda7   *       18304       18690     3108546   83  Linux
/dev/sda8           18691       18716      208813+  82  Linux swap / Solaris

Did something wrong...

---

### Post by Magneticgravity on 2007-08-27
On Disks manager i now have two new partitions:

Partition 7 - /dev/sda7
Swap - /dev/sda8

OK, i need to delete these and start over?

---

### Post by notwen on 2007-08-27
Using the gParted cd.  Lets turn off the swap partition, unmount it, then lets remove the whole sda4 and sda5-sda8 along w/ it.  Then repeat the creating a new / and swap partitions steps and remember to right click your / partition and give it the boot flag.

---

### Post by Magneticgravity on 2007-08-27
OK, well something big went wrong. In the end my GRUB wouldn't work so i had to put it my Xp disc and do some commands.
Ive decided im gonna simply go to the Partitions thing on the Xp disc and simply format them, then using my Feisty LiveCD do it all again from there.

Thanks alot for your time though :D

---

