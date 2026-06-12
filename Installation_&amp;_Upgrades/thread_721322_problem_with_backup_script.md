---
title: "problem with backup script"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Nighthawk71 on 2008-03-11
I am in the process of migrating from Fedora to Ubuntu for all of our Linux desktops and servers.

The latest part of this migration was our primary backup server.  I replaced an old AMD Athlon XP 2500 box with a new Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz.  with 2GB of DDR2 667 memory and 4 500gb hard drives partitioned as follows:

/dev/sda1    /                        20gb
/dev/sda2    /backup/sda    457gb
/dev/sda3    swap                   4gb
/dev/sdb1    /                       481gb
/dev/sdc1    /                       481gb
/dev/sdd1    /                       481gb

The O/S is Kubuntu 7.10

the backup script is a perl script which I have written and updated over the last 4 years.  It runs nightly as a cron process.

Here is my root crontab file:
# m h  dom mon dow   command
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/gamesx
00 2 * * * set > /home/backup/set.txt
30 2 * * * /home/backup/backup.sh > /var/log/backuplog.log
02 7 * * * /home/backup/setdate.sh
03 7 * * * run-parts /etc/cron.daily

here is backup.sh:
#!/bin/sh
#
# Ensure that Drive Mounts are Still Active
#
umount -a -t nfs
/root/mountfiles.sh
date
/home/backup/scripts/backupstart.pl
/home/backup/scripts/shark/backupmcsepub.pl
/home/backup/scripts/penguin/backupdocs.pl
/home/backup/scripts/penguin/backuppretreat.pl
/home/backup/scripts/marlin/backup-posystem.pl
/home/backup/scripts/penguin/backupprojects.pl
/home/backup/scripts/whale/backuphome.pl
/home/backup/scripts/shark/backupgis.pl

date
/home/backup/scripts/copytohaddock.pl
/home/backup/scripts/backupfinish.pl
dmesg > /home/backup/log/dmesg.log
/home/backup/scripts/sendmessages.pl



If I run the /home/backup/backup.sh script manually, it works perfectly.  If I run it as a cron process, it runs until about 3:49 or so and then starts giving the following errors:

Creating /backup/sda/shark/gis/Friday1.tar.gz resulting in error code #0
Creating /backup/sda/shark/gis/Friday2.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday3.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday4.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday5.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday6.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday7.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday8.tar.gz resulting in error code #36096
Creating /backup/sda/shark/gis/Friday9.tar.gz resulting in error code #36096

Here is the section of perl code that is giving the problem

@files=("",
	"/export/backup/shark/gis/ac*",
        "/export/backup/shark/gis/av*",
        "/export/backup/shark/gis/ba*",
        "/export/backup/shark/gis/co*",
        "/export/backup/shark/gis/ht*",
        "/export/backup/shark/gis/m*",
        "/export/backup/shark/gis/n*",
        "/export/backup/shark/gis/s*",
        "/export/backup/shark/gis/u*");

$numfiles = 9;

#######################
# Create new archive1 #
#######################

$errors=0;
$pass=0;
while ($pass<$numfiles) {
   ++$pass;
   print "About To Create archive:  $newarchive[$pass] using filespec:  $files[$pass] \n";
   @error2 = system("tar zcvf $newarchive[$pass] $files[$pass]") or ++$errors;
#   print "$newarchive[$pass]  $files[$pass]";
   if ($errors = 0) {
      print LOG "$newarchive[$pass] successfully created \n";
      print LOG2 "$newarchive[$pass] successfully created \n";
      }
   else
   {
      foreach $line(@error2){
         print LOG "Creating $newarchive[$pass] resulting in error code #$line \n";
         print LOG2 "Creating $newarchive[$pass] resulting in error code #$line \n";
         }
   }
}

I have googled repeatedly on this and have not been about to find out what that error code represents.

Also, the backup runs perfectly fine on our fedora boxes running fedora 3, 4, 5, or 6.

Please, any help would be appreciated

Jon Shorie
Systems Administrator
Medina County Sanitary Engineers

---

### Post by Nighthawk71 on 2008-03-12
If there is a better forum where I can post this, please let me know.  This is still happening and I would appreciate any suggestions if possible.

Thank you

---

### Post by Nighthawk71 on 2008-03-13
Well, I found a fix for this problem.  Apparently, if you have a long cron process (> 1 hour or so) you need to have a mail server installed.  It does not have to be configured, just installed.

I found this on:
[http://ubuntuforums.org/showthread.php?t=526217](http://ubuntuforums.org/showthread.php?t=526217)

It is very strange.  After I did an:
apt-get install sendmail
the script worked properly.

Jon Shorie
Systems Administrator
Medina County Sanitary Engineers

---

