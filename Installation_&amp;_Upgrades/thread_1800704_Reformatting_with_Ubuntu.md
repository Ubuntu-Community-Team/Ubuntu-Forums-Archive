---
title: "Reformatting with Ubuntu"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by april33 on 2011-07-09
Hi, I'm new here and have  some questions about installing and reformatting with Linux/Ubuntu.   I've lost my admin password on my current Windows OS and would like to install Linux Ubuntu or a similar user-friendly distro of Linux alongside, see how that goes and possibly reformat my PC with Linux as  I was told it would convert NTFS formatted drives to ext3, not delete them. I'm not too sure what thats about, si if anyone could explain it further, I'd really appreciate it.  This is my last resort and I don't want to do something I'll regret.  I'm not too sure what to do at this point, so any info and tips are appreciated.

---

### Post by mörgæs on 2011-07-09
Hi, welcome to the fora.

Which version of Windows are you using?

---

### Post by april33 on 2011-07-09
I am currently running Win7 home premium.

---

### Post by mörgæs on 2011-07-09
First we have to find out how Ubuntu runs on your computer. I would recommend that you try a live boot of Xubuntu 11.04. 

Take a look here:
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by april33 on 2011-08-07
I'm going no run a demo of Mint Xfce because that is what has caught my interest. It based off of ubuntu so It shouldn't be too complicated.

---

### Post by omelette on 2011-08-07
In response to your question about formatting the drive, your NTFS partitioning info gets zapped totally and replaced with a Linux file-system, EXT4 by default were you to install the latest Ubuntu.  That's if you reformat the whole drive, if you are just going to format an already-existing but different partition, then your NTFS partition will remain untouched.

---

### Post by april33 on 2011-08-07
hmm what'll happen to the hard disk and data (backup)drives if they're "converted to EXT4?

---

### Post by -kg- on 2011-08-08
I think I see what you want to accomplish.  You want to "convert" the partition(s) on your hard drive(s) from NTFS to ext3 while leaving the data in those partitions intact.  As far as I know, this can't be done.  There is no facility in GParted (or the KDE Partition Editor) to do that.

Whether there is such a facility in some other third party partition editor or not, I don't know, but you're pretty much going to have to copy what data you want to save to another location, reformat the partition, then move it back onto the partition once it's been reformatted.

And if you're looking to save your Windows partition for possible later reinstallation with the data intact, you'll need to make an image of the partition.  Read at the link in my signature block for further information on partitioning operations.

---

### Post by Guilden_NL on 2011-08-08
Well first, I have to let my inner self ask "WTF?" How can you "lose" your password?

Did you try putting Capslock on and typing your password?

Dependent on how badly you want to recover your data, if you really want to save that data, I would first recommend cracking Windoze Admin password before formatting your HD.  You will not be able to "convert" your data from one file system or another. Think about it - you placed your data under NTFS file system security.  If it were that easy to convert to EXT3 or EXT4 and suddenly have access to that data, it wouldn't be secure.  Rightttttttt?

Second, I have to let my inner self say "WTF?" about not backing up said data on an external HD and/or cloud backup storage facility.

Ubuntu One - Free
Many others 1 GB for free, and very cheap for additional.
I pay ~US$5.00/month with Rackspace for all of our family photos - haven't looked recently but must be a quarter of a Terabyt of data.

Sorry, but someone had to say it. :P

Now, go crack that POS Windoze admin pwd and recover your data.

---

### Post by april33 on 2011-08-08
> **-kg- said:**
> I think I see what you want to accomplish.  You want to "convert" the partition(s) on your hard drive(s) from NTFS to ext3 while leaving the data in those partitions intact.  As far as I know, this can't be done.  There is no facility in GParted (or the KDE Partition Editor) to do that.

Whether there is such a facility in some other third party partition editor or not, I don't know, but you're pretty much going to have to copy what data you want to save to another location, reformat the partition, then move it back onto the partition once it's been reformatted.

And if you're looking to save your Windows partition for possible later reinstallation with the data intact, you'll need to make an image of the partition.  Read at the link in my signature block for further information on partitioning operations.


Just yesterday I was trying to install a Linux Mint demo from a liveusb with no initial success , until I accidentally found BiOS and wiped my drives ( It took less than 5 minutes for BiOS to wipe EVERYTHING ) . I start up the machine again and I am prompted with the option to install factory state windows with one partion , two partions or Entire HD, I chose restoring entire HD. So when It booted up , everything was gone and THere was one big 450 something GB HD instead of two. So I shrink the HD partion, and assign the now unallocated 300GB partion I had made to D:. After fiddling around with Mint (As I had figured out how to load it by then) I installed it on D: and am now trying to get an antivirus on it as I am using Dual booting with windows so I want to be as safe as possible. Everything seems fine so far.

ps. I has backed up important files on an external HD but I didn't know I was going to screw up this much so I can't remeber all the Firefox addons I had installed...

---

### Post by april33 on 2011-08-08
> **Guilden_NL said:**
> Well first, I have to let my inner self ask "WTF?" How can you "lose" your password?

Did you try putting Capslock on and typing your password?

Dependent on how badly you want to recover your data, if you really want to save that data, I would first recommend cracking Windoze Admin password before formatting your HD.  You will not be able to "convert" your data from one file system or another. Think about it - you placed your data under NTFS file system security.  If it were that easy to convert to EXT3 or EXT4 and suddenly have access to that data, it wouldn't be secure.  Rightttttttt?

Second, I have to let my inner self say "WTF?" about not backing up said data on an external HD and/or cloud backup storage facility.

Ubuntu One - Free
Many others 1 GB for free, and very cheap for additional.
I pay ~US$5.00/month with Rackspace for all of our family photos - haven't looked recently but must be a quarter of a Terabyt of data.

Sorry, but someone had to say it. :P

Now, go crack that POS Windoze admin pwd and recover your data.


What are you, 12?

I made a separate admin account seperate from my regular account for security reasons on my WINDOWS OS. I could still acess all my files. I just didn't have admin privileges.

---

### Post by infamous-online on 2011-08-09
> **april33 said:**
> Hi, I'm new here and have  some questions about installing and reformatting with Linux/Ubuntu.   I've lost my admin password on my current Windows OS and would like to install Linux Ubuntu or a similar user-friendly distro of Linux alongside, see how that goes and possibly reformat my PC with Linux as  I was told it would convert NTFS formatted drives to ext3, not delete them. I'm not too sure what thats about, si if anyone could explain it further, I'd really appreciate it.  This is my last resort and I don't want to do something I'll regret.  I'm not too sure what to do at this point, so any info and tips are appreciated.

First off, April be sure to backup all your important files that you have to have onto a flash drive, external drive, dvd or whatever storage option that's available to you. After you're done with that Try a live demo of Mint or Ubuntu to see if you'll like it first, and if you say about a week or two that this is what I want then install the linux os onto the harddrive. Before you install linux first be sure you have the Windows 7 disc just incase you don't like linux so you can go back to that, and then with those files you backed up you can re-install your Windows machine exactly the way you had it before hope this helps.

---

### Post by -kg- on 2011-08-10
OK, I'm having great difficulty in figuring out what you did, and how you did it.

> **april33 said:**
> Just yesterday I was trying to install a Linux Mint demo from a liveusb with no initial success , until I accidentally found BiOS and wiped my drives ( It took less than 5 minutes for BiOS to wipe EVERYTHING ).

I've dealt with computers for many years now (since the early '80s) and I've never run across a machine whose BIOS would wipe a hard drive.  Are you *sure* it was BIOS that did it?  You hit the special key at boot time that took you into BIOS instead of booting up normally?  What is the make and model of your computer?

> **april33 said:**
> I start up the machine again and I am prompted with the option to install factory state windows with one partion , two partions or Entire HD, I chose restoring entire HD.

OK, unless you had the Windows 7 installation/recovery disk, then the hard drive wasn't *entirely* wiped.  You still had a "Recovery" partition...that, or it's loaded into BIOS as Firmware (which I can't see, since Windows 7 requires a LOT of memory space for the Installer).  Again, need the Make and Model of your computer so I can look it up.

> **april33 said:**
> So when It booted up , everything was gone and THere was one big 450 something GB HD instead of two. So I shrink the HD partion, and assign the now unallocated 300GB partion I had made to D:.

No, you couldn't have.  An unallocated space is not a partition, and cannot be "assigned" a Drive designation, whether a Windows Drive letter or a Linux drive designation, like "sda2".  You have to create a partition and format it in order to do that.  An unallocated space cannot be detected by any OS...the only thing that can show you an unallocated space is a partition editor.

> **april33 said:**
> After fiddling around with Mint (As I had figured out how to load it by then) I installed it on D: and am now trying to get an antivirus on it as I am using Dual booting with windows so I want to be as safe as possible. Everything seems fine so far.

At this point, I have a suspicion...did you install Mint using WUBI?  That would explain your "D:" drive designation.  Also, since you had to at some point create and format a partition in order to install Mint, what partition editor did you use to create it?  Is that partition visible in Windows as the "D:" drive?

> **april33 said:**
> ps. I has backed up important files on an external HD but I didn't know I was going to screw up this much so I can't remeber all the Firefox addons I had installed...

That shouldn't be too much of an issue.  Just install them as you remember them.  Actually, I only use a few, but every once in a while I find one that I'd like to try.  They're easy enough to add.

I'm still interested in how you wiped your hard drive with BIOS, though.  I've never heard of that before, and just can't imagine a BIOS that can do that.  If you can, run Gparted and post a screen shot of your hard drive partition set-up here.

You can do that, or open Terminal and run the command,

```
sudo fdisk -l
```

...and post the results here.  That will show us the current set-up of the partitions on your hard drive.  Oh, and give us the Make and Model of your computer so I (or we) can look up the specs (unless you already know them).

Addendum - I have done a bit of research, and the only thing I could find on the subject of partitioning a hard drive with BIOS had to do with Xbox.  Apparently it can be done, but as for reinstalling Windows 7 factory, I'm still a bit bewildered.

---

### Post by april33 on 2011-08-10
> **-kg- said:**
> OK, I'm having great difficulty in figuring out what you did, and how you did it.



I've dealt with computers for many years now (since the early '80s) and I've never run across a machine whose BIOS would wipe a hard drive.  Are you *sure* it was BIOS that did it?  You hit the special key at boot time that took you into BIOS instead of booting up normally?  What is the make and model of your computer?



OK, unless you had the Windows 7 installation/recovery disk, then the hard drive wasn't *entirely* wiped.  You still had a "Recovery" partition...that, or it's loaded into BIOS as Firmware (which I can't see, since Windows 7 requires a LOT of memory space for the Installer).  Again, need the Make and Model of your computer so I can look it up.



No, you couldn't have.  An unallocated space is not a partition, and cannot be "assigned" a Drive designation, whether a Windows Drive letter or a Linux drive designation, like "sda2".  You have to create a partition and format it in order to do that.  An unallocated space cannot be detected by any OS...the only thing that can show you an unallocated space is a partition editor.



At this point, I have a suspicion...did you install Mint using WUBI?  That would explain your "D:" drive designation.  Also, since you had to at some point create and format a partition in order to install Mint, what partition editor did you use to create it?  Is that partition visible in Windows as the "D:" drive?



That shouldn't be too much of an issue.  Just install them as you remember them.  Actually, I only use a few, but every once in a while I find one that I'd like to try.  They're easy enough to add.

I'm still interested in how you wiped your hard drive with BIOS, though.  I've never heard of that before, and just can't imagine a BIOS that can do that.  If you can, run Gparted and post a screen shot of your hard drive partition set-up here.

You can do that, or open Terminal and run the command,

```
sudo fdisk -l
```...and post the results here.  That will show us the current set-up of the partitions on your hard drive.  Oh, and give us the Make and Model of your computer so I (or we) can look up the specs (unless you already know them).

Addendum - I have done a bit of research, and the only thing I could find on the subject of partitioning a hard drive with BIOS had to do with Xbox.  Apparently it can be done, but as for reinstalling Windows 7 factory, I'm still a bit bewildered.

[IMG]http://i962.photobucket.com/albums/ae108/yoseinoyume/Screenshot-08102011-101249AM.png[/IMG]

Here is the hard drive partions. As you can see the "RECOVERY" partion is separate from the OS partion, so It was not affected. I doubt a 3 to 5 min "process" could have wiped my whole drive... But re-installing WINDOWS to factory state must have written over all the previous data, I suppose. 

Anyhow, My laptop is an ASUS ul30vt.

Stats:
4GB of DDR3 RAM, 2 slots, 8GB Max, 
500GB SATA Hard Drive  (5400 RPM),

 It says it runs win 64 bit but I'm pretty sure mine is only 32bit.


I partioned the unallocated space and no It is not visible on windows as "D:" as far as I can tell.

About the BiOS... I pressed "F10" at startup and that opened up a Screen which was I identified as  "BiOs" as that was what it said on the header and a list of paths, so I chose the F: which was where the liveusb was and then it froze for about a minute. Noticing no progress, I shut it down and upon startup I was prompted to install factory state windows .

How do I install the Eset Nod32 av? I'm not too familar withe terminal or how I would go about it. Any help is appreciated, thank you.

---

### Post by -kg- on 2011-08-12
I pulled up the specs on your laptop (nice specs, BTW):

[http://www.asus.com/Notebooks/Superior_Mobility/UL30Vt/#specifications]("http://www.asus.com/Notebooks/Superior_Mobility/UL30Vt/#specifications")

I noticed a little discrepancy between them and your description, BTW.  The specs on that page say that max memory is 4 GB, but that shouldn't alter anything concerning this.

I'm not sure what function in BIOS might have done that.  I do things the more "conventional" ways.  Instead of BIOS, I go into Windows Partition Manager (whatever it's called...it's called different things in different releases) and use that to shrink the Windows partition.  While GParted would shrink a Windows XP and earlier partition with no problem, from Vista on it could cause problems, and it's been recommended that you deal with a Windows Vista and later partition with Windows partition manager.

Then I usually use GParted to create Ubuntu's (or any Linux Distro, for that matter) partitions and load into them.  I have, however, created the partitions before running the Installer...same difference, except you have to use the Manual Partitioning section of the installer in order to install into the partitions you already created.

The only reason I go into BIOS is if there's something I absolutely ***have*** to do in it, and disk partition editing isn't one of those.  But whatever you did, it seems to have worked out well for you, even if you did seemingly have to do backflips to get it accomplished. :P

One thing I noticed; you don't have a swap partition.  With 4GB of RAM you don't particularly need it unless you plan or anticipate needing to hibernate at some point, or plan doing something that requires massive amounts of RAM (like video editing or Computer Assisted Design).  If you do, you seem to have scads of room to create one.

I'm assuming you have it up and operating now.  Good computing!

<edit> Oh, on the Eset Nod32 question, I found the following link that seems pretty good:

[http://ubuntuguide.net/install-eset-nod32-antivirus-4-in-ubuntu-11-04-natty]("http://ubuntuguide.net/install-eset-nod32-antivirus-4-in-ubuntu-11-04-natty")

<Edit2> Oh that's right...you're running Mint.  Since it's based on Ubuntu, it should be virtually the same.  Just watch for the possible differences in Desktop Environment versions and requirements, and you should be good to go.

---

### Post by april33 on 2011-08-12
> **-kg- said:**
> I pulled up the specs on your laptop (nice specs, BTW):

[http://www.asus.com/Notebooks/Superior_Mobility/UL30Vt/#specifications](http://www.asus.com/Notebooks/Superior_Mobility/UL30Vt/#specifications)

I noticed a little discrepancy between them and your description, BTW.  The specs on that page say that max memory is 4 GB, but that shouldn't alter anything concerning this.

I'm not sure what function in BIOS might have done that.  I do things the more "conventional" ways.  Instead of BIOS, I go into Windows Partition Manager (whatever it's called...it's called different things in different releases) and use that to shrink the Windows partition.  While GParted would shrink a Windows XP and earlier partition with no problem, from Vista on it could cause problems, and it's been recommended that you deal with a Windows Vista and later partition with Windows partition manager.

Then I usually use GParted to create Ubuntu's (or any Linux Distro, for that matter) partitions and load into them.  I have, however, created the partitions before running the Installer...same difference, except you have to use the Manual Partitioning section of the installer in order to install into the partitions you already created.

The only reason I go into BIOS is if there's something I absolutely ***have*** to do in it, and disk partition editing isn't one of those.  But whatever you did, it seems to have worked out well for you, even if you did seemingly have to do backflips to get it accomplished. :P

One thing I noticed; you don't have a swap partition.  With 4GB of RAM you don't particularly need it unless you plan or anticipate needing to hibernate at some point, or plan doing something that requires massive amounts of RAM (like video editing or Computer Assisted Design).  If you do, you seem to have scads of room to create one.

I'm assuming you have it up and operating now.  Good computing!

<edit> Oh, on the Eset Nod32 question, I found the following link that seems pretty good:

[http://ubuntuguide.net/install-eset-nod32-antivirus-4-in-ubuntu-11-04-natty](http://ubuntuguide.net/install-eset-nod32-antivirus-4-in-ubuntu-11-04-natty)

<Edit2> Oh that's right...you're running Mint.  Since it's based on Ubuntu, it should be virtually the same.  Just watch for the possible differences in Desktop Environment versions and requirements, and you should be good to go.


Swap Partition? Can you elaborate as to what that is?  I'm runing Linux Mint Debian which is what Ubuntu is based on but Mint  Debian Edition and Ubuntu are not at all similar, I've heard.

I might run some graphic design software, that's about it, but I'm not sure I like this vesion of Mint. Its very buggy.  The startup screen mention it didn't find a BIOS loader and the screen has pixelated and frozen on multiple occasions for no particular reason. Flash has crashed a couple times, the system has muted itself once and I wasn't able to un-mute it. I've never experienced this many issues on any other OS. I'm worried that the installation must not have gone smoothly.

/thanks for your help, anyways.

---

### Post by gordintoronto on 2011-08-12
> **april33 said:**
> Swap Partition? Can you elaborate as to what that is?  I'm runing Linux Mint Debian which is what Ubuntu is based on but Mint  Debian Edition and Ubuntu are not at all similar, I've heard.

I might run some graphic design software, that's about it, but I'm not sure I like this vesion of Mint. Its very buggy.  The startup screen mention it didn't find a BIOS loader and the screen has pixelated and frozen on multiple occasions for no particular reason. Flash has crashed a couple times, the system has muted itself once and I wasn't able to un-mute it. I've never experienced this many issues on any other OS. I'm worried that the installation must not have gone smoothly.

/thanks for your help, anyways.

Windows uses a swap file if you run out of actual memory. Linux uses a swap partition. You have lots of memory, so it's optional on your computer -- unless you like to have 40 tabs open in your Internet browser.

Ubuntu and Linux Mint Debian Edition are still fairly similar. I have had good success with plain old Linux Mint 11, and with Ubuntu 11.04. After installing Ubuntu, install the "restricted extras."

The only reason to have an anti-virus program in Ubuntu or Mint, is to catch Windows viruses, so you don't accidentally send them to your friends as file attachments. It doesn't make your Ubuntu system any safer.

---

### Post by april33 on 2011-08-12
how would I send a virus to a friend "accidentally"?

But still, I'm dual booting so an antivirus is somewhat of a necessary security precaution.

Install ubuntu? I'd assume it'd be a bit more user-friendly but I'd have to uninstall mint then and as buggy as it can be, It has grown on me.

I'll take my complaints to the mint forums then.

Thanks all!

---

### Post by infamous-online on 2011-08-13
> **april33 said:**
> how would I send a virus to a friend "accidentally"?

But still, I'm dual booting so an antivirus is somewhat of a necessary security precaution.

Install ubuntu? I'd assume it'd be a bit more user-friendly but I'd have to uninstall mint then and as buggy as it can be, It has grown on me.

I'll take my complaints to the mint forums then.

Thanks all!

I'd say give Ubuntu a shot to see what you may or may not like about the os. Some hate the new unity interface myself included, but you can easily switch to the classic look if unity is not your cup of tea. So try a live demo of it before making a decision to jump into it all the way :wink:

---

### Post by -kg- on 2011-08-13
Oh, BTW...a swap partition is a Linux thing, not just an Ubuntu one.  As gordintoronto says:

> Windows uses a swap file if you run out of actual memory. Linux uses a swap partition. You have lots of memory, so it's optional on your computer -- unless you like to have 40 tabs open in your Internet browser.

Actually, in the newer versions of Windows (W2K Pro and beyond) it uses what's called a "Paging File", but it's the same difference.  You won't need it unless you have RAM-intensive software, or are using normal software in a RAM-intensive manner (like having "40 tabs open in your browser"), or intend to hibernate (in which the contents of your RAM are saved into the SWAP file for loading when you "wake it up").

Here's a screenshot of my hard drive.  Notice the highlighted line at the bottom, and the graphic of the partition my pointer is pointing to:

---

### Post by april33 on 2011-08-13
> **-kg- said:**
> Oh, BTW...a swap partition is a Linux thing, not just an Ubuntu one.  As gordintoronto says:



Actually, in the newer versions of Windows (W2K Pro and beyond) it uses what's called a "Paging File", but it's the same difference.  You won't need it unless you have RAM-intensive software, or are using normal software in a RAM-intensive manner (like having "40 tabs open in your browser"), or intend to hibernate (in which the contents of your RAM are saved into the SWAP file for loading when you "wake it up").

Here's a screenshot of my hard drive.  Notice the highlighted line at the bottom, and the graphic of the partition my pointer is pointing to:


I cannot even begin to understand why you've partitioned your HDD that way. Do you need the partitions for backup?

I'm going to have someone look at my HDD before I start partitioning drives again. It might need to be replaced so I'll postpone changing anything for a while.

Can you link me to a tutorial that would explain how to create a swap partition? Would shrinking the D: drive be of any use? Would shrinking said drive affect the MINT OS that I've installed?

And concerning the "look" of the OS, I'm particularly picky about that. As long as I am able to use and access my preferred programs, I'm fine. Mint has some minor annoyances here and there, but so far I've been able to get a good amount of functionality out of it. Setting up a network printer has been near impossible, but I'm sure I'll figure that out in time.

---

### Post by gordintoronto on 2011-08-13
> **april33 said:**
> how would I send a virus to a friend "accidentally"?

But still, I'm dual booting so an antivirus is somewhat of a necessary security precaution...

"I downloaded this Windows program, which seems to be really cool, so I am sending you the .zip file attached to this email." And then it turns out that the program is malware.

You certainly need an anti-virus on the Windows side, but not on the Linux side.

---

