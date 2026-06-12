---
title: "newbie installation slow as molasses"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by jallred on 2010-05-07
I've been using Windows XP on an [HP Compaq nc6400]("http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html") laptop for years and over time it has become unbearable to use, so I moved all my files to an external hard drive and installed Ubuntu 10.4. I did not leave WinXP on the drive, I had Ubuntu overwrite the entire drive.

This is my very first experience using Ubuntu (or any linux distro for matter, I've always used Windows and Macs previously). The installation was very easy and I had no problems whatsoever. All of my hardware was recognized (I was especially impressed with how easily my HP printer was setup).

The problem I've experienced though is one of speed. I feel like I am using the William Shatner OS where ... every ... action ... is ... followed ... by ... a ... noticeable ... pause. The only software I've installed is Chrome (Firefox was so slow as to be unuseable). I've gone to System > Preferences > Appearance > Visual Effects and set it to NONE. That actually helped a little, but not enough unfortunately.

As I said, this is my first experience with linux, so for all I know this is how Linux runs on everyone's machine and is expected behavior. But I doubt that is the case (if so I can't believe anyone would actually continue to use it). I assume this is simply a newbie issue that has a simple fix (there is a "run faster" button somewhere, right?)

If I can't this resolved soon I'm afraid I'm going to have to go back to Windows. Things were getting messed up under Windows XP, but at least it was fast enough to be useable. Sigh.

---

### Post by nicolastroche on 2010-05-07
What version you download? If you download Ubuntu Netbook it's probably it runs a little slow. Try to install ubuntu desktop or xubuntu.

---

### Post by powerofpi on 2010-05-07
Would you open the System Monitor and let us know which processes are gobbling up the most CPU power?

---

### Post by tommcd on 2010-05-07
> **jallred said:**
> 
The problem I've experienced though is one of speed. I feel like I am using the William Shatner OS where ... every ... action ... is ... followed ... by ... a ... noticeable ... pause. The only software I've installed is Chrome (Firefox was so slow as to be unuseable). I've gone to System > Preferences > Appearance > Visual Effects and set it to NONE. That actually helped a little, but not enough unfortunately.

Have you tried running Ubuntu for a while from the live CD? Does Ubuntu run very slow from the live CD? (Note that the live CD is expected to run a little slower than Ubuntu installed on the hard drive, since hard drive access is a lot faster than cdrom access).
If running from the live CD is faster than your installed version of Ubuntu, then this would point to a faulty install.
The specs of your laptop should work ok in Ubuntu / linux.
BTW, I like, the "William Shatner OS" reference!

And welcome to the Ubuntu forums!!

---

### Post by jallred on 2010-05-07
> **nicolastroche said:**
> What version you download? If you download Ubuntu Netbook it's probably it runs a little slow. Try to install ubuntu desktop or xubuntu.

 I installed ubuntu 10.4 desktop 32 bit

---

### Post by jallred on 2010-05-07
> **powerofpi said:**
> Would you open the System Monitor and let us know which processes are gobbling up the most CPU power?

 When I have only the system monitor open, it uses nearly 90% of the CPU. If I have nothing open and use TOP from the terminal window nothing is really taking up much CPU time. (I was surprised that the system monitor was using so much CPU so I did a google search and people recommended using top from the terminal window instead).

---

### Post by jallred on 2010-05-07
> **tommcd said:**
> Have you tried running Ubuntu for a while from the live CD? Does Ubuntu run very slow from the live CD? (Note that the live CD is expected to run a little slower than Ubuntu installed on the hard drive, since hard drive access is a lot faster than cdrom access).
If running from the live CD is faster than your installed version of Ubuntu, then this would point to a faulty install.
The specs of your laptop should work ok in Ubuntu / linux.
BTW, I like, the &quot;William Shatner OS&quot; reference!

And welcome to the Ubuntu forums!!

  I did run from the Live CD long enough to test out all of my hardware to make sure it would all work before committing to a full install. I probably used it for less than an hour, but it was definitely slow. But I expected that. I was actually amazed that it ran as well as it did. Who knew you could run a full OS from a CD?!

---

### Post by jallred on 2010-05-09
To be more specific, when running top in the terminal window and nothing else xorg uses 5% of the CPU, top and terminal use another 5%, and everything else is 0%.

If I run chrome and nothing else, Chrome has two processes running (I assume one for the browser and one for the tab I have opened up). One process uses about 98 - 117% of the CPU, the other uses about 35 - 54% of the CPU, xorg uses about 11% of the cpu, top and terminal use about 5% and everything else uses 0%.

---

### Post by NUboon2Age on 2010-05-09
How much memory does your machine have (and what processor does it use)?  If you have a low memory situation my experience might provide some light.  Also could you provide the full listing from TOP?

I've got a 5 yr old lap top I'm experimenting with that only has 238M memory.  Thing is it seemed pretty zippy on the Ubuntu Netbook Edition even though the system requirements state something like 512M.  I was running it off a CD and yeah the boot up was extremely slow off CD, but after I was logged in, pretty good really!  So unlike what the person above said it might perform BETTER w/ the Ubuntu Netbook Edition (UNE) than the desktop edition (which would kind of make sense).     

I've been running Xubuntu and I got it to a decent place with performance and then I added some more software and somewhere along the line I ended up in the morass of low memoryville.  I'm trying to figure out which straw it was that broke the camel's back.  My TOP/System Monitor readings look similar to yours -- nothings really sticking out.  When I run Swiftfox (the Linux-specific build of Firefox), that does take quite a bit of memory and CPU cycles, but I was running that previously with good performance, so I don't think its that by itself.  I loaded Clam antivirus (hoping to scan a Windoze partition) and that may have started some daemons that are causing the slow down.

It sounds like Lubuntu is better suited for low system resources than Xubuntu, because from what I've read Xubuntu has gotten away from focusing on low memory requirements (even though the description talks about that).  Of course there are many other Linux (and even Ubuntu derived) distros that focus on low system resources.    

Hope that helps.  Hope you can resolve it within the land of the truly free -- Linux and don't feel compelled to put the shackles of Mega$hackle back on.

---

### Post by hatebreed on 2010-05-09
Ubuntu needs more ram to run without a doubt. I had it running on a 400 celeron with 256 meg ram and it ran but it was laggy. As soon as you bump up the ram to 512 it it noticably faster. It also helps of course to run it on a faster cpu, as I have it on a dual 400 with 450 meg ram and it runs much better. I can still see some lag with many tabs open in opera. I have also noticed that, with browsers in general, that they take up quite abit of memory and cpu. I can't quite figure this out though, it doesn't make since cause a browser is typically not a power hungry app, especially opera.

---

### Post by tommcd on 2010-05-10
> **jallred said:**
> To be more specific, when running top in the terminal window and nothing else xorg uses 5% of the CPU, top and terminal use another 5%, and everything else is 0%.
This, by itself, does not seem to be unusual.
> **jallred said:**
> 
If I run chrome and nothing else, Chrome has two processes running (I assume one for the browser and one for the tab I have opened up). One process uses about 98 - 117% of the CPU, the other uses about 35 - 54% of the CPU, xorg uses about 11% of the cpu, top and terminal use about 5% and everything else uses 0%.
Do you have Flash installed?
The Flash player is known to be a big CPU hog on linux. From what I have read, Adobe does not provide enough resources for developing their binary-blob, closed-source flash player for linux as they do for Windows. The result is that flash on linux, (and in my experience, especially on Ubuntu) will use a LOT of your CPU. Obviously, this will be more of a problem on slower and older machines.
So ... try removing or disabling flash, and see if Google Chrome, Firefox, and everything else is more manageable on your system.
The specs in the link you gave in post #1 of this thread:
[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html)
would indicate that your system is fine for running Ubuntu. One gigabyte of memory should be good enough, and Ubuntu should not be using 90+% of your CPU.
Note that my laptop has an Intel Celeron 1.6GHz CPU. For quite a while I ran the system with 1GB memory and it ran just fine. I recently upgraded to 1.5 GB memory; but I was doing just fine with only 1GB.

---

### Post by jallred on 2010-05-26
Do you have Flash installed?
 Sorry I haven't replied earlier. For some reason I didn't receive an email indicating the thread had been updated.  In response to your question, no, I haven't installed flash yet.   I think the problem lies with the intel video driver, but I can't figure out what to do to fix it. My wife and kids are tired of the slow computer so I'm probably going to reinstall Windows XP during the long weekend coming up.  Thanks for the help to all those who responded, but, at least for me and my machine, it looks like Linux isn't quite there yet.

---

### Post by WinRiddance on 2010-05-26
> **jallred said:**
>   In response to your question, no, I haven't installed flash yet.   I think the problem lies with the intel video driver, but I can't figure out what to do to fix it. My wife and kids are tired of the slow computer so I'm probably going to reinstall Windows XP during the long weekend coming up.  Thanks for the help to all those who responded, but, at least for me and my machine, it looks like Linux isn't quite there yet.

Well, if you've got time over the Weekend for Windows then why not take some time out for Linux instead? Believe me, I've installed Ubuntu on about 15 machines so far, three of them pretty old, and Ubuntu always ran way better on those machines than with windows because Ubuntu does use considerable fewer resources. More than likely it's just one little issue that's holding up everything else.

Tell you what, since you already mentioned that it's an older machine and since the newest Ubuntu version is pretty loaded up with lots of toys and things, why not try to run the desktop version of an earlier Ubuntu instead, say perhaps the 32bit desktop version of Karmic Koala (Version 9.10) which was only replaced a month ago, or perhaps the next version dowm Ubuntu 9.04 Jaunty Jackalope?

**Some additional tips:** You really should have _a bare minimum_ of 512 MB Ram these days, more is better of course. But you should also, especially on an older machine with little memory, create yourself a **3 or 4 GB swap partition**. The swap partition works just like "fake memory" and really helps older machines with their performance. The partition for _Ubuntu 9.04 can make use of the ext3 file system_ **but** the partition for Ubuntu 9.10 and Ubuntu 10.04 should have the partition formatted to ext4 instead. I've used Windows professionally for 18+ years and ever since Ubuntu 9.04 there's been no looking back for me. The first month was a nightmare, all new terminology and such ... the second and third months were still a pain in the rear ... but ever since then it's been nothing but a pleasure to work with a system that's more stable, more secure, faster, safer, free of charge, and so on. Even my 75 year old mother made the switch, no kidding.

---

### Post by NUboon2Age on 2010-05-27
> **WinRiddance said:**
> 
Tell you what, since you already mentioned that it's an older machine and since the newest Ubuntu version is pretty loaded up with lots of toys and things, why not try to run the desktop version of an earlier Ubuntu instead, say perhaps the 32bit desktop version of Karmic Koala (Version 9.10) which was only replaced a month ago, or perhaps the next version down Ubuntu 9.04 Jaunty Jackalope?

**Some additional tips:** You really should have _a bare minimum_ of 512 MB Ram these days, more is better of course. .

Or another alternative -- **I recently successfully installed Peppermint OS on an older limited-resource machine. Peppermint OS is Ubuntu-based** (and Mint-based and stays relatively up to date with the Ubuntu releases so you don't have to get involved with sorting out and finding support for older versions of programs) and doesn't fall that far from the tree except that its focused on ease-of-use for new users and being lighter-weight.  **I found that the support team is really on the ball!  I was very impressed.**


> [[IMG]http://peppermintos.com/wp-content/themes/peppermint/images/screenshot.jpg[/IMG]]("http://peppermintos.com/")
[SIZE="2"]Built for Speed[/SIZE]
Peppermint OS was designed to be easy on your processor and system resources so you can get going and get things done...

[SIZE="2"]Lightweight[/SIZE]
Peppermint OS is under 512MB and easy to run as a Live CD or USB. Loads and Shuts down in Seconds...

[SIZE="2"]User Friendly[/SIZE]
Step-by-step installation, Works out of the box, Easy to Navigate with Automatic Updates....
Seesmic Gmail Hulu YouTube Prism Flash


> 
[SIZE="3"]Get Peppermint[/SIZE]
Peppermint is a Linux based Operating System that is Cloud / Web Application Centric, Sleek, User Friendly and Insanely Fast. Download a copy and get going today
[URL="http://peppermintos.com/download"]
[IMG]http://peppermintos.com/wp-content/themes/peppermint/css/images/download.jpg[/IMG][/URL]
[SIZE="3"]
About Peppermint[/SIZE]
Peppermint was designed for enhanced mobility, efficiency and ease of use. While other operating systems are taking 10 minutes to load, you are already connected, communicating and getting things done. And, unlike other operating systems, Peppermint is ready to use out of the box. Why spend hours tinkering and tweaking? Install Peppermint and get going !!


[http://peppermintos.com/about-peppermint/](http://peppermintos.com/about-peppermint/)
"
> System Requirements:

    * i386 or derivative processor (AMD64 and x86_64 are fine as well)
    * 256 MB of RAM (possible it works with as little as 192, but not positive)
    * 4 GB hard drive space (this is an overestimate just for good measure)

Under the Hood:

    * Linux Kernel 2.6.32
    * Xorg 7.5
    * Openbox 3.4.10
    * PCManFM 0.9.5
    * LXSession 0.4.3

{skipping more details...  My bolding:}

> A New philosophy&#8230;

As long time Linux users and supporters we have seen certain levels of divide in the Linux community. We have also seen over the years the tendency to not kindly invite new users to Linux who are exploring and looking for an answer beyond the two seemingly defacto systems that dominate the market. The biggest breath of fresh air in the past few years have been Ubuntu and Linux Mint with their commitment to community and offering a welcome place for all to explore.

The notion that in order to use, enjoy and be proficient with Linux is that you will need uber-geek hacking skills is completely False. And, this is just the stigma surrounding Linux that needs to be erased once and for all with Peppermint. There hasn&#8217;t been one person we have shown Peppermint OS to who hasn&#8217;t understood how to operate it as a desktop environment by just putting it in front of them and turning it on&#8230;

**Team Peppermint is committed to welcoming new Linux users, offering them a product that is fast, easy to understand, and offering them an arena to experiment with Linux and all the while offering avenues to educate them further.** Empowering the planet with Linux is our goal. Will you join us in this journey? We certainly hope so&#8230;

Kindest regards to all,

Team Peppermint"[SIZE="2"][/SIZE]

---

### Post by NUboon2Age on 2010-05-27
Two other things I did:

1) I found that on Ubuntu if I looked at System->Preferences->Startup Applications that there were some items configured to start automatically that I didn't need and they were probably bogging things down a bit.

2) I successfully ran the Ubuntu Netbook Edition on the same machine and that was much lighter.  I had no issues with its speed.

---

### Post by jallred on 2010-05-29
Thanks for the suggestions to try Peppermint OS and Ubuntu Netbook. I burned both ISO to disk, but for some reason the peppermint disk didn't work (it started to boot up, then said there was a problem and died). But, I was able to successfully install Ubuntu Netbook. So far it has worked great! Tons speedier than Ubuntu desktop. The computer is actually usable again. I haven't had a chance to test all my hardware (like the printer and scanner), but so far so good.

Thanks again, and thank to everyone else that chimed in with suggestions.

---

### Post by tommcd on 2010-05-29
> **jallred said:**
> Thanks for the suggestions to try Peppermint OS and Ubuntu Netbook. 
If you wish to stay within the Ubuntu framework, you may also want to consider the new Lubuntu: [http://lubuntu.net/](http://lubuntu.net/) 
In my (limited) experience it runs faster and uses fewer resources than the stock Ubuntu. Lubuntu has access to the the same repos as Ubuntu. Be advised though, that if you install a lot of resource hungry apps from the Ubuntu repos (e.g., Rhythmbox or Amarok instead of a lighter music player like Exaile) your system may slow down.

Also, note that Ubuntu is based on Debian. I have always found that Debian runs much faster, and uses few resources, than Ubuntu. Debian also tends to be more stable and bug free than Ubuntu. The trade off is that Debian stable gets a bit out of date since there is a relatively long time between stable releases. You can run Debian testing if you prefer a more up to date system; but you will have to stay on top of the updates more attentively, and possibly deal with a few bugs along the way. Though Debian testing tends to be very stable due to the conservative nature of the Debian devs. Debian, and the Debian forums, are also not very friendly for linux beginners. Debian is not difficult to learn though if you have experience with Ubuntu.
Be advised: Do your homework, before asking a question on the Debian forums!!!

Other light weight distros that are very good, and easy to use:
[http://zenwalk.org/](http://zenwalk.org/)
[http://www.salixos.org/wiki/index.php/Home](http://www.salixos.org/wiki/index.php/Home)
[http://www.absolutelinux.org/](http://www.absolutelinux.org/)
Those 3 are all based on Slackware. Slackware is the most perfect linux OS in my experience.
Zenwalk, Salix, and Absolute are all intended for beginners though. Zenwalk and SalixOS in particular are very good. I have been using Zenwalk since version 4.0 and it has always worked very well for me.

---

### Post by itbcn8 on 2010-05-31
I'm having the same problem!
I log in, brand new install of Ubuntu 10.04 (through Wubi)...

And all of the sudden everything is slow and laggy.
My windows partition on this same computer runs great... so this is not a good sign for Ubuntu.

Anyway, I checked my memory and CPU usage. The RAM usage is normal and consistently underused (1.5Gb total), but my 2 CPU cores seem to alternate hitting 100% for a second (I guess enough to bottleneck everything and causing lag).

This is especially problematic because I can't stay in Ubuntu to troubleshoot (wayyyy to slow). So I don't know what you guys can do to help...

Please advise something...

---

### Post by tommcd on 2010-05-31
> **itbcn8 said:**
> 
This is especially problematic because I can't stay in Ubuntu to troubleshoot (wayyyy to slow). So I don't know what you guys can do to help...
Please advise something...
Wubi is simply a way to try Ubuntu. It was never intended to be a way to actually use Ubuntu over the long term. Since the Ubutnu live CD already allows you try Ubuntu without installing anything to your hard drive, Wubi has very little relevance or utility imo. If you want to really use Ubuntu, you will need to *install* Ubuntu to a dedicated partition on your hard drive.
Understand that the live CD will run slower than a hard drive install since cdrom access is a lot slower than hard drive access. 
If you really want to actually use Ubuntu (or any linux distro for that matter) you should do a real Ubuntu install to a dedicated partition on your hard drive.
Here is a good site to help you get started with a real Ubuntu install:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
There is also info on that site about Wubi if you wish to continue to purse using Wubi to run Ubuntu.

Here is another site to help you dual boot with Windows:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by hreichgott on 2010-05-31
I just found that uninstalling Ubuntu One, Gwibber, and couchdb made everything much, much faster.  I too was experiencing extreme slowness after upgrading to 10.04.  I have a Lenovo Thinkpad T60 with 2 CPUs and 500 mb RAM.

But please do check this thread first in case anyone has chimed in with things to beware of... I probably have just enough knowledge to seriously break something.
[http://ubuntuforums.org/showthread.php?t=1498474](http://ubuntuforums.org/showthread.php?t=1498474)

---

### Post by tommcd on 2010-06-01
> **hreichgott said:**
> I just found that uninstalling Ubuntu One, Gwibber, and couchdb made everything much, much faster.
Just out of curiosity, how did you come to decide that those packages should be removed? Did you see a separate thread on this or something?

---

### Post by hreichgott on 2010-06-01
I kept an eye on System Monitor and noticed that ubuntuone-syncdaemon was very busy.  I have no idea why I should bother having a resource-hungry Ubuntu One program running all the time on my computer when the website interface works perfectly well, and only runs when I actually ask it to run.

I searched the forums about couchdb because I was trying to figure out what the heck it was.  When I learned that it was another constantly-running document-syncing thing, I decided I didn't need it.  I found out that Gwibber depends on couchdb, but I don't use Gwibber, just Facebook.  Therefore I uninstalled Gwibber.

In general, since I have a machine with only 500 mb RAM, and since I regularly ask it to do things like stream audio, I want to keep everything else pretty minimal.

I originally switched to Linux so that I could easily keep up a machine with only the programs I actually need and use.  The closer I can get to that point, the better.

---

### Post by tommcd on 2010-06-03
> **hreichgott said:**
> I kept an eye on System Monitor and noticed that ubuntuone-syncdaemon was very busy. ... 
For future reference, you could have just gone to: system > preferences > startup applications, and disabled Ubutnu One from starting automatically.

---

