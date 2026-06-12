---
title: "Disappointed with RAID support on Ubuntu"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by LinuxSouthpaw on 2007-06-18
First of all, I think I should start out on a positive note.  After I tried the Live CD for Ubuntu, that was the first time I thought Linux might actually be a good OS for my desktop for a variety of reasons.  There's only one thing that has stopped me from completely implementing it, and that's an almost complete lack of RAID support.  I run a RAID 1 setup on all my computers, just in case a hard drive dies.  I'm not willing to compromise on keeping my data mirrored; I'll switch to a different OS if necessary.

Here's what I have tried so far (none of it with total success):

1)  Enable RAID in my mobo's BIOS and attempt to install onto the resulting /dev/mapper disk.  So far, CentOS and Fedora are the only distros I found that recognize it as one disk, but they both freeze up my (brand spankin' new) computer, so they're out of the picture.

2) Try installing onto the /dev/mapper disk as outlined here:  [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
It's a well-written article, but the whole process is a complicated nightmare.  Plus, despite following all the instructions to the letter, I ended up with a non-booting system.

3) I disabled RAID in my BIOS, then I tried going into the Feisty alternate CD and installing from there.  [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
The process seemed simple enough, but I keep running into error messages whenever I try to delete existing md devices.  I can get rid of some of them, but not all of them.  I always get a "device busy" error; the delete function has never worked for me.  Without being able to clear out the old md devices, I'm stuck.

4) I tried installing Ubuntu onto a single disk, then setting up a software RAID partition after the installation.  Not surprisingly, that didn't work; every attempt resulted in a "device busy" error.

5) After Ubuntu was installed on a single HDD, I tried booting into the Live CD and setting up a software RAID partition from there.  I didn't get any "device busy" errors, but my system refused to boot after that.


I'll wait a few days to see if I get any helpful responses, then I'll report any applicable bugs to Ubuntu and move on to another OS.  It takes me all of ten minutes to set up RAID under Windows; I may go back to running that OS instead.  Bottom line, I like the GUI on Ubuntu, but with RAID support that I could generously describe as inadequate, I can't justify using it long-term for storing my critical data.

Any suggestions or advice to point me in the right direction would be welcome and greatly appreciated, because I've just about given up on Ubuntu.

---

### Post by kidders on 2007-06-19
Hi there,

Sorry to hear you haven't had much luck.

Generally speaking, Linux's RAID support is regarded as unparalleled, having been around for a very long time. Having said that, it doesn't tend to like many of the fake RAID chipsets that seem to be appearing on more and more motherboards these days. Most of the time though, that's no bad thing, since they're often pretty crappy.

I make pretty regular use of RAID too ... a lot of the time, it's simply the best way of protecting against hardware failures. However, even if on-board RAID chipsets were perfect in every way (which they couldn't be further from being!), the idea of replacing one single point of failure (a hard disk) with another (the RAID controller) always seemed questionable to me.

To be honest, I would suggest buying a proper RAID controller, or using proper software RAID, rather than falling in between the two.

Exactly what kind of setup is best is very purpose-specific (so this example might not be applicable to your situation), but where the amount of data being stored is small (ie not too far into the terabyte range), I tend to opt for software RAID. Where the data is particularly critical, I like to distribute the array over a couple of machines. Often, the most flexible approach is to keep only parts of a system on a RAID array (ie rather than the whole OS, along with all the data), because arrays can be created and destroyed on the fly with a single command, and are easily swappable between machines, regardless of CPU architecture.

What kind of operation are you running?

---

### Post by bsmith1051 on 2007-06-21
> **kidders said:**
> I would suggest buying a proper RAID controller, or using proper software RAID, rather than falling in between the two.
Can you suggest a proper hw RAID controller, i.e., one (or two) that are known to work easily with Ubuntu?

I'm in the typical boat -- I'd expected to setup a "hw" mirror of my boot drive, same as I've been doing in Windows, but now learn that it's a huge process and less than ideal if accomplished.  Even setting-up the Linux sw raid sounds like a pain, on the boot drive(s) at least.

---

### Post by kidders on 2007-06-22
Hi there,

I'd be reluctant to make a suggestion that involves other peoples' money. :-/ The best approach would be to ask your retailer what he recommends for Linux platforms. He'll be able to roll *all* of his customers' experiences into once sentence for you ... after all, Linux + hardware RAID isn't exactly a rare combination. It's important to remark though that fakeRAID and true hardware RAID are in completely different ballparks. If you even considered using fakeRAID on your system for a *moment*, true hardware RAID (and the expense that goes with it) probably isn't right for you.

> **bsmith1051 said:**
> I'm in the typical boat -- I'd expected to setup a "hw" mirror of my boot driveThere are two issues here, I think.[LIST=1]
[*]Modern fakeRAID manufacturers often either choose to, or are manipulated into, neglecting Linux, which leaves its developers playing catch-up, while they reverse-engineer drivers for them. As a result, Linux lacks good support for some of them.
[*]Since Linux users often expect far more from their RAID than Windows users do, fakeRAID support may not be quite as high a priority for developers as would be ideal. I may, of course, be mistaken, but in my experience, on-board RAID controllers just don't seem to cut it in the eyes of the average Linux user. In general, they fail to compete with Linux's own software (which is all fakeRAID is anyway) RAID implementation, and are completely out-classed by reputable hardware solutions.[/LIST]Having said all that, given the right on-board controller (which I'm afraid I have no idea about), many Linux users seem to have a perfectly satisfactory experience of using it. One place that might be worth looking for information on what's supported is the kernel configurator, which contains a list of virtually every device supported by the Linux platform, along with some general comments on many of them.

Anyhow, I hope that helps a little.

---

