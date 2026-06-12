---
title: "[SOLVED] Backup of profile and personal settings / location?"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-10-24
I'd like to make backups of my desktop-profile and personal desktop settings, if possible, also from installed apps.

Is there a program that can perform such things? What folder would I have to backup to protect the basic profile at least (Xfce settings, desktop settings, Xorg settings, mount settings, network...) ?


Thank you for info!


perixx

---

### Post by Ivo Moelans on 2007-10-25
Settings an so on are kept in your home directory in hidden files. Hidden files begin with a dot. To see them go to your home directory and press Ctrl+H.
To back up my home directory I use rsync (see: [http://www.linux.com/feature/117236](http://www.linux.com/feature/117236)), but there are  other programs as well.

---

### Post by perixx on 2007-10-25
hi...

I thought so and have already made a copy of the whole /home/USER directory recursively. 

But I've read about other locations where personal settings are stored - somewhere in the /var, in the /usr/local and /etc directories ... con you confirm these and which exactly, if any?


perixx

---

### Post by Ivo Moelans on 2007-10-25
Sorry: I know system settings like Xorg etc. are kept in different locations. Am not to sure myself whether it is very useful to make a backup of these since Ubuntu seems to make most of these itself and/or they are easily configurable with the items in the preferences and administration menus.

---

### Post by perixx on 2007-10-25
Well, I'm determined to have the following settings saved with an update:

- Taskbars / Systray (with all symlinks and positions)
=??
- Additional desktop-symlinks (incl. icon settings)
=?? 
- Xorg's (monitor and card settings / refresh rates) 
= /etc/X11/xorg.conf
- installed programs settings and codecs
=/usr/share/applications ? // =/usr/lib/codecs
- mime-type linkages 
=/etc/mime.types? // /usr/share/mime-info? // /usr/share/mime? // /usr/lib/mime/packages? /usr/share/xfce/mime?

Where ? means that I'm not sure of the exact positions and ?? means that I've got no idea at all!

I'd be glad if you could help out... ;-]

So I'd need a backup program, that either saves those settings automatically or let me specify additional paths/files for the backup ('sbackup' might be able to do it and another program I cannot remember the name of now... I believe grsync can't do that, can it?)


perixx

---

### Post by Ivo Moelans on 2007-10-25
Sorry, but I wouldn't know all these exact locations... But there are backup programs that let you select directories (just google them or search in System - Administration - Synaptic Package Manager). And yes, with rsync you could make a simple script to back up all those directories, make that script executable (how to's are easy to find) and even put that script under a hotkey. 
Then again, are you sure it is worth the trouble? I have made clean installs from Ubuntu 5.10 to 7.10 and I found it generally speaking less work just to tweak it afterwards (and put the home directory back, of course). I have a file (on an external disk) where I wrote down e.g. the resolution and refresh rate of my monitor and some other details. I also keep on an external disk icon, mouse pointer, metacity and beryl (compiz) themes that I particularly like (although they are also in my home directory in setting directories). Last, there is one program of which I keep the deb file on an external disk because it is more recent than that in the repositories. The only directory I backup regularly (= almost daily) is my home directory.
After a clean install I have about 2 hours work, but then again: I like tinkering and it there are 'only' two new editions of Ubuntu each year.

---

### Post by perixx on 2007-10-26
There will be certain difficulties with the person I set this PC up for, when I enforce 'tweaking' around when doing a system recovery :]

Besides, there's nothing against a simple way of getting the OS back to it's specified settings with a few clicks, don't you agree?

Really, I couldn't ask this person to manually set up all the different symlinks, graphical- and system settings - that would be simply beyond her.

I still hope to gather some information on how and where all the settings are stored, e.g. in case I encounter problems with the Desktop or applications, apart from that - I hate it to know that there might be a simple manual edit of a certain file in order to fix something, but not knowing where exactly. Since I'm on my way to changing from Windows to Linux for my main system, I'm yearning to find out any useful information I can to cope with mosrt problems myself in the long run ;)


perixx

---

### Post by perixx on 2007-10-26
> I thought so and have already made a copy of the whole /home/USER directory recursively. 

Btw.: would such an action with the 'cp' command keep the folders' and files' original permissions and ownership?


perixx

---

### Post by perixx on 2007-10-26
I'm trying to figure out what the best backup tool might be for me:

HomeUserBackup
sbackup
Grsync

I would think 'HomeUserBackup' seems pretty neat... anybody has experience with it? Does it work under Xubuntu 7.04?


perixx

---

### Post by perixx on 2008-01-09
For the time being, I've found satisfying solutions:
[http://ubuntuforums.org/showthread.php?p=4102800#post4102800]("http://ubuntuforums.org/showthread.php?p=4102800#post4102800")

perixx

---

