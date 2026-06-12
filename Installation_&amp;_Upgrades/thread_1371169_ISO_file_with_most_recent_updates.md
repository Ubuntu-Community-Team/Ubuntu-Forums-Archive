---
title: "ISO file with most recent updates"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by ublondie on 2010-01-03
After not having used Ubuntu for a few months now, I want to make up a new LiveCD and possibly a bootable USB. The times I have done this in the past, the installations don't include recent updates which need to be downloaded and installed once the system is running. (Understandably)

Two questions:

1) Does Ubuntu update the downloadable ISO periodically to include recent updates?

...for example: Now that it is January (ie. some 3 months after release of Karmic in October '09 and some 200-300Meg+ of updates required since that time), will I be downloading an ISO from Ubuntu that has recent updates already as part of it, or will it still require updates to be downloaded and installed once Ubuntu is running on the computer?

2) If the downloadable ISO has not been updated since Oct '09, is there a way of making a LiveCD/bootable USB that has up-to-date updates already installed?   (if you know what I mean?)   ....and is this process relatively simple?

Thanks

---

### Post by Herman on 2010-01-03
> 1) Does Ubuntu update the downloadable ISO periodically to include recent updates?No, only every six months when a new release comes out. Excpet for LTS releases, those get something called 'point releases', every now and again, see [Ubuntu Release Cycle]("http://www.ubuntu.com/products/ubuntu/release-cycle") - ubuntu.com.
> 2) If the downloadable ISO has not been updated since Oct '09, is there a way of making a LiveCD/bootable USB that has up-to-date updates already installed? (if you know what I mean?) ....and is this process relatively simple?
Yes, the way I do it is to keep a copy of my own /var/cache/apt/archives in a directory in a USB stick. 
The .deb files in /var/cache/apt/archives contain all the updates and all my added software too. 
When I install another Ubuntu that's the same version for a friend, regardless of whether I use a CD to install with or a USB stick, I run a script for copying all the .deb files from the USB to the new installation's /var/cache/apt/archives right away as soon as the installation is finished.
The script then tells the new operating system to get updates from the internet if any are available, and then copies the whole lot back to the USB stick together with any new updates. That's very fast and saves a lot of internet bandwidth too.

---

### Post by .nedberg on 2010-01-03
> **ublondie said:**
> 

2) If the downloadable ISO has not been updated since Oct '09, is there a way of making a LiveCD/bootable USB that has up-to-date updates already installed?   (if you know what I mean?)   ....and is this process relatively simple?


I think you can use [remastersys]("http://geekconnection.org/remastersys/remastersystool.html") to do this. It should be relatively simple, but I have never done it so I don't actually know :).

---

### Post by ublondie on 2010-01-03
Thanks guys. The first idea sounds a bit beyond me to be honest and I also don't have an existing Ubuntu install, so I'll be making the LiveCD/USB from Windows. ...hence I won't have an existing archive of updates anywhere.

I'll have a look at the 'remastersys' ...thanks.

---

### Post by .nedberg on 2010-01-03
> **ublondie said:**
> Thanks guys. The first idea sounds a bit beyond me to be honest and I also don't have an existing Ubuntu install, so I'll be making the LiveCD/USB from Windows. ...hence I won't have an existing archive of updates anywhere.

I'll have a look at the 'remastersys' ...thanks.

Remastersys also uses an existing install of Ubuntu...

---

### Post by ublondie on 2010-01-03
Thanks, I just saw.

I did find this page:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

...but not sure if what I want to do is possible from outside the Ubuntu operating system (ie. from Windows)  ...{sigh}!  :(

---

### Post by .nedberg on 2010-01-03
Well, you could install Ubuntu in a virtual machine.

Have a look at VirtualBox ([www.virtualbox.org](www.virtualbox.org)). It is easy to use and you can use snapshots to "undo" errors along the way. A great way to experiment with Ubuntu or any other OS.

---

### Post by ublondie on 2010-01-03
Thanks for the info.

I had been using Ubuntu for a while and had 9.10 running ...that was until my laptop ended up with hardware failure with the video card and I haven't replaced (or repaired) it since. Now I'm using other people's machines which are of course invariably Windows.

I want to make up a fresh bootable USB memory stick with Ubuntu, but don't want to have to go through the tedious process of the 200Meg+ updates that are going to have to be installed. But it looks like there is no other way around for the time being.

Never mind ....nice thought. :)

PS. ...og jeg ka se du er Norsk. Så jeg går ud fra du har masser af sne hvor du er? ...godt nytår.  ;)

---

### Post by .nedberg on 2010-01-03
> **ublondie said:**
> 

PS. ...og jeg ka se du er Norsk. Så jeg går ud fra du har masser af sne hvor du er? ...godt nytår.  ;)

Ja, snø i massevis! Og -20°C...

Just to keep your head up: Virtualbox can be run from a USB, no need to install on a machine. If you also keep a Ubuntu install on a USB-drive you will have what you want, and don't even need to reboot the computer!

---

### Post by spcwingo on 2010-01-03
They used to do that.  I think they stopped after Hardy.  If you want an updated Hardy live-cd, here's a link:

[http://cdimage.ubuntu.com/hardy/daily-live/current/]("http://cdimage.ubuntu.com/hardy/daily-live/current/")

I hope this helps.

---

