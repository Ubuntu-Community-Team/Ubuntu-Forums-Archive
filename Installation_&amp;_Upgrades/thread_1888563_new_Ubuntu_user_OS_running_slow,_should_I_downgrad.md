---
title: "new Ubuntu user: OS running slow, should I downgrade?"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by NikkiRuiz on 2011-11-29
Hello, this is my first post to Ubuntu Forums.  I just installed Ubuntu 11.10 to an old Acer Aspire 1690 laptop originally designed for MS Windows XP.  Ubuntu works, but is running super slow, with delays of 3-10 seconds for opening programs, and frequent crashes, up to every couple minutes.  Just to get this posted, it crashed three times, and this is the fourth time I've tried to write this.  Is the latest Ubuntu version too intensive for my old laptop and I should downgrade to an older version??  If not, what else might be wrong?  If so, how do I downgrade and what version would be optimal for this computer (or at least the newest version that wouldn't have issues)?  The computer has an Intel Pentium M 715 processor with 1.5 GHz, 400 MHz FSB, & 2 MB L2 cache, 75.5/80 GB HDD, and 512 MB DDR.  I only have a loose familiarity with Ubuntu or Linux, so am very much a novice at this unfortunately.

---

### Post by raja.genupula on 2011-11-29
Hi your Laptop configuration is not good for Running Ubuntu 11.10 .  there is(are)  solution(s) for you 

1.Xubuntu (512MB RAM)
2.Lubuntu (256MB RAM)

They are light weighted Ubuntu Operating system specially designed for Old systems and Laptops with Low configuration.

---

### Post by crazy bird on 2011-11-29
Agree with raja. Use a lightweight operating system. However, keep in mind that running a lightweight operating system does not mean that you still can install heavy programs since this will slow down your system as well. You only have 512mb RAM, Lubuntu/Xubuntu will take some of that for its resources. The little RAM left should not be taken away by a heavy program which consumes a lot of RAM. Best is to keep your installation as basic as it is. Just use the tools/programs provided after the installation is completed.

---

### Post by NikkiRuiz on 2011-11-30
Thank you for telling me about Xubuntu and Lubuntu.  I was able to get a Xubuntu install disc from my university computer help desk but it was only a marginal improvement, with crashes every 10 minutes or so, as opposed to every couple minutes on Ubuntu.  I was able to stay logged in long enough to download and burn Lubuntu thankfully, and am on that now.  However, I am still experiencing a very wide array of difficulties, including the computer freezing up very often and needing to be manually rebooted.  Start-up sequence varies wildly too, from normal startup and log-in to just a blank black screen or various terminal views with odd error messages.  I did a disk check and the disk is in good condition.  I noticed that the files installed on the computer are about 4 GB (as it should be) but the actual memory usage is almost 20 GB (as if Ubuntu and Xubuntu were still on there somewhere).  Each install I told the installer to departition and erase the previous OS; what is the extra HDD memory usage and might that be causing the current problems?  I thought it might be a need to defragment the old data, but I googled that, and it seems Linux doesn't need to be defragged?  The Lubuntu task manager says that the RAM and CPU usage is fine, so the problem isn't there.

---

### Post by NikkiRuiz on 2011-11-30
I also noticed that the requirements for Ubuntu Server seem to be significantly less than Ubuntu: 300 MHz CPU, 128 MB RAM, & 1 GB HDD (Ubuntu Server) vs. 1 GHz CPU, 1 GB RAM, & 15 GB HDD (Ubuntu Desktop).  With my laptop having 1.5 GHz CPU, 512 MB RAM, & 80 GB HDD, might Ubuntu Server be a better option than those I've tried already (Ubuntu, Xubuntu, Lubuntu)?

---

### Post by al108 on 2011-11-30
Sorry to hear that you still have problems. It does sound like there are other issues going on there then just 512 RAM. A couple of things to consider - 1) There's driver(s) conflict(s) with default installations of the OS. It could be anything from network card driver to video driver. 2) Hardware problems in the computer itself. Those may not be always apparent even if Windows still "works fine". I would start by checking all the connections are secure. Remove extra addon cards if present. Check Hard Disk for errors (including smart if available) 3) Installation media/CD drive errors. I had this happen before when everything seemed fine but I was getting strange problems untill I checked CD for errors...

Try something like ```
dmesg
```
and see if you can find some messages that suggest what the problems are.

Server installs don't have GUI by default. Though you may not need it for what you want to use the computer..

Good Luck
Alex

---

### Post by NikkiRuiz on 2011-11-30
I ran the Lubuntu Disk Utility disk checks, and everything came out good, including SMART.  I also ran the disc check for the installation disc before installing, and that came out good too.  Regarding anything with the internal hardware, I'm at a loss for that, getting the software working seems to be tough enough.  There does seem to be something screwy though with Lubuntu, perhaps there is an incompatibility with that version of Linux and this particular system.  The Chromium browser keeps failing to load a lot of pages (including on here; the "aw snap!" error is funny the first couple times, but after that is just downright aggravating :-P), the Xfburn disc burner keeps failing in mid-burn (ruining a bunch of my CDs), AbiWord has errors with saving documents, and the whole OS continues freezing up over and over.  Thanks for the heads-up though on Ubuntu Server, I definitely don't have the technical know-how to use Linux without the GUI, but my options look slim.  I was able to burn that disc successfully though, so I can try it out as a live CD first.

---

### Post by NikkiRuiz on 2011-11-30
Just tried the Ubuntu Server disc, and it apparently doesn't have a live run option.  I'll leave that as a last resort I suppose, but Lubuntu isn't running that much better than Xubuntu or Ubuntu did; do I have any other alternatives?  With Ubuntu Server, how exactly does it work without any GUI?  Is it similar to DOS in that I can still open programs that display normally?  I would definitely need a web browser to search for help and text commands to use....

---

### Post by al108 on 2011-12-01
Nikki, I don't think at this point there's a fast way to fix it. If you want we can continue digging. I'm not a big expert on this but I can show you what to check and maybe we'll find an easy solution. You will have to use terminal and run some commands and report the output here or make sense of them on your own. Looking at your first post you did mention some error messages. They possibly point to a reason while you having the problems. Look at system logs or at least run dmesg and tell us what it says or at least take time to figure out what those messages are about. Your system being a laptop doesn't make it easy to swap the incompatible hardware but there are still possibilities to find a good solution for you.

---

### Post by lykwydchykyn on 2011-12-01
Have you tested the Memory?  A bad RAM chip can cause all kinds of random chaos.

The disc has a memtest boot option, if your computer doesn't have built-in memory diagnostics.  Run it for an hour or two and see if any memory errors show up.

---

### Post by al108 on 2011-12-01
> **lykwydchykyn said:**
> Have you tested the Memory?  A bad RAM chip can cause all kinds of random chaos.

The disc has a memtest boot option, if your computer doesn't have built-in memory diagnostics.  Run it for an hour or two and see if any memory errors show up.

Yep, this is another easy test to do, and RAM is usually not hard to replace even in a laptop.

---

### Post by al108 on 2011-12-01
> **NikkiRuiz said:**
> Just tried the Ubuntu Server disc, and it apparently doesn't have a live run option.  I'll leave that as a last resort I suppose, but Lubuntu isn't running that much better than Xubuntu or Ubuntu did; do I have any other alternatives?  With Ubuntu Server, how exactly does it work without any GUI?  Is it similar to DOS in that I can still open programs that display normally?  I would definitely need a web browser to search for help and text commands to use....

Yes, default server install is just that - command line interface - black box, no graphical anything. Your might be surprised to find out that you can browse the web with text only browsers but it's not so easy if you're not used to it:) Obviously not all web pages will work in a text only mode

I don't see a point for you trying it if you want to be in the desktop environment. To diagnose problems though I'm sure both Xubuntu and Lubuntu have a rescue mode with command line only, without loading any of the graphics. It will have limited functionality for you, but it may give you a clue on the problems that you're having. See if your system is stable in rescue mode (should be able to select it during boot). You can also run different test programs from it that will help you identify faulty memory or other hardware. mprime for example.

---

