---
title: "[SOLVED] Move From IDE to SATA Drive - How?"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2007-07-07
Okay - I'm a noob so please be gentle.  Currently I have 4 HD's in my system and I'm about to add an additional SATA Raptor to my system for booting ubuntu64.  I've got my system running nice and I want to MOVE my OS to the new drive.  Please tell me how to do this...

Thanks

---

### Post by crjackson on 2007-07-08
Would someone please help me on this...

---

### Post by Shazaam on 2007-07-08
You could clone it to the new drive. Check out clonezilla or g4linux (ghost for Linux). Or research the "dd" command.

---

### Post by crjackson on 2007-07-08
> **Shazaam said:**
> You could clone it to the new drive. Check out clonezilla or g4linux (ghost for Linux). Or research the "dd" command.

I have a cloning program already.  The problem is that according to the program, the drive won't be bootable because the grub is looking for a different hd setup.  I know how to clone the drive, but how do I make it bootable.  It's going to be looking for an IDE drive but I'm moving to an SATA drive.

---

### Post by dabl on 2007-07-08
Grub doesn't care whether it's IDE or SATA, although /etc/fstab does, and Grub has to match /etc/fstab, so there probably is an issue there, indirectly.

Why are you not willing to simply install the OS on the new drive?  It seems to me that is the least trouble-prone approach -- it will write a new Grub boot menu for you in the process, and it should result in your other drives and OS's  being recognized correctly immediately, which I'm not sure will be the case if you copy the image.  Won't it believe it's on the wrong drive?  Won't it be looking for /home on the wrong drive? It seems to me you'll be editing configuration files forever to get it straightened out afterward, versus simply installing the OS where you want it, and letting it see the rest of the system while it installs.  :confused:

---

### Post by crjackson on 2007-07-09
> **dabl said:**
> Grub doesn't care whether it's IDE or SATA, although /etc/fstab does, and Grub has to match /etc/fstab, so there probably is an issue there, indirectly.

Why are you not willing to simply install the OS on the new drive?  It seems to me that is the least trouble-prone approach -- it will write a new Grub boot menu for you in the process, and it should result in your other drives and OS's  being recognized correctly immediately, which I'm not sure will be the case if you copy the image.  Won't it believe it's on the wrong drive?  Won't it be looking for /home on the wrong drive? It seems to me you'll be editing configuration files forever to get it straightened out afterward, versus simply installing the OS where you want it, and letting it see the rest of the system while it installs.  :confused:

I didn't know it would be that complicated.  I move drives and OS around all the time in windows using Acronis TrueImage.  I was hoping for the same type of solution.  It's so much easier.

I'm a Linux newbie and it's taken me a while to get software installed and system configured.  I don't know what I'm doing and I really hate to start from scratch again now that I'm starting to like the way this thing runs.

---

### Post by Shazaam on 2007-07-09
Once again dabl is correct.
I have swapped drives, partitioned them sensless, cloned and copy/pasted OS's till my hard drive with Linux on it wont boot anymore with my XP drive still connected. I am currently researching cures but it doesn't look good. A wipe/reinstall is a chore at this time as I only have dialup and updates take forever:(

---

### Post by crjackson on 2007-07-09
> **Shazaam said:**
> Once again dabl is correct.
I have swapped drives, partitioned them sensless, cloned and copy/pasted OS's till my hard drive with Linux on it wont boot anymore with my XP drive still connected. I am currently researching cures but it doesn't look good. A wipe/reinstall is a chore at this time as I only have dialup and updates take forever:(

Would be nice if someone made a utility LIKE Acronis TrueImage that would handle the issue...

---

### Post by dabl on 2007-07-09
> **crjackson said:**
>  I move drives and OS around all the time in windows using Acronis TrueImage. 

True confessions .... I'm not all that experienced with Linux -- I only did my first (through tenth) installation 8 months ago.  But, I built a desktop system from scratch with 1 IDE/PATA drive and 2 SATA drives, and I spent 3 days trying to convince Edgy that it would be OK to install Grub on one of the SATA drives, with Win XP installed on the IDE drive. Major waste of time! I learned a lot about fstab and grub, and one big lesson was to forget about the way things used to be in Windows - Linux is very, very different and one thing you cannot do in Linux is mix 'n match hard drives like you used to do in Windows.

BTW, I'll share my secret recipe for making a dual-boot Linux/Win XP system on a platform with both IDE and SATA drives, with the master boot record on a SATA drive:

1. fdisk all hard drives, and do NOT partition or format the IDE drive.
2. Install Win XP on the SATA drive, in a partition as you wish.
3. Install (K)(X)Ubuntu on the SATA drive of your choice, or on the IDE drive, partitioning and formatting during installation. It will automatically put Grub on the MBR where Win XP is.
4. Install any other Linux OSs that you may fancy, bearing in mind the cardinal rule regarding Grub: "Last Linux Wins" -- the applicable /boot/grub/menu.lst file that controls the boot menu will be written by the last OS that you install.  So, with a little planning, you can sequence your installation to have the boot menu look the way you want.  But if you change your mind later, you'll be hand-editing that last menu.lst file.

So, as a result of learning this stuff, I have a system that will boot (1) Ubuntu Feisty 64-bit, (2) Kubuntu Feisty 32-bit, (3) Elive development version, and (4) Win XP.  And the Linuces each can read and write to all drives and partitions on the system. 


I hope this helps!  :)

---

### Post by Shazaam on 2007-07-09
The mistake I made was during the last episode of tweaking. Using the gpartedLiveCD I had swapped Windows from the SATA drive where it was installed to an IDE drive. I then swapped the Linux installs from the IDE drive to the SATA drive. No problems reported by the gpartedLiveCD. BUT, when gparted was refreshing the drives the SATA showed as unpartitioned. HORRORS!
I thought I had lost everything. Did a testdisk (from the gparted cd) which showed the partitions as unreadable. Used test disk to find and re-write the partition table using backup superblocks and got 3 Linux os's back. Rebooted and grub was a mess, not allowing me to boot anything. After a BUNCH of edits to fstab and menu/lst in all of the Linux os's I had a running system. But it wouldn't boot to grub after hooking the Windows drive back up. A BUNCH more edits again and it still doesn't work. Thats ok 'cause I don't really use the XP drive much anyway.
To make a long story short I  have a hunch that I should have rebooted the pc when the SATA disk showed up as blank as I think it was a bug with the gpartedLiveCD.

---

### Post by crjackson on 2007-07-09
> **dabl said:**
> True confessions .... I'm not all that experienced with Linux -- I only did my first (through tenth) installation 8 months ago.  But, I built a desktop system from scratch with 1 IDE/PATA drive and 2 SATA drives, and I spent 3 days trying to convince Edgy that it would be OK to install Grub on one of the SATA drives, with Win XP installed on the IDE drive. Major waste of time! I learned a lot about fstab and grub, and one big lesson was to forget about the way things used to be in Windows - Linux is very, very different and one thing you cannot do in Linux is mix 'n match hard drives like you used to do in Windows.

BTW, I'll share my secret recipe for making a dual-boot Linux/Win XP system on a platform with both IDE and SATA drives, with the master boot record on a SATA drive:

1. fdisk all hard drives, and do NOT partition or format the IDE drive.
2. Install Win XP on the SATA drive, in a partition as you wish.
3. Install (K)(X)Ubuntu on the SATA drive of your choice, or on the IDE drive, partitioning and formatting during installation. It will automatically put Grub on the MBR where Win XP is.
4. Install any other Linux OSs that you may fancy, bearing in mind the cardinal rule regarding Grub: "Last Linux Wins" -- the applicable /boot/grub/menu.lst file that controls the boot menu will be written by the last OS that you install.  So, with a little planning, you can sequence your installation to have the boot menu look the way you want.  But if you change your mind later, you'll be hand-editing that last menu.lst file.

So, as a result of learning this stuff, I have a system that will boot (1) Ubuntu Feisty 64-bit, (2) Kubuntu Feisty 32-bit, (3) Elive development version, and (4) Win XP.  And the Linuces each can read and write to all drives and partitions on the system. 


I hope this helps!  :)

I already have a similar install.  I have an SATA Raptor for XP, 2 other SATA's for storage of files and video processing, 2 IDE DVD Burners, 1 IDE Seagate (slave to a burner) with ubuntu.

It all works pretty well - I chose my boot drive using a BIOS menu.  Grub has nothing to say about it.

I want to add another fast Raptor drive on one of my 3 open SATA ports - and move my Linux install from the IDE to the Raptor.  Then I'll remove the IDE and put it in another Linux Only machine.

Looks like I won't be able to make that happen.

---

### Post by dabl on 2007-07-09
Nope.

Putting your IDE drive in another machine, and re-installing Linux, is easy.  But I don't think copying or moving the Linux OS that is presently on the IDE drive to your new Raptor is going to work like you imagined.  But, if you want to be able to boot Linux or Win XP, then just plug in the new Raptor and install Linux -- it will configure itself according to the other hard drives, put Grub on the MBR where Win XP is, and life should go on pretty much as it is now.  After you've re-installed and configured your software packages, of course.  :neutral:

---

### Post by maestrobwh1 on 2007-07-09
There is sort of a way to "clone" in this situation but it isn't so much a drive/partition, but your installation.  If you are like me, you spent a bizillion hours to get an incredible system and "Why don't you just do a fresh install?" isn't going to be "good enough" answer.

Keep in mind that this is only in case you are going from IDE to SATA  or some other drive type.  Otherwise a disk clone using software should work... and I hear you can even move the partition.  You could do the first part of the following anyway, just in case.  I keep my linux partition backed up with clonezilla, at least on a bimonthly basis.    You could pretty much do this process if you want a similar install on a different machine with different specs.  It might crap out on you though if you are moving to a "higher bred" machine.  I.e. athalon to athalon 64, or to a different processor brand altogether.  Some of my programs (swiftfox for example) are dependent on processor architecture.

I got this from using "Ubuntu Hacks" Oxer, Rankin & Childers... a book I highly recommend... Hack 80... clone an installation.  This will not be identical, but it will install all of your old packages.  Your current system has to be up and working though... at least to some sort of shell.

And if you go about moving drives all the time, get the book.  There is a section in there about installing to a removable drive.  I am not selling anything here so that is as far as I will go.

First (save process):
A. Copy your apt package list from /etc/apt (sources.lst) and put it on a removable media (you do not need to do this if you have not added any repositories other than the ones that come with x,k ubuntu).

B. If you are only changing drives, and nothing else in your system, copy your xorg.conf from /etc/X11 if you have modified it in any way that makes it work better for you.  There might be other config files in your home directory and elsewhere, but I would just tweak the settings in the new install.  Too much mixing of old new, unless you really know what you are doing, could really foil (ruin) your efforts.

C: Do this from shell:
Copy and paste these longer commands.  It is hard to get it right otherwise with all of the characters and spaces.

D: In terminal>

sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list

And this will "print" packages to a file in your home directory called package_list and copy it to removable media.

Second (restore process):
You will then need to install x,k ubuntu from cd of the same distro i.e. feisty or edgy or whatever.  I think you can change this but it causes other issues, as new versions use different package names.  Better to restore original and then upgrade it when you are all done with this procedure?  

At this point, I would have enabled all of my repositories and installed some twin panel file manager... just because it makes this easier for anyone who is graphical.  I am a KDE guy, so I use krusader in root mode for the following things:

A: Copy your original  sources.lst to /etc/apt... or I suppose you could open both as root, and copy/past the stuff out of the one that would not be included in the new one.

B: In terminal >$
sudo apt-get update

C: Copy your package_list to your home directory on your new install.

D-1: In terminal >$
cat package_list | xargs sudo apt-get install 

D-2: Instaed, you could use the -f flag after apt-get so it will try to continue if there is a glitch, (unavailable package). It would look like:
cat package_list | xargs sudo apt-get -f install 

Go eat lunch.  Or better, go to your favorite book store and do as I did to learn of this stuff.  After this is all done:

I ALWAYS do this, even after updates

E: Terminal>$
sudo dpkg --configure -a

If it just goes the the prompt again, you are probably in luck.

Reboot and see what happens.

E-2: If you copied your original xorg.conf to a removable disk, and it was modified by you, go to root, rename the old one, copy it to removable, whatever, and then put your old one in its place... DO NOT do this if you never modified your old one.  If you did, you would know.  Also, DO NOT do this if you had video issues before and the new install seems to work well.  DO NOT do this before you have all your packages installed first.  This should be your very last step if you are going to do it at all... the last thing you need is for X to call for a driver you didn't install (yet).

I never did the "restore" part (the Second part), but I do have my package_list current and stored on removable media... just in case.

If anyone tries this and it is successful, post here.

---

### Post by crjackson on 2007-07-09
** @maestrobwh1 **

Thanks for the information.  Actually - I was trying to avoid having to reinstall video driver/codecs/flash/ etc...

Video drivers on this ATI card sometimes install without a hitch sometimes and at other times I can't get it right without reinstalling the whole OS from scratch.  Desktop configuration is not a big deal.  Mine is plain and simple.

Installing the apps. and having them WORK is however a big deal.  Especially the media players and getting them configured to work correctly.

It's looking like the only way is for me to start all over again - weather I like it or not.  I think a cloned drive would work were it not for grub/fstab.

I have actually cloned/restored ubuntu many times just like windows, but I have always restored to the same drive.

My process is to have a VERY stable install w/updats and working video driver.  Then I make an image of the drive once I'm satisifed with the basic install.

Next I do some minor little things like customize the desktop only to the extent of my theme, wallpaper, panels, ect...  Once I test everything for a few days I make a new image (overwriting the old one).

Next I start tweaking by installing the flash/required wrapper, media codecs/players, and test for a few days.  If all is well then it's time to overwrite my image with a newer one.

Then I install my apps. and test them one at a time.  Once I'm satisifed all is working well - I do the image thing one app. at a time.  Sometimes, something I install or change will break my system, then I just restore the image to the drive and no one (meaning Linux/Windows) knows anything has been changed except for me.

Now that I have my system solid, only short of a few tweaks and device drivers, I didn't want to have to start the process all over again as it's VERY time consuming.

I guess I'm out of luck on this one...

---

### Post by maestrobwh1 on 2007-07-09
Actually, as long as you installed your codecs via apt-get, aptitude, synaptic, adept, then all of your codecs should install... 

And the result should be just as stable as your old system.

Now if you installed things from source, i.e. tarballs... then I think you would have to redo that.

I actually used to back up my drive via a norton ghost disk, but when I switched to feisty, I had to do a restore and since I had done this with edcy more than once, I thought "NO big deal"  Both were ext3... but I tried to restore 3 different images I had for my feisty install.  It all went well, but it never could read the disk when it got to a certain point.  I tried fsck, knoppix, and all sorts of things to try to fix it and I had to start from scratch. 

I now use Clonezilla, and I use that hack I just wrote in a bin file that executes daily to create my packages.

Everything should technically install that was installed from a repository.  You won't ahve custom settings, but if you use Amarok to play your iPod and you need faac to read the aac files (m4a), it should all work.

Also, if you can read your disk via Knoppix, and you could copy/burn your home directory, along with /etc and /usr/local.  If you use the same name for your login, it should work to copy these things to a new system... at least in part.   I have more than once restored a home/.wine directory and had it all work:-)

Last... and this might be overkill but useful if you have a lot of storage space... install and use "simple backup" and have it back these selected directories for you to a tar file>

---

### Post by crjackson on 2007-07-09
> **maestrobwh1 said:**
> Actually, as long as you installed your codecs via apt-get, aptitude, synaptic, adept, then all of your codecs should install... 

And the result should be just as stable as your old system.

Now if you installed things from source, i.e. tarballs... then I think you would have to redo that.

I actually used to back up my drive via a norton ghost disk, but when I switched to feisty, I had to do a restore and since I had done this with edcy more than once, I thought "NO big deal"  Both were ext3... but I tried to restore 3 different images I had for my feisty install.  It all went well, but it never could read the disk when it got to a certain point.  I tried fsck, knoppix, and all sorts of things to try to fix it and I had to start from scratch. 

I now use Clonezilla, and I use that hack I just wrote in a bin file that executes daily to create my packages.

Everything should technically install that was installed from a repository.  You won't ahve custom settings, but if you use Amarok to play your iPod and you need faac to read the aac files (m4a), it should all work.

Also, if you can read your disk via Knoppix, and you could copy/burn your home directory, along with /etc and /usr/local.  If you use the same name for your login, it should work to copy these things to a new system... at least in part.   I have more than once restored a home/.wine directory and had it all work:-)

Last... and this might be overkill but useful if you have a lot of storage space... install and use "simple backup" and have it back these selected directories for you to a tar file>

Acronis TI 9.1 WS works very well.  I have restored ubuntu images at least 25 times while testing.  It works perfectly as long as you are restoring to the original drive (perhaps even a different drive too, provided it's going to replace the original drive on the same interface connector, I haven't tried this yet though).

---

### Post by maestrobwh1 on 2007-07-11
Actually, I have yet to need to restore since I use Clonezilla.  I hear Arconis is good, but Clonezilla is free.

The hack I spoke of earlier would only be better if something is drastically different in configuration and you could not get your old install/image to work.

I think the new Norton Ghost probably would work fine, as my version is a few years old.

---

### Post by Panzor on 2007-07-11
> **crjackson said:**
> Would be nice if someone made a utility LIKE Acronis TrueImage that would handle the issue...

This is all you need to do. Save your /home folder onto one of your other hard drives. This saves all of your configurations and files. Next, install Ubuntu onto the desired drive. Overwrite the old /home folder to the new one. Now, "sudo aptitude install" everything in one, long list (separate each name by a space after the word 'install' and you're old system is back!

You're probably just thinking about it too hard. Debian OSs use very easy ways to switch OSs and retain data (i.e. Debian to Ubuntu or Ubuntu to Foresight, etc). The reason they don't make a cloning program is because there is no need. Copying /home and installing the programs again on a fresh system would take less time than an OS clone.

---

### Post by maestrobwh1 on 2007-07-12
Actually, that is good to know.  I still think having the package list to print out first, then after making a fresh install, import the list to apt.  I have a lot of apps installed, and had to do some tweaking that I don't think I would remember how to do.  I had to put a bunch of stuff into my xorg file for example, to make fully use of my video card.  This is NOT a complaint.  This is why I have it copied.

At any rate, I do agree it is easier than I thought with your info... and with the Feisty Distro, it was way easier to get everything working than in the Dapper days.  Toss in Automatix... and you can get on the road pretty quick.

Clonezilla does work really fast.  It backs up my partition in less than 5 min.  I remember installing kubuntu from scratch when I did some crazy thing that made my system unusable and did not have a working image from Norton... it isn't that easy for those of us who don't have a (half) day to rebuild a system.  I guess easy is the wrong term.  Time-consuming.  I have 10 min here and there to do backups, so perhaps in the long run, I am spending more time:confused:

I also was very "verbose" in my post because I had found early on in my linux days that the ones most willing to help were the ones who knew the most, of course, but were short on detail for the novices.

---

