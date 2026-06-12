---
title: "Any Movement on Fixing the Networking Issues?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-10-25
I've read *dozens* of threads regarding the networking troubles on Karmic, ranging from slow Internet speeds (possibly a DNS issue) to slow networking speeds in-general (possibly an avahi-daemon issue), and am wondering if any fixes are in the pipeline.

My particular problem is all the proposed "fixes" don't work for me and, actually, make my system *worse*. Please, this isn't a rant or flamebait; I'm just trying to figure-out how to speed this stuff up.

Thanks, community!

---

### Post by Rinzwind on 2009-10-25
Hello, just to add to the confusion: I have not had a single problem with networking. Even the annoying keyring question at start-up when auto-login is set was solved with some settings in /applications/accesories/password and encryption keys. 


Except for smplayer sometimes stopping playback when I ffw and the spacebar stopping playback but not restarting playback when I press it again are the only 2 issues I have yet to solve or find a sollution to.

No, nothing that is related to connectivity.

---

### Post by moore.bryan on 2009-10-25
That really does add to the confusion, but highlights the concept of anecdotal evidence; i.e., it *seems* as though *everyone* is having problems. So, it's nice to hear it's working "out of the box" for someone! :-)

Oh, and, I never ran into the keyring problem... I guess that also furthers the confusion!

---

### Post by phrizek on 2009-10-25
I came here wondering the same thing. I've had tons of networking issues with Karmic, especially concerning slow internet speeds using wireless. I really hope 9.10 isn't released without a fix first, or I feel many people (new to ubuntu in particular) will be put off by this otherwise fantastic release. As it is now, I can't seriously use my computer because of spotty access to the internet, and I'm considering going back to 9.04. Considering that people mostly use their computers for surfing the web, this should really be a top priority.

Hopefully something is being done as we speak!

---

### Post by Crunchy the Headcrab on 2009-10-25
Yes, I have slow internet also.  Communicating on my local network seems to work fine.  Also I can't use certain websites like Last.fm that I could use on Jaunty or on other distros that used Firefox 3.5.3 also.

---

### Post by cyberkilla on 2009-10-25
No problems for me either.

---

### Post by coffeecat on 2009-10-25
No problems here either. I've tried four different wireless chipsets and they all work fine. I wonder if the reported slow wireless speeds are down to particular chipsets. It would be helpful if people reporting slow speeds with wireless were to report what chipset they are using. Without such information, such reports are of little use.

One good thing I've found in Karmic is that the [fiddling you had to get up to]("http://ubuntuforums.org/showthread.php?t=1169149") in Jaunty in order to browse smb shares is no longer necessary.

---

### Post by anselm on 2009-10-25
Some of the fixes have helped me a little but my internet page load times are awfull was a lot better in previous releaes 8.04 is were it started getting bad for me. my lan speeds are great just internet.

Have a dell 2400, using a realtek network card not the on board broadcomm.

---

### Post by sdowney717 on 2009-10-25
what happened to my network manager?
it is still working for the wired network, but i can get no information out of it.

---

### Post by sdowney717 on 2009-10-25
here is a better shot. 
also what happened to the pictures, used to post picture, click on it and you get it zoomed, now it is tiny.

---

### Post by Crunchy the Headcrab on 2009-10-25
> **anselm said:**
> Some of the fixes have helped me a little but my internet page load times are awfull was a lot better in previous releaes 8.04 is were it started getting bad for me. my lan speeds are great just internet.

Have a dell 2400, using a realtek network card not the on board broadcomm.

Okay.  I just entirely fixed my problems by setting a static IP address for my machine and manually entering the DNS addresses.

Obviously not an optimal solution because it means that I have to manually enter the information for any network I want to use...but at least it works fast at home now :).

PS.  I also have a realtek device.

---

### Post by Crunchy the Headcrab on 2009-10-25
Okay.  It's not as complicated as I made it seem the first time.  I already tried the other fixes and none of them seemed to work for me but this did.

System > Preferences > Network Connections

In my case I access the internet through a wireless nic so I navigated to the wireless tab and hit edit on my wireless connection.

Then I changed the drop down menu from automatic (DHCP) to
automatic (DHCP) addresses only

Finally I put the DNS servers provided by my isp in the field labled DNS servers.

So it turns out I don't have to use a static IP address.

---

### Post by moore.bryan on 2009-10-26
Interesting there is such a varied response to the thread... I've dumped Swiftfox and am using only Firefox from the PPA (3.5.5pre) and Opera 10 Beta (10.10); things have sped-up *significantly *compared to before, but still stagnates far too often for my comfort.

I've never used DHCP, but made the ipv4 changes suggested; nothing. I've also done all the "stand-on-one-leg-as-you-hold-your-right-ear-and-howl-at-the-moon" tricks suggested in other threads, but nothing really works. I'm fairly certain this is a DNS issue, but none of the DNS fixes work for me.

lspci:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```

---

