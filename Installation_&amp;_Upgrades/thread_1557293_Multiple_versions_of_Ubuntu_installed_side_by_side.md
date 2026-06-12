---
title: "Multiple versions of Ubuntu installed side by side, reduce to one"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by laserman on 2010-08-20
Over the past few months, I have installed various versions of Ubuntu 10.04 side by side on the same hard drive. I have been successful in starting the computer and going to the version of my choosing, seeing the differences and trying to settle on one.

I have noted posts regarding removing Ubuntu and keeping Windows or removing Windows and keeping Ubuntu. 

Is there a post previous to this that goes into detail about removing other Ubuntu versions and keeping only one? 

Thanks.

laserman

---

### Post by Mr.Comix on 2010-08-21
format the partition of the hard disk that the version of Ubuntu which you want to uninstall has been installed on

i am not sure whether this way works :)

---

### Post by Herman on 2010-08-21
I can't think of any specific previous posts or how-tos on this, but probably there would be a few around. Maybe under 'how to back up and restore in Ubuntu or something like that.

Ubuntu is a fast moving operating system, always under development and  with a new release every six months, so moving or copying the user files  forward into a new release is a frequent task.

How soon we abandon our older, more stable system and move into a newer release is a matter for the individual preferences.
Most of us want to make the current stable release our main operating system and some of us might have another Ubuntu installation or two, such as maybe a testing version of Marveric Meerkat, or their old stable operating system, Karmic Koala, which will be supported for a long time to come.

Besides the obvious ordinary user files to be moved like music and videos, there is email, calendar, memos and tasks from .evolution, bookmarks from .firefox, and other files and settings you may want to carry with you for many of the other programs you might have installed. GPass is one of mine, so I always carry forward the .gpass folder.

The most important thing for new users to know about it is to look for the hidden files in the home folder, those are the ones with the dot in front of their file names. 
You can see them if you click 'View', 'Show Hidden Files', when you're in your /home/username directory.

In times of old, I used to configure evolution in the new operating system, then close evolution and  open the older Ubuntu's /home/username folder and copy the .evolution addressbook, calendar, memos and tasks and paste it into my newer installation's .evolution folder, to over write the new empty files that were created during setup.
Then when the new evolution is opened again, it would contain all my old addresses, calendar appointments, email, memos and tasks. 
Sometimes it wouldn't all show up until after a reboot for some reason, I don't know why.
I'm not sure if that's the correct way to do it anymore, but it's quite simple, and it works. 
There may be a more civilized method like using an 'export' and 'import' tool.

Firefox bookmarks used to be similar, I used to just look for the bookmarks .html in the .mozilla/firefox/UUID directory somewhere and copy it into the corresponding location in the new system's .mozilla files and that would move forward my old bookmarks.
Now I think we're supposed to use the export/import functions.

I also use and recommend a great app called 'Password Manager' and all of my passwords are stored in an invisible folder called .gass, so to carry forward all my accounts and password info, I first configure Password Manager in the new installation, then copy forward my old .gpass directory, to overwrite any .gpass directory that;s there. Then as soon as I open Password Manager and type in my master password, I have access to all of my other account details and passwords.

There are apps we can install like simple backup and simple restore that  can help take way some of the work involved in this kind of endeavor.

When overwriting files, there is always the risk of losing work. One problem with multi booting is if we have two or three or more copies of a file with the same name in different operating systems, and have worked on the file separate times in different systems. Sometimes it can be a time consuming job open files and read them to try to decide which file to keep, or to amalgamate the best information from the various copies of the same file, before deleting the stuff we don't want.
That's one of the pitfalls to try to avoid when multi booting.
A shared data partition or an external USB disk for common data storage can help to avoid that problem to a great extent.
An even better way is to use Ubuntu One and Sync our data.

There are times when the command line comes in handy too. There's also the -u option for the cp command that will cause it to only overwrite a file if the one being written is a newer version of the same file, (and therefore presumably more up to date).

Don't just copy all of the /home/username files from one installation to  the other with any sudo command because there are some files in there  that are unique to the operating system they belong in and you can bork  your system and you will need to re-install. I forget what the exact  error message was, it has been a long time since I tried that.
However, it is possible to delete all the operating system files in a  partition leaving only the /home/username directory and then turn that  inside out and have it set up as the /home partition for a subsequent  new Ubuntu installation, I have managed to do that a while back as an  experiment and it worked for me when I tried it.
Another idea that's quite popular is to have a separate /home and share it between more than one operating system. That way you never have to more your files. 
The downside is, you accumulate a lot of garbage that way and no matter how large you make your partitions, or how carefully you plan, you will eventually run out of room in one or another.

Like Mr.Comix said in the above post, once you're absolutely certain there's no data you don't have a backup copy of that you haven't moved forwards into your new main operating system, you can once and for all kiss your older installation goodbye and delete the old partition and reformat it, or resize your new main operating system to fill the now vacant space.

Sorry for the long answer, you did say you wanted a detailed answer, but I hope I didn't bore you. Are you still awake? 

Regards, Herman :)

---

### Post by Herman on 2010-08-21
Oh, and you should make yourself a **[GRUB2 Rescue Disk]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM") **if you haven't already done so, because if you delete the operating system that GRUB is installed from, you will temporarily lose your ability to boot in the normal way.
A **[GRUB2 Rescue Disk]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")** is a good thing to have around and I think everyone should have one.

Regards, Herman :)

---

### Post by laserman on 2010-08-22
Lot to digest...but it centers on what I was thinking on two levels. 

One, I can backup and install new, then restore. I saw a posting  at [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) that talks about backup and restore but I haven't dove into it. 

As far as data, I just grazed the top of all of the variants. Not much data to concern myself with with the exception of the .deb packages. That gets a bit wearing having to update them in the individual os's. I did stumble across a couple of posts talking about local repositories but that will have to take a day in itself. One local repository post I saw stated that if you wanted to make your own local repos, get ready for 35 - 40 gig download. My bandwidth wouldn't allow that. I'm going to have to take that one in small bites. Once I get it downloaded, it would be time to refresh again, 

:lolflag:.

Mr. Comix did make a good point about deleting partitions. My hesitance in that was messing up Grub or Grub2. I would lean to this one as it is the lesser of two evils and I will make a Grub2 Rescue Disk. Is Grub2 Rescue straight forward? Any leads on this dive or just delete partitions and reboot?

laserman

---

### Post by Herman on 2010-08-22
> Not much data to concern myself with with the exception of the .deb  packages. That gets a bit wearing having to update them in the  individual os's. I did stumble across a couple of posts talking about  local repositories but that will have to take a day in itself. One local  repository post I saw stated that if you wanted to make your own local  repos, get ready for 35 - 40 gig download. My bandwidth wouldn't allow  that. I'm going to have to take that one in small bites. Once I get it  downloaded, it would be time to refresh again, The .deb packages are stored in /var/cache/apt/archives/, and you can include them in a backup if you wish, however there are two things be be aware of.
Firstly, it's only good to restore the .deb packages to a new installation of the same architecture and the same version as the operating system they came from. You will quite likely damage your system if you try to install packages not designed for it, so be careful about that.
Secondly, the .deb packages may be superceded and go out of date quickly, some more quickly than others, but it probably wouldn't be worth bothering with them if they have been stored for too long.

By different versions of Ubuntu I mean like [Ubuntu 9.04]("http://www.ubuntu.com/getubuntu/releasenotes/904overview") Jaunty Jackalope, [Ubuntu 9.10]("http://www.ubuntu.com/getubuntu/releasenotes/910overview") Karmic Koala, or [Ubuntu 10.04]("http://www.ubuntu.com/products/ubuntu/release-cycle") -  Lucid Lynx. Avoid mixing packages between those.

It doesn't matter if you mix different desktops, like Xubuntu, Kubuntu or Ubuntu. As a matter of fact several of the various desktops can be installed simultaneously in the same operating system and we can choose which desktop to log in to at the login screen.

By architecture I mean i386 or AMD64, as far as I'm aware, it's not a good idea to mix packages from one architecture with the other.

It's easy to copy the .deb packages from the /var/cache/apt/archives/ directory of an operating system to be deleted, but to get them into the same directory in another operating system you'll need a sudo command,
```
sudo cp Backup/Packages/*.deb /var/cache/apt/archives/
```Where your .deb files are located in a directory called Backup/Packages, if not just alter the command with the file path to suit your actual circumstances.

After copying them to your /var/cache/apt/archives/, you just install your software in the regular way, but if you watch carefully you may notice the absence of the downloading phase of the operation.

---

### Post by Herman on 2010-08-22
> My hesitance in that was messing up Grub or Grub2. I would lean to this  one as it is the lesser of two evils and I will make a Grub2 Rescue  Disk. Is Grub2 Rescue straight forward? Any leads on this dive or just  delete partitions and reboot?**Everyone should make themselves a GRUB2 Rescue disk**, they're easy to make and simple to use, and only costs the price of a blank CD and a few minutes of time.

This link should still be up to date about how to make one,  **[GRUB2 Rescue Disk]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM"),** and as soon as I get time I'll try it again myself to make sure.
When you use your GRUB2RESCUE CD. you should expect it to boot to a GNU GRUB Command Line.

**From your GNU GRUB Rescue CD's Command Line** you have two choices,

**either**
**1)** From GNU GRUB CLI Mode, you can easily run the command: configfile /grub.cfg    ... if you want to see your own familiar GRUB Menu and boot from that.

**or**
**2)** Otherwise, it's not really so difficult to boot from the GNU GRUB Command Line as many people might imagine. Try this How-To here,** [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") - Rescue your System ** (this is also linked to from the first link).

It's a good idea to practice with it once or twice when you *don't* really need it just to become familiar with it. Think of it as something like a fire drill.
With only a little practice, coping with any computer with booting troubles will not be a problem any more.
Knowing you can always boot any operating system no matter what (well, almost), is a great confidence booster.  :D

---

### Post by laserman on 2010-08-23
Your input has been a big help. I have a Grub2 Rescue disk made and in the process of cutting and chopping the different versions of Ubuntu 10.04, weeding down to one on the hard drive. Also, thanks for the input about the.deb backup. I knew where they were at but hadn't thought about the copying. All of these variants I have been working with are 10.04 so they should all go well together. 

Again, thanks. Like your icon. I manage 12 acres with cattle and seeing the windmill still makes me want one. Take care.

---

### Post by Herman on 2010-08-23
That's our 'Wirilla Windmill' and it's a 35' Comet Windmill, and it's about 72 years old.
35' is not the height of the tower, (which is not such an important measurement for windmills), but the diameter of the wheel. Since it's off topic, here's a link in case you're interested in more on the [Wirrilla Windmill]("http://picasaweb.google.com/herman543/WirrillaWindmill#").

---

