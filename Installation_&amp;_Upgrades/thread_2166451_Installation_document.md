---
title: "Installation document"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2013-08-09
Hi all,
I am about to help someone install 12.04 but as he lives in Canada and I am in Scotland timezones can be a problem so I thought i would just review some of the documents and came across this:
[https://help.ubuntu.com/lts/installation-guide/i386/howto-installation.html](https://help.ubuntu.com/lts/installation-guide/i386/howto-installation.html)

Well I have installed 12.04 on my own and my wife's laptops and I am sure I am confused because most of what the document says about 
a minimal base system and extra packages is not my experience.

However I always do a manual partitioning with /, swap and /home so I am now thinking this may be the reason for the difference.

I was trying to find out specifically what partitioning the automatic install would choose as, if it's simply / and swap then I will talk him through doing it the way I usually do as i have done it that way since around 6.04. The reason I have done it that way is because although each time I try an upgrade it has messed up so I then just do it manually, choose the same user name and don't format /home

Also the document talks about setting the password for root But I don't think that's correct is it?
Can anyone enlighten me please?

---

### Post by bapoumba on 2013-08-09
[https://help.ubuntu.com/12.04/installation-guide/i386/index.html](https://help.ubuntu.com/12.04/installation-guide/i386/index.html)
I navigated back up from the link you provided and down again, the url looks a little different and the info has changed a little.

I also always set up a separate /home as you do, with additional /storage partition(s) depending on the drive size.

---

### Post by linuxonbute on 2013-08-09
Thanks [COLOR=#000000]bapoumba, 
I did what you did but I ended up at the same page which does not seem to have changed.
I have installed ubuntu many times and it has never, ever asked me to set up root's password. I am sure the default is not to set one up or allow a user to log in as root unless the first user set up uses sudo to set one up for root. Nor have I seen the other bit about choosing other software apart for non free stuff.
I still cannot find for certain what configuration ubuntu uses for partitions as a default.
Correction I have now found it's / and swap.
I'll open a new thread now[/COLOR]

---

### Post by bapoumba on 2013-08-09
Well, I looked more carefully, even at the 13.04 doc page, and it seems indeed a little outdated or even from older debian install pages.

1- the first user created during an install will be able to have root privileges, using sudo/gksudo (or pkexec that I have yet to go around using). So no need to activate a root account. See here : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
2- to custom partition the drive during the install process, choose "Something else", here is a screen capture of what it looks like : [https://help.ubuntu.com/community/GraphicalInstall#Installation_type](https://help.ubuntu.com/community/GraphicalInstall#Installation_type) with additional info here : [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

As default and if you choose to erase the disk or install next to another OS, I *think* there will not be a separate /home (to be confirmed). I've never done it myself, always keep a separate /home and other storage partitions, so I always use a manual partitioning.

There is no time stamp on the doc page you linked to. So I'm not sure when it was last updated.

---

### Post by linuxonbute on 2013-08-09
Yes I agree with your comments but the problem is I want the install on a laptop in Vancouver area and live on Bute an island off the west coast of Scotland.
The person who's laptop it is knows nothing about Linux and has a very messed up copy on the laptop.I believe that if /home was on it's own partition it would be safer for him. 
I have opened a new thread about hacking a standard iso. 
If it can be made to default to /, swap and /home I could just send him the disc and he could install it without any bother really and /home would be protected if I needed to talk him through an install later when he might have more confidence.

---

### Post by bapoumba on 2013-08-09
OK, I do not know how easily that could be done (making your own ISO). I'd say that if they have another computer or a phone, something like a hangout could be more effective :)

---

### Post by linuxonbute on 2013-08-09
He does have another laptop but with the 8 hour difference it's not easy to find a time of day when we can both have enough time to get it done:rolleyes:

---

### Post by bapoumba on 2013-08-09
> **linuxonbute said:**
> He does have another laptop but with the 8 hour difference it's not easy to find a time of day when we can both have enough time to get it done:rolleyes:

Yeah, but that is just a matter of a few minutes once he gets to the screen. Evening for you is morning for him, say next Sunday ? :tongue:
I'm kidding you, but it may be the easiest way.

---

### Post by linuxonbute on 2013-08-09
Just come across this thread so it might not be so bad. just a steep learning curve to figure out how to edit the default cofig to partition the disc:)

[http://ubuntuforums.org/showthread.php?t=1874634](http://ubuntuforums.org/showthread.php?t=1874634)

---

### Post by bapoumba on 2013-08-09
Cool :)
Just had a look, the remastersys project has been stopped. Guess you'll have to go with [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by linuxonbute on 2013-08-09
Great. it would take some time to go through all of this but that's no problem. A quick look didn't seem to show what I need to do to get the default config for partitions changed but if I can find that it will probably be all I need in this instance. Looks worth exploring for some other projects though.
Thanks

---

### Post by bapoumba on 2013-08-09
I'm no expert on these questions at all, but if you can learn in the process, that might be worth a try. I did not see either how to configure the partition setup, but I did not read very carefully.

---

### Post by linuxonbute on 2013-08-09
At present it looks like it's ubiquity which is apparently 'a mainly python script' to install a live distribution! had a look at a few files but not found anything specific yet so I may have a look at my live disc and see if I can find anything there. Anyway up early tomorrow to catch a boat to the mainland so I will maybe look tomorrow night.

---

### Post by bapoumba on 2013-08-10
Have an nice trip, and please share your findings on the Live CD :)

---

