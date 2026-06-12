---
title: "various problems after lubuntu 14.04 install"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2015-11-12
I have just installed Lubuntu 14.04.3 on an old laptop (HP-Compaq nx7010) and I am experiencing a number of strange problems:
1) USB drives  are not mounted automatically, but the system sees them (command sudo fdisk -l) I can mount them from terminal (it takes a while!) but the file manager PCManFM doesn't see them anyway; I can see the drives content in terminal only (command ls).
2) sometimes the keyboard stops working and I have to reboot to get it working again.
3) the laptop doesn't turn off on command, it freezes in the process (black screen with Lubuntu in the middle) and I have to hit the power button to shut it down.

I am on the verge to try a lubuntu reinstall, but first I ask for some hint...

---

### Post by mörgæs on 2015-11-13
If you decide to reinstall I suggest that you try 15.10.

---

### Post by vasa1 on 2015-11-13
Re. mounting of USB drives, please post the contents of ls -alR ~/.config/pcmanfm. This is what I have:```
06:30 PM ~ $ ls -alR ~/.config/pcmanfm
/home/vasa1/.config/pcmanfm:
total 16
drwx------  4 vasa1 vasa1 4096 Nov 14  2014 .
drwx------ 38 vasa1 vasa1 4096 Nov  7 10:19 ..
drwx------  2 vasa1 vasa1 4096 Nov 13 18:27 default
drwx------  2 vasa1 vasa1 4096 Oct 31 00:01 lubuntu

/home/vasa1/.config/pcmanfm/default:
total 12
drwx------ 2 vasa1 vasa1 4096 Nov 13 18:27 .
drwx------ 4 vasa1 vasa1 4096 Nov 14  2014 ..
-rw-rw-r-- 1 vasa1 vasa1  462 Nov 13 18:27 pcmanfm.conf

/home/vasa1/.config/pcmanfm/lubuntu:
total 16
drwx------ 2 vasa1 vasa1 4096 Oct 31 00:01 .
drwx------ 4 vasa1 vasa1 4096 Nov 14  2014 ..
-rw-rw-r-- 1 vasa1 vasa1  306 Nov 14  2014 desktop-items-0.conf
-rw-rw-r-- 1 vasa1 vasa1  461 Oct 31 00:01 pcmanfm.conf
06:30 PM ~ $ 

```
Then please post the contents of each pcmanfm.conf file. You can modify the settings under **[volume]**, by opening pcmanfm and clicking on Edit, Preferences, Volume Management. It's best **not** to edit pcmanfm.conf directly.

Your other issues may be related to the age of your hardware. I'm using Lubuntu 14.04.3 on a laptop from 2009 and don't have such issues.

---

### Post by Gingalone on 2015-11-16
Vasa1, here the output you asked for:
```
ls -alR ~/.config/pcmanfm

pcmanfm.conf

cecilia@cecilia-HP-compaq-nx7010-DU259A-ABZ:~$ ls -alR ~/.config/pcmanfm
/home/cecilia/.config/pcmanfm:
totale 12
drwx------  3 cecilia cecilia 4096 ott 22 13:38 .
drwx------ 21 cecilia cecilia 4096 nov  9 10:02 ..
drwx------  2 cecilia cecilia 4096 nov 16 09:59 lubuntu

/home/cecilia/.config/pcmanfm/lubuntu:
totale 16
drwx------ 2 cecilia cecilia 4096 nov 16 09:59 .
drwx------ 3 cecilia cecilia 4096 ott 22 13:38 ..
-rw-rw-r-- 1 cecilia cecilia  364 nov 16 09:59 desktop-items-0.conf
-rw-rw-r-- 1 cecilia cecilia  419 nov 12 17:28 pcmanfm.conf

cecilia@cecilia-HP-compaq-nx7010-DU259A-ABZ:~/.config/pcmanfm$ cd lubuntu
cecilia@cecilia-HP-compaq-nx7010-DU259A-ABZ:~/.config/pcmanfm/lubuntu$ ls -la
totale 16
drwx------ 2 cecilia cecilia 4096 nov 16 09:59 .
drwx------ 3 cecilia cecilia 4096 ott 22 13:38 ..
-rw-rw-r-- 1 cecilia cecilia  364 nov 16 09:59 desktop-items-0.conf
-rw-rw-r-- 1 cecilia cecilia  419 nov 12 17:28 pcmanfm.conf

cecilia@cecilia-HP-compaq-nx7010-DU259A-ABZ:~/.config/pcmanfm/lubuntu$ cat pcmanfm.conf
[config]
bm_open_method=0

[volume]
mount_on_startup=1
mount_removable=1
autorun=1

[ui]
always_show_tabs=1
max_tab_chars=32
win_width=821
win_height=555
splitter_pos=322
media_in_new_tab=0
desktop_folder_new_win=1
change_tab_on_drop=1
close_on_unmount=1
focus_previous=0
side_pane_mode=dirtree
view_mode=icon
show_hidden=0
sort=mtime;descending;
toolbar=newtab;navigation;home;
show_statusbar=1
pathbar_mode_buttons=0

```

---

