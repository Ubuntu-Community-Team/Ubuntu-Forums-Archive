---
title: "[SOLVED] Trouble moving /var"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2008-10-07
I'm following [THIS](http://www.gentoo.org/doc/en/articles/partitioning-p2.xml) tutorial for moving the /var directory to another partition and I'm running into a problem

When I get to step "6.1 Backing up the directories"  I type in 
```

root@server1:/# cp var var.old
cp: omitting directory 'var'
root@server1:/#

```


I don't understand why I'm getting the "cp: omitting directory 'var' error.

What I do know is that the operation is not working and I hesitate to progress any further until I get this figured out. 

I tried this out once before and when I ignored it and moved to the next step of creating symbolic links to /var, I would keep creating symbolic links inside of /var (ie: /var/var.lnk would be created)


Please help.

TIA

---

### Post by Braytok on 2008-10-07
try this:
```
sudo cp -R var var.old
```

---

### Post by madhartigan on 2008-10-07
Thanks!!

That got me past that step, now I have to figure out my other issue.

When I create the symlink for /var, it creates the symlink IN the /var directory.

the command is:

ln -s /mnt/rwstorage /var

I run that from / and all it does is create the var link inside the /var directory which is useless for the purpose that I intended.

I'm not sure if I'm supposed to delete the /var directory after creating the /var.old copy but when I try to delete it, I get errors for the /var/run and /var/lock directories saying that the "device is in use" or something.

I'm not sure if I'm supposed to delete the /var directory from a Live CD or not because the tutorial I referenced says you don't since you're running everything from an "init 1"ed terminal as the root.  Evidently that's not the solution for Hardy.

I'll try it from the Live CD, I guess but, I'll keep an eye out for any suggestions as well.

Thanks again.

---

### Post by Braytok on 2008-10-07
If you don't mind my asking, why are you wanting to move your /var directory? there may be another way to accomplish you end goal...

---

### Post by madhartigan on 2008-10-07
eventually var is where I'm going to store my website (ie: /var/www) and I'd like to have all of var (for /var/ftp and /var/mysql as well) stored on my RAID 1 array (md0) which is comprised of 2 mirrored 320GB drives.  

Currently, I have my / installed on a 74GB drive and it's not a RAID.  So, for redundancy purposes and capacity purposes I'd like /var to be on the md0 RAID.  Also, I think that spreading the load across two drives helps in performance.

---

### Post by Braytok on 2008-10-07
AH! I get it.:P

So... If you have not yet set up your website yet, keep in mind that your site files do not have to be in the /var directory. But if it is and your wanting to move it I would do this:

Assuming your drive (md0) is mounted to /media you could simply:
```
 sudo cp -R var /media/md0/
```

This will copy var to your raid array.

you may need to chown it once its copied to read and write to it.

I'm still learning myself so If I'm wrong or some one has a better way please speak up.

Edit:
BTW you most certainly would not want to delete you original /var directory. That would cause some nasty things to happen :)

---

### Post by madhartigan on 2008-10-07
The one issue I run into when trying what you mention is the need to have the system look at the /var mounted on /media/md0 (as you put it) instead of the one originally created during install.

If you read through the tutorial I initially referenced, you'll see that the problem with simply deleting the original /var is that it's constantly in use by the system thereby prohibiting you from deleting the original /var directory.

To get around this, I'm going to try using a Live CD which will allow me to manipulate the /var directory without any troubles. (hopefully :( )

---

### Post by Braytok on 2008-10-07
I was just now taking a second look at the link you supplied, I think the single user mode they refer to is the same as sudo for Ubuntu.

have you tried:
```
sudo ln -s /mnt/rwstorage/var /var
sudo ln -s /mnt/rwstorage/tmp /tmp
``` ?

---

### Post by madhartigan on 2008-10-07
sudo wouldn't matter I was performing the commands as root in the init 1 mode.  I do that to avoid having to type sudo for every command.  It gets a bit redundant when you're the admin.

I definitely only use root for system adjustments and maintenance.

---

### Post by madhartigan on 2008-10-08
still having trouble with this so if anyone can shed some light on what i can do to properly move /var to another drive, I'd appreciate it.

I've tried pretty much everything I've seen on the net (ie: create /var/run and /var/lock in root while still mounting the other drive to /var, etc.)  Honestly, I just don't know what's wrong.  I could just be doing the /var/run  and  /var/lock process incorrectly, but I wouldn't know what I'm doing wrong.


if someone could give me a quick step-by-step, I'd appreciate it.  I've tried this so many different ways that I think I could understand even the most concise break down of the steps.

Thank you!!

---

### Post by madhartigan on 2008-10-08
Sorry for the triple post.


I've solved my problem.

Basically, your best bet is to follow the directions I found in [color=blue][THIS](http://ubuntuforums.org/showthread.php?t=859847)[/color] post.

boot into livecd
move data off of /var to new harddrive using cp -[color=red]ax *[/color]
once data is copied over, move old /var to /var_bk
create new /var with run and lock subdirectories
change fstab to point the new drive to /var
reboot into hard drives

(note the change to the original post's copy command)




One of my obstacles in following this method was mounting my RAID arrays while in the Live CD environment.  Check out [color=blue][THIS](http://ubuntuforums.org/showthread.php?t=408461)[/color] post for directions on assembling pre-existing RAID arrays inside the Live CD environment (specifically section 7).




Another obstacle, once I had reassembled my RAID array was how to mount the root filesystem on my hard-drive and not the volatile root that the Live CD creates in RAM.  I don't have a link for advice on this so I'll do my best to explain it.


**[SIZE="5"]Mounting in Live CD environment[/SIZE]**


Typically, the Live CD allows you to see the system disk as a disk icon labeled with its capacity. My disk showed up as 71.3GB (for a 74GB drive).

I right clicked on that drive and selected "Mount".

This mounts the disk at /media/disk

Once that mount is established, you can get to your hard disk's /var directory by chdir'ing to /media/disk/var.

While doing the move of /var using the Live CD method, be sure that you are mounting the partition to which you're moving var in your /media/disk/mnt directory, NOT /mnt  (I'm not sure that it really matters but it's what I did and I only want to provide advice on exactly what I did because that's what worked)


**[SIZE="5"]How I did it:[/SIZE]**


If it's any help, here are my commands once I had reassembled my RAID array and mounted it at /media/disk/mnt/newvar

[color=red]All actions performed as root.[/color]

```

cd /media/disk/var

```    
(get into the hd's /var)

```

cp -ax * /media/disk/mnt/newvar 

```
(copy the contents of /var to the new partition. Substitute /mnt/newvar with whatever you chose to mount your partition on.)

```

cd /media/disk

```
(go back to the hd's / )

```

mv /media/disk/var /media/disk/var_old

```
(this essentially removes the /var directory and creates its backup at the same time)

```

mkdir /media/disk/var
mkdir /media/disk/var/run
mkdir /media/disk/var/lock

```
(these steps create the /var directories that Ubuntu requires to still be on the root drive)

```

gedit /media/disk/etc/fstab

```
(now edit fstab to always mount /var to your new /var partition.)



That's it.

As always I don't guarantee these steps, but I do provide them with the caveat "User Beware".  Make sure you've researched this process beyond simply following these directions before you actually go and do it.

Also keep in mind that you create /var_old in this process which you can always "mv /var_old /var" in order to re-establish the original /var.




I'm very happy to have finally conquered this puzzle.  Hopefully this post will help someone else.

---

