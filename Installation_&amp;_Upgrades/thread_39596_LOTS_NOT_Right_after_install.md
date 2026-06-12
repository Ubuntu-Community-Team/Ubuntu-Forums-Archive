---
title: "LOTS NOT Right after install"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by phil54601 on 2005-06-05
Hello All;
    I'm new to any form of Linux.   I installed Ubuntu 5.0.4 this past Friday night 'Expert mode'.  Most everything on my motherboard was Identified correctly.  Most of my add-ons were NOT. 

My serial mouse doesn't work.  The USB mouse, I didn't have plugged-in, works.  I want the serial mouse, actually a 'focus keyboard & trackball combo', the keyboard works.

My Display monitor was selected as generic, 1024x768 @60hz.  I want 85hz.  I found xorgcfg, but couldn't get the monitor info I added to be accepted.

The sound blaster 'Audigy 2ZS' sound card doesn't work.  I had disabled the on-board sound in the Bios, but that seems to be the one Ubuntu picked. 

I also have a partition problem.  I partitioned manually within the installer program.  Where can I find that partition tool? 

 cfdisk gave me a fatal error. 

"Bad logical patition 10: enlarged logical partitions overlap

The display monitor problem is my highest priority, followed by the partiton error.
I did find a listing (I think device manager) that said partition 10:

volume.mount.point  /home

I thing /var followed, I don't remember #9.  Each directory is on it's own partition.

Grub installed correctly, and Windows2000 works ok, except partition magic complains about not being able to identify a partitions type.  I think it's the same problem.
I much prefer GUI methods to the command line, which I haven't used since dos6.22.
Thank You in advance for any help.
Phil

---

### Post by mingus on 2005-06-05
Phil,

First, a few words about character mode.  I appreciate your sentiment.  Here's the deal:  Distros like Ubuntu don't have the GUI syadmin tools of SuSE and Red Hat.  Ubuntu strives to "just work" outa the box, which it does most of the time.  But if it doesn't, it's likely the fix will require terminal mode.  No way around it.  And so . . . 

Re your serial mouse, take a look at:
[http://www.ubuntulinux.org/wiki/SerialMouseHowto](http://www.ubuntulinux.org/wiki/SerialMouseHowto)

Re your monitor:
The reason you can't get your desired refresh rate is probably due to the video card, not the monitor.  Generic usually does fine.  The X-server config will try to read all the supported resolutions from the video card driver, but sometimes it doesn't get it right or the video card driver doesn't return the right values, or the driver isn't found or a proprietary driver must be installed (like ATI cards).  If for example, the color depth is too high, the refresh rate will be reduced to protect the monitor from frying.  Take a look at . . .
[http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto](http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto)
[http://www.ubuntulinux.org/wiki/DebuggingXAutoconfiguration](http://www.ubuntulinux.org/wiki/DebuggingXAutoconfiguration)

Re partitioning:
The installer uses a partitioner called PartMan, which can be re-used from the installer but isn't installed afterward.  Install GParted instead.  BTW, it is highly advisable to not mix partitioners; this is a bit of a black art in any environment.

re the Audigy card:
You first need to determine if it was detected and it's just not a setup tweak needed.  Search the forums, for example -
[http://ubuntuforums.org/showthread.php?t=38385](http://ubuntuforums.org/showthread.php?t=38385)
[http://ubuntuforums.org/showthread.php?t=37635](http://ubuntuforums.org/showthread.php?t=37635)
Start with System/Preferences/Multimedia System Selector, "test" will tell you if a device was found.  Try switching from ESD to ALSA there.
The sound driver is probably snd-emu10k1.  See
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Platinum+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Platinum+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1)
for details.  In a terminal type:  lsmod
You should see the drive listed.  If it isn't, it wasn't loaded.
This may also help; it may be just a matter of installing or configuring the driver.
[http://ubuntuforums.org/showthread.php?t=35452](http://ubuntuforums.org/showthread.php?t=35452)
[http://ubuntuforums.org/showthread.php?t=23329](http://ubuntuforums.org/showthread.php?t=23329)

Let us know how this goes; you'll find a great community in these forums.

---

### Post by phil54601 on 2005-06-06
Hello Mingus;
   I tried to start your suggested corrections, But I'm not in the sudoers file.   I read the man pages for sudo and suders, but didn't understand much.  If I read correctly their are 4 types of  alias.  I'm guessing I need an entry in the cmd_alias part.  How do I do that?  I know I need to use the command 'visudoers', again if I remember right.
I have a home network under windows. The work group is 'home' and my PC is 'PhillipL' .  Windows is not case sensitive.  The caps here are just for clarity.  This info is so a more specific example can be provided.  During install I set the domain to 'home'.  I'm not in a domain.  I don't want to create any name conflicts.
Thanks again
Phil

---

### Post by mingus on 2005-06-06
The command is "visudo".  This runs a protective wrapper program that invokes nano to edit the /etc/sudoers file.

"Sudoers" is a method of enabling you to run as an ordinary user yet also easily use commands requiring root permission.  It is the equiv in Windows of having an Administrator and a User, and switching between them (but a lot easier with sudo).  Windows defaults the main user to "Administrator", a very bad idea.  And even worse idea is to be running ordinarily as root, which is more powerful than Administrator in Windows.

The syntax is to preface a command with "sudo".

To use "visudo" you will probably need to do:
#sudo visudo

If this doesn't work, then try:
#su
<enter root password>
#visudo

There are many postings in the forums re how to setup the sudoers file.  It need not be complicated.  Simply a matter of entering the username and providing the level of permission, which can be thru a "group" association or even by just indicating "ALL", which is less secure but will allow you to sudo into anything you might need to.  You can always change that after you've finished all your setup.

Alternatively, during your setup you can also just run temporarily as root.  If you want to login to Gnome with root, go to System/Administration/Login Screen Setup.

If you have a problem getting in initially as root, see the Starter Guide for various ways to workaround this, depending on the exact situation.

Re the network information:
What is the question?

---

### Post by phil54601 on 2005-06-07
Hello again;
    I fixed the monitor problem yesterday.   It took all day to find a post on how to add 'me' to the sudoers list.  I don't have the internet setup in Ubuntu, So I do all my internet acccess from windows.   I used syntax like:
 phil ALL=(ALL),ALL.
  I had to use su and the root password to be able to do this.  I saw on a few forum posts about security and using sudo and having a root account.  Have I opened some big gaping security holes?  What does each 'ALL' in that command mean,(eg. individual,group)?  

  I fixed the monitor with 'sudo dpkg-reconfigure xserver-xorg'  I didn't make a copy first.  What's the line from the (FixVideoResolutionHowTo) starting with sh -c 'md5 \etc...  actually do?  The first line makes a copy. 

 Ii took 3 trys, but eventully I: selected my i810 chipset, added 1280x1024, entered the vertical & horizontal refresh rate ranges. then specified what I wanted.  After logging back into my account it asked whether to use 'gdm' or 'xserver' settings, I picked xserver.   It worked.  Why did you have me change the settings at the xserver level instead of the gdm level?

 I also tried to fix the mouse while I was there.  It still doesn't work right.  I'll come back to that later.   

You included a link to: DebuggingXautoConfiguration.  I haven't done any of that yet.  Is it still worth while, since I fixed the monitor problem?  If it IS good to go.  Then after 'sudo dpkg-reconfigure xserver-xorg', it says to 'attach:'  does that mean to copy & paste the 'lspci -n', etc. output?   Lastly when all this info is collected, what do I do with it?

The partitioning problem is next.
Thanks for the help.
Phil

---

### Post by mingus on 2005-06-07
> **phil54601]
  Have I opened some big gaping security holes?  What does each 'ALL' in that command mean,(eg. individual,group)?[/QUOTE]

Basically you have given yourself permission to execute any command requiring root priviledge if you can supply your password.  It's not the same as running as root.  More analagous to Windows Adminstrator (which is not as powerful as root said:**
> What's the line from the (FixVideoResolutionHowTo) starting with sh -c 'md5 \etc...  actually do?  The first line makes a copy.

"sh" invokes the bash shell's interactive language; analogous in Windows to doing Run/cmd.  The "-c" tells it to execute the following string.  The "md5sum" command instructs that the file integrity be checked using its md5sum signature.  The following command was what changed things by invoking the built-in configuration program when this X-server is installed.

[/QUOTE]Why did you have me change the settings at the xserver level instead of the gdm level?[/QUOTE]

gdm is just the login manager for gnome.  It starts the X-server.  The X-server controls your mouse, keyboard, video, and monitor.

[/QUOTE] Then after 'sudo dpkg-reconfigure xserver-xorg', it says to 'attach:'  does that mean to copy & paste the 'lspci -n', etc. output?   Lastly when all this info is collected, what do I do with it?[/QUOTE]

Sorry, dunno that one.  I doubt it.  If your video is working right, I'd just leave off with this.

[/QUOTE]The partitioning problem is next.[/QUOTE]

Be very cautious with this.  Know what you are doing.  Even though the partitioner will show you what you are doing before it actually commits the changes, once you've said 'yes', you are committed.  GParted works pretty much like PartitionMagic.  But it wouldn't be a bad idea to post your partition table to this thread for us to take a look first (just $sudo fdisk -l, copy/paste).  

[/QUOTE]Thanks for the help.[/QUOTE]

You're most welcome.  You'll find that the Ubuntu forums is one of the most active, and this community has a wonderfully positive attitude.

---

### Post by phil54601 on 2005-06-07
Hello again;
   I haven't been into Linux all day.  I have been reading forums, and HowTos.
I was looking at the documentation for GParted at ([http://gparted.sourceforge.net/documentation.php)](http://gparted.sourceforge.net/documentation.php)),
 since that's the program you had suggested that I use.   That document refernces this website and the page 'Large-Disk-6':
[http://www.win.tue.nl/~aeb/linux/Large-Disk.html#toc6](http://www.win.tue.nl/~aeb/linux/Large-Disk.html#toc6)

[http://www.win.tue.nl/~aeb/linux/Large-Disk-6.html](http://www.win.tue.nl/~aeb/linux/Large-Disk-6.html)
This page refers to 'partitions and `overlap'' and cfdisk says I have `overlap', this page also states:
[/QUOTE]Use the commands cfdisk -Ps /dev/hdx and cfdisk -Pt /dev/hdx to look at the partition table of /dev/hdx.[/QUOTE]
I think cfdisk just crashes, without arguments, and after reporting the overlap.  My question is: Do I use 'fdisk' or 'cfdisk -Ps' or 'cfdisk -Pt' along with '/dev/hdb', the second physical hard drive?

I understand how important the partition table is, and I don't want to mess it up.  I want to fix the problem, so that Linux and partition magic6.0 both will work.  I'll post a partition table later tonight or tomorrow morning when I'm sure I can do it without messing things up.
Thanks
Phil

---

### Post by oritpro on 2005-06-07
phil54601

the Linux Audigy driver likes to default to the digital output when first installed, if your speakers are attached to the analog output then you won't hear any sound. I believe this can be changed in the alsa mixer control panel.

these links should help.

[http://www.ubuntuforums.org/showthread.php?t=30795&highlight=audigy](http://www.ubuntuforums.org/showthread.php?t=30795&highlight=audigy)
[http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy](http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy)

Also see [http://ubuntuguide.org](http://ubuntuguide.org) for another sound fix you'll probably need. This site is an awesome starter guide for Linux newbies as well.

---

### Post by mingus on 2005-06-08
Phil,

A rule of thumb in partitioning is (a) try to use a partitioner native to the OS, and (b) do not mix partitioners.  Certain combinations are especially dangerous, like using Windows Disk Manager (awful) with anything else, including DOS fdisk.

In your first post it sounded like you had created partitions on this disk before with PartitionMagic, then created the Ubuntu partitions with the installer, and created a different partition for each primary Ubuntu directory (if so, why?)?

Post the partition table here.

And what filesystem did you use for each partition?

Use GParted now.  It uses the same underlying code as does the installer's partitioner, which is different from cfdisk.  Use fdisk only to query.

---

### Post by phil54601 on 2005-06-08
Hello;
> 
In your first post it sounded like you had created partitions on this disk before with PartitionMagic, then created the Ubuntu partitions with the installer, and created a different partition for each primary Ubuntu directory (if so, why?)?.
Essentially that is correct.  The disk I installed Ubuntu on has been in my PC for a couple years.  It was installed shortly after getting this Dell PC. It's 120GB, and was partitioned for windows2000 mainly as NTFS with a couple Fat32 partitions, as a data disk.   I used partition magic to move & shink partitons to make room for Ubuntu.  The extended patition was left large for all the windows stuff at the end, and the Ubuntu non-boot partitions at the beginning.  The primary boot patition is at the start of the physical drive.  With the exception of the extended partition and windows partitions, I created all other partitions with the installer.  I used a seperate partition for each directory because my reference book said it made backups easier and that there was less chance of corruption from a rogue program.  I've had my system hosed by rogue programs a few times in windows.
The reference book is "Special Edition using Linux 4th ed." published by Que, 1999. It covers Linux in general, and red hat 5.1 and caldera1.2 specifically.

As I said earlier I only have the internet thru windows, and I don't have any way to copy between windows and Linux, unless my USB flash drive will work in Linux?

I haven't tried the USB drive in Ubuntu yet.  I'll do that as soon as I post this.

If I'll need to do anything special to get the USB drive to work please explain, if not then disregard this question?

I need to get this whole mess fixed.  If that means chucking Ubuntu for now, repatitioning and reinstalling then OK.  I'd prefer to create a backup some way, rather than a reinstall..
Thanks
Phil

---

### Post by phil54601 on 2005-06-08
Hello Mingus;
The USB drive worked perfectly!  In windows there is a taskbar button to stop the USB drive before removing it.  Does Ubuntu have anything similar?

phil@phillipl:~$ sudo fdisk /dev/hdb -l

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         608     4883728+  83  Linux
/dev/hdb2             609       14593   112334512+   f  W95 Ext'd (LBA)
/dev/hdb5            2551        3002     3630658+   7  HPFS/NTFS
/dev/hdb6            3003        7376    35134123+   7  HPFS/NTFS
/dev/hdb7            7377       10653    26322471    7  HPFS/NTFS
/dev/hdb8           10654       12043    11165143+   7  HPFS/NTFS
/dev/hdb9           12044       14593    20482843+   b  W95 FAT32
/dev/hdb10            609         644      289107   83  Linux
/dev/hdb11            645         826     1461883+  83  Linux
/dev/hdb12            827        1191     2931831   83  Linux
/dev/hdb13           1192        1203       96358+  83  Linux
/dev/hdb14           1210        1331      979933+  83  Linux

Partition table entries are not in disk order

Does it make any difference that I used a terminal window, and not F1?

The partitions 10 - 14 are at the beginning of the extended partition, and 5 - 9 are at the end.  The swap partition was created with the installer in unallocated space on the first physical hard disk.  It is in the middle of the extended partition, I think the extended partition was modified with partition magic.
If you have any questions about the partition table, just ask.

Thanks
Phil

---

### Post by mingus on 2005-06-08
Re USB flash:  I use one on Windows all the time.  The icon will appear whenever any USB device is plugged in, and is not necessary to unplug.  Neither so in Ubuntu.  This is handled by what is called "hotplug" in Linux.

Partitions are numbered in the table in the order in which they are created, not physical placement on disk.

Now, as far as the cfdisk message, you're in luck.  It's just a cfdisk quirk.  See:
[http://lists.debian.org/debian-boot/2003/12/msg01637.html](http://lists.debian.org/debian-boot/2003/12/msg01637.html)

The only thing I noticed off-hand unusual about your setup is the gap between 14 and 5.  But that doesn't necessarily in itself mean a problem.  What matters most is that the table addresses are correct.

You don't indicate the mount points, but I'm guessing they are /, /boot, /home, /var, /opt, and /usr - a traditional layout recommended by SuSE & RH for the reasons you cite. The flipside to this is that it (a) allocates space that is/may not be used, so it is less real estate efficient, and (b) if any partition becomes too small, you will need to use a procedure to create a new one to swap into its place (you delete the prev then), and this requires extra disk space not now on that drive.  It's not possible to know if this would ever even come up, depends on how much you use of each partition.  But it's for these reasons that typically users just do /, /boot, /home, and of course, swap.  The extra partitions will also slow your boot a tad.

Hopefully you made all those partitions journaled filesystems (prob ext3 or reiserfs), except for /boot which is best left ext2 (but no big deal if not).

Bottom line, at the moment there are no indications of a problem.  So it's best to leave that table alone.  If you are nervous about it, use a lot of what's in Ubuntu which will exercise files all over the disk and probably reveal any problem.  Also look at dmesg which will show any blips the kernel found when mounting.

PS.  Get a newer book.  Unix fundamentals the same, but an awful lot has changed since RH5.  I prefer google and linux websites.

---

### Post by phil54601 on 2005-06-08
Hello Mingus;
   I had seen a similar post about cfdisk before, but didn't really understand it.  This link that I provided earlier seems to address my problem with partition magic:

[http://www.win.tue.nl/~aeb/linux/Large-Disk-6.html](http://www.win.tue.nl/~aeb/linux/Large-Disk-6.html)

They talk about partitions starting or ending 'ON' a cyinder boundery which linux doesn't care about, but dos & partition magic do.  They also mentioned type 85 extended partitions that dos doesn't see.

I also think I may have miss partitioned my drive.  The mount points are:
/dev/hdb1    /
/dev/hdb10    /Home
/dev/hdb11    /usr 
/dev/hdb12    /var
/dev/hdb13    /usr/local              (error: shouldn't /local be a subdirectory of usr?)
/dev/hdb14    /opt
/dev/hdb2    I think is the extended patition
hdb5 to hdb9 are the windows partitions, no 'mount.point' listed under the ''advanced' tab in device manager.

Bigger ERROR: it also appears that 'boot' and '/' are the same partition.  Thats NOT what I intended, or I didn't know any better.
All Linux partitions are ext3.

[/QUOTE]The only thing I noticed off-hand unusual about your setup is the gap between 14 and 5. But that doesn't necessarily in itself mean a problem. What matters most is that the table addresses are correct.[QUOTE/] 

That free space was for a fat32 partition that was to be shared between windows and linux that failed during install.  I kept trying to allocate more space than was there, finally realized what I was doing then used 'max' as the dialog suggested.
After reboot I had 2 partitions that failed to mount.  I don't know which they are unless one was the seperate boot partition I wanted.  
Doesn't '/boot' have to be the first partition on the disk, but under 'root' in the file tree?

I can't find/locate GParted in my linux system.  Where can I get it?  I do have the 3 disk set for RedHat linux 9. 
 I think I need to fix that free space that was earmarked as sharing space between windows and linux, to see if that will fix the partition magic problem.
I also don't really understand that cylinder thing mentioned in that link above, but believe it is a factor with patition magic.
Thanks
Phil

---

### Post by phil54601 on 2005-06-08
Hello oritpro;
   I have been concentrating on the hard drive, but I did look at the sound.  On the desktop I bring up the volume control.  The title bar says:
volume control: Sound Blaster Audigy(alsamixer)
The "Audigy Analog/Digital Output Jack" was NOT selected,  I selected it, but no change, still no sound from a CD.
The first link you provided has my question, but I don't understand the answer:

[/QUOTE]If you are using alsamixergui (sudo apt-get install alsamixergui) you just click with your mouse on the un highlighted icon and it will go blue[QUOTE/]

I tried the sudo command, but got an error about not finding 'alsamixergui'.  Isn't IT already installed.  I don't remember seeing a 'un highlighted icon' in the mixer settings dialog?  Is there one?  
The other link you provided:
[http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy](http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy)
seems to be wrong for me.   Why switch to or add " kmix"?  The whole post was VERY confusing to me.
Thanks
Phil

---

### Post by phil54601 on 2005-06-08
This is actually a follow up for mingus.  
I found the gparted program (gparted_0.0.8-1_i386.deb ) and libary (libparted1.6-12_1.6.20-0.exp.1_i386.deb) and down loaded them.

As soon as I understand how to partition and comply with the cylinder boundry thing I'll be set.
Thanks
Phil

---

### Post by mingus on 2005-06-08
omigosh . . .

The webpage you found explains re my earlier post to use a partitioner native to the OS and also not to mix partitioners.  Pls, do not get into geometries and explicitly stating cylinder boundaries.  What you have in the partition table may be fine.  Where trouble arises usually is with files near the boundaries when the boundaries have been calculated differently.  In your setup, the risky point is between hdb14 and hdb5, and there is a gap there which for this purpose is good.

About the partitions and mount points . . .  

You currently do not have a /boot partition, it is inside /.   Yes, a primary reason that /boot has traditionally been separate is because of the 1024 cyclinder boundary limitation.  This is a very lengthy topic, not for here.  What's relevant now is (a) the size of hdb1 and (b) the size of /, given that you have also separated /var, /opt, and /usr, making / much smaller.  Looks like the partition is within the 1024, and that it's size is ample.

I had come up with a nifty procedure to fix what is defintely a problem with the hdb13 partition having /usr/local.  And then I took a closer look at the sizes of hdb10, hdb11, hdb14 - they all look much too small, especially hdb10 for /home.  Question is, do you want to try to resize these or just start from scratch?  You can post back the sizes and I'll double-check the calcs.  However, if it's not too big a pain, you probably should consider a re-install.

---

### Post by phil54601 on 2005-06-09
Hello Mingus;
[/QUOTE]
Pls, do not get into geometries and explicitly stating cylinder boundaries.[QUOTE/]
I agree 100%.  I just want things right when I do partition.

You read my mind.  Re-install is the way to go and fix the partiton sizes & allocations all at the same time.
I figured 5GB for these partitions + 10GB to 15GB for unfore seen storage.
The pattition sizes I wanted are:
var     2-3 GB (3GB is what I actually used)
root    100MB
usr     1.5GB
home  200MB
tmp    50MB
opt     (I don't have it in my notes probably 100MB)

Notice NO 100MB boot partition!

My swap partition may be too small too.  I read that the rule of thumb is 2x or 2.5 x the ram size, unless there is over (I think) 200MB of ram, then swap equal to ram..   I have 384 MB of ram and a swap partition size (I think) of 500MB.  I didn't expect to get it perfect the first time.
I want to use GParted to delete the current partitions, but I'm getting a lot of dependency errors when installing.  I think I used some thing like this to insatll.

sudo bpkg -i gparted_0.0.8-1_i386.deb.   GParted is verion 0.0.8.  Is that too new,unstable, buggy?

I searched the news groups all day yesterday, but coudn;t find where is the correct place to store debs that I down load? (/root/downloads)?.

How do I add a(that) directory to synaptic repositories?   I saw this syntax, but am confused.

deb file:// root download

That looks wrong, shouldn't it be:

deb files:///root/download?

Some of these questions are putting the cart ahead of the horse.  I just want to learn as much as possible as fast as possible.
Thanks
Phil

---

### Post by phil54601 on 2005-06-09
Follow up for Mingus
   Forget about the gparted question:
GParted is verion 0.0.8. Is that too new,unstable, buggy?
I found the answer.  version 1.6.22 is current and stable.
thanks
Phil

---

### Post by mingus on 2005-06-09
Allow me to make this suggestion:  Keep the partitioning simple.  What you read earlier about separate partitions having greater security and sysadmin advantages, is true for mission-critical situations; I have a SuSE SOHO setup this way.  For consumers this is over-kill, and security is better served with the suggestions in the Starter Guide.  And separate partitions are only useful for recovery with a rigorous and sophisticated backup scheme.

A better fit for you would be:  / (the root), /boot, /home, and swap.  Before offering a suggestion, what is on those 4 NTFS partitions, and why are there so many?

BTW, the *proportionate* use of swap decreases as the size of RAM goes up; not linear.  500MB should do just fine.  If for some reason you need more later, easy to do.  Also, while putting it on the hda1 drive might improve performance, if the drives are on the same channel you won't notice it.  Keep this simple, too.

As far as deb's are concerned, for now it would be wise to stay with the ubuntu main, restricited, universe, and backports repositories.  Stay with Synaptic for now.  Installing deb's built for another Debian derivative *quite likely* will get you in trouble.  Even packages built for one release of Ubuntu may not work with another.

---

### Post by mingus on 2005-06-09
I just noticed your remark re different versions of GParted.  Ahem . . . take a closer look:

[http://sourceforge.net/project/showfiles.php?group_id=115843](http://sourceforge.net/project/showfiles.php?group_id=115843)

GParted is at version 0.8, this is the libparted with a gnome wrapper
libparted is at 2.6.20, this is the core code used by GParted, QTParted, & Partman.

Be careful to know what you're doing first.

---

### Post by phil54601 on 2005-06-09
Hello Mingus;
Remember I'm coming from Win2000. I've used it for about 4 years, and have reinstalled it 5 or 6 times.
> 
What you read earlier about separate partitions having greater security and sysadmin advantages, is true for mission-critical situations; ... For consumers this is over-kill, ... And separate partitions are only useful for recovery with a rigorous and sophisticated backup scheme.
Mission-critical is how I look at my system.
> ... what is on those 4 NTFS partitions, and why are there so many?
Windows is on the 'C' drive ALL other 'programs' are on the 'D' drive(both disk 1), and all 'data' goes on other partitions. All those other partitions are for data - or what ever. Large partitions take forever to defrag. or back up, the drives are 80GB and 120GB.

I have started using drive image to do an image of each partition, and save them to another partition. I have a second install of Win2000, I use only for the backups & restores.

I like to get a system set up, do a back up of this base, then another back up any time anything SIGNIFICANT changes, like installing a new program. Data backups generally means temporarily copy the directory of my data to another partition. Once I learn how to back up in Linux, I'll probably use a similar schedule.

> ... while putting it[swap] on the hda1 drive might improve performance, if the drives are on the same channel you won't notice it. Keep this simple, too.
Both drives are on the primary channel, master & slave. Swap on master, and Linux on slave.

> As far as deb's are concerned, for now it would be wise to stay with the ubuntu main, restricited, universe, and backports repositories. Stay with Synaptic for now. Installing deb's built for another Debian derivative *quite likely* will get you in trouble. Even packages built for one release of Ubuntu may not work with another. I don't have internet set up on Linux.  I MUST down load in windows. I then copy the deb to a linux partition.  My first try at setting up a shared partition for linux & windows didn't work(all the free space), and I don't trust sharing one of my regular win2000 partitions!  I don't know how to point synaptic to my local directory.

Any more suggestions or guide lines would be GREATLY welcomed, before I start over.  I've had too many BAD experiences with windows, which is also a reason why I'm looking into Linux.

Thanks
Phil

---

### Post by mingus on 2005-06-09
Save me the time doing the math . . . what are the sizes hdb10-14 and hdb1?  And is hdb9 expendable?

Re the packages, have you found:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)
[http://packages.ubuntu.com/hoary/allpackages](http://packages.ubuntu.com/hoary/allpackages)

Use these to find the packages you need to download separately.

---

### Post by phil54601 on 2005-06-09
Hello Mingus;
I can't get partition magic to run.  It halts after an error about NOT being able to determine a partitions drive letter.  I just figured out why!
I run verison 6.0 published in 2000.  It supports  Ext2, and extendedX which linux Kernel before ver 2.2 doesn't support.  But unless extendedX & Ext3 are the same then it doesn't support Ext3.  ALL my linux partitions must be Ext2!  A new version of partition magic is a NO-NO.

Windows is my primary system.  It & partition magic MUST run.

The sizes are:
volume.num.blocks------578214------hdb10------4.66GB------/home
volume.num.blocks------2923767------hdb11------2.82MB------/usr
volume.num.blocks------5863662------hdb12------1.39GB------/var
volume.num.blocks------192717------hdb13------2.80GB------/usr/local
volume.num.blocks------1959867------hdb14------94MB------/opt
The next to last column is from win2k disk manager.
I hope that is what you wanted.
If the info above is ok then disregard this:  Not being able to run partition magic, how do I coorelate between linux & windows, to know which drive letter is partition hdb9?

1) Can I & should I delete all the linux partitons from within linux or using win2k disk manager?
2) shrink my windows extended partition with parition magic.
3) then reinstall.
4) during reinstall create a 500MB boot partition.
5) create another extended partition, using the rest of the free space.
6) Unless linux is far easier to back up than windows the seperate partitions is the way for me to go.  create the / 'root', /home, /var, /usr, and /tmp partitions, no /opt, or is it needed.   'usr' will end up 5.62GB, with a 2.8GB subdirectory /local.
7) Use half this free space (10GB) for my fat32 sharing partition.
Thanks
Phil

---

### Post by mingus on 2005-06-09
Don't confuse partitioning with formatting (creating a filesystem).  A partition of type "linux" (remember 83 from cfdisk?) doesn't become ext3 until its formatted as such, a seperate step.  

If PM is unable to read a drive letter, the problem has nothing to do with the linux partitions.  Drive lettering is strictly a Windows thing.  Windows only assigns letters to the partitions it recognizes, FAT32 and NTFS.  As I recall, if PM creates a Windows partition, it will assign it a letter using the same logic as Windows does.  Drive letters can be changed in Windows.  Out of sync drive letters can sometimes be remedied by PM's Drive Mappers.  Re the hdb9 FAT partition, if Windows sees it (like in Explorer) it will have a letter assigned.  I cannot speak to why PM might choke on it, esp if Windows does not.  It is at the end of the drive and should have no bearing on the linux partitioning.  Beyond this, I've no suggestions.

If you must do something to alter the hdb9 partition, and since it follows the NTFS partitions (safer), if would be preferable to use whatever tool created it.  But with all you've got going on here, don't use either DM or PM on the linux partitions.    

Before continuing, you didn't provide the size of hdb1.  Need that.

---

### Post by mingus on 2005-06-09
Forgot . . . you probably already have, but if not, take a look at -

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition)

---

### Post by phil54601 on 2005-06-09
Hello;
[QUOTE=mingus]Don't confuse partitioning with formatting (creating a filesystem).  A partition of type "linux" (remember 83 from cfdisk?) doesn't become ext3 until its formatted as such, a seperate step.[/QUOTE]  True, but the installer partitions & formats, prior to copying files.  The installer choked on some of my partitions because, as I said earlier it displayed a message that 2 partitions weren't mounted, when it rebooted.  One of those partitions was probably the fat32 partition.
[QUOTE=mingus]If PM is unable to read a drive letter, the problem has nothing to do with the linux partitions.  Drive lettering is strictly a Windows thing.  Windows only assigns letters to the partitions it recognizes, FAT32 and NTFS.[/QUOTE]
Again true, but that one fat32 (possibly corrupt) partition is in the part of the extended partiton used by linux and partitioned by BOTH PM & the ubuntu installer.
[QUOTE=mingus]Re the hdb9 FAT partition, if Windows sees it (like in Explorer) it will have a letter assigned.[/QUOTE] hdb9 isn't the problem.  I think the problem is in the first part of the extended partition (created by PM) where I tried to create a fat32 sharable partition using the installer. DM shows partitions hdb10 to hdb14, about 47 MB free space another 957MB partition detected as fat32, but listed as '0' size under properties, then another partition of 9.34GB free space.   That '0' size fat32 partition I think is the trouble!  DM can't give a consistent size for it.  The free space, fat32 partition, and last free space were all supposed to be a single 10GB fat32 partition.
[QUOTE=mingus]If you must do something to alter the hdb9 partition, and since it follows the NTFS partitions (safer), if would be preferable to use whatever tool created it.  But with all you've got going on here, don't use either DM or PM on the linux partitions.[/QUOTE]
I'd prefer NOT to do any thing with hdb9.  I thinks it's my second install of windows and is at the opposite end of the disk from linux.  Hdb5 is the closest to linux.  
[QUOTE=mingus]Before continuing, you didn't provide the size of hdb1.  Need that.[/QUOTE]
I don't think there is a hdb1. I think hdb10 is the first partition on the disk, but I'll have to go back into linux to be sure..

Linux in in the first 20GB of hdb.  I think deleting the whole first 20GB on hdb, and reinstalling will cure the problems.  Of that first 20 GB, 5GB is a primary partition, the next 15GB are in the extended partition created with PM for win2k.  That last sentence is significant.


Possibly even deleting that bad patition from linux & recreating it from linux would solve the problem with PM.  The BEST solution it to delete that 20GB & start over.
Phil

---

### Post by mingus on 2005-06-10
It's time to step back a bit.  This has become very time-consuming.  And IMHO, over-complicated. 

The ref to the difference between partitioning and formatting were in response to your remarks about PM not being able to determine a drive letter and its not supporting ext3.  The former is a Windows problem and the latter is not germaine. 

Whatever the msg from the Ubuntu installer, it did not fail because partitions were not mounted.  It can't do this operation if they were mounted, just as PM cannot.  

The remarks re hdb9 were only in response to the drive letter question:  "how do I coorelate between linux & windows, to know which drive letter is partition hdb9?"  The linux partitions have no bearing on how Windows assigns or sees drive letters.  

In all honesty, I can't follow the description of what DM sees with hdb10-14.  I think I follow your meaning about hdb1 and hdb10, although the language is inaccurate.  And "the next 15GB are in the extended created for win2K" is confusing; hdb1 is physically followed on the disk by 5 linux logicals, and then 5 Windows logicals.   

Here's one last shot at this, trying to simply:

There are two alternatives:  The first is to backup the NTFS partitions, wipe the disk by deleting the table, rebuild the table with PM (not DM!) specifying the desired linux partitions as ext2 (this is the equiv of linux 83; do not format), restoring the NTFS data to the new NTFS partitions, and then using the installer's partitioner to format the desired partitions and assign their mount points.  Depending on what you used for the backup (files vs image), you can do as you want with the NTFS partitioning.  For Ubuntu, you will want a small (50MB) primary as hdb1 mounted /boot.  What follows depends on if you want /var, /usr/ and /opt in their own partitions.  This is not what the Ubuntu and Debian teams recommend for single-user workstations, but that is your decision.   /usr would probably be fine with 5GB, /var with 2GB, /opt with 3GB.  The root partition (/) is fairly small if these other three are separated, 1 GB would be plenty.  Obviously, if you combined the four, it would be 10GB.  /home is for user programs and data files, and can grow considerably.  Whether you allocate a large space for /home vs adding specialized partitions (music, video, etc) is a personal choice.  For performance considerations, you will probably do best putting the program file partitions (whether just / or the separated partitions) adjacent at the front of the drive, followed by the swap a little closer to the center and between the executables and the data on /home (reduces head movement).

Alternative 2 is to try to work with what you have, 2550 cylinders.  You use PM to delete hdb1 and hdb10-14.  Still, you are constrained by the extended boundary at cyclinder 609.  How you approach this now is again determined by whether you use one (/) partition for the programs or four.  3 primaries can be put in the 5GB before hdb2.  Ample for /boot, swap, and either /var or /opt (but obviously not /usr, nor / if you combine it with the other 3).  Then put the remaining program partitions in logicals starting at 609.  Fill the remaining space up to about cylinder 2500 with /home.  Leave 2500-2550 as dead space, just in case of a boundary overlap. 

My preference would be the first option.  That's about all I can offer.  Best of luck.

---

### Post by mingus on 2005-06-10
P.S. - PM can work fine with Linux.  In fact, SuSE once bundled PM with its product.  Just try to stick with 1 partitioner.  And do not use DM or Windows fdisk!  And while PM is fine for formatting FAT and NTFS, don't let it format the Linux partitions; use Linux to do that (GParted doesn't actually do the formatting either, it calls a Unix tool specific to each filesystem).

---

### Post by phil54601 on 2005-06-10
Hello Mingus;
I agree that this has gotten way too complicated. I don't folllow IMHO?

Your comments at the bottom half were excellent! I'll try your simple (first) approach. 

[Quote]
Whether you allocate a large space for /home vs adding specialized partitions (music, video, etc) is a personal choice. For performance considerations, you will probably do best putting the program file partitions (whether just / or the separated partitions) adjacent at the front of the drive, followed by the swap a little closer to the center and between the executables and the data on /home (reduces head movement).[/Quote:]

**** You seem to be reccomending seperate partitions for /home subdirectories, true?  One partition with numerous directories would be fine.  I just want it to work.

I did some searching on google yesterday about the error 117 PM problem. There were lots of posts, (even a couple from ubuntu forums) but few solutions.
I also ran a partiton info program for NT from Symantec. I know little or nothing about disk geometry and partitions, so these errors are way beyond my understanding.
"
Warning #113: EPBR partition starting at 9767521 overlaps previous EPBR partition.
Linux Ext3 Log 282.3 9,767,521 0 9,767,646 578,214

Info: Logical starting at 9767646 is not one head away from EPBR.
Warning #113: Logical starting at 40965813 overlaps enclosing extended volume.
Error #114: Logical starting at 40965813 is not one head away from EPBR.

Info: Partition didn't begin on head boundary.
ucBeginSector expected to be 1, not 2.
Error #120: Logical Drive chain extends toward start of drive.
"
If these errors help you understand my problem fine, if not then disregard.

I just want to understand this next paragraph!
I think the problem about hdb10 - hdb14 is in trying to use linux terminology for windows displays. I just looked in linux divice manager again.  There is a hdb1 '/', minor 65.  Minor 66 thru 73 are hdb3, hdb5, hdb8, hdb9, how they relate to my winows partitions I have no idea.  The hdb10 - hdb14 are the other linux partitions, and are labeled.  This sequence can't be the physical layout on the disk can it?  It doesn't agree with either DM or PM, and both DM & PM agreed before linux.

Like most windows users I just want 'it' to install and WORK! 

If the repartitoning and reinstall that you suggest doesn't fix these errors either alone or with minimal tweaking, then linux will be gone.
Thanks for all the help
Sorry it has taken so much of your time!
Phil

---

### Post by mingus on 2005-06-10
Thank you for the constructive response.

If you are going to use approach #1 - backup/wipe/build partitions/format/restore NTFS files/install Ubuntu formatting those partitions at that time - then all your questions and problems about the current table and PM's behavior, should just take care of themselves.  Working with a clean slate and a reliable tool like PM to build the table, carefully planned, and everything should be fine.  Besides, you never really wanted to know the differences between OS's and tools in calculating drive geometries? ;-)   

Regarding the list of volumes in Ubuntu Device Manager, no mystery there, they are simply sorted.  The name of the drive (/dev/hdb*) is a string, or alphanumeric.  1-10-11-12-13-14-2-3-4-etc, see?  If you sorted this column in Excel, it would do it the same.  As far as the rest of the hexidecimal values, minors, blocks, etc. - don't go there.

You do need to get the hang of partition identification in linux vs Windows.  Linux is very simple; it uses the partition table with a pre-defined prefix for type of drive.; hda for master on first IDE channel, hdb for the slave, sda master first SATA, etc.  People do sometimes get confused about the numbering; these are not so much numbers as they are ID's.  *Usually* the numbers are the same as the physical sequence on the disk, but this is just coincidence.  The numbering is the sequence in which the partitions were *created*.   So your 10-14 are physically before 5-9, not after.  That's why in working a problem like this one must look at the cylinders  not just the partition IDs.

With Windows, altogether different.  Windows writes a letter into the file label on each partition it uses; ignoring all others.  By default it does that in alpha sequence, but not always and the user can change the letter anyway.  So if you had e.g., a drive with C, unallocated, D, E and then created a new partition in the unallocated space, it would be F.   Windows drive lettering often does not bear any resemblance to how the drive is physically laid out.  Unfortunately, in Windows the drive letter is used in paths everywhere especially in the Registry.  Change a drive letter and ouch!  That what PM's Drive Mapper is intended for.

Whew!

Regarding /home subdirectories, no that is not what I was saying at all.  You can do it either way.  Some users like their data physically segregated, like your separate hdb5-8.  That's one decision.  A different decision is where to mount the partitions.  Some like distinct top-level directories (/data, /software, /music) and some prefer subdirectories (/home/data, /home/software, /home/music).  On the other hand, if you put all the data on a single partition, then you can organize it with subdirectories, but in that case they are *not* mount points.  Concept is basically the same in W$, with most users going the latter route.

Hopefully, your questions are answered.  Go down the start-fresh route, plan ahead, have a *proven* backup, and you'll do fine.

Best of luck.

---

### Post by phil54601 on 2005-06-12
Hello Mingus;
   Your last post was EXCELLENT.  That post is what I have been looking for since about post #10 or #12. 

 [Quote]   then all your questions and problems about the current table and PM's behavior, should just take care of themselves.[Quote]

In fact that one line is what I have been waiting to see.  
In all your previous posts, prior to #30 you seemed to ignore my PM problem. At that time PM wouldn't run at all!  Not a windows version or from a dos prompt.   This POS 'dell' computer doesn't have a floppy drive, and won't recognize my USB drive as a bootable, even though it supports bootable USB drives.  

This is all just academic now anyway.  I deleted each linux partion with DM, the only thing that would work.  After deleting @ partition I tried to run PM.  NO luck, still errors 113, 114 117.  Even after deleting all the linux partitions on the slave drive it wouldn't run.  Now error #185, not explained in my manual.  Finally after deleting the swap partition on the primary drive, PM would run.  

For the benefit of any newbies following this thread.  I used the win2000 cd to repair my drive 'C' installation, then the console recovery with command 'fixmbr'  That removed grub from the master boot record, and returned my PC to the condition prior to the linux install.

Thank You for all the time you have invested.  I HAVE learned a lot about linux in general.  What I have learned about Ubuntu specifically is that it's NOT for me.  There are just too many hardware compatability problems.  I have been looking at the Xandros reviews, hopfully not a dirty word or topic here.  I have a broadcom modem and network, which seem to be problems with ubuntu, 'ndiswrapper'  where as xandros has a broadcom driver.
I believe this is an excellent forum with very knowledgable people.  It's just that I'm not a hacker, and ubuntu seems to be hacker oriented.  
Feel free to respond to my observations, but I probably won't see them.  I don't intend to visit this forum any more.
Good by, & thanks for ALL the help.
Phil

---

### Post by mingus on 2005-06-12
good grief, what a trip!

---

### Post by oritpro on 2005-06-13
I have another system with an Audigy 2 that I installed Ubuntu on a few weeks ago and ran into the no sound problem.  I fixed it, but don't remember exactly how.  This system had an ATI card that I just replaced with an Nvidia and will be re-installing Ubuntu again.  I'll take note of the fix and get back to you on it.

> **phil54601]Hello oritpro said:**
> If you are using alsamixergui (sudo apt-get install alsamixergui) you just click with your mouse on the un highlighted icon and it will go blue[QUOTE/]

I tried the sudo command, but got an error about not finding 'alsamixergui'.  Isn't IT already installed.  I don't remember seeing a 'un highlighted icon' in the mixer settings dialog?  Is there one?  
The other link you provided:
[http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy](http://www.ubuntuforums.org/showthread.php?t=26158&highlight=audigy)
seems to be wrong for me.   Why switch to or add " kmix"?  The whole post was VERY confusing to me.
Thanks
Phil

---

