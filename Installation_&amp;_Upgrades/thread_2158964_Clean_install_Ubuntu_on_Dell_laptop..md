---
title: "Clean install Ubuntu on Dell laptop."
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by jimv8673 on 2013-07-01
I have decided to install ubuntu on my dell laptop and replace the windows 7 that is on there now.  My decision was based on the fact that i really dont use this computer for the normal things, just internet.  Being a clean freak, what i want is a small operating system that runs faster than windows, without all the bloat.

So... im downloading ubuntu desktop 64, and wondered if that iso did a complete reformat of my hard drive so as to start with a squeaky clean machine with only ubuntu on it??

If not, how can i clean everything off before i start??  i would like all my drive space to be on on partition instead of being broken up into like C and D etc. except make sure i still show a drive for zip drives, CD's etc.  removable stuff.

Any help is much appreciated.

---

### Post by mastablasta on 2013-07-01
yes complete reformat. make sure it works first though by booting into live OS.

Furthermore to get something really fast try Lubuntu or Xubuntu. Lubuntu should spend about 100MB-130MB on idle.

you will get even less with a couple of other desktops and windows managers.

---

### Post by Lars Noodén on 2013-07-01
How minimal do you want?  Probably the lightest you can get and still have a full [desktop environment](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/) would be to install the Ubuntu Server or use the Alternate disc to install a 'Command-line system'  From there you could add the package [lubuntu-core](http://packages.ubuntu.com/raring/lubuntu-core).

If you want lighter, skip the core and just install a window manager, such as fvwm-crystal or Openbox, instead of a Desktop Environment.

---

### Post by craig10x on 2013-07-01
If you like the standard ubuntu with unity desktop that you downloaded, then that would be fine as long as you don't have a very old computer with limited specs...Just run it in the live session mode (try ubuntu first selection when you boot iso) and see how it runs on your computer...

If it runs well, then on the search type "install ubuntu" in the search bar and you can select for the installer to totally wipe windows 7 and install ubuntu over it....windows will be totally off the drive (that is the way i install when i get a new computer)...just make restore discs for windows before you wipe it off...in case you ever need to re-install it for any reason...

After installing, you will want to install ubuntu restricted extras from the software center to get all your codecs and flash that you will need for your web surfing, listening to music, etc...

---

### Post by HermanAB on 2013-07-01
Howdy,

Regular Ubuntu is big, bloated and slow as molases compared to other versions such as Xubuntu or Lubuntu. So, if you want something small, without the bloat, then you know what to do.

---

### Post by leunam12 on 2013-07-01
> **Lars Noodén said:**
> 
If you want lighter, skip the core and just install a window manager, such as fvwm-crystal or Openbox, instead of a Desktop Environment.Interesting! how can you this? are there any tutorials out there?

---

### Post by craig10x on 2013-07-01
Regular Ubuntu is not big and bloated as the previous poster stated...you would only need to try xubuntu or lubuntu if you have a pretty old computer that doesn't have enough resources to run it...a live session will tell you...

That is assuming you like the unity interface (personally, i love it)... if you do not, then you would want to try them for sure...I'm assuming you have at least 2 gigs of ram....though running Regular Ubuntu, even with multiple programs running, i don't think i ever used more then about 1 gig ram...but it's good to have a cushion...

---

### Post by su:bhatta on 2013-07-02
u can hav a look at xubuntu... itz nice out of the box...
givin ur machine specs is gonna be really helpful... 

based on ubuntu u hav the elementary OS which i have used n it was neat, clean n super quick... (maybe i shouldn't suggest this)
(but i hav 3.5 gigs of ram...)

If ur machine can load the live session then try out plain vanilla ubuntu, thatz nice to use out of the box too...

Getting ur box squeky clean is hardly an issue, when installing just choose 'remove everything and install ubuntu' or whatever distro u find acceptable...

Also, i suggest (i guess u hav another laptop), use virtualbox to try out different distros n then choose the 1 u find most friendly, usable to you...

---

### Post by houseworkshy on 2013-07-02
If at the choosing stage youtube is pretty good as people post videos of various systems so you can see things in action.  distrowatch.com has an advanced search function and most labeled as "light" or "lite" will be quick and low resource.  If you are new to linux you may want to add the term "beginer" and definately add the term "supported" 

 "bloat" is a bit of a weighted word but definately Unity wants more system resources then Xfce and LXDE and it includes "Unity-lens-shopping" which many don't like though it can be removed fairly easily, it is however one of the best out there for touchscreens.    
There are a lot of desktop enviroments [https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment) and most will run on most linuxes.  In Ubuntu there are several preconfigured alternatives to Unity, Kubuntu runs KDE, Xubuntu runs Xfce, Lubuntu runs LXDE and Bhodi Linux runs enlightenment.  You can actually have several enviroments installed on one system and choose at bootup, though you will likely have some duplication in menu entries if you do that.

So stay with windows for a while and have a good browse read and watch.   Then download and burn distros you like the look of and try them out in  live sessions.  Live sessions usually crawl compaired to hd installations;  exceptions to that being Knoppix and puppylinux which are primarily designed to be run live.  When you do choose one for a hard disk install I'd recomend duel booting for a while so what you know is still there while you test what is new.  There are plenty of guides on how to do that.  Have fun.

---

### Post by snowpine on 2013-07-02
Ubuntu is an absolutely dreadful choice if you are looking for a "small operating system without bloat."

Try: Puppy (133mb), SliTaz (35mb), or TinyCore (12mb).

If you want to stay in the 'Buntu family then check out this excellent tutorial: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by buzzingrobot on 2013-07-02
Just downloading the ISO file will have no impact on your Windows filesystem, other than the creation of that new file.  When you install Ubuntu, you will be given several choices of approaches, including replacing Windows. 

Anecdotal reports about which version of XYZ is lighter or heavier, or faster or slower, need to be considered with *your* hardware and *your* interests in mind.  Memory use, for example, often differs when only the amount of available memory changes. Less memory use is not necessarily synonymous with faster execution.

---

### Post by Bucky Ball on 2013-07-02
*Thread moved to **Installation & Upgrades**.*

I have changed the title of your thread to reflect your issue. This will increase your chances of getting help. Please avoid the generic; most people here 'need help' or wonder 'what's this?'.

You can go one step further with clean and manually partition the drive. With Ubuntu you choose 'Something Else' when it gets to the partitioning section of the drive.

Some good suggestions for OSs above. Puppy flies. My suggestion would be a Ubuntu minimal install. Rather more involved though and something to try later. Basically, you install the Ubuntu base kernel then add what you like, including a lightweight desktop environment. That way you can create a beast that flies! (And is clean.)

For a basic setup you need:

/ = root partition, where the OS goes; depends on the OS and whether you store your personal data elsewhere but 15-20Gb is plenty for standard Ubuntu;
/home = home. Your personal data, Documents, Videos, etc. This depends on how you have things set up but it is a good idea to store you data outside / for a number of reasons;
/swap = swap. 2Gb fine, unless you do a lot of hibernating apparently but I don't so can't advise.

Good luck.

PS: Lubuntu or Xubuntu are probably the lightest *buntus, Lubuntu lightest. I use a minimal install with Xfce from Xubuntu as desktop environment myself. ;)

---

