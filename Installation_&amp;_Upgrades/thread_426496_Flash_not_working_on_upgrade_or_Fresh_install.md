---
title: "Flash not working on upgrade or Fresh install"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by icantthinkofausername on 2007-04-28
Hello all!

I was wondering if anyone else out there has experienced this issue with 7.04. Here are the steps I took.

1. Downloaded one fresh copy of 7.04 and installed it on my laptop and desktop.
2. On the laptop I don't have any issues with Flash. On the desktop flash won't install. All worked fine in 6.10 and 6.06.
3. So I re-installed 6.10 on the desktop ---- and now Flash is working. 
4. I upgraded to 7.04 and now its not working again.

Its obviously an issue with my hardware and 7.04...............how can I determine what the issue is and how to fix it???

:confused: :(

---

### Post by bapoumba on 2007-04-29
Hello :)

I will probably not be able to help you with hardware issues, but it looks strange to me it's working with edgy and not with feisty. May be a problem in the install process?

Feisty has now a new meta-package, ubuntu-restricted-extras (in multiverse) that installs a whole bunch of [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats"). I did install that, and flash worked right away. May be an idea to check ?

edit: lol, what a nick ;)

---

### Post by icantthinkofausername on 2007-04-29
I have tried installing from Multiverse. This is pretty much what happens to flash when it tries to install......
[B]
[I][I]Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--21:20:45--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.134.70
Connecting to fpdownload.macromedia.com|72.246.134.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .....[/I][/I][/B]


It basically locks up that terminal session. I have to stop the process by doing ctrl-c or It will stay locked up infinitely. 

Then if I try to view a web page that has flash it does not even load it. And of course if I try to install anything else I get the following message........
[B][I]
sudo dpkg --configure -a[/I][/B]

---

### Post by mister mick on 2007-04-30
> **bapoumba said:**
> Feisty has now a new meta-package, ubuntu-restricted-extras (in multiverse) that installs a whole bunch of [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats"). I did install that, and flash worked right away. May be an idea to check ?

/agree

The package ubuntu-restricted-extras is what I used on my fresh install, and I have flash as well as mp3 and some others I'm sure.

---

### Post by icantthinkofausername on 2007-05-06
Nope...........still not working folks. Basically something is not allowing me to finish the install of Flash. When I try to install **ubuntu-restricted-extras** it shows the following under "details"

[B]Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--21:20:45-- [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
=> `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.134.70
Connecting to fpdownload.macromedia.com|72.246.134.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

0K .....[/B]



Even though it says "ok" things are not ok. The install bar is only halfway across and it locks that terminal session up. This makes no sense I used this same computer on 6.10 and flash was ok. I used the same copy of 7.04 on anther computer and flash was ok on it. So its not the copy that I have problems with. 
Fortunately I love Linux and won't go back to Windows even if I cant get this to work. I might just have to stick with 6.10. I would love to use 7.04 though. 

Any help would be much appreciated..........and I do mean any!

Thanks

---

### Post by icantthinkofausername on 2007-05-06
I know this must be weird but, I have limited my conflict down to the CPU, the MOBO, or memory.

MOBO =  Asus PL-VM 1394
CPU = Intel Dual Core 6600
Ram = Kingston DDR2 667 (PC 5300)

Keep in mind that this setup worked on the Flash that was installed with 6.10. So what is different about the flash for 7.04??

---

### Post by icantthinkofausername on 2007-05-06
Okay..........after a bit of patience. The following error came up. I am guessing that this is some type of memory error?

"18:58:19 (5.42 MB/s) - Read error at byte 10938/2609703 (Connection timed out). Retrying."

---

### Post by icantthinkofausername on 2007-05-13
Well what can I say guys and gals..............other than I am very persistent:) 

I have changed out my motherboad.............still no luck
Changed out the memory...............still no luck
 Well it doesn't take a rocket scientist to discover the only thing left is my CPU. It is an Intel 6600 Dual core.
Unless 7.04 does not like DDR 667 for some reason.


Is anyone else out there using an Intel 6600 with DDR 667:confused: :confused: :confused: :confused:  

I wonder if it has something do do with the dual core on my 6600. :confused: :confused: :confused:

---

### Post by icantthinkofausername on 2007-05-15
Anyone???
Any ideas??

Please:) 

I know begging is pathetic............:( 

I not a complete newb..........but when it comes to trouble shooting issues like this I am kinda lost. I am not sure what to look for

If I do "about:plugins" in Firefox Shockwave Flash shows installed. I am assuming that this is different than Adobe Flash though. 
For example YouTube videos play just fine, but I cant even bring up the Fandango.com website. 

I am able to play YouTube videos due to Shockwave flash being installed........correct??
And Fandango won't come up because of the Adobe based Flash that is programed into the website.........correct??

What else should I look for?

---

### Post by bapoumba on 2007-05-16
Sorry I did not answer previously, but did not know what to answer :/

The error looks like a network time out problem. I looked around a bit, found similar errors for wget for ex, but did not come across a real fix.

Bumping your thread. Anyone ?

---

### Post by icantthinkofausername on 2007-05-16
Thanks for the reply bapoumba !

Well I was thinking along the lines of a network timeout at first...........then I just downloaded flash 9 onto my thumb drive from another computer. I installed it per the readme text file..........it installed okay. But when I tried to use a website with any Flash programming it does no load.

---

### Post by gbusse on 2007-06-20
Same problem here.. it is almost as if it hangs when trying to download flash from fpdownload.macromedia.com. This is really annoying.

Any tips would be greatly appreciated.

Thanks,
Gord

---

### Post by shanen on 2007-06-27
I've always had lots of problems with Flash in Ubuntu, and never had much success getting them fixed... I doubt it will be a helpful data point, but I'll say that I have now tried it under three machines running Feisty. All three of them are fairly standard IBMs, two ThinkPads and one NetVista. One of them is working pretty well, and the other two are more or less not working. The one that is working best was a clean install directly to Feisty, and the other two were upgraded all the way from Breezy. One of those machines actually has two partitions running Feisty, but neither of them works very well for Flash.

My usual test website is Comedy Central's website, where they have many Flash videos. There are at least two failure modes. In one, it just reports that Flash needs to be installed even though it has been installed. In the other, it is attempting to open a large window for a new Flash player, and it either gives a similar message about needing a new version or it just hangs indefinitely.

I think the minimalist approach I'd like to use would be to compare the two configurations, working and broken, so that I could report on something substantive about the causes of the problems. However, I don't have much idea how to isolate the Flash-specific configuration information.

---

