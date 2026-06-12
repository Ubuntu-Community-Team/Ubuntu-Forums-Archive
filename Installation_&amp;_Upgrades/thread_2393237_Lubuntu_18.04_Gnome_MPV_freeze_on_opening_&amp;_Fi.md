---
title: "Lubuntu 18.04 Gnome MPV freeze on opening &amp; Firefox 59 tab crashes for some websites"
date: 2018-05-31
forum: Installation &amp; Upgrades
---

### Post by aksam84 on 2018-05-31
Hi,
I've been running Lubuntu 14.04 on my desktop pc for 2 years. It was great and I'm very satisfied. However as forum members advice here, for pass couple of days, I tried the Lubuntu 18.04 using a live USB drive and then installed it on my pc. After installing everything seems to be ok except when I open or try to play a video the Gnome MPV players freeze. It completely freezes the pc, no key or combination of keys work. I had to restart the pc. 

I looked for solutions online and tried out some but nothing worked so far. What should I do? Please help. Thanks

--------------
My PC comfiguration is as follows.

Samsung brand CPU
CPU TYPE: Intel Core 2 Quad Q8200
CUP Speed: 2.33 GHz.
CPU Core: Quad Core
Memory: 4096 MB

VGA Compatible controller: NVidia Corporation C73 [GeFore 7100 | nForce 630i] (rev a2)

-----
Running "sudo sudo lshw -C video" for graphic card gave me this answer in command line:
> sudo sudo lshw -C video
[sudo] password for aksam: 
  *-display                 
       description: VGA compatible controller
       product: C73 [GeForce 7100 / nForce 630i]
       vendor: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:19 memory:f1000000-f1ffffff memory:d0000000-dfffffff memory:f0000000-f0ffffff memory:c0000-dffff



---
Here are some of the things I've tried doing so far to rectify this issues.

* Tried live USB again and tried to open Gnome MPV in it but it  also freezed.
* I did a checksum of the live USB before installing the OS.
* Updated os using software updater after isntalling
* Installed extra codecs for mp3, mp4 etc.
* I desabled Firefox -> Preference-> "Use hardware acceleration when available"
* Installed VLC Player (I was able to play a few videos using vlc. it worked normal except once it got stuck when I rewinded a video I think)
*

---

### Post by TheFu on 2018-05-31
No clue from me, but there have been some issues with video players running inside "snaps" - perchance, was mpv installed via snap?

If you run mpv from a shell with one of the files that fails, what exactly are the outputs?  You can send the output to a file using '**tee**'.

---

### Post by aksam84 on 2018-05-31
TheFu,
Thanks for the reply. I'm sorry, I'm not very familiar with linux technical stuff. So, I'm not sure about "snaps" or how to run the mpv player in a shell and get the output. Can you please explain the steps for me please?

The Gnome MPV player came installed by default when I installed Lubuntu.  I  installed Lubuntun using the Live USB I created via the  pendrivelinux.com software after downloading the 32 bit iso file from  Lubuntu website.

By the way, I've been checking more solutions online and one had mentioned about inadequate swap partition space. I wondering whether it can be the issue because when installing, it asked for partition I did by guesswork (I coudn't read anything about proper partitioning because didn't have anything to access internet for info). I don't think I made a swap partition. But then again, even when I run MPV in the Live USB drive it freezes the machine. What do you think?

---

### Post by TheFu on 2018-05-31
Thanks for asking.  Nobody knows this stuff in the beginning.  Best to ask when something isn't clear. We've all been there.  Sometimes google can help too, but for really new-to-linux people, google can provide wrong or dangerous data too. It takes experience to learn trustworthy sources.  Generally, I look for websites with "ubuntu" somewhere in the domainname part for reputable sources.  help.ubuntu.com wiki.ubuntu.com   .. askubuntu.com ... ubuntuforums.org ... you get the idea.

I don't run 18.04 yet.  I did beta test it pre-release for a few weeks.  It made some fundamental changed to the way things work, so I wanted to give it a few months before I brought it into a test system.  Definitely won't use it for "production" until the fall, at the earliest.  Some people think I'm overly cautious.

I use mpv, but without any GUI.  It is run from a terminal. For me, using the terminal is more efficient, since it doesn't change with every release and works the same on the local computer and on computers 5K miles away.  Everyone should use the interface that works best for themselves.  What works best for you is all that matters.

For troubleshooting, using a terminal/shell/CLI is the first step almost always.  
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Most of the time, Ctrl + Alt + T  will bring up a new terminal window.

Snaps ... a very simple tutorial, perhaps too simple. [https://tutorials.ubuntu.com/tutorial/basic-snap-usage](https://tutorials.ubuntu.com/tutorial/basic-snap-usage)   I don't know much besides the 10,000 ft version. That link doesn't explain WHY a snap is good in some situations and not in others. [https://docs.snapcraft.io/snaps/intro](https://docs.snapcraft.io/snaps/intro) is a little better, though uses techno-mumbo-jumbo.  Looks like a standardized way,probably a little better,  to do things we were doing in the 1990s with environment variables and jails.

mpv is tied to the GPU drivers.  Are you using the correct drivers for your GPU?

---

### Post by poorguy on 2018-05-31
I wasn't able to get ***Gnome-MPV*** working at all.

I uninstalled ***Gnome-Mpv*** using*** Synaptic Package Manager***.

I then restarted my computer and using ***Synaptic Package Manager*** I installed*** MPV***  [COLOR=#ff0000]***not Gnome-MPV***[/COLOR] .

After installing ***MPV*** do the following.

Open ***Command Terminal ***and **copy and paste** this command [COLOR=#0000cd]***sudo apt install libdvd-pkg***[/COLOR]  then ***press enter*** and ***enter your password***.

Then*** copy and paste ***this command [COLOR=#0000cd]***sudo dpkg-reconfigure libdvd-pkg***[/COLOR]  then ***press enter***.

When all is done restart your computer you should be good to go.

---

### Post by monkeybrain20122 on 2018-05-31
> sudo sudo lshw -C video
[sudo] password for aksam: 
  *-display                 
       description: VGA compatible controller
       product: C73 [GeForce 7100 / nForce 630i]
       vendor: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: **driver=nouveau** latency=0
       resources: irq:19 memory:f1000000-f1ffffff memory:d0000000-dfffffff memory:f0000000-f0ffffff memory:c0000-dffff

Maybe you need the proper driver for your graphic card. The 7100 requires nvidia-304 but it has been [removed]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1748000") from the repo due to lack of maintenance upstream. Fortunately you can still get it from the graphic driver [ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=bionic").

To install the driver
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-304
```

Then reboot.

P.S Also repo's mpv tends to be out of date. I would get it from mc3man's [ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-test"). And [smplayer]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer/") is a way better front end to mpv than gnome-mpv IMO.

---

### Post by poorguy on 2018-05-31
> **monkeybrain20122 said:**
> 
P.S Also repo's mpv tends to be out of date. I would get it from mc3man's [ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-test"). And [smplayer]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer/") is a way better front end to mpv than gnome-mpv IMO.

Yeah seems like when I was using ***Ubuntu 14.04 LTS Trusty Tahr ***and was using ***MPV ***the version in the repo was several versions old.

What I see in the repo is this version  ***0.27.2-1ubuntu1*** so it isn't that far behind.

The latest version I could find is ***0.28.2*** ***stable release ***in the link below.

[https://en.wikipedia.org/wiki/Mpv_(media_player)](https://en.wikipedia.org/wiki/Mpv_(media_player))

I'm going to stay with the repo version as it works well for me on my outdated spare parts computer. ;)

---

### Post by monkeybrain20122 on 2018-05-31
> **poorguy said:**
> Yeah seems like when I was using ***Ubuntu 14.04 LTS Trusty Tahr ***and was using ***MPV ***the version in the repo was several versions old.

What I see in the repo is this version  ***0.27.2-1ubuntu1*** so it isn't that far behind.

The latest version I could find is ***0.28.2*** ***stable release ***in the link below.

[https://en.wikipedia.org/wiki/Mpv_(media_player)](https://en.wikipedia.org/wiki/Mpv_(media_player))

I'm going to stay with the repo version as it works well for me on my outdated spare parts computer. ;)

It is not that far behind because 18.04 is a new release, in a while it will become old. :)

---

### Post by poorguy on 2018-06-04
[QUOTE=monkeybrain20122;13772256]
And [smplayer]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer/") is a way better front end to mpv than gnome-mpv IMO.
/QUOTE]
Hey monkeybrain20122,

I went ahead and installed [COLOR=#0000cd]smplayer[/COLOR] and you are right about the front end being way better.

I really appreciate the input / advice / opinion as nothing is better than an actual user testimonial. :)


Thanks

---

### Post by aksam84 on 2018-06-05
Sorry for the late reply everyone. Thank you for trying to help me. After trying out 18 for few days now I have decided to isntall 16 for the time being. I will upgrade to 18 maybe at the end of the year. 

TheFu,
Thanks for the detailed reply. I've been working on 18 for the past few days and while its ok, there are some issues coming up. Sometimes when I switch on the pc the Internent doesn't work, but works when I reboot it. Other times it works. Since yesterday sound isn't work. No pc sounds or youtube/vidoe sounds. I think like you, I'll install 16 and upgrade to 18 after sometime.

---

