---
title: "Reinstall root only"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Kschikan on 2007-11-26
As detailed in my previous thread (found at [http://ubuntuforums.org/showthread.php?t=593247](http://ubuntuforums.org/showthread.php?t=593247)) I had an issue with an upgrade from 7.04 to 7.10. Since I couldn't find a solution to that problem, I was wondering if it would be possible to install *just* the root directory to my drive, and then point my home directory at the old home directory (which I hopefully would not overwrite in the process). It seems like the manual install from LiveCD allows me to specify just the root partition, but I wanted to be sure that I would A) not overwrite my old home directory if I didn't use that partition for anything and B) be able to point my home directory to the old /home on the machine.

Any help?

---

### Post by nzadLithium on 2007-11-26
I dont think its possible to install only the root directory. i think if you have an empty partition u dont need though ( i dont think many people would waste disk space but u never know) you can install the whole of ubuntu to that partition and then relink to your home directory on another one. If your new install is written to a dif partition than your old install i seriously doubt it will overwrite your old home directory however if you reinstall over the same partition im fairly sure it will overwrite it.

Is it possible for you to be able to run these commands like in your previous thread
chown -R <name> /home/<name>
chgrp -R <name> /home/<name>
chmod -R 755 /home/<name>
chmod 644 $HOME/.dmrc
and then to copy your home directory to another disk (hard disk or dvd or whatever) then do a complete reinstall?

This way you can keep all your files. You will lose all your programs though because they are stored all over the place :S

---

### Post by Kschikan on 2007-11-28
As I said in my previous thread, my home directory does not show up in my tty login; I therefore cannot execute those commands. I *can* see the partition if I boot with the Linux System Rescue CD and look at the drive with gParted. If possible, I'll try to use the System Rescue CD to copy that partition over; otherwise, I'd love suggestions.

---

### Post by nzadLithium on 2007-11-29
can you get into your hard disk at all from a tty login?

---

### Post by Kschikan on 2007-11-29
I can login and see my root directory from a tty terminal, but I get the warning "WARNING! Cannot find home directory!" (or something similar, it's not in front of me). The root directory seems fine, although it's obviously not if I can't login in graphically or see my home directory. Using gParted on the Rescue CD I can see that the partition that has my /home directory has data, so I'm fairly certain my data is still there, I just can't access it.

---

### Post by nzadLithium on 2007-11-30
are you logged in as root when you login to the tty?
If you are then try doing cd /home/(your username)
then type ls
see if your home directory stuff shows up.
if you arent logged in as root then login as root :D

If it does work then we may be able to 'reattach' your home directory and that might fix your gui problem.

---

### Post by Kschikan on 2007-12-01
I get the following when logging in and looking in my home directory. 

No directory, logging in with HOME=/
To run a command as administrator (user="root", use "sudo <command>".
See "man sudo_root" for details.

kane@phoenix:/$ cd home
kane@phoenix:/home$ ls
kane@phoenix:/$ cd kane
-bash: cd: kane: No such file or directory
kane@phoenix:/$

---

### Post by froy02 on 2007-12-02
precede each command with sudo like:
sudo cd kane
sudo ls

Or you could just type sudo su before you issue any command. This would make you a super user without preceding each command with sudo.

---

### Post by Kschikan on 2007-12-02
I am well familiar with the sudo (and su) command. Note that Ubuntu does not have a root user created by default (the man page for sudo_root documents this). **My home directory does not appear in the /home folder. I cannot access it in any way when I login. It does not matter if I use the sudo command to execute ls or not.** I only know the data I have for my /home partition is alright because I booted with the Linux System Rescue CD and looked at the drive with gParted. If someone can tell me how to force the home drive to include a link to that partition, I would be happy. There are no files/folders/links/anything in my /home folder.

I apologize if I sound frustrated, but I have explicitly pointed out that I *cannot* see my home directory when I login through a tty terminal. I cannot execute any commands that have /home/<username> in them, *because that folder DOES NOT EXIST.*

---

### Post by nzadLithium on 2007-12-02
ah you have a seperate home partition??

ok post the contents of /etc/fstab
i think unless you want to type the whole thing out then you'll have to use your rescue disk thing again to get the contents.

I think whats happening is either your home partition isnt mounted or it isnt mounted correctly.

---

### Post by nzadLithium on 2007-12-06
come on reply! if its really that its just not mounting your home partition then its so easy to fix!

+ if you still need to reinstall then since your home is on a seperate partition its even easier for you to do a complete reinstall than before. Just install it without installing anything on that home partition then we can point the home partition back to that home folder. :D

post up that file and ill tell you what to add

---

### Post by Kschikan on 2007-12-06
Apologies for the slow reply - Bellsouth decided I didn't need the internet at home for a few days..

Below are the contents of my fstab file. For fun and profit, I included fstab.edgy and fstab.pre-uuid

thanks again.

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc	/proc	proc	defaults	0	0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7e5176e5-c7e3-454f-a4a0-6044b3bc3245 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=e66bb58f-1f21-495d-9e74-b8e4fde52d5d /home ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=f46e81cd-4160-482f-82e4-fc63cbce66c1 none swap sw 0 0 
/dev/cdrom	/media/cdrom0	udf,iso9660 user,noauto	0	0


fstab.edgy


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc	/proc	proc	defaults	0	0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7e5176e5-c7e3-454f-a4a0-6044b3bc3245 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=e66bb58f-1f21-495d-9e74-b8e4fde52d5d /home ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=f46e81cd-4160-482f-82e4-fc63cbce66c1 none swap sw 0 0 
/dev/hdc	/media/cdrom0	udf,iso9660 user,noauto	0	0

fstab.pre-uuid


# /etc/fstab: static file system information.
#
# <file system> <mount point> 	<type> 	<options> 	<dump> <pass>
proc		/proc		proc	defaults	0	0
/dev/hda1 	/ 		ext3 	defaults,errors=remount-ro 0 1
/dev/hda3	/home 		ext3 	defaults 	0 	2
/dev/hda2	none 		swap 	sw 		0 	0 
/dev/hdc 	/media/cdrom0	udf,iso9660 user,noauto	0	0

---

### Post by nzadLithium on 2007-12-08
the most likely reason for whats going on is that the line about your home directory

I don't know much about UUIDs so i looked it up in wikipedia.
"The intent of UUIDs is to enable distributed systems to uniquely identify information without significant central coordination."

I think this means that that uuid points to some storage location so it can get the data it needs. So it is possible the data at this location has changed somehow which would stop it mounting your home directory.

What i think you should try is doing sudo mount /dev/hda3 /home
if you get any errors post them here
otherwise goto your home folder and see if it now contains anything.

If it does then this should be fairly simple to fix. Just go into that fstab file again and replace the line that says this
UUID=e66bb58f-1f21-495d-9e74-b8e4fde52d5d /home ext3 defaults 0 2
with
/dev/hda3 /home ext3 defaults 0 2

if that still doesnt work but the mount did then you could try replacing that uuid line then going to /etc/rc.local and put in that mount command there.

---

### Post by Kschikan on 2007-12-08
I tried the mount and it failed with:

error: either /dev/hda3 is already mounted or /home is busy


I tried reverting to the other two fstab files, to no avail, although when rebooting to try one of them (the pre-uuid one) i got the following,

[ some number here ] device-mapper: table: 254:1 linear: dm-linear: Device lookup failed


and this repeated, with the number increasing, until I powered down.

Unless somebody has a fix in the next few days, I'll try reinstalling and relinking my /home folder.

---

### Post by nzadLithium on 2007-12-09
run mount
(just the word mount)

check for anything that says /dev/hda3 or /home
post any line that contains either of those words here.

---

### Post by Kschikan on 2007-12-11
I was having issues with my device-mapper (see previous post) and was having trouble getting a terminal. Being fed up with all of this, I used a LiveCD to reinstall over the root partition, while ignoring my /home partition. After that, I remounted my /home drive and everything was fine. This seems like a good argument for keeping one's /home drive on a separate partition (or drive).

Thanks for all the help.

---

