---
title: "At the moment, how useable is Ubuntu Lucid Lynx 10.04?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gymophett on 2010-03-13
So, I have a partition for Windows, one for Linux, and another for all of my files. 
I really want to give 10.04 a go, tried in Virtualbox, with a few minor crashes.

But if I ran it on my Linux partition, would that be a bad idea?
If it did crash, I wouldn't lose any files and I would have my Windows partition.

Is it worth it?

---

### Post by cariboo on 2010-03-13
Why not check [here]("http://ubuntuforums.org/forumdisplay.php?f=377"), to see what usability issues there are. For me Lucid works great on 2 systems, and just about great on another system..

---

### Post by MasterNetra on 2010-03-13
It runs on my old desktop better then any other modern Distro and even better then Karmic or Jaunty. Its a bit buggy still but really what do you expect from a alpha release?

---

### Post by gnomeuser on 2010-03-13
I run it on every one of my machines and subject them so all kinds of intensive daily use. It is very stable, not without its bumps but usable and pleasant.

---

### Post by Phrea on 2010-03-13
I'd wait if I were you...
You can always run the live cd, and play with it, but a serious install on a default machine, I would not do that yet.

You could wait and install the RC, and just install the updates, to avoid the rush hour when Lucid stable arrives.

---

### Post by gnupipe on 2010-03-13
> **gymophett said:**
> So, I have a partition for Windows, one for Linux, and another for all of my files. 
I really want to give 10.04 a go, tried in Virtualbox, with a few minor crashes.

But if I ran it on my Linux partition, would that be a bad idea?
If it did crash, I wouldn't lose any files and I would have my Windows partition.

Is it worth it?

It's not worth of it. Don't waste your time unless you want to report bugs.

---

### Post by Uncle Spellbinder on 2010-03-13
Bottom line: If you're into testing and want to contribute by filing bugs and testing, install it. It's quite stable, actually. But an alpha build is just that....an alpha. Anything can break at any time. There are 2 mote betas and an RC to go. The first beta is due March 19.

---

### Post by chriswyatt on 2010-03-13
I tried a Beta release before and ended up with an unbootable system because I wasn't clued up on what a partial upgrade was.  Luckily I was dual booting with a stable version of Ubuntu.

The beta version of Karmic didn't give me any grief, I found it very stable for a beta release.

Use at your own risk is basically the theme here.

---

### Post by Paqman on 2010-03-13
Unless you're confident that you could troubleshoot and fix problems on your own, don't run the development branch. There are sizeable updates every day, and any one of them could cause serious b0rkage.

Getting involved in testing is a great way to help out Ubuntu, but don't run it as your main system.

---

### Post by 3rdalbum on 2010-03-13
I had a really stable, absolutely-nothing-ever-breaks experience with Lucid on my netbook. And then yesterday I applied the last 24 hours of updates; the new version of Plymouth had been updated, but not the new version of mountall that needs to know about the new Plymouth.

My netbook wouldn't boot, I had to boot into Android and check Launchpad to find out how to fix it. (which was thankfully easy; I downgraded Plymouth, and now the new Mountall is available anyway).

If you can stand the slight possibility of having something break and needing to go into recovery mode to fix it, then you should upgrade to Lucid. It's a very nice distro.

---

### Post by Tibuda on 2010-03-13
The last I used Ubuntu, I had a dual boot between the development version and the stable version, sharing the same /home partition. It was kind of a rolling-release system with a stable fallback. The development release is not really "broken", but things **can** break sometimes.

---

### Post by Irihapeti on 2010-03-13
As the saying goes, your mileage may vary.

I've got it running almost flawlessly on one netbook, rather bumpily on an old laptop (mainly graphics issues) and not at all on another computer (won't boot).

All that could be totally obsolete tomorrow, of course.

I find it helps to think about what you'd do if the worst happened. (Backups come in handy here.) Unless "panic like mad" is your main option :), once you have that sorted, you can enjoy the ride.

---

### Post by mkvnmtr on 2010-03-13
I have tried it four times in virtual box. Installed evey time and looked great. Then an update left me not even able to get to get to a command line. Bear in mind none were a standard install. All were minimal installs with LXDE or XFCE4. I probably installed some apps that did not play well. But I will try again with a beta. If I had a partition I would probably install a regular install. Would not recomend it to anyone that asked the question should I install 10.04. Will not be long before it is ready.

---

### Post by scouser73 on 2010-03-13
I've been using Lucid alpha 3, it's the only PC that I have and I've got to say that for me, it's been incredibly stable.  I'm backing up on a daily basis on the account if anything happens, then I'm safe.

---

### Post by NightwishFan on 2010-03-13
I used it for a few months until I switched to Debian. I have been using the development releases since Gutsy. (Though not on my main machine). I have found this to be the most stable development release so far. I have reported the issues I had, you can check my launchpad account about that. They have all been fixed by now. I say go for it, but make sure you read the release notes.

10.04 looks like a great release, but I am unsure if all the changes are suitable for the LTS. It just seems counter purpose. In the description for the LTS it says they will not drop newer technology or frameworks, but I suppose plymouth does not fit that? For the last one it was pulseaudio.

---

### Post by witeshark17 on 2010-03-13
Seems like very nice progress. :popcorn:

---

### Post by markyb73 on 2010-03-14
I run it on a spare partition just to play with it, it does seem very stable but i will resist and keep karmic for day to day. As someone else said here i will probably grab the rc before the mad rush starts :D I think this will be a great release!

---

### Post by ssam on 2010-03-14
i've had it running on a partition for ages. last night i updated my main partition on my desktop to lucid.

seems to be one of the most stable dev versions ever (i think thats the plan). should be a good release.

before you actually install it there are a few things.
install testdrive ( [https://launchpad.net/testdrive](https://launchpad.net/testdrive) ) and check that any important apps that you need work.
make a live cd/usb-stick for a daily iso (you can use the one that testdrive downloaded), and check that you can boot it and that your hardware works.
do a backup.
make sure you know how to connect to your network and use the package manager without X running. and read about using chroot from a live cd to fix things. most likely you wont need these skills, but if a bad update comes though you may.

---

### Post by Cushie on 2010-03-16
> **gymophett said:**
> 
But if I ran it on my Linux partition, would that be a bad idea?

Is it worth it?

Yes it is , I installed last night and did some preference tweaks this morning and it looks great.

Partitioning can involve some risks so suggest make a couple of ext4 partitions first before you boot the CD and then install / & home to those.

Go for it!
:)

---

