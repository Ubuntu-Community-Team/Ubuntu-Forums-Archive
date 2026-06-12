---
title: "Transmission bug"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hgergo on 2009-09-04
I have a big problem with transmissionbt since version 1.73 when i try to download a file transmission is freezing and i can do nothing but upload is working ok.
Can sombody help me with this problem?

---

### Post by Charles Kerr on 2009-09-04
> **hgergo said:**
> I have a big problem with transmissionbt since version 1.73 when i try to download a file transmission is freezing and i can do nothing but upload is working ok.
Can somebody help me with this problem?
Since you say upload is working okay, by "freezing" do you mean that Transmission isn't downloading?

If you're able to upload, your networking is probably okay.  The most likely reason is a stuck swarm -- few seeds and lots of downloaders all at about the same % done as you. You can test this by looking at the peers' % done in the Properties dialog's Peers tab and comparing it to your own.  When this happens, all you can do is wait for another seed to show up or to find a similar .torrent somewhere else.

As with Every BitTorrent Thread Ever, there will doubtless be posters who say switching to their favorite client will fix this problem.  If the swarm is stuck, they are wrong. ;)

---

### Post by taavikko on 2009-09-04
> **Charles Kerr said:**
> Since you say upload is working okay, by "freezing" do you mean that Transmission isn't downloading?



1.73 version the gtk-interface seems to freeze. As what my limited testing allows me to observe.
Let's wait for the 1.74 version to have FFe...

---

### Post by steeleyuk on 2009-09-04
I had the same problem on Jaunty using 1.73, seems like an issue with that version.

---

### Post by taavikko on 2009-09-04
> **steeleyuk said:**
> I had the same problem on Jaunty using 1.73, seems like an issue with that version.

Issue with it or some incompatibly issues with gtk..
Let's wait for what Charles has to say (I believe he's the man behind transmission)

ps. Having tried almost every torrent-client in known universe, have found my choice for gnome. Thank you for that.

---

### Post by hgergo on 2009-09-04
interesting thing observed transmission is freezing when downloading to ntfs and to ext4 is working ok

---

### Post by taavikko on 2009-09-05
Seemed to be just some sort of temporary glitch with me...
(if not making poor performance by wifi an issue)

All I seem to get is some warnings if changing preferences...
```
(transmission:14490): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.21.5/gobject/gsignal.c:2387: instance `0x235bd80' has no handler with id `4525'
```

And Charles, if reading, when to expect an systray speed settings in gtk?
(like in deluge, and if not mistaken, osx version is accompanied with similar?)
not meaning the "temporary speed limit"

//edit
transmission fails to close, sporadically.

---

### Post by hgergo on 2009-09-08
And the big question is why ubuntu is not updating transmission?

---

### Post by taavikko on 2009-09-08
> **hgergo said:**
> And the big question is why ubuntu is not updating transmission?

[https://bugs.edge.launchpad.net/ubuntu/karmic/+source/transmission/+bug/418367](https://bugs.edge.launchpad.net/ubuntu/karmic/+source/transmission/+bug/418367)
It's being worked on (no need to comment on the bug)

---

### Post by forcecore on 2009-09-08
[http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

thats it... you can manually install 1.74

---

### Post by hgergo on 2009-09-08
i try it is teh same it still freez when downloading to ntfs partition.
And is is jounty olnythat is see can be from hat te problem to i think

---

### Post by hgergo on 2009-09-12
Sad things 1.74 is freezing too teh update solved nothing

---

### Post by andrewabc on 2009-09-12
According to website [http://www.transmissionbt.com/](http://www.transmissionbt.com/)
They are putting out 1.75 betas.
[http://trac.transmissionbt.com/wiki/Changes](http://trac.transmissionbt.com/wiki/Changes)

Dunno if any of those bugs were the problem. Maybe file a bug on ubuntu and transmission bug trackers?

---

### Post by OwnSurname on 2009-09-13
I'll post here because I think is related, otherwise I'm going to open a new thread. I've two computers (one on Jaunty 64-bit, the other one on Jaunty 32-bit), my modem/router is a Thomson tcw710 (unfortunately), and both are connected via wireless, and correctly portforwarded with static IP. When I switch on Transmission (1.51), after few minutes it freezes all the connections, so I can't browse (neither with Opera, nor with Firefox), can't use Skype, and so forth. I can still ping though. So I installed Transmission 1.74, but the problem is still there. I can tell it's NOT a bandwidth problem, because I installed deluge on one computer, and using the maximum download bandwidth I can still browse and all the rest. Anyway, as soon as I switch on Transmission on one of the two computers (I tried both), then everything freeze. Also, it happens even if I limited the u/d bandwidth to 1 KB/s. If switched off, after few minutes everything get normal again, but not always, sometimes a restart of the computer is needed. Any guess / clue?

---

### Post by bobince on 2009-09-14
> **OwnSurname said:**
> When I switch on Transmission (1.51), after few minutes it freezes all the connections, so I can't browse

This is usually a router problem rather than anything to do with the client or OS. Cheap and nasty routers/modems can't handle all the connections a busy BitTorrent swarm can generate, and sometimes fall over. See if reducing the &#8216;Maximum peers&#8217; limits in the Network prefs tab helps.

(Other protocols can have the same effect, but BT is especially effective at sucking up connections fast.)

---

### Post by andrewabc on 2009-09-14
Transmission 1.75 is out.
[http://trac.transmissionbt.com/wiki/Changes](http://trac.transmissionbt.com/wiki/Changes)

Once debian gets 1.75 someone should report it to launchpad so it gets updated.
[http://packages.debian.org/sid/transmission](http://packages.debian.org/sid/transmission)
[https://launchpad.net/ubuntu/+source/transmission/+bugs](https://launchpad.net/ubuntu/+source/transmission/+bugs)

---

