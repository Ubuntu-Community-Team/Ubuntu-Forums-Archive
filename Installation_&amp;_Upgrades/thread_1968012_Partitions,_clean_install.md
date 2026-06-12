---
title: "Partitions, clean install"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2012-04-28
I like to do clean installs when I upgrade. I currently have three partitions:
```

/     15 GB
/home 65 GB
/swap  2 GB

```
I plan to create a separate partition /usr/local for installing outside software. (For example, the latest texlive.)

In addition, Ubuntu documentation suggests separate partitions for usr, var, and tmp. This would lead to (sizes yet to be determined):
```

/
/usr
/usr/local
/var
/tmp
/home
/swap

```
Several questions:
1. Is du -sh a good way to assess how much disk space is being used for each of these directories in my current (11.10) installation so I can come up with sizes for my new partitions?
2. During a new clean installation, which of these directories must be rewritten? For example, I know that the installer does not need to change /home.
3. What are the advantages to having separate partitions for /usr, /var, and /tmp? I understand the reason for a separate /home and /usr/local.
4. If I shrink my current /home partition to pick up space for the new /usr/local partition, am I likely to lose data there? df shows 17G of the 65G currently in use, and I don't anticipate using much more.

This is a home computer, not a server. What I have now (the three partitions) has been working quite well for several years, but I would like to learn more about this.

Yes, I will be very careful to back everything up before I start this adventure. I've learned this the hard way several times in my life. ;)

-Bob

---

### Post by darkod on 2012-04-28
There should be no data loss when you shrink /home. Of course you will need to do it from live mode and backup your data first just in case. :)

You can add /usr/local but I don't see much point in making /usr, /var and /tmp separate partitions. That is more for servers I think. For example, the logs go into /var/log and on servers sometimes you would want that separate and under control.

Google for more details but I don't think it's worth the bother on a desktop system.

---

### Post by oldfred on 2012-04-28
As Darko says the old info on separate partitions is more for servers and where you may need to isolate different tasks. When I installed Redhat 12 years ago, it really was more of a server install with a gui and I had to create all those partitions separately. Now Ubuntu just has / (root) and swap and not everyone even thinks you need swap separate.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I do like to separate system from data, but that is my own preference.

---

### Post by rplantz on 2012-04-28
Thank you, Oldfred and Darko, for your very interesting comments and the link to Herman's comments. I especially appreciate your differentiating between desktop and server machines. Many contributors assume that everyone else is running a server or wants to do gaming. I use my machine for everyday stuff (email, surfing) and programming.

This has caused a 180 in my thinking. I've kept /home on a separate partition so I can do clean installs when I upgrade, but I only do that on my desktop. I've simply done upgrades on my laptop for the past several releases, and that has worked quite well.

At this point I'm inclined to switch to a single partition per Herman's suggestions. Then if I do upgrades instead of clean installs, I won't have to worry about /usr/local. As Herman says, it all sounds a lot simpler. I like simplicity.

I use an rsync script to backup /home on an external disk, so the switch should be fairly easy.

-Bob

---

### Post by oldfred on 2012-04-28
As I mentioned my preference is to keep system separate from data. With my new SSD I have all the system on the SSD, no swap, but my data partitions are on my rotating drives. I mount data in /mnt and link all the folders into /home so it looks like a normal install.

With several drives I want to keep each drive bootable with MBR, & all boot and system files including the hidden user files in /home on that drive. Then if any drive fails I can fully boot another, it just some of my data may then not mount correctly but hopefully that is backed up.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive, so I have a system on every drive. (I do have Knoppix as a repair ISO if need be.)

---

### Post by rplantz on 2012-04-28
> **oldfred said:**
> As I mentioned my preference is to keep system separate from data. With my new SSD I have all the system on the SSD, no swap, but my data partitions are on my rotating drives. I mount data in /mnt and link all the folders into /home so it looks like a normal install.


By "data partitions" do you mean /home? Are there others?

-Bob

---

### Post by zdeuyo on 2012-04-28
Hello,

This should fix it.

Here is the link

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Follow the instructions exactly on that page.

---

### Post by oldfred on 2012-04-28
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by rplantz on 2012-04-28
> **oldfred said:**
> I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

Aha! It's finally sinking in. I was getting confused about what is considered "data." Neat way to do things. I will probably get an SSD before too long and have been thinking about ways to keep my personal data on the mag disk while the system stuff is on the SSD. You've answered my questions.

-Bob

---

### Post by silencej on 2012-06-27
Interesting! I am also considering creating a separate partition for /usr/local and doubting that fresh Ubuntu re-install may overwrite it.

Bob: Have you tried on this and does it work? Same and easy as an independent /home partition?

> **rplantz said:**
> I like to do clean installs when I upgrade. I currently have three partitions:
```

/     15 GB
/home 65 GB
/swap  2 GB

```I plan to create a separate partition /usr/local for installing outside software. (For example, the latest texlive.)

Bob: Have you tried on this and does it work? Same and easy as an independent /home partition?

In addition, Ubuntu documentation suggests separate partitions for usr, var, and tmp. This would lead to (sizes yet to be determined):
```

/
/usr
/usr/local
/var
/tmp
/home
/swap

```-Bob

---

### Post by silencej on 2012-06-27
Sorry for duplication. Don't know how to delete...

---

