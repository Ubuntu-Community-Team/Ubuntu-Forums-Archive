---
title: "Trying to install on a Presario F500 laptop..."
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by NooBuntu63 on 2014-02-05
...and so far, no go. 

I have both 10.10 on a CD, and the latest version downloaded today. Because this isn't a terribly important thing - and largely experimental - I figured I'd try the 10.10 disc first. At best, it gets to the progress 'dot' bar, and just...keeps...'progress'ing...but not really. Most times, it'll stop and just hang there. Often, it'll go to a black screen after a while, but no prompt or anything. Sometimes the 'progress' bar will fill up and it'll just sit there, too. Hours of fun for the entire family.
I tried pulling the hard drive, hooking it up to another computer, and putting the latest version on it. It doesn't seem really interested in doing much, either.

As I'm typing this, I've gone back to trying the 10.10 CD and the 'progress' bar is still dotting away, 10-15 minutes in.


Any ideas on how to get this to happen?

---

### Post by NooBuntu63 on 2014-02-05
And two hours later, still working the progress bar...

---

### Post by fantab on 2014-02-05
Post some hardware details of your computer, like RAM CPU Graphics Card etc...
Are you trying to dual-boot?
Can you load Ubuntu DVD/USB and successfully "Try Ubuntu Without Installing"?
If you can, then post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

Ubuntu 10.10 has been long dead. It is not supported any more. There is no point even trying it.
Try the latest and supported version of Ubuntu, like 12.04 or 13.10.

---

### Post by NooBuntu63 on 2014-02-05
Well, I kinda did that already... created a 12.04.3 bootable USB with UNetbootin. I get as far as the UNet GUI, where I get an interesting menu...
**H**elp
**T**ry Ubuntu without installing
**I**nstall Ubuntu
**C**heck disc for defects
Test **m**emory
**B**oot from first hard disk
Try Ubuntu without installing
Install Ubuntu
Check disc for defects

... as if the list starts to repeat without the highlighted letters.

In any case, whether or not I select 'Install' or let it auto-boot, it simply hangs on this screen.

There's no dual-boot. I wiped this drive some time ago, and I intend to run only Ubuntu on it. And I'm not sure about the rest of the machine details, as it was a salvage project from a non-profit computer recycling business I worked for a few years back.

---

### Post by fantab on 2014-02-05
It is possible that the ubuntu.iso didn't BURN properly to the USB... try again after checking the integrity of the download with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM"). Re-download the .iso if needed.
You have to find out what hardware is in there. Certain Hardware require some 'special' attention. It will be difficult to guess the issue without much detail. The computer specifications are important.

---

### Post by NooBuntu63 on 2014-02-05
It has the AMD Sempron processor, and after looking (I shut it down), 1.5G RAM, NVIDIA GeForce Go 6100 video.

hashes match on .iso, too.

---

### Post by mastablasta on 2014-02-06
try the boot options (nomodeset ...) :[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also if you get to loading dots you should be able to hit Ecs and it should show what is loading or where it stopped.

---

### Post by mörgæs on 2014-02-06
I would forget about Ubuntu and go for Lubuntu 13.10 using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

---

### Post by NooBuntu63 on 2014-02-06
> **mörgæs said:**
> I would forget about Ubuntu and go for Lubuntu 13.10 using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

Since I'm learning about all this, please share why you would make that choice...?

---

### Post by mörgæs on 2014-02-06
Running a GUI during installation (as with the standard ISO) is an unnecessary risk. The alternate ISO often works when the GUI installation gives inexplicable errors, like the one you encountered. No point in troubleshooting the error, better to try to avoid.

Please post back and tell us how it worked.

---

### Post by NooBuntu63 on 2014-02-07
Well, I haven't tried Lubuntu yet because I wanted to make sure it wasn't a hardware issue; I replaced both sticks of RAM (went to 2G in the process, and ran the RAM tests) and put another hard drive in there and that's when I started to see some progress. 
*Some*.
I started with the 10.10 disc. Got all the way through to just before the end, and got an 'installation failure' message, rambling on about how either the hard drive or the CD was in error. It *did* manage to boot from the CD though, and I ran it for a few minutes in that mode.
Then, I went back to 12.04.3 on a bootable USB made with Unetbootin. I've gotten as far as going through the whole install process BUT I get an installation failure message at the 'find and install software' leg of it. I can skip that step and do the grub loader and all that goes after that; it will tell me installation is finished and it's time to reboot from the system, but when I do the machine goes to black screen and just sits there. It's hardwired to the 'net so there's no wireless connectivity issue (in previous attempts of installs it established connection with the router and got an IPv4 and IPv6 assignment), and I can see it's not even trying to connect to the 'net, let alone the mothership.

I would like to think this is something I'm doing wrong, or not 'getting', and maybe learn a little about all this... but right now, I'm eyeing the hammer in my toolbox as a next installation technique (the "Stanley Hardboot").

---

### Post by NooBuntu63 on 2014-02-07
So... I clicked on your link about old hardware...

"[I]For [AMD]("http://en.wikipedia.org/wiki/Comparison_of_AMD_processors")  processors a K7 is the baseline for reasonable performance, and the  youngest members of the K7 family (like Athlon XP or Sempron) can  support a light GUI. Again, 512 MB of memory is necessary, but 1 GB is a  big improvement.

Be aware that K7's do not offer SSE2 and hence do not support the latest  Flash. K8's like for example an Opteron or a 64 bit Athlon are the  oldest for which Flash works without modifications; just add lubuntu-restricted-extras or install Chrome (not Chromium), in which a Flash player is built in from the beginning.[/I] "

Okay, that makes sense. Not that I 'must have my Flash' or anything, but there's a level of frustration a guy doesn't need.
Then I clicked on the blog link you have...


[LIST]
[*]***NOT OLD**: Anything 64 bit or  dual-core, Pentium D, Core 2, Sempron, Opteron, etc. These are computers  designed for Windows Vista or newer, and they really aren&#8217;t old in 2011  Linux terms.*
[/LIST]


...and while I realize it's now 2014, I would think the 10.10 build would be just fine for this machine, being that this blogger has the Sempron listed. 

So, now I'm a tad confused. :)

---

### Post by Dennis N on 2014-02-07
> NooBuntu63;12921149]It has the AMD Sempron processor, and after looking (I shut it down), 1.5G RAM, NVIDIA GeForce Go 6100 video.

hashes match on .iso, too.

Some encouragement: I have a machine here (also someone else's discard) with similar specs that does very well with Xubuntu or Lubuntu, once you get it installed, of course. Except it's a desktop. Currently using Xubuntu 12.10 release. I did not attempt Ubuntu Unity at all. The installation process went normally.

AMD Sempron 3100+ 1.8ghz single-core
NVidia GeForce 6100
1 gB RAM

Good luck.

---

### Post by mörgæs on 2014-02-07
10.10 was supported until april 2012. That means for almost two years no security bug fixes have been released. In short: Don't install it.

Best is to wait with dealing with the Flash problem until rest of the system is working.

---

### Post by NooBuntu63 on 2014-02-07
> **Dennis N said:**
> Some encouragement: I have a machine here (also someone else's discard) with similar specs that does very well with Xubuntu or Lubuntu, once you get it installed, of course. Except it's a desktop. Currently using Xubuntu 12.10 release. I did not attempt Ubuntu Unity at all. The installation process went normally.

AMD Sempron 3100+ 1.8ghz single-core
NVidia GeForce 6100
1 gB RAM

Good luck.

Well, you got me to thinking about creating a bootable 12.10 USB from the server (12.10 X64), which I did. And in the past hour or so I've had the most progress so far, not getting any 'installation failed' messages. In fact, it appears to have been a successful install. With one exception:
As in other cases, when it says 'installation complete and time to reboot', and it reboots from the installation, the machine will go to black screen and just sit there.
If - as I have done previously - I hit the power button, before it shuts off I get a CLUI list of all the processes it's stopping, and the very last one is "System V runlevel compatibility". Doesn't matter how long I wait before trying this, list is always the same.

I'm extremely close to burning out on this.

---

### Post by NooBuntu63 on 2014-02-07
[SIZE=5][B]I FINALLY RESOLVED THE ISSUE!

[/B][/SIZE]




I pulled the RAM, and the hard drive, buttoned it back up, and put it in the recycle pile.


After trying for two and a half days to try to get this thing running... multiple incarnations of Ubuntu, both on CD and on bootable USB, and then a bootable USB of Lubuntu 12.04, all of which either went stillborn on reboot or had part of the install fail or have the installer crash (Lubuntu).... I've concluded this isn't fun anymore; I'll never get that time back and I probably don't have much left anyway so I don't wanna waste on frustrating idiotic pursuits like this. Too bad, because it looked like a nice little machine. Bottom line is, there is something about this thing that *does not want to work*, so I will honor that and get rid of the stupid b***h.

---

### Post by Dennis N on 2014-02-07
> K8's like for example an Opteron or a 64 bit Athlon are the oldest for which Flash works without modifications; just add lubuntu-restricted-extras or install Chrome (not Chromium), in which a Flash player is built in from the beginning.


This is misleading. Most AMD Sempron processors (like the 3100+) are K8 and DO support flash with no problem. We don't know what yours is. Depends on how old the machine is (was). All the facts are here:

[http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html](http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html)

The black screen problem on boot probably could have been solved -it's not that uncommon. You may want to think it over before its too late.

---

### Post by NooBuntu63 on 2014-02-07
Well, the specs I'd found earlier indicated a 3100 (I did neglect to include that in previous posts). As for age, the only real clue I have is the CD/DVD drive has a manufacture date of 2007 on it; whether or not that drive was ever replaced, or the drive was backstock and HP made this machine in early '08, we'll never know.
You know, I just remembered something: When I was doing the RAM test last night, I noticed the screen indicated a Turion, which had me scratching my head.
Like I said, I was able to run it live off CD, so I kept going because  of that... so it stands to reason the display and drivers are ok, or at  least compatible.

But, here's what I'm thinking: No matter what I've tried, it never either a) completes an install, or b) moves past a black screen. Having changed out RAM and harddrive, I've basically eliminated them as suspects. For crying out loud, even a Lubuntu install crashed. Something in this machine does not want to cooperate.

---

### Post by NooBuntu63 on 2014-02-07
In the meantime, the Acer 4620-6736 seems quite happy with its latest upgrade.

---

### Post by Dennis N on 2014-02-07
Sempron 3100+ was introduced in 2004, so your machine (and mine) is no older than that. _By the way, it is a 32 bit processor, so you cant use a 64 bit installer. _ 

I had intermittent boot to black problems with no spash screen on a different machine. This solution fixed it.

[http://askubuntu.com/questions/79953/why-does-plymouth-start-so-late](http://askubuntu.com/questions/79953/why-does-plymouth-start-so-late)

I didn't use the first command shown there, I just made and copied the required file to the right place. You then run the second line of the solution in the terminal. Back to the Sempron, it had no splash screen showing originally, but this same solution fixed that as well.

NOTE: There is also a Sempron 64 3100+ which is 64 bit.

---

### Post by NooBuntu63 on 2014-02-07
I took momentary pity on this thing and fired it back up, booted into system setup.

Athlon 64x2 dual-core TK-53, 1700 MHz, system board id of 30D3

Built on Wednesday, Dec. 5, '07, rolled off line at 3:31 in the afternoon.

---

### Post by Dennis N on 2014-02-07
That is a fairly new machine. It should be good for Linux. Both my laptops are older than that and they run Linux.
This may work to get past the black screen: Ctrl+Alt+F2 may open a terminal. Log in, then try startx to get to the desktop.

---

### Post by NooBuntu63 on 2014-02-07
> **Dennis N said:**
> That is a fairly new machine. It should be good for Linux.
This may work to get past the black screen: Ctrl+Alt+F2 may open a terminal. Log in, then try startx to get to the desktop.

Assuming there's an install on the hard drive, yes? In other words, let it do its thing up until it goes black, then try to get terminal...?

---

### Post by Dennis N on 2014-02-07
Correct. Linux has to be loaded and running, but the screen is black because the desktop did not start; there may be a cursor. If the OS is not running, it won't work.

You can also possibly boot into recovery mode, but I have never needed to use that.
Also see nomodset in next post.

---

### Post by Dennis N on 2014-02-07
Also consider **nomodset** option, which seems to be a solution for black screen:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)
google or search ubuntuforums.org for many other posts on nomodset.

Recovery Mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by mörgæs on 2014-02-08
> **Dennis N said:**
> This is misleading. Most AMD Sempron processors (like the 3100+) are K8 and DO support flash with no problem. We don't know what yours is. Depends on how old the machine is (was). All the facts are here:

[http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html](http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html)

The black screen problem on boot probably could have been solved -it's not that uncommon. You may want to think it over before its too late.

Thanks for pointing out. Correct, Sempron is a big family, and most members support SSE2. The post has been edited now.

---

### Post by mörgæs on 2014-02-08
NooBuntu, the thread is marked 'solved'. Good!
In order to help other people please post the solution.

---

### Post by NooBuntu63 on 2014-02-08
The solution was to take the removeables out of it and put it in the recycle pile.

---

### Post by mörgæs on 2014-02-09
Oh... sad that you took that road without posting the results from the alternate ISO. A 64 bit double core is quite capable.
Well, your decision.

---

### Post by NooBuntu63 on 2014-02-10
OK, well... you've apparently also missed where I tried Lubuntu - at your suggestion and for great reasons - only to have the installer crash on me and fail as well.

I only have so much time and energy for this stuff. I never got to have kids, but I'm pretty certain it's easier to get a teenager to clean his/her room than it is to get this particular laptop to accept an installation of Ubuntu.

---

