---
title: "update on Lucid and Grub2?"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SeePU on 2010-02-05
I am sure there's a lot of posts on this but I am wanting this thread to be specific to the overall state of Lucid and Grub 2 and how it's progressing.

I was wondering how a Lucid install and Grub 2 is with older machines, I guess, like my notebook, a Thinkpad T41.

I tried a Live CD of Lucid Alpha 2(?) and to my amazement, I was able to enable 3D and desktop effects with my radeon card!   Nice.

I have tried installing Debian testing, LXDE, on my notebook but Grub 2 didn't detect my other operating systems, XP and Mepis.  So, I installed/used Grub Legacy for the boot loader.  I am wondering if Grub 2 works for you if you use that as your boot loader.   'Didn't for me and I was a bit surprised at it not working but I probably shouldn't be surprised.  Maybe?

Anyway, I'm interested in what bugs are showing up in Lucid so far.  

Thanks in advance for any info/insight on it.

---

### Post by VMC on 2010-02-05
> **SeePU said:**
> ...I tried a Live CD of Lucid Alpha 2(?) and to my amazement, I was able to enable 3D and desktop effects with my radeon card!   Nice.

I have tried installing Debian testing, LXDE, on my notebook but Grub 2 didn't detect my other operating systems, XP and Mepis.  So, ....
I'm surprised it didn't find your OS's. What's the output of:

```
sudo fdisk -l
sudo blkid
```

To give us an idea of what's on your computer.

---

### Post by SeePU on 2010-02-05
> **VMC said:**
> I'm surprised it didn't find your OS's. What's the output of:

```
sudo fdisk -l
sudo blkid
```

To give us an idea of what's on your computer.
I'm using Grub Legacy for the bootloader now.

Do you still want the info?

I feel that one of the problems with Ubuntu is their indifference to bug reporting.  I have not noticed any response to the fact you CANNOT get the reboot screen in Ubuntu 10.04 still.  

Really annoying.  With all the available screen real estate and there's only one GUI method to get log out/reboot/shutdown?!?   But, it doesn't even work properly?  I click the top right corner 'icon' but nothing happens, just a buggy shaded icon with a partial dropdown 'chunk.'  

You would think this would be acknowledged and fixed by now.  It's a pretty serious bug.

---

### Post by decoherence on 2010-02-05
so much for this thread being specific to lucid/grub2 :biggrin:

and yes, i imagine we would still like the output. part of fixing bugs and all.

---

### Post by SeePU on 2010-02-05
> **decoherence said:**
> so much for this thread being specific to lucid/grub2 :biggrin:

and yes, i imagine we would still like the output. part of fixing bugs and all.
I didn't install it, only tried on Live CD.

Too many serious bugs for an install but I guess a Grub 2 problem could be fixed (if it was installed).

Even when I hard reboot or 3 finger salute to it, it does not reboot properly.  I can take out the CD but the screen freezes with the 'Ubuntu' title in the center (w/ black screen).  I'm afraid what I'd get with an install.  

I know this is Alpha but how long will Ubuntu be in this state?

Also, the 3D is set via default on the middle option.  But, I don't notice any effects working.  I moved it to the 'full' or optimized setting (botton option) and I had 3D.  Is this normal?

Anyway, other than those bugs, I was able to connect with the wireless card.  I am sure software could be installed easily or I could find the documentation to do so.  

The bugs I report, though, must be well known by now.  It hampers normal day-to-day activity.

---

### Post by SeePU on 2010-02-05
Okay, this issue is already reported.  
> On video hardware that supports KMS, the live CD sometimes does not reboot successfully, instead displaying the boot logo indefinitely. To work around this, you will need to power down the system manually. Investigation of this issue is ongoing. As a workaround, users can boot from a USB stick instead of from a CD. (506418)

---

### Post by VMC on 2010-02-05
> **SeePU said:**
> ... I click the top right corner 'icon' but nothing happens, just a buggy shaded icon with a partial dropdown 'chunk.' ...
Are you sure its the shutdown icon your clicking and not your user icon. The one you want it the one on the far right:

---

### Post by SeePU on 2010-02-05
> **VMC said:**
> Are you sure its the shutdown icon your clicking and not your user icon. The one you want it the one on the far right:
Yes, that one.

I don't have a problem on each boot but the previous time I tried to shutdown, I had the problem as described.

I have another question, though.  When I enable desktop effects, I can only get one 'feature', the wobbly windows, but I have to choose 'Extra.'  When it's on 'Normal', nothing looks enabled.  On Ubuntu 9.04, I could get effects (transparency) with the middle option checked.  Any reason for this?

Also, I have to edit xorg.conf to get any type of 3D in 9.10, Karmic, and I found only one collection of settings to work (still not sure what should be there).  I believe that 10.04 is automatically configured so you don't need/have an xorg.conf.  Will I still need to create one?  It seems the X settings have only minimal settings/effects as default again.  

Anyway, to answer your question, yes, the far right top corner is where I had that 'bug.'  You have 'vmc' to the left of it and I have 'ubuntu' to the left (default).

---

### Post by scradock on 2010-02-05
To answer your original question, yes, I have Lucid with Grub2 working fine on an older machine, using an ATI Radeon Express 200M and the ati/radeon OS drivers. No need for xorg.conf.

The reason you have "ubuntu" as the user name is that the LiveCD doesn't set up your own user until you install. Take the plunge and install, and you will have your own account. I have been using this machine since ?gutsy?, and each time it updates to the new version, some things are different, but it all works. In my experience, Karmic was one of the least successful versions; Lucid is beating it hands-down so far.

I installed from a USB image of the LiveCD of Lucid alpha2, and had to enable compiz to get the full range of eye-candy, but that sort of personalisation is what makes linux fun, in my view. There are some things that are still works in progress - plymouth, for instance - but Grub2 is getting firmer with each update. My boot time has gone down from about a minute to under 40 sec in the last week or so, for instance.

Take courage, and install Lucid!

---

### Post by ranch hand on 2010-02-05
It is going to stay an alpha until March 18th.  Then it will be Beta1.

As for no movement on bugs, bunk.  We have had as many as 2 grub updates a day since this problem arose.  Another today and a kernel update.  Booting fine (alpha fine now).

If you are banging your head on the wall over the A2 install disk, it is very old. try a daily.  I suggest tomorrows which will have the updates from today.

---

### Post by jerrylamos on 2010-02-05
> **SeePU said:**
> 

I was wondering how a Lucid install and Grub 2 is with older machines, I guess, like my notebook, a Thinkpad T41.


Lucid, Grub2 & all runs fine on my Thinkpad T40 except for losing the cursor on my external monitor with the latest kernel, 2.6.32-12.  There's a bug written on that so there may be some action.....

There's a bit of a learning curve on Grub2.  I'm using it successfully multi boot on the T40 including Lucid, Karmic, SUSE, Fedora, DebianLXDE live, SliTaz live & SliTaz installed.  The live versions are a 1G partition which the linux thinks is a CD.

Jerry

---

### Post by ranch hand on 2010-02-05
> **jerrylamos said:**
> Lucid, Grub2 & all runs fine on my Thinkpad T40 except for losing the cursor on my external monitor with the latest kernel, 2.6.32-12.  There's a bug written on that so there may be some action.....

There's a bit of a learning curve on Grub2.  I'm using it successfully multi boot on the T40 including Lucid, Karmic, SUSE, Fedora, DebianLXDE live, SliTaz live & SliTaz installed.  The live versions are a 1G partition which the linux thinks is a CD.

Jerry
What have you had to do with your non debian based OS'?  If you nave made custom entries I would like you to post them on my grub intro thread so I could put them in my first post (see sig).

The only one I have is Mandriva.  Os-prober has got to the point where the generated entry is almost bootable and it doesn't pick up every driver as another kernel.

---

### Post by SeePU on 2010-02-06
> **jerrylamos said:**
> Lucid, Grub2 & all runs fine on my Thinkpad T40 except for losing the cursor on my external monitor with the latest kernel, 2.6.32-12.  There's a bug written on that so there may be some action.....

There's a bit of a learning curve on Grub2.  I'm using it successfully multi boot on the T40 including Lucid, Karmic, SUSE, Fedora, DebianLXDE live, SliTaz live & SliTaz installed.  The live versions are a 1G partition which the linux thinks is a CD.
Jerry
What size are your partitions?

Is 20-25GB enough for Lucid, Mandriva and Debian?  I wanted to try these on my Thinkpad's 160GB Samsung IDE drive.

Also, what graphics card is in your Thinkpad?

I think I'll install Lucid A2, a daily image like the other poster suggested.  Thanks for the answers and replies, guys!  It is greatly appreciated.  It's so timely, too, and I want to install today or tomorrow. ;)   The only concern I have still is that my question of the Desktop Effects settings didn't seem to get resolved.  I am still confused why 9.04/9.10 has 3D activated on the 'Normal' setting but Lucid doesn't seem to have anything enabled on the same setting as it required 'Extra' to be checked.  Not a huge deal but something seems to be different there.  

Imho, 9.04 is a decent release but the kernel/packages are getting a bit old although that's fine as it seems stable.  But, 9.10 has something going on with X/xorg/related 3D that needs xorg customization or it locks up when 3D is activated - at least, on my Thinkpad T41.  Lucid looks really promising except for a few apparent bugs as I described.  I'll try the daily image and see if anything has changed.  It was surprising whne my Debian testing install's grub 2 didn't detect the other operating systems!  I guess Grub 2 is an ongoing project but I'm thinking it is going to require a lot of work since it seems to work quite differently than Grub Legacy.

---

### Post by ranch hand on 2010-02-06
You want to install three more OS'?

I would not do it on less than 10Gb per OS and that is pretty crowded.  !5Gb per OS would be better.

On my test platform I usually give a 10Gb / and a 15Gb /home which is plenty and gives room for a lot of music files.

You may want to think about an external if you want to fool around with alpha releases and see if you can turn off the internal in bios to isolate it from any possible fallout.  I do not like the idea of risking my main production OS or the drive it is on at all.

---

### Post by the.scarecrow on 2010-02-06
@seePU
Have you thought about using a USB stick to do your Lucid testing? I use a 4GB USB that leaves 3.1GB for your updates and additional apps. it works very well and I think with very little risk to your installed Karmic.

After several updates it fails, I assume because the 3.1GB persistance file is full up. So I update my .iso from the daily updates, delete all the files on the USB and re-create it. I even create my Karmic user as user ID:1000 and then I can access all my Karmic files.

Loads of fun and it seems to be safe.

---

### Post by seeker5528 on 2010-02-06
> **ranch hand said:**
> On my test platform I usually give a 10Gb / and a 15Gb /home which is plenty and gives room for a lot of music files.

Your definition of 'a lot of music files' must be different than mine, 40 GB and growing. On the one hand 15 GB could hold a lot of music files, but on the other, what else do you plan on storing in that same 15 GB of space.

In a situation where you have a single installation of Linux I like the separate root and home partitioning approach.

With 2 it's still not too bad.

With 2 Linux + Windows or with 3 or more Linux installations I prefer a single partition for each distribution. Usually since I like to have KDE and Gnome, other window managers to use alone or in place of the default Gnome or KDE window manager and some games and other misc software I figure 10 to 15 GB, with the increasing size of some of the games I'm leaning more toward 15 GB these days and that's not figuring a lot of room for data because I have a partition dedicated exclusively to music, another for MythTV recordings, another for the bulk of my stuff documents, downloads, etc... that I don't care about having access to in Windows, another partition in NTFS format for wallpaper, backup of Firefox bookmarks ([Febe](https://addons.mozilla.org/en-US/firefox/addon/2109)), and other downloads and misc... stuff I want available while I'm booted into my Windows installation.

That's the theory anyway, in reality my scheme gets a little more complicated by the use of multiple drives and the limited window of opportunity when it is convenient to split/merge/resize partitions when replacing an older drive with a newer/larger drive.

Later, Seeker

---

### Post by phillw on 2010-02-06
> **ranch hand said:**
> 

On my test platform I usually give a 10Gb / and a 15Gb /home which is plenty and gives room for a lot of music files.


Yikes !!! Only 3.5GB here - that's a paltry 725 Songs (2 days and 4 hours of continuous music) - lol

Mind you, I think my brother has nearly filled his 64GB Memory Stick with music, but he is a serious collector of music !!!

Regards,

Phill.

---

### Post by SeePU on 2010-02-09
> **the.scarecrow said:**
> @seePU
Have you thought about using a USB stick to do your Lucid testing? I use a 4GB USB that leaves 3.1GB for your updates and additional apps. it works very well and I think with very little risk to your installed Karmic.

After several updates it fails, I assume because the 3.1GB persistance file is full up. So I update my .iso from the daily updates, delete all the files on the USB and re-create it. I even create my Karmic user as user ID:1000 and then I can access all my Karmic files.

Loads of fun and it seems to be safe.
What app to use to create the .iso?  I found UNetbootin to work horribly as it's not reliable and I don't trust the individual distro's application.  They all seem to have their own now and I not found one that works reliably.  I think they should all get together and help out the Unetbootin people so there's a universal app that actually works.

Booting up live via USB is a nice concept but none work properly or reliably.  I'm still using CDs since I know it will work but will be slow.

Both my computers' BIOS support usb but I can't utilize this feature since I don't trust the programs.  I have had some created but over 90% of the attempts have failed and not worked.  Not worth my time.  UNetbootin is a POS and the distro's respective utility also sucks.

I guess 20 to 25GB for the OS is sufficient.  But, then there is not much room for dedicating separate partitions to /home etc.

---

### Post by ranch hand on 2010-02-09
For my test platform with 10.04 I am using 10G for / and 15G for /home.  This really is plenty for testing.  I will admit that this OS, the one I use most of the day, is running 15G for / and 25 for /home.

I have added a bunch of "stuff" to it to try out so it is nice to have plenty of room to play with and both are right around 50% so you really can do with less.

---

### Post by SeePU on 2010-02-09
> **ranch hand said:**
> For my test platform with 10.04 I am using 10G for / and 15G for /home.  This really is plenty for testing.  I will admit that this OS, the one I use most of the day, is running 15G for / and 25 for /home.

I have added a bunch of "stuff" to it to try out so it is nice to have plenty of room to play with and both are right around 50% so you really can do with less.
What is your main OS?

This is a really silly/dumb question but how do you 'divide' this configuration?  I have never done it this way.  I always install them all on one partition.  Is there options during the install for each distro to allow for 'extra' partitions.  You know, to allow for a separate /home and /?  I just thought it would be a pain to keep track but maybe it is better?  I have run out of space usually and I often dedicate 20 to 25 GB per partition.  That's why I plan on having a drive I use as an external drive and just write data to there.  I am hoping that I can save/write data from any distro to there.  It would just be downloaded files, videos, music files, .pdfs, documents, etc. etc. so no matter which distro they are created in, I should be able to, right?  

I have mostly just filled whatever partition but this method just results in me running out of space so I need to find a different way.   Since, my laptop has an even smaller OS HDD, I need this different way, especially.

---

### Post by ranch hand on 2010-02-09
My official main OS is 8.04.  My main production OS is 9.04.

During the day my main production OS is 10.04 (an upgrade from a 9.04 respin to 9.10>10.04).

When I install I have usually done my partitioning with gparted (System>Administration>Gparted) on the LiveCD.  Then go to installation and when it gets to the partitioner select "manual" and then tellit what partitions to use for what.

You can use the installer partitioner to make the partitions too.  I just do it the other way.  There has been some problems with the installer partitioner on the 10.04 LiveCD in the past.  I do not know about now.

I know that I am going to have a number of installs so I actually generally set up several partitions in advance.  Most people are not that crazy so it is easy to set up the partitions with the installer partitioner.

---

### Post by Reiger on 2010-02-09
For me it's 4 partitions: 
```

/usr/local/
/home/
/
swap

```

This allows me to install things outside the repositories and my own little scripts to /usr/local; backup data from /home; and mess up / as much as I (do not) like.

---

### Post by VMC on 2010-02-09
> **SeePU said:**
> What app to use to create the .iso?  I found UNetbootin to work horribly as it's not reliable and I don't trust the individual distro's application.  They all seem to have their own now and I not found one that works reliably.  I think they should all get together and help out the Unetbootin people so there's a universal app that actually works.

Booting up live via USB is a nice concept but none work properly or reliably.  I'm still using CDs since I know it will work but will be slow.

Both my computers' BIOS support usb but I can't utilize this feature since I don't trust the programs.  I have had some created but over 90% of the attempts have failed and not worked.  Not worth my time.  UNetbootin is a POS and the distro's respective utility also sucks.

SeePU, You know what I found out. Windows does a better job at creating a UNetbootin LiveUSB than does Ubuntu?! 

What I'm thinking is that Ubuntu uses an older syslinux version than does windows. Both create ok, its just Windows version LiveUSB is much faster . Not sure why.

---

### Post by SeePU on 2010-02-13
> **VMC said:**
> SeePU, You know what I found out. Windows does a better job at creating a UNetbootin LiveUSB than does Ubuntu?! 

What I'm thinking is that Ubuntu uses an older syslinux version than does windows. Both create ok, its just Windows version LiveUSB is much faster . Not sure why.
:D      LOL!   UNetbootin = POS!  In Windows or Linux.  

I just tried to create a bootable Live Daily ISO with it and what a surprise, it won't boot up.

UNetbootin = POS!!!!

---

