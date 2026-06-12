---
title: "Installing 14.04 LTS beside 12.04 LTS help with partitioning, please"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by wn1ytw on 2014-04-20
[FONT=Helvetica]Pardon my newbiness please. I have 12.04 installed on several machines in different ways but in none of them did I deal with setting up partitioning.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]The install in question this time is on a Asus 1015E DS03 that has 12.04 LTS preinstalled, it works well. In the last two days I have been fighting with it to upgrade to 14.04 LTS. I finally got it to get through the on the net upgrade on the second attempt to have it immediately have errors. I ended up destroying the working 12.04.4LTS and today, er.. (yesterday now) tried again with a USB stick. That finally got burned after several tries due to incompatible sticks. [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Now I got the live part working and tried to install but my choice is “something else’ which wants me to specify the mount points, etc. All way above me! I couldn’t even take screenshots as I was in the ‘live’ USB and the program I’m used to using is not on the stick. There are 4 partitions visible plus the hidden boot one. The 4th has 108GB free I’d like to give to Trusty and have 12.04 stay - so what I wish was that the old ‘alongside’ option had been  there, but not even with the 108GB free did it give me that option. I’ll put a screenshot on my dropbox of the current scheme:  [https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-19%2020%3A52%3A07.png](https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-19%2020%3A52%3A07.png) . The 12.04 is in 192GB partition — more than enough room for 4 different linux systems, so I guess if I gave half to Trusty LTS with the other half staying Saucy LTS it would work fine but I have no clue how to specify that in the setup! [/FONT]
[FONT=Helvetica]More pictures:
 
[/FONT][FONT=Helvetica]https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2008%3A11%3A56.png
[/FONT][FONT=Helvetica]
[https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2008%3A12%3A39.png](https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2008%3A12%3A39.png)[/FONT]
[FONT=Helvetica]
[https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2008%3A13%3A26.png](https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2008%3A13%3A26.png)[/FONT]
[FONT=Helvetica]
[https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2012%3A04%3A49.png](https://dl.dropboxusercontent.com/u/88302677/Screenshot%20from%202014-04-20%2012%3A04%3A49.png)[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I think I would like to add 14.04 LTS to sda2, is that possible without hosing 12.04? And just how? Or must it take sda4?[/FONT]
[FONT=Helvetica]I’d love a walkthrough of ’something else’ showing me exactly how to install trusty alongside the existing 12.04LTS install — PLEASE![/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Having read these as well as others, my head is spinning:[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]https://help.ubuntu.com/community/DiskSpace[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/[/FONT]

---

### Post by fantab on 2014-04-20
> [FONT=Helvetica]I finally got it to get through the  on the net upgrade on the second attempt to have it immediately have  errors. I ended up destroying the working 12.04.4LTS [/FONT]
Are you able to boot 12.04?

Yes you can and should install 14.04 on /dev/sda4 "New Volume 116gb".
You have 'msdos' partiion table, which means there is "ONLY 4 Primary Partitions Limit". If you use up /dev/sda4 then, in future if you need, you won't be able to make any more partitions.
As a workaround to this limitation we have an 'Extended Partition'. 
An Extended partition is a Primary Partition which acts as a container for Logical Partitions. Within the confines of an Extended partition we can have more than 100 Logical partitions.
Linux boots from a Logical Partition.
I suggest you convert that /dev/sda4 to Extended and create Logical Partitions as needed. 
You can do this with [Gparted]("http://www.dedoimedo.com/computers/gparted.html") which is there on 14.04 Live DVD/USB or install it in 12.04 if you don't have it already.

Install Ubuntu.

At the 'Installation Type' dialog choose 'Something Else' option.

Set up the '/' partition for 14.04.
(It is good idea to keep your personal data separate from you system files. Either have a separate /home partiion or a simpe linux data partition)
You already have swap... one swap partition is enough.

Good Luck...

---

### Post by wn1ytw on 2014-04-20
Yes, I have a fully functioning 12.04 LTS that I wish to retain. I have Gparted and used it yesterday to realign the misaligned sda4. Asus also sold the machine in a windows version and when they decided to sell a linux version they kept the same drive arrangement. I can easily do the convert to logical of sda4 I think. I still am confused as to the other parts   - the 'something else' section yesterday did not like any of my answers!! I'll play some more and report back before I do anything final on it! 

But if I tell it '/' for 14.04 what happens to the 12.04 on sda2? The alongside of is what I don't understand how to do, if it was just the 14.04 - no problem but that overwriting 12.04 the other day was a disaster.
off to convert to logical on sda4 at least and then bring up install again and look at least.
scott

---

### Post by wn1ytw on 2014-04-20
I removed sda4 and made it extended, then with 4th partition gone the install gave me the option to install alongside 12.04. Doing it now, thanks!
[h=1][/h]

---

