---
title: "How long should install take. 11.10"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by paulkruger on 2012-03-08
**How long should Ubuntu 11.1 take to install?**

I started install an hour ago and it is still running. 

So far the progress bar says it is creating "ext4 file system" but it has not budged in over 45 minutes.

primary petition 5.5GB
swap 200 MB
and a data partition Fat32 ( so I can access via windows network to transfer music files.
( Total 500GB Seagate drive ):confused:

---

### Post by kc1di on 2012-03-08
It depends on the several factors, 
1. speed of machine
2. amount of ram
3 if you already have the partitions created.

I think in your case it's make a partition where there wasn't any
it has to make room to put the Linux files. 

On my machines here it only takes about 20 minute or less to to an install but I already have my the partitions I want before the install and one a windows machine that can take some time.

Hope it works our for you

---

### Post by jerome1232 on 2012-03-08
Sounds like something went wrong to me, how much ram does the machine have?

---

### Post by paulkruger on 2012-03-08
> **jerome1232 said:**
> Sounds like something went wrong to me, how much ram does the machine have?

256 MB

The final machine at this instant has 49MB but will upgrade to 1GB later once I know I can get it running.  The destination CPU is a re-purposed Seagate Mirra Personal Server.  I intend to use this only as a media server for music files, not video etc.

I am using a spare computer to install the OS due to the small amount of RAM on the other machine.

---

### Post by jerome1232 on 2012-03-08
You may want to try the alternate install cd, I think the graphical installer wants you to have at least 512 mb of ram if I recall correctly.

---

### Post by paulkruger on 2012-03-08
> **jerome1232 said:**
> You may want to try the alternate install cd, I think the graphical installer wants you to have at least 512 mb of ram if I recall correctly.

Where is the iso for that? Not sure I saw that.

Funny though this same machine had Mandriva installed and that went on with no trouble at all?

---

### Post by jerome1232 on 2012-03-08
> **paulkruger said:**
> 
Funny though this same machine had Mandriva installed and that went on with no trouble at all?

Without having ever used Mandriva's installer I can't give much feedback on that, Ubuntu does do the install from a fully functional live environment, which is why it may require more ram to work.

The alternate install cd uses the same installer that debian uses, or so I've been told, I've gotten it to work on a system with 112 mb's of ram.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Also I don't know for a fact it's your ram that's making it hang, you could give it another go to see if it works a second time, I'm just guessing that since it is a low amount of ram, that may be the issue.

---

### Post by georgelab on 2012-03-08
Looks like a RAM issue, but you could try to perform a self-test on the installer media, maybe it's just an ISO problem. Did you try to checksum it?

---

### Post by kc1di on 2012-03-08
> **paulkruger said:**
> 256 MB

The final machine at this instant has 49MB but will upgrade to 1GB later once I know I can get it running.  The destination CPU is a re-purposed Seagate Mirra Personal Server.  I intend to use this only as a media server for music files, not video etc.

I am using a spare computer to install the OS due to the small amount of RAM on the other machine.

Not enough ram ! 

"The minimum memory requirement is 512MB for graphical LiveMedia (LiveCD or LiveUSB)"

---

### Post by paulkruger on 2012-03-08
> **kc1di said:**
> Not enough ram ! 

"The minimum memory requirement is 512MB for graphical LiveMedia (LiveCD or LiveUSB)"

I may be better off going back to Mandriva since it installed with this same box and ram with no issue at all.  Perhaps Ubuntu needs too many resources for what I want to do?  I have not used Ubuntu before but it was suggested in searches for best distro for a media player machine. ( No video, only audio juke box function )

All I need is network access and a audio media player to run. No other bells and whistles.

---

### Post by paulkruger on 2012-03-08
> **kc1di said:**
> Not enough ram ! 

"The minimum memory requirement is 512MB for graphical LiveMedia (LiveCD or LiveUSB)"

I may be better off going back to Mandriva since it installed with this same box and ram with no issue at all.  Perhaps Ubuntu needs too many resources for what I want to do?  I have not used Ubuntu before but it was suggested in searches for best distro for a media player machine. ( No video, only audio juke box function )

All I need is network access and a audio media player to run. No other bells and whistles.

I am downloading the alternative iso to try first.

*( Strange...my post was delayed with an error saying I need to wait 20 seconds between posts even though my last post was a half hour ago?? )*

---

### Post by jerome1232 on 2012-03-08
> **paulkruger said:**
> 
*( Strange...my post was delayed with an error saying I need to wait 20 seconds between posts even though my last post was a half hour ago?? )*

You have two posts in rapid succession with times less than minutes apart. So your last post before this particular post was not 30 minutes ago.

Mandriva's system requirments look to be about the same as Ubuntu's, I'm guessing their installer doesn't run from a live environment which is why the installer might not need so much ram. 


Mandriva is listed as

"Processor

Any Intel, AMD et VIA processor.
Memory & storage

RAM : 1 Go minimum, 2 GB recommended.

Hard disk : 10 GB minimum.
"

Ubuntu is listed as

"1 GHz CPU (x86 processor (Pentium 4 or better))
1 GiB RAM (system memory)
15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
800 by 600 screen resolution
Either a CD/DVD drive or a USB port for the installer media

Internet access is helpful "

---

### Post by jerome1232 on 2012-03-08
deleted: double post

---

### Post by wyliecoyoteuk on 2012-03-08
You could try Ubuntu server, which will install with 128Mb or [vortexbox]("http://vortexbox.org") 
But the latter needs at least 1Gb of ram too.

---

### Post by wyliecoyoteuk on 2012-03-08
deleted double post
Which incidentally, seems to be happening a lot tonight.

---

### Post by paulkruger on 2012-03-08
> **wyliecoyoteuk said:**
> deleted double post
Which incidentally, seems to be happening a lot tonight.

That might explain the 20 second warning.  When I tried to post nothing happened so I clicked a second time then the post was added.  :D

---

### Post by paulkruger on 2012-03-08
I really need to dig in my parts box for some more ram !:D

---

### Post by MAFoElffen on 2012-03-08
> **paulkruger said:**
> I may be better off going back to Mandriva since it installed with this same box and ram with no issue at all.  Perhaps Ubuntu needs too many resources for what I want to do?  I have not used Ubuntu before but it was suggested in searches for best distro for a media player machine. ( No video, only audio juke box function )

All I need is network access and a audio media player to run. No other bells and whistles.
Two comments.

First- If an install locks, figure out what mode the installation is in. Graphics run in tty7. Text installs run in tty1. System messages run in tty4. tty4 would display the error messages.

Two- Mandriva? Really?  Current Mandriva is KDE and in their spec's they say 1GB minimum and 2 GB preferred. (Which is the same RAM spec's as Ubuntu)... 

Three- 256MBs? You "could" install in a text-mode installer (as you and other's here suggested)... (But) Then you have to run it.  

Recommendation- Look at Xubuntu and Lubuntu.

---

### Post by critin on 2012-03-08
> **paulkruger said:**
> 256 MB

**The final machine at this instant has 49MB but will upgrade to 1GB later once I know I can get it running. ** The destination CPU is a re-purposed Seagate Mirra Personal Server.  I intend to use this only as a media server for music files, not video etc.

I am using a spare computer to install the OS due to the small amount of RAM on the other machine.

You're trying to install on a second machine that has 256 ram and it is giving problems, **but the final destination machine only has 49 MB?**  I can't imagine anything running on 49 MB fast enough to enjoy.  Doesn't music take more ram to avoid lagging?

---

### Post by jerome1232 on 2012-03-08
> **critin said:**
> You're trying to install on a second machine that has 256 ram and it is giving problems, **but the final destination machine only has 49 MB?**  I can't imagine anything running on 49 MB fast enough to enjoy.  Doesn't music take more ram to avoid lagging?

He said he was upgrading it to 1 GB, which is fine to run a graphical interface (although I'm not sure a machine with only 49 MB would even be able to upgrade to 1 GB, let alone if the ram for it is even popularly sold anymore)

---

### Post by critin on 2012-03-08
> He said he was upgrading it to 1 GB,Yes, I didn't word the line clearly and was incomplete.  Thanks.   

> **will upgrade to 1GB later once I know I can get it running**My real concern is will it even be gotten to the point of running satisfactorily.  Running the media player on 49 mbs might not be a fair test.  Just adding another 256 would do wonders I think, and it's cheap enough for testing.

---

### Post by paulkruger on 2012-03-09
> **jerome1232 said:**
> He said he was upgrading it to 1 GB, which is fine to run a graphical interface (although I'm not sure a machine with only 49 MB would even be able to upgrade to 1 GB, let alone if the ram for it is even popularly sold anymore)

It is a fairly modern board.(VIA mini ITX )..standard PC133 Ram is available. Two 168 pin slots. Reason I like this is small size and the board has S-Video out which means I can plug it right into my TV where I can select music tracks without needing another monitor.

As to the Mandriva issue the only reason I even mentioned it is that the spare machine I am trying to use to install the Ubuntu from ( to a blank 500GB HD ) has Mandriva installed and it runs pretty well and I had no problems using graphic installer.  I am not trying to run install on the eventual cpu it will be installed in later.  I know the 49 MB on that is way to little and that will be upgraded before I try to use it for it's intended purpose. As it was originally a small Linux box without any GUI dedicated to be a network backup I guess 49MB was sufficient at that time.

I have no clue how to use terminal to install. (-;

(PS I am not a linux expert by a long shot ! )

---

