---
title: "Mysql failed to start after todays updates"
date: 2019-04-24
forum: Installation &amp; Upgrades
---

### Post by drifting on 2019-04-24
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-04-24 18:08:33 BST; 1min 6s ago
  Process: 1061 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAIL

Apr 24 18:08:33 MicroServer systemd[1]: mysql.service: Service hold-off time over, scheduling res
Apr 24 18:08:33 MicroServer systemd[1]: mysql.service: Scheduled restart job, restart counter is 
Apr 24 18:08:33 MicroServer systemd[1]: Stopped MySQL Community Server.
Apr 24 18:08:33 MicroServer systemd[1]: mysql.service: Start request repeated too quickly.
Apr 24 18:08:33 MicroServer systemd[1]: mysql.service: Failed with result 'exit-code'.
Apr 24 18:08:33 MicroServer systemd[1]: Failed to start MySQL Community Server.

Tried the usual :-
mysql -u root mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
sudo mysqld_safe --skip-grant-tables &

Same as above.

At a total loss now, and beyond my knowledge. This was an upgrade from 16.04. Was working fine till I did some update today, must admit only noticed kernel updates, so did not sound any alarm bells.

Been fighting with the upgrade for over a year desperate to get this sorted, wifey will not be happy without TV. ;-)

Any help really appreciated. Cannot see wood for trees at the moment.

Best wishes Paul

---

### Post by SeijiSensei on 2019-04-24
Let's start with a look at the permissions on /var/lib/mysql. Please run the command 
```
sudo ls -lR /var/lib/mysql
```
and see if any files, other than debian-5.7-flag, have another owner or group besides mysql.

If they do, you can fix the problem like this
```

cd /var/lib
sudo chown mysql:mysql -R mysql

```
The -R switch causes chown to recurse down the directory structure.

I just installed mysql-server on this 19.04 machine. All the files in all the directories and subdirectories except the irrelevant debian-5.7-flag are owned the mysql user and mysql group.

---

### Post by drifting on 2019-04-24
Thank you so much for responding.

Not sure what I am looking for, but it all seems to be right with mysql:mysql

/var/lib/mysql:
total 176180
-rw-r----- 1 mysql mysql       56 Jul 31  2018 auto.cnf
-rw-r--r-- 1 mysql mysql        0 Apr 10 15:04 debian-5.7.flag
-rw-r----- 1 mysql mysql      517 Apr 24 17:03 ib_buffer_pool
-rw-r----- 1 mysql mysql 79691776 Apr 24 17:03 ibdata1
-rw-r----- 1 mysql mysql 50331648 Apr 24 17:03 ib_logfile0
-rw-r----- 1 mysql mysql 50331648 Apr 24 17:03 ib_logfile1
drwxr-x--- 2 mysql mysql     4096 Apr 10 15:05 mysql
-rw-r--r-- 1 mysql mysql        6 Apr 10 15:05 mysql_upgrade_info
drwxr-x--- 2 mysql mysql    20480 Apr 24 00:10 mythconverg
drwxr-x--- 2 mysql mysql     4096 Apr 10 15:04 performance_schema
drwxr-x--- 2 mysql mysql    12288 Jul 31  2018 sys

/var/lib/mysql/mysql:
total 22792
-rw-r----- 1 mysql mysql     8820 Apr 10 15:04 columns_priv.frm
-rw-r----- 1 mysql mysql        0 Apr 10 15:04 columns_priv.MYD
-rw-r----- 1 mysql mysql     4096 Apr 10 15:04 columns_priv.MYI
-rw-r----- 1 mysql mysql     9582 Apr 10 15:04 db.frm
-rw-r----- 1 mysql mysql     1464 Apr 12 13:11 db.MYD
-rw-r----- 1 mysql mysql     5120 Apr 12 13:17 db.MYI
-rw-r----- 1 mysql mysql       65 Jul 31  2018 db.opt
-rw-r----- 1 mysql mysql     8780 Jul 31  2018 engine_cost.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 engine_cost.ibd
-rw-r----- 1 mysql mysql    10223 Apr 10 15:04 event.frm
-rw-r----- 1 mysql mysql        0 Apr 10 15:04 event.MYD
-rw-r----- 1 mysql mysql     2048 Apr 10 15:04 event.MYI
-rw-r----- 1 mysql mysql     8665 Apr 10 15:04 func.frm
-rw-r----- 1 mysql mysql        0 Apr 10 15:04 func.MYD
-rw-r----- 1 mysql mysql     1024 Apr 10 15:04 func.MYI
-rw-r----- 1 mysql mysql       35 Apr 10 15:05 general_log.CSM
-rw-r----- 1 mysql mysql        0 Apr 10 15:04 general_log.CSV
-rw-r----- 1 mysql mysql     8776 Apr 10 15:04 general_log.frm
-rw-r----- 1 mysql mysql     8784 Apr 10 15:04 gtid_executed.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 gtid_executed.ibd
-rw-r----- 1 mysql mysql     8700 Apr 10 15:04 help_category.frm
-rw-r----- 1 mysql mysql   114688 Apr 10 15:05 help_category.ibd
-rw-r----- 1 mysql mysql     8612 Apr 10 15:04 help_keyword.frm
-rw-r----- 1 mysql mysql   262144 Apr 10 15:05 help_keyword.ibd
-rw-r----- 1 mysql mysql     8630 Apr 10 15:04 help_relation.frm
-rw-r----- 1 mysql mysql   147456 Apr 10 15:05 help_relation.ibd
-rw-r----- 1 mysql mysql     8770 Apr 10 15:04 help_topic.frm
-rw-r----- 1 mysql mysql  7340032 Apr 10 15:05 help_topic.ibd
-rw-r----- 1 mysql mysql    12982 Apr 10 15:05 innodb_index_stats.frm
-rw-r----- 1 mysql mysql    98304 Apr 24 00:09 innodb_index_stats.ibd
-rw-r----- 1 mysql mysql     8830 Apr 10 15:05 innodb_table_stats.frm
-rw-r----- 1 mysql mysql    98304 Apr 24 00:09 innodb_table_stats.ibd
-rw-r----- 1 mysql mysql     8986 Apr 10 15:04 ndb_binlog_index.frm
-rw-r----- 1 mysql mysql        0 Jul 31  2018 ndb_binlog_index.MYD
-rw-r----- 1 mysql mysql     1024 Jul 31  2018 ndb_binlog_index.MYI
-rw-r----- 1 mysql mysql     8586 Apr 10 15:04 plugin.frm
-rw-r----- 1 mysql mysql    98304 Apr 10 15:05 plugin.ibd
-rw-r----- 1 mysql mysql     9996 Apr 10 15:04 proc.frm
-rw-r----- 1 mysql mysql   301032 Apr 10 15:04 proc.MYD
-rw-r----- 1 mysql mysql     4096 Apr 10 15:05 proc.MYI
-rw-r----- 1 mysql mysql     8875 Apr 10 15:04 procs_priv.frm
-rw-r----- 1 mysql mysql        0 Apr 10 15:04 procs_priv.MYD
-rw-r----- 1 mysql mysql     4096 Apr 10 15:04 procs_priv.MYI
-rw-r----- 1 mysql mysql     8800 Apr 10 15:04 proxies_priv.frm
-rw-r----- 1 mysql mysql      837 Jul 31  2018 proxies_priv.MYD
-rw-r----- 1 mysql mysql     9216 Jul 31  2018 proxies_priv.MYI
-rw-r----- 1 mysql mysql     8692 Jul 31  2018 server_cost.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 server_cost.ibd
-rw-r----- 1 mysql mysql     8838 Apr 10 15:04 servers.frm
-rw-r----- 1 mysql mysql    98304 Apr 10 15:05 servers.ibd
-rw-r----- 1 mysql mysql    10908 Apr 10 15:04 slave_master_info.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 slave_master_info.ibd
-rw-r----- 1 mysql mysql     9468 Apr 10 15:04 slave_relay_log_info.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 slave_relay_log_info.ibd
-rw-r----- 1 mysql mysql     9364 Apr 10 15:04 slave_worker_info.frm
-rw-r----- 1 mysql mysql    98304 Jul 31  2018 slave_worker_info.ibd
-rw-r----- 1 mysql mysql       35 Apr 10 15:05 slow_log.CSM
-rw-r----- 1 mysql mysql        0 Jul 31  2018 slow_log.CSV
-rw-r----- 1 mysql mysql     9016 Apr 10 15:04 slow_log.frm
-rw-r----- 1 mysql mysql     8955 Apr 10 15:04 tables_priv.frm
-rw-r----- 1 mysql mysql     1894 Apr 10 15:04 tables_priv.MYD
-rw-r----- 1 mysql mysql     9216 Apr 10 15:05 tables_priv.MYI
-rw-r----- 1 mysql mysql     8636 Apr 10 15:04 time_zone.frm
-rw-r----- 1 mysql mysql   147456 Apr 12 13:11 time_zone.ibd
-rw-r----- 1 mysql mysql     8624 Apr 10 15:04 time_zone_leap_second.frm
-rw-r----- 1 mysql mysql    98304 Apr 10 15:05 time_zone_leap_second.ibd
-rw-r----- 1 mysql mysql     8606 Apr 10 15:04 time_zone_name.frm
-rw-r----- 1 mysql mysql   327680 Apr 12 13:11 time_zone_name.ibd
-rw-r----- 1 mysql mysql     8686 Apr 10 15:05 time_zone_transition.frm
-rw-r----- 1 mysql mysql 12582912 Apr 12 13:11 time_zone_transition.ibd
-rw-r----- 1 mysql mysql     8748 Apr 10 15:05 time_zone_transition_type.frm
-rw-r----- 1 mysql mysql   524288 Apr 12 13:11 time_zone_transition_type.ibd
-rw-r----- 1 mysql mysql    10816 Apr 10 15:04 user.frm
-rw-r----- 1 mysql mysql      636 Apr 12 13:11 user.MYD
-rw-r----- 1 mysql mysql     4096 Apr 12 13:17 user.MYI

/var/lib/mysql/mythconverg:
total 842880
-rw-r----- 1 mysql mysql      9255 Apr 12 13:11 archiveitems.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 archiveitems.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 archiveitems.MYI
-rw-r----- 1 mysql mysql     20962 Apr 12 13:22 bdbookmark.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 bdbookmark.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 bdbookmark.MYI
-rw-r----- 1 mysql mysql      8630 Apr 12 13:11 callsignnetworkmap.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 callsignnetworkmap.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 callsignnetworkmap.MYI
-rw-r----- 1 mysql mysql     10482 Apr 12 13:22 capturecard.frm
-rw-r----- 1 mysql mysql      1040 Apr 24 00:08 capturecard.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 capturecard.MYI
-rw-r----- 1 mysql mysql      9172 Apr 12 13:11 cardinput.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 cardinput.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 cardinput.MYI
-rw-r----- 1 mysql mysql     13784 Apr 12 13:11 channel.frm
-rw-r----- 1 mysql mysql      8622 Apr 12 13:11 channelgroup.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 channelgroup.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 channelgroup.MYI
-rw-r----- 1 mysql mysql      8592 Apr 12 13:11 channelgroupnames.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 channelgroupnames.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 channelgroupnames.MYI
-rw-r----- 1 mysql mysql     40196 Apr 24 12:58 channel.MYD
-rw-r----- 1 mysql mysql     27648 Apr 24 15:05 channel.MYI
-rw-r----- 1 mysql mysql     10206 Apr 12 13:11 channelscan_channel.frm
-rw-r----- 1 mysql mysql    777772 Apr 24 00:08 channelscan_channel.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 channelscan_channel.MYI
-rw-r----- 1 mysql mysql      9412 Apr 12 13:11 channelscan_dtv_multiplex.frm
-rw-r----- 1 mysql mysql     63852 Apr 24 00:08 channelscan_dtv_multiplex.MYD
-rw-r----- 1 mysql mysql     10240 Apr 24 00:08 channelscan_dtv_multiplex.MYI
-rw-r----- 1 mysql mysql      8714 Apr 12 13:11 channelscan.frm
-rw-r----- 1 mysql mysql       380 Apr 24 00:08 channelscan.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 channelscan.MYI
-rw-r----- 1 mysql mysql      8628 Apr 12 13:11 codecparams.frm
-rw-r----- 1 mysql mysql      1168 Apr 24 00:08 codecparams.MYD
-rw-r----- 1 mysql mysql      4096 Apr 24 00:08 codecparams.MYI
-rw-r----- 1 mysql mysql      8772 Apr 12 13:11 credits.frm
-rw-r----- 1 mysql mysql     41685 Apr 24 14:55 credits.MYD
-rw-r----- 1 mysql mysql    106496 Apr 24 15:05 credits.MYI
-rw-r----- 1 mysql mysql     66032 Apr 12 13:11 customexample.frm
-rw-r----- 1 mysql mysql       140 Apr 24 00:08 customexample.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 customexample.MYI
-rw-r----- 1 mysql mysql        61 Apr 12 13:22 db.opt
-rw-r----- 1 mysql mysql      8644 Apr 12 13:11 diseqc_config.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 diseqc_config.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 diseqc_config.MYI
-rw-r----- 1 mysql mysql      9336 Apr 12 13:22 diseqc_tree.frm
-rw-r----- 1 mysql mysql       112 Apr 24 00:08 diseqc_tree.MYD
-rw-r----- 1 mysql mysql      3072 Apr 24 00:08 diseqc_tree.MYI
-rw-r----- 1 mysql mysql      8648 Apr 12 13:11 displayprofilegroups.frm
-rw-r----- 1 mysql mysql      6356 Apr 24 00:08 displayprofilegroups.MYD
-rw-r----- 1 mysql mysql     17408 Apr 24 00:08 displayprofilegroups.MYI
-rw-r----- 1 mysql mysql      8682 Apr 12 13:11 displayprofiles.frm
-rw-r----- 1 mysql mysql    169760 Apr 24 00:08 displayprofiles.MYD
-rw-r----- 1 mysql mysql    206848 Apr 24 00:08 displayprofiles.MYI
-rw-r----- 1 mysql mysql      9600 Apr 12 13:11 dtv_multiplex.frm
-rw-r----- 1 mysql mysql      5828 Apr 24 00:08 dtv_multiplex.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 dtv_multiplex.MYI
-rw-r----- 1 mysql mysql      8698 Apr 12 13:11 dtv_privatetypes.frm
-rw-r----- 1 mysql mysql      1560 Apr 24 00:08 dtv_privatetypes.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 dtv_privatetypes.MYI
-rw-r----- 1 mysql mysql      8828 Apr 12 13:11 dvdbookmark.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 dvdbookmark.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 dvdbookmark.MYI
-rw-r----- 1 mysql mysql      8812 Apr 12 13:11 dvdinput.frm
-rw-r----- 1 mysql mysql       288 Apr 24 00:08 dvdinput.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 dvdinput.MYI
-rw-r----- 1 mysql mysql      9580 Apr 12 13:11 dvdtranscode.frm
-rw-r----- 1 mysql mysql       600 Apr 24 00:08 dvdtranscode.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 dvdtranscode.MYI
-rw-r----- 1 mysql mysql      8742 Apr 12 13:11 eit_cache.frm
-rw-r----- 1 mysql mysql    459824 Apr 24 15:05 eit_cache.MYD
-rw-r----- 1 mysql mysql    507904 Apr 24 15:05 eit_cache.MYI
-rw-r----- 1 mysql mysql      8662 Apr 24 00:10 filemarkup.frm
-rw-r----- 1 mysql mysql      2408 Apr 24 00:10 filemarkup.MYD
-rw-r----- 1 mysql mysql      8192 Apr 24 00:10 filemarkup.MYI
-rw-r----- 1 mysql mysql      8818 Apr 12 13:22 gallery_directories.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 gallery_directories.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 gallery_directories.MYI
-rw-r----- 1 mysql mysql      9004 Apr 12 13:22 gallery_files.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 gallery_files.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 gallery_files.MYI
-rw-r----- 1 mysql mysql      8594 Apr 12 13:11 gallerymetadata.frm
-rw-r----- 1 mysql mysql        96 Apr 24 00:08 gallerymetadata.MYD
-rw-r----- 1 mysql mysql      8192 Apr 24 00:08 gallerymetadata.MYI
-rw-r----- 1 mysql mysql     13392 Apr 12 13:11 gamemetadata.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 gamemetadata.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 gamemetadata.MYI
-rw-r----- 1 mysql mysql      8906 Apr 12 13:11 gameplayers.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 gameplayers.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 gameplayers.MYI
-rw-r----- 1 mysql mysql      8676 Apr 12 13:22 housekeeping.frm
-rw-r----- 1 mysql mysql       656 Apr 24 14:16 housekeeping.MYD
-rw-r----- 1 mysql mysql      4096 Apr 24 15:05 housekeeping.MYI
-rw-r----- 1 mysql mysql      8670 Apr 12 13:22 inputgroup.frm
-rw-r----- 1 mysql mysql       384 Apr 24 00:08 inputgroup.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 inputgroup.MYI
-rw-r----- 1 mysql mysql     13698 Apr 12 13:11 internetcontentarticles.frm
-rw-r----- 1 mysql mysql   3648496 Apr 24 00:08 internetcontentarticles.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 internetcontentarticles.MYI
-rw-r----- 1 mysql mysql      8992 Apr 12 13:11 internetcontent.frm
-rw-r----- 1 mysql mysql      8252 Apr 24 00:08 internetcontent.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 internetcontent.MYI
-rw-r----- 1 mysql mysql      8800 Apr 12 13:11 inuseprograms.frm
-rw-r----- 1 mysql mysql       168 Apr 24 14:56 inuseprograms.MYD
-rw-r----- 1 mysql mysql      5120 Apr 24 15:05 inuseprograms.MYI
-rw-r----- 1 mysql mysql      8763 Apr 12 13:11 iptv_channel.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 iptv_channel.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 iptv_channel.MYI
-rw-r----- 1 mysql mysql      8990 Apr 12 13:11 jobqueue.frm
-rw-r----- 1 mysql mysql     24384 Apr 24 14:22 jobqueue.MYD
-rw-r----- 1 mysql mysql     23552 Apr 24 15:05 jobqueue.MYI
-rw-r----- 1 mysql mysql      8692 Apr 12 13:11 jumppoints.frm
-rw-r----- 1 mysql mysql     33260 Apr 24 00:08 jumppoints.MYD
-rw-r----- 1 mysql mysql     22528 Apr 24 00:08 jumppoints.MYI
-rw-r----- 1 mysql mysql      8718 Apr 12 13:11 keybindings.frm
-rw-r----- 1 mysql mysql    439920 Apr 24 00:08 keybindings.MYD
-rw-r----- 1 mysql mysql    126976 Apr 24 00:08 keybindings.MYI
-rw-r----- 1 mysql mysql      8606 Apr 12 13:11 keyword.frm
-rw-r----- 1 mysql mysql      1416 Apr 24 00:08 keyword.MYD
-rw-r----- 1 mysql mysql      4096 Apr 24 00:08 keyword.MYI
-rw-r----- 1 mysql mysql     17810 Apr 12 13:11 livestream.frm
-rw-r----- 1 mysql mysql       776 Apr 24 00:08 livestream.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 livestream.MYI
-rw-r----- 1 mysql mysql     17122 Apr 12 13:11 logging.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 logging.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 logging.MYI
-rw-r----- 1 mysql mysql      8674 Apr 12 13:11 movies_movies.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 movies_movies.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 movies_movies.MYI
-rw-r----- 1 mysql mysql      8672 Apr 12 13:11 movies_showtimes.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 movies_showtimes.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 movies_showtimes.MYI
-rw-r----- 1 mysql mysql      8650 Apr 12 13:11 movies_theaters.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 movies_theaters.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 movies_theaters.MYI
-rw-r----- 1 mysql mysql      8810 Apr 12 18:56 music_albumart.frm
-rw-r----- 1 mysql mysql    119864 Apr 24 00:08 music_albumart.MYD
-rw-r----- 1 mysql mysql     46080 Apr 24 00:08 music_albumart.MYI
-rw-r----- 1 mysql mysql      8724 Apr 12 18:56 music_albums.frm
-rw-r----- 1 mysql mysql    105988 Apr 24 00:08 music_albums.MYD
-rw-r----- 1 mysql mysql     94208 Apr 24 00:08 music_albums.MYI
-rw-r----- 1 mysql mysql      8614 Apr 12 13:11 music_artists.frm
-rw-r----- 1 mysql mysql     46504 Apr 24 00:08 music_artists.MYD
-rw-r----- 1 mysql mysql     71680 Apr 24 00:08 music_artists.MYI
-rw-r----- 1 mysql mysql      8646 Apr 12 13:11 music_directories.frm
-rw-r----- 1 mysql mysql     28800 Apr 24 00:08 music_directories.MYD
-rw-r----- 1 mysql mysql      8192 Apr 24 00:08 music_directories.MYI
-rw-r----- 1 mysql mysql      8600 Apr 12 13:11 music_genres.frm
-rw-r----- 1 mysql mysql      2124 Apr 24 00:08 music_genres.MYD
-rw-r----- 1 mysql mysql      9216 Apr 24 00:08 music_genres.MYI
-rw-r----- 1 mysql mysql      8832 Apr 12 13:11 music_playlists.frm
-rw-r----- 1 mysql mysql    123404 Apr 24 00:08 music_playlists.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 music_playlists.MYI
-rw-r----- 1 mysql mysql     17246 Apr 24 00:08 music_radios.frm
-rw-r----- 1 mysql mysql    131072 Apr 24 00:08 music_radios.ibd
-rw-r----- 1 mysql mysql      8602 Apr 12 13:11 music_smartplaylist_categories.frm
-rw-r----- 1 mysql mysql        68 Apr 24 00:08 music_smartplaylist_categories.MYD
-rw-r----- 1 mysql mysql      5120 Apr 24 00:08 music_smartplaylist_categories.MYI
-rw-r----- 1 mysql mysql      8780 Apr 12 13:11 music_smartplaylist_items.frm
-rw-r----- 1 mysql mysql       360 Apr 24 00:08 music_smartplaylist_items.MYD
-rw-r----- 1 mysql mysql      3072 Apr 24 00:08 music_smartplaylist_items.MYI
-rw-r----- 1 mysql mysql      8776 Apr 12 13:11 music_smartplaylists.frm
-rw-r----- 1 mysql mysql       344 Apr 24 00:08 music_smartplaylists.MYD
-rw-r----- 1 mysql mysql      6144 Apr 24 00:08 music_smartplaylists.MYI
-rw-r----- 1 mysql mysql     13876 Apr 12 18:56 music_songs.frm
-rw-r----- 1 mysql mysql    807212 Apr 24 00:08 music_songs.MYD
-rw-r----- 1 mysql mysql    488448 Apr 24 00:08 music_songs.MYI
-rw-r----- 1 mysql mysql      8782 Apr 12 13:11 music_stats.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 music_stats.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 music_stats.MYI
-rw-r----- 1 mysql mysql     17212 Apr 24 00:08 music_streams.frm
-rw-r----- 1 mysql mysql    163840 Apr 24 00:08 music_streams.ibd
-rw-r----- 1 mysql mysql      8852 Apr 12 13:11 mythexport.frm
-rw-r----- 1 mysql mysql      8662 Apr 24 00:08 mythexport_job_queue.frm
-rw-r----- 1 mysql mysql     98304 Apr 24 00:08 mythexport_job_queue.ibd
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 mythexport.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 mythexport.MYI
-rw-r----- 1 mysql mysql     57970 Apr 12 13:11 mythlog.frm
-rw-r----- 1 mysql mysql     70528 Apr 24 00:08 mythlog.MYD
-rw-r----- 1 mysql mysql     11264 Apr 24 00:08 mythlog.MYI
-rw-r----- 1 mysql mysql      8624 Apr 12 13:11 mythweb_sessions.frm
-rw-r----- 1 mysql mysql     91812 Apr 24 11:56 mythweb_sessions.MYD
-rw-r----- 1 mysql mysql      5120 Apr 24 15:05 mythweb_sessions.MYI
-rw-r----- 1 mysql mysql      8620 Apr 12 13:11 networkiconmap.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 networkiconmap.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 networkiconmap.MYI
-rw-r----- 1 mysql mysql      8726 Apr 12 13:11 newssites.frm
-rw-r----- 1 mysql mysql       916 Apr 24 00:08 newssites.MYD
-rw-r----- 1 mysql mysql      4096 Apr 24 00:08 newssites.MYI
-rw-r----- 1 mysql mysql      8602 Apr 12 13:11 oldfind.frm
-rw-r----- 1 mysql mysql        18 Apr 24 00:08 oldfind.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 oldfind.MYI
-rw-r----- 1 mysql mysql      8604 Apr 12 13:11 oldprogram.frm
-rw-r----- 1 mysql mysql    854304 Apr 24 01:14 oldprogram.MYD
-rw-r----- 1 mysql mysql    815104 Apr 24 15:05 oldprogram.MYI
-rw-r----- 1 mysql mysql     62608 Apr 12 13:11 oldrecorded.frm
-rw-r----- 1 mysql mysql   4554792 Apr 24 14:22 oldrecorded.MYD
-rw-r----- 1 mysql mysql   5183488 Apr 24 15:05 oldrecorded.MYI
-rw-r----- 1 mysql mysql      8594 Apr 12 13:11 people.frm
-rw-r----- 1 mysql mysql    120312 Apr 24 00:08 people.MYD
-rw-r----- 1 mysql mysql    153600 Apr 24 00:08 people.MYI
-rw-r----- 1 mysql mysql      8802 Apr 12 13:11 phonecallhistory.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 phonecallhistory.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 phonecallhistory.MYI
-rw-r----- 1 mysql mysql      8864 Apr 12 13:11 phonedirectory.frm
-rw-r----- 1 mysql mysql        60 Apr 24 00:08 phonedirectory.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 phonedirectory.MYI
-rw-r----- 1 mysql mysql      8628 Apr 12 13:11 pidcache.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 pidcache.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 pidcache.MYI
-rw-r----- 1 mysql mysql      8754 Apr 12 13:11 playgroup.frm
-rw-r----- 1 mysql mysql        28 Apr 24 00:08 playgroup.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:08 playgroup.MYI
-rw-r----- 1 mysql mysql     53722 Apr 12 13:11 powerpriority.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 powerpriority.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 powerpriority.MYI
-rw-r----- 1 mysql mysql      8704 Apr 12 13:11 profilegroups.frm
-rw-r----- 1 mysql mysql       760 Apr 24 00:08 profilegroups.MYD
-rw-r----- 1 mysql mysql      9216 Apr 24 00:08 profilegroups.MYI
-rw-r----- 1 mysql mysql     63393 Apr 24 00:10 program.frm
-rw-r----- 1 mysql mysql      8676 Apr 12 13:11 programgenres.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 programgenres.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 programgenres.MYI
-rw-r----- 1 mysql mysql  28066152 Apr 24 15:01 program.MYD
-rw-r----- 1 mysql mysql  20617216 Apr 24 15:05 program.MYI
-rw-r----- 1 mysql mysql      8672 Apr 12 13:11 programrating.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 programrating.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 programrating.MYI
-rw-r----- 1 mysql mysql      8606 Apr 12 13:11 recgrouppassword.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 recgrouppassword.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:08 recgrouppassword.MYI
-rw-r----- 1 mysql mysql      8728 Apr 12 13:22 recgroups.frm
-rw-r----- 1 mysql mysql       140 Apr 24 00:08 recgroups.MYD
-rw-r----- 1 mysql mysql      3072 Apr 24 00:08 recgroups.MYI
-rw-r----- 1 mysql mysql      8736 Apr 12 13:11 recordedartwork.frm
-rw-r----- 1 mysql mysql    220208 Apr 24 14:15 recordedartwork.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 15:05 recordedartwork.MYI
-rw-r----- 1 mysql mysql      8772 Apr 12 13:11 recordedcredits.frm
-rw-r----- 1 mysql mysql      6540 Apr 24 00:08 recordedcredits.MYD
-rw-r----- 1 mysql mysql     17408 Apr 24 00:08 recordedcredits.MYI
-rw-r----- 1 mysql mysql     13572 Apr 12 13:22 recordedfile.frm
-rw-r----- 1 mysql mysql    129688 Apr 24 14:22 recordedfile.MYD
-rw-r----- 1 mysql mysql     75776 Apr 24 15:05 recordedfile.MYI
-rw-r----- 1 mysql mysql     63628 Apr 12 13:22 recorded.frm
-rw-r----- 1 mysql mysql      8694 Apr 12 13:11 recordedmarkup.frm
-rw-r----- 1 mysql mysql    332172 Apr 24 14:22 recordedmarkup.MYD
-rw-r----- 1 mysql mysql    369664 Apr 24 15:05 recordedmarkup.MYI
-rw-r----- 1 mysql mysql    619296 Apr 24 14:22 recorded.MYD
-rw-r----- 1 mysql mysql    196608 Apr 24 15:05 recorded.MYI
-rw-r----- 1 mysql mysql     59314 Apr 12 13:22 recordedprogram.frm
-rw-r----- 1 mysql mysql    412552 Apr 24 14:22 recordedprogram.MYD
-rw-r----- 1 mysql mysql    147456 Apr 24 15:05 recordedprogram.MYI
-rw-r----- 1 mysql mysql      8672 Apr 12 13:11 recordedrating.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:08 recordedrating.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 12:58 recordedrating.MYI
-rw-r----- 1 mysql mysql      8698 Apr 24 00:09 recordedseek.frm
-rw-r----- 1 mysql mysql 396748484 Apr 24 14:22 recordedseek.MYD
-rw-r----- 1 mysql mysql 385787904 Apr 24 15:05 recordedseek.MYI
-rw-r----- 1 mysql mysql      8696 Apr 12 13:15 recordfilter.frm
-rw-r----- 1 mysql mysql      1252 Apr 24 00:09 recordfilter.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 recordfilter.MYI
-rw-r----- 1 mysql mysql     63858 Apr 12 13:22 record.frm
-rw-r----- 1 mysql mysql      8716 Apr 12 13:15 recordingprofiles.frm
-rw-r----- 1 mysql mysql      1920 Apr 24 00:09 recordingprofiles.MYD
-rw-r----- 1 mysql mysql      3072 Apr 24 00:09 recordingprofiles.MYI
-rw-r----- 1 mysql mysql      8906 Apr 12 13:15 recordmatch.frm
-rw-r----- 1 mysql mysql     23983 Apr 24 15:01 recordmatch.MYD
-rw-r----- 1 mysql mysql     53248 Apr 24 15:05 recordmatch.MYI
-rw-r----- 1 mysql mysql    372880 Apr 24 12:58 record.MYD
-rw-r----- 1 mysql mysql    174080 Apr 24 15:05 record.MYI
-rw-r----- 1 mysql mysql     59720 Apr 24 00:08 record_tmp.frm
-rw-r----- 1 mysql mysql    507904 Apr 24 00:08 record_tmp.ibd
-rw-r----- 1 mysql mysql     13098 Apr 12 13:15 romdb.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 romdb.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 romdb.MYI
-rw-r----- 1 mysql mysql      8672 Apr 12 13:15 scannerfile.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 scannerfile.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 scannerfile.MYI
-rw-r----- 1 mysql mysql      8686 Apr 12 13:15 scannerpath.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 scannerpath.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 scannerpath.MYI
-rw-r----- 1 mysql mysql      8572 Apr 12 13:15 schemalock.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 schemalock.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 schemalock.MYI
-rw-r----- 1 mysql mysql     53686 Apr 12 13:15 settings.frm
-rw-r----- 1 mysql mysql    181548 Apr 24 14:56 settings.MYD
-rw-r----- 1 mysql mysql     93184 Apr 24 15:05 settings.MYI
-rw-r----- 1 mysql mysql      8670 Apr 12 13:15 storagegroup.frm
-rw-r----- 1 mysql mysql      1272 Apr 24 00:09 storagegroup.MYD
-rw-r----- 1 mysql mysql     10240 Apr 24 00:09 storagegroup.MYI
-rw-r----- 1 mysql mysql      8758 Apr 24 00:09 suggested.frm
-rw-r----- 1 mysql mysql    114688 Apr 24 00:09 suggested.ibd
-rw-r----- 1 mysql mysql      8950 Apr 12 13:15 tvchain.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 tvchain.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 tvchain.MYI
-rw-r----- 1 mysql mysql      8750 Apr 12 13:15 tvosdmenu.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 tvosdmenu.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 tvosdmenu.MYI
-rw-r----- 1 mysql mysql     12962 Apr 12 13:15 upnpmedia.frm
-rw-r----- 1 mysql mysql   1341148 Apr 24 00:09 upnpmedia.MYD
-rw-r----- 1 mysql mysql    830464 Apr 24 00:09 upnpmedia.MYI
-rw-r----- 1 mysql mysql      8606 Apr 12 13:22 user_permissions.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 user_permissions.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 user_permissions.MYI
-rw-r----- 1 mysql mysql      8758 Apr 12 13:22 user_sessions.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 user_sessions.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 user_sessions.MYI
-rw-r----- 1 mysql mysql      8694 Apr 12 13:22 users.frm
-rw-r----- 1 mysql mysql        52 Apr 24 00:09 users.MYD
-rw-r----- 1 mysql mysql      5120 Apr 24 00:09 users.MYI
-rw-r----- 1 mysql mysql      8592 Apr 12 13:15 videocast.frm
-rw-r----- 1 mysql mysql    215436 Apr 24 00:09 videocast.MYD
-rw-r----- 1 mysql mysql     95232 Apr 24 00:09 videocast.MYI
-rw-r----- 1 mysql mysql      8600 Apr 12 13:15 videocategory.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 videocategory.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 videocategory.MYI
-rw-r----- 1 mysql mysql      9214 Apr 12 13:15 videocollection.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 videocollection.MYD
-rw-r----- 1 mysql mysql      4096 Apr 24 00:09 videocollection.MYI
-rw-r----- 1 mysql mysql      8598 Apr 12 13:15 videocountry.frm
-rw-r----- 1 mysql mysql       936 Apr 24 00:09 videocountry.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 videocountry.MYI
-rw-r----- 1 mysql mysql      8594 Apr 12 13:15 videogenre.frm
-rw-r----- 1 mysql mysql       776 Apr 24 00:09 videogenre.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 videogenre.MYI
-rw-r----- 1 mysql mysql      8600 Apr 12 13:15 videometadatacast.frm
-rw-r----- 1 mysql mysql     58482 Apr 24 00:09 videometadatacast.MYD
-rw-r----- 1 mysql mysql     96256 Apr 24 00:09 videometadatacast.MYI
-rw-r----- 1 mysql mysql      8606 Apr 12 13:15 videometadatacountry.frm
-rw-r----- 1 mysql mysql      2385 Apr 24 00:09 videometadatacountry.MYD
-rw-r----- 1 mysql mysql     14336 Apr 24 00:09 videometadatacountry.MYI
-rw-r----- 1 mysql mysql     14014 Apr 12 13:15 videometadata.frm
-rw-r----- 1 mysql mysql      8602 Apr 12 13:15 videometadatagenre.frm
-rw-r----- 1 mysql mysql      6300 Apr 24 00:09 videometadatagenre.MYD
-rw-r----- 1 mysql mysql     28672 Apr 24 00:09 videometadatagenre.MYI
-rw-r----- 1 mysql mysql    798620 Apr 24 00:09 videometadata.MYD
-rw-r----- 1 mysql mysql    136192 Apr 24 00:09 videometadata.MYI
-rw-r----- 1 mysql mysql      8632 Apr 12 13:15 videopart.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 videopart.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 videopart.MYI
-rw-r----- 1 mysql mysql      8766 Apr 12 13:15 videopathinfo.frm
-rw-r----- 1 mysql mysql         0 Apr 24 00:09 videopathinfo.MYD
-rw-r----- 1 mysql mysql      1024 Apr 24 00:09 videopathinfo.MYI
-rw-r----- 1 mysql mysql     21200 Apr 12 13:15 videosource.frm
-rw-r----- 1 mysql mysql        88 Apr 24 00:09 videosource.MYD
-rw-r----- 1 mysql mysql      5120 Apr 24 00:09 videosource.MYI
-rw-r----- 1 mysql mysql      8728 Apr 12 13:15 videotypes.frm
-rw-r----- 1 mysql mysql       708 Apr 24 00:09 videotypes.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 videotypes.MYI
-rw-r----- 1 mysql mysql      8758 Apr 24 00:09 weatherdatalayout.frm
-rw-r----- 1 mysql mysql    229376 Apr 24 00:09 weatherdatalayout.ibd
-rw-r----- 1 mysql mysql      8720 Apr 24 00:09 weatherscreens.frm
-rw-r----- 1 mysql mysql     98304 Apr 24 00:09 weatherscreens.ibd
-rw-r----- 1 mysql mysql      8954 Apr 24 00:09 weathersourcesettings.frm
-rw-r----- 1 mysql mysql    131072 Apr 24 00:09 weathersourcesettings.ibd
-rw-r----- 1 mysql mysql      8652 Apr 12 13:15 websites.frm
-rw-r----- 1 mysql mysql        40 Apr 24 00:09 websites.MYD
-rw-r----- 1 mysql mysql      2048 Apr 24 00:09 websites.MYI

/var/lib/mysql/performance_schema:
total 1060
-rw-r----- 1 mysql mysql  8706 Apr 10 15:04 accounts.frm
-rw-r----- 1 mysql mysql  8624 Apr 10 15:04 cond_instances.frm
-rw-r----- 1 mysql mysql    61 Apr 10 15:04 db.opt
-rw-r----- 1 mysql mysql  9103 Apr 10 15:04 events_stages_current.frm
-rw-r----- 1 mysql mysql  9103 Apr 10 15:04 events_stages_history.frm
-rw-r----- 1 mysql mysql  9103 Apr 10 15:04 events_stages_history_long.frm
-rw-r----- 1 mysql mysql  8874 Apr 10 15:04 events_stages_summary_by_account_by_event_name.frm
-rw-r----- 1 mysql mysql  8844 Apr 10 15:04 events_stages_summary_by_host_by_event_name.frm
-rw-r----- 1 mysql mysql  8854 Apr 10 15:04 events_stages_summary_by_thread_by_event_name.frm
-rw-r----- 1 mysql mysql  8844 Apr 10 15:04 events_stages_summary_by_user_by_event_name.frm
-rw-r----- 1 mysql mysql  8814 Apr 10 15:04 events_stages_summary_global_by_event_name.frm
-rw-r----- 1 mysql mysql 10597 Apr 10 15:04 events_statements_current.frm
-rw-r----- 1 mysql mysql 10597 Apr 10 15:04 events_statements_history.frm
-rw-r----- 1 mysql mysql 10597 Apr 10 15:04 events_statements_history_long.frm
-rw-r----- 1 mysql mysql 10000 Apr 10 15:04 events_statements_summary_by_account_by_event_name.frm
-rw-r----- 1 mysql mysql 10102 Apr 10 15:04 events_statements_summary_by_digest.frm
-rw-r----- 1 mysql mysql  9970 Apr 10 15:04 events_statements_summary_by_host_by_event_name.frm
-rw-r----- 1 mysql mysql 10369 Apr 10 15:04 events_statements_summary_by_program.frm
-rw-r----- 1 mysql mysql  9980 Apr 10 15:04 events_statements_summary_by_thread_by_event_name.frm
-rw-r----- 1 mysql mysql  9970 Apr 10 15:04 events_statements_summary_by_user_by_event_name.frm
-rw-r----- 1 mysql mysql  9940 Apr 10 15:04 events_statements_summary_global_by_event_name.frm
-rw-r----- 1 mysql mysql  9800 Apr 10 15:04 events_transactions_current.frm
-rw-r----- 1 mysql mysql  9800 Apr 10 15:04 events_transactions_history.frm
-rw-r----- 1 mysql mysql  9800 Apr 10 15:04 events_transactions_history_long.frm
-rw-r----- 1 mysql mysql  9468 Apr 10 15:04 events_transactions_summary_by_account_by_event_name.frm
-rw-r----- 1 mysql mysql  9438 Apr 10 15:04 events_transactions_summary_by_host_by_event_name.frm
-rw-r----- 1 mysql mysql  9448 Apr 10 15:04 events_transactions_summary_by_thread_by_event_name.frm
-rw-r----- 1 mysql mysql  9438 Apr 10 15:04 events_transactions_summary_by_user_by_event_name.frm
-rw-r----- 1 mysql mysql  9408 Apr 10 15:04 events_transactions_summary_global_by_event_name.frm
-rw-r----- 1 mysql mysql  9401 Apr 10 15:04 events_waits_current.frm
-rw-r----- 1 mysql mysql  9401 Apr 10 15:04 events_waits_history.frm
-rw-r----- 1 mysql mysql  9401 Apr 10 15:04 events_waits_history_long.frm
-rw-r----- 1 mysql mysql  8874 Apr 10 15:04 events_waits_summary_by_account_by_event_name.frm
-rw-r----- 1 mysql mysql  8844 Apr 10 15:04 events_waits_summary_by_host_by_event_name.frm
-rw-r----- 1 mysql mysql  8878 Apr 10 15:04 events_waits_summary_by_instance.frm
-rw-r----- 1 mysql mysql  8854 Apr 10 15:04 events_waits_summary_by_thread_by_event_name.frm
-rw-r----- 1 mysql mysql  8844 Apr 10 15:04 events_waits_summary_by_user_by_event_name.frm
-rw-r----- 1 mysql mysql  8814 Apr 10 15:04 events_waits_summary_global_by_event_name.frm
-rw-r----- 1 mysql mysql  8654 Apr 10 15:04 file_instances.frm
-rw-r----- 1 mysql mysql  9740 Apr 10 15:04 file_summary_by_event_name.frm
-rw-r----- 1 mysql mysql  9844 Apr 10 15:04 file_summary_by_instance.frm
-rw-r----- 1 mysql mysql  8628 Apr 10 15:04 global_status.frm
-rw-r----- 1 mysql mysql  8628 Apr 10 15:04 global_variables.frm
-rw-r----- 1 mysql mysql 10483 Apr 10 15:04 host_cache.frm
-rw-r----- 1 mysql mysql  8676 Apr 10 15:04 hosts.frm
-rw-r----- 1 mysql mysql  9240 Apr 10 15:04 memory_summary_by_account_by_event_name.frm
-rw-r----- 1 mysql mysql  9210 Apr 10 15:04 memory_summary_by_host_by_event_name.frm
-rw-r----- 1 mysql mysql  9220 Apr 10 15:04 memory_summary_by_thread_by_event_name.frm
-rw-r----- 1 mysql mysql  9210 Apr 10 15:04 memory_summary_by_user_by_event_name.frm
-rw-r----- 1 mysql mysql  9180 Apr 10 15:04 memory_summary_global_by_event_name.frm
-rw-r----- 1 mysql mysql  8998 Apr 10 15:04 metadata_locks.frm
-rw-r----- 1 mysql mysql  8684 Apr 10 15:04 mutex_instances.frm
-rw-r----- 1 mysql mysql  8908 Apr 10 15:04 objects_summary_global_by_type.frm
-rw-r----- 1 mysql mysql  8776 Apr 10 15:04 performance_timers.frm
-rw-r----- 1 mysql mysql 10541 Apr 10 15:04 prepared_statements_instances.frm
-rw-r----- 1 mysql mysql  8624 Apr 10 15:04 replication_applier_configuration.frm
-rw-r----- 1 mysql mysql  8849 Apr 10 15:04 replication_applier_status_by_coordinator.frm
-rw-r----- 1 mysql mysql  8953 Apr 10 15:04 replication_applier_status_by_worker.frm
-rw-r----- 1 mysql mysql  8759 Apr 10 15:04 replication_applier_status.frm
-rw-r----- 1 mysql mysql 17724 Apr 10 15:04 replication_connection_configuration.frm
-rw-r----- 1 mysql mysql  9215 Apr 10 15:04 replication_connection_status.frm
-rw-r----- 1 mysql mysql  8750 Apr 10 15:04 replication_group_members.frm
-rw-r----- 1 mysql mysql  9134 Apr 10 15:04 replication_group_member_stats.frm
-rw-r----- 1 mysql mysql  8758 Apr 10 15:04 rwlock_instances.frm
-rw-r----- 1 mysql mysql  8716 Apr 10 15:04 session_account_connect_attrs.frm
-rw-r----- 1 mysql mysql  8716 Apr 10 15:04 session_connect_attrs.frm
-rw-r----- 1 mysql mysql  8628 Apr 10 15:04 session_status.frm
-rw-r----- 1 mysql mysql  8628 Apr 10 15:04 session_variables.frm
-rw-r----- 1 mysql mysql  8701 Apr 10 15:04 setup_actors.frm
-rw-r----- 1 mysql mysql  8605 Apr 10 15:04 setup_consumers.frm
-rw-r----- 1 mysql mysql  8637 Apr 10 15:04 setup_instruments.frm
-rw-r----- 1 mysql mysql  8784 Apr 10 15:04 setup_objects.frm
-rw-r----- 1 mysql mysql  8650 Apr 10 15:04 setup_timers.frm
-rw-r----- 1 mysql mysql  8818 Apr 10 15:04 socket_instances.frm
-rw-r----- 1 mysql mysql  9740 Apr 10 15:04 socket_summary_by_event_name.frm
-rw-r----- 1 mysql mysql  9804 Apr 10 15:04 socket_summary_by_instance.frm
-rw-r----- 1 mysql mysql  8688 Apr 10 15:04 status_by_account.frm
-rw-r----- 1 mysql mysql  8658 Apr 10 15:04 status_by_host.frm
-rw-r----- 1 mysql mysql  8668 Apr 10 15:04 status_by_thread.frm
-rw-r----- 1 mysql mysql  8658 Apr 10 15:04 status_by_user.frm
-rw-r----- 1 mysql mysql  8928 Apr 10 15:04 table_handles.frm
-rw-r----- 1 mysql mysql 10578 Apr 10 15:04 table_io_waits_summary_by_index_usage.frm
-rw-r----- 1 mysql mysql 10488 Apr 10 15:04 table_io_waits_summary_by_table.frm
-rw-r----- 1 mysql mysql 13186 Apr 10 15:04 table_lock_waits_summary_by_table.frm
-rw-r----- 1 mysql mysql  9335 Apr 10 15:04 threads.frm
-rw-r----- 1 mysql mysql  8676 Apr 10 15:04 users.frm
-rw-r----- 1 mysql mysql  8668 Apr 10 15:04 user_variables_by_thread.frm
-rw-r----- 1 mysql mysql  8668 Apr 10 15:04 variables_by_thread.frm

/var/lib/mysql/sys:
total 664
-rw-r----- 1 mysql mysql    61 Jul 31  2018 db.opt
-rw-r----- 1 mysql mysql  2343 Jul 31  2018 host_summary_by_file_io.frm
-rw-r----- 1 mysql mysql  2976 Jul 31  2018 host_summary_by_file_io_type.frm
-rw-r----- 1 mysql mysql  2758 Jul 31  2018 host_summary_by_stages.frm
-rw-r----- 1 mysql mysql  4100 Jul 31  2018 host_summary_by_statement_latency.frm
-rw-r----- 1 mysql mysql  4459 Jul 31  2018 host_summary_by_statement_type.frm
-rw-r----- 1 mysql mysql  4005 Jul 31  2018 host_summary.frm
-rw-r----- 1 mysql mysql  2492 Jul 31  2018 innodb_buffer_stats_by_schema.frm
-rw-r----- 1 mysql mysql  2782 Jul 31  2018 innodb_buffer_stats_by_table.frm
-rw-r----- 1 mysql mysql  5264 Jul 31  2018 innodb_lock_waits.frm
-rw-r----- 1 mysql mysql  4390 Jul 31  2018 io_by_thread_by_latency.frm
-rw-r----- 1 mysql mysql  4169 Jul 31  2018 io_global_by_file_by_bytes.frm
-rw-r----- 1 mysql mysql  2561 Jul 31  2018 io_global_by_file_by_latency.frm
-rw-r----- 1 mysql mysql  5166 Jul 31  2018 io_global_by_wait_by_bytes.frm
-rw-r----- 1 mysql mysql  4983 Jul 31  2018 io_global_by_wait_by_latency.frm
-rw-r----- 1 mysql mysql  3441 Jul 31  2018 latest_file_io.frm
-rw-r----- 1 mysql mysql  3475 Jul 31  2018 memory_by_host_by_current_bytes.frm
-rw-r----- 1 mysql mysql  3214 Jul 31  2018 memory_by_thread_by_current_bytes.frm
-rw-r----- 1 mysql mysql  3475 Jul 31  2018 memory_by_user_by_current_bytes.frm
-rw-r----- 1 mysql mysql  3405 Jul 31  2018 memory_global_by_current_bytes.frm
-rw-r----- 1 mysql mysql   827 Jul 31  2018 memory_global_total.frm
-rw-r----- 1 mysql mysql 10208 Jul 31  2018 metrics.frm
-rw-r----- 1 mysql mysql  8183 Jul 31  2018 processlist.frm
-rw-r----- 1 mysql mysql  1093 Jul 31  2018 ps_check_lost_instrumentation.frm
-rw-r----- 1 mysql mysql  6163 Jul 31  2018 schema_auto_increment_columns.frm
-rw-r----- 1 mysql mysql  3606 Jul 31  2018 schema_index_statistics.frm
-rw-r----- 1 mysql mysql  3725 Jul 31  2018 schema_object_overview.frm
-rw-r----- 1 mysql mysql  5226 Jul 31  2018 schema_redundant_indexes.frm
-rw-r----- 1 mysql mysql  5103 Jul 31  2018 schema_table_lock_waits.frm
-rw-r----- 1 mysql mysql  3987 Jul 31  2018 schema_table_statistics.frm
-rw-r----- 1 mysql mysql  5400 Jul 31  2018 schema_table_statistics_with_buffer.frm
-rw-r----- 1 mysql mysql  1982 Jul 31  2018 schema_tables_with_full_table_scans.frm
-rw-r----- 1 mysql mysql  2294 Jul 31  2018 schema_unused_indexes.frm
-rw-r----- 1 mysql mysql  3044 Jul 31  2018 session.frm
-rw-r----- 1 mysql mysql  2034 Jul 31  2018 session_ssl_status.frm
-rw-r----- 1 mysql mysql  7048 Jul 31  2018 statement_analysis.frm
-rw-r----- 1 mysql mysql  3758 Jul 31  2018 statements_with_errors_or_warnings.frm
-rw-r----- 1 mysql mysql  5656 Jul 31  2018 statements_with_full_table_scans.frm
-rw-r----- 1 mysql mysql  3479 Jul 31  2018 statements_with_runtimes_in_95th_percentile.frm
-rw-r----- 1 mysql mysql  4305 Jul 31  2018 statements_with_sorting.frm
-rw-r----- 1 mysql mysql  4325 Jul 31  2018 statements_with_temp_tables.frm
-rw-r----- 1 mysql mysql  8672 Jul 31  2018 sys_config.frm
-rw-r----- 1 mysql mysql 98304 Jul 31  2018 sys_config.ibd
-rw-r----- 1 mysql mysql    42 Jul 31  2018 sys_config_insert_set_user.TRN
-rw-r----- 1 mysql mysql   720 Jul 31  2018 sys_config.TRG
-rw-r----- 1 mysql mysql    42 Jul 31  2018 sys_config_update_set_user.TRN
-rw-r----- 1 mysql mysql  2343 Jul 31  2018 user_summary_by_file_io.frm
-rw-r----- 1 mysql mysql  2924 Jul 31  2018 user_summary_by_file_io_type.frm
-rw-r----- 1 mysql mysql  2725 Jul 31  2018 user_summary_by_stages.frm
-rw-r----- 1 mysql mysql  4100 Jul 31  2018 user_summary_by_statement_latency.frm
-rw-r----- 1 mysql mysql  4425 Jul 31  2018 user_summary_by_statement_type.frm
-rw-r----- 1 mysql mysql  4697 Jul 31  2018 user_summary.frm
-rw-r----- 1 mysql mysql   461 Jul 31  2018 version.frm
-rw-r----- 1 mysql mysql  3580 Jul 31  2018 wait_classes_global_by_avg_latency.frm
-rw-r----- 1 mysql mysql  3420 Jul 31  2018 wait_classes_global_by_latency.frm
-rw-r----- 1 mysql mysql  3210 Jul 31  2018 waits_by_host_by_latency.frm
-rw-r----- 1 mysql mysql  3413 Jul 31  2018 waits_by_user_by_latency.frm
-rw-r----- 1 mysql mysql  2427 Jul 31  2018 waits_global_by_latency.frm
-rw-r----- 1 mysql mysql  2284 Jul 31  2018 [email]x@0024host_summary_by_file_io.frm[/email]
-rw-r----- 1 mysql mysql  2858 Jul 31  2018 [email]x@0024host_summary_by_file_io_type.frm[/email]
-rw-r----- 1 mysql mysql  2640 Jul 31  2018 [email]x@0024host_summary_by_stages.frm[/email]
-rw-r----- 1 mysql mysql  3923 Jul 31  2018 [email]x@0024host_summary_by_statement_latency.frm[/email]
-rw-r----- 1 mysql mysql  4282 Jul 31  2018 [email]x@0024host_summary_by_statement_type.frm[/email]
-rw-r----- 1 mysql mysql  3651 Jul 31  2018 [email]x@0024host_summary.frm[/email]
-rw-r----- 1 mysql mysql  2430 Jul 31  2018 [email]x@0024innodb_buffer_stats_by_schema.frm[/email]
-rw-r----- 1 mysql mysql  2720 Jul 31  2018 [email]x@0024innodb_buffer_stats_by_table.frm[/email]
-rw-r----- 1 mysql mysql  5116 Jul 31  2018 [email]x@0024innodb_lock_waits.frm[/email]
-rw-r----- 1 mysql mysql  4154 Jul 31  2018 [email]x@0024io_by_thread_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  3800 Jul 31  2018 [email]x@0024io_global_by_file_by_bytes.frm[/email]
-rw-r----- 1 mysql mysql  2266 Jul 31  2018 [email]x@0024io_global_by_file_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  4623 Jul 31  2018 [email]x@0024io_global_by_wait_by_bytes.frm[/email]
-rw-r----- 1 mysql mysql  4381 Jul 31  2018 [email]x@0024io_global_by_wait_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  3261 Jul 31  2018 [email]x@0024latest_file_io.frm[/email]
-rw-r----- 1 mysql mysql  3227 Jul 31  2018 [email]x@0024memory_by_host_by_current_bytes.frm[/email]
-rw-r----- 1 mysql mysql  2967 Jul 31  2018 [email]x@0024memory_by_thread_by_current_bytes.frm[/email]
-rw-r----- 1 mysql mysql  3227 Jul 31  2018 [email]x@0024memory_by_user_by_current_bytes.frm[/email]
-rw-r----- 1 mysql mysql  3157 Jul 31  2018 [email]x@0024memory_global_by_current_bytes.frm[/email]
-rw-r----- 1 mysql mysql   765 Jul 31  2018 [email]x@0024memory_global_total.frm[/email]
-rw-r----- 1 mysql mysql  7679 Jul 31  2018 [email]x@0024processlist.frm[/email]
-rw-r----- 1 mysql mysql  1747 Jul 31  2018 [email]x@0024ps_digest_95th_percentile_by_avg_us.frm[/email]
-rw-r----- 1 mysql mysql   844 Jul 31  2018 [email]x@0024ps_digest_avg_latency_distribution.frm[/email]
-rw-r----- 1 mysql mysql  2926 Jul 31  2018 [email]x@0024ps_schema_table_statistics_io.frm[/email]
-rw-r----- 1 mysql mysql  2469 Jul 31  2018 [email]x@0024schema_flattened_keys.frm[/email]
-rw-r----- 1 mysql mysql  3370 Jul 31  2018 [email]x@0024schema_index_statistics.frm[/email]
-rw-r----- 1 mysql mysql  5029 Jul 31  2018 [email]x@0024schema_table_lock_waits.frm[/email]
-rw-r----- 1 mysql mysql  3391 Jul 31  2018 [email]x@0024schema_table_statistics.frm[/email]
-rw-r----- 1 mysql mysql  4679 Jul 31  2018 [email]x@0024schema_table_statistics_with_buffer.frm[/email]
-rw-r----- 1 mysql mysql  1923 Jul 31  2018 [email]x@0024schema_tables_with_full_table_scans.frm[/email]
-rw-r----- 1 mysql mysql  3170 Jul 31  2018 [email]x@0024session.frm[/email]
-rw-r----- 1 mysql mysql  6738 Jul 31  2018 [email]x@0024statement_analysis.frm[/email]
-rw-r----- 1 mysql mysql  3684 Jul 31  2018 [email]x@0024statements_with_errors_or_warnings.frm[/email]
-rw-r----- 1 mysql mysql  5481 Jul 31  2018 [email]x@0024statements_with_full_table_scans.frm[/email]
-rw-r----- 1 mysql mysql  3228 Jul 31  2018 [email]x@0024statements_with_runtimes_in_95th_percentile.frm[/email]
-rw-r----- 1 mysql mysql  4172 Jul 31  2018 [email]x@0024statements_with_sorting.frm[/email]
-rw-r----- 1 mysql mysql  4192 Jul 31  2018 [email]x@0024statements_with_temp_tables.frm[/email]
-rw-r----- 1 mysql mysql  2284 Jul 31  2018 [email]x@0024user_summary_by_file_io.frm[/email]
-rw-r----- 1 mysql mysql  2806 Jul 31  2018 [email]x@0024user_summary_by_file_io_type.frm[/email]
-rw-r----- 1 mysql mysql  2607 Jul 31  2018 [email]x@0024user_summary_by_stages.frm[/email]
-rw-r----- 1 mysql mysql  3923 Jul 31  2018 [email]x@0024user_summary_by_statement_latency.frm[/email]
-rw-r----- 1 mysql mysql  4248 Jul 31  2018 [email]x@0024user_summary_by_statement_type.frm[/email]
-rw-r----- 1 mysql mysql  4396 Jul 31  2018 [email]x@0024user_summary.frm[/email]
-rw-r----- 1 mysql mysql  3236 Jul 31  2018 [email]x@0024wait_classes_global_by_avg_latency.frm[/email]
-rw-r----- 1 mysql mysql  3187 Jul 31  2018 [email]x@0024wait_classes_global_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  3033 Jul 31  2018 [email]x@0024waits_by_host_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  3236 Jul 31  2018 [email]x@0024waits_by_user_by_latency.frm[/email]
-rw-r----- 1 mysql mysql  2250 Jul 31  2018 [email]x@0024waits_global_by_latency.frm[/email]

---

### Post by #&amp;thj^% on 2019-04-24
Code Tags Please.

---

### Post by SeijiSensei on 2019-04-24
Well, that's not the problem then.  Next step is to look at /var/lib/mysql/error.log and see if shows anything awry.  Here's mine from starting a fresh installation:

```

2019-04-24T19:11:06.706210Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.25-1) starting as process 8888 ...
[stuff]
2019-04-24T19:11:06.712159Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2019-04-24T19:11:06.719131Z 0 [Note] InnoDB: Completed initialization of buffer pool
[stuff]
2019-04-24T19:11:06.720798Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2019-04-24T19:11:06.733600Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
2019-04-24T19:11:06.749428Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2019-04-24T19:11:06.749565Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2019-04-24T19:11:06.785206Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
[stuff]
2019-04-24T19:11:06.787351Z 0 [Note] InnoDB: 5.7.25 started; log sequence number 2524888
[stuff]
2019-04-24T19:11:06.794623Z 0 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
2019-04-24T19:11:06.794646Z 0 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
2019-04-24T19:11:06.794819Z 0 [Note] Server socket created on IP: '127.0.0.1'.
2019-04-24T19:11:06.804687Z 0 [Note] Event Scheduler: Loaded 0 events
2019-04-24T19:11:06.804897Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.25-1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```
Building the initial ibtmp file took a lot longer than I would have expected for 12 MB. Here it already exists.

---

### Post by drifting on 2019-04-24
Opps, ignorance on my part. Sorry.

And I have no logfile in that location? 

Regards Paul.

---

### Post by drifting on 2019-04-24
A good friend remoted in and helped, he said he managed to solve it by doing this :-

Apr 24 21:46:57 MicroServer audit[6037]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=6037 comm="mys
Apr 24 21:46:57 MicroServer kernel: audit: type=1400 audit(1556138817.598:51): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/device
 
Did this:
Updated: /etc/apparmor.d/usr.sbin.mysqld
 
To allow App Armor to let MYSQL start:
 
/proc/*/status r,
/sys/devices/system/node/ r,
/sys/devices/system/node/node*/meminfo r,
/sys/devices/system/node/*/* r,
/sys/devices/system/node/* r,
}
 
Reload App armor config:

apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld
 
Then MYSQL gave this:
 
Apr 24 21:49:05 MicroServer mysql-systemd-start[6114]: ERROR: Unable to start MySQL server:
Apr 24 21:49:05 MicroServer mysql-systemd-start[6114]: 2019-04-24T20:49:05.617823Z 0 [ERROR] unknown variable 'table_cache=128'
Apr 24 21:49:05 MicroServer mysql-systemd-start[6114]: 2019-04-24T20:49:05.622209Z 0 [ERROR] Aborting
 
Updated:
 
/etc/mysql/conf.d/mythtv-tweaks.cnf
Commented out: table_cache  = 128
Added: table_open_cache = 128
 
As per: [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767)

---

