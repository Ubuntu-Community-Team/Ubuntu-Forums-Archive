---
title: "Multi flavour Ubuntu booting - Lets pretend!"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by cygnus-X1 on 2010-02-16
At this point in time I have two boxes. One is XP (being phased out and possibly going to wife) and the other is 8.04(32). Now that I have the hardware for my Ubuntu box how I want it, it's now time to configure it. Up until now the system was a fairly vanilla, 8.04(32) autopilot install. Now I want to dive in and make things interesting. 

Unfortunately, I'm not well versed in what I need to get this done, ie - clueless. So I'm gonna needs some help figuring this out. What I'ld like to do is put this out there for the various gurus, pros and and see what the consensus of opinion is, and go from there. Hopefully this will benefit anyone else interested in this arrangement. Here's the set up:

The hardware: Mobo = Gigabyte MA78GM-S2HP / RAM = 4GB DDR2 800 / CPU = X4 945 Phenom II / HDD1 - WD SATA 160GB (Main OS) / HDD2 - WD EIDE 320GB (DATA ONLY) / WD SATA 640GB external eSATA (Data)

The task: To configure and partition the WD160GB HDD as a multi-flavoured *buntu system capable of using the best partition configuration for forward/backward compatibility. *[NOTE: Please keep in mind that based on current research, I would much prefer not to go into a debate on file systems. I plan on sticking with ext3 for everything.]* This way I can keep what I am familiar with, test the latest & greatest, and migrate at a comfortable pace.

The flavours I'm looking at putting in the box: 8.04(32) [the one I'm most familiar with] / 9.10(32) / 9.10(64) / Mythbuntu [If MythTV can be run in regular Ubuntu, please let me know.] / UbuntuStudio [optional] / 10.04(32 & 64) [to test and possibly replace a previous flavour(s)]{I'm not sure whether I prefer 32 or 64 as yet. I find positives and negatives with both.}

I understand that the swap space can be shared. My questions are, how should I partition the WD160 so that all of these flavours can coexist and be modified as needed; should I have a /boot partition; and how should /root(s) and /home(s) partitions be set up? Should I make a small boot primary and one big *** extended to stick everything else in with one swap and a bunch of 10GB /root & /home logicals. or what? Can I import settings from other /home directories? Hopefully this isn't query overload...  ](*,)

Many thanks in advance!

[COLOR="White"]-[/COLOR]

---

### Post by bwhite82 on 2010-02-16
What I would do is simply partition your drive off to have dedicated installs for each, EXCEPT for a dedicated 'home' partition that could be shared by all. From there, you only need to configure grub correctly so that all installations show up and are bootable from the menu. I would NOT try to make the installations "coexist". That is looking for headaches, but hey thats just my opinion.

---

### Post by cygnus-X1 on 2010-02-17
Hmmm? I understand that a single HDD can have four(4) Primary partitions, one of which can be an Extended partition, which in it can be held a virtually infinite amount of Logical partitions. (virtually infinite = limited only by minimum divisible overall size.) What I meant by coexist is that they can be booted to from GRUB via the choices listed, yet reside on the same drive. Example: 8.04 **or** 9.10 **or** Myth9.10 **or** 10.04 etc. 

So I guess I don't quite follow. It was my previous understaning that each OS would need its own /home and /root partitions. If that's not true, that could be *really* helpful in space allocation, (1 /boot and 1 /home and *x* /roots). Would that mean that the /home partition would need to be larger to accomodate the multiple OS's, or would the typical 10GB suffice? {Unfortunately, I'm mainly a visual learner and a picture of how it would look would be handy.  }  

Based on that, I guess I'm figuring that most of this would be done in an Extended partition with /boot as the first Primary and maybe /home as the second Primary, and an Extended with multiple /root Logicals and a 2GB swap. Does that sound about right?

[COLOR="White"]-[/COLOR]

---

### Post by bwhite82 on 2010-02-17
> **cygnus-X1 said:**
> 

Based on that, I guess I'm figuring that most of this would be done in an Extended partition with /boot as the first Primary and maybe /home as the second Primary, and an Extended with multiple /root Logicals and a 2GB swap. Does that sound about right?

[COLOR="White"]-[/COLOR]

Bingo. If you're sticking with Debian-based distros, I see no problem at all with each sharing the same /home. All it does is store local settings (ie FF bookmarks, GTK theme, etc).

---

### Post by cygnus-X1 on 2010-02-17
Cool! I like hearing that! Just like me to over complicate things when still in uncharted territory. 

Since this looks like this plan reduces the overall space used as a whole, how big would you suggest to make these partitions to optimize the available space to give enough headroom for growth, and potentially add a data storage area if there is significant room left over, given the 160GB drive size? 

*I'm not familiar with how much room /boot normally takes up.
*I've read that 10GB is what was for /root and /home. I figure in this case the /roots would still be the same.
*I'm clueless what size /home should be if it will contain all of the setting across the various versions. Or does that really matter?

And thank you for your patience!

Edited Feb, 17, 2010, 19:30 EST:
Never mind the /boot size. I went on a serious search and found the right combination to pull up anything from 8MB to 512MB as the magic number. The 512MB was posted by bodhi.zazen, so I'll set that one in stone. [http://ubuntuforums.org/showthread.php?t=499356]("http://ubuntuforums.org/showthread.php?t=499356")

Also, I actually have 4GB DDR2 800 RAM. Not 2GB.
[COLOR="White"]-[/COLOR]

---

### Post by cygnus-X1 on 2010-02-17
**UPDATE!!!**

After more than a week of searching the net, I post a question for help. Then I get awesome answers form an obviously knowledgeable user. Now, I finally stumble upon this: [http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

(Smacks self on head with bat!) Hopefully that link can help others wanting multi-*buntu systems.

Now all I need is a reasonable guesstimate/estimate of what /boot should be. Then I can log off and let the games begin! [-o<

Many thanks Soldierboy.
[COLOR="White"]-[/COLOR]

---

### Post by cygnus-X1 on 2010-02-27
Wrap up...

It took a while, but I ended up with this configuration:

/dev/sda1   Primary 512MB GRUB Chainloader
/dev/sda2   Extended
/dev/sda5   Swap      1GB 
/dev/sda6   8.04(32) 15GB Root
/dev/sda7   8.04(64) 15GB Root
/dev/sda8   9.04(32) 15GB Root
/dev/sda9   9.04(64) 15GB Root
/dev/sda10 10.04(32) 15GB Root(Future)
/dev/sda11 10.04(64) 15GB Root(Future)
/dev/sda12 /media/data Remainder of HDD*

* This has created a new problem that should be easily fixed. Can mount from any OS, but cannot do anything with it. Will look at forums and start new thread, if necessary. Also need to hadd an HDD.

---

