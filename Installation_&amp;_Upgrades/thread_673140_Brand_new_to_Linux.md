---
title: "Brand new to Linux"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by LinuxNewbie62 on 2008-01-20
I hope I'm not posting something that someone else has.  I am new to Linux but after speaking with a co-worker, I have decided to give it a try.  I have looked around Ubuntu, Mint and Mepis using a live CD and like the looks of them.  I also like the fact that no anti-virus is required.  My issue is this...I have all 3 of the CDs that I mentioned and I have an older Toshiba laptop that I would like to do a clean install on meaning, I want to get rid of XP and install without partitioning.  Question #1: Which CD would be best or how do I decide which is best?  Question #2: How do I install it so that Windows is no longer there?
I hope someone can help me out with these questions.  Please consider when explaining that I understand as much about Linux as a 1st grader.  I am not familiar with alot of the terms and lingo related to Linux.  I can tell you this much about the laptop;  Toshiba Tecra 8100, 128 Mb RAM, 11 GB hard drive.  I could not run the live CD on this laptop because there is not enough RAM but I did run all 3 on my desktop PC.  Can I even run one of these CDs with such little RAM?

Donna  :confused:

---

### Post by lluisanunez on 2008-01-20
OK, that's easy. To choose you should play with the live CDs, and see wich distro works better with your hardware. I'd recommend Ubuntu :-)

To install without keeping windows, take the first option: automatic partition, when it will ask you during install.

Wellcome!

---

### Post by Pandemic187 on 2008-01-20
> **lluisanunez said:**
> OK, that's easy. To choose you should play with the live CDs, and see wich distro works better with your hardware. I'd recommend Ubuntu :-)

To install without keeping windows, take the first option: automatic partition, when it will ask you during install.

Wellcome!
Uhh I dunno...I wouldn't recommend Ubuntu with such limited system resources. I would think Xubuntu, or something else geared toward older systems would be more appropriate.

By the way, "distro" is short for distribution. A distribution is a version of Linux, with Ubuntu, Mint, and Mepis being different distributions.

---

### Post by Pumalite on 2008-01-20
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your hard drive. Make a new large partition of your whole hard drive. Format ext3 if you want. Then try to install this:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by lluisanunez on 2008-01-20
Ooops, sorry. I read too fast.
128 Mb is really low. There are Mint versions with XFCE and Fluxbox, that should require less. You should read system requirements for both distros

---

### Post by LinuxNewbie62 on 2008-01-20
So you think that the Mint would be better for my particular system?  The CD I have is a burned copy so I am not sure which version of Mint I have.  What do you recommend now?

Donna

---

### Post by Pandemic187 on 2008-01-20
> **lluisanunez said:**
> Ooops, sorry. I read too fast.
128 Mb is really low. There are Mint versions with XFCE and Fluxbox, that should require less. You should read system requirements for both distros
True, but Mint XFCE and Fluxbox are still in beta. Xubuntu 7.10 is not.

---

### Post by Pandemic187 on 2008-01-20
> **LinuxNewbie62 said:**
> So you think that the Mint would be better for my particular system?  The CD I have is a burned copy so I am not sure which version of Mint I have.  What do you recommend now?

Donna
I wouldn't recommend those versions of Mint because they're still in beta. I'm still saying Xubuntu but I'm not sure what else is good for systems with minimal resources.

---

### Post by LinuxNewbie62 on 2008-01-20
I just read that Xubuntu requires 64MB RAM to run but would do better with 128.  They are not offering CDs for free so would i have to download it and burn it for use on my laptop?  If so, would I just need to burn the EXE file (?)?

Donna

---

### Post by Pandemic187 on 2008-01-20
> **LinuxNewbie62 said:**
> I just read that Xubuntu requires 64MB RAM to run but would do better with 128.  They are not offering CDs for free so would i have to download it and burn it for use on my laptop?  If so, would I just need to burn the EXE file (?)?

Donna
Yes, you'd just need to download it. And for future reference, there are no EXE files in Linux. ISO files are what you'd be burning to a CD anyway.

By the way, I like Xubuntu's default theme more than Ubuntu's. Maybe that's just me, but I just find it much more aesthetically pleasing.

---

### Post by LinuxNewbie62 on 2008-01-20
> **Pandemic187 said:**
> Yes, you'd just need to download it. And for future reference, there are no EXE files in Linux. ISO files are what you'd be burning to a CD anyway.

By the way, I like Xubuntu's default theme more than Ubuntu's. Maybe that's just me, but I just find it much more asthetically pleasing.
How many ISO files would there be?

---

### Post by Pumalite on 2008-01-20
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by motang on 2008-01-20
I agree with lluisanunez, play around with all three distros first.  At least for couple of hours, and do everything that you can imagine doing with your laptop.  See which one **you** like using, and which makes sense to **you** and which one is easy to use (I personally like *Ubuntu* and have been since it came out).  

When you are ready and double click on the "Install" icon and you are going through the process of installing the OS just choose the default option to install on the primary partition and the rest of the installation will take is course since you are not worried about the XP partition.  

Hope this helps you out, and let us know how it all went, maybe you can post the reply on your laptop running Ubuntu or which ever one you choose. ;-)

---

### Post by anemptygun on 2008-01-20
> **lluisanunez said:**
> Ooops, sorry. I read too fast.
128 Mb is really low. There are Mint versions with XFCE and Fluxbox, that should require less. You should read system requirements for both distros

I agree with lluisanunez try out XFCE or fluxbox they wll run more efficiently for you! :)

---

### Post by Pumalite on 2008-01-20
I think you should try what I suggested in my first post first. It would be the most satisfying. Next would be the others, including Puppy and DSL

---

### Post by lluisanunez on 2008-01-20
You just need one ISO image, the Xubuntu one:
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
XFCE is cute, you'll like it. On my laptop it needs 112 Mb of RAM, but I'm using normal Ubuntu, it loads part of Gnome as well so with Xubuntu I think it would require less memory.

---

### Post by LinuxNewbie62 on 2008-01-20
I have instructions on burning the Xubuntu but what is XFCE? :confused:

---

### Post by lluisanunez on 2008-01-20
XFCE is the window manager (or graphic desktop) that comes with Xubuntu

Ubuntu = Ubuntu + Gnome
Xubuntu = Ubuntu + XFCE
Kubuntu = Ubuntu + KDE

---

### Post by LinuxNewbie62 on 2008-01-20
I see.  I am off to get me some blank CDs for burning.  I'm sure I'll be posting again within the hour.  I really appreciate all your help.  Once I get it up and running, I will need more help I'm sure and I know I can count on you guys here.  Thanks very much!

Donna

---

### Post by lluisanunez on 2008-01-20
Donna, before you download read the page I sent:

```
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or  192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to have at least 128 MB RAM.
```

So, you should download the **alternate CD**

---

### Post by Pumalite on 2008-01-20
You cannot boot a Live CD with your RAM, unless you make a 500 MB /swap partition ahead of time. I advise you to install with the Xubuntu Feisty Alternate CD.

---

### Post by LinuxNewbie62 on 2008-01-20
I read the info that you sent which is why I chose the Xubuntu.  I just got finished burning it onto a disc and now I am going to see if it runs as a live CD.  I'll let you know how that goes.

Donna

---

### Post by LinuxNewbie62 on 2008-01-20
You were right Puma, I didn't have enough RAM to run the live disc.  I am downloading the alternate now and will burn that to see if that one works.  How are the two difference once they are installed?  I doubt I will be doing much configuring so would the alternate be ok for me?

Donna

---

### Post by Pumalite on 2008-01-20
You end up with the same system. Actually, installing with the Alternate CD is easier, you have more control.

---

### Post by rosegarden78 on 2008-01-20
I would get a Xubuntu disc then install and run Nautilus on Startup if you can.
Xubuntu: 55MB
Ubuntu: 450MB
Kubuntu: 550MB

---

### Post by LinuxNewbie62 on 2008-01-20
What is Nautilus?

---

### Post by lluisanunez on 2008-01-20
Nautilus is the File manager for Gnome. It doesn't come with Xubuntu, but there will be time for that after the install. Besides, there are other file managers perhaps lighter than Nautilus, like Rox or Thunar.

---

### Post by Pumalite on 2008-01-20
That's right.

---

### Post by LinuxNewbie62 on 2008-01-20
Ok, I put the disc in and the only option that I knew what it meant said Install in Text mode so it's installing now.  I chose to use the entire disc since I didn't want it partitioned anyway.  Is there any turning back now?  What if I don't like it?

Donna

---

### Post by lluisanunez on 2008-01-20
:mrgreen:

That's easy: download a different distro and install it on top

---

### Post by Pumalite on 2008-01-20
The disk will get partitioned in '/' and '/swap' anyway.

---

### Post by An_Dynas on 2008-01-20
also consider Fluxbuntu which, on a machine with similar specs, runs really quick.  Ultimately, though, I installed Xubuntu 7.10.
I highly recommend both distros.  With Fluxbuntu, you'll spend a bit more time in the terminal setting it up.

---

### Post by LinuxNewbie62 on 2008-01-20
How about Fluxbox?  Should I try it?

Donna

---

### Post by Pumalite on 2008-01-20
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

---

### Post by LinuxNewbie62 on 2008-01-20
I burned the .gz file onto a disc and tried installing it, but it failed.  WHY is this so hard????

Donna

---

### Post by Pumalite on 2008-01-20
A gz file has to be decompressed first. Every new OS has a learning curve.
Besides Fluxbox is a virtual Window Manager.

---

### Post by LinuxNewbie62 on 2008-01-20
Flux box is not another distro?  I wasted a disc on a windows manager?  UGH!
My co-worker is burning me a copy of Xubuntu and I'll get it tomorrow at work.  Hopefully his will install correctly since mine didn't.  I read him what the error said and he knew what was wrong.  He said that the disc did not burn correctly.  Ok, hopefully I get this thing up and running by this time tomorrow evening.  Wish me luck.  I'll be back tomorrow.

Donna

---

### Post by xeth_delta on 2008-01-20
> **LinuxNewbie62 said:**
> I burned the .gz file onto a disc and tried installing it, but it failed.  WHY is this so hard????

Donna

I just started following this thread and there is something I don't understand. What .gz file did you download? If you want to burn an installation CD, you will need an .iso file. You have to burn the image, not only take the file and copy it to the CD. Follow the link Pumalite gave you about writing an installation CD.

Good luck!

---

### Post by LinuxNewbie62 on 2008-01-20
Well, I need to know where the download .iso file is for fluxbox?  All I see are .gz files.

Donna

---

### Post by Pumalite on 2008-01-20
> **LinuxNewbie62 said:**
> Flux box is not another distro?  I wasted a disc on a windows manager?  UGH!
My co-worker is burning me a copy of Xubuntu and I'll get it tomorrow at work.  Hopefully his will install correctly since mine didn't.  I read him what the error said and he knew what was wrong.  He said that the disc did not burn correctly.  Ok, hopefully I get this thing up and running by this time tomorrow evening.  Wish me luck.  I'll be back tomorrow.

Donna
Good luck!!

---

### Post by LinuxNewbie62 on 2008-01-20
Ok, now I'm installing Mepis.  We'll see how this goes.

Donna

---

### Post by Pumalite on 2008-01-20
Mepis requires more RAM than what you have.

---

### Post by LinuxNewbie62 on 2008-01-20
UGH!!!!  But it's fluxbox, right?

---

### Post by Pumalite on 2008-01-20
[http://www.mepis.org/](http://www.mepis.org/)

---

### Post by xeth_delta on 2008-01-21
> **LinuxNewbie62 said:**
> UGH!!!!  But it's fluxbox, right?

In fact not. It is **Fluxbuntu**. You can get it from: [http://releases.fluxbuntu.org/7.10/rc/]("http://releases.fluxbuntu.org/7.10/rc/").
I think you had the link to just the window manager, fluxbox.

Download the i386 version from the bottom of the page.

Good luck!

---

### Post by LinuxNewbie62 on 2008-01-21
Puma, the Mepis version I have is a lighter version and it did install but there is a problem with the password now so my friend says I need to reinstall it and write down the passwords that I choose (I always use the same one so I don't know how I went wrong there).  I may also try the Alternate version of Xubuntu that my co-worker is bringing me today.  I'll know tonight how that works out.
Thanks to everyone for all their help.  I really do appreciate it.  Like I said, I will need more in the future.

Donna

---

### Post by Pumalite on 2008-01-21
When you reinstall, write down everything you do. That usually helps a lot, especially if one installs a new system every other day.

---

### Post by chrinabuntu on 2008-01-25
Since everyone has been talking about Mepis, which I hadn't heard of before, I decided to look into it, and then was convince to download the iso and try it out.

My question is, is it supposed to detect and connect to your internet card if you're just running the live cd, or do you have to actually install it?  I have used all the *buntus so far (except k), and all of them have connected immediately without any configuring to my internet card.  (NOTE: none of them have recognized or connected to any of my usb internet adapters...but they have all connected to my pcmcia wireless cards).  I was running MEPIS off the live cd just to see how it is, and it said there was no card detected.  I want to know if this is the usual reaction on the live cd before I install it, as I have Linux Mint now and it lives happily with my card already. The others I've used I didn't do the live cd investigation before installing, so I don't know if this is typical.

---

### Post by Pumalite on 2008-01-25
Wireless cards you have to configure after you install. During installation is best to be wired to the Internet, preferably through DHCP.

---

### Post by lluisanunez on 2008-01-25
That's right, but if the live CD detects your wireless it means it will be detected or easy to install afterwards, mind that no all the wireless adaptors are supported in linux, and some are difficult to install.

Hey, glad to see you going on :-)

---

### Post by Pumalite on 2008-01-25
Mepis is OK., but is not Ubuntu, BTW.

---

### Post by chrinabuntu on 2008-01-25
*"mind that no all the wireless adaptors are supported in linux, and some are difficult to install"*

Exactly...but since mine have been detected and connected right away in all my other Linux distros...I don't want to go to one where it will not.  I guess there's only one way to find out!  

Proud to be another Linux female by the way!  The few, the proud!  ;o)

Puma, you don't like Mepis too much?

---

### Post by Pumalite on 2008-01-25
I have it and is fine. It's just that I find myself using Ubuntu all the time.

---

### Post by rosegarden78 on 2008-01-26
> **LinuxNewbie62 said:**
> What is Nautilus?

Actually I'm using Ubuntu GG 7.10 [fresh]("http://ubuntuforums.org/showthread.php?t=677959") install with all compiz files installed, plus the [Avant]("http://ubuntuforums.org/showthread.php?t=385981") WM, on top of an Xfce desktop here.  Nautilus just runs a file manager and/or gnome mount to your desktop.

---

### Post by anemptygun on 2008-01-29
> **LinuxNewbie62 said:**
>  I'll know tonight how that works out.

So how'd that work out?

---

