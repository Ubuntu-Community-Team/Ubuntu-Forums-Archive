---
title: "Switching from i386 to amd64 - expected problems"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by XAVeRY on 2008-06-24
Hello there.
I'm thinking of switching from my i386 Hardy installation to an amd64 Hardy installation. My /home folder is a separate partition. Will I lose any of my settings, logs? Will I have to reconfigure everything from scratch? What kind of problems can I expect?

---

### Post by pytheas22 on 2008-06-24
If you try to just upgrade over the Internet from 32-bit to 64-bit, I doubt it would go smoothly, although I don't really know.  If you do a clean installation, everything should be fine, including your /home directory.  When I switched from Feisty to Hardy, I did just that (went from 32 to 64 via a clean install), while keeping /home, and everything was fine.  I don't think anything in /home cares very much about the system architecture.

Otherwise 64-bit should be pretty solid.  There are a handful of places where you might run into difficulties, but they're increasingly few.  If you use any proprietary applications (Skype is an example), make sure that they release a 64-bit binary or that you know how to run the 32-bit in a 64-bit system (it can easily be done, but it's tough if you don't have directions to follow).  With some wireless cards, ndiswrapper doesn't work well under 64-bit, but again, I think this is rare.  The Adobe flash plugin for Firefox used to be flaky on 64-bit systems, but it seems to work fine in Hardy.  In general I'm very pleased with 64-bit.

---

### Post by XAVeRY on 2008-06-24
I'm considering a clean installation, I'm currently downloading the alternate CD of Hardy AMD64. Thank you very much for your suggestions. I'll surely post my experiences once I'm done.

---

### Post by XAVeRY on 2008-06-25
I'm all done now, so I guess I'll just share what I've been through for the last 19 hours.

I have to admit that I'm very happy in general and I recommend switching from i386 to amd64 to anyone who has a 64-bit capable system. The whole system seems more responsive (at least to me), and besides - you get the good feeling that you're using all the resources that you've been given, what is generally a good thing.

As for my doubts : all my settings have been kept, I was quite surprised when - after the reinstallation - my old desktop showed up, with all the icons and everything (I'm just not used to it since I've been using Windows until April 2008). The only thing that I didn't like is that the package list wasn't kept and I had to deal with it myself, what cost me a little time, but I didn't encounter any larger problems.

As for Skype, I just googled "Skype amd64" and applied to the found instructions - without any problems. My wireless card has native Linux drivers, so that's not a problem either (iwl4965). The Flash plugin works like a charm as well.

The alternate CD install also satisfied me. I felt that - even though it was 100% text mode (I'm used to these, since I used to experiment with Slackware) - it gave me much more control over the installation and I was sure that nothing would be *automagically* formatted by mistake. I just mounted my former /home partition as the new /home partition and voila!

Anyway, I'm very, very satisfied and I encourage all the owners of 64-bit systems to go ahead and install amd64 version of Ubuntu or whatever system they might be using.

Thank you very much.
D.K.

---

### Post by MarcG on 2008-06-25
I did a clean Hardy amd64 install but am having some problems with the flash plugin. Most sites, such as youtube, work fine, but pepsistuff.com partially works. They have what's supposed to be a media player showing video clips. The whole thing requires Flash-8 to show up. But with the flash9 plugin, all I get is the media player, not the video that's supposed to be in the player. And there are a couple other sites where the video is gray. 

Is there any way to get some kind of error report to help figure out what's missing?

Thanks.

--Marc

---

### Post by pytheas22 on 2008-06-25
MarcG,

By default Firefox in Hardy wants to use the shockwave flash plugin, which works pretty well, but which does have some issues on certain sites.  Adobe's plugin is unfortunately not free, but it should work better.  Try this to remove shockwave and replace with Adobe's:
```

sudo apt-get remove swfdec-mozilla
sudo apt-get install flashplugin-nonfree
```

then restart Firefox.

The GNU people have been trying for a while to implement their own free flash player, but they've had a rough time because until recently there wasn't much public documentation about how flash works.  I heard that Adobe had a change of heart, however, and released/will soon be releasing specifications, so hopefully we'll have a good free flash player before long.

(The reason that flash used to have issues on 64-bit systems by the way was that Adobe only released a 32-bit binary and there was some hacking required to get in working in a 64-bit browser.)

---

