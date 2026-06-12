---
title: "[SOLVED] Can I have a single /home partition for multiple distros?"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by charlemagne86 on 2008-05-30
Hello friends...

I have a question as many would already know from the thread title....[B][SIZE="4"]

"Can I have a single /home partition which I can share among various linux distributions? If so how to go about doing it?"[/SIZE][/B]

I want to keep all my documents and medi afiles in a singl ehome partition and use it on all the distros i use..

...I would prefer using 64-bit solutions if any,....

thanks in advance.

---

### Post by abhiroopb on 2008-05-30
Yes this is possible, in FACT this is one of the main reasons for having a separate /home partition.

If you are running Ubuntu then this guide tells you how to put it on a separate partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Patb on 2008-05-31
Charlemagne86, if you intend to have just one distribution installed at any one time, then yes, you could have just one /home partition, preferably in a separate partition.  But if you intend to multi boot, it is probably better to have different /home partitions, one for each linux system.  I went into this a bit myself: [http://ubuntuforums.org/showthread.php?p=4732873](http://ubuntuforums.org/showthread.php?p=4732873)

You can always have your documents stored in a dedicated directory somewhere and use the bind facility in your /etc/fstab file to get automatic access to them.  That way they can be stored in a separate partition which will not be affected by a new installation.  To use my own example, I have documents in a directory called /Docs/ on partition /dev/sdb1 and I have a whole lot of data in the top level directory on a partition /dev/sdb3.  For each of the three linux installations on my system, I have a different /home partition.  But I want to get access to my documents and data via my home partition, no matter which distribution I boot.  To do this, immediately after installing each distribution, I did three steps:

1. Create a directory "/home/pat/Docs/" where I wanted to mount my documents
2. Create a directory "/home/data/" where I wanted to mount my data
3. Edit my /etc/fstab file to include lines to mount those partitions and "bind" the directories at the respective mount points

Here are the relevant lines fom my /etc/fstab file relating to step 3:
```
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
/dev/sdb3 /media/sdb3     ext3    defaults        0       2
/media/sdb1/Docs        /home/pat/Docs  none  bind
/media/sdb3/            /home/data      none  bind
```
To clarify, the first two lines make sure the relevant partitions are mounted and lines 3 and 4 bind the correct directories to /home/pat/Docs and /home/data where I can easily find them.  I'm not sure whether it would be any use for you to do something similar.  

To edit your fstab:
```
sudo gedit /etc/fstab
```
But a word of caution: Don't tinker with anything else in fstab unless you know what you are doing.  

Hope this helps. Cheers, Pat.

---

### Post by charlemagne86 on 2008-05-31
thanks people...will try to do that...


what my dilemma was that if i make seperate /home for each linux install, i hav to keep multiple copies of all my mp3s n all...


Patb' spost cleared a lot of doubts...thnx

btw, can I do this...do a clean insatll of ubuntu on my hdd n keep all my files in its /home partition(a seperate one)  and then nstall debian...and binding in fstab, auto mount my ubuntu home at some place in debian..?

---

### Post by Patb on 2008-05-31
> **charlemagne86 said:**
> can I do this...do a clean install of ubuntu on my hdd n keep all my files in its /home partition (a separate one)  and then install debian... and binding in fstab, auto mount my ubuntu home at some place in debian..?
Charlemagne, I would not bind your entire ubuntu /home directory at some place in debian.  That would unnecessarily duplicate lots of files and directories, particularly hidden directories like /home/.gnome/ and so on.  

Instead, I would bind just the directory which houses the files you want to access at the mount point you create.  For example, you might have all your mp3s in /SomeDirectory/mp3s/.  You would perhaps bind that directory at /debian/home/charlemagne/music/.  In your ubuntu install, you would also bind the same directory at /ubuntu/home/charlemagne/music/.  

That way, whether you boot into Ubuntu or Debian, you will find your mp3s in the directory "music" in your /home folder.  

Hope this helps.  

Cheers, Pat.

---

### Post by Rallg on 2008-05-31
My system has three Ubuntus: two i386, and an amd64. One of the i386 and the amd64 have a common /home partition, BUT my login names are different, so they do not share settings (settings are kept in subfolders for each user name). I did this so I could more easily get to documents (images, word processing) from either installation, without needing to mount a volume.

The other Ubuntu i386 is a special account for guest usage. It keeps its own home folder, so that a guest user (who is not privileged to mount volumes) cannot get to anything I have in my own /home partition for the other installations.

That's not for everyone. I mention it to give you some ideas as to what is possible. In any case, I would probably NOT use the same login name for different installations in a common /home partition, because settings could be merged (not always a good idea).

---

### Post by charlemagne86 on 2008-05-31
gee thanks Patb and Rallag!...

solved my initial querries you did!

Now be kind enough to answer.." Can I have a single swap space for multiple distros?" ...coz i think swap space is just wastage unless dire conditions arise....also havent found swap file space to be ever used in all my linux experience.!

thnx

---

### Post by Rallg on 2008-05-31
Single swap space does the job. Indeed, I believe that if there is already linux-swap on your drive when Ubuntu is installed, it detects it and offers to use it as swap.

If you have the capability to run multiple Linux systems simultaneously (other than as chroot), then have separate swap files. (Does anyone have this capability?)

One general caution: Whenever you re-size (and probably when you re-format) a partition, its UUID is changed. When you run several installers, then depending on what you do, a partition's UUID may be changed in the process. This has the potential to confuse Grub (again, depending on what you do). But it is not difficult to fix.

If, after you have your several installations, Grub is unable to find somkething, it may be because it is looking for the wrong UUID on its menu.lst file. To fix that, get into any Linux (if necessary, live CD) and from Terminal:

ls -l /dev/disk/by-uuid

to discover which partitions have which UUID. Remember that on a single hard drive, (hd0,0) will be sda1, (hd0,1) will be sda2, and so forth.

Then, check against your Grub /boot/grub/menu.lst file. Be sure that you are reading it from the hard drive, rather than a live CD's internal file.

Finally, it is worth checking that each Linux system correctly loads swap. Boot to a system, then use the Administration, System Monitor to see what it says for how much swap you have. If it doesn't show any swap existing (used or not), it means that you might have to fix the swap partition's UUID (or even its partition number) in /etc/fstab.

You might not run across any problems, though.

---

### Post by hal8000 on 2008-05-31
The problem with different distributions is that they dont always use the same groups and permissions.  In order to share /home you would need the same user name on each distribution.
The question the becomes does my group remain the same or change?
The answer depends on the distribution

Use ls -l in ubuntu reveals:

anc@orac:~$ ls -l
total 172
drwxr-xr-x  2 andy andy   4096 2008-05-29 08:19 Desktop
drwxr-xr-x  2 andy andy   4096 2008-05-23 20:00 Documents
lrwxrwxrwx  1 anc andy     35 2008-05-26 12:50 googleearth -> /home/andy/google-ea


Do the same test in Suse and you will find the group changes to users, as in does in other distributions.

To get aound this you'd need a bash script that can change the group name of every file and folder, then change it back when you boot Ubuntu.

The answer is yes you can have a single /home but it can be messy and complicated. For me, I use separate / and /home for each distribution and a common /share partition to swap files- also a little messy perhaps, but its simpler that using a script and works well.

If youre running 2 versions of Ubuntu, then no such problem but any other distro then I'd use a separate /home.

Above all else, back up your personal data and files first.
Hope that helps.

---

### Post by Rallg on 2008-05-31
Hal8000 is right. One possible problem with using a common home (and different user names per distro) has to do with permissions. If you only occasionally wish to transfer a file across users, you can also use Terminal switch to root and change the permissions for a specific file. In my own case, it's not a hassle, since I rarely move a user file or open it from another user. But if you have a lot of stuff, it could be a nuiance.

My settings for some applications (such as Firefox) are different in the different systems, so having distinct user names helps me keep them apart.

---

### Post by tcommbee on 2008-06-07
@hal8000: You can simply create users with same user id and group id on both systems, no problem. Sharing /home between several ubuntu-installs should work well.
@all: However, I would like not only to share music and stuff (which I could also access with nautilus-mount), but primarily gnome ui settings, bookmarks, saved passwords etc.
Are gnome-config files forward and backward compatible? I'm planning to install Fedora and/or Foresight Linux parallel to Ubuntu and they likely have different versions of gnome.

---

### Post by gug@fnal.gov on 2008-06-07
Hi,
   One more voice of caution about completely sharing your home directory between multiple distributions. Several years ago at work I split my time between two offices at work, in the morning in one building and in the afternoon a different one (I was on multiple projects). We have afs at work and it was common to have a home directory in afs space so logging in to multiple nodes always presented the same home area. Basically this worked fine when using ssh to reach remote nodes and I was only sitting in front of one system. However my experience when I started splitting my time was mixed and in part because the two desktop systems had different versions of the operating system. Biggest problem turned out to be quirks with the Gnome window manager and it's hidden directories. First time I logged into the second desktop with a newer version of the OS, several files in those hidden Gnome directories got corrupted (I never did figure out exactly which ones). Lost a lot of my customizations in the process as I did not anticipate this. Only solution that worked in the end was to rename every hidden directory that started with .g* and log in fresh to the new system. That seemed to work but meant I had to re-customize my environment again. I never did figure out if this was an afs issue of truly a window manager issue. Also, I did not have root privileges on the second machine and so was stuck with differing versions of Firefox and Thunderbird, and needless to say plugins and extensions don't work so well when paths to them and their versions differ. Sharing common data like mp3's could migrate to a share area and out of home. Then the only issue is email...

---

### Post by charlemagne86 on 2008-09-22
Okay,...I think we all have a better idea about what we need to know about /home partitions...


so declaring this thread as solved...

thanks to everyone.!!

---

### Post by pbiglr on 2008-09-23
I had similar problem when sharing my home between Ubuntu and Suse. My home directory is on a server and solved the problem by creating separate directories for each distribution. So I have:
   /home/peter/Suse
   /home/peter/Ubuntu

The UID's for the different distros are chosen identical.
In Ubuntu my home directory is set to /home/peter/Ubuntu and in Suse my home directory is set to /home/peter/Suse

All the files that I want to be shared between distros are put in the directory "/home/peter/My". In this directory I have:
   /home/peter/My/Documents
   /home/peter/My/Music
   /home/peter/My/Pictures
   .....

With one symbolic link in the home directory of each distro I have all my data available in whichever distro I choose to boot from.
   cd /home/peter/Ubuntu
   ln -s ../My My
   cd /home/peter/Suse
   ln -s ../My My

---

