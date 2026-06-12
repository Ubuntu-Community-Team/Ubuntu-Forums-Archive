---
title: "how do I downgrade X in Lucid?"
date: 2010-01-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DouglasAWh on 2010-01-10
I'm trying to run Lucid in a VM (VirtualBox 3.1.2).  I already uninstalled xorg.

I tried adding [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) to my repos and used the karmic version of those repos but I could never see old versions in Synaptic or 
```

apt-cache policy

```

I then tried to install from a CD, which didn't work.  So, I commented out all my repos except the CD, thinking that would force it to use the CD.  That did not work.  I tried to install xserver-xorg-core, xserver-common, xorg and xserver-xorg and all of them said there were dependencies.  I'd assume those dependencies were on the CD...

Now that I have X uninstalled, what's the easiest way to get the Karmic version of X installed?

Thanks!

---

### Post by kansasnoob on 2010-01-10
> **DouglasAWh said:**
> I'm trying to run Lucid in a VM (VirtualBox 3.1.2).  I already uninstalled xorg.

I tried adding [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) to my repos and used the karmic version of those repos but I could never see old versions in Synaptic or 
```

apt-cache policy

```

I then tried to install from a CD, which didn't work.  So, I commented out all my repos except the CD, thinking that would force it to use the CD.  That did not work.  I tried to install xserver-xorg-core, xserver-common, xorg and xserver-xorg and all of them said there were dependencies.  I'd assume those dependencies were on the CD...

Now that I have X uninstalled, what's the easiest way to get the Karmic version of X installed?

Thanks!

So you were trying to revert from the xorg edgers ppa version of xorg to the original Karmic version?

If so you shouldn't have uninstalled any xorg packages at all. You just leave the xorg-edgers ppa installed then go to terminal and run:

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge xorg-edgers
```

```
sudo apt-get install --reinstall linux-libc-dev
```

Then make sure the ppa is removed and run "apt-get update" (or reload software sources).

Since you removed so many packages you might try from a terminal (if you can access a terminal in your installed Karmic):

```
sudo apt-get install --reinstall ubuntu-minimal
```

```
sudo apt-get install --reinstall ubuntu-standard
```

```
sudo apt-get install --reinstall ubuntu-desktop
```

```
sudo apt-get update
```

```
sudo apt-get -f install
```

And see how many errors you encounter ;)

---

### Post by slakkie on 2010-01-10
> **kansasnoob said:**
> 

Hello, that is a lot of stuff to type

```

# contents of /etc/apt/preferences

# Make sure the ppa-s have a low prio
Packages: *
Pin: origin ppa.launchpad.net
Pin-Priority: -100

```

Now you should be able to downgrade X to karmic by doing:

sudo aptitude install xserver-xorg/karmic

Otherwise, run apt-cache policy xserver-xorg, grab the correct version:

```

$ apt-cache policy xserver-xorg
xserver-xorg:                  
  Installed: 1:7.4+4
  Candidate: 1:7.5+1
  Version table:
     1:7.5+1 0
        990 ftp://ftp.nl.debian.org unstable/main Packages
 *** 1:7.4+4 0
        900 ftp://ftp.nl.debian.org testing/main Packages
        100 /var/lib/dpkg/status
     1:7.3+20 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

```

and install it like:

sudo aptitude install xserver-xorg=1:7.3+20

That should ideally downgrade all dependencies X has. Otherwise:

dpkg -l | grep xorg  and repeat the action for all packages.

You might want to have a look at this posting for more explanation: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

---

### Post by DouglasAWh on 2010-01-10
> **kansasnoob said:**
> So you were trying to revert from the xorg edgers ppa version of xorg to the original Karmic version?

No. I was trying to get ANYTHING lower than the Lucid X because VirtualBox does not play nicely with the X in Lucid.  When I tried installing the second version that showed up in apt-policy finally, it told me xserver-xorg needed to be uninstalled first.  So, that's what I did.

I think it was this syntax I needed

```

sudo aptitude install xserver-xorg=1:7.3+20

```

I'll give that a shot when I get in to work tomorrow. Thanks!

---

### Post by ranch hand on 2010-01-10
I would wait and download A2 and try it.  You may get it to run in VB your way but it will not truly by 10.04 at all.  The entire Xorg system has been updated everyday for the last few days.

We just got a new kernel version too.  I really think that you are going to have a large problem trying to run 9.10 x-stuff on 10.04 with the 2.6.32-10 kernel.

If you try this I sure hope you are planning on running wit hwhat ever driver the system throws your way because I would be shocked if any other driver, designed for 10.04-testing will work on top of x designed for 9.10.

---

### Post by DouglasAWh on 2010-01-10
> **ranch hand said:**
> We just got a new kernel version too.  I really think that you are going to have a large problem trying to run 9.10 x-stuff on 10.04 with the 2.6.32-10 kernel.

One step ahead of you. Already downgraded the kernel. that was cake. :)

VBox actually gives a warning saying that xorg support for the lucid xorg is experimental. It goes ahead and installs the additions, but clearly doesn't work.

Is there a virtualizer that works well with the current lucid? I need to do some testing for work.  My host is Fedora and I tried to install VMWare player, but it was crashing all the time and VMWare requires the kvm kernel module which messes up VBox. It's pretty easy to go back and forth, but I'd rather not.

That's a long way of saying I highly doubt the newer stuff in alpha 2 will work.  It's up to VBox to step it up.

---

### Post by cariboo on 2010-01-11
I installed the latest daily build, on the latest version of vbox on my office computer Friday, and it worked without the problems I was having with the A1. I was playing with grub theming, and as it is now it sits with a black screen at the grub menu, but thats a question for another thread.

---

### Post by DouglasAWh on 2010-01-11
> **cariboo907 said:**
> I installed the latest daily build, on the latest version of vbox on my office computer Friday, and it worked without the problems I was having with the A1. I was playing with grub theming, and as it is now it sits with a black screen at the grub menu, but thats a question for another thread.

Interesting. I did do updates, but I don't know if that was after I downgraded the kernel or not.  

using VBox 3.1.2?  What problems were you having?  My main issue is that it grabs the mouse rather than allowing me to move back and forth.  It irritates me to no end.

---

### Post by cariboo on 2010-01-11
With A1 I was having the same problem, as well as the mouse pointer disappearing intermittently. I'm running:

[list]
[*] Kernel 2.6.31-18
[*] vbox 3.1.2 r56127
[*] Lucid daily build 12/07/10
[/list]

---

### Post by DouglasAWh on 2010-01-11
> **kansasnoob said:**
> 

```
sudo apt-get -f install
```

And see how many errors you encounter ;)

This was the only one of the commands you gave me that actually worked...

X is back up and running.

How do I know if I have the daily?  Just do apt-get update then apt-get upgrade?

VBox still not working after updates

```

dwhit@vs-lucid:~$ uname -a
Linux vs-lucid 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:54:12 UTC 2009 x86_64 GNU/Linux

```

---

### Post by cariboo on 2010-01-11
You're a couple of kernel updates behind, as of todays updates, this is the current kernel:

```
uname -a
Linux lucid 2.6.32-10-generic #14-Ubuntu SMP Thu Jan 7 17:38:08 UTC 2010 x86_64 GNU/Linux

```

---

### Post by DouglasAWh on 2010-01-11
> **cariboo907 said:**
> You're a couple of kernel updates behind, as of todays updates, this is the current kernel:

```
uname -a
Linux lucid 2.6.32-10-generic #14-Ubuntu SMP Thu Jan 7 17:38:08 UTC 2010 x86_64 GNU/Linux

```
Ah, dist-upgrade was needed, not just upgrade

However, with 

```

uname -a
Linux lucid 2.6.32-10-generic #14-Ubuntu SMP Thu Jan 7 17:38:08 UTC 2010 x86_64 GNU/Linux

```

I still don't have working additions.

My xserver-xorg is now 1:7.5+1ubuntu1

The testing I need isn't time sensitive.  We'd like to be ready to deploy the LTS when it comes out, but we don't really have to be...so I'll wait for a new version of VBox for now I guess.

---

### Post by ranch hand on 2010-01-11
Why not do something radical and try it on real hardware?

Really seems to be working nicely.  That is for me, on my box, today.

---

### Post by cariboo on 2010-01-11
+1 for using real hardware, I'm running Lucid on my main system at home, and running it in vbox on my office system mainly just to play with something when I'm bored. :) BTW I'm self employed, so I don't have to worry about the boss. :)

---

### Post by DouglasAWh on 2010-01-11
> **ranch hand said:**
> Why not do something radical and try it on real hardware?

Really seems to be working nicely.  That is for me, on my box, today.

I have actually...at least twice, but I think more.  I can't use it at home where it's on hardware until the ATI driver issue is fixed...which it may be now.  I haven't had a second to check.  

Actually, I could be done with my first test when I come in in the morning.  I'll have to check closer to release, but we had a problem with Karmic, so we decided to skip it.  As far as we can tell, Lucid should have the same problem, but we figured out a fix after we decided to go back to Jaunty (since those machines need to start being deployed on the 18th and we had earlier deadlines and such).  

My office is a bit crammed with machines, so I don't want to rely on having *functioning* machines available.  Really, space is the larger concern as at the moment I have literally no where another laptop could go...except on top of another laptop.

---

### Post by ranch hand on 2010-01-11
Well all I have is one desktop but plenty of drive room.  I am also running on ATI video.  Using the generic driver I have had no real problem.

If you have room for running in VB you have room on the drive for a dual boot.

I just do not see the purpose in "testing" in VB.  There is too much that is not really running as it really does in a real environment.

---

### Post by DouglasAWh on 2010-01-11
> **ranch hand said:**
> 

If you have room for running in VB you have room on the drive for a dual boot

Sure, there's space, but that's not the issue.  I can't just take an hour to boot up into an unworkable environment.  I have to get work done.  If that works for other people, fine.  It's not going to work for me.

I need to test things like scripts and AnyConnect, things that will work just fine in a VM.  I'm not doing driver or performance testing.  The VM is mainly for keeping an eye on things.  That's why it's important I have seamless access.  I want to go in type a command and not look at it again for an hour (or 4 hours).  That system simply doesn't work with dual boot.

There was a bug filed about ATI cards have xorg spike the CPU to unusable levels.  I'm not the only one with the issue.  I really doesn't affect me whether the bug affects you or not.  I'm glad you like your system.

Also, this has gotten way off topic...

EDIT: as it turns out, on Launchpad I *am* the only one this affects...though it was confirmed.  I swear I saw it somewhere else... I wonder if my problem was because I did an upgrade from Karmic...which I did an upgrade from Jaunty.  the bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/493057](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/493057) Either way, it might be time to do an update on that partition...

EDIT2: there's a thread here on the ATI issue, which was resolved with new updates, though apparently not ones to the kernel. Don't care at this point.

---

### Post by ranch hand on 2010-01-11
Sorry to get off topic.  Just a curious bugger.

Haven't seen too many complaints about cpu spikes in the forum.  You must have a card that is another off the wall one, seems to be a lot of them.

Have FUN.

---

### Post by DouglasAWh on 2010-01-23
just for anyone else looking into the VBox problem, with the last set of dist-upgrade updates, still no working additions.  Will report back here when they work...assuming I remember.

---

