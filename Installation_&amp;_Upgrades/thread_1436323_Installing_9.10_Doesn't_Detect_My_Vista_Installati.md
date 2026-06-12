---
title: "Installing 9.10 Doesn't Detect My Vista Installation"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by stevepaul on 2010-03-22
Now that Chrome on Linux has caught up with the Dev channel on Windows I'be decided to give Ubuntu another try ...

My Dell laptop has 2z160 Gb HDD configured as Raid0 with AMD processors and Vista Home Premium installed, there are 2 Partitions 50Gb for Vista OS and 100Gb for my data, the remainder is unallocated ...

Using the Alternate install AMD ISO for 9.10 the installation stopped at the Grub2 loader, it didn't detect the Vista OS ...

I tried again with the i386 ISO and had the same problem ...

I aborted both installations even though there is the option to continue without loading Grub2 ...

*[COLOR="Red"]**This is the strange bit ...**[/COLOR]*

[I][B][COLOR="Blue"]I tried installing using the previous version 9.04 (both the AMD and i386) and the installation was successful both times !!
[/COLOR][/B][/I]
Obviously the easy option is to upgrade from 9.04 to 9.10 but there's a lot of data to install to bring 9.04 up to date and then a lot more data to upgrade to 9.10 ...

As I am using Mobile Broadband this is both a costly and time consuming exercise ...

From the original installs all the data seemed to be in the right places, it was just missing the Grub loader (and booting to Vista), so is there an easy way to create this or does someone have an answer to making the install recognise my Vista install ...

One of my reasons for wanting to move to Ubuntu is the fact that it supports so much ***[COLOR="Blue"]'Out of the box'[/COLOR]***

For instance one of the things that impressed me about was the fact it supported the scanner on my old (extremely) HP All-In-One PSC, something that I had great difficulty in finding software for in Windows ...

So this little *[COLOR="blue"]'set back'[/COLOR]* isn't going to deter me from moving from Windows to Ubuntu, just causing a bit of frustration at the moment ...

Please bare in mind, if your solution is to create a Grub loader my knowledge of Ubuntu is extremely limited at the moment so it will require a *[COLOR="Blue"]step by step[/COLOR]* guide ...

Thanking you in anticipation ...

A new convert (well almost !!) ;)

---

### Post by stevepaul on 2010-03-23
***Don't worry people I've found my own solution*** :D

Didn't find out why the install doesn't recognise my Vista OS but found the way to update Ubuntu without having to update 9.04 first ;)

The solution is really quite easy ...

You need first to burn a 9.10 Alternate ISO (i386 or AMD depending on your actual 9.04 install) ...

Boot into Ubuntu ...

When you're up and running insert your 9.10 ISO disc ...

You will get an option to Upgrade ...

Start the Upgrade ...

In actual fact this is probably a better way of updating as you haven't got to worry about losing your connection ...

Enjoy :D

---

### Post by Mark Phelps on 2010-03-24
The "standard" desktop CD does not undertand RAID.  As you discovered, you have to use the "alternate" CD to install to a RAID system.

---

### Post by stevepaul on 2010-03-24
Read the post ...

I didn't discover anything, I knew I had to use the 'Alternate ISO' which is what I did ...

To reiterate, neither the 9.10 AMD or i386 ISO's discovered my Vista OS so I had no option to install the Grub2 loader ...

---

