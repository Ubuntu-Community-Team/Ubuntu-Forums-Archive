---
title: "Need help exporting LATEST updates (deltas) to file"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by gunghogarrett on 2010-09-20
Hello all.  I have Alienvault (which is debian based) running on an offline network.  I need to have a repo server on that network in order to provide updates/other installation sources.  Currently I have configured Ubuntu Server 10.04 as an apt-mirror on an internet-connected network.  

What I need to do is find a way to automatically take the newest  updates, and export them to disk.  I need to mirror the internet-connected-repo server on the offline-network side.  But I don't want to burn all 40 gigs or so every time new updates come out.   Basically, I'd like to perform incremental backups of the mirror after the first full backup.  Is it possible to automate this daily?  

If you want to recreate: my /etc/apt/mirror.list has the following sources:

deb [http://data.alienvault.com/debian](http://data.alienvault.com/debian) binary/
deb [http://www.ossim.net/download/](http://www.ossim.net/download/) debian64/
deb [http://data.alienvault.com/debian_shared/](http://data.alienvault.com/debian_shared/) binary/
deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main contrib
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main contrib
deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib
deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) lenny/volatile main
deb-src [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) lenny/volatile main


Thanks!

---

### Post by andydread on 2010-09-20
If i understand you correctly. 

1) insert a linux filesystem formatted usb hard drive in apt-mirror box and mount.  Lets just say device is mounted on /var/backup and your mirror directory is /opt/mirror/lucid.

2) root@onlineserver:~# rsync -au --delete /opt/mirror/lucid /var/backup
(note no trailing slashes in the above command.)

3) unmount usb hard disk.

4) plug usb disk into offline mirror box and mount. 
root@offlineserver:~# rsync -au --delete /var/backup /opt/mirror/lucid

done!

each time you do the above steps only the delta will be synced to the disk and then to the other server.  
hope this helps

Andy.

When you want to copy the the delta just repeat the above steps.
IF you want to automate then you may need to throw together a little script that will run the commands to mount the disk, rsync the files then unmount it.

---

### Post by gunghogarrett on 2010-09-21
Excellent, this is a step in the right direction.  However, it is a company policy to use closed session cds/dvds to transfer to the offline network.  

Is anyone familiar enough with rsync to perhaps:

1. sync the mirror with a "repo share" for example, and
2. output the deltas, or at least hardlinks to the deltas, to a new folder for easy distinguishability.  

Or perhaps there is another way around this.  

In the end, What I'd like to do with the online mirror is to have a web link that will allow me to download an iso with all the newest deltas since the last rsync.  Then I could just burn the iso, pop it in the offline mirror and sync up the deltas.

Thanks!

---

### Post by gunghogarrett on 2010-09-21
Ok, here's an update of what I've been trying:

I've used rsync to sync the /var/spool/apt-mirror directory to /sdb1/repo.  
I've also experimented with rdiff-backup to do the same thing to /sdc1/repo

Syncing the folders is easy and works every time.  

When syncing though, can the changes from each sync (the deltas) be copied to another folder.  

e.g.: if newfile.deb is added to /var/spool/apt-mirror, can rsync or rdiff put newfile.deb in both /repo and in /repo/<todaysdate>/   ?

Thanks.

---

### Post by gunghogarrett on 2010-09-28
The problem is solved.  The below script I wrote works.  The only requirement is that a "yesterday's date" folder must be created along with the full and iso.  For my purposes I will be simplifying this script to allow for different locations to be added.  

```
#!/bin/bash

find /var/spool/apt-mirror -iname "*.deb" -exec cp -al {} /root/repo/debsonly/full \;

ls /root/repo/debsonly/full/ > /root/repo/debsonly/full/fulllist.txt

cp -al /root/repo/debsonly/`date +%Y%m%d -d "-1 day"` /root/repo/debsonly/`date +%Y%m%d`

ls /root/repo/debsonly/`date +%Y%m%d`/ > /root/repo/debsonly/`date +%Y%m%d`/changelog.txt

rsync -anv /root/repo/debsonly/full /root/repo/debsonly/`date +%Y%m%d` | cut -d '/' -f2 > /root/repo/debsonly/changes.txt

rsync -az /root/repo/debsonly/full/ /root/repo/debsonly/`date +%Y%m%d`

diff /root/repo/debsonly/full/fulllist.txt /root/repo/debsonly/`date +%Y%m%d`/changelog.txt | cut -d ' ' -f2 > /root/repo/debsonly/`date +%Y%m%d`/latestdebs.txt

chmod 777 /root/repo/debsonly/`date +%Y%m%d`/latestdebs.txt

rm -rf /root/repo/debsonly/latest
ln -s `date +%Y%m%d` latest

loc="/root/repo/debsonly/`date +%Y%m%d`"
latestdebs="/root/repo/debsonly/`date +%Y%m%d`/latestdebs.txt"

for i in $(cat $latestdebs)
do
if [ -f "/$loc/$i" ]; then
cp -f /$loc/$i /root/repo/debsonly/iso/
else
continue
fi
done


tar -cML 4580000 -f latestrpo`date +%Y%m%d`.tar /root/repo/debsonly/iso

rm -f /root/repo/debsonly/iso/*

```

---

### Post by gunghogarrett on 2010-10-01
I've been playing around with this script and have improved it drastically.  However, if anyone has any input, I'd appreciate it.  So far, it's been quite successful.  This is my first attempt at bash scripting.  I'm having a good time with this.  

Here is what I have so far:

```


#!/bin/bash

mirror="/var/spool/apt-mirror"
repofldr="/root/repo"
fullrepo="/root/repo/full"
todayrepo="/root/repo/`date +%Y%m%d`"
yesterday="/root/repo/`date +%Y%m%d -d "-1 day"`"
day2="/root/repo/`date +%Y%m%d -d "-2 day"`"
day3="/root/repo/`date +%Y%m%d -d "-3 day"`"
day4="/root/repo/`date +%Y%m%d -d "-4 day"`"
day5="/root/repo/`date +%Y%m%d -d "-5 day"`"
day6="/root/repo/`date +%Y%m%d -d "-6 day"`"
day7="/root/repo/`date +%Y%m%d -d "-7 day"`"

if [ ! -d $repofldr/iso ]; then
    mkdir $repofldr/iso
fi
if [ ! -d $yesterday ]; then
    if [ -d $day2 ]; then
        mkdir $yesterday
        cp -al $day2/*.deb $yesterday
    else
        if [ -d $day3 ];then
            mkdir $yesterday
            cp -al $day3/*.deb $yesterday
            continue
            else
            if [ -d $day4 ]; then
                mkdir $yesterday
                cp -al $day4/*.deb $yesterday
            continue
            else
                if [ -d $day5 ]; then
                    mkdir $yesterday
                    cp -al $day5/*.deb $yesterday
                continue
                else
                    if [ -d $day6 ]; then
                        mkdir $yesterday
                        cp -al $day6/*.deb $yesterday
                    continue
                    else
                        if [ -d $day7 ]; then
                            mkdir $yesterday
                            cp -al $day7/*.deb $yesterday
                        continue
                        else
    mkdir $yesterday
    continue
    fi
    fi
    fi
    fi
    fi
    fi
    fi
    
if [ ! -d $repofldr/full ]; then
    mkdir $fullrepo
    continue
fi

find $mirror -iname "*.deb" -exec cp -al {} $fullrepo \;
ls $fullrepo > $fullrepo/fulllist.txt
cp -al $yesterday/ $todayrepo
ls $todayrepo > $todayrepo/changelog.txt
cp -al $fullrepo/*.deb $todayrepo/
diff $fullrepo/fulllist.txt $todayrepo/changelog.txt | cut -d ' ' -f2 > $todayrepo/latestdebs.txt
chmod 777 $todayrepo/latestdebs.txt
rm -rf $repofldr/latest
ln -s $todayrepo latest


mkdir $todayrepo/binary
mkdir $todayrepo/source

##assuming dpkg-dev is installed

dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
dpkg-scansources source /dev/null | gzip-9c > source/Sources.gz
cp $todayrepo/source $repofldr/iso/
cp $todayrepo/binary $repofldr/iso/
cd $repofldr

loc="/root/repo/`date +%Y%m%d`"
latestdebs="/root/repo/`date +%Y%m%d`/latestdebs.txt"

for i in $(cat $latestdebs)
do
if [ -f "/$loc/$i" ]; then
cp -lf /$loc/$i /root/repo/iso/
else
continue
fi
done


tar -cML 4580000 -f latestrepo`date +%Y%m%d`.tar $repofldr/iso/*

rm -f $repofldr/iso/*



```

Thanks!

---

### Post by gunghogarrett on 2010-10-01
I should explain my configuration:

I have configured apt-mirror to download the repositories listed in the first thread here.  

The script I've pasted above finds all the deb files from the mirror, and copies them, as links, to a full repo folder.  You'll notice from the first script I posted that I stopped using rsync.  I did this because I already had the entire mirror downloaded to my server, I just needed to manage the files and output them to someplace useable.  

Next, the script does differential comparisons so any new debs or updated debs will be outputted to the iso folder and made into a tarball.

I tar them so that I can burn them to disk and export them into an offline repository.

---

### Post by gunghogarrett on 2010-10-01
Next thing:

Does anyone know how to make my if statements work better?  I the script to look for a $yesterday folder but if it doesn't exist, then it needs to look for the day before that, and so forth until it finds a folder with the required field.  

Once it finds it, it'll mkdir $yesterday and copy contents of the found folder into yesterday.  It's what the script does, but i only made the statements go back a week before just leaving $yesterday empty (which forces a full dump).  

Thanks, yet again!

---

### Post by gunghogarrett on 2010-10-08
New Update:  

The following script works a lot better, and after playing around with it lots I think it's almost done.  

```
#!/bin/bash
mirror="/var/spool/apt-mirror"
repofldr="/repo"
fullrepo="/repo/full"
daily="/repo/daily"
dirlist="/repo/daily/dirlist"
todayrepo="/repo/daily/`date +%Y%m%d`"
yesterday="/repo/daily/`date +%Y%m%d -d "-1 day"`"

if [ ! -d $repofldr/iso ]; then
        mkdir $repofldr/iso
        else
        continue
fi

if [ ! -d $repofldr/full ]; then
        mkdir $fullrepo
        else
        continue
fi

if [ ! -d $repofldr/daily ]; then
        mkdir $daily
        else
        continue
fi

MAX="9"
MIN="`du /repo/daily/ | awk '{print $1}'`"

if [ "$MIN" -lt $MAX ]; then
        mkdir $yesterday
        else
        continue
fi

ls $daily | egrep -v dirlist  | egrep -v `date +%Y%m%d` | sort -n | tail -1 > $dirlist

for i in $(cat $dirlist)
do
if [ $i -eq `date +%Y%m%d -d "-1 day"` ]; then
         continue
         else
         if [ $i -ne `date +%Y%m%d -d "-1 day"` ]; then
         mkdir $yesterday
         cp -al $i/*.deb $yesterday
         continue
         fi
fi
done

apt-mirror

find $mirror -iname "*.deb" -exec cp -al {} $fullrepo \;
ls $fullrepo > $fullrepo/fulllist.txt
cp -al $yesterday/ $todayrepo
ls $todayrepo > $todayrepo/changelog.txt
cp -al $fullrepo/*.deb $todayrepo/
diff $fullrepo/fulllist.txt $todayrepo/changelog.txt | cut -d ' ' -f2 > $todayrepo/latestdebs.txt
chmod 777 $todayrepo/latestdebs.txt
rm -rf $repofldr/latest
ln -s $todayrepo latest

loc="/repo/daily/`date +%Y%m%d`"
latestdebs="/repo/daily/`date +%Y%m%d`/latestdebs.txt"

for i in $(cat $latestdebs)
do
if [ -f "/$loc/$i" ]; then
cp -lf /$loc/$i /repo/iso/
else
continue
fi
done
                                                                             

MAXSIZE="4294957296"
SIZE="`du -bs /repo/iso/ | awk '{print $1}'`"

if [ "$SIZE" -gt "$MAXSIZE" ]; then
    tar czfP /repo/iso/* | split -d -b 4294957296 - "latestrepo`date +%Y%m%d`.tar.gz."
    continue
    else
    tar czfP "latestrepo`date +%Y%m%d`.tar.gz"  /repo/iso/*
    continue
fi




```

---

