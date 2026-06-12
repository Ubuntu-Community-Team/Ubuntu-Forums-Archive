---
title: "ubuntu 12.04LTS - trying to auto mount mdadm RAID0 2 disk array"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by john153 on 2014-01-31
I"ve recently built an Ubuntu 12.04LTS box and it has been running great so far. I am a relative novice regarding unix. But I do have basic unix terminal use experience. I"ve attached a txt file with my system config which I got by entering gksu lshw-gtk.

I've built a two drive RAID 0 using the alternate install software I downloaded from the Ubuntu site. I created a RAID0 array and am able to mount the 2 drive array using mdadm by opening drive utility and choosing the array and mounting. 
I want to have it mount automatically at startup but can't seem to make it work. 

I tried editing my etc/fstab file and adding it but the machie errors on startup. 

I tried both uuid and mount point. Here is what I tried last in etc/fstab

/media/minecraftserver /dev/md0 ext4 default 0 0
This is the info I get from the drive utility once the drive is mounted

I opened the fstab file by entering in terminal:
gksu gedit /etc/fstab

Anyone see what I'm doing wrong? Or am I going about this in the wrong way? 

Thanks!

john

---

### Post by TheFu on 2014-01-31
I think you are close .... just a few things backwards. Try
```
mkdir /mnt/minecraftserver
/dev/md0 /mnt/minecraftserver  ext4 default 0 0
```

You do understand how very dangerous RAID0 is, correct?  It is suitable only for video editors who need performance and never store anything on the array more than 24 hours. If either drive dies, all the data is gone - lost - unrecoverable.  I suppose excellent backups can mitigate some of this, but every time I've come across RAID0 in the wild, they weren't doing good enough backups.

Is md0 really the RAID device?  Please post as in "copy/paste" the contents of /proc/mdstat here. Use the "Adv Reply" and "code" tags please so everything lines up.

**man fstab** should completely explain the format of the /etc/fstab file. The "mount point" must exist prior to the mount being requested to work - /media is a BAD location to use for this since this location is always used by dynamic mounts.  I avoid /media and /mnt - in my mind, those are for temporary storage only.  I use autofs and /D/ for other mounts that aren't needed in specific locations like /opt, /var, /home ... 

Anyway - hope this helps.

---

### Post by john153 on 2014-02-01
TheFu! Thanks for the help! below is the /proc/mdstat file. I hope I pasted it properly. 

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdb1[1] sda1[0]
      498043904 blocks super 1.2 512k chunks

unused devices: <none>
                                                          

```

I do understand RAID0. I have a samsung ssd with my operating system installed. And the RAID0 is for the minecraft server for my son and friends. That's the only thing on the RAID
I am using the Ubuntu Backup application to backup the server directory to an internal barricuda 2TB I had laying around. How does this sound? I also assumed that because the RAID0 is on SSD's, drive failure would be mimized. 
Do you think I am getting a measurable speed boost by RAID0ing these drives? Or might I be creating more headache than it's worth? 

Anyhow. Would I substitute /mnt for /D in the code you gave me? As in:

```
mkdir /D/minecraftserver
/dev/md0 /mnt/minecraftserver  ext4 default 0 0
```


Yours, 

John

---

### Post by TheFu on 2014-02-01
Run the mkdir - from a shell first. Use sudo, then chown to whatever userid you want to be owner/group.

The /dev/md0 line is for the /etc/fstab and needs to match the new directory:
```
{device} {directory} {filesystem type} options1 options2 options3
```

Sorry that wasn't clear. I'm not too good at remembering everyone else doesn't have 20 yrs of experience doing this stuff.

RAID0 on SSDs ... hummm ... SSD is too new for me to consider using. Perhaps in 5 more years, after all the failure modes are well-known.  I'm extremely cautious with data. It is more important than the hardware most of the time. I can't imagine needing RAID0 performance on a game server, unless it had thousands of paying users.  You've already allocated part of the SSD for mindcraft?  I wouldn't waste the SSD for that, but I don't game at all.  Do what you think is best.

---

