---
title: "Destroyed My Hard Drive"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Memnochxx on 2008-02-17
After installing ubuntu I installed kde and xfce to check them out. Later I planned on installing another distro and sharing /home between them so I opened up the disk partitioner. The disk partitioner started scanning my drives and my hard drive began making clicking noises and gparted failed to do anything else. I restarted my computer and continued to hear loud clicking and scratching noises coming from it. My computer didn't boot from the hard drive. It gave no error. So I popped in the installation disc to check out my hard drive, it didn't detect one. I took that out and started the computer again. This time it started up and the kubuntu splash screen appeared, followed by lots of text and some errors. So I figure maybe it's not totally destroyed after all if that came up and I decided to try reinstalling. I got the following error trying to partition the drive:

```
input/output error during read on /dev/sda
```

So, now I'm out a hard drive? It would be nice if I was told that default programs of my new operating system would destroy my computer.

---

### Post by gpilkay on 2008-02-17
This doesn't sound like an operating system error.  Usually with read/write fail, you have suffered a physical hard drive crash.  There's no real way for an OS to do that, you'd at least have an error about the format or allocation, not read/write.  The inability to actually detect the hard drive pretty much clinches it....

You could try booting from a Live-CD and see if you can mount and recover from it, but usually when this error happens it's gone, though I tend to smash my old drives with a hammer for good data security and stress relief.

---

### Post by Memnochxx on 2008-02-17
So it's a huge coincidence that this hard drive which has been working with XP for years dies when I install Ubuntu?

---

### Post by wpshooter on 2008-02-17
Memnochxx:

I seriously doubt that the problems you are having have anything to do with your attempting to install Ubuntu.

If you have an actually physical problem with your hard drive which the clicking noise you mention "MAY" be an indication of, then the fact that you were installing Ubuntu at the time this happened was probably just a pure concidence. 

Do you have any information on the computer hard drive that is of any value/that needs to be saved ?  If not, then why don't you use another computer to go to [www.killdisk.com](www.killdisk.com) and download the killdisk program and put it on a CD and then boot to that CD and use Killdisk to WIPE the hard drive completely clean and then try the installation of Ubuntu again.  Or alternatively, you could go to the manufacturer of your hard drives website and download their diagnostic software and see if there is an actual physical problem with your hard drive.

Good luck.

---

### Post by Lord Landis on 2008-02-17
> **Memnochxx said:**
> So it's a huge coincidence that this hard drive which has been working with XP for years dies when I install Ubuntu?

Yeah, pretty much.

Here's a trick that may let you get the drive up long enough to recover any data you might have put onto it: stick it in a plastic bag with some dessicant (you know, the little packs of silica gel that come with new shoes, most drugs, and a host of other things) and throw it in the freezer for a few hours (at least 6).  Once it's bitterly cold, take it back out, let it warm up enough that it *does not have any condensation on it* but is still cold.  Reconnect it to your system and try to boot up.  I know it sounds odd, but if there are problems with the bearings or stuck parts, the cold temperatures can cause just enough contraction to loosen them back up.

---

### Post by Crafty Kisses on 2008-02-17
> **Memnochxx said:**
> So it's a huge coincidence that this hard drive which has been working with XP for years dies when I install Ubuntu?

What do you want, a refund? To be honest, it could be a coincidence man, your upset right now and I can understand, but don't start pointing fingers until you know the root of the problem, and what it sounds like to me, is your HDD went bad, since you did say it was clicking, which that is a HUGE indication that your HDD is going bad.

---

