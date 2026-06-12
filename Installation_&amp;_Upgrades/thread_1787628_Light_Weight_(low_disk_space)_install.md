---
title: "Light Weight (low disk space) install?"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by memyselfi on 2011-06-21
So I wanted to install Ubuntu 11.04 on my ASUS 900a that only has 4GB of disk space.  Of course Ubuntu 11.04 requires 4.4GB, so I started looking for alternatives.

I tried to get Lubuntu 11.04, but when I ran the installation process it states that 5GB are required.  Not very light weight IMHO if this is the case.

I was hoping that someone had an idea of how to install a strippted version of Ubuntu 11.04 (maybe without some of the apps like the LibreOffice Suite) or knew why Lubuntu was asking for so much hard drive space.

I'm hoping to move away from my light-weight version of WinXP.  Any suggestions?

---

### Post by mörgæs on 2011-06-21
Hi, welcome to the fora

This should help you:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by snowpine on 2011-06-21
Welcome to the forums!

I have a hard time believing Lubuntu needs 5gb; make sure the installer isn't trying to create a "swap" partition (which is waste of space if you only have 4gb).

The most drastic method is a "minimal" install. Here's a good tutorial: 

[www.psychocats.net/ubuntu/minimal](www.psychocats.net/ubuntu/minimal)

If you are open to options outside the Ubuntu family, you might check out Puppy, SliTaz, or TinyCore. Any of those will use well under 1gb, but the tradeoff is less "stuff" included out-of-the-box.

---

### Post by JC Cheloven on 2011-06-21
The mentioned method of minimal install should work, provided you have an internet conection. I did it many times (I'm forced to, because I like to use it in 64-bit). I do that in this way:

1.- From an alternate cd install (not a live cd), choose "install a text based system" (or some similar wording). This installs a command line system. Any ubuntu flavour (K-X-Ubuntu) will do, as the base system is exactly the same.

2.- Boot into the installed system wired to the internet, and run
```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

3.- 
```
sudo apt-get install lubuntu-desktop
```

Reboot when finished. You should be running lubuntu.

---

### Post by whatthefunk on 2011-06-21
> **memyselfi said:**
> So I wanted to install Ubuntu 11.04 on my ASUS 900a that only has 4GB of disk space.  Of course Ubuntu 11.04 requires 4.4GB, so I started looking for alternatives.

I tried to get Lubuntu 11.04, but when I ran the installation process it states that 5GB are required.  Not very light weight IMHO if this is the case.

I dont know, requiring 5GB of disk space is pretty light weight.  Most computers made over the last ten years have at last 20GB.

Try installing Lubunut 10.10.  The article below says it needs 3.2GB of disk space.  I run Lubunutu 10.10 and love it.  You may need to do an alternate install because the normal install program is graphics heavy and wont run on low spec machines very well.
[http://www.linoob.com/2010/11/lubuntu-10-10/](http://www.linoob.com/2010/11/lubuntu-10-10/)

---

### Post by jerrrys on 2011-06-21
the xubuntu alternate install cd requires 2G of disk space.  couldn't find a reference for lubuntu, but guessing its about the same.

---

### Post by JC Cheloven on 2011-06-21
> **jerrrys said:**
> the xubuntu alternate install cd requires 2G of disk space.  couldn't find a reference for lubuntu, but guessing its about the same.

Some facts:

A command-line install is worth ~ 1Gb

My Lubuntu, with many apps installed (including libreoffice, firefox, chrome, traverso from source with lots of qt dependencies, and many utilities), is 4.25Gb

---

### Post by whatthefunk on 2011-06-21
> **JC Cheloven said:**
> My Lubuntu, with many apps installed (including libreoffice, firefox, chrome, traverso from source with lots of qt dependencies, and many utilities), is 4.25Gb

Mine is 4.7Gb.  I think the OP might be out of luck with Lubunutu...

---

### Post by mörgæs on 2011-06-21
I think you guys have installed a LOT of extras - or forgotten to run

```
sudo apt-get clean
sudo apt-get autoclean
```Are you counting /home in the 4-5 GB?

---

### Post by JC Cheloven on 2011-06-21
> **mörgæs said:**
> I think you guys have installed a LOT of extras - or forgotten to run

```
sudo apt-get clean
sudo apt-get autoclean
```Are you counting /home in the 4-5 GB?

Yes, as said in #7 I have quite some extras. On the other hand, my lubuntu partition is 40Gb, so I can afford to have the .deb packages at hand just in case. Just deleted them to test, and in fact the used space has reduced to 3.63 Gb. Surely I could reduce it even more by caring about the (2) browsers caches, old kernels, orphaned packages etc.
And yes, that includes /home (with ~450Mb of my files).

@whatthefunk:
So I think the OP could be within specs, as I guess a plain lubuntu system will be less than 2.8 Gb.

---

### Post by whatthefunk on 2011-06-22
> **JC Cheloven said:**
> Yes, as said in #7 I have quite some extras. On the other hand, my lubuntu partition is 40Gb, so I can afford to have the .deb packages at hand just in case. Just deleted them to test, and in fact the used space has reduced to 3.63 Gb. Surely I could reduce it even more by caring about the (2) browsers caches, old kernels, orphaned packages etc.
And yes, that includes /home (with ~450Mb of my files).

@whatthefunk:
So I think the OP could be within specs, as I guess a plain lubuntu system will be less than 2.8 Gb.

I roughly estimate that I could get it down to 3.5Gb if I took out the extras.  I suppose the OP could squeeze it in, but I dont know what good an OS with half a gig of free space is.

---

### Post by thecure on 2013-01-24
If you want to install Lubuntu 12.10 on a 4gig SD and not use alternate install disk then boot up Lubuntu on your usb stick. Open a terminal. 
Type "gksu leafpad /usr/lib/ubiquity/ubiquity/misc.py" (Without quotes.)

Click on options and select line number. Then about line # 853 will be something like "min_disk size = size x 2 #fuge factor" change 2 to 1.4 then save and run the install Lubuntu. It should now say minimum disk size 3 gig. Just be sure when you get to the disk partition/install part select other and set up the drive as one ext4 partition as /. No swap; a page will come up saying you didnt make a swap partition but just ignore. Have fun. 

You can also use this technique to install Ubuntu 12.10 but  use gedit instead of leafpad and that line # is different; I think 750 something. One caveat though with Ubuntu you are left with about 350meg of free space! 

I didn't come up with this but found on another web forum but can't remember where. But have used it on a couple of Dell mini 9's.

---

