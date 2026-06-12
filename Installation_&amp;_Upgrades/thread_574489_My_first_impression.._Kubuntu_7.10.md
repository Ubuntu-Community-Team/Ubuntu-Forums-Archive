---
title: "My first impression.. Kubuntu 7.10"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by EclipseAgent on 2007-10-12
First off.. I just wanted to say.. I prefer KDE, and that is why I chose to go with Kubuntu instead of Ubuntu. As much as people want to believe it, Kubuntu is not Ubuntu w/ KDE, just look at the feature sets. 

The reason I was installing Kubuntu for testing ( I have tested various older versions also ) was to give my boss a little explanation of what I feel the differences were between Kubuntu 7.10 (Although RC) and openSUSE 10.3 (Final). First off, they both have their strong points, and we all know the Package Management in (K)Ubuntu is much better then openSUSE 10.3, so I won't harp on that, although I feel the SUSE team, finally are making some strides.. but eons away from the speed / ease of aptitude / apt-get .. 

FIrst. I am typing this from my Kubuntu box.. while downloading Ubuntu to give a shot. 

I am using a Dell D820 w/ 2GB Ram and some of the following: 

68: None 01.0: 10701 Ethernet
  [Created at net.125]
  UDI: /org/freedesktop/Hal/devices/net_00_13_02_b8_41_92
  Unique ID: L2Ua.ndpeucax6V1
  Parent ID: JNkJ.uvAosJ+1yf2
  SysFS ID: /class/net/eth1
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "ipw3945"
  Driver Modules: "ipw3945"
  Device File: eth1
  HW Address: 00:13:02:b8:41:92
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (WLAN controller)


67: None 00.0: 10701 Ethernet
  [Created at net.125]
  UDI: /org/freedesktop/Hal/devices/net_00_15_c5_24_5b_35
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.JlycKlVVZ56
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.2/0000:09:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "tg3"
  Driver Modules: "tg3"
  Device File: eth0
  HW Address: 00:15:c5:24:5b:35
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #30 (Ethernet controller)

  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xefffc000-0xefffffff (rw,non-prefetchable)
  IRQ: 21 (6115 events)
  Module Alias: "pci:v00008086d000027D8sv00001028sd000001CCbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


So here is what I had when I first installed: 

I put in the CD, while docked into my docking station. 
Live CD won't boot up. 

I undock, and boot to CD again, and all comes up fine.. I finish installation (which was very simple, as it's been for a long time with the Ubuntu family). 

I shut down, re-dock close the lid and turn on, video comes on the external screen (20" Widescreen Dell). X starts.. External monitor doesn't have a signal, so I open the laptop.. and all squiggly lines (frequency off). I again undock the machine, boot and all is good. I install the Nvidia drivers (which was very simple, thanks to the restricted driver manager). So, I then shut down and dock my computer again, and boot up.... Still nothing on external monitor. I open the monitor and the login screen is staring at me.. I log in.. have to run nvidia-settings to get output to work correctly, and even then the KDM screen doesn't see the laptop screen as disabled, and it tries to span way too much. Oh well.. 

I log on.. yay rdesktop is actually installed, but hwinfo and firefox of all things are not installed. 

Weird.. KNetworkManager says eth0 (wired) connection is up, but I have an apipa address. Re connect to wired network, and all is good.. Phew.. install a few things (restricted stuff, very easily) and decide to sit in traffic for 1.5 hours and go home. 

I get home.. decide to check wireless.. Doh!.. no go.. thanks ipw3945.. I believe I saw a bug report that this was fixed in Ubuntu.. but possibly not Kubuntu.. sad.. I'm going to have to install Ubuntu.. just to check... (this is also the same issue on openSUSE 10.3).. 

So.. now I am writing you.. from my wireless after farking around.. I just have to use killswitch, and restart it and i'll connect.. (yay).. 

But yeah.. my first overall impression for Kubuntu .. is.. It just wasn't that friendly.. Not installing while docked, the video not working very well out of the box, and FIREFOX not being installed (to me.. it has to be). With all that said, I plan on installing Ubuntu w/ KDE (not sudo apt-get install kubuntu-desktop, but just installing KDE). 

Oh well.. 

Hope someone cares

---

### Post by PmDematagoda on 2007-10-12
I suggest you take a look at some of the Ubuntu 3rd party distros such as Ubuntu Ultimate which has most of the programs installed by default including FF, it also may solve your wireless problems. Ubuntu Ultimate Edition 1.5 also has KDE installed as well, so it would be better for you.

---

### Post by buntunub on 2007-10-12
Very weird. Sounds like you have a bad cd burn. As far as I know, FF is installed by default on all Ubuntu versions; I know it was on my install of Gutsy. As far as the dual head situation, well I and many many others are having major issues with that as well. It seems they have disabled the nvidia-settings in favor of Screens and Graphics utility. Did you try that?

---

### Post by EclipseAgent on 2007-10-13
> **PmDematagoda said:**
> I suggest you take a look at some of the Ubuntu 3rd party distros such as Ubuntu Ultimate which has most of the programs installed by default including FF, it also may solve your wireless problems. Ubuntu Ultimate Edition 1.5 also has KDE installed as well, so it would be better for you.

I'll check out Ubuntu Ultimate.. Any one try it yet? What version of ipw drivers does it have? 

I am guessing Ubuntu has the patched versions yet the Kubuntu RC CD does not (I've install Ubuntu and it's patched, hopefully SUSE and the maintainers of Kubuntu will apply the patches soon). 

The problem is a known issue within the 3945 drivers..

---

### Post by PmDematagoda on 2007-10-13
I tried Ubuntu Ultimate 1.4 and it works properly and I have no complaints for it except that I wish the upgrade script could be a little more "transparent", if you know what I mean:).

---

### Post by EclipseAgent on 2007-10-13
> **buntunub said:**
> Very weird. Sounds like you have a bad cd burn. As far as I know, FF is installed by default on all Ubuntu versions; I know it was on my install of Gutsy. As far as the dual head situation, well I and many many others are having major issues with that as well. It seems they have disabled the nvidia-settings in favor of Screens and Graphics utility. Did you try that?

It's not weird IMO.. It's what I expected from Kubuntu. As much as I want it to be, Kubuntu is not really Ubuntu w/ KDE .. There are alot of differences. Also, yes Kubuntu used to install FF by default, but in 7.10 doesn't seem to be, just has Konq as default browser and Dolphin as default. 

I installed Ubuntu on my laptop now (luxury of 3 hard drives) and will test out the seperate x setup with this box.. 

I am surprised that ccsm isn't installed by default, but all other Compiz and Fusion packages are.. do they not want you to configure it? 

I am installing KDE right now on Ubuntu (sudo apt-get install kde, not sudo apt-get install kubuntu-desktop).. 

Report in a few

---

### Post by Multi-Booter on 2007-10-13
Well, I recently installed Kubuntu 64 bit on my machine... but prefer to usually stay off the cutting edge... often it's the 'bleeding edge'. So I went with the LTS version. Then install itself went great and everything. But it also did not install firefox.

I'm just a novice, but I would not expect any of the 'K' versions to include firefox in the install. I say that because KDE has it's own native browser as well as several other of it's own native items. 

If I had the kind of ability to put together an OS, if I were going to use KDE as the desktop environment, I probably wouldn't break the mold by including something like firefox on the install... just out of respect, if that makes sense?



As far as the ins and outs of one distro to another, and KDE v/s Gnome...
Really, I think it is only all in what you are already used to.

Putting my own self out there for example... My oreintation to linux was through terminal and Gnome... and most of my up-time I've spent wrenching on Fedora. After growing tired of the wrenching, I decided to try Ubuntu, and since Fedora allow me to switch from Gnome to KDE, I thought "why not Kubuntu" because I had found KDE to be a tad prettier in the past.

Now that I've actually installed Kubuntu and started ironing out the wrinkles, I feel like I'm stumbling around on it with two left feet (or two left hands maybe I should say). The distro is different and so is the desktop environment. Although it is similar, it's just enough different to be annoying and cause me to stumble around.

---

### Post by EclipseAgent on 2007-10-13
> **Multi-Booter said:**
> Well, I recently installed Kubuntu 64 bit on my machine... but prefer to usually stay off the cutting edge... often it's the 'bleeding edge'. So I went with the LTS version. Then install itself went great and everything. But it also did not install firefox.

I'm just a novice, but I would not expect any of the 'K' versions to include firefox in the install. I say that because KDE has it's own native browser as well as several other of it's own native items. 

If I had the kind of ability to put together an OS, if I were going to use KDE as the desktop environment, I probably wouldn't break the mold by including something like firefox on the install... just out of respect, if that makes sense?



As far as the ins and outs of one distro to another, and KDE v/s Gnome...
Really, I think it is only all in what you are already used to.

Putting my own self out there for example... My oreintation to linux was through terminal and Gnome... and most of my up-time I've spent wrenching on Fedora. After growing tired of the wrenching, I decided to try Ubuntu, and since Fedora allow me to switch from Gnome to KDE, I thought "why not Kubuntu" because I had found KDE to be a tad prettier in the past.

Now that I've actually installed Kubuntu and started ironing out the wrinkles, I feel like I'm stumbling around on it with two left feet (or two left hands maybe I should say). The distro is different and so is the desktop environment. Although it is similar, it's just enough different to be annoying and cause me to stumble around.

Most distro's including Kubuntu previously installed FF.  Sure it's easy enough to install. But people first trying out linux have a much better chance of knowing what FF is, other then Konq. 

I fixed the Wireless issues by installing Ubuntu and running sudo apt-get install kde kdm and all went well and wireless was fixed (damn I hope suse does it soon  too). 

Also as for the "Gnome vs KDE" blah blah.. I prefer KDE, because the looks and I find it's applications to be better.

---

### Post by Multi-Booter on 2007-10-13
> **EclipseAgent said:**
> Most distro's including Kubuntu previously installed FF.  Sure it's easy enough to install. But people first trying out linux have a much better chance of knowing what FF is, other then Konq. 

I fixed the Wireless issues by installing Ubuntu and running sudo apt-get install kde kdm and all went well and wireless was fixed (damn I hope suse does it soon  too). 

Also as for the "Gnome vs KDE" blah blah.. I prefer KDE, because the looks and I find it's applications to be better.

Agreed for sure on FF.

I can't even say what Konq is like because I am stuck right now.
Kubuntu doesn't see my ethernet at all (onboard Gigabit) which I assume means its running 'default' on my system board.
I don't even know where to begin on that one (have a thread over in networking).

KDE does no doubt look better by default than Gnome... no question.
Gnome can be adjusted to look very good too though.

In time I will have a better, more experienced opinion of KDE and it's apps v/s Gnome.

---

