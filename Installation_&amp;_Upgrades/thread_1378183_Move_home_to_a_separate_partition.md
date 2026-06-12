---
title: "Move /home to a separate partition?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Puzzled Guy on 2010-01-11
I want to move my home directory to a separate partition so I can install the new versions of Ubuntu without losing my data.

Does anyone know how this can be done?

And while I'm at it, what other important directories should I move to separate partitions? And how do I do it?

I'm guessing that the /boot directory should also be moved to its own partition too, yes? Because it has the GRUB in it, and if I removed Ubuntu to make way for a newer version of Ubuntu, I'll just get an error because the computer can't find the GRUB that doesn't exist anymore, right?

And also, if I move those important yet-to-be-listed directories to their own separate partitions, how large should those partitions be?

If that is not enough information for you to work with, just ask and I'll post it here

I don't want to miss out on the upcoming Lucid Lynx (If it will work in the first place, of course :P)

By the way, I have an Ubuntu-Windows XP dual-boot system.

I'll attach a screenshot of my partition table from GPartEd. You can see that I have about 300 GB. The largest partition is Ubuntu.
[ATTACH]143275[/ATTACH]

Thanks

---

### Post by Cheesemill on 2010-01-11
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by J V on 2010-01-11
> **Puzzled Guy said:**
> And while I'm at it, what other important directories should I move to separate partitions? And how do I do it?None are neccesary, /home is the big cheese

> I'm guessing that the /boot directory should also be moved to its own partition too, yes? Because it has the GRUB in it, and if I removed Ubuntu to make way for a newer version of Ubuntu, I'll just get an error because the computer can't find the GRUB that doesn't exist anymore, right?Nope, ubuntu will just put a new one in...

> And also, if I move those important yet-to-be-listed directories to their own separate partitions, how large should those partitions be?/ should be 20 gigs if you're planning for a big party... /home should be rest

Seeing as you are preparing for lucid (as am I) have a look at my little script, installs all my favorite programs, sets up shortcuts, gedit, etc :)

Note: This script assumes they will have 64bit flash in the repositories by then ;)

Edit before use for your own liking :)

---

### Post by Puzzled Guy on 2010-01-11
> **J V said:**
> None are neccesary, /home is the big cheese

Nope, ubuntu will just put a new one in...

/ should be 20 gigs if you're planning for a big party... /home should be rest

Seeing as you are preparing for lucid (as am I) have a look at my little script, installs all my favorite programs, sets up shortcuts, gedit, etc :)

Note: This script assumes they will have 64bit flash in the repositories by then ;)

Edit before use for your own liking :)

By "/" I will assume that you mean all the directories except /home. But are you really sure that / will only need about 20 GB? The partition table says that 14 GB is used...no wait, the home folder is 11 GB, meaning that the rest is only about 3 GB!

Thanks!

Now for the rest of the problem...

I'll post again tomorrow if I still need help! :P

---

### Post by Puzzled Guy on 2010-01-12
Thanks Cheesemill and J V!

The psychocats article did the trick.

Now before I say that my problem is solved, let me just ask one more thing:

Take a look at my screenshot from GPartEd. The red-boxed partition (/dev/sda5) is my "/" directory, and the blue-boxed one (/dev/sda7) is my new /home partition.

For /dev/sda5, the number under "Used" is the same as it was before I created the new home partition. Since the psychocats tutorial gives commands to backup the home directory, the number under "Used" is the same because there is an exact duplicate of /home in it, right?

But under "Properties", it says that the home folder/directory/partition/whatever is 11.1 GiB, while in the GPartEd screenshot it says it's only 8.93 GiB. Any explanation for that?
[ATTACH]143373[/ATTACH]

---

### Post by SecretCode on 2010-01-12
Do you mean right-click properties in nautilus? Hmm ... maybe there is another mount point inside it.

What do you get from
```
df -h
sudo du -hx --max-depth 1 /
du -hx --max-depth 2 /home
```

---

### Post by Puzzled Guy on 2010-01-12
Here is the output from the commands you requested:

**df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G   12G  7.3G  62% /
tmpfs                1002M     0 1002M   0% /lib/init/rw
varrun               1002M  216K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
udev                 1002M  164K 1002M   1% /dev
tmpfs                1002M   88K 1002M   1% /dev/shm
lrm                  1002M  2.2M 1000M   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda7             130G  7.0G  116G   6% /home

**sudo du -hx --max-depth 1 /**
4.0K    /selinux
8.0K    /media
1.4M    /root
6.2M    /bin
0    /dev
84K    /tmp
16K    /lost+found
0    /sys
200K    /srv
211M    /lib
6.8G    /home_backup
16M    /etc
1.7G    /var
2.8G    /usr
8.3M    /sbin
127M    /opt
0    /proc
26M    /boot
4.0K    /mnt
4.0K    /home
12G    /

**sudo du -hx --max-depth 2 /home**
8.0K    /home/hope/.qt
26M    /home/hope/.wine
8.0K    /home/hope/.SimDock
184K    /home/hope/.nautilus
3.6M    /home/hope/.opera
12K    /home/hope/.update-manager-core
8.0K    /home/hope/.avast
36K    /home/hope/.gnupg
4.0K    /home/hope/.aptitude
344K    /home/hope/.openme
1.4M    /home/hope/.macromedia
12K    /home/hope/.pitivi
77M    /home/hope/.cpan
240K    /home/hope/.purple
4.6G    /home/hope/Videos
40K    /home/hope/.pki
364K    /home/hope/.evolution
572K    /home/hope/.gstreamer-0.10
57M    /home/hope/.mozilla
9.4M    /home/hope/.fonts
308K    /home/hope/.java
2.1M    /home/hope/.gconf
8.7M    /home/hope/pitivi
16K    /home/hope/.audacity-data
342M    /home/hope/Pictures
84K    /home/hope/.compiz
12K    /home/hope/.emerald
40K    /home/hope/.subversion
64K    /home/hope/.blender
720K    /home/hope/.adobe
856K    /home/hope/.cache
16K    /home/hope/.gegl-0.0
112K    /home/hope/.pulse
4.0K    /home/hope/.scim
100K    /home/hope/Documents
4.0K    /home/hope/.FBReader
12K    /home/hope/.dbus
700K    /home/hope/.wesnoth1.6
24K    /home/hope/.etracer
150M    /home/hope/.xmoto
8.0K    /home/hope/.update-notifier
32K    /home/hope/.vdrift
16K    /home/hope/.sudoku
8.0K    /home/hope/.audacity1.3-hope
4.0K    /home/hope/.ssh
16K    /home/hope/.alex4
2.9M    /home/hope/.thumbnails
4.0K    /home/hope/.gvfs
464K    /home/hope/.gimp-2.6
80K    /home/hope/.gconfd
24K    /home/hope/.AbiSuite
62M    /home/hope/.icons
12K    /home/hope/.PlaneShift
12K    /home/hope/.gnome
1008K    /home/hope/.gnome2
28K    /home/hope/.xine
5.4M    /home/hope/.mozilla-thunderbird
8.0K    /home/hope/.screenlets
324K    /home/hope/.fontconfig
428K    /home/hope/.checkbox
8.0K    /home/hope/.xmms
4.0K    /home/hope/.gnome2_private
4.0K    /home/hope/.crystalspace
124K    /home/hope/.tomboy
16K    /home/hope/.frozen-bubble
48K    /home/hope/.inkscape
4.0K    /home/hope/.opencity
12K    /home/hope/.numptyphysics
8.0K    /home/hope/.ggz
35M    /home/hope/Music
4.0K    /home/hope/.debtags
8.0K    /home/hope/.cellwriter
4.0K    /home/hope/Downloads
4.0K    /home/hope/.wapi
2.1M    /home/hope/.openoffice.org
4.0K    /home/hope/.google
8.0K    /home/hope/.bmp
12K    /home/hope/.avidemux
8.0K    /home/hope/.themes
4.0K    /home/hope/.synaptic
100K    /home/hope/.ubuntu-tweak
1.4G    /home/hope/Desktop
7.2M    /home/hope/.config
4.0K    /home/hope/.scummvm
8.0K    /home/hope/.Ferrari3D
131M    /home/hope/.local
16K    /home/hope/.mplayer
6.9G    /home/hope
16K    /home/lost+found
6.9G    /home

One question: The /home folder is accessing files from the home partition now, right?

Another question: If I want to do a clean install of Ubuntu (probably to get Lucid), how will set the home partition as /home again?

Thanks, I appreciate all your help guys! ;)

---

### Post by SecretCode on 2010-01-12
Well that didn't explain anything! df and du show only 7.0GB/6.9GB in /home. It's possible gparted is also including the journal space or something like that. Perhaps check properties again.

Other than this odd inconsistency, everything looks fine - your /home is definitely on (accessing) the separate partition sda7.

If you need to reinstall, install as normal except for the partitioning - choose manual partitioning and select sda5 to mount as / (in a new install you'll probably want to reformat this partition) and sda7 to mount as /home (do **not** format it!)

---

### Post by Puzzled Guy on 2010-01-12
Thanks! Problem solved.

Now I have a separate home partition and I know how to set is as /home when I reinstall!

Thanks again :D

---

