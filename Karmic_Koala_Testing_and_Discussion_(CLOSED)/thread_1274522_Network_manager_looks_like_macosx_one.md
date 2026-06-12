---
title: "Network manager looks like macosx one :/"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xens on 2009-09-24
Am I the only one surprised? There are nice new features with this new nm version but the design ?

---

### Post by Tibuda on 2009-09-24
You are talking about the new Humanity iconset?

---

### Post by SuicideSmurf on 2009-09-24
I actually hadn't noticed that! I kind of like it ....

---

### Post by xens on 2009-09-24
I'll send screenshot.
Yes it could be nice but not with this icon set

---

### Post by tretle on 2009-09-24
does anyone else have it crash if you left click on it?

---

### Post by xens on 2009-09-24
screenshot attached

---

### Post by steeleyuk on 2009-09-24
Haven't gotten the updates for that yet, had seen the earlier mockups though which looked quite nice.

---

### Post by Squonk07 on 2009-09-24
> **xens said:**
> Am I the only one surprised? There are nice new features with this new nm version but the design ?

Well, we can't deny (at least I won't) that OS X has a gorgeous shell (by some estimations at least). If the new NM can be said to look that good, then that's an amazing compliment. But if you're referring to the actual layout, I guess there's only so many ways you can arrange the same information.

Personally I like the changes. Hopefully they go more than skin deep. I'd like if NM were a little better at recognizing available networks (it has trouble drawing in the weaker ones).

---

### Post by Roger E Critchlow Jr on 2009-09-24
> does anyone else have it crash if you left click on it?


Yep, that's what happened when I went to look.  Fell right off the wireless network, luckily I have a wired connection sitting  here.

---

### Post by vredley on 2009-09-24
> **tretle said:**
> does anyone else have it crash if you left click on it?
[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097)

Although this is just a duplicate; the original is a secret for some reason.

---

### Post by xens on 2009-09-24
> **Squonk07 said:**
> Well, we can't deny (at least I won't) that OS X has a gorgeous shell (by some estimations at least). If the new NM can be said to look that good, then that's an amazing compliment. But if you're referring to the actual layout, I guess there's only so many ways you can arrange the same information.

Personally I like the changes. Hopefully they go more than skin deep. I'd like if NM were a little better at recognizing available networks (it has trouble drawing in the weaker ones).

I totally agree with you, the point is that there's a lot of changes (xplash, gdm, theme, icons, ...) and nothing is consistent they all looks great one by one but put them together and it's messy. Hope this'll change until release :]

---

### Post by xens on 2009-09-24
> **vredley said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097)

Although this is just a duplicate; the original is a secret for some reason.

I've got better: When I plug my GSM selecting it crash my mobile phone and reset it. I thought that Nokia was bulletproof... FAILED :)

---

### Post by Eestlane on 2009-09-24
It should cut down the Network card names though.

---

### Post by FuturePilot on 2009-09-24
> **tretle said:**
> does anyone else have it crash if you left click on it?

See [http://ubuntuforums.org/showthread.php?t=1269999]("http://ubuntuforums.org/showthread.php?t=1269999")

---

### Post by Squonk07 on 2009-09-24
> **xens said:**
> I totally agree with you, the point is that there's a lot of changes (xplash, gdm, theme, icons, ...) and nothing is consistent they all looks great one by one but put them together and it's messy. Hope this'll change until release :]

At least we're trying. I've been following Ubuntu since Edgy, and other than upstream GNOME changes Ubuntu had remained mostly stagnant (insofar as the interface; the functionality increased at an astounding pace). The changes in Karmic are already pretty revolutionary. I'd rather support a flawed work of genius than a teetotaler's sum total of five years of evolutionary updates.

And, to add to the chorus, my NM just crashed with a left click, too.

---

### Post by zekopeko on 2009-09-24
It looks pretty but it's just a little to big for my taste. I'm using it on a netbook and the screen space it takes is really huge. Font and icons should be smaller IMO.

---

### Post by VMC on 2009-09-24
My network icon works perfectly now. It didn't an hour ago. Left-click, right-click. Everything works. I was told you need Human theme and Humanity icons for it to work. I don't know what that has to do with it, but that's how I'm setup now.

---

### Post by DanaG on 2009-09-25
Hmm, I'd say it's rather ugly.

full-size image also  [here]("http://users.csc.calpoly.edu/~dgoyette/Screenshot-3.png")

Note the horrible proportions, and the odd duplication of the current network in two places -- and wait, is there a network called "Disconnect"?  What was wrong with the radio-buttons we had before?

Edit: I think the duplication is caused by having multiple visible APs with the same SSID. Also, it seems somebody was creating an ad-hoc network with the same name as the managed one -- and yet, with the Tangerine icon theme, the ad-hoc one looks like a "radio tower", which one would reasonably assume indicates an access point.

---

### Post by blakamin on 2009-09-25
Mine doesn't have the network in 2 places. Weird.

And, could you please resize your image or make it an attachment.

---

### Post by Mr. Picklesworth on 2009-09-25
Nice stuff so far. Good thing we're a month from the final release.
As mentioned, Disconnect is abysmally poorly placed.

Broadcom continues to hate freedom, so the network I'm connected to doesn't get listed under Active Network even though I definitely am connected to it. (Why HP continues to support these guys with lines of netbooks that can run Linux is simply beyond my understanding).

The heart icon is horrifying. If it was small - smaller than the network status icon - it would be okay fine. However, it is not so it is simply distracting and looks way more important than it is.

Agreed that the Disconnect button needs to use smaller text and be indented or right aligned.

---

### Post by xens on 2009-09-25
The disconnect button is a really nice option! Before that I had to use the killswitch or turn off wifi in networkmanager

---

### Post by golusweet on 2009-09-25
After latest updates, Network manager icon is missing from panel.

Anyone experiencing same issue?

---

### Post by NCLI on 2009-09-25
It probably crashed, many reports of that happening ATM. Just do an alt+F2 and type "nm-applet"

---

### Post by ljrmorgan on 2009-09-25
> **golusweet said:**
> After latest updates, Network manager icon is missing from panel.

Anyone experiencing same issue?

Yeh, and I have no wireless now too...

I'll try running nm-applet and see if that gets it back, there'll probably be a new update waiting that'll fix it.

---

### Post by Teamgeist on 2009-09-25
I had the same issue. It fixed itself after some more updates and a reboot.

---

### Post by zekopeko on 2009-09-25
> **xens said:**
> The disconnect button is a really nice option! Before that I had to use the killswitch or turn off wifi in networkmanager

I would like the Disconnect button on the right of the selected network. Now it's kinda like another network.

---

### Post by ljrmorgan on 2009-09-25
> **Teamgeist said:**
> I had the same issue. It fixed itself after some more updates and a reboot.

Is there any way to get wireless when your network manager is playing up? Only it makes updating a pain in the *** if you have no internet...

---

### Post by Amaranth on 2009-09-25
Not sure what you're thinking of, this looks absolutely nothing like the OS X wireless manager. Other than the fact that it's an icon near the clock with a menu, anyway.

---

### Post by pelle.k on 2009-09-25
> **DanaG said:**
> Hmm, I'd say it's rather ugly.
Note the horrible proportions, and the odd duplication of the current network in two places -- and wait, is there a network called "Disconnect"?  What was wrong with the radio-buttons we had before?
You're not using the correct icon theme - i belive *most* people are referring to the actual icon, not the UI for the applet.

> Network manager looks like macosx one :/
Other than being monotone (but not the same color) - no it does not. (a matter of how you perceive things i guess)

---

### Post by coldReactive on 2009-09-25
> **vredley said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436097)

Although this is just a duplicate; the original is a secret for some reason.

edge is no longer development launchpad, you can use www/bugs. again. Anyway, I don't mind the new look, but it is pretty different.

---

### Post by VMC on 2009-09-25
From reading this topic, it appears everyone is using a different icon. Mine has been the same ever since it was fixed. I don't see the issues. I'm using wired connections, maybe that's the difference. Today right-click show no more "heart" symbol.

---

### Post by coldReactive on 2009-09-25
> **VMC said:**
> From reading this topic, it appears everyone is using a different icon. Mine has been the same ever since it was fixed. I don't see the issues. I'm using wired connections, maybe that's the difference. Today right-click show no more "heart" symbol.

Same here, but I'm wired. I think the icon changes if you're on wireless (IE: this one shows you're wired.) I'm on jaunty though, this is the default icon for humanity it seems.

---

### Post by xens on 2009-09-25
> **Amaranth said:**
> Not sure what you're thinking of, this looks absolutely nothing like the OS X wireless manager. Other than the fact that it's an icon near the clock with a menu, anyway.

I mean the icons, the battery / wireless and the sound volume.

---

### Post by pelle.k on 2009-09-25
**OT**; I just spotted another thing - the new "wired" icon looks really weird besides the volume icon. It's proportions are all wrong. I left a comment in this old bug report; [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/423167](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/423167)

---

### Post by Squonk07 on 2009-09-25
> **VMC said:**
> Today right-click show no more "heart" symbol.

Yeah, the hearts seem to have gone bye-bye. I'm torn--I kind of liked them, but I agree with others that they were too big. I think a bigger concern would be the weird placement of the Disconnect options. Maybe just an X or some other icon to the side?

---

### Post by hugmenot on 2009-09-25
Well, too f---ing bad. My home network is called "IheartMonstera" and that heart icon was certainly a nice surprise.

---

### Post by Copernicus1234 on 2009-09-25
Gnome is much like Mac OS in its clean simplicity. KDE is much like Windows.

So I dont mind if the devs get some inspiration from Mac OS...Ive always felt its looks is its strong point. But I will never support Apple and buy their products since they are just another kind of Microsoft. Give them a little power and they start telling users what they can and cannot do. Its not for me.

---

### Post by motang on 2009-09-25
Yes, I love it. Karmic is shaping up well!

---

### Post by buzzmandt on 2009-09-25
really like the new nm-applet, I use it in kubuntu.

---

