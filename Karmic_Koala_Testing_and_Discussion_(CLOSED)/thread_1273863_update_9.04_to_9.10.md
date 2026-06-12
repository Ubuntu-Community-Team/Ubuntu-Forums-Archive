---
title: "update 9.04 to 9.10?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by levian on 2009-09-23
i tried to update my 9.04 to 9.10, but after the update completed, it wouldn't even boot, displaying only the black screen. same goes for clean installation. have anyone tried the update? or installed 9.10? thanks!

---

### Post by QIII on 2009-09-23
I hope you backed up your important files...

If you attempted to install using the Alpha 6 iso (September 17), you are probably running into the same sorts of problems everyone else has.

I ended up with a totally borked system trying to install fresh and eventually had to reinstall Alpha 5 and dist-upgrade to Alpha 6.

Alphas are not ready for prime time.  They are not recommended for "production" use.

As for what you can do...

STOP!  Don't do anything until you can recover your important files if you have not backed them up.

There are a couple of products you can use to *hopefully *get your files safely back from your drive and on to removable media.

Google Photorec and TestDisk -- research them.  If you want to use one of them, download it and carefully follow all instructions.

Someone will probably pipe up in a few minutes with other suggestions for file recovery.

I'll have to do some research to see what you might be able to do to get running.

Do you not even get a GRUB2 screen?

---

### Post by levian on 2009-09-23
i was glad i did a backup! therefore i am less panicky to have the system not boot up after the upgrade. i have display problem with my 9.04, that's why thinking about trying out the upgrade, see if it helps. 

the display problem thread: [**here**]("http://ubuntuforums.org/newreply.php?do=postreply&t=1273863")

---

### Post by QIII on 2009-09-24
I'm not sure if the Alpha 6 iso is cleaned up yet.  I've heard that it is, but...

Like I said, I reinstalled Alpha 5 and then did a dist-upgrade (not upgrade) to get Alpha 6 running.

If you really want to go through the pain of running an Alpha (I have it on two test boxes, 32 and 64 bit -- but I also maintain 32 and 64 bit Jaunty on my "main" boxes), it might be worth getting a copy of Alpha 5 and running it Live to see if you encounter problems.

If that goes well, install Alpha 5 and do a dist-upgrade.

---

### Post by levian on 2009-09-24
i am not quite following. what are Alpha 5 n Alpha 6?

---

### Post by QIII on 2009-09-24
Ubuntu 9.10, Karmic Koala, is not a final release yet.  It is an "Alpha", which means it is still in testing.  The next higher level is a Beta.  Then comes a Release Candidate followed shortly by the official Release.

[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

Right now, Karmic is in its 6th Alpha, so Alpha 6.

This means that it is not stable and may have problems that make it unsuitable for a "production" or regular use system.

In my case, I first attempted a clean install of Alpha 6 from the iso provided on September 17th.  That resulted in a borked system on both my 32 and 64 bit machines.  I had to back down and reinstall Alpha 5 on each, then dist-upgrade to Alpha 6 to get it to work.

---

### Post by levian on 2009-09-24
ah, i am getting the bigger picture now. i didn't realize alpha having so many versions. so do you suggest that i download Alpha 5 for it to at least work?

i was trying fedora just now, it too have the display problem like my ubuntu 9.04. makes me wonder if all os that have similar platform like ubuntu will be having the same display problem as well.

---

### Post by vrkalak on 2009-09-24
I recently installed Karmic 9.10 in a dual-boot with LinuxMint-7 on my PC.

Of course, I backed up all my files, desktop settings and bookmarks, before I started.
I downloaded the Ubuntu Karmic 9.10 ISO on my older laptop and burned it to CD (as a back-up plan)
I then did a system/kernel/distro upgrade in Ubuntu Jaunty 9.04, via terminal.

The ISO files took 23 minutes to download on my laptop; 
while, the Karmic 9.10 distro/kernel upgrade too over 5 hours on my PC.

So far, no real problems to speak of.
My Conky does not open at start-up, like it should, and it blinks occasionally.  IDK.

On the Gnome desktop, I lost all borders, until I re-booted.  Otherwise, nothing really.

---

### Post by levian on 2009-09-24
i tried upgrade 9.10 from my 9.04, it stopped at the boot up n gave me a black screen. i then tried downloading the ISO, that too gave me a black screen. however, i am not sure which ISO did i download. most probably Alpha 6 since it was just last few weeks. which ISO was yours?

does LinuxMint required a lot of processing power? i was trying n it loaded but when i clicked on "install" on the desktop, it freeze.

---

### Post by mikewhatever on 2009-09-24
May I suggest you wait for the final release of 9.10. As mentioned above, 9.10 is not yet finished, and all the releases until Oct 29th are intended for developers and testing community. Problems like yours are commonly expected in developmental releases.
As for Linux Mint, it should require about the same resources as Ubuntu.

---

### Post by levian on 2009-09-24
i notice that on my laptop (asus s1300), many os failed to install. so far the successful ones are ubuntu 9.04 n puppy linux. the problem with ubuntu 9.04 was the graphic ([**here**]("http://ubuntuforums.org/showthread.php?t=1260011")), the problem with puppy was unable to setup a network printer. the rest of the os (even ubuntu 8.04), it lagged bad! very bad. what are the possible problems?

---

### Post by ToshibaLaptoplinux on 2009-09-24
Save yourself the pain and suffering and don't do it!!! TOTALLY borked my PC. Fortunately I backed up and my HOME is on a separate partition.

---

### Post by QIII on 2009-09-24
No matter what you do:  If you don't back up you risk piercing yourself with a member of a subset of fastening devices characterized by long, thin, conical shafts wrapped in sharp, raised helical ridges.

[http://en.wikipedia.org/wiki/Screw](http://en.wikipedia.org/wiki/Screw)

This turn of events may also have a vulgar connotation ...

---

### Post by trugate on 2009-09-25
Is everyone the swedish chef on this topic?  bork bork bork borked!

I too suffered the black screen, tried uninstalling video drivers among other things but no go.  I was just messing around with a few apps and look forward to the ppa functionality of 9.10, so I gave it a try.  I would love to know what's causing it though.

Back to 9.04!  Anyone know how to go back from an upgrade through update manager, or should I start fresh (was just cleanly installed yesterday, so I wouldnt lose anything but the packages i installed)?

---

### Post by levian on 2009-09-28
> **trugate said:**
> I too suffered the black screen, tried uninstalling video drivers among other things but no go.  I was just messing around with a few apps and look forward to the ppa functionality of 9.10, so I gave it a try.  I would love to know what's causing it though.


same here, but i guess we should be waiting for the stable release october like what **mikewhatever** mentioned. i tried the rest of the ubuntu based os - 9.04, 8.04, mint, fedora, etc. n still ended up with the same graphic problem (**[here]("http://ubuntuforums.org/showthread.php?t=1260011")**) like what i faced in my current 9.04. are there any other os that i should be trying?

---

### Post by Tom Tiger on 2009-09-28
And mine also went the way of the Bork :-)

Test system, Intel Centrino 1.1 ghz 768 mb of ram, Fujitsu Siemens Stylistic 5021,  the upgrade went flawlessly, but after the restart, black screen and that's about it :-)

Fortunatly this was a test for me to see how tablets are supported under 9.10,  8.10 my stylistic worked perfectly (after a lot of tweaking) 9.04 refused to rotate my stylus but worked pretty much out of the box and 9.10 is a no go and no show.... then again, it's an Alpha release, I'm not suprised. By the way, this was a dist-upgrade from 9.04 to 9.10r6.
So no clean install.

Well time to see what went wrong :lolflag:

---

### Post by 16sinker on 2009-09-28
Just for the record, I upgraded last night. That would be 9.04 to 9.10. "sudo update-manager -d" in a terminal without the quotes. Took about 3 hrs total and had no glitches. My computer is a Dell Inspiron 8000 with 512 mb of ram and it was running Jaunty with no problem. Koala alpha is running fine and I'm looking forward to updating to the release candidate and the final release on Oct. 29. I too would advise waiting for the final, unless you are the adventurous sort.

---

### Post by jheaton5 on 2009-09-28
Totally Borked!  How could that happen?  Fortunately I backed up all my data.  I can access my data on the partition with Debian on another partition.  I may stick with Debian for a while, but the screenshots of Karmic are awesome.

---

### Post by NormanFLinux on 2009-09-28
Wait until the official release. Otherwise you're asking for problems. I have a fresh installed Kubuntu Netbook Edition Alpha6 running but then I haven't upgraded from Jaunty.

---

### Post by levian on 2009-09-28
i updated mine through "sudo update-manager -d" from 9.04 as well. after restart it became black screen. waiting tightly for the october release!

---

### Post by nhasian on 2009-09-29
you mentioned you had a "totally black screen"

if you press enter, do you see the tty1 terminal login screen?  If so, simply switch back to tty7 with Control-Alt-F7.  This is a known bug.

---

### Post by vrkalak on 2009-09-29
I did a "apt-get update, apt-get dist-upgrade" through the 9.04 Update Manager via Terminal.  It seemed to work well, except for a couple of minor glitches.  Easily fixed.  The main problem I had, was that Grub2 wouldn't recognize my other Linux OS.  It would boot straight to Karmic with no other choices.

I then re-partitioned and installed Ubuntu Karmic 9.10 from an ISO CD, I had made earlier the same day.  Everything worked, better than I had imagined ... perfect!!

I definitely recommend doing a 'fresh install' over a dist-upgrade.  The Karmic that came up with the new install, from the ISO files I grabbed off DistroWatch.com, was a lot better than the Karmic that booted from the update/upgrade I had done earlier.

I am really loving the new Ubuntu Karmic Koala 9.10, Alpha 6 and can hardly wait for the Final Release.

---

