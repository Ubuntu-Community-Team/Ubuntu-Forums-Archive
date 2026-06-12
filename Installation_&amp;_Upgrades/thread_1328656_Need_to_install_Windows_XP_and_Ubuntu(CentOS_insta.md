---
title: "Need to install Windows XP and Ubuntu(CentOS installed)"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by affableindia on 2009-11-16
Hello,

I'm Sridhar from India. I never got a chance to work on linux, but working on Microsoft Windows platform for past 11 years. I’m facing malware problem on my websites, so my friends suggested going for linux.

So, I got a CentOS from my friend installed in my laptop. But now I come to know that ubuntu is one of the best comparing to any other linux. 

My problem
----------
1. I have completely uninstalled Windows XP. And installed CentOS (want to remove CentOS).

2. Need to install Windows XP and Ubuntu (1st Widnows XP, 2nd Ubuntu as dual boot).

Can you guide me, I’m trying to install ubuntu for past 3 weeks please help me out. My friends don't have any idea.

---

### Post by audiomick on 2009-11-16
First of all: I am not a computer professional, but rather someone who has had to figure it all out for himself, so what I tell you may not be the best way.

Be that as it may, it should work like this:
The first thing is to set up fresh partitions on your hard disc.
To do this, you úse the partition editor that is included on the Ubuntu live CD, or another one that you are familiar with, or go and get a gparted live CD.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Whichever way you choose; you can't change a partition that is in use, so you need a tool that is on a bootable CD.

On the Ubuntu live CD:
You probably already know this, but:  start the computer with the CD in the drive and choose the option to try Ubuntu without changing the computer.

This is not a bad idea anyway, as it will give you a good idea of how well your laptop will work with Ubuntu

Go into the system administration menu and start the partition editor. This is gparted. With this, you can set up your partitions, same as with the gparted live CD. However, I've read lots of posts from people who say they prefer the gparted live CD to doing it from the Ubuntu live CD. I can't offer an opinion about this, as I don't have enough experience.

You need to decide how much room you want to give to windows, and how much to Ubuntu.

It is not a bad idea to create a second windows, i.e. ntfs, partition as a data swap partition. Linux can read windows file systems, but windows refuses to be able to read Linux file systems. If you need to be swapping files from one to the other, it is good to have a partition that both can read. Also, having a data partition allows you to download stuff in Linux to the partition that windows can read, and run a virus scanner across it before you open it in windows.

For Ubuntu, it is a good idea to have a partition for the operating system that will be mounted at / and a partition for your home folder that will be mounted at /home.
If you  don't understand this, maybe do a bit of research about linux as such, or just run the installer. It becomes a bit self evident when you get to the relevant stage of the installation.
The reason for having a separate /home partition is that that is where all your personal files and config files are stored. In a few months, after you have become an Ubuntu expert ( ;) ), it enables you to retain an existing /home folder in a new installation.

You can also just make the windows partitions for starters, and do the rest during the Ubuntu installation.

As far as size goes, allow about 8 to 10 GB for / where the Ubuntu operating system lives. You also should allow a swap partition for Ubuntu that is a bit bigger than your RAM. If the swap partition is smaller than your RAM, the suspend and hibernate functions can't work.

Install XP. I can't say much about this, as I haven't done a windows install for about 6 years.

It is necessary to install windows first, because if you don't, windows messes up your boot loader. Linux/Ubuntu, on the other hand, allows for the possibility that you might have more than one OS on the computer, and does its' best to make this work.

Once xp is happy, run the Ubuntu installer. It will find the windows installation, and offer you the option of installing next to windows.

When you get to the stage of the installation where the partitioning tool starts, choose the manual option. If you have already set up your partitions, you just have to specify the mount point here; otherwise you need to make the partitions for the Ubuntu installation. To reiterate:
/ about 8 to 10 GB
swap a bit bigger than your RAM
the rest for /home

That is really about all there is to it, assuming everything works right.

You might like to read this thread:
[http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649)
which deals with the same subject, and this

[https://help.ubuntu.com/9.10/switching/index.html](https://help.ubuntu.com/9.10/switching/index.html)
[https://help.ubuntu.com/9.10/switching/index.html](https://help.ubuntu.com/9.10/switching/index.html)

One last thing: I've read a few posts from people who have had trouble with the Live CD for Ubuntu 9.10 not finding their hard discs when installing. The advice in this case is to use the alternative CD instead, which has a different partitioning tool on it, and works better in some cases.

Don't be worried about all of this. It is not as hard as it may sound. A lot of it suddenly makes sense when you actually do it.
Given that you are doing a fresh install for both windows and ubuntu, it is also not a problem if it all goes bad and you have to start again. All it costs you is your own time, and you gain experience.
good luck, and have fun.
Michael

---

