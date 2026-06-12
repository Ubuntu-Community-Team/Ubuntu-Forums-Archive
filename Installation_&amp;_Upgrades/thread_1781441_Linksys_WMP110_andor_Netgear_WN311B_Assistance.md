---
title: "Linksys WMP110 and/or Netgear WN311B Assistance"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by OmegaHarvest on 2011-06-13
Hi All,

First off, I would like to say that I'm completely new to Ubuntu and Linux in general so I'm not very knowledgeable about the ins and outs. I've also done a lot of searching already regarding my current issues and have only gotten so far.

I have a decent machine which I'm trying to get to run Ubuntu natively. I have everything going (and am even able to play many games through WINE) but I am struggling to get 2 of my Wireless PCI network adapters working correctly.

I have a Linksys WMP110 and a Netgear WN311B. Both of these 'kind of' work. In my searches, I have come across an application called 'ndiswrapper' but have had limited success with this, despite the tool looking very promising. I'll go through the issues I've had with each card.

The Linksys WMP110 works, but only at about 20% of the speed it should. I also have Windows (sadly) installed on the same machine and the network speed on this is as it should be. I have tried adding the WinXP drivers for this card using ndiswrapper but am having no luck. I'm using the x64 distro of Ubuntu and made sure I was running 64bit drivers. I got to one point where I ran a command and it said that ndiswrapper was running fine (after I had been through the motions getting errors due to the drivers not being 64 bit previously). Sadly I have forgotten this command, but it was very handy. Yet despite this reporting ndiswrapper working fine, I have no wlan0 at all and could get no further than this.

The Netgear WN311B had a proprietary Broadcom driver which yielded some very strange results. I was unable to see any local wireless networks until roughly 10-15 minutes after Ubuntu had been running. Then I could connect to the wireless but could not get any webpages to show. I hear people have had some success getting this to work in ndiswrapper but am unable to find the correct drivers. The drivers on Netgears website are in exe format so I grabbed the .inf and .sys files from the Windows install on the other partition. I am unsure wether these were the correct drivers though as this didn't seem to work. I had also forgotten the useful command by then which shows the status of ndiswrapper on startup.

What I'm really after is someone who has either of these 2 cards (pref the Linksys one) working well in Ubuntu x64. If someone could let a moron like me know how they got it working,o r what exact files they used for the Neatgear card I would be eternally grateful. I am a beginner when it comes to this so if you are kind enough to offer advice, please keep it simple (like me :-) ) so I can understand it as I slowly learn. I've done lots of playing around myself to get this going but have hit a brick wall so I'm hoping someone here can help!

Sorry for the wall of text and thanks to anyone who has read this and has any advice to give!

Cheers,

Omega/Pete :-)

---

