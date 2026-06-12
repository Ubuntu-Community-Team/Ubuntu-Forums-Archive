---
title: "Failed upgrade to 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by jacob-heller on 2011-05-05
I wanted to upgrade to 11.04 from 10.10, and I (naively) pressed the "update" button. In the middle of the upgrade, I got an error (I can't replicate it now, unfortunately) and the upgrade stopped. Now I think I'm still in 10.10 -- at least, everything looks and feels 10.10 -- and when I go to the upgrade program, although I no longer have the option to press the "upgrade to 11.04" button, I do get an error that reads "Not all upgrades can be installed" and it wants to install a ton of upgrades.

So... what the heck happened? How can I fix it? Might this have anything to do with the fact that I'm using a proprietary Nvidia video driver -- and if so, what? and how can I fix it?

Thanks all -- and I apologize for the definite noob question...

Jake

---

### Post by luckyu on 2011-05-06
I think your update has failed and causing your computer to think that it has done updating when in actuality it hasn't. 

So lets see if this problem is fixable ...
go into terminal and type in these command and post the outputs
```

cat /etc/lsb-release

``` 
```

sudo apt-get update
sudo apt-get upgrade

```

Also as a side, over time I have learned that it is always better to do a fresh install of the latest Ubuntu rather then updating via the internet.

---

### Post by jacob-heller on 2011-05-06
So this didn't go that well for me.

It looks like you were right that it thought it upgraded to 11.04:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

apt-get update spit out something rather long:
```
Ign http://archive.canonical.com natty InRelease
Ign http://extras.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Hit http://archive.canonical.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Hit http://archive.canonical.com natty Release
Get:2 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]
Hit http://security.ubuntu.com natty-security Release
Hit http://extras.ubuntu.com natty Release
Hit http://us.archive.ubuntu.com natty Release
Hit http://archive.canonical.com natty/partner i386 Packages
Hit http://security.ubuntu.com natty-security/main Sources
Hit http://extras.ubuntu.com natty/main Sources
Get:3 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Get:4 http://us.archive.ubuntu.com natty-updates/main Sources [19.5 kB]
Get:5 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]
Get:6 http://us.archive.ubuntu.com natty-updates/universe Sources [5,310 B]
Get:7 http://us.archive.ubuntu.com natty-updates/multiverse Sources [14 B]
Get:8 http://us.archive.ubuntu.com natty-updates/main i386 Packages [75.6 kB]
Get:9 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:10 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [24.6 k                                             B]
Get:11 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [14 B                                             ]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 153 kB in 2s (56.0 kB/s)
Reading package lists... Done

```

And then apt-get upgrade went through a 10-minute process that looked like it worked just fine.

Now, after restarting (bad habit from Windows days), I can't reach the machine over the network (it's non-responsive when I ping it's IP address, etc.). I'll plug it into a monitor later, but I'm afraid it might be hanging at startup or something of the sort. I'll post again in some hours later to see what's happening.

Truth be told, I was perfectly happy with my 10.10 setup. While of course I'd rather have the newest goodies, I think the lesson I learned that upgrading is too much of a hassle with Ubuntu to make it worth the while... Fresh installs would probably be equally annoying, since I'd have to (a) figure out how to not lose all my data and (b) redownload and reconfigure all the software I downloaded -- most treacherously, my Samba network, which was a two-week-long bitch to get working. Blergh.

If anyone has any advice in the interim, let me know!

Jake

---

### Post by luckyu on 2011-05-06
Okay well I can tell you this, I has updated to Natty Narwhal and your software sources are fine. So after you typed in the upgrade command it should have upgraded everything. 
On the side note your IP address is not going to be the same because the update will change most if not all your configurations on your system.  

That is why when I do a update I just backup the data and do a fresh install, because the update will already pretty much change all the packages because that is what essentially happens when you update.


Pull out the dusty monitor and plug it in and login and find your ip address and go from there.
```
sudo ifconfig
```

---

### Post by jacob-heller on 2011-05-07
Thanks for your help so far -- but it turns out that the problem is that Ubuntu 11.04 is somehow not compatible with my proprietary nvidia drivers, and so the machine will hang on boot at the stage where it gets to the Ubuntu with the dots.

To be honest, I'd like to keep my proprietary drivers -- it's the only thing I could get to work with XBMC, which is really the main thing this computer is doing anyway. The only question is, is there a way to re-install Ubuntu 10.10 without losing all my data. I have 200+GB of data in my home folder, so burning it on to DVDs, etc., isn't an option; and I have no access to an external harddrive. 

I've read elsewhere that when you're installing Ubuntu, there is an option *not* to format your computer, but instead to keep the files in the /home folder. Is that actually true? 

Or is there some other solution I should be thinking of?

---

### Post by Dutch70 on 2011-05-07
Try nomodeset or other boot options.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, there is supposed to be a way to "renew" the installation without formatting, that doesn't affect your home directory, but very few people seem to know anything about it. 
Most of us use a separate /home partition for just this reason. Then we can fresh install without formatting the /home partition & keep our data & settings.

Edit: You may also want to try logging in to failsafe mode.

---

### Post by jacob-heller on 2011-05-07
Creating a separate /home partition sounds like a smart plan. How does one set that up? Is it remotely easy for a noob like me?

---

### Post by jacob-heller on 2011-05-07
For what it's worth for those people looking to downgrade like me, here's a helpful video that appears to show you how to do exactly what I'm looking to do. I'm going to try following his instructions--hopefully it'll work!

[http://www.youtube.com/watch?v=QGnsYuWS0xY](http://www.youtube.com/watch?v=QGnsYuWS0xY)

---

### Post by Dutch70 on 2011-05-07
These links are a little dated, so you may want to use ext4 instead of ext 3 as the links advise.

This guide is for creating a separate /home partition if you already installed Ubuntu
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

Creating a separate home partition in Ubuntu during installation
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

---

