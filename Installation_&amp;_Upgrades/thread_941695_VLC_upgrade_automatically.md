---
title: "VLC upgrade automatically"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by mercury80 on 2008-10-08
I have VLC media player 0.8.6e Janus (wxWidgets interface) on Ubuntu 8.04. There is a new version of VLC (0.9.4) available. Will this upgrade eventually come with all the other upgrades i get automatically with Ubuntu? Or do i have to upgrade this manually? I did get several upgrades of VLC through the Ubuntu-update system a few days ago. But i was disappointed to see that it did not include the VLC v0.9 edition...

I did manually upgrade Delube (bittorrent program) from the "one-click-install" system that comes with Ubuntu cause it was an old edition... This will not cos any problems down the line will it?


---------
VLC media player 0.8.6e Janus (wxWidgets interface)
Compiled by [email]buildd@terranova.buil[/email]dd.
Compiler: gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7).

---------
Ubuntu 8.04 (Hardy) x86
Kernel Linux 2.6.24-16-generic
Gnome 2.22.3

---

### Post by mihaiv on 2008-10-08
It is unlikely to get any major version upgrade in ubuntu 8.04. You will eventually get the 0.9 series of vlc with the upgrade to intrepid ibex.

---

### Post by DJ_Peng on 2008-10-08
Christoph Korn has made the newest version of VLC is his PPA (Personal Package Archive). The Tombuntu website has [instructions for using it to get VLC 0.9.4]("http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/") (even though his tutorial says 0.9.2, since Christoph has updated the package).

---

### Post by cariboo on 2008-10-08
VLC 0.9.3 is installed by default in Intrepid, which will be available at the end of the month.

Jim

---

### Post by mess_enger_guy on 2008-10-10
> **DJ_Peng said:**
> Christoph Korn has made the newest version of VLC is his PPA (Personal Package Archive). The Tombuntu website has [instructions for using it to get VLC 0.9.4]("http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/") (even though his tutorial says 0.9.2, since Christoph has updated the package).

Hello friends, I wanted to upgrade my vlc player to 0.9.x so I added the repository provided by Mr. Korn and installed the latest vlc. After upgrading I am not able to see any videos, though I can hear the audio. When I play any video I get the following on the terminal:

[00000456] main video output error: no video filter module matched "adjust"
[00000456] main video output error: no suitable vout module
[00000444] main decoder error: failed to create video output

If I switch back to the older version 0.8.6 provided by ubuntu repository everything comes back to normal. Anybody has a solution for this problem?

---

### Post by slumbergod on 2008-10-10
I was happily using vlc 0.9.3 but I was stupid enough to let it upgrade to 0.9.4 from the Korn repo. After that I no longer had my video window embedded in the main interface. Turns out there was a bug so they disabled it until it is fixed. 

I went to downgrade back to 0.9.3 but unfortunately, I had cleaned out my stored debs and the Korn repo doesn't appear to have 0.9.3.

So, it looks like either the ikky 0.8.x or the not-quite-there 0.9.4

---

### Post by DJ_Peng on 2008-10-11
I trust a bug has been filed about the video issue. That way we can make sure Christoph knows it's happening and he can try to get it fixed.

---

### Post by darco on 2008-10-11
Is this bug you speak of also prevents us from playing .img files? I have 0.9.4 and can longer play these files but I also noticed that .img does not appear in the drop down filter when you chose to open a file in vlc.

darco

---

### Post by mess_enger_guy on 2008-10-11
> **slumbergod said:**
> I was happily using vlc 0.9.3 but I was stupid enough to let it upgrade to 0.9.4 from the Korn repo. After that I no longer had my video window embedded in the main interface. Turns out there was a bug so they disabled it until it is fixed. 

I went to downgrade back to 0.9.3 but unfortunately, I had cleaned out my stored debs and the Korn repo doesn't appear to have 0.9.3.

So, it looks like either the ikky 0.8.x or the not-quite-there 0.9.4

If I am not mistaken your problem seems to be different than mine. You don't see your video embedded in the main interface whereas I don't see any video at all. Is my problem also going to be fixed when the bug is solved? Please correct me if I am wrong...

---

### Post by mc4man on 2008-10-11
Vlc 0.9.x uses a different config. file so maybe next time go into settings and try adjusting the video output module. (audio also
0.9.x stores settings in home dir. -> .config/vlc
0.8.6 stores in home dir. -> .vlc

I wouldn't bother with 0.9.4 till it's fixed.

What you can do (on hardy) is reinstall 0.8.6, get it running right, then build 0.9.3 but don't install it. It can be run directly from the build folder (self contained, won't conflict with 0.8.6

You can make a desktop launcher for it or even set it up as a default autorun choice for dvds. (which also makes it available from the r. click open with menu.
Actually pretty easy to do, takes about a half hour or so

---

### Post by mess_enger_guy on 2008-10-12
> **mc4man said:**
> Vlc 0.9.x uses a different config. file so maybe next time go into settings and try adjusting the video output module. (audio also
0.9.x stores settings in home dir. -> .config/vlc
0.8.6 stores in home dir. -> .vlc

I wouldn't bother with 0.9.4 till it's fixed.

What you can do (on hardy) is reinstall 0.8.6, get it running right, then build 0.9.3 but don't install it. It can be run directly from the build folder (self contained, won't conflict with 0.8.6

You can make a desktop launcher for it or even set it up as a default autorun choice for dvds. (which also makes it available from the r. click open with menu.
Actually pretty easy to do, takes about a half hour or so

Should I really go through the hassle of satisfying dependencies and installing all the dev packages for compiling vlc or should I just wait for the Intrepid release?

---

### Post by DJ_Peng on 2008-10-12
> **mess_enger_guy said:**
> If I am not mistaken your problem seems to be different than mine. You don't see your video embedded in the main interface whereas I don't see any video at all. Is my problem also going to be fixed when the bug is solved? Please correct me if I am wrong...
It definitely sounds like there are two different issues involved. I'd check Launchpad to see if there's a bug for your issue, and if not file your own. If the devs feel it's the same issue they'll take the appropriate steps. You can also subscribe to the existing bug so you can see how they're progressing on resolving it.

> **mess_enger_guy said:**
> Should I really go through the hassle of satisfying dependencies and installing all the dev packages for compiling vlc or should I just wait for the Intrepid release?
If you're happy with the current VLC I'd say hold off to upgrade until Intrepid comes out. It's only another 18 days or so, so it's not like you'd have to wait several months. Granted, the current testing version may not make Intrepid (I haven't looked at which version will be included) but I always recommend staying with what you have if getting the new version either comes with a number of hoops to jump through or isn't a big enough change to make it worth your time and effort.

---

### Post by mess_enger_guy on 2008-10-12
> **DJ_Peng said:**
> It definitely sounds like there are two different issues involved. I'd check Launchpad to see if there's a bug for your issue, and if not file your own. If the devs feel it's the same issue they'll take the appropriate steps. You can also subscribe to the existing bug so you can see how they're progressing on resolving it.


If you're happy with the current VLC I'd say hold off to upgrade until Intrepid comes out. It's only another 18 days or so, so it's not like you'd have to wait several months. Granted, the current testing version may not make Intrepid (I haven't looked at which version will be included) but I always recommend staying with what you have if getting the new version either comes with a number of hoops to jump through or isn't a big enough change to make it worth your time and effort.

Thanks DJ_Peng for answering both my questions. I guess I'll just wait till Intrepid comes out. I can survive with the older vlc for few days.

---

### Post by DJ_Peng on 2008-10-14
Glad I could help. If you could click the Thanks icon (on the far right) on the post that helped I'd appreciate it.

---

### Post by WolfWitch on 2008-10-24
I had the same problem, and was frustrated with a lack of information I was able to find about it. I did finally find this, which fixed the problem:

[http://forum.videolan.org/viewtopic.php?f=14&t=51333](http://forum.videolan.org/viewtopic.php?f=14&t=51333)

I just went into Tools|Preferences and hit the big [Reset Preferences] button. I don't know how to clear the cache (per the VideoLan suggestion), but just resetting the preferences and restarting the video I was currently trying to watch fixed it.

---

### Post by mess_enger_guy on 2008-10-25
> **WolfWitch said:**
> I had the same problem, and was frustrated with a lack of information I was able to find about it. I did finally find this, which fixed the problem:

[http://forum.videolan.org/viewtopic.php?f=14&t=51333](http://forum.videolan.org/viewtopic.php?f=14&t=51333)

I just went into Tools|Preferences and hit the big [Reset Preferences] button. I don't know how to clear the cache (per the VideoLan suggestion), but just resetting the preferences and restarting the video I was currently trying to watch fixed it.

Can't believe the solution to the problem I've stated would've been so simple. Just resetting the Preferences fixes the problem of video not showing up. Thanks a lot WolfWitch.

---

