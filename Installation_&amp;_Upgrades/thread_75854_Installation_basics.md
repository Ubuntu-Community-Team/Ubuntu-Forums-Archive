---
title: "Installation basics"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Samy_Merchi on 2005-10-14
Okay, I'm ready to try and install my first Linux. I'm trying to migrate from Windows XP. I have a few questions, to clarify some points I may run into during my upcoming installation process. I couldn't easily find answers to these in the Wiki.

I have a 120GB hard drive, which is currently partitioned to 10GB (for Windows) and 110GB (for files). I've spent the last couple of days cleaning the second partition to prepare it for shrinking, to make room for Ubuntu. Now, I'm *assuming* that the Ubuntu install CD installer will allow me to shrink the second partition to make room for a third partition where I will be able to install Ubuntu. Is this correct? Also, the actual data on the two existing partitions will not be wiped in the repartitioning process, is this correct? (Yes, I've made backups of the most important stuff just to be sure.) Essentially, I should be able to convert empty space on my D-drive into a third partition to install Ubuntu into, correct? And this should leave the C- and D-drive datas untouched if everything goes right?

How much space do I need for the Ubuntu partition? Can I store most files (music, documents, et al) on the Windows D-drive still, and access that partition both from Windows and Ubuntu? If I try to keep most of my actual files on the shared file partition, how much space will I need for the actual Ubuntu OS install for its own partition? Should I be aware of any particular configuration options or tricks I should do in order to have the fileshare-partition available as a user (/usr?) partition in Ubuntu? I assume a default installation would place my usr, home (or whatever it's called in Linux) 'My Documents' directory on Ubuntu's partition? What do I need to do if I want my 'home' for files to be on the shared partition instead?

I'd appreciate any answers.

---

### Post by Samy_Merchi on 2005-10-14
Okay, the installation went fine, although I was chewing on fingernails really hard during the partitioning phase, hoping that everything'd go okay. No problems with it have surfaced so far.

However, I'm having some problems with mounting my Windows partition. If I go through System > Administration > Disks, I can figure out how to mount a partition (though the way Linux organizes its filesystem seems confusing to me still -- on the Select Mount Point Path window, what is the purpose of the left pane? I can add something there and remove that something, but I don't understand what that's for? So I just went to File System and created a new folder (/files) there and mounted the Windows partition on /files.

The problem emerges, however, when I go out of Disks Manager (which apparently seems to be running under root privileges, whereas normal operation doesn't). In Disks Manager you can access the other partition because of your privileges (/files is set to 500 unlike navigable directories who are 755), but outside the manager you just get an error message about not having privileges to access that folder. This seems to me to be against the "it just works out of the box" mentality of Ubuntu, so I'm hoping somebody can clarify what I should do not. Is the best option to just call up a terminal and do a chmod on the folder?

Also, the thumb button on my mouse doesn't do anything -- I couldn't find anything under Preferences > Mouse to configure it. Does Logitech have Linux drivers on their site?

---

### Post by BLTicklemonster on 2005-10-14
I saw once before, how to configure mouse buttons, but for the life of me I can't find it in here now! If I ever find it again, I'll come link it in here for you. I have a logitech, too, and I'm too lazy to go up and hit the arrows, too.

---

### Post by Samy_Merchi on 2005-10-14
Is it really true there's no stable read/write access available for NTFS partitions? If so, is there a way for me to convert my Windows partition to FAT without losing the data on it?

And here I thought NTFS was supposed to be superior to FAT... :(

---

### Post by toujours on 2005-10-14
I have an NTFS partition for Windows program files, a FAT32 partition for user files and my Ubuntu (ext3 and swap) partitions.

My stuff goes on the FAT32 whether it be Linux or Windows. That's it. There's a line or two that needs to be typed in Ubuntu in order to automount the FAT32. It's described in the Ubuntuguide..

If you have space on your hard drive, make a FAT32 partition, transfer your NTFS user data onto it and then you're done !

---

### Post by Samy_Merchi on 2005-10-14
I have one drive that has three partitions, one for Windows OS (NTFS, 10GB), one for Windows files (NTFS, 100GB) and one for Ubuntu OS (ext3, 10GB). In order to convert the middle partition from NTFS to FAT, do I need to burn all 100GB of content to CDs, then reformat as FAT, then restore everything there from the CD backups?

---

### Post by Samy_Merchi on 2005-10-14
Okay, I figured out how to hash out the mousewheel and thumb button so they work, but in order for them to work, I will always need to run a command at startup. Does Linux have a file like Amiga's startup-sequence where I can put cli commands that auto-execute at boot?

---

### Post by Samy_Merchi on 2005-10-15
Here's one trick that I got to work, in order to easily load the xmodmap command.

(I don't feel like remembering the syntax of the xmodmap command in order to type it in every time I boot, so I need an easier way to autorun it.)

I put it in ~/.bashrc

That way, the xmodmap command gets executed every time you start up a terminal window. So basically, after you boot, open a terminal window (you can close right away if you don't need to do anything with it), and from then on, the mouse buttons should be mapped correctly.

---

### Post by Jussi Kukkonen on 2005-10-15
[QUOTE=Samy_Merchi]Okay, I figured out how to hash out the mousewheel and thumb button so they work, but in order for them to work, I will always need to run a command at startup. Does Linux have a file like Amiga's startup-sequence where I can put cli commands that auto-execute at boot?[/QUOTE]
Open System/Preferences/Sessions, add your command in the Startup commands tab. 

If you want to learn more about linux startup stuff, check out /etc/init.d/* (which contains the startup scripts) and /etc/rc?.d/* (One directory per runlevel. Directories contain links to the actual scripts). 

And no, writing to NTFS is not possible (not safely anyway).

---

### Post by Samy_Merchi on 2005-10-15
The startup programs tab didn't work for me for some reason, but saving the session worked great. Thanks!

---

### Post by Samy_Merchi on 2005-10-15
Ah damn, saving the session only seems to work if I log out with a terminal window open (so that it has to open a terminal window at startup, and consequently loads .bashrc then). Looks like I'm back to having it in .bashrc. It doesn't seem to save the modded map anywhere even if I save session.

---

### Post by jaws862 on 2005-10-24
How exactly did you get the thumb button working?  Currently mine works like the middle button, ie quick copy/paste.  I'm hoping I can get it to work as a Back button, ie ALT+[Back Arrow].  All the editing I've tried has involved xorg.conf, which causes X to crash.  Also, posts have instructed using evdev, which apparently requires the xorg sdk, which doesn't seem to exist for ubuntu [?].  also, if you couldn't tell, i'm pretty much a newb, so any advice would be appreciated.

---

### Post by BLTicklemonster on 2005-10-25
[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

Here's for a logitech mouse.

---

### Post by flower on 2005-10-25
first of all - yes ntfs is superior to fat32 :))) just M$ don't provide easy way for writing in ntfs (as far as I understand the problem)

and yes - there are only expiremental packages which provide linux to write to ntfs and win to write to ext2/ext3 partitions. you can install but you somewhat risc your files ...

I use following partitions : 
C - ntfs for windows and program files
D - ntfs for music & movies 
G - fat32 for shared (win and lin) files
ext2 - ubuntu

this way I can read my music and movies from linux / windows,
and I use the fat32 disc to read/write files from both OSes

in order to make a fat32 partition do this : 

1. free enough space on ntfs partition you are going to cut from (say 15G)
2. defragment this ntfs partition
3. use Partition Magic to resize the ntfs partition and free space on your hdd (say 10G)
4. use Partition Magic to create the new fat32 part. in the free space
5. mount rw the new partition from ubuntu :)

---

### Post by jaws862 on 2005-10-26
Well, part of my problem is when i run xev, both the middle click and the thumb button are charted exactly the same....any suggestions?

---

### Post by jaws862 on 2005-10-26
OK so, with the evdev driver it recognizes the thumb button as button 6 instead of 2.  Which is sortof weird, since evdev wouldn't work before...I had found numerous posts [from google] quite similar to the one you pointed me to before and every time i tried to use evdev, X would crash on startup and i'd have to restore xorg.conf.  I'm not sure what the difference was here, I customized the phys dev etc before...  I have a feeling perhaps I made a mistake typing in the handlers.  Oh well, at least it works now!  Thanks

---

### Post by BLTicklemonster on 2005-10-26
Different direction:

I want to have drive one as ubuntu, and drive two as XP. Physically different drives. I create a file in Ubuntu. 

Um precisely what and how? I don't get a pin pointed answer anywhere. Either that, or I'm totally overwhelmed by the information.

I was told this by someone who uses lilo:

other=/dev/hdc1
label="WindowsXP"
table=/dev/hdc
map-drive=0x80
to=0x81
map-drive=0x81
to=0x80 

but that was incomplete, exactly what do I put for grub, and where do I put it?

How do I use it?

Will Timmy ever get out of the well?

:rolleyes: 

Thanks.

---

