---
title: "dual boot question"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by stlcoptony on 2007-10-04
I looked around with the search function and could not find an answer. If I missed it, someone please point me in the right direction. I am trying to install ubuntu 7.04 on my laptop without messing up the windows install. I am in the middle of the installer right now. What is the safest way for me to keep the windows install and still install ubuntu? Can ubuntu recognize NTFS? If so I would like all the file storage areas to be NTFS so I can see them with windows (have linux on the home computer too, windows doesn't even see the hard drive that ubuntu is installed on!). Any help/suggestions would be appreciated

thanks,
tony

---

### Post by Sef on 2007-10-04
Read Psychocat's [installing.]("http://www.psychocats.net/ubuntu/installing")

---

### Post by stlcoptony on 2007-10-05
I found a site that recommended defragmenting the hard drive that you will be partitioning until all the files are on the left side of the bar? is this necessary? Also does anyone know how safe the partitioning is?

thanks,
tony

---

### Post by oilchangeguy on 2007-10-05
> **stlcoptony said:**
> I found a site that recommended defragmenting the hard drive that you will be partitioning until all the files are on the left side of the bar? is this necessary? Also does anyone know how safe the partitioning is?

thanks,
tony

yes
and yes it's safe
but backup your data BEFORE you attempt to install ubuntu. if something does happen, you'll still have your data intact.

---

### Post by stlcoptony on 2007-10-05
what if I cannot get all the bars (files?) on to the left side? I have done it MANY times and there is a large bar that will not move.

thanks

---

### Post by oilchangeguy on 2007-10-05
> **stlcoptony said:**
> what if I cannot get all the bars (files?) on to the left side? I have done it MANY times and there is a large bar that will not move.

thanks

they probably won't all move. the green bar is not movable.

---

### Post by Herman on 2007-10-05
I'm not too sure if it's an important issue these days or not.
The partman partitioner in the 'Alternate' CD used to refuse to touch a Windows partition sometimes if there was data in the way. That's why I still recommend defragmenting Windows before partitioning when installing Ubuntu with the 'Alternate' CD.

[Geek Girls]("http://www.geekgirls.com/index.htm") website has the best how-to I have seen to help you make Microsoft utilities work properly. Look under '[windows guides]("http://www.geekgirls.com/menu_winguides.htm")'-->'[ windows tools & techniques]("http://www.geekgirls.com/menu_windows_techniques.htm")',-->'[   why defrag?]("http://www.geekgirls.com/windows_defrag.htm")', and see especially where it explains [step by step: efficient defragging]("http://www.geekgirls.com/windows_defrag.htm#efficient"). I use this method all the time for running either scandisk or defrag.  It really works great! (And saves a lot of time too).

That immovable green bar you can see is a thing called a 'page file'. It's kind of equivalent to our swap partition in Linux, as in it's a kind of like 'fake' memory. It's for when your real memory is getting a bit full. It's kind of a 'slow lane' for memory. It works by writting slow moving memory stuff temporarily to the hard disk  leaving your real memory available for the 'fast lane' stuff. 
  If you want to get that out of the way before defragging the partition, just turn it off in 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change', [COLOR=#ff0000]take note of your settings[/COLOR] (on a piece of paper), and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.
Then restart your computer and now you can run defrag as many times as you need to, without the big green block in the way.
   (*If you do this, don't forget to go back and turn it on again later, after the resizing is over, and Ubuntu is installed*).

Since the development of GParted, it is no longer necessary or important to defrag Windows first. GParted can do the job just as well regardless of defragmentation, so if you are using the Ubuntu LiveCD to install with, (that would be most people these days), you won't need to waste your time defragging Windows. GParted will handle it.

Regards, Herman :)

---

### Post by stlcoptony on 2007-10-05
one more question (hopefully) for you guys. If I partition the hard drive have a windows partition, a linux (ext3) partition, a swap partition, and a shared partition, is it now ok to make the shared partition NTFS? I have heard that there is a read/write driver for that file system now. Also, using this basic partitioning scheme, could I later install other distros over ubuntu without having to repartition?
thanks for the help,
tony

---

### Post by Herman on 2007-10-06
> one more question (hopefully) for you guys. If I partition the hard drive have a windows partition, a linux (ext3) partition, a swap partition, and a shared partition, is it now ok to make the shared partition NTFS? I have heard that there is a read/write driver for that file system now. Yes, you can have an NTFS shared data partition. I have been using NTFS support from this how-to [Windows NTFS Partitions Read/write support made easy in Ubuntu Feisty]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html"). I have had t for a long time now and haven't had any trouble with it at all.

> using this basic partitioning scheme, could I later install other distros over ubuntu without having to repartition? Yeah, you can if you want, I can't think of any problems with doing that.

I have sampled a few different distros already myself. I usually install them alongside Ubuntu though. The most noticeable difference for the average user would be the desktop, (whether the distro uses Gnome like Ubuntu, KDE like Kubuntu, XFCE like Xubuntu, or Fluxbox like Fluxbuntu, or some other desktop. 
In Ubuntu you can install all those desktops at once if you want to, and choose which one you'd like to boot into at the login screen.

Another difference between distros is the way that added software and upgrades are installed. I think Ubuntu would score very highly there, we have active developers who are right on the ball and up to date with the latest software and security updates. We can add new software by apt-get, add/remove programs (off the 'Applications' menu), or through synaptic package manager. All those are easy to use. And we get updates frequently. 

Mostly you'll find the software itself very similar, there wouldn't be very much difference in Open Office.org between various distros running the Gnome desktop, or in KOffice between different distros running KDE for example. 

Another thing most people would like is our Web Forums, I think ours is the best. I also like Debian's web forum. If you want to do a tour of lots of different distro's web forums to see what they are like (freindly or not, informative or otherwise), try going to [DistroWatch.com]("http://distrowatch.com/") and find the links to other web forums there.
It's fun to browse other distros forums and it's often possible to learn a few different tricks and tips that can help Ubuntu users as well.

Anyway, the main thing is to have fun, so go ahead and try out as many diifferent flavors of Linux as you can. 

Regards, Herman :)

---

### Post by stlcoptony on 2007-10-06
thanks everyone. This is indeed one of the best forums I have used (probably tied with the mepislovers forum). The reason Ubuntu would be replaced on my computer mentioned above is that it is my laptop (actually a tablet pc -- any support for this?) I have ubuntu, mepis, and sabayon installed on my home computer. 

thanks,
tony

---

### Post by stlcoptony on 2007-10-06
also, I have ubuntu up and running on the laptop now. It is currently trying to download the 122 updates... at @20-30 kB/s. Does anyone know why this is going so slow?

---

### Post by stlcoptony on 2007-10-06
bump - sorry but the wireless speed is the only thing keeping me from making this an ubuntu-only computer

thanks

---

### Post by Herman on 2007-10-07
I wish I could help you there, stlcoptony, but networking isn't really my strongest field. Maybe you should make a new post in the Networking & Wireless section of this web forum and see if you can attract the attention of a networking whiz? :)

Here's how I found  out how to get my laptop's wireless card going, [Setting up my Acer Aspire Notebook for Wireless Networking in Ubuntu]("http://users.bigpond.net.au/hermanzone/p11.htm#wireless_network_configuration")

Regards, Herman :)

---

