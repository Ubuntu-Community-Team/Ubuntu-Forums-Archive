---
title: ":-( Upgrade w/ nVidia : more a story than a help req."
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-10-26
After having tried a bunch of distro, I finally decided to get back  to Ubuntu, mainly because od the out-of-the-box usability: As many of those who like to experiment with their computers, I often srew the OS up, so using a distro that won't require too much post-install work sounded like a good idea, I already knew Ubuntu, and I basically think of it like a working version of Debian.

With my usual luck I decided to install Dapper just a couple of days before Edgy came along, so I tried to upgrade, but that failed because of the nVidia drivers: My box is an AMD Duron 1600 with 1GB of ram and a 64MB video ram nVidia GeForce4 MMX, I didn't install the nVidia proprietary drivers as I don't need 3D acceleration on Linux (I play only one game, and that won't run properly on wine) so I kept the driver that the system choose, probably 'nv', as it does 1280x1024 and I don't need anything else.
Then the upgrade.

I did it like this: First I edited sources.list ```
 gedit /etc/apt/sources.list [code]and changed all the 'dapper' with 'edgy'; then I switched to root and did[code] apt-get update
apt-get upgrade.

```
After rebooting, the OS still looked like Dapper (I didn't know what Edgy should look like but I assumed that it couldn't be just like Dapper). I also got a warning pop-up about Nautilus quitting unexpectedly.
No matter how many times I tried to close that message window, it would always pop up again in a couple of seconds, both by hitting 'restart app' or 'close'.

Besides, the upgrade time had been way too short.
And it looked like Dapper.
So I thought OK, let's try something moer radical: I did ```
apt-get  update 
```again, just in case, checked that there were no errors, then I did ```
apt-get dist-upgrade 
```
That took the time that it should take, all went fine until almost the end, when I got an error about a gtk theme, which I uninstalled and then re-run dist-upgrade, this time it exited with no errors. Reboot.

The X server was crewed up. No X at all. I don't remember the exact message text, but I had seen that error before, that's about video drivers.
So I booted windows (yeah, I could say that I used a liveCD, but I actually used windows) and I got the proprietary driver from [www.nvidia.com](www.nvidia.com), then I restarted and tried to install them but I couldn't, I got errors no matter what kernel I booted.

Eventually I decided to clean install: I know that it's probably a 'fixable' problem but that's also a good excuse for a clean install, and I tend to prefer clean installs over upgrades, tho many ppl say trhat it's exactly the same... and why shouldn't it, anyway?

My new Edgy CD is done now, I was writing while I waited for it, so now I can start my clean install, and now you know that you may run in some problems if you have nVidia and want to upgrade from Dapper to Edgy, so prepare for it and know what to do *before* you upgrade (use google, ask question here, etc)
Or do a clean install directly.:(

---

