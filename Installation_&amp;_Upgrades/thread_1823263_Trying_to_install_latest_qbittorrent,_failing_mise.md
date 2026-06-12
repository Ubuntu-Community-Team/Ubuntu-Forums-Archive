---
title: "Trying to install latest qbittorrent, failing miserably"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by AZBiker on 2011-08-11
I really like qBittorrent.  I would really love it if it worked in the unity desktop.  

There's a few issues with this--

1.  No icon in system tray.

2.  No access to latest version in software center.

Please help.  I've looked around in the forums and tried to "whitelist" all apps--I don't know what that means and don't personally understand why ALL apps weren't whitelisted in the first place.  That was unsuccessful.

Thanks for your help.

---

### Post by MG&amp;TL on 2011-08-11
Code::Blocks IDE is like this, no icon.

If they have a website or a launchpad account, there's probably somewhere you can get the source.

---

### Post by AZBiker on 2011-08-11
If I'm reading launchpad right, he's known about the bug with the tray icon since April.  No fix yet.  I can't complain though, I got what I paid for.

Update:  I just updated the version to the newest version through Synaptic.  I sure hope they work on the software center for Oneiric, because in Natty it's still about as useful as bewbies on a boar.

---

### Post by haqking on 2011-08-11
[http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)

Source and binaries are here, choose your system from drop downs in binaries and you will get the ppa and commands for install.

worked fine for me on 11.04 before i dropped back to 10.10

---

### Post by AZBiker on 2011-08-11
Just launched 2.8.4, still no icon in system tray.

---

### Post by MG&amp;TL on 2011-08-11
The software centre to be fair, is just a 'noob' way of installing something for new users (particularly the iPhone generation) who do 'point, click, done'

Is it available via apt-get? (for future reference)

---

### Post by AZBiker on 2011-08-11
Can anybody help with the system tray icon thing?

Thanks!

---

### Post by haqking on 2011-08-11
have you tried making sure system tray is checked in the qbittorrent options.

I just reinstalled it into my 11.04 VM and it works fine with icons etc.

see my post above for your binaries

---

### Post by MG&amp;TL on 2011-08-11
If you want it that badly, boot into classic gnome until a fix arrives.

You can hurry that along by filing bug reports on launchpad, or even learning to program and taking it on yourself.

---

### Post by AZBiker on 2011-08-11
> **MG&TL said:**
> The software centre to be fair, is just a 'noob' way of installing something for new users (particularly the iPhone generation) who do 'point, click, done'

Is it available via apt-get? (for future reference)

I personally like point, click, done myself.  I use computers as a way to communicate, so I'm always going to be a just a user.  My hobbies are things that go boom and vroom.  

Computers, for me, are just a way to learn more about my hobbies and communicate with people with the same interests.  Never been interested in computers just for computers sake, unfortunately.

---

### Post by MG&amp;TL on 2011-08-11
No, but presumably that's how you got here?

---

### Post by AZBiker on 2011-08-11
I got it to appear in the notification area at the top of my screen, I guess that's going to have to do.

---

### Post by haqking on 2011-08-11
> **AZBiker said:**
> I got it to appear in the notification area at the top of my screen, I guess that's going to have to do.

thats what you asked for right ? Show in system tray

---

### Post by MG&amp;TL on 2011-08-11
Unless he means the launcher?

Could you give us a screenshot of where you want your thing to be.

---

### Post by haqking on 2011-08-11
Well if you install it from apt-get it installs fine in my 11.04 VM and the system tray icon can be turned on and off in the options.

The launcher appeared as it should so perhaps its the old version in the software centre

---

### Post by AZBiker on 2011-08-11
Actually, I started running Ubuntu because I had a HD failure and lost my Windows2000 disc.  Was so desperately broke I needed an OS for internet access.  I asked around and Ubuntu was mentioned as being the most user-friendly of all the distros.  Now I'm not broke anymore so I'm weighing the pros-and-cons of building a new box and just going to Windows7.

With mechanical stuff (cars, motorcycles, guns), I'm the exact opposite.  I like to DIY.

---

### Post by MG&amp;TL on 2011-08-11
:(

At least consider dual-booting. Even kubuntu is considerably faster than windows 7.

---

### Post by AZBiker on 2011-08-11
After this restart it appeared!  I'm sure glad Synaptic still exists....

Thanks for all your help!

---

### Post by MG&amp;TL on 2011-08-11
No problem. Has that radically changed your opinion on Ubuntu? :p

If you do build your own computer (awesome, great thing to do), don't throw this one away, there is some great 'lightweight' distros around-I reccomend:

-Lubuntu. Light Ubuntu, currently runs 4.5x as fast as XP did on my machine.

-Puppy Linux. Ultra-light, boots in 30secs from a CD! Blindingly quick. Runs entirely in RAM, and leaves no trace. ( unless you want it to) Excellent for file recovery. about 10x as fast as XP.

Of course, you can go lighter, but that's where it gets a bit ridiculous.

---

### Post by AZBiker on 2011-08-11
I know there's some 'puter luddites still running Pentium IIs and a linux distro, lol.

If I build a new box it's going to be 64-bit.  I probably won't get rid of this one, it works.  I'm just going to use the new one as a media server eventually.

Right now I'm running an AMD Barton 3.2.  It's okay but not as fast as my Prescott P4 3.06.

I'm sticking to my guns on this though--SC needs a TON of work if it's going to replace Synaptic.  Isn't Oneiric doing away with Synaptic?

---

### Post by MG&amp;TL on 2011-08-11
What!? They can't ditch synaptic! That's the most useful thing in the suite!

If that's true, they'll be more muttered grumblings about Canonical's decisions than when they had Unity (although I like Unity)

Gnome 2 is going entirely in Oneiric. Unity 2d's filling the fallback gap.

---

### Post by AZBiker on 2011-08-11
I misread this article:
[http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html](http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html)

Synaptic will still be available in 11.10, just not installed by default.

---

### Post by MG&amp;TL on 2011-08-11
Thank god for that. No, it's alright, we all do it. I thought Gnome3 was the next default desktop for a bit.

---

