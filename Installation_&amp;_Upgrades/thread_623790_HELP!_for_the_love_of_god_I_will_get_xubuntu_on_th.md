---
title: "HELP! for the love of god I will get xubuntu on this system!"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by linuxnoobz on 2007-11-26
Ok I know this is just a 30 second post to you guys, but its been a 1 week project for me.....

I have a gateway solo 2500, old laptop...... PII 333mhz, 96 megs of ram 6 gig hdd...........it BARELY makes the specs, but I SHOULD be able to get it on here...... plus i've read of other ubuntu installs done on this laptop model.....the dvd rom on here has NEVER liked CD-R's.....

SINCE my DVD-ROM doesnt like ISO's, id rather just do it through wubi.....


ive tried numerous methods......

**1. ISO CD install of xubuntu 7.10 alternate:**

::::::::::::hangs at 6% " during "installing base system".....have tried several CD-Rs, same thing:::::::::

**2. Method 1 from:**
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

:::::::: doesnt find the iso::::::::::::tried hd0,1, hd0,0......


**3. Finally wubi:**

:::::::::after iso download, then reboot,  I get "no disk in drive" repeatedly..... it just hangs there.....:::::::::::

ive tried numerous iso's, including the alternates as wubi suggested

.here is the zenigata.log from wubi:

```
+ PREREQ=
+ ROOTMNT=/root
+ HOSTMNT=/media/host
+ HOSTFOLDER=
+ ISOMNT=/cdrom
+ HOSTKEY=
+ SUITE=
+ DEFAULTSUITE=feisty dapper unstable testing stable
+ SETUP_INIT=busybox init
+ SETUPISO=
+ ROOTIMG=system.virtual.disk
+ HOMEIMG=home.virtual.disk
+ SWAPIMG=swap.virtual.disk
+ EXTRAIMG=extra.virtual.disk
+ USRIMG=programs.virtual.disk
+ DUMMYIMG=install.virtual.disk
+ ROOTDEV=
+ HOMEDEV=
+ SWAPDEV=
+ EXTRADEV=
+ USRDEV=
+ DUMMYDEV=
+ USEFREESPACE=
+ PAUSEFORDEBUG=n
+ cat /proc/cmdline
+ HOSTKEY=/wubi/boot/linux
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ [ -n /wubi/boot/linux ]
+ find_host_folder
+ wait_for_devs
+ log_begin_msg ...waiting for devs...
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT ...waiting for devs...
+ _log_msg Begin: ...waiting for devs... ...
+ echo Begin: ...waiting for devs... ...
Begin: ...waiting for devs... ...
+ udevtrigger --subsystem-match=block
+ udevsettle
+ log_end_msg ...devs loaded...
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 1 ]
+ PROGRESS_STATE=2
+ echo PROGRESS_STATE=2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 2
+ [ -n /wubi/boot/linux ]
+ log_begin_msg Loking for /wubi/boot/linux
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Loking for /wubi/boot/linux
+ _log_msg Begin: Loking for /wubi/boot/linux ...
+ echo Begin: Loking for /wubi/boot/linux ...
Begin: Loking for /wubi/boot/linux ...
+ fast_scan
+ log_begin_msg Fast scan
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Fast scan
+ _log_msg Begin: Fast scan ...
+ echo Begin: Fast scan ...
Begin: Fast scan ...
+ list_devices
+ ALLDEVICES=
+ [ -b /dev/mapper/control ]
+ [ -b /dev/hda1 ]
+ check_fs /dev/hda1
+ dev=/dev/hda1
+ get_fs /dev/hda1
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1
+ [ -b /dev/hdd1 ]
+ check_fs /dev/hdd1
+ dev=/dev/hdd1
+ get_fs /dev/hdd1
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd2 ]
+ check_fs /dev/hdd2
+ dev=/dev/hdd2
+ get_fs /dev/hdd2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd3 ]
+ check_fs /dev/hdd3
+ dev=/dev/hdd3
+ get_fs /dev/hdd3
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd4 ]
+ check_fs /dev/hdd4
+ dev=/dev/hdd4
+ get_fs /dev/hdd4
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd5 ]
+ check_fs /dev/hdd5
+ dev=/dev/hdd5
+ get_fs /dev/hdd5
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd6 ]
+ check_fs /dev/hdd6
+ dev=/dev/hdd6
+ get_fs /dev/hdd6
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd7 ]
+ check_fs /dev/hdd7
+ dev=/dev/hdd7
+ get_fs /dev/hdd7
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd8 ]
+ check_fs /dev/hdd8
+ dev=/dev/hdd8
+ get_fs /dev/hdd8
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd9 ]
+ check_fs /dev/hdd9
+ dev=/dev/hdd9
+ get_fs /dev/hdd9
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hda ]
+ check_fs /dev/hda
+ dev=/dev/hda
+ get_fs /dev/hda
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdc ]
+ check_fs /dev/hdc
+ dev=/dev/hdc
+ get_fs /dev/hdc
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdd ]
+ check_fs /dev/hdd
+ dev=/dev/hdd
+ get_fs /dev/hdd
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ dev=/sys/block/hda/hda1
+ dev=/dev/hda1
+ [ -b /dev/hda1 ]
+ check_fs /dev/hda1
+ dev=/dev/hda1
+ get_fs /dev/hda1
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda1
+ scan_devices /dev/hda1 /dev/hda1
+ devs=/dev/hda1 /dev/hda1
+ is_host_device /dev/hda1
+ dev=/dev/hda1
+ log_begin_msg Testing device /dev/hda1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/hda1
+ _log_msg Begin: Testing device /dev/hda1 ...
+ echo Begin: Testing device /dev/hda1 ...
Begin: Testing device /dev/hda1 ...
+ safe_mount /dev/hda1 /media/host
+ dev=/dev/hda1
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/hda1
+ dev=/dev/hda1
+ FSTYPE=unknown
+ [ ! -b /dev/hda1 ]
+ /lib/udev/vol_id -t /dev/hda1
+ FSTYPE=vfat
+ [ -z vfat ]
+ mount -t auto /dev/hda1 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/hda1!!!!
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 2 ]
+ PROGRESS_STATE=3
+ echo PROGRESS_STATE=3
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 3
+ return 0
+ return 0
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 3 ]
+ PROGRESS_STATE=4
+ echo PROGRESS_STATE=4
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 4
+ return 0
+ mount_host_dev /dev/hda1
+ hostdev=/dev/hda1
+ log_begin_msg Mounting /dev/hda1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/hda1
+ _log_msg Begin: Mounting /dev/hda1 ...
+ echo Begin: Mounting /dev/hda1 ...
Begin: Mounting /dev/hda1 ...
+ safe_mount /dev/hda1 /media/host rw
+ dev=/dev/hda1
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/hda1
+ dev=/dev/hda1
+ FSTYPE=unknown
+ [ ! -b /dev/hda1 ]
+ /lib/udev/vol_id -t /dev/hda1
+ FSTYPE=vfat
+ [ -z vfat ]
+ mount -t auto -o rw /dev/hda1 /media/host
+ HOSTFOLDER=/wubi/boot
+ HOSTFOLDER=/wubi
+ [ /wubi = / ]
+ HOSTFOLDER=/media/host/wubi
+ grep /media/host /proc/mounts
+ grep -q rw
+ 
+ return 0
+ rm_logs
+ [ -e /media/host/wubi/logs ]
+ get_target_devices
+ [  = y ]
+ [ -f /media/host/wubi/disks/system.virtual.disk ]
+ [ -f /media/host/wubi/disks/swap.virtual.disk ]
+ [ -f /media/host/wubi/disks/home.virtual.disk ]
+ [ -f /media/host/wubi/disks/extra.virtual.disk ]
+ [ -f /media/host/wubi/disks/programs.virtual.disk ]
+ return 0
+ [ -n  ]
+ echo ROOT=
+ echo ROOTFLAGS=''
+ echo ROOTFSTYPE=vfat
+ echo ISOMNT=/cdrom
+ echo ROOTMNT=/root
+ echo HOSTFOLDER=/media/host/wubi
+ echo SUITE=
+ echo SETUPISO=
+ echo HOSTMNT=/media/host
+ echo ROOTDEV=
+ echo HOMEDEV=
+ echo SWAPDEV=
+ echo EXTRADEV=
+ echo PAUSEFORDEBUG=n
+ [ -f /media/host/wubi/boot/lupin ]
+ pause_for_debug Zenigata End
+ cd /
+ cp_logs
+ [ -e /logs ]
+ mkdir /logs
+ cp /tmp/zenigata.log /logs/
+ [ -e /media/host/wubi ]
+ [ -e /media/host/wubi/logs ]
+ mkdir -p /media/host/wubi/logs
+ cp /tmp/zenigata.log /media/host/wubi/logs

```


any ideas? whats wubi doing wrong??? any solutions for any of these problems?

As I said, i'd like to avoid any CD-R installations, cuz my DVD-ROM has never cared much for CD-Rs for some reason....... so ANY ideas to resolve these issues or any NO-CD install alternatives are welcome

---

### Post by scrooge_74 on 2007-11-26
go to debian, and get the Debian Xfce4  version or the Net install for Lenny, and go from there

---

### Post by linuxnoobz on 2007-11-26
tried debian lenny net install with disks.....

got I/O error on root disk.....read about the disk install issues...... wrote the image several times, tried a different disk......tried a different download of root img....

also add unetbootin and another manual iso install to the list of failed attempts......

good heavens......i mean really.....every method has a freakin problem........... kernel panic, i/o read error, no disk in drive......

not very merciful software....

---

### Post by scrooge_74 on 2007-11-26
Then instead of instaling to disk use Damn Small Linux or Puppy linux

---

### Post by Craigus on 2007-11-26
> the dvd rom on here has NEVER liked CD-R's

Have you tried burning the iso to DVD-R or +R instead?

Here's an older site dealing with linux on your machine:

[http://www.thehayesweb.org/jhayes/solo2500.html]("http://www.thehayesweb.org/jhayes/solo2500.html")

---

### Post by dolphin_oracle on 2007-11-26
I've got on old vaio (PCG-FXA32, 900mhz Duron, 128mb ram, 15 gb HD), so I feel your pain to an extent.

On a low spec machine, the installation of Xubuntu will hang at 6% FOREVER.  Mine hangs everytime for about 45 minutes, then procedes normally.  How long did you wait?  Also, waiting to configure the network until after the installation is complete seems to help.

My guess is no 1 is probably a successful installation, its just gonna take a LONG time.  96mb of ram isn't a lot of ram (bbviously).

I've had this problem on edgy, feisty, and gutsy.

---

### Post by anv on 2007-11-26
Dear heavenly Father, you are God of plenty the El-Shaddai I ask in Jesus name to grant better hardware to my brother, so that he don't have to play with worlds best operative system with some trashy old laptop. Amen   :confused:

---

### Post by linuxnoobz on 2007-11-26
> **Craigus said:**
> Have you tried burning the iso to DVD-R or +R instead?

Here's an older site dealing with linux on your machine:

[http://www.thehayesweb.org/jhayes/solo2500.html]("http://www.thehayesweb.org/jhayes/solo2500.html")

yep, tried it

---

### Post by linuxnoobz on 2007-11-26
> **dolphin_oracle said:**
> I've got on old vaio (PCG-FXA32, 900mhz Duron, 128mb ram, 15 gb HD), so I feel your pain to an extent.

On a low spec machine, the installation of Xubuntu will hang at 6% FOREVER.  Mine hangs everytime for about 45 minutes, then procedes normally.  How long did you wait?  Also, waiting to configure the network until after the installation is complete seems to help.

My guess is no 1 is probably a successful installation, its just gonna take a LONG time.  96mb of ram isn't a lot of ram (bbviously).

I've had this problem on edgy, feisty, and gutsy.

What happens is the DVD-ROM starts making unorthodox noises and then I get the red screen of death telling me it cant read the cd

---

### Post by scrooge_74 on 2007-11-26
I think you have hardware problems there. If you still have some kind of windows on that machine you can do a net install if you follow [this link]("http://goodbye-microsoft.com/")

---

### Post by dolphin_oracle on 2007-11-26
> What happens is the DVD-ROM starts making unorthodox noises and then I get the red screen of death telling me it cant read the cd

I had this problem with Gparted - the old DVD-ROM drives are incredibly finicky when it comes to the cd-r media.  Mine doesn't like imation disks - i generally stick to verbatim or memorex. 

Of course, there is probably a different problem if you get to 6% (obviously reading the disk) and then it craps out.

---

### Post by nzadLithium on 2007-11-26
can i ask why you want to put Xubuntu on it? It will go extremely slowly. I've installed ubuntu on a pentium 3 700mhz (i think) and it took ages to install and runs slowly when you get in. I think you would be better off with Damn small Linux or Knoppix or any smaller distro like them. Ubuntu isnt really designed to run on anything less than a 1.5ghz pentium 4 imo. You might be able to get Xubuntu to go on a 1.0ghz proccessor but i think anything less would be too slow.

---

### Post by linuxnoobz on 2007-11-26
ive thrown it on several 500mhz systems, 128/256mb, and it ran pretty decent. Not GREAT but not slow enough to take it off....

and i just like the gui of it, included applications, etc

---

### Post by linuxnoobz on 2007-11-26
p.s. i gave up on the solo. diagnosis, dvd-rom

the solo 2500 comes with the dvd rom option, and im guessing all successful 2500 installs we're with the regular cd rom most likely........never heard/read of a net/usb install with the 2500

it does definitely have some proprietary hardware on it

---

### Post by nzadLithium on 2007-11-27
maybe u could install from a usb disk? you could prob stick on usb and use a floppy boot disk to install see how that goes?

---

### Post by Aniongap on 2007-11-27
Simply not enough RAM?

---

### Post by psycho5 on 2007-11-27
that 6% 'hang' is not really a hang, just a *&^$ing long wait time at that point, it'll proceed after half an hour or 1 and a half hours... 

my installation, that 6% percent really pissed me off, it actually "failed" a couple of times, I kept retrying and it finally was "stuck" for what seemed like an eternity, then later it proceeded with the rest of the install. You just got to be patient.

---

### Post by jimbob83 on 2007-11-27
I'm a complete linux noob trying to install xubuntu 7.10 on a similar spec system (HP Omnibook 900, PII 300, 160MB RAM, 40GB hd).  The installer is hanging at 15% with a message "Detecting file systems..."  There was no hang at 6%.  Nothing seems to be happening, its been sitting like that for the last 50  minutes or so.  Should I keep waiting?

This is the 2nd time trying to install, and its hanging at exactly the same point.  The first time I gave up after 45 minutes and rebooted.  The 1st time the computer seemed to have locked up -- none of the keys worked, not even CTRL-ALT-DEL.

---

### Post by jimbob83 on 2007-11-27
Never mind, I gave up. Going to try another distribution.

---

### Post by nzadLithium on 2007-11-27
jimbo of course its hanging your running it on a pentium 2! it was extremely slow install while running on pentium 3 700mhz. It took about an hour to install so on that pc im thinking it will take probably 3 hours?

I do think your idea of going to a diff distribution is sensible though running on ubuntu on that in my opinion is not sensible. Its fine to run ubuntu on a intel processor 1.5ghz or greater or an AMD one probably 1.3ghz or greater. (not referring to dual or quad core processors here)

I would suggest damn small linux or knoppix as distros to run on that. They are pretty much the smallest distros you can get.

---

### Post by linuxnoobz on 2007-11-27
> **psycho5 said:**
> that 6% 'hang' is not really a hang, just a *&^$ing long wait time at that point, it'll proceed after half an hour or 1 and a half hours... 

my installation, that 6% percent really pissed me off, it actually "failed" a couple of times, I kept retrying and it finally was "stuck" for what seemed like an eternity, then later it proceeded with the rest of the install. You just got to be patient.

i meant it stops, doesnt hang, it stops reading the cd and tells me so

---

### Post by jimbob83 on 2007-11-27
Thanks for the feedback nzadLithium.  I think the computer was actually locked up as nothing would respond.

Right now I've got it going through the xubuntu alternate install. Its up to 85% through Select and Install Software and seems to be hanging again, but I'll leave it overnight and see what happens.  Hopefully it can get all the way through.

I tried Knoppix earlier today, but working off the cd is painfully slow.

If the xubuntu turns out to be really slow too (I'm guessing it will given what you said and how long its taking to install) then I'll give Damn Small Linux a try.  I've downloaded DSL but went back to xubuntu after looking at the number of files on the ftp download pages for DSL (guessing that DSL will require much more configuration than ubuntu).

---

### Post by nzadLithium on 2007-11-27
as long as you dont try to install anything extra into dsl you will be fine. If you want extra programs though then it gets messy. Can be done but im having a bit of fun installing java on an old pc running dsl atm :D

---

