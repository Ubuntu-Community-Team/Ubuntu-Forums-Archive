---
title: "apt get/ synaptic broken"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by electrocutioner on 2006-10-24
I have used automatix a number of times and have always reverted to the original repositories no problem.
I used it to install wine and then ran winecfg,
Now when I try to update anything I get the following errors or when I try it force an install to correct the problem


Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing bash (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

any thoughts?

---

### Post by funkyade on 2006-10-24
1. check that you have space available on your /var partition.
```
#> df -h
```

2. what happens when you run ?
```
#> sudo apt-get autoclean
```

3. if all else fails, delete everything in /var/cache/apt/archives
```
#> sudo rm -fdr /var/cache/apt/archives
```
then add a default sources.list and 
```
#> sudo nano /etc/apt/sources.list
#> sudo apt-get update
```

hth

---

### Post by electrocutioner on 2006-10-24
Thanks for responding,Funkyade.

1 seems ok, I get this

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              19G  4.6G   13G  27% /
varrun                443M   92K  443M   1% /var/run
varlock               443M  4.0K  443M   1% /var/lock
udev                  443M  100K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   19M  424M   5% /lib/modules/2.6.15-25-386/volatile
/dev/hda              354M  354M     0 100% /media/cdrom0


2 gives me that error

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing bash (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I ran the code in 3-the second line lists the sources and the final line gives me

E: Archive directory /var/cache/apt/archives/partial is missing.


 So i am still missing something-
 btw I also installed google picasa with automatix before apt-get broke-but that's it,I swear!](*,)

---

### Post by electrocutioner on 2006-10-25
anybody?

---

