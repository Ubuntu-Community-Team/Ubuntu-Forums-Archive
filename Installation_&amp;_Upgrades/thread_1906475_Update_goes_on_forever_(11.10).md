---
title: "Update goes on forever (11.10)"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by maja_z on 2012-01-09
Hi! I'm having trouble updating:

1. using sudo apt-get update it simply gets stuck on something like
```

Get:67 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:68 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:69 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]

```
and goes on like this seemingly forever (I've gotten up to "Get: 190" this way, after a couple of hours). I'm attaching the whole log if it is of help!

2. using the update manager, it stays in "Updating Cache" window forever as well. The download indicator thingy just keeps  sliding left and right... It doesn't even ever stop to say "Failed" or "Connection dropped" or whatever!?

I'm not really sure where to start?
Thanks!

---

### Post by searchfgold6789 on 2012-01-09
Please attach your '/etc/apt/sources.list' file.

---

### Post by maja_z on 2012-01-09
Here's my file. Thanks!

---

### Post by maja_z on 2012-01-15
(bump)

I'm still unable to update my machine. Update manager now says I have 33 updates waiting to be installed, and yet when I click Install updates it stays forever on "downloading language-pack-en" and nothing ever happens!

---

### Post by spacecheck on 2012-01-15
I would suggest you try closing all package managers and then edit your sources.list to have a hash mark # in front of these lines:
```

deb http://ftp5.gwdg.de/pub/misc/cran/bin/linux/ubuntu oneiric/
deb http://qgis.org/debian oneiric main
deb-src http://qgis.org/debian oneiric main
```

(You may also want to comment out the lines for backports, unless you are having a problem with something specific, which requires a specific backport)

Then, save the file and try again with:
```
sudo apt-get update
sudo apt-get upgrade

```

If it resolves the problem, be sure to use the thread tools to mark the thread as Solved. 
If it doesn't work, report back for further suggestions.

Good luck!

---

### Post by maja_z on 2012-01-17
Thanks spacecheck!

I commented out the sources you suggest and reran update and upgrade. This time at least update 'finished', but upgrade ended up running through the night and only stopped because the connection was lost at some point. 

I'm attaching the logs (which was originally a 490 Kb file and therefore too big to attach :). So I've removed most of the repeating lines and split it into the update and upgrade logs respectively.

Thanks!

---

### Post by maja_z on 2012-01-23
Can anyone help me please? Is it possible that apt-get is somehow broken, I don't know?
I can't seem to install any packages, it just takes forever and no errors are given?! 
Update manager now says I already have 53 packages that need to be upgraded. But also I need to install libgdal1-dev and the same thing happens when I run: sudo apt-get install libgdal1-dev.
Any pointers will be greatly appreciated!

edit: well apt-get isn't not broken, I just did this as a mini test and it worked fine:

```
X@Y:~$ sudo apt-get install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  nautilus-open-terminal
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
Need to get 63.1 kB of archives.
After this operation, 918 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe nautilus-open-terminal amd64 0.19-1build1 [63.1 kB]
Fetched 63.1 kB in 2s (31.2 kB/s)           
Selecting previously deselected package nautilus-open-terminal.
(Reading database ... 182810 files and directories currently installed.)
Unpacking nautilus-open-terminal (from .../nautilus-open-terminal_0.19-1build1_amd64.deb) ...
Processing triggers for gconf2 ...
Setting up nautilus-open-terminal (0.19-1build1) ...
X@Y:~$
```

---

### Post by cortman on 2012-01-23
Looks to me like you should change mirrors- you can do that in Synaptic. Open up Synaptic and select Settings>Repositories, and change the "Download from" to a different server. See attached image.

---

### Post by maja_z on 2012-01-26
Thanks cortman! I tried changing mirrors but it hasn't changed anything. I also swithched to a lan cable in case it was the wireless causing problems in any way.
My internet conenction is fine for everything else, is it possible that it is still the cause? Namely I am doing this at work - the only place I have access - so perhaps the network setup (beyond my control) could be at fault? 
Also it doens't matter if I use apt-get, the Update  manager or Synaptic. 
Although on some occasions there seems to be some downloading going on, overall the upgrade never finishes properly..
E.g. choosing the mirror I clicked "select best server", which started doing its thing and then half way through just stopped. Like forever. When I clicked cancel it says " check your internet connection". And yet when I tried the (exact) same thing again, it worked fine and selected a reasonable one close by. 
Like I said, my internet is fine otherwise, why does it seem to be acting up (in such an error-less way) when I try to upgrade!?

---

### Post by cortman on 2012-01-26
> **maja_z said:**
> Thanks cortman! I tried changing mirrors but it hasn't changed anything. I also swithched to a lan cable in case it was the wireless causing problems in any way.
My internet conenction is fine for everything else, is it possible that it is still the cause? Namely I am doing this at work - the only place I have access - so perhaps the network setup (beyond my control) could be at fault? 
Also it doens't matter if I use apt-get, the Update  manager or Synaptic. 
Although on some occasions there seems to be some downloading going on, overall the upgrade never finishes properly..
E.g. choosing the mirror I clicked "select best server", which started doing its thing and then half way through just stopped. Like forever. When I clicked cancel it says " check your internet connection". And yet when I tried the (exact) same thing again, it worked fine and selected a reasonable one close by. 
Like I said, my internet is fine otherwise, why does it seem to be acting up (in such an error-less way) when I try to upgrade!?

It could very well be your work network setup. Do you use a proxy? Although if everything else in Ubuntu connects fine that probably wouldn't be the case... Firewall?

As a last resort (it may not be related at all, but give it a try) open a terminal and enter the following-

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

and see if it works. Otherwise I'm afraid I'm at the end of my very limited knowledge.
Good luck!

---

### Post by maja_z on 2012-01-29
OK, I'll mark this as solved, although I'm still not sure what is going on, but I did manage to update. 

I left Synaptic running for about 3 hours - 3 hours of it doing absolutely nothing!  When it says it is downloading files, but only shows one file "queued", nothing happening at all, no network traffic showing up or anything. Then all of a sudden, out of the corner on my eye, I see the progress bar suddenly start filling up. Man, I almost had a heart attack!

This was all on cable, at work. With no other network thing running. So I don't know what was semi blocking it and why it then let it through, probably something to do with the network anyway and since I have no admin rights this thread is unlikely to lead to anything more helpful for anyone else.

Thanks again to everyone who helped!

---

