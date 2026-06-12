---
title: "will karmic have 64bit flash or.."
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by binskipy2u on 2009-10-23
will we have to jump thru hoops looking/googling for a how'to to install 64bit flash in ubuntu 64bit (mustve read 10 different sites/blogs, how to do this)?

it's apain to install 32bit this or that, and then find how to uninstall and install 64bit flash..

---

### Post by DougieFresh4U on 2009-10-23
> **binskipy2u said:**
> will we have to jump thru hoops looking/googling for a how'to to install 64bit flash in ubuntu 64bit (mustve read 10 different sites/blogs, how to do this)?

it's apain to install 32bit this or that, and then find how to uninstall and install 64bit flash..
I believe you will find all you need [here]("http://ubuntuforums.org/forumdisplay.php?f=343")

---

### Post by binskipy2u on 2009-10-24
i did look there ,thats where i found all the different ways.. scripts, etc..
will it be in the repos , the 64bit in the medibuntu repos? or will i have to look there and find one of the many that actually work ?

---

### Post by howefield on 2009-10-24
Couldn't be simpler.

Download the file and place in your .mozilla/plugins folder.

---

### Post by Colonel Kilkenny on 2009-10-24
You guys should probably mention what is your browser. Okay, it is probably Firefox as it's the default and you're having problems with Flash but the fixes for Firefox + Flash can be totally different than Chromium/Opera/etc. + Flash.

---

### Post by SuperSonic4 on 2009-10-24
Yes it's very easy to download and install but that's not what the OP is asking.

My own opinion is that it won't make it in because it's not stable enough for ubuntu's package policy

---

### Post by philinux on 2009-10-24
I dont think it will hit the ubuntu repos until it is actually release. It's still an alpha refresh.

However debian dont seem to have a problem. They have a deb package.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555)

or

[http://packages.debian.org/sid/flashplugin-nonfree](http://packages.debian.org/sid/flashplugin-nonfree)

Also see last post.
[http://swiss.ubuntuforums.org/showthread.php?t=1297977](http://swiss.ubuntuforums.org/showthread.php?t=1297977)

---

### Post by zenarcher on 2009-10-24
I just get it by adding the PPA and it works fine for me.

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

Cheers,
zenarcher

---

### Post by Martin Marshalek on 2009-10-24
Is that an official adobe ppa or just a user ppa?

---

### Post by jblackhall on 2009-10-24
> **binskipy2u said:**
> will we have to jump thru hoops looking/googling for a how'to to install 64bit flash in ubuntu 64bit (mustve read 10 different sites/blogs, how to do this)?

it's apain to install 32bit this or that, and then find how to uninstall and install 64bit flash..

Do you specifically want 64-bit Flash, or do you just want Flash to work with Firefox on a 64-bit Ubuntu install?  If you just want working flash, you simply need to install flashplugin-installer.  If you specifically want/need a 64-bit Flash, that may be a different story.  Is there a reason you want/need 64-bit Flash as opposed to using the one in the repos that works?

---

### Post by scottmuz on 2009-10-24
I've just installed karmic and was disappointed that for amd64 the 32 bit flashplugin with ndiswrapper is still used.

Adobe have had the native 64 bit flashplugin out for about 8 months now and it works very well. 
Why not include this?

---

### Post by Keyper7 on 2009-10-24
> **jblackhall said:**
> Is there a reason you want/need 64-bit Flash as opposed to using the one in the repos that works?

Most people install the 64-bit version because it works better and it's more stable than the wrapped 32-bit version, in their experience.

---

### Post by Keyper7 on 2009-10-24
> **scottmuz said:**
> I've just installed karmic and was disappointed that for amd64 the 32 bit flashplugin with ndiswrapper is still used.

Adobe have had the native 64 bit flashplugin out for about 8 months now and it works very well. 
Why not include this?

Because it's still labeled as alpha. This hasn't caused problems so far, but Adobe can always pull off a "Well, it's an alpha, you were advised not to use it in production machines..." as an argument to not release security updates. We have no idea of all possible under-the-hood reasons that is making Adobe keep the alpha label, and Canonical surely does not want to be held responsible for making its entire userbase vulnerable to security holes.

I use the 64-bit version, but I agree with their position. I don't worry about flash security too much because I use Flashblock and never visit questionable websites, which is NOT the case of a lot of users.

---

### Post by macaholic on 2009-10-24
I think it's silly to withhold it from the official repos, nspluginwrapper has always been a messy workaround. If the reason truly is that it is still labeled as an "alpha" by adobe, then it's just an issue of semantics; it seems the general consensus is that the native 64-bit flash is more stable than the wrapped 32-bit plugin, despite its more "complete" status label from adobe.

---

### Post by null_pointer_us on 2009-10-24
> **Keyper7 said:**
> Because it's still labeled as alpha. This hasn't caused problems so far, but Adobe can always pull off a "Well, it's an alpha, you were advised not to use it in production machines..." as an argument to not release security updates. We have no idea of all possible under-the-hood reasons that is making Adobe keep the alpha label, and Canonical surely does not want to be held responsible for making its entire userbase vulnerable to security holes.

I use the 64-bit version, but I agree with their position. I don't worry about flash security too much because I use Flashblock and never visit questionable websites, which is NOT the case of a lot of users.

1. Oddly, I never thought of 32-bit Flash as being for the security conscious, even when kept up-to-date. My understanding is that it was an unstable, poorly optimized mish-mash of low quality 32-bit/x86 code that Adobe has had to largely rewrite in order to port it.

2. IMO it's better to be "more vulnerable" than to inflict the virus-like unstable mess that is nspluginwrapper + 32-bit flash. Maybe it has greatly improved since 8.10, when a flash-using tab would often take down the whole browser or lock up other tabs seemingly at random.

---

### Post by Keyper7 on 2009-10-25
> **macaholic said:**
> I think it's silly to withhold it from the official repos, nspluginwrapper has always been a messy workaround. If the reason truly is that it is still labeled as an "alpha" by adobe, then it's just an issue of semantics; it seems the general consensus is that the native 64-bit flash is more stable than the wrapped 32-bit plugin, despite its more "complete" status label from adobe.

Care to provide *evidence* that it's just an issue of semantics?

What if "alpha" actually means "it's feature-complete but the security part has not been completely ported yet"?

> **null_pointer_us said:**
> 1. Oddly, I never thought of 32-bit Flash as being for the security conscious, even when kept up-to-date. My understanding is that it was an unstable, poorly optimized mish-mash of low quality 32-bit/x86 code that Adobe has had to largely rewrite in order to port it.

Regardless, it's still the version that Adobe officially supports and compromises to provide patches to security problems they know of. The same cannot be said about the 64-bit version while it's shielded by the "alpha" label.

> **null_pointer_us said:**
> 2. IMO it's better to be "more vulnerable" than to inflict the virus-like unstable mess that is nspluginwrapper + 32-bit flash.

You think that way because you're not Canonical. And therefore you're not the one who will come under fire if a serious security hole only in the 64-bit version is found.

---

### Post by zenarcher on 2009-10-25
> **Martin Marshalek said:**
> Is that an official adobe ppa or just a user ppa?

I think it's just a user PPA.  I just know that installing from there, I have the Adobe 64 bit flash and it has worked perfectly for me.  When I manually install from Adobe, for some reason, I have to tweak around to get Hulu Desktop to find the flashplayer.  Yet, installing from this PPA, it just works.

Cheers,
zenarcher

---

### Post by Martin Marshalek on 2009-10-25
Thanks, I tried the repo and it's great that there is finally a deb file. Until now I've used the script on in the sticky but I never liked it because it can't be uninstalled easily (in event the developers put the native flash in the repos). Now I just need to use synaptic.

---

### Post by macaholic on 2009-10-26
> **Keyper7 said:**
> Care to provide *evidence* that it's just an issue of semantics?

What if "alpha" actually means "it's feature-complete but the security part has not been completely ported yet"?

I don't know that it means that and neither do you, nobody but adobe knows what the "alpha" label means for it. There's other beta and alpha software in the repositories, the user generally knows the risks associated when installing these programs. I just don't see the justification in withholding it from the repositories completely, it's not as if it is installed by default.

---

### Post by SevenMachines on 2009-10-26
> **Martin Marshalek said:**
> Is that an official adobe ppa or just a user ppa?

It's a user ppa :) Its just the main karmic 32 bit package tweaked to download the 64 bit plugin instead, with chromium added. Hopefully its a bit easier than downloading and setting up manually

---

### Post by zika on 2009-10-26
> **zenarcher said:**
> I think it's just a user PPA.  I just know that installing from there, I have the Adobe 64 bit flash and it has worked perfectly for me.  When I manually install from Adobe, for some reason, I have to tweak around to get Hulu Desktop to find the flashplayer.  Yet, installing from this PPA, it just works.

Cheers,
zenarcherThere is a simple way of installing 64-bit-flash-plugin. It as as easy as:
1. download archive from adobe site for example with ```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```2. extract libglashplayer.so from the archive for example with ```
tar -xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```3. make sure You have ~/.mozilla/plugins folder for example with ```
mkdir ~/.mozilla/plugins
```4. copy libflashplayer.so to ~/.mozilla/plugins for example with ```
cp libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```If You want to uninstall the only thing You need to do is remove libflashplayer.so from ~/.mozilla/plugins folder for example with ```
rm ~/.mozilla/plugins/libflashplayer.so
``` so I, really ca not see any simpler method than this. No sudo, no .deb, nothing. Also very easy to refresh once new version is available and safer than having this plugin under sudo privileges in systems folder.

---

### Post by zenarcher on 2009-10-26
> **zika said:**
> There is a simple way of installing 64-bit-flash-plugin. It as as easy as:
1. download archive from adobe site for example with ```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```2. extract libglashplayer.so from the archive for example with ```
tar -xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```3. make sure You have ~/.mozilla/plugins folder for example with ```
mkdir ~/.mozilla/plugins
```4. copy libflashplayer.so to ~/.mozilla/plugins for example with ```
cp libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```If You want to uninstall the only thing You need to do is remove libflashplayer.so from ~/.mozilla/plugins folder for example with ```
rm ~/.mozilla/plugins/libflashplayer.so
``` so I, really ca not see any simpler method than this. No sudo, no .deb, nothing. Also very easy to refresh once new version is available and safer than having this plugin under sudo privileges in systems folder.

That's the way I've always done it, as well, however when doing so, for some reason, the Hulu Desktop application cannot find the flashplayer and I have to modify the Hulu Desktop file to point to the flashplayer.  Using the PPA, that isn't necessary.  Hulu Desktop finds the flashplayer without any modification.  Otherwise, as you say, it works fine per your directions.

Cheers,
zenarcher

---

