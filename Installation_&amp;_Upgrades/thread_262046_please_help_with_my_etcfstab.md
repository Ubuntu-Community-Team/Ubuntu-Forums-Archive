---
title: "please help with my /etc/fstab"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by palz on 2006-09-21
Hello I need to totally overhaul my ubuntu server. :confused:  I don't know what's wrong. I am a noob and would like to familiarize myself with the file system of linux.

In our office I was tasked to create a simple file server with windows clients connecting to it. Good thing ubuntu just released Ubuntu 5.10 back then. I research on the web and found this how to link. 

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

I followed it step by step and it worked like a charm.

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro,usrquota,grpquota    0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda4       /home           ext3    defaults,usrquota,grpquota    0    2
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


However what i didn't realized back then was that I didn't have SCSI HDDs! I have IDE ones. This is where the problem starts. The server ran for months while I left it to be filled with data. Recently I made a quick check on the disk

df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             19228308  15056820   3194736  83% /
tmpfs                   517824         0    517824   0% /dev/shm
tmpfs                   517824     12644    505180   3% /lib/modules/2.6.12-9-686/volatile

and I was shocked that my / folder was already 83% and rising. So I decided to extend that by adding another hard disk.

so I researched on ubuntuforums.org, etc... on how to do it and this is what happened. After physically placing my new hard disk it was identified by Ubuntu as "hdd". (Secondary Slave)

sudo lshw -C disk

Password:
  *-disk
       description: ATA Disk
       product: ST380011A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 8.01
       serial: 5JVTKQT2
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm
       configuration: smart=on
  *-cdrom
       description: IDE CD-ROM
       product: GCR-8525B
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 1.01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
  *-disk
       description: ATA Disk
       product: WDC WD800BB-00JHC0
       vendor: Western Digital
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 05.01C05
       serial: WD-WMAM9Y039985
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm
       configuration: mode=udma5 smart=on

I need to increase space in the folder / so I then proceeded in mounting it by typing:

sudo mount /dev/hdd /

I thought It would just add the space (by the way, the new hard disk was already formatted with ext3) (whole disk) but this is what happended


df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             19228308  15056820   3194736  83% /
tmpfs                   517824         0    517824   0% /dev/shm
tmpfs                   517824     12644    505180   3% /lib/modules/2.6.12-9-686/volatile
/dev/hdd1             19228308  15056820   3194736  83% /

The new hard disk had the same % as my sda3 (I don't know if this is reflected properly though)

mount:

/dev/sda3 on / type ext3 (rw,errors=remount-ro,usrquota,grpquota)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-686/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdd1 on / type ext3 (rw)

I know this has something to do with quota? Is it?

Thanks for bearing with my long explanation. I think I'm totally screwed.:confused: :D

---

### Post by bernied on 2006-09-21
You are not totally screwed. You have simply mounted an empty disk over the top of your root directory. You haven't deleted anything. Unmounting /dev/hdd1 should restore the system.

I doubt this is anything to with quotas, I don't know what is going on with df, but all the strangeness is probably due to mounting two devices on a single mount point.

So, if it were mine, I'd try something like this:
sudo umount /dev/hdd1
cd /
ls
# is everything there? good!

do this, then work out how you're going to use that extra drive - but don't attempt what you did the first time.

---

### Post by bernied on 2006-09-21
I've just realised that umount is an application (/bin/umount) so will be unavailable in the server's current state, so you probably need to shutdown the system (if it hasn't crashed already). If you have put the /dev/hdd1 line into /etc/fstab then you may not be able to boot the machine into that install, so you'll need to fix the /etc/fstab (just remove that line) from an alternate method - maybe a live-cd?

Is that the entire output from df and mount?
If it is then your /dev/sda1 and /dev/sda4 partitions do not seem to be mounted. You also do not seem to have any swap space mounted.

If your /home partition is not mounted, then this might account for your / partition filling up. Everything that was meant to be in /dev/sda4 (ie. your /home directory) will be on /dev/sda3.

(note that you should NOT simply mount the /dev/sda4 on /home now, because in all likelihood it is empty, and it will look like you have lost all of the files in /home)

Have a look at dmesg, you should find information about the mounting of filesystems at boot time. Here's some of mine:
```
$ dmesg
.
.
.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb7, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb8, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
.
.
etc..
```You can see that each filesystem that is mounted is listed here, including swap space. If there is a problem with mounting, it will be listed here.

---

### Post by palz on 2006-09-21
thanks bernied, you saved me from a lot of trouble there. I simply unmounted my /dev/hdd disk by typing:

```
sudo umount /dev/hdd
```

This was my first mount and umount :D

:KS :p 

Yup you're  right about my /dev/sda1 , sda2, sda3 ,sda4, they are not mounted at all that is why my / folder is getting filled up. I will post my dmesg later if I have the chance.

I woke up early to be able to tinker with the /etc/fstab of the server. What I did was to change all the sda's into hda's like this: (I really had to muster courage to do this, because this might crash something)

```

/dev/hda3 / ext3 defaults,errors=remount-ro,usrquota,grpquota 0 1
/dev/hda1 /boot ext3 defaults 0 2
/dev/hda4 /home ext3 defaults,usrquota,grpquota 0 2
/dev/hda2 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```

I restarted the server then it happened... I saw at the start up that the quotas has been started. I then saw the server's /home, /boot folders at the df!:D 

I also saw the bulk of the 80 gig at the /home folder it was showing only a 4% of usage.:D This is where I want to put the old files in.:razz: 

This is where my problem starts. I was excited to check on the client computers if they can access the old files. When I tried accessing them from the client side. I couldn't access them. It's like they are denied to access that folder. It seems that there is something wrong with the configuration of Samba (take note: I did everything it said to the tutorial link). 

Do I need to do something about the permissions on the server. Do I need to chmod 777 anything? Can someone point me in the right direction. Thank very much.

---

### Post by bernied on 2006-09-22
Slow down.
You have now mounted your empty /sda4 partition on top of your old home folders. So you cannot access the data in /home
Unmount that partition and sit tight. I have a meeting - will offer more advice in 2-3 hours.

---

### Post by bernied on 2006-09-22
Right, so you need to understand what it is to mount. Whenever you mount something (lets say hda4) onto a mountpoint on the filesystem (lets say /home), then the contents of hda4 will be available from /home. Whatever was in /home before will appear to have vanished, but it is still on the disk (hda3 in your case). You will find it very hard (perhaps impossible) to access the data that was in /home before you mounted hda4, while you've still got hda4 mounted over the top of it.

So, I see your problem in three stages:
1 - move data from old /home on /dev/hda3 to /dev/hda4, then get that mounted at /home
2 - get samba working with this new configuration
3 - work out what you want to do with your new 74GB drive

I don't know anything about using quotas through samba, which will affect stage 2, and this aspect might need more consideration.

So, this system of yours, are people actually using the file store on this machine? If they are, then I suggest that you take this very slowly and carefully and don't rush in without understanding the consequences before you act. Otherwise your users will get even angrier with you than they must already be by now. So, if this server is in constant use then the approach you should take would be a little different and should involve having a complete, tested course of action that will fix both stages 1 and 2 above, before you begin. I can outline how to achieve stage 1, but suggest that you do this not on /home, but elsewhere (say /mnt/temphome), then setup samba to share this new directory and make sure that samba is working well, before you implement the solution on /home. 

So, first make a backup of your /ect/fstab
$ sudo cp /etc/fstab /etc/fstab.working

Then change that line in /etc/fstab that mounts /dev/hda4. Change the mountpoint from /home to /mnt/temphome and save the file.

Then, if you haven't already, unmount /dev/hda4
$ sudo umount /dev/hda4
(if it doesn't unmount - because it is in use - you will have to stop whatever is using it - samba maybe - then unmount, then restart whatever it was that you stopped, else you could just restart the server)
Now have a quick look to see if your /home directory has been restored - yes? good.

Next, create the temporary mount point for hda4.
$ sudo mkdir /mnt/temphome
then, mount hda4 there
$ sudo mount -a
then go to the mountpoint and check it's empty
$ cd /mnt/temphome
$ ls
and maybe just check that it's mounted and is listed in df
$ mount
$ df
If it all looks good, continue, else STOP and fix whatever is wrong.

So, if all is well, copy everything in /home to the new partition. This may take some time, depending on how much is stored in /home. You may want to research this command before you do it, to understand what you are doing (try 'man cp' for a description). You may want to leave out the 'v' option, but I think the 'a' option is what you need to preserve all permissions and timestamps - here we go:
$ sudo cp -av /home/* /mnt/temphome/

So now you should probably rummage around in /mnt/temphome and compare the contents with /home. Use 'ls -l' to check that everything is the same in the parallel directories.

Did that work? If not, STOP and fix it.

Next, get this /mnt/temphome folder (or maybe just a part of it) shared on samba. You might want to warn your clients that this folder will appear and that they should ignore it, but be aware that if you get this part wrong you might give everyone access to all users files - again, you would not be popular. So maybe you could set the path to only your user.
So, in your /etc/samba/smb.conf file, add a new folder that duplicates the one you have for /home, except that it says 
[temphome]
  path = /mnt/temphome/palz
etc..
then restart samba
$ sudo /etc/init.d/samba restart
and see if it all looks ok from the client's perspective.

If the temphome samba share does not work, then this may be to do with quotas. Make sure you know what is going on here and that samba works propoerly on the temphome folder before you continue.

If this works, and you are sure that you are ready to start using your new copy of /home, then you will need to have some time when samba is stopped, because you can't have users using the files when you are moving them about.
I suggest you do it something like this...
Stop samba
$ sudo /etc/init.d/samba stop
Check that /dev/hda4 is still mounted
$ mount
If it is not, then mount it with 'mount -a' and check that this worked.

Update your copy of /home - this should be much faster than the first cp, because you are only copying changed or new files (read man cp again to see which options I'm suggesting here)
$ sudo cp -avu /home/* /mnt/temphome/
change the name of the old /home and make a new /home
$ cd /
$ sudo mv /home /oldhome
$ sudo mkdir /home
Make sure this worked, else you will lose access to the old /home directory once you mount, which is next. Do not continue if you errors with either of these steps.

Next change /etc/fstab so that /dev/hda4 mounts on /home.
Then, unmount /dev/hda4 from /tmp/mount and mount it on /home.
$ sudo umount /dev/hda4
$ sudo mount -a
Restart samba
$ sudo /etc/init.d/samba start

Should be done, so go and test it.
If it worked, you can then decide what to do with /oldhome (be very careful to know that all has gone well before you delete the folder)

If you have trouble with this, if anything goes wrong, you can reverse it like this
$ sudo /etc/init.d/samba stop
$ sudo umount /dev/hda4
$ sudo mv /oldhome /home
$ sudo /etc/init.d/samba start

And change back the /etc/fstab so that /dev/hda4 mounts on /mnt/temphome (or comment out this line).

Now you can go on with stage 3

I also suggest that you put some thought into a backup system - you will have very angry users if you lose their data as part of your rushing to fix things that are already working.

If you have trouble, post what you did and the output including any error messages.

---

### Post by palz on 2006-09-27
Sorry for the late reply, I have been busy with work. Hmm.. so that's why I can't access my shares. I will analyze your suggestions and get back to you as soon as possible. Thanks :D

---

