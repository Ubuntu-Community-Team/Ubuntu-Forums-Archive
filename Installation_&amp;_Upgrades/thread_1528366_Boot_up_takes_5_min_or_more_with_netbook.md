---
title: "Boot up takes 5 min or more with netbook"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by User_1 on 2010-07-10
Hello all, 

I was hoping I would see that others are having the problem I'm having, and I really don't see it anywhere.  I started out with a completely clean HD, formatted in fat32.  I installed Win7 and updated it.  The HD is 150GB and used a partition of 40GB for Win7.  Everything worked, so then I installed the netbook version of Ubuntu that is located here, 
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
I followed the directions and did the updates after the install.  The problem is that it took over 5 minutes for Ubuntu to boot up and get running.  I reformatted the HD and did the same install thinking I must have screwed up somewhere, but had the same results as before.  So what I did this time was just install Ubuntu by itself.  The slow boot ups continued.  After doing the updates and all, it now takes about 8 minutes to boot up!

My system is a Toshiba NB305 with 2GB of ram.  The bios version is 1.50.  

I'm really lost as to what is going on and what to do now.  Any help in this matter is GREATLY appreciated.

---

### Post by sgosnell on 2010-07-10
That is certainly not normal.  I run standard Ubuntu, not the netbook remix, but it boots in <30 seconds.  I couldn't get the page you linked to load, but I assume it's 10.04.  What type filesystem are you using?  Ext4?  I have no experience with that particular model, but my wife's Toshiba Satellite boots in about the same time as my Asus EEE, something under 30 seconds.  You might take a look at Launchpad bug reports & see if there is anything specific to your model.

---

### Post by cj.surrusco on 2010-07-10
Welcome to the forums, first of all.

We want to take a look at how your system is booting, so let's install bootchart to monitor it. To do that, type the following into a terminal:

```
sudo apt-get install bootchart pybootchartgui
```

Type in your password when prompted, then when it is finished, restart your computer.

Once you have restarted, open /var/log/bootchart in nautilus. Wait a minute or two and there should be an image file. Go ahead and post that image back on this thread.

---

### Post by User_1 on 2010-07-10
> **cj.surrusco said:**
> 
Once you have restarted, open /var/log/bootchart in nautilus. Wait a minute or two and there should be an image file. Go ahead and post that image back on this thread.

Well I was able to do the first part, copy and paste the command in the terminal, but the rest I'm a bit shaky at doing.  I do know that Nautilus is installed.  I'm very much a noob at this OS.  Have a good amount of experience at windows though. 

Also I noticed that the OS is booting up much faster now.  I'm up and running in less than 30 seconds.

---

### Post by kerry_s on 2010-07-10
see this thread:
[http://ubuntuforums.org/showthread.php?p=9547125#post9547125](http://ubuntuforums.org/showthread.php?p=9547125#post9547125)

on the nohz=off fix, it's a toshiba problem.

---

### Post by cj.surrusco on 2010-07-10
Well it seems that your problem is solved. Anyway, Nautilus is your file browser that is used in Ubuntu.

---

### Post by User_1 on 2010-07-12
The nohz=off sounds like it may have been my problem when I started out with installing Ubuntu along side Win7.  I installed both OS again after wiping the HD clean and I still had the problem of Ubuntu taking over 5 minutes to boot.  Right now it's the only OS on the netbook after wiping the HD clean again, and looks like the problem is solved.  I thought it was kinda strange how it got repaired.  Looks like all I did was install a boot tool for checking the process.  And wham-bam it's fix!  I hope all my problems are this easy around here. :D

Thanks for the help guys.

---

