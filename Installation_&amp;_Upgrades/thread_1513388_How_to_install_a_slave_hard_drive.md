---
title: "How to install a slave hard drive?"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by revhead347 on 2010-06-19
I recently ran out of storage space on my primary hard drive, and wanted to add a second hard drive. Computer is currently operating on Xubuntu 9.04.  I got a new Western Digital internal 500gig IDE drive and installed.  The two hard drives are pinned for primary with slave and slave.  Both hard drives come up in the bios CMOS menu.  How do I format that second hard drive and start using it?

Kurt

---

### Post by darkod on 2010-06-19
Open Gparted in System-Administration and create any partitions you want on the new disk. Then set them to automount or just mount them when ever you need them.

If Gparted is not there install it from Software Center or in terminal with:

sudo apt-get install gparted

---

### Post by revhead347 on 2010-06-19
There is no administration function under System.  I entered that script into the terminal.  It comes up with a password que and a field that you can't enter anything into.

Kurt

---

### Post by kansasnoob on 2010-06-19
> **revhead347 said:**
> I recently ran out of storage space on my primary hard drive, and wanted to add a second hard drive. Computer is currently operating on Xubuntu 9.04.  I got a new Western Digital internal 500gig IDE drive and installed.  The two hard drives are pinned for primary with slave and slave.  Both hard drives come up in the bios CMOS menu.  How do I format that second hard drive and start using it?

Kurt

You scare me saying:

> The two hard drives are pinned for primary with slave and slave.

Both drives can't be set to "slave"! I'd think you'd want to be sure the original drive is still set to Master and that it's attached to the end connector of the IDE cable. Or are you using two different cables?

I guess that's where we should start, are both drives sharing one cable?

---

### Post by dwasifar on 2010-06-19
> **kansasnoob said:**
> You scare me saying:


Quote:
The two hard drives are pinned for primary with slave and slave. 

Both drives can't be set to "slave"! 

I think he means "primary with slave" and "slave."  One drive is jumpered for Master with Slave Present, and the other is jumpered for Slave.

Personally I stopped screwing around with this a long time ago and just jumpered all my drives to Cable Select until SATA made them obsolete.

The OP should open a terminal and type "sudo gparted".

---

### Post by kansasnoob on 2010-06-19
> **dwasifar said:**
> I think he means "primary with slave" and "slave."  One drive is jumpered for Master with Slave Present, and the other is jumpered for Slave.

Personally I stopped screwing around with this a long time ago and just jumpered all my drives to Cable Select until SATA made them obsolete.

The OP should open a terminal and type "sudo gparted".

The OP said, "The two hard drives are pinned for primary with slave and slave."

That leads me to believe they have a MoBo with a primary and a secondary IDE connector, and both of these drives are sharing one cable connected to the Primary IDE port. That is fine, but (s)he  needs to understand that the Master needs to be connected to the end of the cable and be set either as Master or "cable select", and the new "slave" be set as Slave or cable select and be connected to the center connector of the cable.

There are other scenarios, like having a CD/DVD drive connected as slave to the center of a cable (which I don't like), but we need to get a "picture" of the hardware layout before we can make any real recommendations.

Many things to consider. I often have people bring me old machines that are still using 40 wire IDE cables :(

But after sorting out hardware issues if I had a machine with two IDE ports, two IDE hard drives, and one IDE optical drive I'd attach both hard drives to the primary cable with the OS drive set as Master and attached to the end connector, the data hard drive set as Slave and attached to the middle connector, and the optical attached to the secondary IDE port.

---

### Post by darkod on 2010-06-19
> **revhead347 said:**
> There is no administration function under System.  I entered that script into the terminal.  It comes up with a password que and a field that you can't enter anything into.

Kurt

How can you not have Administration submenu under System? Is it because it's Xubuntu? Or there are broken ubuntu images around. There have been few strange statements on the forum lately.

Like the live mode asking for username and password when loading...

I'm also surprised at Master with Slave. Why not simply Master? Even with single ide hdd I always used that setting. Set the one as Master, the other as Slave, if possible.

Forget Master with Slave.

---

### Post by dwasifar on 2010-06-19
I have here in front of me a Western Digital WD2500 drive, with the sticker clearly showing different settings for "Master" and "Master with Slave."  Master is all jumpers open; Master with Slave is a jumper at pins 5-6; Slave is pins 3-4; and Cable Select is pins 1-2.  If you don't believe me, [look it up.]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=932&p_created=&p_cats=185&p_cv=1.185&p_pv=2.295&p_prods=227%2C295#jumper")

You follow the advice "forget Master with Slave" at your peril.  I can tell you from experience that if you don't have the Master with Slave (or Cable Select) jumper set, this drive will not work correctly when used as a master with a slave present.  Usually the system won't even boot.

Yes, the OP said "The two hard drives are pinned for primary with slave and slave."  I think you're reading that wrong.  You're reading it as "primary, with slave and slave."  I think the meaning was "primary with slave, and slave."  I think he means "master" when he says "primary."  In other words, drive 0 is jumpered to be master with slave present, and drive 1 is jumpered to be slave.  It struck me strange at first too, until I realized what he must have meant.  A comma or something would have helped.

It would be nice to hear back from the OP on this.  He seems to have vanished.

---

### Post by revhead347 on 2010-06-19
Ok, sorry I was helping a friend fix his car.  I guess I need to clear it up.  Both hard drives are on one IDE (ribbon looking thing) cable.  The jumper on the primary is set to "Primary with slave," and the jumper on the new hard drive is jumpered for "slave,"  The primary drive is on the end of the cable, and the computer is working normally.  I'm on it right now.  When I go into the bios, both hard drives show in their respective position and functioning.  I have a WD800 on the primary, and a WD5000 on the slave.  So I'm pretty sure it should work the way it is wired right now.  What I need to know is how to get Xubuntu to locate that second hard drive, and format it.  There is no Administration under the system menu.  There is an "Authorizations" menu though.

Kurt

---

### Post by revhead347 on 2010-06-19
> **dwasifar said:**
> I have here in front of me a Western Digital WD2500 drive, with the sticker clearly showing different settings for "Master" and "Master with Slave."  Master is all jumpers open; Master with Slave is a jumper at pins 5-6; Slave is pins 3-4; and Cable Select is pins 1-2.  If you don't believe me, [look it up.]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=932&p_created=&p_cats=185&p_cv=1.185&p_pv=2.295&p_prods=227%2C295#jumper")


That is exactly how I have the jumpers set up on it.  The Master has the jumper on pins 5-6, and the slave has it on pins 3-4.  I just looked at the top of the hard drive, and that made the most logical sense to me.

Kurt

---

### Post by revhead347 on 2010-06-19
> **dwasifar said:**
> 

The OP should open a terminal and type "sudo gparted".

Ok, I did that, and then it says "[sudo] password for kurt:"  But you can't type in a password.  None of the keys do anything.

Kurt

---

### Post by darkod on 2010-06-19
> **revhead347 said:**
> Ok, I did that, and then it says "[sudo] password for kurt:"  But you can't type in a password.  None of the keys do anything.

Kurt

Just type the password and hit Enter. It just looks like doing nothing but it's accepting the letters. When entering the sudo password it always does that.

---

### Post by dwasifar on 2010-06-19
> **revhead347 said:**
> The jumper on the primary is set to "Primary with slave," and the jumper on the new hard drive is jumpered for "slave,"  The primary drive is on the end of the cable, and the computer is working normally.  I'm on it right now.  When I go into the bios, both hard drives show in their respective position and functioning.  I have a WD800 on the primary, and a WD5000 on the slave.

You caused us a lot of confusion by calling it Primary instead of Master.  :)  Kansasnoob was convinced you were talking about the primary IDE controller.  I knew what you meant because you said you had it "pinned," meaning jumpered, to Primary, and the jumper settings don't enter into what IDE connector you've attached your cable to.  Glad we got that all cleared up.  :)

Okay, here's the full sequence of what you need to do.

In a terminal, sudo gparted as before.  Type password when prompted; it does not appear as you type.

You will get the Partition editor window.  In the upper right corner there will be a drop-down menu for you to select what drive you are working with; it will default to /dev/sda (or it may be called /dev/hda on your system) which is your master drive.  Pull it down and select /dev/sdb (or /dev/hdb) which will be your slave drive.  It should be easy to tell which is which because the sizes will be displayed.

If the new drive already has a partition on it, you can wipe it out by pulling down the Device menu, choosing Create Partition Table, and following the prompts.  The default is an MS-DOS partition table, which is fine.

If everything has gone well up to this point you should have a big gray rectangle representing the drive space, labeled "Unpartitioned space."  Right-click on that and choose New.  The default is to create an ext2 partition filling all the available space.  You will probably want to change that to ext3 or ext4, but otherwise you can accept the defaults.  Click Add and then click the green check mark at the top of the window to apply the changes and create the partition.

When that is done, you have a new empty partition.  Now you need to mount it somewhere.  For instance, you might create a folder called "storage" in your home folder.  Then to mount it there, from the terminal type "sudo mount /dev/sdb1 ~/storage"  This will make that partition available at that mount point.

If you want it to mount there every time you boot, then you need to add it to the /etc/fstab file.  In terminal, type "sudo gedit /etc/fstab".  The format of the file is: partition, mount point, partition type, options.  If your drive came up as /dev/sdb in gparted, and you formatted it to ext4 and used my example of a folder called "storage," then you would add a line to the bottom of the file:
```
/dev/sdb1 /home/kurt/storage ext4 errors=remount-ro 0 1
```
Adjust this as necessary depending on your mount point and partition type.  Save the file and either reboot or just issue "sudo mount -a" from the terminal.

Hope this gets you through.  Let us know how it goes.

---

### Post by revhead347 on 2010-06-19
Ok, I'm moving forward a little here.  I typed in "sudo dparted" in the window, and it came back "command not found."  I'm thinking at this point to just upgrade to 10.04 and see what happens.  I hate updating software to a newer version though.  If it works fine, I generally leave it alone.

Kurt

---

### Post by oldos2er on 2010-06-19
> **revhead347 said:**
> Ok, I'm moving forward a little here.  I typed in "sudo dparted" in the window, and it came back "command not found."

The correct command would be ```
gksu gparted
```

---

### Post by dwasifar on 2010-06-19
> **oldos2er said:**
> The correct command would be ```
gksu gparted
```

Yes, gksu will work too for this.  I tend not to use it because it changes the focus from the terminal to a password confirmation window, and I just find it easier to type the password in the same place where I just typed the command.  The more important thing is that he needs to type gparted and not dparted.  :)

---

### Post by revhead347 on 2010-06-19
Thanks for everyone's help.  I have upgraded to Xubuntu 9.10 in hopes of an easier install. However, still not there.  I type in "gksu gparted" into the Terminal and then it prompts a password in seperate window.  After I type in the password, a box appears in the task bar that says "Starting Administrativ....."  It's there momentarily, and then it disapears, and then the cursor begins to flash in the Terminal again.  But that's as far as it gets.

Kurt

---

### Post by darkod on 2010-06-20
I'm not familiar with Xubuntu and I see no one else is asking the question.

Is Gparted installed at all in Xubuntu by default? I know you have to add it in Ubuntu.

Try to install it first with:

sudo apt-get install gparted

Then to start it (because it's graphics program gksudo is better than sudo):

gksudo gparted

---

### Post by revhead347 on 2010-06-20
> **darkod said:**
> I'm not familiar with Xubuntu and I see no one else is asking the question.

Is Gparted installed at all in Xubuntu by default? I know you have to add it in Ubuntu.

Try to install it first with:

sudo apt-get install gparted

Then to start it (because it's graphics program gksudo is better than sudo):

gksudo gparted

Ok, I've made huge progress overnight.  I finally got the hard drive partioned.  You were correct, Gparted was not installed in Xubuntu.  I finally got gparted loaded.  I upgraded to 10.04 last night in hopes that it would make things easier.  Anyway, I used the code you have above to get gparted, but for some reason my computer doesn't like the term "sudo," but when I substituted gksu in there, it worked.  I went into gparted, found the drive, and formatted it.  I made it "ext3" as recommended above.  Now I'm not having any luck mounting it.  The code to mount it just comes up "command not found" or "Starting Administra..." box appears, and nothing happens.

Kurt

---

### Post by dwasifar on 2010-06-20
Can you share with us the exact command you are entering to mount the drive?

---

### Post by revhead347 on 2010-06-20
Ok, I think one of the things that might be confusing me, is that I can't create a folder in the home folder.  The function in the window is not there.  The default storage folder in the home folder is called "kurt.," my name obviously, and I can put a folder called "storage" in there.   I would prefer to mount the hard drive to my desktop for ease, but mounting it anywhere would work at this point.

Kurt

---

### Post by revhead347 on 2010-06-20
> **dwasifar said:**
> Can you share with us the exact command you are entering to mount the drive?

Absolutely.  I have tired "sudo mount /dev/sdb1 ~/storage" and I have tried "gksu mount /dev/sdb1 ~/storage"  This was the recommended entry from above.  In gparted, the second drive is labeled "sdb1"  Now I read in another thread that if after I mount it, and I screw up the code in fstab at all, the computer will become unbootable.  How true is this?

Kurt

---

### Post by darkod on 2010-06-20
It seems for Xubuntu you need to use gksu, as someone suggested. So use that instead of sudo.

Next, you will only be able to mount it at ~/storage if a 'storage' folder exists in your home folder. And it has to be the exact name, not Storage, because linux makes difference in file and folder names too, unlike windows.

It is very strange not to be able to make a folder inside your home folder, if I understood right. That might point out that you have other issues with permissions.

Just open you home folder, right-click in the white space and is there option in the menu called Create Folder? If there is, simply create the 'storage' folder.

Alternatively, if you already have a folder there called 'kurt' and you want use that as the mount point, in terminal just try:

gksu mount /dev/sdb1 ~/kurt

As far as fstab is concerned, you read right, if you mess it up you can make the xubuntu unbootable. That's why you need to pay attention what you change in fstab.

---

### Post by dwasifar on 2010-06-20
Okay, I think I see the problem.  It's terminology again.  You are trying to create a folder inside /home, right?  Sorry; it's common practice to call a user's folder inside the /home directory their "home" folder.  What I meant by your home folder is /home/kurt, not /home.  I can see why you might not have known that.  Sorry for the confusion.  

Create the storage folder inside the /home/kurt folder, then mount it with an explicit path and the partition type spelled out:

```
gksu mount -t ext3 /dev/sdb1 /home/kurt/storage
```

In regular Ubuntu, using the Gnome desktop, this puts a shortcut on your desktop automatically.  Don't know if Xubuntu will do the same, but it might.

Regarding fstab, you can indeed bork your system if you do something horrendously wrong in /etc/fstab, but since about 9.04 (I think) it just ignores drives it can't find rather than halting boot.  So as long as you don't change anything that's already there, you're likely to be safe.  If you want, you can back it up first, so if you do screw it up you can boot from a live CD and restore it.

---

### Post by cascade9 on 2010-06-20
> **kansasnoob said:**
> That leads me to believe they have a MoBo with a primary and a secondary IDE connector, and both of these drives are sharing one cable connected to the Primary IDE port. That is fine, but (s)he  needs to understand that the Master needs to be connected to the end of the cable and be set either as Master or "cable select", and the new "slave" be set as Slave or cable select and be connected to the center connector of the cable.

Ummm....as long you have the jumper set to 'master' you can have the drive conencted to the middle connector. I always do this, it makes cable management easier (and also makes the data cable shorter, less chance of crosstalk, etc). 

I also have a habit of slicing off the end connector of IDE cables. Not all of them, you never know when you might want to install a slave drive (HDD or optical). 

> **kansasnoob said:**
> There are other scenarios, like having a CD/DVD drive connected as slave to the center of a cable (which I don't like), but we need to get a "picture" of the hardware layout before we can make any real recommendations.

Many things to consider. I often have people bring me old machines that are still using 40 wire IDE cables :(

Why dont you like optical drives conencted to the centre as 'slave'? Not that I do this much, I'm just wondering. 

> **kansasnoob said:**
> But after sorting out hardware issues if I had a machine with two IDE ports, two IDE hard drives, and one IDE optical drive I'd attach both hard drives to the primary cable with the OS drive set as Master and attached to the end connector, the data hard drive set as Slave and attached to the middle connector, and the optical attached to the secondary IDE port.

I do things differently. 

If I have 2 HDDs, they both get set as 'master'. I tednt o have the drive with the OS as the faster drive, and connected to the primary IDE. The data drive connected to secondary IDE, with the optical drive as slave. 

Not that it makes a huge amount of difference, unless you are copying a lot of files, or large files, from one HDD to the other (running reading and writing through a single IDE channel is slower than reading from one IDE channel and writing to the other).

Edit- sorry about this post being a bit behind, alomst to the point of being offtopic.

---

### Post by revhead347 on 2010-06-20
[QUOTE=darkod;9487111

gksu mount /dev/sdb1 ~/kurt
[/QUOTE]

Ok, I tried a few of the codes on here with no result whatsoever.  I finally got some info back when I tried this code, but it wasn't promising.  Only that I'm getting somewhere, because the computer is responding to this code in some fashion.  This was the reply.  I have also included exactly what I put in on the command line.  I assume there is problem because the name kurt is specified twice as if I'm commanding it to mount the hard drive inside a folder called kurt, inside the folder called kurt.

kurt@kurt desktop:/$ gksu mount /dev/sdb1 ~/kurt
mount: mountpoint /home/kurt/kurt does not exist
ount: mount point /home/kurt/kurt does not existkurt@kurt-desktop:/$ ^C

Kurt

---

### Post by darkod on 2010-06-20
> **revhead347 said:**
> Ok, I tried a few of the codes on here with no result whatsoever.  I finally got some info back when I tried this code, but it wasn't promising.  Only that I'm getting somewhere, because the computer is responding to this code in some fashion.  This was the reply.  I have also included exactly what I put in on the command line.  I assume there is problem because the name kurt is specified twice as if I'm commanding it to mount the hard drive inside a folder called kurt, inside the folder called kurt.

kurt@kurt desktop:/$ gksu mount /dev/sdb1 ~/kurt
mount: mountpoint /home/kurt/kurt does not exist
ount: mount point /home/kurt/kurt does not existkurt@kurt-desktop:/$ ^C

Kurt

Post #24 explained it for you.

The /home/kurt is the location of your home folder, or replaced by the ~ mark. I was just going by what you said, that you have kurt folder inside your home folder. So the location of that kurt folder inside Home would be /home/kurt/kurt.

However, obviously you don't have kurt folder existing inside your home folder.

We can't know what you have there, and you are not precise in telling us. At the end of the day, it doesn't really matter, just make up your mind for a folder name, and as I said, create it in your home folder, and just use it as mount point. It doesn't really matter how it's called.

The last message you got said that /home/kurt/kurt doesn't exist which is probably right, even though you said in post #21

>  The default storage folder in the home folder is called "kurt.,"

---

### Post by revhead347 on 2010-06-20
Thank you guys so much for bearing with me.  I admit I am a computer moron.  I got it mounted.  It's in kurt/storage.  I typed in the code, and inside of the storage folder I got another folder called "lost+found"  Not sure what that is.  But the important thing is that it now the properties show 435gb available, and the hard drive showed up in my system monitor.  Now onto the hard part, getting the hard drive to mount on startup.

Kurt

---

### Post by darkod on 2010-06-20
Well, you made it work and that's what matters. :)

PS. In post #13 you have the line you need to add in /etc/fstab just replace ext4 with ext3 if you formatted sdb1 as ext3. That should mount it on boot.

---

### Post by revhead347 on 2010-06-20
Ok, I'm typing in the following.

gksu gedit /etc/fstab

I get the little box that says "Starting Administra...." in the task bar momentarily, but nothing comes up.  I assume a file should follow with a bunch of code for the fstab.

Kurt

---

### Post by revhead347 on 2010-06-20
Still haven't gotten the fstab to come up, but I thought I might ask the next question anyway.  The poster in #13 listed this code.

/dev/sdb1 /home/kurt/storage ext4 errors=remount-ro 0 1


I assume it should be

/deb/sdb1 /kurt/storage ext3 errrors=remount - ro 0  1

Not sure if I need the home in there.

Kurt

---

### Post by darkod on 2010-06-20
Yes, you do need the home in there because the location of your home folder is consisting of the /home mount point and your username (kurt). Hence, the location of your home folder is /home/kurt, or the location of the storage folder in it /home/kurt/storage.

So it should be like:

/dev/sdb1 /home/kurt/storage ext3 etc...

Not sure why the gedit command doesn't work. Maybe it's not installed by default in xubuntu too? Try installing it first:

sudo apt-get install gedit

I'm really not familiar with xubuntu and it seems there are differences with ubuntu for the default programs used for some operations.

---

### Post by revhead347 on 2010-06-20
I tried

gksu apt-get install gedit

It runs the installer.  Comes up with a bunch of information about things it will remove and add.  The end statement is that it will add 17.5mb to the system.  Then it asks if I want to continue [y/n].  I type in 'y', hit enter, and then nothing happens.

Kurt

---

### Post by darkod on 2010-06-20
> **revhead347 said:**
> I tried

gksu apt-get install gedit

It runs the installer.  Comes up with a bunch of information about things it will remove and add.  The end statement is that it will add 17.5mb to the system.  Then it asks if I want to continue [y/n].  I type in 'y', hit enter, and then nothing happens.

Kurt

That is command just to install it, it should have installed it after the Y.

Did you try opening fstab after that with:

gksu gedit /etc/fstab

---

### Post by revhead347 on 2010-06-20
> **darkod said:**
> That is command just to install it, it should have installed it after the Y.

Did you try opening fstab after that with:

gksu gedit /etc/fstab

Yeah, tried it all again.  Tried it again after a restart.  It won't install gedit package.  After the y/n question, nothing happens.

kurt

---

### Post by darkod on 2010-06-20
> **revhead347 said:**
> Yeah, tried it all again.  Tried it again after a restart.  It won't install gedit package.  After the y/n question, nothing happens.

kurt

Gedit is gnome based text editor for ubuntu. Xubuntu doesn't use gnome so probably it won't install because of that.

Google says that the xubuntu text editor is called mousepad, so try:

gksu mousepad /etc/fstab

PS. Otherwise Mousepad should be in Applications-Accessories. Look around Xubuntu for these basic programs for basic use.

---

### Post by revhead347 on 2010-06-20
Now we are getting somewhere.  This is what comes up in a seperate window when I type in that.  With a pretty strong warning in red that if I screw this up, I'm going to mess up my system.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=09e05ea1-46ba-4287-ba7d-289bf99bd5a4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1115e4de-ad99-4800-9974-a4a1c22b335a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Kurt

---

### Post by darkod on 2010-06-20
OK. The lines having # at front are ignored, so it can help you putting a note what you did.

At the end of the fstab file, and according to post #13, add these two lines:

# my /dev/sdb1 mount
/dev/sdb1 /home/kurt/storage ext3 errors=remount-ro 0 1

Save and close the file. Restart and the new partition/disk should be mounted automatically.

---

### Post by revhead347 on 2010-06-20
Holy crap, it worked the first time I tried it.  I can't believe it.  Now here comes the really easy and stupid question.  How do I get files into that storage folder?  The old logic of drag and drop doesn't seem to work on Xubuntu.  Thank you very much for all your help.

Kurt

---

### Post by dwasifar on 2010-06-20
Not sure why drag and drop wouldn't work.  Last time I used Xubuntu, it was using the Thunar file manager and drag-and-drop was no problem.  That was a few versions back, but I can't imagine why they'd remove that functionality.  Can you successfully drag and drop to other folders?  Like, say, from home folder to desktop?

I also remain confused why sudo wasn't working for you, though you seemed to have gotten past that okay.  As far as I know every variant of Ubuntu uses sudo.  But no matter.  :)

---

### Post by revhead347 on 2010-06-20
Yeah, the sudo just didn't work, no idea why.  I can drag and drop to other folders just fine.  I think the problem might be in authorizations.  The 'storage' folder has only one folder in it, labeled "lost+found."  That little folder icon has a little 'x' over it.  Whenever I double click the 'lost+found" folder, it pops up with a window that says "permission denied."  Maybe I need to authorize myself to write stuff to my own hard drive.

Kurt

---

### Post by revhead347 on 2010-06-20
Ok, I went into the "users" menu, and authorized myself to do a bunch more stuff.  That didn't work.  I went back into Gparted to check things out a little bit.  The slave hard drive has a little set of keys in the logo next to /dev/sdb1.  I'm wondering if I have to unlock the use of that hard drive or something.

Kurt

---

### Post by dwasifar on 2010-06-20
> **revhead347 said:**
> Yeah, the sudo just didn't work, no idea why.  I can drag and drop to other folders just fine.  I think the problem might be in authorizations.  The 'storage' folder has only one folder in it, labeled "lost+found."  That little folder icon has a little 'x' over it.  Whenever I double click the 'lost+found" folder, it pops up with a window that says "permission denied."  Maybe I need to authorize myself to write stuff to my own hard drive.

Kurt

Yes, you do, it appears.  Try this.  At terminal, type "gksu -s" and you should get a window with a box to run a command in.  Run this in it:

```
chown -R kurt:kurt /home/kurt/storage/
```

That'll probably fix you right up.

---

### Post by revhead347 on 2010-06-20
> **dwasifar said:**
> Yes, you do, it appears.  Try this.  At terminal, type "gksu -s" and you should get a window with a box to run a command in.  Run this in it:

```
chown -R kurt:kurt /home/kurt/storage/
```That'll probably fix you right up.

That did in fact fix me right up as far as putting files on the hard drive.  However, my wireless card is not working really well now.  I am off the desk top and on my laptop to get online now.

Kurt

---

### Post by dwasifar on 2010-06-21
I guarantee you that nothing we did here had anything to do with your wireless card.  :)

---

