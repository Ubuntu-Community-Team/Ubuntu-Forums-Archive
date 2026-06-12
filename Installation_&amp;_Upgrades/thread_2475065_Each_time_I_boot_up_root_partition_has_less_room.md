---
title: "Each time I boot up root partition has less room"
date: 2022-05-15
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2022-05-15
I am running an ordinary installation of Ubuntu 20.04 installed from the iso image. I partitioned my 1 tb drive with 20 gb for / and most of the rest for /home.
Every time I boot up I get a message that my / directory is running low on space. I started checking and after each boot up my / has shrunk by anywhere from 2 - 20 mb even if I do nothing else but boot into the system. I am now down to only 500 mb of free space. I don't know what is wrong. I regularly check and get rid of old kernels so I don't think that is the problem. here is the output from df -h :
(base) bob@Emma:~$ sudo df -h
[sudo] password for bob: 
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.3M  1.6G   1% /run
/dev/sdd2        19G   17G  551M  97% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/loop1      128K  128K     0 100% /snap/bare/5
/dev/loop3       56M   56M     0 100% /snap/core18/2409
/dev/loop2      112M  112M     0 100% /snap/core/12941
/dev/loop5       62M   62M     0 100% /snap/core20/1434
/dev/loop4      392M  392M     0 100% /snap/gimp/383
/dev/loop6      111M  111M     0 100% /snap/core/12834
/dev/loop7      278M  278M     0 100% /snap/gimp/380
/dev/loop0      9.0M  9.0M     0 100% /snap/canonical-livepatch/132
/dev/loop8      302M  302M     0 100% /snap/qt5-core20/10
/dev/loop9      9.0M  9.0M     0 100% /snap/canonical-livepatch/138
/dev/loop10      44M   44M     0 100% /snap/snapd/15177
/dev/loop11     248M  248M     0 100% /snap/gnome-3-38-2004/87
/dev/loop13      45M   45M     0 100% /snap/snapd/15534
/dev/loop14     133M  133M     0 100% /snap/chromium/1985
/dev/loop12     259M  259M     0 100% /snap/qt551/37
/dev/loop15     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop16      56M   56M     0 100% /snap/core18/2344
/dev/loop17     918M  918M     0 100% /snap/libreoffice/254
/dev/loop18     112M  112M     0 100% /snap/simplescreenrecorder-brlin/69
/dev/loop19     249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/loop20      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop21     302M  302M     0 100% /snap/qt5-core20/8
/dev/loop22     5.7M  5.7M     0 100% /snap/olivia/139
/dev/loop24     133M  133M     0 100% /snap/chromium/1993
/dev/loop23      66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop25     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop26     8.9M  8.9M     0 100% /snap/pdfmixtool/864
/dev/loop27     219M  219M     0 100% /snap/gnome-3-34-1804/77
/dev/loop28      55M   55M     0 100% /snap/snap-store/558
/dev/loop29     8.9M  8.9M     0 100% /snap/pdfmixtool/862
/dev/loop30     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop31      62M   62M     0 100% /snap/core20/1405
/dev/loop32     626M  626M     0 100% /snap/libreoffice/250
/dev/loop33      51M   51M     0 100% /snap/snap-store/547
/dev/loop34     291M  291M     0 100% /snap/kde-frameworks-5-qt-5-14-core18/4
/dev/loop35     5.7M  5.7M     0 100% /snap/olivia/140
/dev/loop36     261M  261M     0 100% /snap/kde-frameworks-5-core18/32
/dev/loop37     259M  259M     0 100% /snap/qt551/39
/dev/sdd1       234M  8.1M  226M   4% /boot/efi
/dev/sdd4       879G   92G  743G  11% /home
/dev/sdb2       458G   73M  435G   1% /mnt/ff49c606-03d8-4ffc-ae6f-abc545a8d719
tmpfs           1.6G   20K  1.6G   1% /run/user/125
tmpfs           1.6G   64K  1.6G   1% /run/user/1000
(base) bob@Emma:~$ 

and also du -d :
(base) bob@Emma:/$ sudo du -d 1 | sort -n
du: cannot access './run/user/1000/doc': Permission denied
du: cannot access './run/user/1000/gvfs': Permission denied
du: cannot access './run/user/125/gvfs': Permission denied
du: cannot read directory './proc/3138/task/3138/net': Invalid argument
du: cannot read directory './proc/3138/net': Invalid argument
du: cannot access './proc/7288/task/7288/fd/4': No such file or directory
du: cannot access './proc/7288/task/7288/fdinfo/4': No such file or directory
du: cannot access './proc/7288/fd/3': No such file or directory
du: cannot access './proc/7288/fdinfo/3': No such file or directory
0	./dev
0	./proc
0	./sys
4	./cdrom
4	./srv
8	./media
16	./lost+found
48	./mnt
208	./tmp
2364	./run
13012	./root
13028	./etc
80138	./boot
877324	./opt
5704024	./usr
10810048	./var
20545418	./snap
96048460	./home
134094107	.
(base) bob@Emma:/$

What should I do next?

---

### Post by Bashing-om on 2022-05-15
Baasha; Hello -

I would suspect logs running amok.

However, in my tightly controlled system, I show
> 
72	./tmp
1504	./run
4868	./grub
6604	./etc
13056	./sbin
13496	./bin
69832	./boot
251664	./opt
673868	./var
1272412	./lib
1944992	./usr
2156508	./home
7767864	.


Ouch! 
> 
/dev/sdd2 19G 17G 551M 97% /


as the system does get upset at greater than 90% usage
so ----
Logs in /var/log/ running amok ?
duplicate installs of snap apps and updating ?
log files in your /home ?


[INDENT]gots to be a reason
[/INDENT]

---

### Post by Dennis N on 2022-05-15
This might help:
Journals takes up space and continually grow. Check the size:

```
journalctl --disk-usage
Archived and active journals take up 3.0G in the file system.

```

Reduce to a certain size (20MB in the example below)

```
sudo journalctl --vacuum-size=20M
[omitting detailed output]
Vacuuming done, freed 2.9G of archived journals from /var/log/journal/9ed82d8ab296403d83c5d42c73c47c81.

```

So I recovered 2.9G of disk space.
Check regularly.

---

### Post by Impavidus on 2022-05-16
2-20MB growth each time you boot isn't that much. I suspect growing logs and accumulating updates. The old logs and software will be removed automatically, if you wait long enough, which will stabilise disk usage somewhat, but that may take until you've got some old versions of everything. You've got 10GB in /var, which has your logs and snaps (the snap directory has the mountpoints for your snaps, but not the actual storage).

The main thing is, 20GB for your root partition is just too small if you install a lot of snaps, and I see 37 of those. With a 1TB drive, there's no reason not to make the root partition a bit larger. Or do you think that a 980GB home partition will be much better than a 970GB home partition, enough to justify constantly keeping an eye on your root partition?

---

### Post by Baasha on 2022-05-16
@ Dennis
Thanks. Your tip helped. By setting vacuum_size to 20M I got my / down to 87%.
I still worry though about why my / is so big in the first place. I have another computer with an identical set-up and / only takes 3 GB. Any other ideas?

---

### Post by Holger_Gehrke on 2022-05-16
The snaps!

By my calculation those take about 6GB and slightly less than half of that is older versions of the same snaps kept at hand in case a new snap has a bug so you can revert quickly. Since snaps are isolated from the rest of the system and only see whatever libraries they bring along (or can get from other snaps), you've got three (slightly) different version of the Gnome Runtime (3.28, 3.34, and 3.38) in addition to the Gnome that comes with your system. On a system with a small root, snaps are generally not a great idea.
You can remove old snap versions with
```

snap remove --revision revision-number snap-package-name

for example

snap remove --revision 145 gnome-3-28-18-04

```
Be aware though: at the next refresh of your snaps the current version will again be kept as backup and you will have to go through removing the backups again.
To see what snaps are backups, you can use 'snap list --all', the backups have the word 'disabled in the last column of the output.

Holger

---

### Post by GhX6GZMB on 2022-05-16
The Wonder of snaps! Aren't they beautiful?
[/sarcasm]

---

