---
title: "Edgy to Feisty upgrade, gone horribly wrong, messed up my computer!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by goodbyewindows on 2007-04-20
I upgraded Edgy to Feisty using the update manager, seemed fine (took 2 hours, but i had time). Now when I boot ubuntu, it shows the loader bar, but then text appears on the screen:
```

 * Checking file systems
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3 No such file or directory while trying to open /dev/hda4
/dev/hda4
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really does contain an ext2 
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 0
[fail]
* file system check failed
A log has been saved in /var/log/fsck/checkfs if that location is writable.
(or type Control-D to continue):el and resume system boot

```
I think I remember mounting /dev/hda4 to my /home directory.
Anyway when I press Control-D, the screen goes black. I then press Ctrl-Alt-F1 to get to a prompt. It tells me it cant finds /Home so its using the root directory. when I ls /Home, nothign is there!
Help please!

---

### Post by heimo on 2007-04-20
I'd try:
```
sudo e2fsck -b 8193 /dev/hda4
```And if that goes well:
```
sudo mount -a
```

---

### Post by goodbyewindows on 2007-04-20
> **heimo said:**
> I'd try:
```
sudo e2fsck -b 8193 /dev/hda4
```And if that goes well:
```
sudo mount -a
```
that doesnt work, it just returns the same error message about superblocks

---

### Post by goodbyewindows on 2007-04-20
Edit: nonsense

---

### Post by alanjcfs on 2007-04-21
Strangely, I had the same problem, but I had a different hard drive to hold my /home partition. Usually, that takes hdb1, but mounting filesystem couldn't find /dev/hdb1. After some investigation, i saw that there was no hda in the /dev directory. I found that there was an sda device.

Working from a hunch, I decided to "mount -t ext3 /dev/sdb1 /home", and it worked. I could go into /home and find all my files there.

So then, I went into /etc/fstab with nano and changed the line from /dev/hdb1 to /dev/sdb1. Then I pressed Ctrl+D.

I think you could try "mount -t ext3 /dev/sda4 /home" and see if it works. I'm not sure why this upgrade switched from hda to sda. I upgraded from Dapper to Edgy, which created the UUID.  I decided to create a separate /home partition, which resulted in me using /dev/hdb1 rather than a UUID. I guess in the upgrade from Edgy to Feisty, the installer wasn't equipped to handle that scenario.

---

### Post by goodbyewindows on 2007-04-21
I followed the instructions of someone on the IRC channel, now I don't have the error message about sda4, but after booting, the screen goes black, the last thing it loads is "* Starting Local Boot Scripts (/etc/rc.local) [OK]"

---

### Post by dannyboy79 on 2007-05-10
> **goodbyewindows said:**
> I followed the instructions of someone on the IRC channel, now I don't have the error message about sda4, but after booting, the screen goes black, the last thing it loads is "* Starting Local Boot Scripts (/etc/rc.local) [OK]"

OH MY GOSH!!!!! Thank gosh I found this thread!!!!! I installed Fiesty from Scratch. I had dapper for a long time, then I thought, I want to save all the settings and programs that I had installed along the way so I did an upgrade to Edgy, it seemed to have gone ok, but then when I tried to update to Fiesty I kept getting  failures regarding many different things.

So I said forget it, I used a script I found in the internet which basically used dpkg and it asked me if I wanted it to show me the libs, and a bunch of other stuff, then at the end it asked for a filename, I named it installed packages and that created a file wjhich had a nice list (1 column) of all the packages that I had installed since I installed dapper. this is great, now I could do a fresh install and then use that list as "input" using apt-get to install all of them again after the fiesty install. I also have always had my /home partition seperate for changing verisons of ubuntu as well. ANyway, everything went fine, fresh install and I used my old home partition. I did a bunch of stuff for a couple of hours, restarted about 3 times, then the last time I did a restart the system needed to run fsck, well I got the error listed above, fsck died with exit status 0. then it came to login and it stated that it couldn't find home and it asked if I wanted to use / in it's place. I thought, what???? so I shut her down and was going to run a live cd to see what's up and possibly back everything up if need be (maybe the drive is dieing?) 
Unfortunately I had to go to work so I have been kind of freaking out about this since I wasn't able to resolve it right away, I hate it when my baby is out of commission for even a little amount of time. 

So i ahve been gogling this all morning and found this!! hopefully it works. i have seen many threads about fiesty changing all ide device id's from the hdX to sdX but most of the people sstated that this only happened when they did an upgrade, but I did a fresh install so I am not sure about this solution? also, I don't really like the fact that I was able to restart over and over and didn't have a any rpblems but all of a sudden since the system wanted to run fsck and it died, that my home is gone? like I said, I hope this is the solution if not, it'll be time for dd-rescue to see what I can salvage.

---

### Post by HaxTbh on 2007-05-22
I keep getting errors like this. I have noticed that my /home partition is mapped by /dev/mapper/sda3 instead of /dev/sda3. Could this have something to do with it.
Also it just shows the UUID in the fstab, would it be better to change these to a /dev/sdaX (X is number of partition)

---

### Post by dannyboy79 on 2007-05-22
what's weird is that htis happens to me after everytime the fsck is forced upon boot up after 30 mounts. what I have to do is shut down the machine after the fcsk runs, then restart and everything is ok. I am going to remove the uuid's and just use the device locations and see if that helps. at least all I have to do is restart to fix this, I am not sure what you guys do to resolve this.

---

