---
title: "Problems With Setting Up A Separate /home Partition"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by johncs2008 on 2008-07-20
This is only my first ever post to a Linux forum.

I have been using Ubuntu on and off for a year or so and at that time, I was a complete newbie (although my previous years of allowing myself to be ripped off by a certain, Mr. Bill Gates and his empire meant that I hadn't actually realised that I was only a newbie then).

Because I was a newbie, I struggled to get certain things (mainly pieces of hardware) working in Linux and at times, that would push me back to Windows because I believed that this shouldn't be happening (because I thought that I was more of an expert than I actually was).

Nevertheless, I have gradually built up my knowledge of Linux by reading the posts in this forum (and others), following the appropriate advice in them and in other tutorials on the web which have been referred to from these forums and other such websites. Google has helped a lot in this (although there has been times when I have felt that this has been a fruitless task) and I have also bought a number of books on the subject which have also helped.

Even today, I can now happily claim that I'm STILL no expert in Linux. However a few months ago, I finally managed to get everything in working order in Linux. I am happily using Ubuntu 8.04 and have even decided that its default GNOME desktop is my favourite. This has been achieved without me posting a single post in these forums to ask for help (because someone else has usually already asked my question and so, I've just needed to go by the answers that's given although I welcome the fact that this option is there if I need it, but the fact that I haven't needed to ask for help shows the power of the support for Linux which is out there) and I even managed a celebratory drink once I felt confident enough in my use of Ubuntu, to ditch Windows altogether. To this day, I have never looked back since (although unfortunately, I still have to use Windows at work as part of a policy of the organisation which I work for, which I am powerless over).

Anyway, one thing I did was to set uo a separate home partition in my installation of Ubuntu. This has been done from my live CD by using GParted to create the partition for that and then, setting that up in the installation procedure by choosing MANUAL for the partitioning. This works very well for me and has the advantage that I can reinstall Ubuntu at any time or even install a different Linux distro in place of Ubuntu, and STILL manage to have my data (ie. things like my music collection and important documents) kept intact.

This works well as long as I have only one Linux distro installed onto my hard disc. However potential problems with that CAN arise when you have have two or more Linux distros installed at the same time in a multi-boot system as I discovered some time ago when I experimented with having Ubuntu and Mandriva installed as a dual-boot system with both distros sharing a common /home folder.

Firstly, the /home directory contains not only things like your documents and music collection, but it also contains hidden directories such as .mplayer and .xine which contain the settings for various pieces of software, which are relevant to individual users. That could cause a potential problem where both distros use the same software, but different versions of that software because it may well be that the configuration files are structured a bit differently for each version of that software. That could potentially cause that software to become confused and not work properly as a result.

The second important issue is that the /home directory also contains each user's desktop icons (in the directory called ~/Desktop). However, these icons are going to be different in one distro from the other because you're never going to have the exact same software installed in both (or all) distros. That then raises the danger that you could click on an icon for something in the other distro (perhaps forgetting that this is the case) and discover that you get an error message because the icon is linked to something which isn't in your current distro. Yet if you then delete that icon, you could then end up deleting something which is crucial to the other distro.

The way to deal with this is through the fact that you have folders called Documents, Pictures, Music, Videos and Podcasts in your home folder. The contents of each of these folders can be placed into a separate partition on the hard disk and that means that all you then need to do is to edit the /etc/fstab file in each distro to mount at startup, each appropriate partition into the appropriate subdirectory of the home folder, and then set the appropriate permissions for your data. That way, you won't need a separate home partition and the configuration files for all of the sofware in each distro can then be kept separate without getting mixed up with each other.

That would work well for me as I am the only regular user of my machine (I know that every UNIX system is technically, multi-user orientated, hence my use of *regular* user as I'm the only person who ever uses my machine). I'm aware that this probably wouldn't be a great solution in cases where more than one person is likely to use the machine but as that isn't the case with me, it is only a single-user solution which I have given here.

That is only an idea but personally, it's a route which I have decided in the end NOT to take. Neverthless, someone who is reading this might disagree with that and so, I welcome any views on this subject in case someone out there MIGHT be thinking about going down that route. What I therefore do is to just have one distro (which is Ubuntu) installed on my hard disc (WITH a separate home partition) as my main OS. However, I also have VirtualBox installed so that if I want to try out distros as an experiment, I can use VirtualBox for that to save me from continally having to reboot my machine between different distros. For that, I have also set up the appropriate data folders in /home as shared folders which can then be accessed in VirtualBox.

---

### Post by johncs2008 on 2008-07-20
I also forgot to add in my last paragraph that I AM aware that I could just use a live CD to experiment with most distros. VirtualBox is there in case I want to use the same distro over a period of time because in that situation, I don't want to be continually digging out the live CD for it.

---

