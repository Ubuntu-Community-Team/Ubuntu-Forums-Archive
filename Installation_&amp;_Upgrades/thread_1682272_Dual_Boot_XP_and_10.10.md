---
title: "Dual Boot XP and 10.10"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Clive McCarthy on 2011-02-05
The instructions for creating a dual-boot system are vague and out of date.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

The page even reads:

[COLOR="Red"]&#8226;Choose the First Option (It should be *something like*: "Resize IDE1 master, partition #1 (hda1) and use freed space").[/COLOR]

[my italics]

Which does NOT have the clarity such an important step demands. I'm setting up a clean dual-boot system. I have installed XP and specified that XP should use half the HDD. When I get to the installation screen from the Ubuntu 'live'CD it seems to show the XP partition as the target and NOT the free space. The advanced options simply lead to yet more potential confusion. :confused:

I have simply clicked 'forward' and am hoping for the best...

... well it worked. But I still think it is UGLY.

---

### Post by Swagman on 2011-02-05
Don't be afraid of the advanced options.

You simply need

/boot <-- dunno about that but I made a small partition for it anyway
/ <---root
/swap
/home

[img]http://localhostr.com/file/ePwQuiS/Ubuntu155.jpeg[/img]

---

### Post by oldfred on 2011-02-05
You do not need boot and yes they have messed up the installer and it is altogether too easy to delete your windows.

Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Everyone has different options about optimal partitioning. I only had / (root) and swap with a small shared NTFS partition with XP for several years.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

