---
title: "Natty + HD 6670 + Mesa = ???"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by silentwords on 2011-04-30
It was a rough upgrade, but that's what I get for buying an ATI card that just went retail last week.

After  fixing the purple log in screen with nomodeset, and installing the  proprietary ATI driver, I noticed that the performance seemed... slow. I  tweaked the settings such at Anti-Tear, but it just didn't seem as  smooth as it should be. Not nearly as smooth as my other dual boot OS.  Then I saw this article. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It  talks about installing the open source driver. It also mentions that  the 6670 should work with 11.04, BUT, it needs a newer version of Mesa  than Nattys default. Unfortunately, it didn't say anything about how to  upgrade it.

So I searched for Mesa, and found the edge ppa, but  that's pretty much where my learning curve takes an abyssal plunge, and  I'm left staring blankly at the screen with my head half cocked.

Is  there going to be a Natty update for Mesa in the near future that I can  just sit tight for? If not, would someone be willing to write a  detailed guide for this card in particular?

I think it's worth  it. This card will probably be popular since it's really cheap and efficient. It  way out performs my old Nvidia 9800GTX (in 3D games), while drawing half the power.

Thanks for your time and help.

---

### Post by iSynic on 2011-05-01
Well, I'm pretty sure Mesa isn't our problem (but I think I know the install guide you're referring to - which did mention updating Mesa). I snagged Sapphire's Radeon HD 6670 and am having problems as well. 

If you want to try updating Mesa open up Synaptic and search for 'Mesa'. Chances are you're running the latest version, though.

I couldn't even get past login after installing Natty until I booted in safe-graphics-mode and updated the display drivers from there.

Regardless, I've got access to all of the animations but they're choppy and unpleasant. The Catalyst Control Center has no problem giving a detailed profile of my card, but clearly has a hard time utilizing it.

I'm going to try uninstalling and reinstalling the latest Catalyst package and see where I get. We may just have to wait for new drivers. But it seems like they should work better (since the same drivers offer much better performance in Maverick).

---

### Post by khelben1979 on 2011-05-01
[Mesa 7.10.2 Release Notes]("http://www.mesa3d.org/relnotes-7.10.2.html").

It's possible to download the source code and install the latest version of Mesa if this is the source of the problem. Installing instructions [here]("http://www.mesa3d.org/install.html"). Otherwise it's more recommended to just let the Ubuntu system do it's own upgrades to avoid problems which haven't been tested once the Ubuntu 11.04 was built.

---

### Post by silentwords on 2011-05-01
I was able to smooth it out a lot by installing the Compiz Manager and disabling VSync under OpenGL. 

Being 6 months new to Linux in general, I think I'm going to hold tight until the Ubuntu team updates it for me.

---

### Post by iSynic on 2011-05-01
> **silentwords said:**
> I was able to smooth it out a lot by installing the Compiz Manager and disabling VSync under OpenGL. 

Being 6 months new to Linux in general, I think I'm going to hold tight until the Ubuntu team updates it for me.

This seems to have helped me a lot as well. Thanks!

---

### Post by silentwords on 2011-05-02
Right on, glad it helped.

---

### Post by Funckyfizz on 2011-11-14
Hi, sorry to but in on this but I'm planning to build a computer using the HD 6670 as well. I was wondering if these problems have been fixed yet? Does ubuntu get full use out of the 6670 yet and if not, do you guys think it will any time soon?

Sorry for the noob questions but I've been running OS X for the past 4 years and am now planning on building a ubuntu machine :/

Thanks,
James

---

