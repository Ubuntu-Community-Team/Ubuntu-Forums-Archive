---
title: "Struggling to free disk space for Feisty upgrade"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2007-05-22
I'm upgrading from Edgy to Feisty on a small (4GB) HD.  The system requirement for Ubuntu is 2GB, but the install/upgrade process presumably requires a lot of files to be cached temporarily.

The upgrade is failing because I need to fee another 20.4MB.  I have very little stored on my HD - just the Edgy installation, plus a few small additions eg proprietary codecs and one or two other packages not in the default Ubuntu installation.  I've cleared off just about everything I can think of.  I've also run **sudo apt-get clean** and emptied my wastebasket.

[LIST=1]
[*]Where I should look for temporary internet files?
[*]In /var/cache/archives I have files **pkgcache.bin** @ 10MB and **srcpkgcahe.bin** @ 9.9 MB.  The upgrade manager advises clearing out the archive.  Is it safe to remove these files?
[*]Any other ideas for files I can safely remove, packages to uninstall, etc?
[/LIST]

Thanks

---

### Post by taurus on 2007-05-22
Also look in /var/log and remove all the backup log files.  See if you have anything large in /tmp.  Any chance /var/backup takes up space too?

```
sudo du -h /var
```

---

### Post by Karl S. on 2007-05-22
Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=414639&page=2") can help you.

---

### Post by dannyboy79 on 2007-05-22
have you tried to use the clean and autoclean options for aptitude or apt-get? that should clear out a significant amount of space. Are you sure you've emptied your trash bins for both root and all your usernames? have you removed any .deb's that you've downloaded over time as you can always download them again if need be?

---

### Post by Edward The Bonobo on 2007-05-22
Good suggestions.  Thanks.

How do I empty the wastebasket for root?

---

### Post by Waappu on 2007-05-22
> **Edward The Bonobo said:**
> Good suggestions.  Thanks.

How do I empty the wastebasket for root?

Hi

Type in terminal ```
sudo rm /root/.Trash/*
sudo rm -R /root/.Trash/*
```

---

### Post by Edward The Bonobo on 2007-05-22
/var/log haS 9.7MB - but very little of this is labelled as backup files (eg lots of gzip archives).  Can all of this stuff go?

/var/backups has 6.7MB on it.  Can I delete everything?

/var has 276MB total

---

### Post by Edward The Bonobo on 2007-05-22
I can't view (or do anything else to) /root/.Trash as sudo.

---

### Post by Waappu on 2007-05-22
> **Edward The Bonobo said:**
> I can't view (or do anything else to) /root/.Trash as sudo.
Hi

Type in terminal ```
sudo dir -a /root/.Trash
```to see if there is any files in root deleted items folder

---

### Post by Edward The Bonobo on 2007-05-22
It seems not.  I'm at 1.2GB free now, so wish me luck as I try the upgrade again...

---

### Post by Edward The Bonobo on 2007-05-22
Eek!  It gets worse!

Earlier I had 980MB fee, and it was asking me for an extra 20.4MB.  Now I have 1.2GB free...but it's asking for 300+MB.  Does Upgrade Manager include a random number generator?

Back to the /var/log files I mentioned earlier. Can I delete?

---

### Post by Waappu on 2007-05-22
> **Edward The Bonobo said:**
> Eek!  It gets worse!

Earlier I had 980MB fee, and it was asking me for an extra 20.4MB.  Now I have 1.2GB free...but it's asking for 300+MB.  Does Upgrade Manager include a random number generator?

Back to the /var/log files I mentioned earlier. Can I delete?
Hi

Read this if it helps you
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Edward The Bonobo on 2007-05-22
I tried all the steps from that link (and, jeez, I wish Synaptic allowed multiple-select!).  It didn't free up any more space.

---

### Post by Edward The Bonobo on 2007-05-22
CORRECTION: I tried the deborphan trick (from the link).  When it ran, it gave me a list of packages to remove using **apt-get remove**, but then stopped without taking me back to the prompt.  I came out of Terminal and went back in again.  I'd freed up about 100MB.  But apt-get remove doesn't free up any extra.

---

### Post by taurus on 2007-05-22
Do you have a separate /home or you only have one partition, /?  Post the output of these commands.

```
df -h
du -h /home
```

---

### Post by Edward The Bonobo on 2007-05-22
df -h
> 
**:~$ df -h**
Filesystem            Size Used Avail Use% Mounted on
/dev/hdd1             5.9G  4.2G  1.4G  76% /
varrun                155M   80K  155M   1% /var/run
varlock               155M  4.0K  155M   1% /var/lock
procbususb             10M   96K   10M   1% /proc/bus/usb
udev                   10M   96K   10M   1% /dev
devshm                155M     0  155M   0% /dev/shm
lrm                   155M   18M  138M  12% /lib/modules/2.6.17-11-386/volatile
/dev/hda1              19G   19G  409M  98% /media/windows
/dev/hdc              690M  690M     0 100% /media/cdrom0


df -h /home
> 
**:~$ df -h /home**
Filesystem            Size Used Avail Use% Mounted on
/dev/hdd1             5.9G  4.2G  1.4G  76% /


---

### Post by Edward The Bonobo on 2007-05-22
btw - Upgrade Manager's asking for about another 100MB now.

---

### Post by taurus on 2007-05-22
It's

```
du -h /home
```
Maybe you need to delete some files in your $HOME directory to free up some space.

---

### Post by Edward The Bonobo on 2007-05-22
Yes, 207MB of hidden files in /home, but nothing really leaps out and shouts 'delete me':

> 
:~$** du -h --max-depth=2 /home/**
1.6M    /home/my_user_name/.gconf
88K     /home/my_user_name/.gconfd
2.4M    /home/my_user_name/.gnome2
8.0K    /home/my_user_name/.gnome2_private
8.0K    /home/my_user_name/.gstreamer-0.8
276K    /home/my_user_name/.nautilus
8.0K    /home/my_user_name/.qt
8.0K    /home/my_user_name/.update-notifier
824K    /home/my_user_name/.metacity
60K     /home/my_user_name/Desktop
104K    /home/my_user_name/.Trash
132M    /home/my_user_name/.thumbnails
20M     /home/my_user_name/.mozilla
36K     /home/my_user_name/.gnome
4.0K    /home/my_user_name/.themes
4.0K    /home/my_user_name/.icons
2.0M    /home/my_user_name/.openoffice
4.5M    /home/my_user_name/.gtkpod
17M     /home/my_user_name/.evolution
4.0K    /home/my_user_name/.gpilotd
2.4M    /home/my_user_name/.openoffice.org2
456K    /home/my_user_name/.cache
96K     /home/my_user_name/.local
172K    /home/my_user_name/.config
88K     /home/my_user_name/.gnupg
1.4M    /home/my_user_name/.aMule
44K     /home/my_user_name/.xine
1.4M    /home/my_user_name/.macromedia
520K    /home/my_user_name/.streamtuner
12K     /home/my_user_name/.synaptic
8.0K    /home/my_user_name/.sane
16K     /home/my_user_name/.mcop
488K    /home/my_user_name/.gstreamer-0.10
4.0K    /home/my_user_name/.bogofilter
36K     /home/my_user_name/.bmp
156K    /home/my_user_name/.kde
4.0K    /home/my_user_name/my_user_name
28K     /home/my_user_name/.gqview
11M     /home/my_user_name/.limewire
364K    /home/my_user_name/.vlc
84K     /home/my_user_name/.wapi
4.0K    /home/my_user_name/.cddbslave
8.0K    /home/my_user_name/.AbiSuite
3.0M    /home/my_user_name/.java
8.0K    /home/my_user_name/.serpentine
484K    /home/my_user_name/.loki
712K    /home/my_user_name/.gimp-2.2
4.3M    /home/my_user_name/.googleearth
56K     /home/my_user_name/.checkgmail
20K     /home/my_user_name/.mplayer
76K     /home/my_user_name/.adobe
168K    /home/my_user_name/.BitTornado
4.0K    /home/my_user_name/.gnome_private
12K     /home/my_user_name/.gnucash
4.0K    /home/my_user_name/Incomplete
4.0K    /home/my_user_name/Shared
4.0K    /home/my_user_name/Azureus Downloads
44K     /home/my_user_name/.gdesklets
8.0K    /home/my_user_name/.update-manager
28K     /home/my_user_name/.xmms
8.0K    /home/my_user_name/media
20K     /home/my_user_name/.easytag
8.0K    /home/my_user_name/.camel_certs
207M    /home/my_user_name
207M    /home/


---

### Post by Edward The Bonobo on 2007-05-22
Hold on just a doggone miniute...132MB of thumbnails?!  wtf?  Looks like every image file I've ever viewed.

---

