---
title: "[SOLVED] Dual boot Dell Lat D630 install problems"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by CharlieNixon on 2007-07-07
Hi all,

Please let me know if anyone has any ideas. I have XP installed already on my drive (I have to have XP for work). I want to use the partioner to create a new partion and dual boot Ubuntu.

I tried to install 7.04 from a disc I made via the .iso file. I checked the file's MD5 and checked the CD with the provided utility. After I choose "install" I get some stange prompt that says "type 'help' for a list of commands".  It looks like some kind of shell. 

After that didn't work twice I tried an older .iso file (verson 5, Breezy) I had on hand. I burned the disc and this time the install started, but would not detect the NIC.

AHHH!! I ordered a disc to be mailed, but it will take weeks. What should I do?

Thanks

---

### Post by Pumalite on 2007-07-07
What's your memory? If 256 RAM or less>'Alternate Xubuntu CD'

---

### Post by CharlieNixon on 2007-07-09
2 Gigs

---

### Post by Pumalite on 2007-07-09
You can use Ubuntu Live CD without problems. After Md5sum of iso, burn at 4x or less. Then check integrity of CD before install. Download yourself a Live CD. See if that works. ( seems you are using 'Alternate CD' now)

---

### Post by CharlieNixon on 2007-07-09
Sounds like a good idea. I don't remember at what speed I burned the disc. I know I downloaded the live CD and I already checked the MD5, so I'll re-burn at a lower speed and post the results.

---

### Post by CharlieNixon on 2007-07-10
I burned a new copy at 8x (that's the slowest Nero will burn) and I have the same problem. Here are some better details:

The CD runs when windows is already running. It opens with no problems and I even downloaded Firefox from it. However, the problem occurs when I try to boot from the CD. I can not run the Live CD function or anything else. The menu comes up with several options (launch or install, check this disc for errors, etc) but when you make a selection it dumps you to some kind of Linux prompt with the error "can not access tty...type help for a list of commands" (typing help just gives you a list of standard Linux commands). 

I'm starting to think this isn't a problem with the CD, but maybe the BIOS on the laptop or something. Any thoughts??

---

### Post by jsage on 2007-07-10
Charlie,

You're going to have difficulty with both the Feisty or Gutsy live CDs - the Santa Rosa chipset in the D630 is fairly new and either live CD will dump you to the BusyBox shell.  Here's what you need to do to get your dual-boot set up on the D630:

1. In Windows XP, defrag your hard drive at least three times.  This will move most of the Windows install into a contiguous group of files, making the partition resizing much easier.

2. Download and burn a GPartEd live CD to resize the partition, version 0.3.4-8.  Get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

3. Boot GPartEd and resize your partition to whatever size you feel is appropriate for Windows.  On my 120GB drive in my D630, I used 40GB for Windows.

4. Download and burn a Feisty "Alternate Install" CD.  You can get it here (if you're in the US):  [http://mirrors.easynews.com/linux/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso](http://mirrors.easynews.com/linux/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)

5. Boot the alternate install CD and select a text-based install.  When you get to the partitioning section, you can choose Guided (let the installer make decisions) or Manual (you make the decisions).  I chose Manual.  Here's the layout I used for dual boot:

  Partition 1 (sda1) - Dell diagnostics partition (primary)
  Partition 2 (sda2) - WIndows XP (primary)
  Partition 3 (sda3) - swap (primary, end of drive)
  Partition 4 (sda4) - root (logical)
  Partition 5 (sda5) - home (logical)

When you've got all this done, the install should proceed smoothly.  To resolve the remaining D630 issues in Feisty, look here:

[http://ubuntuforums.org/showthread.php?t=481651&highlight=feisty+d630](http://ubuntuforums.org/showthread.php?t=481651&highlight=feisty+d630)

Keep in mind that a few issues will not be solved until Gutsy is complete.


have fun,
john

---

### Post by kansei on 2007-07-10
Good stuff. So the wired, wireless, etc will work fine in  gutsy? I've been doing all my gutsy testing on my 'old' D620, but I've got a D630 sitting here collecting dust (still sealed in the packaging) and think I might put gutsy on that instead. If I ghosted the 60GB D620 drive to the 120GB D630 drive, you think it'll actually boot? As long as at least the wired network car works that would be awesome, don't really feel like reinstalling again (I install operating  systems 5-10x a day, it gets old)

off-topic, how do you like the D630? Is the graphics performance acceptable? I 've heard great things about the Crestline graphics but it's 8MB of video memory vs 128MB on my D620 (nvidia quadro 110m).

---

### Post by jsage on 2007-07-10
kansei,

I haven't gotten Desktop Effects to run more than a few minutes without freezing my session completely (CTRL-ALT-BACKSPACE won't work either).  I've only had the D630 for a day now.  I've migrated just the essentials from my IBM T43p so far.

Performance with the C2D 2.4GHz seems very nice - much more snap than the 2.13GHz  Pentium M in the IBM.  When booting XP, the display properties show 384MB RAM assigned to the graphics adapter, but I don't know where to look to find this in Linux.

In Feisty, the Fn keys for battery, brightness, volume and suspend work fine.  Haven't tried the others.  And the D630 will not come out of suspend correctly.  No WiFi, haven't tried Bluetooth yet.  Nor have I tried TPM or the fingerprint reader.

As far as Gutsy goes, I hear the 4965AGN card will be supported.

Despite all this, I've used it all day as my primary email / brower / office suite machine with no problems.  As I have time I'll work on nailing down the rest of the issues.

have fun,
john

---

### Post by kansei on 2007-07-10
I'm honestly considering swapping the D620 motherboard into the D630 so I can keep the nvidia graphics (though the latest nvidia drivers have loads of bugs). though I need to remind myself that I don't game.. at all.. as long as I can eventually get desktop effects working I'll be happy.

I already swapped my intel 39xx wireless card and bluetooth module from the 620 into the 630.. I gotta figure out what the best combination of hardware is :P

now to get ubuntu installed on the D630 (on my T42 right now :) ).

edit: crap! after 3 hours of downloading the x64 install cd I just read that line about needing the alternate cd. why oh why isn't the text install included on both discs??

edit2: screw it I'm just going to take the processor from the 630 and put it in my (non-64bit) 620. I'll stick to the 'old' chipset until things are straightened out more (hopefully by the time gutsy releases?)

edit3: maybe I'll swap motherboards so I can use a shiny new laptop.. good thing I'm a DCSE :P

edit4: ok so the core2duo isn't compatible with the coreduo motherboard.. I could have swore I read somewhere they were compatible, plus didn't some late model D620s come with the core2?? bah

---

### Post by CharlieNixon on 2007-07-11
John,

I followed the suggest steps and they worked mostly well. I was able to re-size the windows partition and get fiesty installed with one problem. The GDM doesn't work. When I attempt to start Ubuntu the systems returns "no screen" errors and outputs a pretty interesting display. I have the ability to view a report of the failure and then I am ushered to the shell. 

At one point in the install it asked me to choose a screen resolution. I made my best best guess, but I'm sure it could be wrong. Could this have caused the problem?

Anywho, once I figure out how to get the gui up and running it will be easier for me to work through the other issues (WiFi, etc). So I'm looking forward to getting there.

Any ideas?

thanks

---

### Post by Pumalite on 2007-07-11
Have you tried?:

sudo dpkg-reconfigure xserver-xorg

---

### Post by jsage on 2007-07-11
> **CharlieNixon said:**
> 
Any ideas?


charlie,

from the command line, type this:

```
sudo apt-get install xserver-xorg-video-intel
```then, edit your xorg.conf file using this command

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```in your xorg.conf, look for the section entitled "Device", about 2/3rds of the way down.  In the "Device" section, you'll see the line:

```
     Driver     "i180"
```it might be "i810", "vesa" or even something else.  change it to look like this:

```
     Driver     "intel"
```now, restart and see if you can get into X.


have fun,
john

---

### Post by CharlieNixon on 2007-07-11
Puma,

I tried "sudo dpkg-reconfigure xserver-xorg". Autodetecting the screen type failed, so I tried the manual route. The system asked about 20 questions about what type of hardware I have. Needless to say, no dice.

John,

I tried those steps almost exactly (except I'm not familiar with nano, so I used vi). I rebooted and got the same error with the exception that now when the display fails it won't even display the shell. It seems like I'm going to have to re-install to get the shell back. Do you agree?

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **CharlieNixon said:**
> John,

I followed the suggest steps and they worked mostly well. I was able to re-size the windows partition and get fiesty installed with one problem. The GDM doesn't work. When I attempt to start Ubuntu the systems returns "no screen" errors and outputs a pretty interesting display. I have the ability to view a report of the failure and then I am ushered to the shell. 

At one point in the install it asked me to choose a screen resolution. I made my best best guess, but I'm sure it could be wrong. Could this have caused the problem?

Anywho, once I figure out how to get the gui up and running it will be easier for me to work through the other issues (WiFi, etc). So I'm looking forward to getting there.

Any ideas?

thanks

yeps. Try in the shell:

sudo apt-get install GDM

Good luck! ;)

---

### Post by jsage on 2007-07-11
> **CharlieNixon said:**
> It seems like I'm going to have to re-install to get the shell back. Do you agree?

charlie,

possibly not, try this first.  type the following command again:

```
sudo apt-get install xserver-xorg-video-intel
```it should either tell you that the newest version is already installed, or it should install it.

next, open up the attachment in this post.  it's a copy of my xorg.conf which works fine on my D630 in Feisty (except I haven't got touchpad scrolling working yet).

replace the contents of your /etc/X11/xorg.conf with my version.

let's see what happens.



john

---

### Post by jsage on 2007-07-11
charlie,

it just occurred to me that you might be running with the optional nvidia card.  if that's the case, then my xorg.conf will not work for you.  you'll need to use one of the nvidia drivers.


john

---

### Post by Pumalite on 2007-07-11
The thing with configure  xorg is that gives you the opportunity to choose a 'jack of all trades' driver: vesa. That allows you to get in, and once you are in, you can start thinking about installing special or propietary drivers. So if you are using an Nvidia card and you are having graphical interface problems; you can still get in. Where did you fail with my command?

---

### Post by CharlieNixon on 2007-07-11
John,

I am running the intel graphics chip (according to "lspci"). But I can not figure out how to get your file on my file system. I copied it to a flash drive and tried to mount it in my file system with:

sudo mount /dev/sda1 /mnt/usbflash

but apparently sda1 is not the flash drive because when it mounted there was a whole mess of crap in there that looked like system files. If I can figure out how to mount the flash drive (or a CD for that matter) I will try your file.


Puma,

It "failed" immediately in that it did not auto detect my graphics chip. It tries to have me fill out all the specs on it by answering a bunch of questions, but I don't know the answer to any of them.


P.S. I reloaded a fresh copy (same error with the screen) of Ubuntu so I can keep trying...

---

### Post by kansei on 2007-07-11
> **CharlieNixon said:**
> John,

I am running the intel graphics chip (according to "lspci"). But I can not figure out how to get your file on my file system. I copied it to a flash drive and tried to mount it in my file system with:

sudo mount /dev/sda1 /mnt/usbflash

but apparently sda1 is not the flash drive because when it mounted there was a whole mess of crap in there that looked like system files. If I can figure out how to mount the flash drive (or a CD for that matter) I will try your file.


Puma,

It "failed" immediately in that it did not auto detect my graphics chip. It tries to have me fill out all the specs on it by answering a bunch of questions, but I don't know the answer to any of them.


P.S. I reloaded a fresh copy (same error with the screen) of Ubuntu so I can keep trying...

It'll be sdb1 most likely. Your onboard hard drive is sda on todays laptops (serial ATA).

---

### Post by CharlieNixon on 2007-07-12
Thanks Kansei, that worked great.

John,

I was able to copy your file and got the same result. The GUI doesn't load and it causes more problems (in that I can't even get to the shell). So I rebooted in recovery mode and put the old file back in place (glad I made the backup) and I'm back to where I started at least (which is command line, but no GUI). 

Do we have any more ideas?

---

### Post by jsage on 2007-07-12
charlie,

well, i only have two more suggestions.  first, go back into your xorg.conf and in the "Device" section replace

```
     Driver    "intel"
```with

```
     Driver    "vesa"
```on my initial feisty install, it used the vesa driver just fine and at the proper resolution.  you might want to first make sure that the vesa driver is installed:

```
sudo apt-get install xserver-xorg-video-vesa
```if that doesn't work, try re-installing from the alternate cd.  since you've already created the partitions, all you'll need to do is specify mount points for and reformat / and home.

have fun,
john

---

### Post by CharlieNixon on 2007-07-12
I am currently using the vesa driver (that is, vesa is listed under "device" in the /etc/X11/Xorg.conf and I can see the shell, remember when I loaded the intel version I couldn't even get to the shell). Anywho, when I issued the command **startx** the screen blinks like it's trying to start and then comes back to the shell prompt with an error that says a bunch of stuff. One of the lines says:

no screen (s) found

The message also says a error has been logged in a file (I think /var/log/Xorg.conf.something). I looked through the file and read that the video chipset was found and found a line that said:

screen (s) found, but not configured (paraphrase)

What I'm saying is that I have the intel chipset, but the vesa driver(s) loaded. 

Does this seem like a problem that may not be fixable? Should I attempt to load another distro? I'd really like to use Ubuntu, but I can't figure this out. How is it that the gui can work on some people's d630 and not on others? I is there anything else to configure?

to summarize: AAAAAAAAAAHHHHHHHHHhh

---

### Post by CharlieNixon on 2007-07-12
more info:


The error says: No matching modes were found.

When I boot the system it looks like it is trying various resolutions or "modes". It tries 1240x768 and fails. Then it tries another resolution and fails. Finally it settles on the orginal 1240x768 and failing. So it looks like this kinda:

usplash: trying mode "1240x768"
usplash: trying mode "1240x800" (or something)
usplash: using mode "1240x768"

login@


I also tried editing the /etc/X11/xorg.conf and changing all the listed modes to "1440x900" (which is what is listed in the file John gave me which he uses) as well as changing the monitor from "generic monitor" to "Dell 630". I rebooted and it still tried the same list of modes and got the same old error "no matching modes". I guess those modes are listed somewhere else for this "usplash". 

any thoughts??

---

### Post by CharlieNixon on 2007-07-13
Hey y'all,


I found a thread that talks directly about the video issue I'm having and since my original problem was the install itself (which John answered for me) I am going to mark this thread as resolved. Thanks for all the help!


If anyone else is having display problems with their D630 check out this thread:
[http://ubuntuforums.org/showthread.php?t=481651](http://ubuntuforums.org/showthread.php?t=481651)

thanks again!

---

### Post by jsage on 2007-07-13
charlie,

the problem in the "Latitude D630 with Feisty" thread is a blurry display once an X session has started.  since you can't get X to start, you have a far different issue.  my feeling is either your notebook has a bad video subsytem or your X installation is hopelessly borked.

the easiest thing to try at this point is a re-install (msg #22) from the alternate CD.

the D630 issues that everyone's having stem from Intel's Santa Rosa platform, which is brand new.  similar issues face everyone who has a Santa Rosa-based notebook (T61, etc).

dell uses two different video sets (nvidia and intel) and four different wifi cards (atheros/ dell AG or AGN, intel 3945 or 4965).  all have varying degrees of support with linux.

bottom line - you're on the cutting edge of hardware, so expect to bleed a bit.  if you want better linux support, install gutsy from an alternate cd.  but then you're on the cutting edge of software, so you're going to bleed some more.

since you can boot XP, you're notebook probably has no hardware issues.  so use XP day to day until gutsy is released (october), then try again.  or try the feisty reinstall.  my D630 installed fine (once i setup the partitions with gparted live) and started X with the vesa driver and the correct resolution.  i installed the intel driver and restarted x without having to touch my xorg.conf.  you should be able to do this too.

have fun,
john

---

### Post by CharlieNixon on 2007-07-13
> **jsage said:**
> charlie,

the problem in the "Latitude D630 with Feisty" thread is a blurry display once an X session has started.  since you can't get X to start, you have a far different issue.  my feeling is either your notebook has a bad video subsytem or your X installation is hopelessly borked.

...

since you can boot XP, you're notebook probably has no hardware issues.  so use XP day to day until gutsy is released (october), then try again.  or try the feisty reinstall.  my D630 installed fine (once i setup the partitions with gparted live) and started X with the vesa driver and the correct resolution.  i installed the intel driver and restarted x without having to touch my xorg.conf.  you should be able to do this too.



That thread does deal with the blurry issume mostly, but in post #5 one user (susan_1890) gives a list of instructions for when the graphics don't work at all, which is the problem I'm having. 

...

I'm not against re-installing. I've already done that. If I re-install again it will be the third time. The second install generated the exact same error as the first. Do you really think a third install will yield a different result? Further, I used gparted live to resize my partitions, I used the alternate CD and I used (am using) the vesa driver (I still don't know what resolution I should be aiming for). All of this to say that I don't know why the display is not working, but I believe I've followed your instructions exactly. If there is a command you would like me to run and report the output to verify we're on the same page (hardware wise) I am more than willing to oblidge. 

My guess is that there is some hardware difference between our D630's. The question is what and where. And, like I said, I am able to install the OS from the alternate CD, which was the point of this thread in the first place. Do you think I should begin a new thread called "D630 display problems" or something?

---

### Post by jsage on 2007-07-13
charlie,

i understand your frustration.  i still believe though that your X install or xorg.conf is hosed.  i'm attaching another xorg.conf with the vesa driver configured to work properly at 1024 X 768 (should be a safe resolution for testing).

the zip contains two files - xorg.conf.vesa and xorg.conf.intel.  i've used both files as is on my D630 and they work as required.  try copying xorg.conf.vesa to /etc/X11/xorg.conf and let me know if this works.  if that works, then try xorg.conf.intel - you can always go back to xorg.conf.vesa if it doesn't.

john

---

### Post by kansei on 2007-07-13
p.s. there's no atheros wifi card that I'm aware of.. the 'dell' wireless card (the G one, model 1390 I think?) is a Broadcom.

And for the OP.. 1440x900 is the native resolution of the panel.

---

### Post by jsage on 2007-07-13
> **kansei said:**
> p.s. there's no atheros wifi card that I'm aware of.

sorry kansei, i was probably thinking of the T61.  i'm going back and forth with feisty on both the D630 and the T61.


john

---

### Post by CharlieNixon on 2007-07-16
It's working! I used the xorg.conf.vesa file and the GDM started working. The maximum resolution looks like it's 1024x768. Should I try the intel drive to get the better res (1440x900) or should I just manually edit the the xorg.conf file?

---

### Post by kansei on 2007-07-16
> **CharlieNixon said:**
> It's working! I used the xorg.conf.vesa file and the GDM started working. The maximum resolution looks like it's 1024x768. Should I try the intel drive to get the better res (1440x900) or should I just manually edit the the xorg.conf file?

Well to get halfway decent performance you'll need to get the intel drivers working eventually. Make a backup copy of your current xorg.conf so when you play around with stuff, you can always go back.

p.s. how is the battery life on that thing with the intel card? With wifi/ethernet on and the screen at brightness level 3 (default for on battery in the bios), the extended battery AND the battery that sits in the d/bay, the power meter was reporting 11 hours 55 minutes remaining! On my D620 (also a 2ghz core2duo, but lower front side bus and memory speed.. also Nvidia Graphics card) with the big extended battery I get 2 hours tops

---

### Post by CharlieNixon on 2007-07-17
I haven't really tested the battery life yet (I've only had it a few weeks and it is on my desk most of the time).  I'll letcha know if/when I test it. 

As far as updating to the intel driver is concerned, what do I have to do? Is it as simple as swapping the xorg.conf.vesa (which I'm currently using) with the xorg.conf.intel? 

Also, will moving to the intel driver net me a higher resolution than 1024x768?

---

### Post by jsage on 2007-07-17
charlie,

> Is it as simple as swapping the xorg.conf.vesa (which I'm currently using) with the xorg.conf.intel?yes


>  Also, will moving to the intel driver net me a higher resolution than 1024x768?and yes too.



have fun,
john

---

### Post by CharlieNixon on 2007-07-25
I forgot to reply...but this worked also. Thanks a bunch!

---

### Post by CharlieNixon on 2007-07-27
John,

I must be off my rocker. I just realized something strange about my display. The resolution is set to 1440x1024 (even though it is defined in /etc/X11/xorg.conf as 1440x900) and I have no option for 1440x900. This means that I can't see the bottom bar of my desktop. 

Why it took me so long to notice this is beyond me. I went to hit the "show desktop" button and thought "HEY!! where is my bottom bar!"

I think setting it to 900 would do the trick, but I don't know where to do that (other than the previously mentioned file). 

Did you have this problem or know how to fix it?

---

### Post by kansei on 2007-07-29
> **CharlieNixon said:**
> John,

I must be off my rocker. I just realized something strange about my display. The resolution is set to 1440x1024 (even though it is defined in /etc/X11/xorg.conf as 1440x900) and I have no option for 1440x900. This means that I can't see the bottom bar of my desktop. 

Why it took me so long to notice this is beyond me. I went to hit the "show desktop" button and thought "HEY!! where is my bottom bar!"

I think setting it to 900 would do the trick, but I don't know where to do that (other than the previously mentioned file). 

Did you have this problem or know how to fix it?

I'd just set it in /etc/X11/xorg.conf .. any util you use to change it will just edit that file anyhow.

weird though

---

### Post by CharlieNixon on 2007-07-30
what I'm saying is that the file already says 900, but the gui says 1024

---

### Post by kansei on 2007-07-30
> **CharlieNixon said:**
> what I'm saying is that the file already says 900, but the gui says 1024

I've never had the gui actually list my current resolution properly.. it wasn't enough of a bug for me to file a report though. Are you sure your bottom bar isn't just removed?

---

### Post by CharlieNixon on 2007-07-31
I figured it out. The resolution is not set by the driver alone but also by the type of screen detected. With the default laptop screen only the native (1440x900) will boot and work fine. Where things get messed up is when I boot with an additional screen attached to the vga output. I guess it confuses the driver when the hardware detects a different size screen attached. 

Anywho, the solution is just to hook up the additional display AFTER the lappy boots.

---

### Post by markusfarkus on 2007-08-10
FYI to anyone that cares. I was having trouble with my Latitude D630.  My plan was to dual boot Vista and Ubuntu (this will work with XP as well).  This post says to use Gparted live disk...but that did not work for me.  Vista can now resize partitions...and you don't have to have Vista installed to so.  If you boot off of a Vista disk and get to a command prompt you can use the command diskpart to resize partitions on a hard drive.  I don't know if this will be of any help to anyone, but it seems like the latitudes are so much trouble and this helped me out a lot.

Thanks everyone.

---

### Post by markusfarkus on 2007-08-10
I forgot one more thing.  [http://support.microsoft.com/kb/300415](http://support.microsoft.com/kb/300415) is the link so you know how to use the command.

---

