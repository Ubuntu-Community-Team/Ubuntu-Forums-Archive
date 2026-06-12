---
title: "The time has come to get rid of windows"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by roger99 on 2006-09-17
This is gonna be a kinda comment and question all rolled into one so I hope I've posted in the right place. Here goes and I'll try not to make it too long and boring :)

I've been a PC nut for about 16 years now so my roots were established in the good old DOS days when the command line was everything you had and everything you'd ever need.  Back then I was a tinkerer and would spend hours fiddling, customising etc.  Even then I used an alternative DOS, I can't remember what it was called off hand but suffice to say it wasn't by MS.  I used to love to code and was even writing my own win 3.1 alternative (it was rubbish and I never finished it but it was showing potential if given lots (read lots and lots and lots) of time.  But then win95 happened and somehow I kinda got sucked into it.  But it was strange, in the days of DOS i practically knew every file on my system (then again I did only have a 20MB hard drive) and what relevance it bore, with the event of 95 that just seemed to disappear.  I've tried to tinker and customise on all the win OS's but it really doesn't seem to work very well, you can do it but everything slows to a nasty unusable speed and then you go back to the norm.

Five or six years ago I managed to get hold of a Linux distro, again I can't remember which one, and with a fair deal of excitement installed it onto a new partition.  Bearing in mind I didn't even have dial-up back then and everyone I knew ran MS software, I was pretty much on my own.  Surprisingly enough a few cockups and a few reinstalls later I gave up and gave the space back to windows.

Fast forward to now, and I've got myself broadband, and my thoughts return to Linux and it's supposed power and flexability.  I have a look around and decide to download suse 10.0.  A while later it's itstalled on my now empty 80gb drive while windows sits happy on the other and it's booting for the first time.

A few weeks later and I'm kinda settling in, i'm getting really accustomed to GNOME's desktop and although a lot of people would balk at me for saying this, I'm loving the use of the command line again.  Although the commands are still a bit alien i'm learning and it's all good.  One thing that really didn't go well though was trying to use YasT and it's crappy software management.  After coming from windows trying to install software through it was an absoloute nightmare,  with it's massive daunting looking conflict and dependancy lists.  And I nearly gave up again, but I had used it for a while now and could see it's potential so decided to try another distro.

Thats when I found out about Ubuntu and I have to say i'm very, very impressed.  It didn't set itself up for my hardware as well as suse but I'm actually happy about that as I have had to find my way around it to get it setup properly.  Now most things work, except my Nebula DigiTV card, which i'm looking at as a work in progress!.  I've started customising with xgl+compiz and i've got things like VMware server and samba running plus all other essentail software that I can think of.

I've also discovered a happy, helpfull community of like minded people in this forum, and although I've only posted two really dumb, total noob, questions I look forward to when I'm knowledgable enough to be able to help people out myself.

Now here comes the question that this entire post has been leading up to.

I want to make my 250gb drive (the one that currently holds windows) my main ubuntu drive.  I would like to partition the drive to create a more effecient easily recoverable setup.  This is where my plan comes unstuck.  I realise I will want a sizeable /home partition.  But what about the rest of the possible mount points.  How many partitions should I make, do, ideally, i want to mount things like /etc /usr /root /bin /dev all as seperate partitions or is this overkill?  If i do ideally want to create all these partitions what sort of rough size's should I make them.  And would transferring the system i've created be as simple as just copying the files from my current installation to the corresponding partitions or would a reinstall be in order.

Any suggestions or maybe examples of other peoples setups would help me make up my mind on how to organise my drive.

Well thats about my lot, sorry for waffling but I got there in the end ](*,)

---

### Post by kidders on 2006-09-17
Hi there,

The short answer to your question about partitioning is that, like Windows, people don't tend to use more than one unless there's a reason for doing so. For instance, tinkering with your registry to make, say, E:\ your "Documents and Settings" folder is the equivalent of creating a separate /home partition. Commonly, people do this to share files between multiple operating systems, retain personal data between OS reinstallations, or increase the amount of space available to personal files.

Basically, partition schemes tend to be designed for practical or performance reasons, and each one is different, depending on the individual needs of the user.

Any help?

Another reason for creating extra partitions is the opportunity to use more than one filesystem format on your computer ... something that is really only applicable to high-end servers. ReiserFS, for instance, delivers extraordinary performance on partitions full of millions of tiny little files, a feature that is not universally applicable to an entire operating system. Other motivations are more safety-oriented; for instance, you might choose to isolate your /boot in a partition on its own. By leaving it dismounted most of the time, you don't run the risk of accidentally botching it up and rendering your PC unbootable.

---

### Post by roger99 on 2006-09-17
I suppose i could of shortened that question to "Would I gain anything by partitioning by drive for a fresh install of Ubuntu." Would have been a lot easier to read, eh :D You have also answered another question I meant to ask and that is what is the difference between ext3 and reiser.  Cheers for the words of advice

---

### Post by kidders on 2006-09-17
Hehe! Your post was an interesting read :-)

The difference between the Extended filesystems and ReiserFS is far more involved than the performance issue I mentioned, btw. Other common choices include HFS, JFS and XFS, all of which behave slightly differently, and have their own unique charm (lol).

I'm glad my ramblings were of some use!

---

### Post by karamba_kid on 2006-09-17
I use logical volume management (LVM).  It's laid out like this.

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg0-root  7.9G  370M  7.2G   5% /
varrun                252M  120K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  156K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M 8% /lib/modules/2.6.15-26-386/volatile
/dev/hda1             177M   22M  146M  14% /boot
/dev/mapper/vg0-home   75G   31G   41G  43% /home
/dev/mapper/vg0-tmp   1.9G   34M  1.8G   2% /tmp
/dev/mapper/vg0-usr    22G  2.3G   19G  11% /usr
/dev/mapper/vg0-var   3.0G  300M  2.6G  11% /var

---

### Post by roger99 on 2006-09-17
Thanks, i'm gonna have a read up on LVM tomorrow when I can keep my eyes open  and I'll post back here if i have any queries about your particular setup, or how to proceed.

OK maybe just a couple of questions before I toddle off to bed.

```
varrun 252M 120K 252M 1% /var/run
varlock 252M 0 252M 0% /var/lock
devshm 252M 0 252M 0% /dev/shm
lrm 252M 19M 234M 8% /lib/modules/2.6.15-26-386/volatile
```

What is the particular importance of these points that they would deserve their own partitions.  Sorry if that seems like a daft question but, hey, i'm new to this linux stuff.

---

### Post by daxelrod on 2006-09-17
You might find the [Linux Partition Howto]("http://www.tldp.org/HOWTO/Partition/") helpful.

---

### Post by kidders on 2006-09-18
Hi again,

These partitions aren't used by all Linuxes. tmpfs filesystems can be handy though, in that they are stored in RAM (ie you won't find them on any of your disks). This can be a nice way of vastly increasing I/O response times ... assuming of course you have a decent amount of memory!

---

### Post by anil_robo on 2006-09-18
During the Ubuntu installation process, I simply selected the option "select and use entire hard drive for ubuntu" and it works great! Why don't you do the same? It also creates a swap partition for you! :D

---

### Post by roger99 on 2006-09-18
Right, multiple replies in one I think.

The Linux Partition How-To seems like it may be exactly what i'm looking for.  I'm gonna give it a good read after dinner! :D 

The tmpfs filesystem sounds interesting as well, i'm gonna do some research on that.  I have 1gb of ram so I may consider this if it really seems relevant to my setup.

As for the one partition standard installation, this is how my current setup is now and when I move Ubuntu to the big drive I'd like to change this.  I've allways had a thing about partitioning drives, I suppose I don't really like to keep all my eggs in one basket so to speak!

Anyways I've got some reading to do so thanks to all!

---

