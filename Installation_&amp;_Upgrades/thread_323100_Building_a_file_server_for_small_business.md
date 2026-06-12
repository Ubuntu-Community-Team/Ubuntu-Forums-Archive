---
title: "Building a file server for small business"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by HeavyAl on 2006-12-21
Hey all,

I'm hoping someone has some suggestions for me before I go ahead and take the plunge on this.

My day job is working for a small company that has a local 'server' that it houses all its business files on. The current setup is incredibly lame - its really just a windows xp pro box with a couple of external usb maxtor drives attached to it. I have worked here a bit over a year and in that time I've had to reboot the thing more times than I can count. It locks up constantly and I have to do a hard reboot at least once a month (actually its been 3 times this week so far).

Anyway, I'm thinking of wiping the machine (except the external drives which have the real data on them) and installing Ubuntu on it (which I personally use in several locations already including my laptop, two home desktops and the web server install). I'll need it to be accessible via the windows-based network with read/write capability so I imagine its going to need some sort of samba setup installed on it and I'd also like to be able to administrate it from another machine so some kind of ssh server will probably be in order. Problem is, I dont know how to set up either of those things. This is further complicated by the fact that the external drives use the ntfs file system so I dont know if we can even write to them with Linux.

The machine is a Celeron running at 600mhz with 384megs of ram. The primary drive is a 5 gig quantum fireball. Seems to me the specs are so low that only a server install of ubuntu would be possible anyway.

Any insights into what route I should take on this would be very much appreciated!

---

### Post by psycho78 on 2006-12-21
Ok, first of all I would not wipe the machine without learning how to setup samba on a different machine first. You got to be sure what you are doing. 
The machine should do the job perfectly but you should copy all the data onto  a linux filesystem (e.g. ext3).  There are several samba howto's on the net and I think samba is really not hard to setup as long as you don't need any kind of directory service... I guess you only need some users any not many different access rights? SSH access is always a good Idea... and if you want to setup shares graphically there is a package called swat [SIZE=2]([/SIZE][SIZE=2]swat is the Samba Web Administration Tool) which may help you with that..... 
So go on and do it! :)  Every pc without windows make this world a little better ;)
[/SIZE]

---

### Post by TheWizzard on 2006-12-21
> **psycho78 said:**
> you should copy all the data onto  a linux filesystem (e.g. ext3). 
this won't be necessary if all the data is on external usb hdd's. 

samba servers are pretty easy to setup. but make sure you know what you're doing. 
make sure you have good backups before you start playing around.

---

