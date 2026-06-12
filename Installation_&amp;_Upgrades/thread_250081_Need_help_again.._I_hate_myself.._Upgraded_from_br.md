---
title: "Need help again.. I hate myself.. Upgraded from breezy to dapper, but cant login now"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by Rizla on 2006-09-03
Hey Guys,

I've been working on trying to get ubuntu installed for the past couple days.  Its been one hassle after another.  I intially tried instally ubuntu-server 6.06 iso that i downloaded, but that wasnt workign out.  I kept getting uncompressing errors err:2.  Then i got crc errors.. i never got it to work of the iso,i burned two iso, but none of them worked for me.

I later went and bought 'Beginning Ubuntu Linux' just cuz it came with an install cd.  Of course it was an older version it was Breezy 5.10.  It wasnt workign when i tried to do the regular desktop install, so i tried server and that finaly worked. 

From there I did the apt-get install ubuntu-desktop.  took awhile, got it installed and i had a working desktop install. My next step was to upgrade from breezy to dapper following this tutorial: [http://www.psychocats.net/ubuntu/dapper.php]("http://www.psychocats.net/ubuntu/dapper.php")

i did the aptitude update, then i edited my sources list and modified all instances of breezy to dapper.  Then i did the aptitude dist-upgrade.

Everythign seemed to have worked fine, but then i tried to log in as the username i created and thats when the trouble started.

It would briefly login then prompt an error message regarding that it couldnt modify the .dmrc file in the $HOME directory.  Then once it almost gets in, it says that its loggin me out after 10 seconds.  Then it puts me back at the login screen.  I cant do anythnig.  THe only way i can get to a prompt is if i boot into safe mode and login as root.

Thats wehre Im at right now.  I only have a working command prompt with root in safe mode.  I cant get into my desktop.  How do i fix this?  Should i reinstall and start again, knowing that i'll have to start with the base server install, then upgrade to desktop, then upgrade to dapper again?

Please help.  I just want to use linux.:-?

---

### Post by Anonii on 2006-09-03
Not your main problem, but you first edit the sources.list, then you update. Update just sees the packages in each repository you have in your sources.list, so you first have to edit the list and then update. 
About your other problem, I dont know, but I bet someone else does.

(btw, be patient :] )

---

### Post by kh4nh on 2006-09-03
Is this the message: "User's $HOME /dmrc file is being ignored. This prevents the dfault session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."

ls -l /home/USER_NAME/.dmrc

if that file does not belong to you (USER_NAME), then change the ownership of    the file:

chown USER_NAME:USER_NAME /home/USER_NAME/.dmrc

Other wise, change the file access permission:

chmod 644 /home/USER_NAME/.dmrc

---

### Post by James_Nostack on 2006-09-03
Hi Rizla!  I'll try to help, but I'm kind of a n00b at Ubuntu.  Hopefully I won't steer you too far wrong.  (It's also likely that you know more about Ubuntu than I do, but hey, that's life!)

Let me see if I understand your situation:
1.  You tried to install 6.06 Server Edition (or whatever it's called) but it didn't work very well.  

1A.  (From the rest of your post, it sounds like you're trying to run the Desktop version.  So I'm not sure why you wanted Server first.  Maybe I am misunderstanding?)

2.  You then tried to install Breezy using a 5.10 Desktop CD.  This didn't work well, so you tried using 5.10 Server, which *did* work.

3. You then tried to upgrade from 5.10 Server to 6.06, using [http://www.psychocats.net/ubuntu/dapper.php](http://www.psychocats.net/ubuntu/dapper.php) --and then the fun begins :)

First of all: this past week, I tried to upgrade from 5.10 to 6.06 too, and the installation got screwed up half-way through, and it sent me into a shell.  I finally managed to fix things on my machine.  But I'm not sure if this approach will work for you.

Step 1 - When I boot up my machine, I get a message talking about a Grub 1.5 loader thing.  I press Escape, which lets me select which Ubuntu kernel to use.  (I found that 2.6.12-9-386 worked fine for me, and got me to my desktop.)

Step 2 - On my desktop, I tried to run some update utilities--the "red circle" near the clock, Update Manager, Synaptic Package Manager.  None of them worked correctly, but they usually gave me advice.  I wrote it down, and when they gave me a command, I went to my Terminal (by pressing Alt+F2) and ran the commands.

Step 3 - I used these upgrade instructions -- [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

I decided that using a 6.06 CD was the simplest, least risky thing (because I am stupid, and didn't want to take risks).  But since my computer has trouble recognizing my CD-ROM drive, I downloaded the 6.06 Alternate Install ISO to my desktop and used those instructions.

Step 4 - Because my laptop is silly and likes to overheat, I kept it in a bucket of ice during the installation.  It worked fine.

=====
Now, the trouble is, if you're operating entirely from root, you might have trouble.  But if you can burn a Dapper Alternate CD, maybe from work or from a friend, I'd give those instructions a try--might work from the shell after all.  [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

Good luck!

---

### Post by Rizla on 2006-09-03
Ok, heres my update.  After I posted, i said screw it i'll try to reinstall.  

Here's what I did.  I used the Breezy CD i recieved with the book ver 5.10 i believe.  I installed the desktop version this time it surprisingly worked.  Got everythign back up and running.  Then i got a message saying that a new version was available.  SO i used the automatic updater to install 6.06.  It did its thing, downloaded, then removed a bunch of stuff that said it wasnt supported any more unless i had the universe repository.  

After all that, i had to reboot.  Now grub is showing a bunch of versions.  Here's what's listed:

Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)
Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386 
Ubuntu, kernel 2.6.12-9-386 (recovery mode)

I bootted to the first option, it went into the login screen.  I put the credentials i initially setup.  It looked like i successfully logged in, then the scren goes black, briefly shows the command line, then goes back to the login screen and puts me back at square one..

Why is this happening?  I didnt do anything fiddling with anything, i just updated it according to the sytem message that i got saying there was a newer version available.  

Any ideas?

---

### Post by Rizla on 2006-09-03
Alright.. another update on my miserable happenings so far.  Like i said earlier i have all those options now to boot to.  I chose to go into the second option recovery mode.  I got to the command line and did startx and suprisingly it loaded gnome automatically.  I bypassed the login.  Im assuming that im in as root.

How do i get it back to the point where i can login as my username/pass that i created when i intially set it up?

And i thought linux had a shot at going mainstream.. If stuff like this happens when you do a simple upgrade, it would be enough to drive a novice crazy..

---

### Post by James_Nostack on 2006-09-03
Rizla - Like I said, I would try Ubuntu, kernel 2.6.12-9-386 and follow the instructions here: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) and see if that works.

> [the computer] goes back to the login screen and puts me back at square one.  Why is this happening? I didnt do anything fiddling with anything, i just updated it according to the sytem message that i got saying there was a newer version available. Any ideas?

Unfortunately, no.  But I don't know very much about Linux or Ubuntu.  I do know that, when faced with a similar problem, the method above worked for me.

> And i thought linux had a shot at going mainstream.. If stuff like this happens when you do a simple upgrade, it would be enough to drive a novice crazy.

Yeah, no kidding.  My hardware doesn't run Windows very well, though, so Linux is really all I've got, and Ubuntu's allegedly the best of the bunch!  In defense of Ubuntu, though, I've been running it for 12 months without a single crash.  (Aside from the headache of major upgrades like this.)

---

### Post by Rizla on 2006-09-03
I'll read the link over again.  The thing is that i already upgraded to dapper.  Its just having a bunch of problems.  Maybe the article will have some much needed advice.

---

### Post by Rizla on 2006-09-03
Alright i tried everything on that page you gave me (with the exception of the pcmcia stuff).  It said my system was up to date.  There's nothing for it to do at this point.  this is so annoying.. maybe i should reinstall for the 3rd time..

---

### Post by Rizla on 2006-09-03
Alright, i've started my 3rd fresh install.  Im wondering if the problem is happening because of the way i have my partitions set up.  Maybe when it updates the kernel, since my /home folder is in another partition its not finding my user info.  This is 100% speculation since i dont know how the inner workings go.  Here is how i set up my partitiions

20Gb -primary- Windows Partition (my windows setup)
7Gb -primary- "/"(root) ex3t files system
20Gb -logical- "/home" ex3t 
1Gb -logical- swap
32Gb -logical- "/windows" fat32 (to be used to interchange files)

SO thats how i setup my hard drive on the primary IDE1 physical 80gig drive.

Does that seem like a normal way to set it up?

This time around, im going to follow the directions you posted the link to VERBATIM.

---

### Post by James_Nostack on 2006-09-03
Hmm - if it doesn't work, I'm fresh out of ideas, which isn't surprising because I don't really know what I'm doing.  I hope it works, or if it doesn't, that someone else can help.  (I never managed to figure out the partition thing, myself.)

---

### Post by Rizla on 2006-09-03
yea.. the mount points was a little confusing at first, but i read up on it and found a great how to describing the process step by step.  There is one thing i have to say about ubuntu and the linux community as a whole, and that is that its a very active community.  So much information available online, almost too much so.  Right now im almost complete with the install.  then i'll get goign on updating it.

how did you setup your partitions?

---

### Post by az on 2006-09-03
> **Rizla said:**
> [http://www.psychocats.net/ubuntu/dapper.php]("http://www.psychocats.net/ubuntu/dapper.php")

i did the aptitude update, then i edited my sources list and modified all instances of breezy to dapper.  Then i did the aptitude dist-upgrade.

Everythign seemed to have worked fine, but then i tried to log in as the username i created and thats when the trouble started.

It would briefly login then prompt an error message regarding that it couldnt modify the .dmrc file in the $HOME directory.

That error message also goes on to say that the home directory should not be world-writeable.  I submetted a bug report about that, saying that the error should be more specific.  You get the same message whether it is a .dmrc not writeable or a home folder that is world-readble.

That's one of the problems with backing up your home folder and using it for an entirely new install (if it does not have the same user (in terms of number, you're in trouble).  Just change the ownership of the home folder to be owned by you and not world-readable.

---

### Post by Rizla on 2006-09-03
Thanks for that info, i wish i would have been told that earlier.  It could have saved me two new installs.  But right now i dont get that message anymore since i did the last install and upgrade.  The problem i was having was that I couldnt login anymore.  It would login, briefly show the desktop, jump to the black command line screen, then put me back out to the login gui.  The only way i was able to get back into the desktop was to go into recovery mode and then starx back into gnome.

I'll keep you posted on this latest install.  Right now i'm downloading all the new stuff.  I havent gotten to the point of doing the distro upgrade yet.

---

### Post by Rizla on 2006-09-03
I just updated all the lastest software.  I rebooted for the hell of it to make sure everything still worked.  Im replying to this from the new setup.

One thing i did notice as that it added two new entries in GRUB.  How come it does that?  I still havent updated to 6.06 yet, im sort of hesitant at this point given how things happened last time.

What are the advantages of going to 6.06?

---

### Post by James_Nostack on 2006-09-03
> What are the advantages of going to 6.06?

Better product support, they tell me.  :roll: 

No, seriously: the system seems a little bit smoother, and there are at least a few new packages.  But I'm not a techie, I couldn't really tell you.  Best of luck.

---

### Post by Rizla on 2006-09-03
Thanks for all the help guys.  I finally got the system updated properly.  NOw im just struggling to use it and get around all these permission issues.

Does anyone know how i could view my files from my shared hard drive?  I have an NTFS drive that i keep my movies and mp3's on.  When i try to browse to it via the icon on my desktop it tells me i dont have permission to do so.

I did the alt+f2 command and typed gksudo nautilus and that brought up the browser and i browsed to the drive and I saw all my data.  Now how do i have it so that i don thave to do that everytime?

---

### Post by DigitalAxis on 2006-09-04
aha!  I can actually help you with that.

Your problem is that your Windows partition has no permissions on it, so they're assigned to whoever mounts it- if it's automatically mounted, that's root.

***** WARNING!  THIS REQUIRES MODIFYING /etc/fstab WHICH IS A CRITICAL SYSTEM FILE AND MIGHT PREVENT YOUR COMPUTER FROM BOOTING *****
That said, if you just make sure to edit the right lines and stick with the correct format, it's fairly easy to modify.

Try this:
1.) get to a console (there's probably a better graphical way, but I know the console method) and type **cat /etc/passwd**
2.) Find your login name in that list, and the associated number.  Assuming you're the first user created on the system, it should be 1000, and near the bottom of the list.
3.) type **sudo nano -w /etc/fstab**.  DON'T FORGET THE -w.  It turns word wrap off; wrapped lines WILL break your /etc/fstab and YOUR COMPUTER WON'T BE ABLE TO BOOT.
4.) This is the list of where your computer finds out how to mount things.  Find the drive that's going to be mounted as 'ntfs', or as /windows, or whatever.

Now, there are two things you can do:
a.) type '**noauto**' in the options section of the line to be mounted as ntfs.  This prevents it from being mounted by root at boot-time.  You'll have to do it yourself every time you restart your computer and want to use your drive, but then you'll own the files.
***or***
b.) add **uid=1000,gid=1000** (or whatever number:number you found in step 2) to the options line instead.  This will mount it with you as the owner.

If it's not already there, add an **ro** to the options so the drive is mounted read-only (the current in-kernel ntfs driver can't write data safely)

5.) make sure there's exactly one filesystem per line- if you use nano, your newly modified windows entry should stretch off the end of the screen with an $ at the end.  IF NOT, go to the beginning of the line that doesn't start with /dev/something and hit backspace.

***This is what my /etc/fstab looks like:*** (incidentally, it's been modified much the same way; vfat is a FAT32 partition)
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               jfs     noatime,errors=remount-ro 0       1
/dev/hda2       /C              vfat    defaults,utf8,dmask=022,fmask=133, user,uid=1000,gid=1000 0       1
/dev/hda1       /boot           ext2    noatime,noauto        0       2
/dev/hda7       /home           jfs     noatime,        0       2
/dev/hda5       /tmp            jfs     nosuid          0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

***This is a broken /etc/fstab:***
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               jfs     noatime,errors=remount-ro
 0       1
/dev/hda2       /C              vfat    defaults,utf8,dmask=022,
fmask=133,user,uid=1000,gid=1000 0       1
/dev/hda1       /boot           ext2    noatime,noauto        0       2
/dev/hda7       /home           jfs     noatime,        0       2
/dev/hda5       /tmp            jfs     nosuid          0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

6.) exit, saving your new file.  Upon next boot, you should either be able to mount your windows partition, or find it automatically mounted for you.

---

