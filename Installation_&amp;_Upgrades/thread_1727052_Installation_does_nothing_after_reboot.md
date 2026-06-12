---
title: "Installation does nothing after reboot"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by GridLynx on 2011-04-12
Greetings.

I was curious about how Ubuntu would perform if installed alongside with my current OS without having to partition... At any rate, for this solution i tried WUBI and all went fine and i got to the point where it requested me to restart.

So i did so but.. instead of noticing any start up menu to let me choose for a different OS or the conclusion of the installation, i got absolutely nothing!

Details:
- Wubi along with Ubuntu were mounted in  CD image in Alcohol 52%
- My laptop is a Centrino duo 1.6ghz with 2 gbs of ram and currently running windows xp media center edition with service pack 3.

---

### Post by bcbc on 2011-04-12
right click on My computer, Properties, Advanced, Startup and recover settings. There's a drop down box there. Make sure Ubuntu is in it (don't select it). If the timeout is zero set it to 30. If the Ubuntu entry is not there, post back.

---

### Post by GridLynx on 2011-04-12
Alright, Sorry for the late reply.

I just redid the installation and checked the drop down box "Ubuntu" is there
and i just ticked the option to show OS's for 30 seconds, about to restart to see if it worked, Wish me luck!

---

### Post by bcbc on 2011-04-12
> **GridLynx said:**
> Alright, Sorry for the late reply.

I just redid the installation and checked the drop down box "Ubuntu" is there
and i just ticked the option to show OS's for 30 seconds, about to restart to see if it worked, Wish me luck!

Good luck. ;)

---

### Post by GridLynx on 2011-04-12
Haha it worked!  Thank you man! 

I sort of feel dumb now, not realizing the option to choose  OS at startup wasn't ticked :P

At any rate, thanks once again.

---

### Post by bcbc on 2011-04-12
> **GridLynx said:**
> Haha it worked!  Thank you man! 

I sort of feel dumb now, not realizing the option to choose  OS at startup wasn't ticked :P

At any rate, thanks once again.
Well.. you shouldn't feel dumb. For most people - there is no manual 'ticking' required. And I wouldn't have known about that the first time I installed Wubi either.

Please check out the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide"). Wubi is a very good way of trying out Ubuntu - nearly identical to a real dual boot (just a bit slower and it runs off a virtual disk - a file called \ubuntu\disks\root.disk on the 'drive' you installed Wubi to). 
Because the virtual disk is stored within a file on your windows file system there more likelihood of data loss in the event of corruption. Protect yourself by avoiding hard shutdowns - instead use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device") and keep important data backed up.

When you look at your files within Ubuntu you'll see just the files on the virtual disk - to access the files under the Windows host, look on /host (Alt-F2, nautilus /host), or click on the Places menu, Computer, File system, host.

---

### Post by GridLynx on 2011-04-12
Thank you, for the great information! right now is pretty late but i am just glad i am able to navigate ubuntu with a bit more of a hands on approach, rather than in the live usb... i was impresed with how fast it loaded after i rebooted it for the first time and to believe this is the speed it harnesses with just a virtual installation! 

I am saving those links you just gave me :) 

Also if you can, try looking for my post in the general help section. I am giving some of my technical background on what i might need of an OS and  i am  looking for suggestions from the most seasoned users ( which you appear to be ) If i might benefit from a complete Ubuntu installation.

---

### Post by bcbc on 2011-04-12
I don't recommend you get rid of Windows right from the start. But it's obviously your choice. I'd recommend you get familiar with Ubuntu first.

Also, if you're thinking of going that route - you might find that moving to a proper dual-boot (rather than Wubi) is a good idea. Wubi is a great way of trying out Ubuntu but isn't ideal for long term use. There's no rush - the whole point of Wubi is to try out Ubuntu in a risk free way (risk free to Windows) - without the hassle of partitioning and while it is possible to migrate a Wubi install to a full install later (without losing your programs/settings or data), if you are certain you'll be a long-time Ubuntu user, then you might consider just doing a normal dual boot install from the start.

Whatever you decide - make sure you have backups and recovery disks at hand. Most of the time they're not required, but it's good to have them just in case.

---

