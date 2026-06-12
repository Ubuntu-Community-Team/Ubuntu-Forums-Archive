---
title: "Dual boot fail"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by createsean on 2010-01-02
I just attempted to install ubuntu for the 4th and 5th time and have yet again had a fail. This time it actually completed the installation, which is a first.

however upon reboot it takes me directly to Vista - I don't see grub or a o/s selection choice.

I thought linux is supposed to just work. guess not.

---

### Post by zey on 2010-01-02
you do original install or using wubi..?

[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by JC Cheloven on 2010-01-02
Bet yes :-)

Please, have a look on the manual first:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

And tell us some more details about what you did, so that we can help.
Are you installing from live cd or from alternate? In the first case, how was it the live session? Any malfunction? ...

---

### Post by createsean on 2010-01-02
Original install from a live CD that i downloaded directly from this site only a couple of hours ago.

I already had a paritition set up on my Hard Drive so I put the cd in and installed it.

When it finished I rebooted, took the CD out of the drive and voila ended up at Vista with no o/s choice option available.

I deleted the partition and then reinstalled yet again doing the exact same thing and once again no option to go to Ubuntu.

---

### Post by gnimsh on 2010-01-02
So when you get to the partitioning stage of the installation, do you choose the option to install "both OSes side by side, choosing between each at startup" or to specify partitions manually?

---

### Post by createsean on 2010-01-02
side by side

---

### Post by gnimsh on 2010-01-02
Since you already have a 2nd partition set up, choose to do it manually.  Make sure you have a 3rd partition for swap (4-5 GB is fine). I think 4 parts are a good number: 1 for the root install, one for home, one for swap, and one for windows. This way if you want to install a new distro it doesn't pooch your linux data.  

But ya at least try installing it manually on the separate partition, which should be formatted as ext3 or ext4 (ext4 will speed up boot time).  I've always had success doing it this way.

---

### Post by createsean on 2010-01-02
When I looked at the manual option it seemed to want to delete the vista partition - wasn't very intuitive to me. Will try that tomorrow.

---

### Post by gnimsh on 2010-01-02
Just choose the partition labaled free space, that has no format label. Do NOT check the format box next to the ntfs formatted partition. Leave that alone. Only format for ext4.

---

### Post by JC Cheloven on 2010-01-03
@createsean:

The problem may be, among others, that the manufacturer have created too many partitions in your hard disk, and now the ubuntu installer wants to create some more, and isn't possible. 
But not pay attention to this guess by now. I haven't enough info to say. It could be a bad cd burnt or whatever. Please answer the following to get a closer idea of the actual state of your system, and I'll (hopefully) be able to tell you what to do step by step.

1) The cd boots ok into a live ubuntu session, with usable internet, right? We will operate from that live session in the following. So start your live session, in firefox keep open a new post in this thread, and do the following.

2) Open a terminal (Accesories-Terminal), write this command,
```
sudo fdisk -l
```  press enter, select the output with the mouse, from the menu do edit-copy, and paste it back here, in your post (you can copy the command and paste it at the terminal to avoid typos).

3) Do the same with each one of these:
```
free -m
```
```
sudo lshw -c cpu
```
```
uname -a
```
and just in case
```
lspci
```

That will give us the needed info.
Note.- I wouldn't try further (blindly) installing for the moment. In the trial and error process you could mess your vista boot, or something else.

---

### Post by createsean on 2010-01-03
I got it worked out via a twitter friend, my laptop and a web cam discussion.

I disconnected my 2 other harddrives and then installed ubuntu. Then everything worked. 

Strange.

I reconnected the 2 hard drives and I can still dual boot so everything is good. I'm not sure why, but if it works that's all that matters to me.

Now I need to figure out how to get my right monitor to rotate 90 degrees. I've got dual monitors working, but can't use it due to my 2nd monitor being in a vertical profile. I found instructions for nvidia cards but nothing for ati which I am using.

---

### Post by JC Cheloven on 2010-01-03
Glad you solved your problem. I agree in what it isn't worth to waste your energy in finding out what the hell was hapenning. Multidisk shouldn't be an issue, indeed.

As for your vertical monitor setup, have you tried the obvious system-preferences-monitor and choosing the option you need? I never used that, so I don't know really how well it works. If this doesn't help, Id suggest to open a different thread. "Always a new thread for a new problem" ;-)

---

