---
title: "Upgrade/Installation troubles"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by TracyO on 2008-08-08
I have a Dell that came with Gutsy already installed.  I was upgrading to Hardy through the update manager, and it froze with 7 minutes left in the installation process--not the computer, just the upgrade.  

I restarted the computer, and as soon as I log in, it freezes completely.  I can get in through GNOME and presumably other options, but other than the terminal, my computer is not functional at this time.

I went into recovery mode, and it leaves me with root@dell-desktop:~#, and I note that I also get "Profile /etc/apparmor.d/usr.sbin.cupsd failed to load" and "Setting kernel variables
error: "vm.mmap_min_addr" is an unknown key" saying that the latter failed as well.

I'm still fairly new to Linux and haven't had the chance to learn as much as I would like, so along with some help, I also need some patience if I ask lots of seemingly silly questions.

Thank you!
Tracy

---

### Post by Diabolis on 2008-08-08
Once I had a similar problem. While doing a major update, a kernel update, my laptop did a hard reboot. So It left dpkg and the kernel in a unstable state.

What I did was to boot from a live-cd and executed this commands:
```
sudo apt-get update
sudo apt-get upgrade
```

It fixed my problem.

---

### Post by TracyO on 2008-08-08
Thanks, Diabolis.  My only concern is losing everything that's currently on my computer.  This would occur if I used a live cd, right?  If it's the only solution, I'll certainly do it, but I was hoping there might be a way without losing everything.

Tracy

---

### Post by Diabolis on 2008-08-08
Those commands won't delete anything. They are safe.

---

### Post by psuliin on 2008-08-08
I have a very similar problem.  Does this need to be a live 8.04 CD, or 7.10?

EDIT: One difference between my situation and Tracy's - My upgrade hung at 8 minutes remaining on building locales.  When I restarted, I got an error telling me that my home directory did not exist.  I OK'd starting as root, but I then got an error telling me that my $HOME/.dmrc file was being ignored.  It said this prevented my default session and language from being saved.  It went on to say that my $HOME file needed to be owned by the user and have 644 permissions.

So, should I still try the live-CD upgrade?  Like Tracy, I'm concerned about losing data.

> **Diabolis said:**
> Once I had a similar problem. While doing a major update, a kernel update, my laptop did a hard reboot. So It left dpkg and the kernel in a unstable state.

What I did was to boot from a live-cd and executed this commands:
```
sudo apt-get update
sudo apt-get upgrade
```

It fixed my problem.

---

### Post by Diabolis on 2008-08-09
Since the apt-get commands will access the official repositories, you have to use a cd of the same version as your Ubuntu installation.

@psuliin
In your case, try first to fix the permissions problems with the chmod command.

> It went on to say that my $HOME file needed to be owned by the user and have 644 permissions.

```
sudo chmod 644 /home/*"home folder name"*
sudo chown *"your user name"* /home/*"home folder name"*
```

[linux file permissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

---

### Post by psuliin on 2008-08-10
Well, the saga continues.

Diabolis, I was a little unclear.  When I tried to log in after the upgrade hang, my system told me that my home directory didn't exist.  The permission problem was with my $HOME/.dmcr file, which the error message said was being ignored.

So naturally when I went in on the live CD and tried to change the permissions on my home directory, it didn't work.  Not only that, but I wasn't able to find any file or path called $HOME/.dmcr.  

But wait, there's more.  I DID find my home directory, but the file hierarchy had been bollixed.  If my home directory had previously been named /home/paul, it was now /media/disk-1/paul.  "disk-1" was the generic name assigned to my data partition.  It was just listed as an unnamed drive when I found it through the live CD, and as soon as I opened it the system assigned that name to it.  

So here's what I ended up doing:

First, I tried to change the permissions on my "new" home directory, using the new directory structure.  That didn't work, because I wasn't even listed as a user account on the system any more.  So I added myself as a user via the live CD user management GUI.  Then I changed my permissions and that worked.  Then I reinstalled 7.10.  I think I managed to save most of my data, since I pulled some off to a flash drive and I'd had at least enough foresight to install Ubuntu and house my data on different partitions.  

After I did all this I was finally able to log in again.  And the partition with my data is still there.  However I didn't have permission for some reason.  So, I changed the permissions AGAIN.  And now ls -l shows me as the owner, but when I try to open anything in that directory it says I don't have permission.

Here's the record of that last permission change.  I've made the name of my machine generic.

CORSAIR is my flash drive.
sda1 is my root partition, where I made the new install.  
sda4 is my data partition, which supposedly belongs to me now, but which I can't access.
```

paul@machine:/media$ cd sda4
bash: cd: sda4: Permission denied
paul@machine:/media$ sudo chmod 644 /media/sda4
[sudo] password for paul:
paul@machine:/media$ sudo chown paul /media/sda4
paul@machine:/media$ cd sda4
bash: cd: sda4: Permission denied
paul@machine:/media$ ls -l
total 24
lrwxrwxrwx  1 root root        6 2008-08-09 16:06 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-08-09 16:06 cdrom0
drwx------ 13 paul root     4096 1969-12-31 16:00 CORSAIR
drwxrwx---  1 root plugdev 12288 2008-08-09 09:21 sda1
drw-r--r--  5 paul root     4096 2008-04-13 04:25 sda4
```

I notice that the permissions don't seem to be the same in CORSAIR (which works fine) as they are on sda4 (which doesn't), but I don't know how to fix this.

So, any advice?  Once I get this straightened out, I still need to upgrade to 8.04.  Yeesh.

---

### Post by Diabolis on 2008-08-10
> I wasn't able to find any file or path called $HOME/.dmcr. 

$HOME is an environment variable and its value changes in each session and each ubuntu installation. You can see its actual value with this command:
```
echo $HOME
```

> If my home directory had previously been named /home/paul, it was now /media/disk-1/paul.

When you boot up from a live-cd a totally new and different system is running now. So none of the things that you have done in your installation will be loaded. Your old home folder, */home/paul*, is not seen as a home folder, is just another generic partition that needs to be mounted. That is why if goes to the /media folder.

> First, I tried to change the permissions on my "new" home directory, using the new directory structure. That didn't work, because I wasn't even listed as a user account on the system any more. So I added myself as a user via the live CD user management GUI.

Probably thats where your problem is. You assigned the ownership to a user that you created from the live-cd, which is a different system than the one that you have installed. Then you try to boot up from your hard drive installation and the user that you created from the live-cd no longer exists. Even when they have the same names, because the live-cd and the hard drive are different and separate systems.

The apt-get commands that I gave you were meant to be run from the live-cd and the chmod, chown commands had to be run from the current system.

If you couldn't log in into your system to execute chmod and chown, you could do it from another tty. You do this by pressing **<Ctrl><Alt>FX**
 where **FX** can be any F key from F1 to F6, F7 will return to the graphics.

---

### Post by psuliin on 2008-08-10
> **Diabolis said:**
> $HOME is an environment variable and its value changes in each session and each ubuntu installation. You can see its actual value with this command:
```
echo $HOME
```I'll bear that in mind for the future.  Since I reinstalled, I'm not having any trouble logging in.  I just need to get my system straightened out again before I upgrade.  

> Probably thats where your problem is. You assigned the ownership to a user that you created from the live-cd, which is a different system than the one that you have installed. Then you try to boot up from your hard drive installation and the user that you created from the live-cd no longer exists. Even when they have the same names, because the live-cd and the hard drive are different and separate systems.Well, the problem is that I ran the sessions in the transcript I posted AFTER I had reinstalled and logged in again.  So, if I'm understanding you right, the "paul" that I transferred ownership to should have been the one active on that login - that is, me, on my new account.  But that account can't access the sda4 directory.  Any ideas why not?  Should I start a new thread in a different section?

> The apt-get commands that I gave you were meant to be run from the live-cd and the chmod, chown commands had to be run from the current system.Ah, I wasn't clear on that.  

So, once I get my system back together, how should I upgrade to avoid the hanging problem that so many people seem to be getting when we go from 7.10 to 8.04?

---

### Post by Diabolis on 2008-08-10
Just correct the permissions as you did before, but from the system that you'll be running, not the live-cd.

About the upgrade thing, I don't know if you can tell before hand if it will hang. Just as a tip, I wouldn't upgrade. I would download hardy and burn it to a cd, so if something happens I can just reinstall it again instead of going through the hassle of downloading and upgrading everything again.

---

### Post by psuliin on 2008-08-10
> **Diabolis said:**
> Just correct the permissions as you did before, but from the system that you'll be running, not the live-cd.Hm.  I thought I was clear on that: that's what I did.  I posted the results of that [in this message]("http://ubuntuforums.org/showpost.php?p=5559043&postcount=7"). The code I posted there is from the new system that I'm now running Ubuntu on.  And as you can see I'm still having permission problems.

Just to clarify, I've corrected the permissions twice now: once with the live CD, and again after I reinstalled and rebooted on the new system.  The code I posted is from the second time.

I don't know that I could even reformat the sda4 partition until I get the permissions ironed out, so it's really critical that I regain control of that partition.

> About the upgrade thing, I don't know if you can tell before hand if it will hang. Just as a tip, I wouldn't upgrade. I would download hardy and burn it to a cd, so if something happens I can just reinstall it again instead of going through the hassle of downloading and upgrading everything again.Sounds reasonable, but before I do any more tinkering with that, I need this permission matter solved.  Is there somewhere else that I should post this?

---

### Post by Diabolis on 2008-08-10
I gave a look to my storage partition and the only difference between mine and yours is that it belongs to a different group.

Thats the only thing I can think about right now, so change the group of your partition too.
```
sudo chwon paul:paul "folder path"
```

The first "paul" is the owner and the second one is the group.

---

### Post by psuliin on 2008-08-11
> **Diabolis said:**
> I gave a look to my storage partition and the only difference between mine and yours is that it belongs to a different group.

Thats the only thing I can think about right now, so change the group of your partition too.
```
sudo chwon paul:paul "folder path"
```

The first "paul" is the owner and the second one is the group.
Hi, Diabolis!

OK, I'm a noob, so before I fool around with my system any more I want to make sure I understand what I'm doing.  I hope you can bear with me.  

This is what I see when I look at the volumes on my media directory: 

```
lrwxrwxrwx  1 root root        6 2008-08-09 16:06 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-08-09 16:06 cdrom0
drwx------ 13 paul root     4096 1969-12-31 16:00 CORSAIR
drwxrwx---  1 root plugdev 12288 2008-08-09 09:21 sda1
drw-r--r--  5 paul root     4096 2008-04-13 04:25 sda4
```

Now, I can access every one of those except for /media/sda4.  The user/group assignments are:

cdrom0: root/root
CORSAIR: paul/root
sda1: root/plugdev
sda4: paul/root

I can access /media/CORSAIR, and it has the same user/group assignment as /media/sda4, which I can't access.  

The main difference seems to be in the access permissions.  /media/sda4 doesn't have e(**x**)ecute permission for either the user or the group.  All the others have (x) for at least the user, and usually both.  I just noticed this after digging around in Sobell's *Practical Guide to Ubuntu Linux* to learn how to decode the output from **ls -l**.

If I understand directory access permissions, that would prevent me from using **cd** to get into the directory, which is the problem I'm having.  If that's correct, then **chmod** should be able to help.  Something like this:

```
$ sudo chmod u+x /media/sda4
```

Before I go poking any more sticks into this, though, I'd like to confirm with someone more knowledgeable than I that this is the right command to fix this problem.

There is one other possible problem that occurred to me while I was trying to figure this out.  Is it possible for two different user accounts to have the same ID and password on a single system?  I wouldn't think it would be, but I wonder if, when I added "paul" as a user through the live CD, I might have created a second user named "paul" on my machine.  In that case the "paul" listed as user on /media/sda4 might not be the same as the "paul" on /media/sda1.

That seems like an awfully slipshod way to design a system, so it seems pretty unlikely, but I figured I ought to ask before I go in and tinker with my access permissions any more than I already have.

Thanks for your help and feedback so far.

---

### Post by misterfixit on 2008-08-19
> **Diabolis said:**
> Since the apt-get commands will access the official repositories, you have to use a cd of the same version as your Ubuntu installation.

@psuliin
In your case, try first to fix the permissions problems with the chmod command.


```
sudo chmod 644 /home/*"home folder name"*
sudo chown *"your user name"* /home/*"home folder name"*
```

[linux file permissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")


Seems like everytime I allow the system to upgrade, ther is Yet Another Glitch (YAG).  Here is what I am getting NOW:

dave@dave-desktop:~$ sudo chmod 644 /home/dave
sudo: unable to resolve host dave-desktop
[sudo] password for dave: 
dave@dave-desktop:~$ sudo chown dave /home/dave
sudo: unable to resolve host dave-desktop
dave@dave-desktop:~$ 

This is frustrating, since my Ubuntu system of 2 PC's on a network are "windows Free" and are running my entire home office now.

I get this 644 permission thing AGAIN ... and now I can't print across the network from the main PC (which has no printers attached physically) to the other PC which has 3 printers physically attached.  It used to work ... last week ...

Sure would be nice to get some answers on these problems; Ubuntu has only in the past few weeks become very unusable for me.  Not enough to make me reload that old WinXP CD I have laying around, but the multiple problems are kicking my butt when it comes to productivity -- I am now spending about 30 minutes out of each hour trying to "make things work".  And that just isn't right.

---

### Post by TracyO on 2008-08-20
I ended up fixing the problem by getting instructions on how to back up my system from the terminal to my external hard drive, and then reinstalling completely.  

This is from Luke:
sorry for the delay. here are some instructions for you.

background info:

* hard drives and partitions should appear up in the /dev directory as
/dev/sda
/dev/sda1
/dev/sda2
...
/dev/sdb
/dev/sdb1

all the partitions on the first drive that the kernel sees, which
should be your internal hard drive, begin with sda. when you attach
other drives, the device names begin with sdb, sdc, etc.

0. I recommend booting to the LiveCD with your external drive unattached.
1. when you have logged in and see the desktop, connect the USB drive.
If I the drive is automatically mounted, and an icon appears on the
desktop, you can double click the icon and browse the files. if this
worked automatically, ignore the instructions pertaining to mounting
the external drive (4.2, 5.2)
2. open a terminal
3. type
       ls /dev/sd*

4.1 make new directories for mounting the internal and external
drives. for each partition in /dev that begins with sda, and ends in a
number (sda1, sda2, etc.) make a directory by typing
       sudo mkdir /media/internal1 /media/internal2

4.2 for the external drive, for each partition in /dev that begins
with sdb, and ends in a number (sda1, sda2, etc.) make a directory by
typing
       sudo mkdir /media/external1 /media/external2

5. mount the partitions to your filesystem.
5.1 internal drive:

       sudo mount -t ext3 /dev/sda1 /media/internal1
       sudo mount -t ext3 /dev/sda2 /media/internal2
       ... etc. until all the sdaX devices are mounted.

5.2 external drive:
       sudo mount -t vfat /dev/sdb1 /media/external1

6. now you should be able to browse the files in the internal drive
and copy and paste everything from /home and wherever you have
important data. look at your internal drive's files by clicking on
Places -> Computer -> Filesystem -> media -> internalX

tips:
 * in the file browser, hidden files in your home directory can be
made visible by hitting Ctrl+h
 * find out more about commands like mount by typing
       man mount

7. when you feel comfortable that you have backed up all your
important files, click on the Install icon on the desktop to begin
installing a new image of Ubuntu on your internal drive.

BTW
when installing the new image, i would recommend creating separate
partitions for / and /home
for the / partition 15 GB should be plenty/overkill, but you probably
want at least 8 GB.

the rest of your drive can be allocated to the /home partition.

you also need a swap partition of about (i think) 150% the amount of
RAM in your machine.

---

### Post by misterfixit on 2008-08-23
Now after going in and trying the 644 without any luck and about 5 complete restarts; I get THIS message when trying to use a terminal:

dave@dave-desktop:~$ sudo (some command)
sudo: unable to resolve host dave-desktop
dave@dave-desktop:~$ 

Never a dull moment ...

---

