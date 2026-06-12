---
title: "Help with data recovery"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by jurjiu-cata on 2014-03-31
First of all, I'm not an ubuntu newbie. I've installed, reinstalled and tinkered with my ubuntu install hundreds of times, and had no problems. This time however, I decided to ask for help.

So, long story short, during a Ubuntu reinstall I accidentally clicked to wrong option, and my whole drive was formatted. To be more specific, I clicked the option that said "Erase everything". I had dual bool Ubuntu 13.10 with Windows 8.1.

Now I'd want to get my data back ( family photos, university projects, personal projects, etc ). I had windows installed on a ~200+ GB partition, and the data I'm interested in on a separate partition about ~140 GB in size.

So, after a quick google search I came across various tools that supposedly are able to recover data from messed up partitions. I'm talking about Gparted ( with gpart ) and Testdisk. I also tried Parted but didn't manage to make it work the way that I wanted.

Quick state of how things are now. These are my current partitions, as shown by Gparted:

[ATTACH=CONFIG]251618[/ATTACH]

Partitions in Testdisk:
[ATTACH=CONFIG]251621[/ATTACH]

What I did so far was to use Testdisk to try and discover my lost  partitions, and (if possible) to recover them. However, I always get the  following message:

[ATTACH=CONFIG]251622[/ATTACH]

Yesterday it was telling me I needed 900GB of space to recover my data, now it tells me I need 14TB of space to recover my stuff.

Also, during the scan i get the following errors:

[ATTACH=CONFIG]251623[/ATTACH]

I searched the internet a bit, and the tesdisk forums. I found some answers, but none of them addresses all my problems. Usually I'm more brave with the things I try, but now, knowing I can loose all my personal stuff, I'm a bit more reserved.

So...can anyone make any sense of all the details I wrote here? Can someone tell me how can I get my old partitions& data back? /sigh

I'm not stuck to using Testdisk, as long as the new tool can recover my data

Thanks in advance..

LE: After some more tinkering, I managed to save my files. /wohoo. I still don't know how to get my old partition table back, but I don't mind reinstalling everything that much, as long as I have my files back. If anyone has any suggestions on how to do that, they're more than welcomed. Otherwise, this issue is solv'd :)

---

