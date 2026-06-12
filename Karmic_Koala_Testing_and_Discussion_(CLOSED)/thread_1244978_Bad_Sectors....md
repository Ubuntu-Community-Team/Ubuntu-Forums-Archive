---
title: "Bad Sectors..."
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jonnydopemsr on 2009-08-20
okay so i wiped and installed 9.10 but even before that during the live cd it said my 1.5TB drive has bad sectors in it. but yet when i am in 9.04 live cd and just had it on my pc not more then 2 hours ago that never popped up.

can anyone tell me if its possible a bug in the alpha build or what? i know it is alpha and all but still thats my media drive and well backing it up right now is not possible...

thx in advance.

Jonny

---

### Post by steeleyuk on 2009-08-20
Same issue on my Raptor drive. Its the new Palimpsest app, theres another thread about it somewhere.

You could install smartctl and run checks on your drive using that, probably more reliable. Also, if you want to stop Palimpsest notifying your of errors/remove the icon from the notification area then you can uncheck System > Preferences > Startup Applications > Disk Notifications.

---

### Post by jonnydopemsr on 2009-08-20
Okay yea i finally started seeing others with this issue... i have a seagate 1.5TB one of the lucky ones that didnt have the bad firmware but yea i am thinking it has to be the app as well since seeing others, and u, having this issue as well... hopefully this will be fix by the final...

---

### Post by Seventh Reign on 2009-08-21
Its a bug in Palimpsest, not in Ubuntu.  That same program shows the same errors in every single distro its install on.

---

### Post by jaakan on 2009-08-21
> **jonnydopemsr said:**
> okay so i wiped and installed 9.10 but even before that during the live cd it said my 1.5TB drive has bad sectors in it. but yet when i am in 9.04 live cd and just had it on my pc not more then 2 hours ago that never popped up.

can anyone tell me if its possible a bug in the alpha build or what? i know it is alpha and all but still thats my media drive and well backing it up right now is not possible...

thx in advance.

Jonny

Try wiping your harddrive with DBAN. 

make sure smart is enabled in your BIOS.
make sure you have the smarttools installed
and do the following ( the following is my work desktop but you get the idea )

sudo -i
fdisk -l | grep Disk
Disk /dev/sda: 250.0 GB, 250000000000 bytes
Disk /dev/sdb: 250.0 GB, 250000000000 bytes
smartctl -a /dev/sda 
smartctl -a /dev/sdb
smartctl -a /dev/sda | grep rror
smartctl -a /dev/sdb | grep rror

"| grep rror" and not "| grep error" because Error and error are listed in the output.


here is what my desktop at work looks like as you can see this is an issue with the sda drive.
 smartctl -a /dev/sda | grep rror
                                        was completed without error.
                                        without error or no self-test has ever 
Error logging capability:        (0x01) Error logging supported.
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       12
SMART Error Log Version: 1
ATA Error Count: 1
        ER = Error register [HEX]
Error 1 occurred at disk power-on lifetime: 11604 hours (483 days + 12 hours)
  When the command that caused the error occurred, the device was in an unknown state.
  Commands leading to the command that caused the error were:
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     29573         -
# 2  Short captive       Completed without error       00%      3017         -
# 3  Short offline       Completed without error       00%         0         -



the command line tool seems to be correct I ran at home on my Dell laptop which I know has bad sectors and it shows it too.

the bug with the GUI app is that it "reports a disk as failing even if it's under the threshold." under the threshold doesn't = failing since all harddrives have extra sectors that get remapped to being available when a bad sector is found.

---

### Post by jaakan on 2009-08-21
read this bug report

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/412152](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/412152)

jonnydopemsr: I think you still have bad sectors but not anything to really worry about just keep your data backed up.

---

### Post by kansasnoob on 2009-08-21
Every drive I've connected (both internal and external) and checked with palimpsest have shown the "bad sectors" error.

I've checked the same drives with an old V-Com System Suite utility in Win XP and they show being fine. The drives range in age from several years old to only a few months old.

I never worry too much because I have multiple backups of everything important.

---

### Post by jonnydopemsr on 2009-09-19
> **jaakan said:**
> read this bug report

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/412152](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/412152)

jonnydopemsr: I think you still have bad sectors but not anything to really worry about just keep your data backed up.

saddly that drive is my media drive as well as backup lol... and right now i dont have the money to get another one or else i would lol...

but thx for that info i will give it a shot

---

