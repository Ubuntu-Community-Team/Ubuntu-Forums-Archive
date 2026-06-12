---
title: "The woes of an older machine. Tried multiple distros to no avail."
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by MikeonTV on 2008-08-09
I'm trying to install on an older machine. It used to run Windows 2000 on a 10 GB HD and has 768MB RAM. I had an old 60GB hard drive that I formatted and partitioned using the gParted disk

This is where the excitement begins. 

I started by thinking that Xubuntu would be the best option for a machine of this caliber. I began getting install errors when trying the alternate Hardy Heron disk. After trying different alternate disk I gave up on Xubuntu.

I have a live CD of Feisty Fawn and Hardy Heron (both Ubuntu) and figured that I might as well give it a shot. Again errors came up during the 'installation' process. Things like "errno 5 input/output error". 

So I've given up on that disk. On to the Feisty Fawn Live CD. Well this install works. It go to 100% and then the installation process just ended. I was left with the normal brown background and options I had when inserting the disk. 

So I restarted and it tells me "Error loading operating system".

I searched and found [this solution]("http://ubuntuforums.org/showthread.php?t=224351") but have not tried it (I'm away from that machine for the morning). 

Could it be anything else? Did I make a mistaking when formatting/partitioning the HD? Was this machine not destine to hold such a beautiful operating system concept? 

Thanks.

---

### Post by meindian523 on 2008-08-09
Did you check the CDs for defects?md5 sums?It's unlikely that all your downloads were bad,but it's not unheard of.

---

### Post by Zill on 2008-08-09
I run Xubuntu on a 500MHz PC with 312MB RAM and a 10GB hdd so I guess your spec is quite adequate.

Does the Xubuntu live CD run correctly?  If not then I suggest you fix that first - report any problems here if necessary.

Then, assuming you are not trying to dual-boot with Windows, I suggest that you click on the "install" icon and let Xubuntu repartition the entire disk, then proceed with software installation.

As meindian523 suggested, it is quite possible that your CD may be bad - the live CD should help identify this.

I think you might have problems getting Ubuntu to run on your machine due to the limited spec - Xubuntu would be a better option.  However. someone may prove me wrong on this :-)

---

### Post by MikeonTV on 2008-08-09
Well as I stated before I have tried three installs with three different discs. I dont think it is the software. I believe I made mistakes partitioning the drive. 

I opened gparted and deleted any partition then I created a partition (using 100% of the drive) But I just choose the first option (ext2, ect) when doing so. What specs do I have to make the drive to run ubuntu?

---

### Post by mikjp on 2008-08-09
Sometimes trying another distro magically helps ;-) Why not try Vector, Zenwalk, Debian or Slackware?

One of my old PCs does not read CD-RWs, only CDRs. Could this be the reason for failures in your case?

Use ext3 rather than ext2. It is better :-)

mikko

---

### Post by Zill on 2008-08-09
> **MikeonTV said:**
> ... I believe I made mistakes partitioning the drive...

You don't need a separate disk for partitioning.  When you click on the install icon on the Xubuntu live CD desktop this will automatically start the built-in partitioner.  If you select the "entire disk" option and accept the defaults this should partition and install Xubuntu correctly.

It is useful to have a separate "/home" partition but this would require some manual intervention with the partitioner.  It is therefore easier to just use the defaults for now :-)

BTW, does the Xubuntu live CD run correctly - if not then it can't install!

---

### Post by MikeonTV on 2008-08-09
I have not attempted the Xubuntu Live CD but have (to no avail) with two different released of the Ubuntu Live CD.

thats why I think it's a partition problem

---

### Post by Zill on 2008-08-09
> **MikeonTV said:**
> I have not attempted the Xubuntu Live CD but have (to no avail) with two different released of the Ubuntu Live CD.

thats why I think it's a partition problem
My comments apply equally to the Ubuntu partitioner - it is the same system.  If you let the OS partitioner do the work then it should be partitioned correctly. :-)

If the Ubuntu/Xubuntu live CD doesn't run properly then you won't get very far with installation.

I still believe the requirements for Ubuntu, rather than Xubuntu, may be too great for your machine.

---

### Post by MikeonTV on 2008-08-09
> **Zill said:**
> My comments apply equally to the Ubuntu partitioner - it is the same system.  If you let the OS partitioner do the work then it should be partitioned correctly. :-)

If the Ubuntu/Xubuntu live CD doesn't run properly then you won't get very far with installation.

I still believe the requirements for Ubuntu, rather than Xubuntu, may be too great for your machine.
In that case, what linux distro can I put on the machine? DSL?

---

### Post by Zill on 2008-08-09
> **MikeonTV said:**
> In that case, what linux distro can I put on the machine? DSL?
DSL is a good distro and you may like to try that - I keep it as a handy live CD.

However, if you want all the bells and whistles of an Ubuntu based system then I do suggest you try Xubuntu as I discussed earlier.  It *should* install and run on your PC.

---

### Post by MikeonTV on 2008-08-09
> **Zill said:**
> DSL is a good distro and you may like to try that - I keep it as a handy live CD.

However, if you want all the bells and whistles of an Ubuntu based system then I do suggest you try Xubuntu as I discussed earlier.  It *should* install and run on your PC.

So could I get 8.04 (HH) in Xubuntu or 6.06 a better idea, or does it not matter?

---

### Post by Zill on 2008-08-09
> **MikeonTV said:**
> So could I get 8.04 (HH) in Xubuntu or 6.06 a better idea, or does it not matter?
6.06 (Dapper) is the old LTS (long term support) version.  While this is still (just) supported, it has been superseded by 8.08 (Hardy Heron).

8.08 is the current LTS version and has many improvements over 6.06.  Unless you have a specific reason to want an old distro then I suggest you install Xubuntu 8.08 - it should run quite happily on your PC.

---

### Post by MikeonTV on 2008-08-09
> **Zill said:**
> 6.06 (Dapper) is the old LTS (long term support) version.  While this is still (just) supported, it has been superseded by 8.08 (Hardy Heron).

8.08 is the current LTS version and has many improvements over 6.06.  Unless you have a specific reason to want an old distro then I suggest you install Xubuntu 8.08 - it should run quite happily on your PC.

I'm downloading the top option on this page right now. 

[http://mirror.csclub.uwaterloo.ca/xubuntu-releases/8.04/release/](http://mirror.csclub.uwaterloo.ca/xubuntu-releases/8.04/release/)

hope it's the right one then.

---

### Post by Zill on 2008-08-09
> **MikeonTV said:**
> I'm downloading the top option on this page right now. 
[http://mirror.csclub.uwaterloo.ca/xubuntu-releases/8.04/release/](http://mirror.csclub.uwaterloo.ca/xubuntu-releases/8.04/release/)
hope it's the right one then.
Looks fine to me - assuming you have a "normal" PC, not AMD ;-)

---

### Post by meindian523 on 2008-08-09
I'm running Ubuntu 8.04 on a 512MB RAM system and it works fine.Xubuntu might save you RAM but I doubt it's useful in reducing the stress on your processor.Though,someone may prove me wrong here.BTW,the Live CD says and I quote "You need a minimum of 384 MB RAM and 5 GB space on your HDD to install the system" in so many words.Your RAM is more than adequate.

---

### Post by mikjp on 2008-08-10
> **MikeonTV said:**
> In that case, what linux distro can I put on the machine? DSL?

Zenwalk, VectorLinux, Debian, Slackware or some other distro mentioned in my [blog posting about lightweight distributions.](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

mikko

---

### Post by robert shearer on 2008-08-10
just a couple of things to check...  Open up your machine and check that the h/d you are installing to is set as Master on the first ide channel.
If you have just the one h/d plus the cd drive then have the cd drive set as Master on the second ide cable.
 
The hard drive should be connected with an 80 wire ide cable. The cd can be used with an older 40 wire cable.

Use the gparted cd to Wipe the hard drive- this may take a while - Then try installing xubuntu or ubuntu (using the default partitioning when you reach that stage.)

If problems persist there may be damaged sectors on the h/d. Try above first.
Posted using celeron 1ghz cpu/ 512Mb ram running Ubuntu hardy. Not fast but works well for day to day use.  Hope this is of use.

---

### Post by MikeonTV on 2008-08-10
> **robert shearer said:**
> just a couple of things to check...  Open up your machine and check that the h/d you are installing to is set as Master on the first ide channel.
If you have just the one h/d plus the cd drive then have the cd drive set as Master on the second ide cable.
 
The hard drive should be connected with an 80 wire ide cable. The cd can be used with an older 40 wire cable.

Use the gparted cd to Wipe the hard drive- this may take a while - Then try installing xubuntu or ubuntu (using the default partitioning when you reach that stage.)

If problems persist there may be damaged sectors on the h/d. Try above first.
Posted using celeron 1ghz cpu/ 512Mb ram running Ubuntu hardy. Not fast but works well for day to day use.  Hope this is of use.


Thanks I shall try all that tonight when I get home. Last night I attempted to install Xubuntu (and Ubuntu) using different Live CD's and Alternate CD's. Still nothing installed without crashing. I even went the route of trying the Fedora netinstall method. 

I'm beginning to think that it's either the CD drive or the Hard disk (I'm hoping it's the former).

So today I am going to give @robert shearer's advice a shot then attempt to install Ubuntu Server edition and then install the desktop from terminal. If that doesn't work I'm going to give Zenwalk distro a shot and if that doesn't work I'm going to donate the machine to a landfill.

---

### Post by Zill on 2008-08-10
You still haven't told us if the live CD(s) run OK.  Don't try to install - just run the live CD and see if everything sems to work or not.  It is generally pointless trying to install the OS if a live CD won't run!

Let's keep it simple and tackle one distro at a time :-)

---

### Post by cariboo on 2008-08-10
Have you tried the mini.iso, this is just a net based installation. If you have a good internet connection, I would suggest this may be the way to go. 

I used it on a computer I'm fooling around with. When I did the original installation the computer only had 96MB ram, and hardy ran so slow it wasn't woth it. Right now it is running just the command line as an overly large mp3 player. It's been running three days straight with no problems.

Jim

---

### Post by meindian523 on 2008-08-11
> **zill said:**
> you still haven't told us if the live cd(s) run ok.  Don't try to install - just run the live cd and see if everything sems to work or not.  It is generally pointless trying to install the os if a live cd won't run!

Let's keep it simple and tackle one distro at a time :-)
+1.

---

### Post by MikeonTV on 2008-08-13
I ended up finally getting ZenWalk to install (although errors popped up) fine. The system now works with a gnome like UI and fine speed. Great for a little light browsing, media and programming

---

### Post by mikjp on 2008-08-14
Cool! Zenwalk is really nice little distro for older computer.

mikko

---

