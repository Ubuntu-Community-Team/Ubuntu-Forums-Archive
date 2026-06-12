---
title: "Install Hangs After Desktop Background Displays"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by BlueMonkMN on 2008-05-11
I have an old Micron system that I haven't used in quite a while.  It had Windows on it when I got it (possibly 98, possibly XP; I can't remember any more), but a few years ago, I formatted the system and installed Debian on it, and it was running well (still does if I boot from the hard drive).  I haven't used it in the past couple years, though.  It's a Pentium II system with 128 MB of RAM.  I booted from the CD and things were going nicely on the initial boot screen.  They slowed down a bit on the screen with the progress bar.  But it finally got done with the progress bar and switched video modes and displayed the background image.  I was quite impressed with its ability to detect and use my video hardware since that's always been a pain.  However, after that, nothing happens for at least 3 hours.  The mouse pointer is an arrow, and I can move the mouse occasionally, but that's it.  The CD drive just sits running, flickering off occasionally, but apparently not helping much.

[LIST]
[*]I've tried both running without installing as well as installing.  When I tried running without installing I got some error about the Gnome Settings application being unable to start, which might result in the inability to support themes etc.  I didn't let this one sit for 3 hours, but it seemed like it wasn't going anywhere after that.
[*] I've tried the same CDRW on another system and it works fine on my Dell Dimension 8300.
[*] I've tested the install CD using the built-in test feature, and it says it's fine on the Dell.
[/LIST]

What are the requirements for Ubuntu (8.04)?  How do I see more of what's going on, and get more info about where it might be failing?

Ubuntu looks quite cool.  I was hoping it could help me bring an old system back to life and make it useful for something again (considering hooking it up to a new large screen TV for watching videos.  Pentium II systems did at one time play videos right? :popcorn:)

I looked briefly at the documentation, but didn't see anything helpful with these questions yet.  I'll continue to search for info on troubleshooting but hoped that someone might have time to reply while I search.

---

### Post by jackalparty on 2008-05-11
I attempted to do a 128 ram install of ubuntu on an old machine of mine and hit the same problem. I got it past the initial install but the system would crash as soon as the OS loaded. I believe that 128 will not suffice, I added some memory and now It runs (slow but surely). Take a peek at some distros like small linux, archlinux, there are loads of compact distros out there.

or hell go all out and make a txt console of ubuntu.

---

### Post by BlueMonkMN on 2008-05-11
I think I finally found the page with the minimum requirements for Ubuntu, and supposedly it should run on as little as 48 MB of RAM.

---

### Post by vorgusa on 2008-05-11
To install with less then 192 MB of RAM you need to use the alternate CD which is just a more simple and direct install with more options.  scroll to the bottom of this link and find the alternate CD that fits your computer

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by jackalparty on 2008-05-11
yes, use the alternate install cd, but you may have to go into grub and turn off some boot programs to get it to run with that amount of memory. Give it a shot and see if you can get it working and then come back here if you have the same problem that I had and I can help get you through grub.

---

### Post by BlueMonkMN on 2008-05-12
That worked great.  I'm writing this from the new Ubuntu installed environment.  My next potential problem is the list of 61 updates.  I told it to go ahead and install all of them, and the window has just been sitting there disabled for 15-20 minutes now.  I'll give it until morning... should I be seeing something?

---

### Post by BlueMonkMN on 2008-05-13
It seems that if I select a few updates at a time, things are sometimes OK.  But if I select all the updates or certain subsets of updates, the update manager just hangs with everything disabled, and never prompts for an administrative password or downloads anything.  It doesn't have purely to do with size, because I downloaded and installed a 7 MB update, but I can't download and install some smaller subsets.

Is there anything I can do to narrow down the problem?  Also, is there anything I can do to reduce memory usage... is there an easy way to switch to a lighter weight desktop environment besides Gnome, or a lighter weight graphical file browser than Nautilus?  There was mention above of turning some things off in grub... can you elaborate?

---

### Post by vorgusa on 2008-05-13
Hmm interesting problem.. not sure if it is related to the low memory on the machine.  I do see it on occassion when I install other OS's, and what I usually do to fix the problem is go to command line and update that way.  Just in case you do not know how:

sudo apt-get update
sudo apt-get upgrade

Do one then the other, and use your user account password.

---

### Post by BlueMonkMN on 2008-05-14
I also got this unresponsiveness problem when trying to download a codec to play MPG files.  The program that suggested getting a codec to play the file attempted to begin downloading, but never actually started the download, just like updater.  It looks like this system won't play videos at more than about 2 FPS (even using the proprietary NVIDIA driver), so I guess this isn't going to work out the way I hoped.  I'll need to use a newer system if I want to play videos.  Strange; I thought systems from the late 1990s could play video.

---

### Post by misterspider on 2008-05-14
I was having problems with 8.04 freezing completely, even on a brand new machine with 2gb ram.

Have a look here from about half way down...

[http://forums.whirlpool.net.au/forum-replies.cfm?t=968521&p=2](http://forums.whirlpool.net.au/forum-replies.cfm?t=968521&p=2)


They suggest turning off desktop effects.

---

