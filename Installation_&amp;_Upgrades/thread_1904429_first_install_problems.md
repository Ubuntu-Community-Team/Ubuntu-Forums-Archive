---
title: "first install problems"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by skintner on 2012-01-04
Hello,
TOTAL newbie here, so your patience is appreciated.
 
I finally got around to trying to install Ubuntu on an old win server 2003 box... tried10.04.1 failed at the install package after formatting the partitions... the desktop version 10.04.3 failed with cd errors (burned ISO)... downloaded and started the 11.10 desktop version (burned from ISO) and it's been sitting on the purple screen with the red to white dots for about 45 minutes now...
 
At this point I am not impressed... I've been told it should install easily --- Win Server 2003 installed on this old celeron box, you'd think this would as well. 
 
I did format the drives that win was installed on... no biggie... but I would like to get Ubuntu installed. However, booting from the current cd it doesn't seem to want to go to any install, and there's no command prompt or options to install or run from cd.
 
so what now?
thanks
steve

---

### Post by darkod on 2012-01-04
Are you burning at low speeds, not more than 8x?

Install CDs are always best to be burned at really low speeds since CDs today go up to 56x. It reduces errors.

Loading live mode (Try Ubuntu) can fail because of bad cd/image, or hardware issue, mostly graphics. What video card does the computer have?

Also, it's best to download with torrent always as it checks for corruption during download.

---

### Post by skintner on 2012-01-04
Ok, I will use ISO burner and select a slower speed, but I find it interesting that none of the ISO files I downloaded for my MS Action pack subscription gave me any problems.
 
thanks,
steve

---

### Post by SteveHillier on 2012-01-04
Steve, 
Take note of Darkod's comments about burning CDs.  I never burn at more than half the maximum and I always do a verify after burning.
When you did the install how did you partition it.  Did you select the 'Use the entire Disk' option and let the installer do it's own thing.  That does not normally cause any problems.  Were you connected to the internet during install?
In all the installs I have done, and that is a lot over the years, I have not really encountered any problems that were due to Ubuntu itself.
Post back if you have some specifics.
Good luck
Steve

---

### Post by skintner on 2012-01-05
Hi again and thanks for the replies.
 
These ISO files were burned using whatever the default ISO burner is in Win7 Pro 32bit... as near as I could see, there was no option in that program to select the burn speed.  Win7 made that choice in a manner invisible to me.  If you know of a way to change win7's default iso burn speed, please let me know.
 
I have a downloaded ISO burning program on one of my Winsrv2008r2 boxes... I tried to install the same program on my win7 box but avast reports a virus.  note, I don't have antivirus on the win server.  I have also attempted to download several other iso burning apps but they tend to be loaded down with so much crap (toolbars, offers, and such) that I'm really reluctant to pursue them any further.
 
I have a fairly fast connection to the internet -- 1.5m or thereabouts... I have downloaded many large files and successfully burned them to discs > with cue/bin files, and ISO image files.  The ubuntu images downloaded successfully (3 different versions now) and burnt to disc.  
 
I ran the ubuntu server (10.04.1) install which appeared to be able to partition and format the drive(s)... I tried to use each disk on seperate install attempts but once the partitioning process was finished, it tried to install the package but reported a failure... I tried a couple different format options, the last was to use the entire disk and let the installer do it's thing.  It reports successful formats/partitioning but fails on the loading of the package.  I will run it all again here in a few minutes and quote back what it says.  Anyway, when the server install failed several times after partitioning succeded, I tried to install the two latest versions or ubuntu desktop (11.4?)... both booted to the cd initially and made it as far as a purple screen with the ubuntu title splash and some white dots that alternately turn red (process/progress indicators) and that is where it stops...
 
I don't know what else to say other than I would like to be able to have both the desktop version and the server running (on different boxes, of course) because of their reported efficiency... not to mention after 17 years of windoze I'd like to gain some proficiency in Linux, in whatever incarnation it takes.
 
So that's it...
 
Thanks for your help!
steve

---

### Post by darkod on 2012-01-05
Imgburn is a very good freeware windows program. Also you can download from [www.filehippo.com](www.filehippo.com), it seems all software is checked for spyware there.

---

### Post by skintner on 2012-01-05
Ok, the server disc was apparently corrupted... I dl'd imageburn (8x)and did a new disc for 11.10 desktop... it's still churning away with the purple screen and the *moving* dots...  this has been going on for 10+ minutes now... I am going to reburn the server image and try it...

---

### Post by skintner on 2012-01-05
now it's hung up with 1 white dot and 3 red dots...  sheesh...

---

### Post by darkod on 2012-01-05
Often the desktop doesn't load from cd because of hardware issues etc.
Try this: boot with the cd but hit Esc right away at the first purple screen, before the dots start.
That should bring you to the older type main menu. Hit F6 for advanced options, and select nomodeset. Then select Try Ubuntu and see if that loads live mode.

You might need to play with few more of the options, depends. What video card does it have?

---

### Post by skintner on 2012-01-05
Hi again,
After an 8x reburn of Ubuntu Server 10.04.1, changing out the cd rom and the hard disk, install appears to be happening successfully... 
 
Now I need to examine my options for what and how to equip this server and begin the arduous process of learning Linux. I suppose there is a gui that I can install if push comes to shove. What would be nicer would be an Ubuntu Desktop box that I can administer the server remotely from. Is that a possibility? I'm interested in maybe Apache, and possibly streaming media services of some kind. 
 
Any recommendations from here would be much appreciated.
 
Thanks in advance,
steve
 
Edit:
Hi darko... thanks for the tips. I have another box of similar configuration that I will try to install the Desktop on using your suggestions. The display adapter is built into the motherboard and I don't know what it is... server seems to be ok with it.
 
It is my belief that if the hardware is capable of supporting Win Server 2003 then it should support Ubuntu desktop (provide all the hardware is functioning as it should).

---

### Post by skintner on 2012-01-08
I've added an old Compaq Presario to my Ubuntu lineup, currently installing the latest version of the desktop.  It appears to be progressing along.
 
So, at the risk of asking this in the wrong forum, can anyone tell me if there is a graphical remote server administration program for Ubuntu desktop?
 
Thanks for the help and encouragement.
 
steve

---

### Post by skintner on 2012-01-12
I managed to successfully install the latest version of Desktop (11.10) but was really disappointed with it's sluggishness so I got rid of it and replaced with version 10.04
 
I am satisfied with the performance of this version of the desktop program.  I have also found Webmin which I will attempt to install on the server.  I am quite happy to have these alternatives to windoze and look forward to becoming fluent in command line linux.
 
Thanks for all the help!
 
steve

---

### Post by SteveHillier on 2012-01-25
Hi skintner,

Just a couple of comments to your recent posts.
FOr the most part if you are running a server you will operate it from the command line / terminal / shell.  There is nothing wrong in you setting up a machine with the desktop version and running it as a server.  You get the GUI to do a lot of the things you are used to.
Perhaps when you are more used to messing around at a command level you can try a server install without a GUI.
On the matter of video adapters Darkod does have a point.  Just because the video is on the motherboard does not mean that the version of Linux you are installing has support for it.
I once had a machine that I was setting up as a web server, modern motherboard, on-board networking.  Try as I may I could not get the networking to function.  In the end I went to the garage and rummaged around until I found an 8 year old PCI network adapter.  Fitted it - network ran a dream.
Remember, because very few manufacturers think there is anything out there except Windows, they don't write drivers for Linux.  So when some new hardware comes out we who only wait have to wait for one of our Linux friends to write a driver and release it for use.  That takes time and goodwill.

---

