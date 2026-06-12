---
title: "Ubuntu installation help (not your average cup of tea)"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by bluelight0 on 2012-05-16
hi, this could be a bit long but here it goes.
I have used gnu/linux/ubuntu for a while and am pretty used to it.
So i decided I wanted it on my HP touchpad so I can take it wherever I go.
Now, i have everything i need to set it up (kernel, image, software, commands ect.)
And i have actually setup a similar system before and had ubuntu running but it was not native. So I am doing a native install (triboot)

Now i have setup my boot loader to point to ubuntu and i can see the option. I also have the kernal installed. I have got a partition created, but it needs the directory setup in /media/ext3fs

This is where i get errors.

I remount like guides recommend,
Then try:
     mkdir -f /media/ext3fs
And it outputs something like:
      Can't make directory : not enough space free on device

Edit: if needs be i have a partition editor, complete format is not an option I'm afraid

Anyone have any idea what is causing this?

I have been Googling for hours and still haven't found a solution.

Thanks in advance.

---

### Post by cmont899 on 2012-05-16
Outputs of the following please:

```
mount
```

```
df -h
```

```
fdisk -l
```

---

### Post by jadtech on 2012-05-16
never  installed on a touch pad  so  no xp at it but it sounds like you dont have the unallocated space for the partition ..

---

### Post by bluelight0 on 2012-05-16
Thanks guys,

I may take a while to do this because it has no copy/paste for terminal

scratch that I will use `` to echo to file

... currently on terminal ...

---

### Post by bluelight0 on 2012-05-16
MOUNT
rootfs on / type rootfs (rw) /dev/root on /boot type ext3 (rw,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on / type ext3 (rw,relatime,errors=continue,barrier=0,data=writeback) proc on /proc type proc (rw,relatime) sysfs on /sys type sysfs (rw,relatime) /dev/mapper/store-root on /dev/.static/dev type ext3 (ro,relatime,errors=continue,barrier=0,data=writeback) tmpfs on /dev type tmpfs (rw,relatime,size=2048k,mode=755) none on /dev/cpuacct type cgroup (rw,relatime,cpuacct,cpu) devpts on /dev/pts type devpts (rw,relatime,gid=5,mode=620) /dev/mapper/store-var on /var type ext3 (rw,noatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-media on /media/internal type vfat (rw,relatime,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro) /dev/mapper/store-log on /var/log type ext3 (rw,noatime,errors=continue,barrier=0,data=writeback) tmpfs on /tmp type tmpfs (rw,relatime,size=40960k) tmpfs on /var/run type tmpfs (rw,relatime,size=16384k) tmpfs on /var/tmp type tmpfs (rw,relatime,size=32768k) tmpfs on /media/ram type tmpfs (rw,relatime) cryptofs on /media/cryptofs type fuse.cryptofs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other) none on /dev/cpuset type cgroup (rw,relatime,cpuset) /dev/mapper/store-cryptodb on /var/db type ext3 (rw,noatime,errors=continue,barrier=0,data=ordered) /dev/mapper/store-cryptofilecache on /var/file-cache type ext3 (rw,noatime,errors=continue,user_xattr,barrier=0,data=writeback) extractfs on /var/luna/data/extractfs type fuse.extractfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0) tmpfs on /var/palm/jail/org.webosinternals.tweaks.prefs/tmp type tmpfs (rw,relatime,size=40960k) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/lib type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/bin type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/bin type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/lib type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/frameworks type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/nodejs type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/data type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/share type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/services type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/public type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) proc on /var/palm/jail/org.webosinternals.tweaks.prefs/proc type proc (rw,relatime) tmpfs on /var/palm/jail/org.webosinternals.tweaks.prefs/dev/shm type tmpfs (rw,relatime,size=2048k,mode=755) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/etc/ssl type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-var on /var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/trustedcerts type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-var on /var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/certs type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-var on /var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/crl type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/etc/ls2 type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) tmpfs on /var/palm/jail/org.webosinternals.tweaks.prefs/dev/logdir type tmpfs (ro,nosuid,relatime,size=2048k,mode=755) /dev/mapper/store-var on /var/palm/jail/org.webosinternals.tweaks.prefs/var/palm/tokens type ext3 (rw,noatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-var on /var/palm/jail/org.webosinternals.tweaks.prefs/var/luna/preferences type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-cryptofilecache on /var/palm/jail/org.webosinternals.tweaks.prefs/var/file-cache type ext3 (rw,noatime,errors=continue,user_xattr,barrier=0,data=writeback) /dev/mapper/store-root on /var/palm/jail/org.webosinternals.tweaks.prefs/etc/palm type ext3 (ro,nosuid,relatime,errors=continue,barrier=0,data=writeback) /dev/mapper/store-media on /var/palm/jail/org.webosinternals.tweaks.prefs/media/internal type vfat (rw,relatime,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro) tmpfs on /var/palm/jail/org.webosinternals.tweaks.prefs/var/run type tmpfs (rw,relatime,size=16384k) cryptofs on /var/palm/jail/org.webosinternals.tweaks.prefs/media/cryptofs/apps/usr/palm/services/org.webosinternals.tweaks.prefs type fuse.cryptofs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)

---

### Post by bluelight0 on 2012-05-16
df -h
-------------------------------------
Filesystem Size Used Available Use% Mounted on
 /dev/root 31.0M 31.0M 0 100% /boot
/dev/mapper/store-root 559.1M 559.1M 0 100% /
 /dev/mapper/store-root 559.1M 559.1M 0 100% /dev/.static/dev
tmpfs 2.0M 176.0K 1.8M 9% /dev
 /dev/mapper/store-var 62.0M 11.1M 50.9M 18% /var
/dev/mapper/store-media 3.9G 2.8G 1.1G 71% /media/internal
/dev/mapper/store-log 23.2M 9.1M 14.1M 39% /var/lo
 tmpfs 40.0M 196.0K 39.8M 0% /tmp
 tmpfs 16.0M 84.0K 15.9M 1% /var/run
tmpfs 32.0M 16.0K 32.0M 0% /var/tmp
tmpfs 459.2M 0 459.2M 0% /media/ram
cryptofs 3.9G 2.8G 1.1G 71% /media/cryptofs
/dev/mapper/store-cryptodb 240.0M 26.5M 213.5M 11% /var/db
 /dev/mapper/store-cryptofilecache 127.5M 37.6M 89.9M 29% /var/file-cache
 tmpfs 40.0M 196.0K 39.8M 0% /var/palm/jail/org.webosinternals.tweaks.prefs/tmp
 /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/lib /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/bin /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/bin /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/lib /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/frameworks
 /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/nodejs
/dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/data /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/share /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/services /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/usr/palm/public
 tmpfs 2.0M 176.0K 1.8M 9% /var/palm/jail/org.webosinternals.tweaks.prefs/dev/shm
 /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/etc/ssl /dev/mapper/store-var 62.0M 11.1M 50.9M 18%
/var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/trustedcerts
 /dev/mapper/store-var 62.0M 11.1M 50.9M 18% /var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/certs /dev/mapper/store-var 62.0M 11.1M 50.9M 18% /var/palm/jail/org.webosinternals.tweaks.prefs/var/ssl/crl /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/etc/ls2 tmpfs 2.0M 176.0K 1.8M 9% /var/palm/jail/org.webosinternals.tweaks.prefs/dev/logdir
/dev/mapper/store-var 62.0M 11.1M 50.9M 18% /var/palm/jail/org.webosinternals.tweaks.prefs/var/palm/tokens
 /dev/mapper/store-var 62.0M 11.1M 50.9M 18% /var/palm/jail/org.webosinternals.tweaks.prefs/var/luna/preferences
/dev/mapper/store-cryptofilecache 127.5M 37.6M 89.9M 29% /var/palm/jail/org.webosinternals.tweaks.prefs/var/file-cache
 /dev/mapper/store-root 559.1M 559.1M 0 100% /var/palm/jail/org.webosinternals.tweaks.prefs/etc/palm /dev/mapper/store-media 3.9G 2.8G 1.1G 71% /var/palm/jail/org.webosinternals.tweaks.prefs/media/internal tmpfs 16.0M 84.0K 15.9M 1% /var/palm/jail/org.webosinternals.tweaks.prefs/var/run
cryptofs 3.9G 2.8G 1.1G 71% /var/palm/jail/org.webosinternals.tweaks.prefs/media/cryptofs/apps/usr/palm/services/org.webosinternals.tweaks.prefs

---

### Post by bluelight0 on 2012-05-16
sorry don't have fdisk as command...

anything you notice?

sorry if they don't line up like a table

---

### Post by darkod on 2012-05-16
Hold on, I didn't understand a word you said :)

What is /media/ext3fs and what are you trying to do with it?

Also, to start with, do you have any RAID or encryption on the laptop?

And can you boot into ubuntu live mode and post the output of:
sudo parted /dev/sda print

It's better if you can make a screenshot and attach it here, otherwise the text with copy-paste is all over the place.

Then we can take it further.

---

### Post by bluelight0 on 2012-05-16
ok... Sorry I don't know what RAID is and as far as I'm aware I have no encryption.

this is a device with no usbports or cd drives just power slot and wifi connection.

I can't get screen shots because I have no up arrow :(

Is there a command that would allow an echo to show line by line and preserve
/r/n ?

the top cuts off...

I will try and edit my post so it lines up please give me a moment

---

### Post by bluelight0 on 2012-05-16
oh... The /media/ext3fs is where my ubuntu partition should be.
the partition exists but does not have a directory.

the device in question is not a laptop but a HP touchpad.
When I last had ubuntu on it ext3fs was shown at /media/ext3fs

now when I come to recreate that directory it errors.

---

### Post by darkod on 2012-05-16
And from what OS are you trying to make the directory? Android? What is it running, WebOS, Android?

/media/ext3fs doesn't sound like a partition, if the convention is similar to linux. It sounds like a folder.

I think the copy-pasted text would stay better formatted if you paste it inside code tags, like [ code ] and [ /code ], but without the spaces.

You can also select the text you want to put inside the tags and hit the # button in the toolbar above when creating the post.

---

### Post by bluelight0 on 2012-05-16
I am using webos for terminal but have android also. Media doesn't show in android in the same way.

have I got this wrong?
which directory would a normal ext3fs be in?

[ubuntu chroot]("http://www.webos-internals.org/wiki/UbuntuChroot")

because I was thinking it would be in the same place as the chroot.
(scroll down to setting up ext3fs.

note: I am not making a chroot just analysing the setup, maby I should try a different directory

---

### Post by bluelight0 on 2012-05-16
here's the scripts I am using to install ubuntu by the way.
[http://code.google.com/p/hp-touchpad-ubuntu/wiki/Installation]("http://code.google.com/p/hp-touchpad-ubuntu/wiki/Installation")

the step that is failing is the media/ext3fs part but the rest should be fine with me.

---

### Post by jadtech on 2012-05-16
still again no expert not even close  but this is what I find  are the codes for mounting .. 

```

mount -o remount,rw /
mkdir -p /media/ext3fs


```

check out this  URL 

[http://www.webos-internals.org/wiki/Application:MetaDoctor#How_to_get_the_optional_ext3fs_partition_mounted_at_device_boot](http://www.webos-internals.org/wiki/Application:MetaDoctor#How_to_get_the_optional_ext3fs_partition_mounted_at_device_boot)

it is important that you use /media/ext3fs as the location, otherwise some homebrew applications (such as Optware and the Ubuntu 11.04 Chroot) will not be able to find it and use it properly.
After you have created the mountpoint, we are going to edit the fstab file to set it up to mount at bootup.

---

### Post by jadtech on 2012-05-16
> **jadtech said:**
> still again no expert not even close  but this is what I find  are the codes for mounting .. 

```

mount -o remount,rw /
mkdir -p /media/ext3fs


```

check out this  URL 

[http://www.webos-internals.org/wiki/Application:MetaDoctor#How_to_get_the_optional_ext3fs_partition_mounted_at_device_boot](http://www.webos-internals.org/wiki/Application:MetaDoctor#How_to_get_the_optional_ext3fs_partition_mounted_at_device_boot)

it is important that you use /media/ext3fs as the location, otherwise some homebrew applications (such as Optware and the Ubuntu 11.04 Chroot) will not be able to find it and use it properly.
After you have created the mountpoint, we are going to edit the fstab file to set it up to mount at bootup.

all of this will work provide you created the ext3fs right for webos doctor of at least 2gb  more if you want it larger for the ubuntu parts you will want to run and install..

after the mount and all is done  go back to this site

[http://www.webos-internals.org/wiki/UbuntuChroot](http://www.webos-internals.org/wiki/UbuntuChroot)

starting  AT STEP 3 partitioning by hand

---

### Post by darkod on 2012-05-16
OK, so, right now, if you want to check if there is anything in /media/ext3fs, what does it say when you run the command:
ls -l /media/ext3fs

---

### Post by bluelight0 on 2012-05-16
and that is where the juice runs out...
It won't let me run that second command.

maby I should try mnt instead of media (re looked over the purpose of each.)
is this a good idea?

It mentions chroot but I am doing a native install so it should not matter.

---

### Post by darkod on 2012-05-16
No, I would rather use /media. At least in ubuntu, I use /mnt only for temporary mounts, you want a permanent mount and I would use /media for that.

Did you check if you currently have anything in /media/ext3fs?

---

### Post by bluelight0 on 2012-05-16
> **darkod said:**
> OK, so, right now, if you want to check if there is anything in /media/ext3fs, what does it say when you run the command:
ls -l /media/ext3fs

error , does not exist.

---

### Post by bluelight0 on 2012-05-16
the chroot tutorial is the original kne I followed for a chroot of ubuntu inside webos.

now I have deleted the partition and come back to recreate it and make a triboot of webos,android,ubuntu

where it mentions partitioning I have software sorta like gparted on my tablet for that.

I will try deleting and recreating the partition to see if that fixes anything.

EDIT : if I don't come back in 15 mins I probably screwed up but so far I have resized it multiple times perfectly.

---

### Post by darkod on 2012-05-16
OK, so the folder doesn't exist.

Are you using the WebOS Doctor approach, or the manual steps?

If you are doing the manual steps, did you create the logical volume ext3fs in the volume group store?

If you try something like:
lvscan

What does it show? Which LVs do you have?

---

### Post by bluelight0 on 2012-05-16
ok... Re made the partition and it doen't let me mount becuase #directory# does  not exist.

tring lvscan now

---

### Post by bluelight0 on 2012-05-16
lvscan

ACTIVE '/dev/store/root'[568.00 MB] inherit
ACTIVE '/dev/store/var' [64.00 MB] inherit
 ACTIVE '/dev/store/update' [16.00 MB] inherit
 ACTIVE '/dev/store/log' [24.00 MB] inherit
ACTIVE '/dev/store/mojodb' [256.00 MB] inherit
ACTIVE '/dev/store/filecache' [136.00 MB] inherit
ACTIVE '/dev/store/media' [3.91 GB] inherit
ACTIVE '/dev/store/swap' [512.00 MB] inherit
ACTIVE '/dev/store/cm-system' [504.00 MB] inherit
ACTIVE '/dev/store/cm-cache' [504.00 MB] inherit
ACTIVE '/dev/store/cm-data' [3.91 GB] inherit
ACTIVE '/dev/store/ext3fs' [3.85 GB] inherit

---

### Post by bluelight0 on 2012-05-16
the meta doctor errors on me so I use a tool called tailor on webos which worked perfectly for android.

I also used this for my old ubuntu chroot, I didn't like how it was within the webos card (the equvlent of a window) but liked ubuntu so am trying to install a native version.

plus it was a tad too slow.

---

### Post by darkod on 2012-05-16
It seems you have the store-ext3fs LV active.

But the folder doesn't exist. Do you need to use maybe some equivalent of sudo when making the folder?

Otherwise, that tutorial you linked says only:
mkdir /media/ext3fs

EDIT: /media/internal is mounted right? Because if you left it unmounted of course you can't create any folders inside it. The manual instructions say to unmount it for resizing the LVs, but then to mount it again. I assume it's mounted ok.

You can always try different folder name:
mkdir /media/ext4fs

---

### Post by bluelight0 on 2012-05-16
the terminal is in root, I think its a custum for webos (xterm) and it does not have sudo. But I can make users and stuff but it defaults to root each time I use it.

so, everything I do is basically sudo so I should not need it.

---

### Post by darkod on 2012-05-16
Look in the edit of my last post if it gives you any idea. And try with different folder name, it doesn't need to be ext3fs specifically.

---

### Post by bluelight0 on 2012-05-16
no matter what I put...

mkdir: can't create directory 'insert snazzy name here': no space left on device.

hmm...

I'm googling it and finding similar problems but no answers yet.

---

### Post by darkod on 2012-05-16
Maybe we should take that message seriously. :)

Can it be that full that it doesn't even let you create a folder on it? Can you check how much of /media you have free? Or on your /root?

A little space is needed for every folder creation, even though the folder is empty at the beginning. Don't forget that.

This is something related to this message, and the space.

---

### Post by bluelight0 on 2012-05-16
know a command? My folder viewer seems to not show it.

---

### Post by bluelight0 on 2012-05-16
just says 3gb....

this matches ... Usb storage.

wow this confuses me.

---

### Post by bluelight0 on 2012-05-16
I am going to try something....

decreasing ubuntu partition and giving back to usb (media0


ok now I'm nog confused

---

### Post by darkod on 2012-05-16
Sorry, I have no idea about webos/android commands. In linux it would be like:
df -h

That also shows used percentage. I believe you have close to 100% on some, the results at the start of the thread were not readable easy. I think you ran df -h once and there were some 100% inside.

---

### Post by darkod on 2012-05-16
Note that if you created filesystem on store-ext3fs you can't simply shrink the LV. You can but it will mess up the filesystem.

You don't have any data there yet but don't forget to reformat it again to create new FS that will correspond to the size of the LV.

---

### Post by bluelight0 on 2012-05-16
I didn't do the last task, the shrinking stuff.

but I tried removing some stuff off media / internal and tried again but still the same

inside media I have a folder called media/ internal which webos documents and stuff are kept.in this I can freely create stuff like folders and files no problem.

but not in media

ps. Android shares this but is called sdcard in the file system not internal.

---

### Post by bluelight0 on 2012-05-16
some more googling... You don't suppose inodes have anything to do with this do you?

my knolegdge isn't that clear on them but they seem to me like something that stores an I'd of each file, has a maximum num of inodes and is usualy full due to lots of small files.

but I am still able to make stuff on media/internal so this makes no sense tome

---

### Post by darkod on 2012-05-16
To be honest, you are beginning to lose me. I have absolutely no experience with webos and android so far. :)

This is a question about creating a folder, it's not even ubuntu issue. And the ubuntu for tablet is also not the full ubuntu otherwise it would never fit into the 2GB that tutorial assigns to the LV. :)

I really have no ideas about this, except some general knowledge which I already posted.

---

### Post by bluelight0 on 2012-05-16
it isn't a full version because it has allot stripped from it like software ect...

I came here for help because it was an issue with a command for creating a file for ubuntu. So I was thinking that this was more of a ubuntu thing than webos/android

so I don't think this is much to do with webos or android.

the root system seems to be the same.

but yer, not too sure where to take this now.

---

### Post by bluelight0 on 2012-05-16
anyway **thankyou** for your help.

you've taught me a lot about the structure (I had a rough idea buy was confused)

I will continue checking up on this but I have to sleep now (10pm)

see you for now.

:-k

---

### Post by darkod on 2012-05-16
Creating that folder is part of the preparation for the stripped ubuntu install. So at that time you are still in webos (or anadroid if doing it through android).

Yes, there is similarity because android is based on linux too, but make no mistake, creating that folder is a webos task. If anything is holding you back creating it, you need to look into webos, not ubuntu.

Ubuntu is not even installed since that comes later after you have the folder created because the folder is the destination for the install. That's what that link says. You do the ubuntu chroot (stripped ubuntu) install only after the /media/ext3fs folder is created and store-ext3fs mounted in it.

---

### Post by jadtech on 2012-05-16
as I understand it what is being installed is basic ubuntu kernel which has only a raw root shell no gui or graphic  more to the nature of a Ubuntu minimal ISO on usb only this USB is virtual all the files have to be down down loaded part by part, once all the peices of this ubuntu mini are down loaded  you can then install with graphic desk top upgraded   or it can be ran as is boot like live CD .. 

shrug I could be misunderstanding

---

### Post by bluelight0 on 2012-05-17
Pretty much,

It comes with unity and touchscreen drivers so you can navigate easily
(Only a touch screen)

But other than that, yes it is quite minimal.

I will try webos nation, maby they know.

Still i will keep checking here for any input. :)

---

### Post by bluelight0 on 2012-05-17
yay! I go it working!

Now all i need is wifi.

Thankyou for all your help.

I got it working by creating a temporary mount in /tmp
Then i could install and then rebooted into ubuntu!
Still not sure about that media partition glitch... but oh well. It doesn't stop me using ubuntu now.

---

