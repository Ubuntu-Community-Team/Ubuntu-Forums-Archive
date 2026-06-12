---
title: "Partitioning help with /home"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2011-01-29
Situation: Ubuntu died on me. I was trying to uninstall the Nvidia drivers after some really troublesome glitches that wouldn't allow compositing. So now all i have is the command prompt. I don't fee like dealing with it again even though this glitch plagued me in my 5 last ubuntu installations. 

What I want to do: Instead of trying to figure out how to install the Nvidia drivers through a command prompt I want a fresh start. Thing is that this time I want multiple Operating systems. Right now I'm stuck with windows 7 but i want about 7 other Linux operating systems. 

Which operating systems i want:
1. Windows 7 (already have)
2. Ubuntu 10.10 Which i hope will continue to be my default
3. Ubuntu 11.04 Natty I can't wait for this release and I desperately want to test it. Just wondering but does it update itself everyday?Is it a nightly build or do I constantly have to update every time a new RC or beta or whatever comes?
4. Mint OS: I heard its better than Ubuntu, I want to check it out
5. Pinguy: Same as Mint OS, I want to see what really sets them apart
6. Arch Linux: I don't know if this might be destructive to my other operating systems but I want to get a better experience with the Terminal, by the way does the Ubuntu terminal differ much from the Arch Linux terminal? Can it use .deb files?
7. Fedora Linux: This is really just a place holder for other opating system i want to try such as chrome os if i can find a way to get it installed or even mac osx again if i can find a way. 

Questions: So do you guys think this might be too much or unreasonable?

Will I be able to, or better, should I use teh same home drive? Are thee any risks to using the Same home drive for all of them? Any limitations? 

Can they affect each other?

Oh and I have a 640 gb hard drive but i want to use about 150gb for windows and my HP computers back up thingy. The linux stuff is all going to be on a extended partition. If I use teh same home should it be very large or liek a standard 10 gb? The root for each should be 20 gbs? ;I'm not sure. 

So yea PLEASE HELP ME WITH THIS. If anyone wants me to describe afterwards how each of these works for a newbish person like me, ill be sure to respond and stuff.

---

### Post by oldfred on 2011-01-29
You do not want to share /home but can create /data to share all you data. The only issue may be Fedora. Different distributions use different user id numbers so the ownership of files between Debian based on Fedora based has to be adjusted. There are several posts on that issue somewhere here recently, but I do not sue Fedora.

Some say correctly that you can use the same /home partition but then have to use different users so to me that defeats the purpose.

If you do not hibernate you can have just one swap which should be 2GB or the size of RAM. I would just create 20GB partitions for each root and include /home in /. If you want you can then copy those settings you like to the next install, but I find I do not copy as much as I thought. I do move all hidden data directories like Thunderbird, Firefox, & Kmymoney into my /data so any data is not in /home.

If sharing data with windows you should also have a NTFS shared data partition. It is best not to write into another system as that can cause problems. You can read and if necessary make repairs, but do not plan on regular writing.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

I use linking like these instead of bindfs:
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments, I now mount my data partition in /mnt.
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I export all my installed apps and with Ubuntu can reinstall all of them with each new install.

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

I found after going thru all this for several Ubuntu installs on two computers that I could manually do most of it from command line, list history and copy history to bash file. Then it is automated. May only work with Ubuntu and not with Fedora.

---

### Post by daksai3 on 2011-01-29
Thank you for all the help but there are a few things i need for clarification. 

> Different distributions use different user id numbers so the ownership of files between Debian based on Fedora based has to be adjusted.
So would it be alright if i used the same /home for two Debian based distributions such as Mint OS and Ubuntu? Could i also just transfer my .config files?

Oh and i'm a bit confused as to what exactly is on the home directory. I know it hold the configurations files, but does it also hold desktop configurations like the background image, fonts? does the root also hold configuration files for some programs???

> If you want you can then copy those settings you like to the next install, but I find I do not copy as much as I thought. I do move all hidden data directories like Thunderbird, Firefox, & Kmymoney into my /data so any data is not in /home.

Is that situation that you are describing for backing up? Could I simply mount a directory inside the /dara as my home directory when i'm installing ubuntu? And as a side note i also want to share my /data directory with windows 7 so as to place all my documents there, would it be possible to have a ext4 home directory in the ntfs partition? am i missing something?

> If sharing data with windows you should also have a NTFS shared data partition. It is best not to write into another system as that can cause problems. You can read and if necessary make repairs, but do not plan on regular writing.

do u mean that i need another partition in order for sharing data?
could i use one partition for sharing data and the multiple home drives?

> I export all my installed apps and with Ubuntu can reinstall all of them with each new install.

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

is this only for the names of each program? is it possible to actually move the root files or whatever similar to that in windows and moving program files? 

on one of the links it mentions that /data is good for backing up the home directories, does that mean it has to be ext4 or can it be ntfs?

---

### Post by oldfred on 2011-01-30
Folders are inside your partitions and each partition has to have a format ext3, ext4 etc or windows compatible NTFS. Folders do not have a separate format. All Linux system folders had to have Linux formats including /home. You cannot share /home with windows, but can link or mountyour NTFS data back into /home.

Do not share /home even with similar distributions, it is not worth the risk of problems. Copy some settings if need be. Setting are not large in the scheme of things. I still have my .wine in /home and it is 750MB and my /home is just over 1GB.

You have to understand system from user. System settings are in /etc. User settings are in /home. So all your user settings are in /home and normally all your data files. But it is easy to move data.

This is the type of thing you just need to do. Start off partitioning with windows (must be primary partition), several root partitions, swap & two data partitions one NTFS & the other ext4. Leave space for future on your drive for the future installs and get started. I think you need to walk before you run and as you start using system you will find you may want to do things differently. I find what I though was best for me last year has changed this year. But every few years I buy another drive so I have space to reorganize.

---

### Post by srs5694 on 2011-01-30
> **daksai3 said:**
> So would it be alright if i used the same /home for two Debian based distributions such as Mint OS and Ubuntu? Could i also just transfer my .config files?

Oh and i'm a bit confused as to what exactly is on the home directory. I know it hold the configurations files, but does it also hold desktop configurations like the background image, fonts? does the root also hold configuration files for some programs???

First, let's be clear about something: Linux is a multi-user system. Every login user has a home directory, which is a subidrectory of /home. On most of my systems, my home directory is /home/rodsmith. Somebody else who uses the computer could have a different home directory, such as /home/fred, /home/betty, or /home/r2d2.

Home directories hold user data, including the data files you normally think of (MP3s, word processing documents, etc.) and configuration files (which normally reside in files or directories whose names begin with a dot, like .bashrc). There are also system-wide configuration files, most of which reside in the /etc directory tree. One problem with sharing a /home directory between distributions is that *if* both distributions try to use the same home directory, the configuration files may be incompatible. For instance, one might reference a font or icon that doesn't exist on the other; or one might use a more recent software version that uses a different configuration file format.

Most fonts, icons, and other support files don't exist in the users' home directories; those are system files, most of which reside somewhere in /usr.

See the [Linux FHS documents](http://www.pathname.com/fhs/) for more information on where everything goes in a Linux system.

> Is that situation that you are describing for backing up? Could I simply mount a directory inside the /dara as my home directory when i'm installing ubuntu? And as a side note i also want to share my /data directory with windows 7 so as to place all my documents there, would it be possible to have a ext4 home directory in the ntfs partition? am i missing something?

Linux home directories normally reside in /home, as I stated. You can change this and put home directories elsewhere; however, there's seldom any reason to do so, particularly on a new Ubuntu installation. Linux requires filesystem features in the home directory that aren't supported by NTFS, so you can't use an NTFS partition as /home; and since Windows support for Linux-native filesystems (even with third-party drivers) is poor, giving Windows access to /home is pretty pointless.

It's generally best to create a separate FAT or NTFS shared-data partition to hold data that will be shared between both OSes.

> on one of the links it mentions that /data is good for backing up the home directories, does that mean it has to be ext4 or can it be ntfs?

I don't know what whoever wrote that meant; however, you can back up any Linux files to any filesystem you like if you use a suitable carrier format. For instance, you could create a tarball (using the "tar" utility), which will be a single file that holds as many files as you like and that will uncompress back into the original files, including the usual Linux filesystem features.

[quote=oldfred]Do not share /home even with similar distributions, it is not worth the risk of problems. Copy some settings if need be. Setting are not large in the scheme of things. I still have my .wine in /home and it is 750MB and my /home is just over 1GB.
[/quote]

I disagree with oldfred on this point. So long as you use separate user home directories, there's no problem with sharing /home between installations. Creating a separate /data partition for Linux makes your system weird and inelegant from a Linux standards point of view.

That said, if most of your data will be shared between Linux and Windows, there might be no point to creating (and sharing) a /home partition; if your home directories will house just a few megabytes of configuration data, there's no point in creating a separate partition for them. The fact that you can't put Linux home directories on NTFS means you'll have to put most of your user data in a separate partition that you access in some other way.

Personally, I wouldn't do it that way, since Linux's NTFS access has a number of problems; however, I seldom boot Windows at all, so most of my files are Linux-only (or are accessed over the network using file-sharing tools). If you mainly use Windows and just want to try Linux, putting most of your files on NTFS may make sense, at least for the moment.

---

