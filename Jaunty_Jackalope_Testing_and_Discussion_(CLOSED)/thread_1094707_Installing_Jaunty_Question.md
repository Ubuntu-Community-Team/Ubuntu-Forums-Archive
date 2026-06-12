---
title: "Installing Jaunty Question"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by masterkoppa on 2009-03-12
I have recently been testing Kubuntu 9.04 and it seems very promising. This testing has been going on in my testing desktop. But i really want to try Jaunty in my laptop. Currently I have a really messed up Kubuntu 8.10. So I would like to make a jump to Jaunty instead of re-installing. 

My question is would it be possible to re-size the current partition, use the free space to install Jaunty, transfer all the files from Kubuntu 8.10 and resize the jaunty partition to use the whole disk.

Thanks in advance.

---

### Post by Herman on 2009-03-12
Yes, that should be possible.

You would be best advised to make a backup of all of your files to some other media, such as another hard drive or an external USB drive though, for two reasons.
1. In case anything goes wrong with your partition table or with the hard disk itself. Although rare, you should always protect yourself from the possibility of such a disaster.
2. Linux partitions can easily and quickly be resized from the left or inside edge, but resizing from the right or moving the right-hand end of a Linux partition is very slow. It's the sort of thing you start in the evening and let run all night while you're asleep.
On the other hand, it only takes half an hour to install again, so personally, I prefer to just install again after copying all data out rather than tie my computer up all night with the resizing process.

Regards, Herman :)

---

### Post by Dr.Suave on 2009-03-13
I just downloaded and booted the 9.04 Alpha 6 disk, and found that on boot the disc was actually Intrepid Ibex. The disk is titled 9.04, but boots 8.10!

Anyone know whats going on/have also downloaded Alpha 6?

---

### Post by masterkoppa on 2009-03-13
Thanks for the quick reply. Then only reason I want to do this process instead of just backing up and restoring is the long time it takes to restore all the backup files. Since I don't have an external drive I do this through a NAT, which is very slow. But doing this process will probably be faster to move the files from one partition to the other.

Also, I haven't downloaded Alpha 6 but I would recommend you to download the Daily Builds, these are a little more unstable, but are really up to date.

---

### Post by Herman on 2009-03-13
Well, your idea is good, that's the way I do it myself, I install the next version of Ubuntu beside the existing one and then copy the files from the old /home/username folder to the new one, but I do have my data on another hard disk.
The important data in the /home/username directory is in the hidden files, the ones in directories with names beginning with a dot. In the .evolution directory you will find your email, addressbook, calendar, memos and tasks, in the .mozilla directory you will find your firefox bookmarks. There will be other directories which store the settings and data for many other programs you might have installed. I use a program called 'Password Manager', so it is very important for me to copy the hidden directory which belongs to the program and contains all of my passwords in an encrypted form. There may be other hidden directories that are important to you, so just be sure you click on 'View'-->'Show Hidden Files' and copy the ones you need.

For most programs you can just copy and paste the associated hidden file from the old installation to overwrite any existing hidden file in the new installation if one exists.
For Evolution, you should configure Evolution in the new installation first, so that there will be a .evolution directory containing the other directories which you can overwrite.

For .mozilla, it is different now, it used to be simple but now we have to 'export' our bookmarks in the old installation to a file and 'import' that file again in the new installation. I don't think just copying the .mozilla directory will work.
For most programs though, you can just copy and paste the user's hidden files to the new installation and when you install your favorite programs they will find the user's hidden files containing your old settings and start using the same settings as you had in your old installation. Most of the time that's good, but sometimes it might be better to start fresh, that's up to you to decide what you want to do for each program.

For me I like to just leave the old operating system there instead of deleting it. I have lots of hard disk space. Then when the next new Ubuntu version is released or gets advanced enough, I install it over the oldest installation and test it.  Then after a while when that version is ready I transfer the settings back across in the same way and make that one my main operating system. Some of my freinds also like having two Ubuntus, one for their main operating system, and one for an auxiliary. That's a good way to do things if you have enough hard disk space.

---

### Post by Rocket2DMn on 2009-03-13
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by masterkoppa on 2009-03-13
Thank you for this great hint. I have only one question regarding this, will it matter if I change from 32-bit to 64-bit.

Thanks in advance

---

### Post by Herman on 2009-03-13
> Thank you for this great hint.You are welcome. But since you had Kubuntu and you're moving to Ubuntu, you might find that there are some programs that are KDE based and some might not share settings with Gnome applications, I'm not sure. 
You probably have Konqueror instead of mozilla firefox, and you probably have kmail instead of Evolution mail, I'm not sure if the bookmarks and mail format will be the same between KDE applications and Gnome Apps. 
But certainly all your files will transfer easily.
> I have only one question regarding this, will it matter if I change from 32-bit to 64-bit.I'm not sure but I don't think so, not as far as files or user settings are concerned.

---

### Post by masterkoppa on 2009-03-15
Thanks for your tips again, but after doing this I found out that the main problem I was having with my kubuntu installation, was partially, due to settings. So i just dumped it all out and started out in a new environment.

Thanks for all your help again. It's because of people like you that ubuntu is one of the best distros out there.

---

