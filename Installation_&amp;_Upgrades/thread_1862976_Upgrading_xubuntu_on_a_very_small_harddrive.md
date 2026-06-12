---
title: "Upgrading xubuntu on a very small harddrive"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by primvirlaux on 2011-10-17
Hey.

I'm using xubuntu 11.04 on an Asus x101 netbook. Total HD space is 8 GB, of which about 5 GB is used for the root partition. In practice, I have to be careful what I install and download in order not to run out of space.

I now got the message asking me if I want to upgrade to xubuntu 11.10, but doing so via the update manager is maybe not a good idea. Here are the problems I see: a) the update manager says it will download 700 MB in the process, which is already dangerously close to the free space left on the root partition. But even if I have enough space for the download, I don't know what the total space/temp files needed during installation will be, so there's chance I'll run out of space during the upgrade process. b) I don't know what the 11.10 upgrade includes in detail. It mentions a large number of new installations, probably lots of things I don't want since I'm low on space and that I would want to remove afterwards anyway.

Any suggestions how I should go about this? For one, can I upgrade (x)ubuntu from a live USB (same way as I installed it)? That would help with point a), since the installation files would only be on my usb, but that still wouldn't solve my problem b), that I'm afraid the ugrade will install things I don't need. Is there a way to perform a "minimal" upgrade, that only upgrades the core functionality?

Sorry, I guess you can see I'm pretty clueless about Linux... don't really know what exactly the upgrade 11.04 --> 11.10 entails. I guess a short answer to that question would be helpful too for me to understand what I actually want to do.

---

### Post by -kg- on 2011-10-17
With 8 GB total hard drive space (5 of which is root...what's the other 3 used for?), I wouldn't think you have much in the way of data you would need to save/back up.  What I would do (especially if you have/can get more than one USB drive) is to save what data/information you need to one USB drive, then do a fresh installation from the other Live USB.  If you're running so close to maxing out the drive, that's the only way I can see to be absolutely safe.

I'm not sure if you can upgrade from a CD/USB like you're asking.  I can find no information on it.

---

### Post by snowpine on 2011-10-17
I agree with -kg-'s suggestion, and furthermore you might consider performing a "minimal install" which is not as scary as it sounds if you follow a tutorial like this one: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by primvirlaux on 2011-10-17
Thanks for the suggestions, but isn't there an easier way than a complete re-install? I just installed xubuntu 2 weeks ago, and just now got all the configurations (desktop, touchpad settings) to my liking, so a complete new install seems a bit excessive to me, especially considering that in 6 months or so I'll have to do it again?

Like I said, I really don't know much about Linux, so I was wondering, what does the upgrade 11.04 to 11.10 actually include? The kernel is the same, right? So it'll update some existing and install some new programs? I'm sorry for the perhaps somewhat stupid question, but I'm wondering if the upgrade is actually worth the hassle, and on the other hand, what I'm missing out on if I skip this update (and if I can perhaps manually include part of the update myself by updating programs I use).

---

### Post by snowpine on 2011-10-17
> **primvirlaux said:**
> Thanks for the suggestions, but isn't there an easier way than a complete re-install? I just installed xubuntu 2 weeks ago, and just now got all the configurations (desktop, touchpad settings) to my liking, so a complete new install seems a bit excessive to me, especially considering that in 6 months or so I'll have to do it again?

Like I said, I really don't know much about Linux, so I was wondering, what does the upgrade 11.04 to 11.10 actually include? The kernel is the same, right? So it'll update some existing and install some new programs? I'm sorry for the perhaps somewhat stupid question, but I'm wondering if the upgrade is actually worth the hassle, and on the other hand, what I'm missing out on if I skip this update (and if I can perhaps manually include part of the update myself by updating programs I use).

Upgrading is one-click easy, but you said you don't have enough room, right?

Anways I personally would never blindly upgrade without making a Live USB of the new release and taking it for a week-long test drive. Give it a try and you will see for yourself what the new features are.

The biggest difference between Ubuntu releases is that all of the software (including the kernel) is approximately 6 months newer.

Some people keep individual applications up-to-date using the "PPA" system: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by -kg- on 2011-10-17
> **primvirlaux said:**
> Thanks for the suggestions, but isn't there an easier way than a complete re-install? I just installed xubuntu 2 weeks ago, and just now got all the configurations (desktop, touchpad settings) to my liking, so a complete new install seems a bit excessive to me, especially considering that in 6 months or so I'll have to do it again?

Not that I know of, really.  You could try an upgrade if you think you can make enough room to do it.  You'd need to uninstall any unnecessary software and transfer any data off the hard drive to external storage.  If the upgrade doesn't work, then you'll have to fresh install anyway, but it might be worth a try.  That's going to have to be a decision you make. (BTW, what is the extra 3 GB being used for?  If it's swap, you might be able to shrink it and make a little more room in your root partition.)

> **primvirlaux said:**
> Like I said, I really don't know much about Linux, so I was wondering, what does the upgrade 11.04 to 11.10 actually include? The kernel is the same, right?

Oh no...there is a major kernel upgrade.  The current kernel version in 11.04 is 2.6.38-11.  In 11.10 it is currently 3.0.0-14...a major kernel upgrade.  Other than that, there are a few changes for Xubuntu, specifically...[https://wiki.ubuntu.com/Xubuntu/OneiricOcelot/Final]("https://wiki.ubuntu.com/Xubuntu/OneiricOcelot/Final") (be sure to check out the technical data...some will apply to all branches).

It's just a decision you're going to have to make for yourself, specific to your circumstances.  If your current installation is working well for you, you might want to wait for the LTS in April.

---

