---
title: "Ubuntu on Master, XP on slave"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by louca on 2006-04-22
hey
I am a newbie and I have alittle problem here that I would like some help with.

I did a clean install of ubuntu 5.10 on one hard drive after first **unplugging** the original drive which had windows xp on it. well i have put that drive back in as a slave and I dont know how to boot windows from it using GRUB.

what am i to do? :(

---

### Post by jak on 2006-04-22
*Updated*
Okay, try this:

In the terminal,
Change the directory to grubs
# cd /boot/grub
Make a backup of the menu.lst file
# cp menu.lst menu.lst~
Open the menu.lst file
# gksudo 'gedit menu.lst'

Now, if you add this to the end...

```

# This will boot XP on the Slave hard drives primary partition
title           Windows XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

I hope that works for you, it does for me.

---

### Post by Mustard on 2006-04-22
Actually the above guide is great, but is missing one important part.  Windows needs to be tricked into thinking its on the master drive (assuming the above user is going to put XP back as the slave drive), so your entry in grub would look like this...

```
title           Windows XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

The two 'map' entries make Windows think its the on the Master.

Also if you use gksudo with gedit you will have to change the way you normally edit files or it will open up a blank file.  Do this instead...

```
gksudo 'gedit menu.lst'
```

If you don't include the single quotes when using gksudo, then gedit will open a file called *menu.lst'*, note the extra single quote that will get appended to the filename you open. This will be a blank file, and the new user will be somewhat confused as to what is going on. :)

---

### Post by confused57 on 2006-04-22
That's how I have my system setup, Ubuntu drive master, XP slave, I used this thread:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

Mustard is right, you have to have the mapping to fool XP.  By the way, lha(lower case "L") is the dual boot dual hd expert I've found out.

---

### Post by louca on 2006-04-22
Thanks alot :D

I am going to reboot and see if it works now.

---

### Post by confused57 on 2006-04-22
Good luck, here's another thread that might help:

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

---

### Post by louca on 2006-04-23
*edit*
i got the file editted

---

### Post by louca on 2006-04-23
it works! :D  *dances around*

now.. how do i get to read the files which are on the xp hard drive from ubuntu?
(and dare i say.. vici versa)

---

### Post by confused57 on 2006-04-23
As far as reading Windows files from Ubuntu, it is a matter of "mounting" the windows drive, see this link & click on windows:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)

I'm just a noob also, but wanted to get you started until someone who really knows sees this thread.

---

### Post by louca on 2006-04-23
ok i got it done.

note: you can only have READ access to ntfs partitions.

for ntfs, there are two ways to do this, you can go into the terminal and type:

```
 sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000 
```

replacing /dev/hda1 in the second line with whatever your windows partition/harddrive is called. you can check the name if you are not sure in System -> Administration -> Disks and click on the drive in there.

Once you have done that you can access ur windows harddrive in /media/windows


OR


You can just enter the first line from before:

```
sudo mkdir /media/windows

```

and then go to System -> Administration -> Disks
click on the windows disk
type in /media/windows as the path
and click enable.

do you guys think it is a good idea to give the user access or leave access as root?

---

### Post by louca on 2006-04-23
Ok, two questions now, (you guys have been great by the way), how do I give user access to the windows hd?

Also, even though it is on an NTFS file system, is it possible to copy files on the windows drive onto my ubuntu drive? How is this possible?

---

### Post by Mustard on 2006-04-26
I've been mucking around installing Dapper (and overcoming some hardware issues), so I haven't been following your progress.  I'm stuck on Dapper atm with no access to my usual list of help guides.  What you talk about above is all possible.  If you do a quick search using the forum search function, you'll find quite a lot of threads on the subject of mounting ntfs and fat drives from ubuntu.

---

