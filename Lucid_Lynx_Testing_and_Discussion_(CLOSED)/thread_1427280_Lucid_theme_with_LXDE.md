---
title: "Lucid theme with LXDE"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MonsterTrimble on 2010-03-11
Hi all!

Last weekend I picked up my first laptop - 1.3 Ghz, 512 MB RAM, 40 GB HD. Nothing fancy. I also have been playing around with LXDE on my desktop (as a replacement for KDE) and liked it, so I installed LXDE from the repos onto the laptop. I saw the new artwork, log-in and menu from Lucid Alpha 3 and love them. BUT I can't seem to get them to come up on my laptop. What do I have to install to have the new artwork? I have already upgraded to Lucid on it.

Thanks!

---

### Post by ranch hand on 2010-03-11
If you like Lxde, I do, you really ought to try Lubuntu 10.04.  The boot is different, as is the artwork, but you may like it a lot.  On that 40Gb HDD it will save you quite a chunk of space even if you install a bunch of bid stuff like Gimp on it.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by phillw on 2010-03-11
Hi

'Buntu + lxde = lubuntu

Head over to [https://wiki.ubuntu.com/Lubuntu/](https://wiki.ubuntu.com/Lubuntu/)  for details.

hope to see you on irc channel #lubuntu :D

Regards,

Phill.

---

### Post by MonsterTrimble on 2010-03-11
I actually did do the full Lubuntu install initially but I did not like the large number of Gnome apps which came with it. What i ended up doing is reformatting the machine and installing the command-line ubuntu, then added the LXDE package on top of it from the repos plus Opera, Pidgin & Thunderbird. I am trying to be uber minimalist with apps on this machine and I found when I had Lubuntu on it and trying to uninstall the apps I didn't want led to it wanting to uninstall Lubuntu.

---

### Post by uRock on 2010-03-11
Being Lubuntu isn't supported by Canonical it may take a while to get the new artwork. I installed it via synaptic and it works fine. The Lubuntu website only has Beta versions.

---

### Post by phillw on 2010-03-11
> **iRock said:**
> Being Lubuntu isn't supported by Canonical it may take a while to get the new artwork. I installed it via synaptic and it works fine. The Lubuntu website only has Beta versions.
The plan is for Lubuntu to become a full member of the Canonical family with 10.04, so far that schedule is on target. The Lubuntu team is a small team, so don't expect Daily Builds. The new artwork is currently being discussed, as you will recall, the announcement was quite recent !

If you're interested in where things are headed, you can join the mailing list via the wiki page in my earlier posting and catch up with previous IRC Meetings from there as well. :p

Regards,

Phill.

---

### Post by uRock on 2010-03-11
> **phillw said:**
> The plan is for Lubuntu to become a full member of the Canonical family with 10.04, so far that schedule is on target. The Lubuntu team is a small team, so don't expect Daily Builds. The new artwork is currently being discussed, as you will recall, the announcement was quite recent !

If you're interested in where things are headed, you can join the mailing list via the wiki page in my earlier posting and catch up with previous IRC Meetings from there as well. :p

Regards,

Phill.

That is awesome news. I hadn't noticed they were going to start supporting it. I use it on my netbook and it is awesome.

Thanks for straightening me out, I'll have to get involved in the testing for it.

---

### Post by ranch hand on 2010-03-11
> **iRock said:**
> That is awesome news. I hadn't noticed they were going to start supporting it. I use it on my netbook and it is awesome.

Thanks for straightening me out, I'll have to get involved in the testing for it.
It boots better than Ubuntu right now.  This of coarse may change.

Because it is still kind of on its own the alpha an beta releases will not be a simple snapshot but can be quite different.

I have 2 installs, 1 is A2 (updated daily), 1 is A3 (like wise updated).  They are both working great.

---

### Post by phillw on 2010-03-11
> **ranch hand said:**
> 
Because it is still kind of on its own the alpha an beta releases will not be a simple snapshot but can be quite different.

I have 2 installs, 1 is A2 (updated daily), 1 is A3 (like wise updated).  They are both working great.



@Ranch hand, have you got the lubuntu ppa added for your daily builds ?

```

sudo add-apt-repository ppa:lubuntu-desktop/ppa
```I was advised to then use

```

 sudo apt-get update
 sudo apt-get dist-upgrade

```To pull in all updates.

And, yeah, it's running really nicely :p

Regards,

Phill.

---

### Post by ranch hand on 2010-03-11
> **phillw said:**
> @Ranch hand, have you got the lubuntu ppa added for your daily builds ?

```

sudo add-apt-repository ppa:lubuntu-desktop/ppa
```I was advised to then use

```

 sudo apt-get update
 sudo apt-get dist-upgrade

```To pull in all updates.

And, yeah, it's running really nicely :p

Regards,

Phill.
No I do not.  I am thinking of putting it on the A3 install and leaving the A2 to just the repo installs so that they stay separate and just to see the difference.

Haven't had much time to fool with it with the problems in 10.04, mainly in trying the 8.04>10.04 upgrade.  I have that working pretty well but folks keep insisting that upgrading is the best way to go (stick with old grub and ext3).  Object to that and say a clean install and transfer files is better and you get told that you can change to ext4 on the fly (worked but results are inferior to transfered files).

I also have my 8.04 install on one partition.  So just make a second /home.  Did that yesterday and haven't gotten it to run right yet.

It is easier and faster to do this the clean install way but I guess more macho to upgrade.

Being in the ranching profession, I can deal with macho.  I can't deal with doing things the hard way to consider your self macho.  That is not macho.  It is silly.

I think I will add that ppa today and forget fooling with the other until another day.

---

### Post by MonsterTrimble on 2010-03-11
OK, so back to my original question: How do I get the new artwork to work on the base lxde package from the ubuntu repos?

---

### Post by ranch hand on 2010-03-11
I would go to the package page and download the debs from there and install them.

---

### Post by phillw on 2010-03-11
> **MonsterTrimble said:**
> OK, so back to my original question: How do I get the new artwork to work on the base lxde package from the ubuntu repos?

Okies, as you now know that Lubuntu is yet not fully adopted by Canonical ...

Get the Lubuntu a3 iso and pop it onto a 5GB area of your 40GB Hard Drive.
Else you can run it via a USB-Stick, but I found that kernel updates killed my USB version and it is not a target market for Lubuntu.

Lubuntu will, of course, happily live in a lot less than that, possibly breaching the 2.5GB hell threshold. But I'd say give it 5GB, Lubuntu needs very little, but a few (hundred) songs and the odd video clip will eat up disk space !!

Once you have it installed, put on the ppa for lubuntu-desktop as per post #9

Do the updates, as per that post.

You will then have the draft artwork (as I said before, not yet finalised) but also you will get the work that has been done for file-manager (such as seeing hard disk partitions, usb sticks, etc).

Lubuntu, at its core is full on 10.04, so there are updates from 10.04 that apply to Lubuntu. The Lubuntu ppa is for updates of things specifically for lubuntu.

Regards,

Phill.

---

### Post by seeker5528 on 2010-03-11
> **MonsterTrimble said:**
> OK, so back to my original question: How do I get the new artwork to work on the base lxde package from the ubuntu repos?

If you want to try to get the artwork while keeping other stuff to a minimum, you probably want to start with the packages:

lubuntu-artwork
lubuntu-plymouth-theme
lubuntu-default-settings

I didn't add any PPAs to get these things, but if they are not from the PPA they may not be the most current art work.

Later, Seeker

---

### Post by MonsterTrimble on 2010-03-15
> **phillw said:**
> You will then have the draft artwork (as I said before, not yet finalised) but also you will get the work that has been done for file-manager (such as seeing hard disk partitions, usb sticks, etc).

Phill - Thank you for the advice. I have not done it as yet (due to my weekend being completely full and hardcoding in the USB to fstab. Not my favorite job, but a necessary one with PCMan at 0.5.x as it is. 

> **seeker5528 said:**
> If you want to try to get the artwork while keeping other stuff to a minimum, you probably want to start with the packages:

lubuntu-artwork
lubuntu-plymouth-theme
lubuntu-default-settings

I didn't add any PPAs to get these things, but if they are not from the PPA they may not be the most current art work.

Seeker - I did the artwork & plymouth from the standard repos however trying to install the Lubuntu-default-settings makes the system want to uninstall the lxde packages, which is kinda needed me thinks! However, I did play with the icon sets afterwards and everything is a lot nicer. 

At this point, I have three things which I need to get sewn up before I'm in love (and kicking Kubuntu to the curb):

1) Network Browsing - From all accounts PCManFM2 takes care of that and the aforementioned USB.
2) Boot Times - On Saturday I noticed the loading screen reverted to a weird purple screenwhich said 'Ubuntu 10.04' with found small boxes below it. It also takes a tremendous amount of time to load (on the order of five or ten minutes if it loads at all). I did install pmount around the same time although I haven't investigated the root cause yet.
3) Slideshow background - It's a small quibble but I love it in KDE4. I assume it's been done for LXDE but I haven't looked for it as yet.

---

### Post by ranch hand on 2010-03-15
If you are using Lxde from the Ubuntu repo on an Ubuntu or Kubuntu install I would wipe the bugger and go to Lubuntu.

Runs better than the minimal install I did with Lxde or the Ubuntu install with Lxde.  Actually boots right with plymouth even.

---

### Post by seeker5528 on 2010-03-15
> **MonsterTrimble said:**
> Seeker - I did the artwork & plymouth from the standard repos however trying to install the Lubuntu-default-settings makes the system want to uninstall the lxde packages, which is kinda needed me thinks! However, I did play with the icon sets afterwards and everything is a lot nicer.

If you have lxde-settings-daemon install, you might try installing lxsession. I started with a Karmic minimal install, added the lxde stuff, upgraded to Lucid, then I when I wasn't getting everything as I expected I poked around and added the Lubuntu stuff. Lxsession replaced lxde-settings-daemon, but there may be some dependency stuff that is not all sorted out yet. Other than that I have everyting installed that comes up when you search in Synaptic for everything that has lxde in the description or name except for lib-menu-cache-dev. 

> At this point, I have three things which I need to get sewn up before I'm in love (and kicking Kubuntu to the curb):

1) Network Browsing - From all accounts PCManFM2 takes care of that and the aforementioned USB.

My installation has PyNeighborhood installed, which seems to work, at least I can see the shares on the network, didn't try to mount any to see where they get mounted. 

2) Boot Times - On Saturday I noticed the loading screen reverted to a weird purple screenwhich said 'Ubuntu 10.04' with found small boxes below it. It also takes a tremendous amount of time to load (on the order of five or ten minutes if it loads at all).[/quote]

I get reasonably quick boot times, if you get the lubuntu-default-settings installed, it should get you set up for the Lubuntu-plymouth stuff during the boot. But that may not make a difference on the speed, there may be something with the recent kernel update in regard to the video driver you are using.

> I did install pmount around the same time although I haven't investigated the root cause yet.

Pmount is for USB stuff, which there seems to be a lot of issues with at the moment. Not desktop specific. Haven't tried with KDE, but I haven't been able to get any of my USB stuff to mount automatically in Gnome, there was a thread about it that had some solutions that seemed to work for some people.

> 3) Slideshow background - It's a small quibble but I love it in KDE4. I assume it's been done for LXDE but I haven't looked for it as yet.

I haven't looked for anything like that recently. The stuff I used to use to change the wallpaper on a timed interval was dropped from Debian some time ago, don't know if it was ever in Ubuntu. If you don't mind adding QT stuff to the mix, I see a package named wally that looks promising based on the description that shows in Synaptic. 

EDIT: Haven't taken the time to fully investigate Wally, but it runs in the tray so should be good in any desktop, just have to add it to the start up applications. Which in LXDE looks like you have to create a .desktop file in '~/.config/autostart' with contents similar to:

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/wally

```

The next time you log in it should start automatically.

Later, Seeker

---

### Post by MonsterTrimble on 2010-03-16
Ok, first off I installed PCManFM2 (0.9.x) from the nightly build repos given in Post #9 and frankly, it's not ready for primetime as yet. I found the background and all my LXPanel settings gone and no real way to get them back. As well, USB access was totally denied as was the local network, although the network I chalk up to a poorly set-up Samba. (Goal for tonite - fix smb.conf)

Plymouth started causing some major headaches in the log-in department, which from all accounts is the norm. A quick apt-get remove plymouth fixed that situation. I still have to have a USB drive plugged into my computer for the log-in which I will hopefully address tonite (Goal #2).

> **seeker5528 said:**
> My installation has PyNeighborhood installed, which seems to work, at least I can see the shares on the network, didn't try to mount any to see where they get mounted. 

I looked briefly at that too, but until I get my smb.conf fixed I'm not going to bother.

> **seeker5528 said:**
> I haven't looked for anything like that recently. The stuff I used to use to change the wallpaper on a timed interval was dropped from Debian some time ago, don't know if it was ever in Ubuntu. If you don't mind adding QT stuff to the mix, I see a package named wally that looks promising based on the description that shows in Synaptic. 

EDIT: Haven't taken the time to fully investigate Wally, but it runs in the tray so should be good in any desktop, just have to add it to the start up applications. Which in LXDE looks like you have to create a .desktop file in '~/.config/autostart' with contents similar to:

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/wally

```

The next time you log in it should start automatically.

I have no problem mixing in KDE items - in fact, my desktop system runs KDE4.4 - but I have a serious issue with the Akanodi server neding to be installed with EVERYTHING. I don't quite understand why Amarok & Dolphin need it, they both ran fine (Or better) before without it. Anyway, I will take a look at Wally.

And by the way, thanks for all the help. It's really appreciated. I owe you a coke. :)

---

### Post by phillw on 2010-03-16
> **MonsterTrimble said:**
> Ok, first off I installed PCManFM2 (0.9.x) from the nightly build repos given in Post #9 and frankly, it's not ready for primetime as yet. I found the background and all my LXPanel settings gone and no real way to get them back. As well, USB access was totally denied as was the local network, although the network I chalk up to a poorly set-up Samba. (Goal for tonite - fix smb.conf)


PCManFM2 gets builds, via the ppa - Yes, it's still a bit rough round the edges, but I have no problems with usb sticks. There is a new version for the beta1 release, which links to Xarchiver.

> Plymouth started causing some major headaches in the log-in department, which from all accounts is the norm. A quick apt-get remove plymouth fixed that situation.

Well, things are moving..
> I added support for lxdm, a new display manager, in the plymouth package. Change are available in the branch from 3 days ago

and
> LXDM almost certainly needs modifying still; which sequence do you use
for transition at this point?

** Changed in: plymouth (Ubuntu)
      Status: Triaged => Fix Committed From an hour ago (time / date to this edit)


I've had a quick 'play' with pyneighborhood but not got too far with it, I've been trying with these instructions --> [http://www.freesoftwaremagazine.com/articles/connecting_linux_to_windows_servers_using_pyneighborhood](http://www.freesoftwaremagazine.com/articles/connecting_linux_to_windows_servers_using_pyneighborhood)   but cannot get it 'see' the windows machine at all. If you know of a newer set of instructions, I'd be grateful.

Regards,

Phill.

---

### Post by MonsterTrimble on 2010-03-19
I have a confession to make, after two reformats trying to get the screen back to 1024 x 768 I have stayed on 9.10 and probably will until May or June just so the bugs can be hammered out a bit more. I can deal with almost anything but the 800 x 600 was the deal breaker for going to Beta.

> **phillw said:**
> I've had a quick 'play' with pyneighborhood but not got too far with it, I've been trying with these instructions --> [http://www.freesoftwaremagazine.com/articles/connecting_linux_to_windows_servers_using_pyneighborhood](http://www.freesoftwaremagazine.com/articles/connecting_linux_to_windows_servers_using_pyneighborhood)   but cannot get it 'see' the windows machine at all. If you know of a newer set of instructions, I'd be grateful.

I hope to take a swipe at it this weekend. When & if I get it sorted out I'll post here.

---

### Post by phillw on 2010-03-19
> **MonsterTrimble said:**
> I have a confession to make, after two reformats trying to get the screen back to 1024 x 768 I have stayed on 9.10 and probably will until May or June just so the bugs can be hammered out a bit more. I can deal with almost anything but the 800 x 600 was the deal breaker for going to Beta.

I hope to take a swipe at it this weekend. When & if I get it sorted out I'll post here.

My native intel graphics on my laptop have never had a problem with video resolution; cheap and cheerful. I do understand that there are issues for some nvidia and ati.

Be aware that there is a bug lurking that affects pyneighborhood (and nautilus, and pcmanfm), if your CPU usage hurtles to about 100% and you get an error with "org.freedesktop.DBus.Error.NoReply", you'd best head over to [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024) and tick the 'affects me box'. There is a thread on the forum about it over here --> [http://ubuntuforums.org/showthread.php?t=1426517](http://ubuntuforums.org/showthread.php?t=1426517)

Do post how you get on, 

Thanks,

Phill.

---

### Post by MonsterTrimble on 2010-03-26
Sorry about not getting back to you sooner - life gets in the way of everything dontcha know!

I tried doing the setup of the pyNeighborhood and it failed miserably. Something very strange going on there, and frankly, I can hobble along for a few weeks until Lucid RC hits and I get PCManFM2. 

My only real worry is that Lucid won't like my trident video card. The previous install with 10.04 wouldn't let me get anywhere near 1024x768. Max was 800x600 and none of the tricks I found worked. My hope is that the RC will eliminate that problem.

---

