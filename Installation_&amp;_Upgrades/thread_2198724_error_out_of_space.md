---
title: "error: out of space"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by antsco on 2014-01-10
Hi all
I just reinstalled Ubunto 12.04 on my dell inspiron 6000 laptop, on top of Windows7
My hard disk is an older IDE drive of 320 Gb which, as I learned on a previous installation, has problems seeing disk spaces bigger than 137 Gb (my old laptop doesn't support newer SATA drives which I think do not present this kind of problems).
Nevertheless I chose to let ubuntu installer decide where to install ubuntu. The installation went apparently well but...when I rebooted
ZAP! I get an "error: out of disk"  message and after that the grub2 prompt emerges.

I used boot-repair to see if the problem could be fixed. I had to run it twice.
The first time run it with the general process, and it apparently solved the problem or so it said: (here is the result: ([http://paste.ubuntu.com/6723853](http://paste.ubuntu.com/6723853)) but upon rebooting...ZAP again! same error message.

I rerun boot-repair, going into the advanced options and marked the ATA disk check box, and this time too it said that the problem was solved
(with the following check list: [http://paste.ubuntu.com/6723859](http://paste.ubuntu.com/6723859)).
Indeed when I first rebooted it was all right, well almost, I first got an "error: can't find device" (or something similar), but after a few seconds the dual-loader boot menu appeared and could normally login into ubuntu.

After that, I downloaded lots of updates and finally shut the system down..and went to bed :KS
This morning I got again the same initial problem: error: our of disk, and I wonder why.
Could it have been caused by the fact that I downloaded so much system SW upgrades, so that what had been fixed has been manipulated again?

On the other hand my HD, as per when it was firstly installed Win7, had only one C: drive with some 98Gb of space, where Win7 was installed. Being aware that this problem could arise with my machine I hoped that the installer would install ubuntu in the same partition as where Win7 was installed so that the boot sector for ubuntu would be closer to the area that the BIOS can recognize (not sure if I am using the right terminology here), but I problably misread the instructions I had found in the ubuntu installation page
If we take a look at the image attached given by GParted and the pastebin from boot-repair, Ubuntu seems to have been installed on sda5 which is out of reach of the bios.
So....what can I do at this point to fix this?
Do I need to reinstall Ubuntu and specifiy to create a boot partition whitin sda2, and how? or what else?
Any help appreciated
All the best

Antonio

---

### Post by Mark Phelps on 2014-01-10
> I hoped that the installer would install ubuntu in the same partition as where Win7 was installed

The only way the Ubuntu installer can install INSIDE a Windows NTFS partition is if you use Wubi -- and support for that has been discontinued.

It looks like you installed Ubuntu to its own partition, anyway.

To confirm that, please open a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one) -- and post the results back here.

---

### Post by TheFu on 2014-01-10
Please post the output of 
```
df -h
df -i
```
Use the adv reply to wrap the output in "code" tags. Thanks.  This previously had the incorrect command, du. Sorry for the mistake.

Is this a **WUBI** install? If so, boot-repair won't help. It may damage things.  WUBI has many caveats to use. 
[https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)
I have **never** used WUBI myself. UEFI breaks it, so it will be unavailable going forward.

Without more detailed information, can't guess about this issue. Sorry. What do the log file show? That is the 1st place to look for system errors.  /var/log/*

I doubt the system is limited to 137G. Linux has worked around that for ... many, many years.  OTOH, if there is only 1 partition on the HDD and Linux was forced to share it with another OS, then that other OS has control over the partition space issues, NOT Linux. Any limitations of the other OS would still be there.

---

### Post by antsco on 2014-01-10
> 
To confirm that, please open a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one) -- and post the results back here.

Hi Mark
thx for your reply. Here the result of fdisk:


sudo fdisk -lu

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x0143a0cc

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   205826047   102809600    7  HPFS/NTFS/exFAT
/dev/sda3       205828094   625141759   209656833    5  Extendida
/dev/sda5       205828096   620949503   207560704   83  Linux
/dev/sda6       620951552   625141759     2095104   82  Linux swap / Solaris

Disco /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 cabezas, 63 sectores/pista, 121597 cilindros, 1953458176 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0xe1033c84

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT

Cheers
Antonio

---

### Post by oldfred on 2014-01-10
Ubuntu will not specify sizes or locations on drive if you have specific needs. Better to use Something Else or manual install and specify your own partitions.

Better to shrink Windows with Windows disk tools and reboot so it can run chkdsk.
Then either create a separate /boot partition 300 to 500MB fully within the first 100GB or create a smaller / (root) of 15 or 20GB and have separate /home and/or shared NTFS data partition. 
Do not shrink Windows NTFS partition too much as it needs 30% free space to work well, but it look like you have lots of unused space.

---

### Post by antsco on 2014-01-10
Hi TheFu
here is the result of du -h (du -i doesn't seem to work/exist on this version of ubuntu (12.04))
Although I reckon that this is only showing  the file system under the live demo installation which I am running, and not the file system which was installed on sda5
 so probably not very significant. If you know how to get the du -h of the partition where ububtu was installed please let me know

```

384K    ./.gstreamer-0.10
28K    ./.pki/nssdb
28K    ./.pki
4,0K    ./.googleearth/crashlogs
0    ./.googleearth/Temp
356K    ./.googleearth/Cache/webdata
0    ./.googleearth/Cache/qwebdata/offline_access/prepared
64K    ./.googleearth/Cache/qwebdata/offline_access/http
64K    ./.googleearth/Cache/qwebdata/offline_access
64K    ./.googleearth/Cache/qwebdata
0    ./.googleearth/Cache/models
120K    ./.googleearth/Cache/icons
4,1M    ./.googleearth/Cache/unified_cache_leveldb_leveldb2/lost
30M    ./.googleearth/Cache/unified_cache_leveldb_leveldb2
31M    ./.googleearth/Cache
31M    ./.googleearth
0    ./.shotwell
544K    ./.thumbnails/normal
544K    ./.thumbnails
0    ./.mozilla/extensions
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/CC
92K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/37
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/E0
48K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/EA
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/84
232K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/DF
160K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/6E
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/C9
108K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/A3
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/A9
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/91
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/79
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/3F
72K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/32
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/A8
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/7E
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/F/15
1,1M    ./.mozilla/firefox/02bz1kx5.default/Cache/F
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/96
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/DE
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/28
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/E8
104K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/BF
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/17
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/1C
76K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/BB
104K    ./.mozilla/firefox/02bz1kx5.default/Cache/E/5F
468K    ./.mozilla/firefox/02bz1kx5.default/Cache/E
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/9A
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/30
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/CD
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/F1
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/85
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/CB
80K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/10
48K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/45
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/8B
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/C6
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/D/B3
460K    ./.mozilla/firefox/02bz1kx5.default/Cache/D
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/5D
108K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/9C
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/D2
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/77
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/9E
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/3C
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/04
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/5C
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/D6
204K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/3B
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/E5
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/CC
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/C/EE
700K    ./.mozilla/firefox/02bz1kx5.default/Cache/C
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/29
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/09
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/0E
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/77
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/27
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/64
80K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/F3
132K    ./.mozilla/firefox/02bz1kx5.default/Cache/B/3A
432K    ./.mozilla/firefox/02bz1kx5.default/Cache/B
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/C3
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/70
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/4D
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/F3
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/EE
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/A/2E
216K    ./.mozilla/firefox/02bz1kx5.default/Cache/A
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/56
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/99
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/A7
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/86
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/11
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/54
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/2F
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/C3
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/BE
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/9/91
348K    ./.mozilla/firefox/02bz1kx5.default/Cache/9
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/3C
76K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/24
136K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/AD
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/C9
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/D8
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/37
92K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/47
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/33
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/ED
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/30
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/EB
104K    ./.mozilla/firefox/02bz1kx5.default/Cache/8/D9
736K    ./.mozilla/firefox/02bz1kx5.default/Cache/8
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/5E
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/E1
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/C4
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/16
72K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/A1
80K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/34
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/31
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/14
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/7/50
364K    ./.mozilla/firefox/02bz1kx5.default/Cache/7
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/4E
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/4C
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/74
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/BC
108K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/E6
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/27
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/15
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/6/E4
360K    ./.mozilla/firefox/02bz1kx5.default/Cache/6
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/D5
752K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/09
48K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/F2
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/8C
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/3A
132K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/C3
212K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/62
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/79
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/A0
88K    ./.mozilla/firefox/02bz1kx5.default/Cache/5/69
1,4M    ./.mozilla/firefox/02bz1kx5.default/Cache/5
40K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/66
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/54
64K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/A8
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/56
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/B5
240K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/FA
48K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/22
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/4/85
504K    ./.mozilla/firefox/02bz1kx5.default/Cache/4
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/70
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/5D
32K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/62
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/18
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/4C
108K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/C7
356K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/A9
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/3/CB
720K    ./.mozilla/firefox/02bz1kx5.default/Cache/3
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/02
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/3C
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/11
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/DD
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/D4
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/BA
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/07
60K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/4A
24K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/A4
36K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/25
56K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/C7
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/2/21
404K    ./.mozilla/firefox/02bz1kx5.default/Cache/2
172K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/04
76K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/3D
108K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/A2
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/90
28K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/84
68K    ./.mozilla/firefox/02bz1kx5.default/Cache/1/17
480K    ./.mozilla/firefox/02bz1kx5.default/Cache/1
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/F5
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/21
44K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/74
52K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/6A
188K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/01
116K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/F0
20K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/D7
136K    ./.mozilla/firefox/02bz1kx5.default/Cache/0/4C
596K    ./.mozilla/firefox/02bz1kx5.default/Cache/0
14M    ./.mozilla/firefox/02bz1kx5.default/Cache
8,0K    ./.mozilla/firefox/02bz1kx5.default/bookmarkbackups
728K    ./.mozilla/firefox/02bz1kx5.default/startupCache
0    ./.mozilla/firefox/02bz1kx5.default/minidumps
75M    ./.mozilla/firefox/02bz1kx5.default
4,0K    ./.mozilla/firefox/Crash Reports
75M    ./.mozilla/firefox
75M    ./.mozilla
4,0K    ./.mission-control/accounts
4,0K    ./.mission-control
0    ./.gvfs
0    ./.gnome2/nautilus-scripts
0    ./.gnome2/keyrings
0    ./.gnome2
0    ./Vídeos
2,2M    ./Imágenes
0    ./Música
4,0K    ./Documentos
0    ./Público
0    ./Plantillas
44M    ./Descargas
4,0K    ./.local/share/applications
20K    ./.local/share/webkit/icondatabase
20K    ./.local/share/webkit
204K    ./.local/share/zeitgeist/fts.index
1,4M    ./.local/share/zeitgeist
4,0K    ./.local/share/telepathy/mission-control
4,0K    ./.local/share/telepathy
144K    ./.local/share/gvfs-metadata
0    ./.local/share/icc
1,5M    ./.local/share
1,5M    ./.local
24K    ./.fontconfig
36K    ./.pulse
12K    ./.config/gedit
12K    ./.config/Google
0    ./.config/software-center
4,0K    ./.config/eog
0    ./.config/update-notifier
0    ./.config/goa-1.0
0    ./.config/gnome-disk-utility/ata-smart-ignore
0    ./.config/gnome-disk-utility
4,0K    ./.config/nautilus
0    ./.config/compiz-1/compizconfig
0    ./.config/compiz-1
0    ./.config/gnome-session/saved-session
0    ./.config/gnome-session
4,0K    ./.config/ibus/bus
4,0K    ./.config/ibus
8,0K    ./.config/dconf
56K    ./.config
4,0K    ./.gconf/desktop/ibus/general
4,0K    ./.gconf/desktop/ibus
4,0K    ./.gconf/desktop
4,0K    ./.gconf/apps/gedit-2/plugins
4,0K    ./.gconf/apps/gedit-2/preferences/ui/statusbar
4,0K    ./.gconf/apps/gedit-2/preferences/ui
4,0K    ./.gconf/apps/gedit-2/preferences
8,0K    ./.gconf/apps/gedit-2
4,0K    ./.gconf/apps/gnome-terminal/profiles/Default
4,0K    ./.gconf/apps/gnome-terminal/profiles
4,0K    ./.gconf/apps/gnome-terminal
4,0K    ./.gconf/apps/file-roller/ui
4,0K    ./.gconf/apps/file-roller/listing
8,0K    ./.gconf/apps/file-roller
4,0K    ./.gconf/apps/eog/view
4,0K    ./.gconf/apps/eog/ui
8,0K    ./.gconf/apps/eog
4,0K    ./.gconf/apps/shotwell/preferences/window
4,0K    ./.gconf/apps/shotwell/preferences
4,0K    ./.gconf/apps/shotwell
4,0K    ./.gconf/apps/nautilus/preferences
4,0K    ./.gconf/apps/nautilus
4,0K    ./.gconf/apps/deja-dup/s3
8,0K    ./.gconf/apps/deja-dup
4,0K    ./.gconf/apps/update-notifier
4,0K    ./.gconf/apps/compizconfig-1
4,0K    ./.gconf/apps/compiz-1/plugins/gnomecompat/screen0/options
4,0K    ./.gconf/apps/compiz-1/plugins/gnomecompat/screen0
4,0K    ./.gconf/apps/compiz-1/plugins/gnomecompat
4,0K    ./.gconf/apps/compiz-1/plugins
4,0K    ./.gconf/apps/compiz-1/general/screen0/options
4,0K    ./.gconf/apps/compiz-1/general/screen0
4,0K    ./.gconf/apps/compiz-1/general
8,0K    ./.gconf/apps/compiz-1
4,0K    ./.gconf/apps/nm-applet
4,0K    ./.gconf/apps/metacity/window_keybindings
4,0K    ./.gconf/apps/metacity/global_keybindings
4,0K    ./.gconf/apps/metacity/general
12K    ./.gconf/apps/metacity
76K    ./.gconf/apps
80K    ./.gconf
4,0K    ./.dbus/session-bus
4,0K    ./.dbus
6,0M    ./.cache/software-center/software-center-agent.db
488K    ./.cache/software-center/download-cache
800K    ./.cache/software-center/reviews.ubuntu.com_reviews_api_1.0_review-stats-pkgnames.p__5.1.db.dbenv
3,6M    ./.cache/software-center/piston-helper
4,0K    ./.cache/software-center/rnrclient
48K    ./.cache/software-center/icons
13M    ./.cache/software-center
0    ./.cache/gnome-screenshot
4,0K    ./.cache/unity-lens-video
4,0K    ./.cache/ubuntuone/log
4,0K    ./.cache/ubuntuone
4,0K    ./.cache/sso
4,0K    ./.cache/indicators/messages
4,0K    ./.cache/indicators
4,0K    ./.cache/indicator-appmenu
4,0K    ./.cache/unity
0    ./.cache/gvfs-burn
368K    ./.cache/wallpaper
112K    ./.cache/compizconfig-1
0    ./.cache/indicator/sound/album-art-cache
0    ./.cache/indicator/sound
0    ./.cache/indicator
8,0K    ./.cache/ibus/bus
8,0K    ./.cache/ibus
4,0K    ./.cache/dconf
13M    ./.cache
20K    ./Desktop
166M    .

```

---

### Post by antsco on 2014-01-10
Hi Oldfred
thx for your reply
Actually my initial idea was to install ubunto within those 98Gb where Windows is installed by shrinking it somehow, and I thougth that this would happen through the installer (need to reed more carefully next time) but, how can I implement what you write?   I guess this would mean to unistall the ububtu installation and start again, right? Right now I cannot access windows. 
Any suggested steps of action? 
All the best
Antonio

---

### Post by oldfred on 2014-01-10
You can install a Windows boot loader. Use your Windows repairCD or flash drive or Boot-Repair can install a Windows like boot loader, but not do other Windows repairs.
With boot repair it will just auto fix grub, which still will not work, but you manually can choose in Advanced tab Windows and sda and it will put a Windows type boot loader in.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by TheFu on 2014-01-10
My mistake - should have been 
```
df -h 
df -i
```

I'm very sorry.  Will change the post above accordingly.

---

### Post by antsco on 2014-01-10
> With boot repair it will just auto fix grub, which still will not work,  but you manually can choose in Advanced tab Windows and sda and it will  put a Windows type boot loader in.

Hi Oldfred
I run the boot-repair utility by using the advanced options as you explain, and this is the generated report [http://paste.ubuntu.com/6728036/](http://paste.ubuntu.com/6728036/)

After rebooting, things haven't changed though and can't still access windows either.
Best regards
Antonio

---

### Post by oldfred on 2014-01-10
You still have grub in MBR. You need to use advanced mode not auto fix and choose Windows and sda to add a Windows boot loader.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)



Or use Windows.
       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by antsco on 2014-01-10
> **oldfred said:**
> You still have grub in MBR. You need to use advanced mode not auto fix and choose Windows and sda to add a Windows boot loader.[l]("http://www.bleepingcomputer.com/tutorials/tutorial148.html")
Hi
I tried to do what you suggest. I run boot-repair in advanced mode and checked 
- reinstall GRUB in the Main options tab
-Windows & sda in the GRUB Location
- Reset extra space after MBR + Uncomment GRUB_GFXMODE+ATA disk support

This was apparently successful since I can now make linux boot finally
The only problem is that I cannot boot into windows.

At startup the dual loader menu appears although the characters are bigger than usual
This gives me the possibility to start up form either ubuntu or Windows either in sda1 or in sda2
but none of them works. When I try to bood with any of them I receive a disk error message
I wonder if this can be due to the options that I checked above.

Also I tried to repair the Windows part running the start-up repair for Windows 7 but dind't work.

Eventually I removed ubuntu and will try to reinstall it by selcting disk space within 100 Gb
Thanks for all your help 
Cheers
Antonio
Antonio

---

### Post by oldfred on 2014-01-11
Grub only boots a working Windows. So I still might install a Windows boot loader to MBR. Most have said that booting Windows from grub is so quick that f8 to get into recovery is difficult, you have to be very quick.
Or better to use the Windows repair CD or flash drive to fix Windows.

Reinstalling Ubuntu will not fix Windows booting. 
Also be careful to only use manual install or Something else. If you do not see Windows and multiple operating systems during install choices, and it only sees Ubuntu, then it will erase entire drive as it does not correctly see Windows. With manual install you just choose existing partitions. 

But if Ubuntu boots you do not need to reinstall?

---

