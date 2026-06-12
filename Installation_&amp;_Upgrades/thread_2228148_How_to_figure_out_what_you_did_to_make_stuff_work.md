---
title: "How to figure out what you did to make stuff work"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by Elssha on 2014-06-05
Hi, 
   Haven't been here in a long time, and for that I apologize. 
For those who don't want backstory; 
I'm looking for a way to see what has been added/changed/etc to the actual ubuntu that made it work on my laptop so I can redo it when I get a new hard drive. Now, the details;

So over a year ago, I started my long road toward a dual boot with win8 on an Asus G75vx ROG laptop. I opened a [topic ]("http://ubuntuforums.org/showthread.php?t=2134969")to help me, and also did loads of googling and tons of trial and error. I got as far as getting all but the wireless to work by May, but then put everything on a back burner as life took over. Didn't touch linux until December or so, and somehow I managed to get the wifi to work. Now everything is (more or less) perfect... but with all the fudging I did, I don't have a CLUE what actually worked and what was a waste of time. Also, I probably only have 1/3 of the sites I looked at saved in my history. 

I'm planning to get an SSD and turn it into my primary drive in a month or two (crucial M550 is what I'm leaning towards atm, if anyone has any side comments on the subject) because the slow drive it has now is keeping this thing from being all it can be. 
I was hoping someone might point me to somewhere in the OS itself that might tell me what drivers were added after the inital install... maybe even if any OS files were edited, etc. 
... or maybe how to make an install usb that would install my ubuntu as it is now? 

Thanks, and I realize I'm probably not saying this right at all >_<
Any help you are willing and able to give me will help me a LOT, since I really don't want to be stuck in JUST win 8.1
All the best, and I look forward to your replies, 

Elssha

---

### Post by TheFu on 2014-06-06
Well, versioned backups are how I do it.
If you backup /etc/ you'll get 85-100% of the system config changes.
If you backup ~/ you'll get 100% of your personal account changes.
If you capture a list of installed packages with every backup, you'll have the changes of those installed / purged / removed packages over time too.  The command is: dpkg --get-selections     store the output in a file that gets backed up.

Clearly, if there is other data, programs installed outside the package manager (like via source or .deb files) or settings outside these areas, those will need to be backed up too. Nobody but you will know those changes.

With this data, most people can recreate a system close enough on new hardware that any slight differences don't matter.  There are small manual tweaks needed - UUID for any mounted partitions, perhaps a MAC address for an ethernet card, but pretty much everything else doesn't need to be manually touched.

There used to be a way to make an installer based on a current install.  If you don't care about any data or settings, that can be done through the list of currently installed packages.

If you google "ubuntu system migration" - more detailed how-tos should come up.

There are probably other ways to accomplish this. I just don't know them.

---

### Post by tgalati4 on 2014-06-06
Use a notepad and keep a record of changes that you make.  I use *zim* for an electronic copy but also a trusty, old-school, spiral binder for computer notes.

---

### Post by elssha2 on 2014-06-15
TheFu;
    I'm mostly concerned with having my Nvidia and Wireless work. Would backing those places up help with that, or would those be elsewhere?
If it's no issue, a clean install would be preferable, but digging for this stuff for the next 6months isn't my idea of a good time, either >_<
As I'm going to be doing the same with the win8 on this thing, can I clean install windows then clone Ubuntu, or would it be an all or nothing thing?
thanks!

tgalati4; Yeah... I'll remember that for next time ^_~

---

